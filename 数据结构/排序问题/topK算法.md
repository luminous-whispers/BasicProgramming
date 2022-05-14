```ad-info
已魔改为	求中位数~
```
## 分析
### 介绍
- 由**Blum、Floyd、Pratt、Rivest、Tarjan**提出。
- 该算法的思想是修改快速选择算法的主元选取方法，提高算法在最坏情况下的时间复杂度。
- **递归**也是核心思想之一

### 时间复杂度
最坏上界 O(N)
## 实现
-源码:
```c
int bfprt(int *Data, int Len)
{
    const int Size = 5;
    int i;
    if (Len <= Size){//递归结束条件
        insertSort(Data, Len, 1);
        return *(Data + Len/2);
    }
    for (i = 0; i < Len-5; i += Size){
        insertSort(Data+i, Size, 1);
        *(Data+i/Size) = *(Data+i+Size/2+1);
    }
    insertSort(Data+i-Size, Len-i+Size+1, 1);
    *(Data+i/Size) = *(Data+i-Size/2);
    return bfprt(Data, Len/5+1);
}

int * insertSort(int *Data, int Len, int Mode)
{
    int i, j, Tmp = 0;
    if (Mode){
        for (i=1; i<Len; i++){
            for (j=0; j<i; j++){
                if (*(Data+j) > *(Data+i))
                {
                    Tmp = *(Data+i);
                    *(Data+i) = *(Data+j);
                    *(Data+j) = Tmp;
                }
            }
        }
    }
    else if(!Mode){
        for (i=1; i<Len; i++){
            for (j=0; j<i; j++){
                if (*(Data+j) < *(Data+i)){
                    Tmp = *(Data+i);
                    *(Data+i) = *(Data+j);
                    *(Data+j) = Tmp;
                }
            }
        }      
    }
    else
        printf("please input correct mode1");
}
```
