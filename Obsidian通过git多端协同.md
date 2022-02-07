## 这个文档已经被废弃
正常同步即可，obsidian手机端不支持直接移植配置文件夹。
另外，手机端workingCopy很容易排除cache。等再研究下pc端的git for o b

### 目标
obsidian多端同步, 可以通过git的pull/push方式进行手动同步, 操作便捷可移植性强. 
在ios手机/平板端也可以通过workingCopy和github进行编辑和同步.

### 实现

#### 思路

- 利用[Obsidian设置文件夹]([[Obsidian操作指南]])可迁移的特性进行设置同步. 同时利用git进行内容同步
- 克服的困难主要是ios端复杂的跨应用文件交互方式

#### 工具
- pc端 
	1. Git /免费
	2. github.com /免费
	3. Obsidian /免费
- 移动端
	1. WorkingCopy /128元买断
	2. Obsidian /免费
	3. ios文件app
	4. github.com /免费

#### 过程
##### pc端:
1. 配置好Obsidian设置文件夹, 名字为 .obsidian
2. 进行.obsidian备份, 我是存储在单独的仓库中
	这里的考量是:
	- obsidian设置文件夹的缓冲文件会频繁更改, 最好添加到ignore中不让Git进行同步
	- ignore后, 各端需要进行设置同步(比如热键自定义设置很重要)时就需要随时在云端能取出
	- 这样不同端设置不必实时保持一致, 避免了因手机和电脑端差异产生的一些设置差别被Git一视同仁. 比如手机和电脑这样就可以应用不同的主题, 否则就会必须保持一致还不能随意更改.
	但缺点是:
	- graph中的分组等频繁变动的设置不能同步, 如果需要同步, 只能手动复制黏贴
3. 新建文件夹, 然后新建.gitignore文件, 写入`/ .obsidian/*`
**(这个文件夹才是你的库, 刚才配置设置的文件夹不是, 只取出.obsidian文件夹就可以删了)**
	- 注意不要着急将.obsidian文件黏贴进来, 否则前功尽弃
	- 这是因为Git的ignore功能不会对已经提交过的文件生效, 我们需要先行提交一遍.gitignore文件
4. Git init这个库, 将.gitignore先commit, 信息可以写"add ignore setting file"
	- 别着急push
5. 黏贴入.obsidian, commit之后, 链接远程库, 然后push
	- 这样库就和远程库同步好了

##### ios端
1. 在ObsidianApp中建一个空白库, 然后打开文件app看是否建成功
2. 打开WorkingCopy, 选择Setup synced directory, 然后选择同步Obsidian中刚刚建立的这个库( 文件夹 )
 - 这一步的效果是, WorkingCopy会自动将它底下的库文件夹和Obsidain文件夹下的这个库相关联, 然后这两个文件夹会同步内容( 完全一致)
3. 用WorkingCopy和远程库链接. 
	- 别急着pull
4. 在WorkingCopy该目录下建一个和pc端一摸一样的.gitignore文件夹
5. 然后把另一个远程库/或提前存在手机的.obsidian文件夹移动到WorkingCopy该库目录下, 此时运气好的话直接就变灰了( 意味着被ignore了 ), 运气不好可以右划手动变灰
6. 试着push一次, 看看是否ignore成功. 
 - 恭喜, 移动端和电脑端同步成功.
 - 一言蔽之, 不要将.obsidian同步, 不要让它出现在github仓库里
 - 不幸的是, ios端目前不支持读取文件.obsidain设置