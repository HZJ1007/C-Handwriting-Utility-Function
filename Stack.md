# 栈  $\text{ Stack}$
### **使用说明**

`Empty()` 不用填写任何元素，返回值共 $2$ 种， $1$ 表示栈为空， $0$ 表示栈不为空。

`push(一个元素)` 需要填写入栈的元素，将此元素入栈，无返回值。若栈的长度大于的给定的 **数据范围**  ，便会输出越界错误提示。

`pop()` 不用填写任何元素，将栈顶出栈，无返回值。若栈为空，便会输出越界错误提示。

`top()` 不用填写任何元素，返回栈顶元素。若栈为空，便会输出栈空错误提示。

`Size` 变量值，栈顶的下标（下标从 $1$ 开始），也可以表示栈的长度。

--------
```cpp
//注意：请勿使用STL的头文件，否则可能会引起名称冲突
//需要自定部分
#define diytype /*这里填入一种数据类型，如 int/float/char……都行*/
const int R= /*这里填入数据范围*/;

//手写部分
diytype stack[R];
int Size=0;
bool Empty(void)
{
    return Size==0?true:false;
}
void push(diytype num)
{
    if (Size+1>R)  std::cout<<"Out of bounds ERROR!!!";//越界错误
    else    stack[++Size]=num;
    return ;
}
void pop(void)
{
    if (!Empty())   Size--;
    else    std::cout<<"Out of bounds ERROR!!!";//越界错误
    return ;
}
int top(void)
{
    if (Empty())   std::cout<<"stack empty."; //内容为空，无法找到top元素
    else    return stack[Size];
    return -1;
}
```

### 简化模板（可以直接 copy ）
```cpp
//需要自定部分
#define diytype /*这里填入一种数据类型，如 int/float/char……都行*/
const int R= /*这里填入数据范围*/;
//手写部分
diytype stack[R];int Size=0;bool Empty(void){return Size==0?true:false;}void push(diytype num){if(Size+1>R)std::cout<<"Out of bounds ERROR!!!";else stack[++Size]=num;return ;}void pop(void){if (!Empty())Size--;else std::cout<<"Out of bounds ERROR!!!";return ;}int top(void){if (Empty())std::cout<<"stack empty.";else return stack[Size];return -1;}int Getsize(void){return Size+1;}
```

测试程序
```cpp
#include <iostream>
//需要自定部分
#define diytype int/*这里填入一种数据类型，如 int/float/char……都行*/
const int R= 10/*这里填入数据范围*/;
//手写部分
diytype stack[R];int Size=0;bool Empty(void){return Size==0?true:false;}void push(diytype num){if(Size+1>R)std::cout<<"Out of bounds ERROR!!!";else stack[++Size]=num;return ;}void pop(void){if (!Empty())Size--;else std::cout<<"Out of bounds ERROR!!!";return ;}int top(void){if (Empty())std::cout<<"stack empty.";else return stack[Size];return -1;}int Getsize(void){return Size+1;}

int main()
{
    std::cout<<"原数组：";
    for (int i=1;i<=10;i++)
    {
        std::cout<<i<<' ';
        push(i);
    }
    std::cout<<"\n越界测试：";
    push(11);
    std::cout<<"\n栈顶依次输出：";
    while (!Empty())
    {
        std::cout<<top()<<' ';
        pop();
    }
    std::cout<<"\n越界测试：";
    pop();
    std::cout<<"\n空栈栈顶输出测试：";
    top();
    std::cout<<"\n测试结束";
    return 0;
}
```
