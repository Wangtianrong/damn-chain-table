# damn-chain-table
The problem that I hope to solve
本题要求实现一个函数，将两个链表表示的递增整数序列合并为一个非递减的整数序列。
函数接口定义：

List Merge( List L1, List L2 );
其中List结构定义如下：
typedef struct Node *PtrToNode;
struct Node {
    ElementType Data; /* 存储结点数据 */
    PtrToNode   Next; /* 指向下一个结点的指针 */
};
typedef PtrToNode List; /* 定义单链表类型 */
L1和L2是给定的带头结点的单链表，其结点存储的数据是递增有序的；函数Merge要将L1和L2合并为一个非递减的整数序列。应直接使用原序列中的结点，返回归并后的链表头指针。
裁判测试程序样例：

#include <stdio.h>
#include <stdlib.h>

typedef int ElementType;
typedef struct Node *PtrToNode;
struct Node {
    ElementType Data;
    PtrToNode   Next;
};
typedef PtrToNode List;

List Read(); /* 细节在此不表 */
void Print( List L ); /* 细节在此不表；空链表将输出NULL */

List Merge( List L1, List L2 );

int main()
{
    List L1, L2, L;
    L1 = Read();
    L2 = Read();
    L = Merge(L1, L2);
    Print(L);
    Print(L1);
    Print(L2);
    return 0;
}

/* 你的代码将被嵌在这里 */我的代码：
List Merge(List L1, List L2) {
	List p21=L1->Next,p11=L2->Next,p22=L1->Next->Next,p;
	if(p11||p22==NULL){
			if((p21->Data)<=(p11->Data)){
		List p21=L2->Next,p11=L1->Next,p22=L2->Next->Next;//第一个数字表示数列首位大小，1大2小，第二个数字为2的是临时容器指针 
	}
	p=(List)malloc(sizeof(struct Node));
	p->Next=p11;
	while(p11->Next){
		if (p11->Data <= p21->Data&&p11->Next->Data >=p21->Data) {
		p22=p21->Next;
		p21->Next=p11->Next;
		p11->Next=p21;
		p11=p21;
		p21=p22;
		}
		else
		p11=p11->Next;
		if(p21==NULL)
		break;
	}
	if(p21!=NULL){
		p11->Next=p21;
	}
	}

	L1->Next=NULL;
	L2->Next=NULL;
	return p;
}
