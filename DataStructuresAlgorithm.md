# Data Structures

## 第一章 绪论

### 1.1 什么是数据结构

数据结构的研究内容：

- 如何有效地**组织数据**
- 如何巧妙地**设计算法**

> 从程序设计的角度看，
> 数据结构是一门研究程序设计中的操作对象，以及这些对象之间的关系和操作的学科。

### 1.2 相关概念和术语

- 数据

  所有能输入到计算机中并被计算机程序处理的符号的总称

  > 文本、声音、图片、视频等

- 数据元素

  是数据的基本单位，它通常用于完整地描述一个对象

- 数据项

  指组成数据元素的、有独立含义的、不可分割的最小单位

- 数据对象

  指性质相同的数据元素组成的集合，是数据的一个子集

- 数据结构

​		带“结构”的数据元素的集合

>  结构表现为两个方面
>
>  - 逻辑结构
>
>   数据元素以及相互之间的关系在逻辑上的表示
>
>  > 线性结构：线性表、栈、队列、字符串、数组、广义表
>  >
>  > 非线性结构：树形结构、图形结构
>
>   <img src="Data Structures & Algorithm.assets\image-20230904164302159.png" alt="image-20230904164302159" style="zoom:80%;" />
>
>  - 存储结构
>
>   数据元素以及它们之间的关系在计算机中的存储方式
>
>   <img src="Data Structures & Algorithm.assets\image-20230904164434660.png" alt="image-20230904164434660" style="zoom:80%;" />



Eg：

![image-20230904163351169](Data Structures & Algorithm.assets\image-20230904163351169.png)

- 学号、姓名、性别、籍贯为4个**数据项**
- 每一行（一条学生记录）为一个**数据元素**
- 这张学生名单可以看作一个**数据对象**



### 1.3 算法和算法分析

算法：为了解决某类问题而规定的一个**有限长**的**操作序列**

**算法的特征**

- 有穷性

  执行的步数有穷；每一步的执行时间有穷

- 确定性

​		含义明确，非二义性

- 可行性

  每一步都是基本操作运算可实现的

- 输入

  有**零个**或多个输入

  > 算法输入可以是0个

- 输出

  有一个或多个输出

**评价算法优劣的基本标准**

- 正确性

  运行结果正确

  >首要指标

- 可读性

​		便于理解与交流

- 健壮性

​		对不合理输入的反应和处理能力

- 高效性

  - 时间高效

    执行效率高

  - 空间高效

    占用存储空间合理

  时间复杂度与空间复杂度是衡量算法效率的**主要指标**



### 1.4 时间复杂度

​		用语句执行的次数衡量算法的执行时间

Eg：求两个n×n矩阵的乘积

<img src="Data Structures & Algorithm.assets\image-20230905084348970.png" alt="image-20230905084348970" style="zoom:80%;" />

> 第一行`for(int i = 1; i <= n; i++)`执行了（n+1）次，因为从i=1开始执行，执行n次后，i等于n+1，此时会回到第一行，判断i是否≤n，所以第一行一共执行了（n+1）次
>
> 第二行`for(int j = 1; j <= n; i++)`执行了n* （n+1）次，对于每一个i，j都会执行n+1次，原因同上。第一行执行到i等于n+1时，跳过for循环语句，所以第二行一共执行n*（n+1）
>
> 总结：
>
> for循环的循环条件那一行执行n+次，循环体执行n次

本题中，f(n)=2n^3+3n^2+2n+1，即语句执行的次数与n有关，n是**问题的规模**。

下面具体计算本题的时间复杂度：

<img src="Data Structures & Algorithm.assets\image-20230905085759929.png" alt="image-20230905085759929" style="zoom:80%;" />



![image-20230905085911253](Data Structures & Algorithm.assets\image-20230905085911253.png)

> 通常用常见函数的增长趋势来表达一般算法的渐进复杂度

More Examples：

<img src="Data Structures & Algorithm.assets\image-20230905090255606.png" alt="image-20230905090255606" style="zoom:80%;" />

> 例1语句执行的次数与问题的规模没有关系，是一个确定的常数10000次
>
> 例2语句执行的次数与问题的规模有关系，且f(n)=n+1

<img src="Data Structures & Algorithm.assets\image-20230905091146282.png" alt="image-20230905091146282" style="zoom:80%;" />



> 例3易求
>
> 例4中，i与语句执行的次数f(n)有关，且i=2^f(n)，又因为i≤n，所以，又2^f(n)≤n，指对转换即可

#### 最好、最坏和平均时间复杂度

<img src="Data Structures & Algorithm.assets\image-20230905091713924.png" alt="image-20230905091713924" style="zoom:80%;" />

### 1.5 空间复杂度

​		算法执行过程所需临时存储空间的个数。

​		记作：S(n)=O(f(n))，其中n为问题的规模

<img src="Data Structures & Algorithm.assets\image-20230905092300214.png" alt="image-20230905092300214" style="zoom:80%;" />

> 只需要关注算法所需的临时存储空间的个数



- 算法要建立在数据结构的基础上
- 数据结构要通过算法来展现其魅力



## 第二章 线性表

### 2.1 线性表

#### 线性表的定义

​		线性表是由n个**类型相同**的**数据元素**组成的**有限**序列记为(a1，a2，a3...an)

​		<img src="Data Structures & Algorithm.assets\image-20230910121028846.png" alt="image-20230910121028846" style="zoom:67%;" />

> 线性表长度：线性表中元素的个数n( n ≥ 0 )
>
> 空表：n=0

#### 线性表的存储结构

- 顺序存储 （顺序表）：逻辑上相邻，物理上也相邻

<img src="Data Structures & Algorithm.assets\image-20230910121406231.png" alt="image-20230910121406231" style="zoom:67%;" />

> 顺序表要占用一片连续的存储空间。



顺序表的初始化工作：

```c++
#define MAXSIZE 10000
typedef struct
{
    ElemType *elem;//数组的动态分配
    //顺序表的基地址
    int length;//顺序表当前的长度
}SqList;
SqList L; 
L.elem = new ElemType[MAXSIZE]; 
L.length = 0;
//初始化工作
```

> `ElemType`: 数据元素的类型名，可以是简单数据类型或者自定义数据类型，例如，可以是int、double这些基本数据类型，也可以是book、stu这些自定义的数据类型。

- 链式存储（链表）





### 2.2 顺序表的基本操作

#### 初始化

​		制造一个空的顺序表

```c++
bool InitList(SqList & L){
	L.elem=new ElemType[MAXSIZE];//为顺序表分配空间
    //或用c的内存分配函数：
    //L.elem=(ElemType*)malloc(sizeof(ElemType)*MaxSize);
    //需要加载头文件<stdlib.h>，使用完毕要用free释放
	if(!L.elem) return 0;//存储空间分配失败
	L.length=0;//空表长度为0
	return 1;
}
```

#### 取值

​		根据给定的位置序号i，获取顺序表中**第i个**数据元素的值

```c++
bool GetElem(SqList L,int i,ElemType & e){
    if(i<1||i>L.length) return 0;//若i不合理，返回0
    e=L.elem[i-1];//第i-1个单元存储着第i个数据元素
    return 1;
}
```

> 根据给定的序号，而直接定位存储单元的特性，称为随机存取

#### 查找

​		指根据给定的数据元素的值e，查找顺序表中第一个与e相等的数据元素如果查找成功，就返回数据元素在顺序表中的序号，如果查找失败，就返回0。

```c++
int LocateElem(SqList L,ElemType e){
   for(int i=0;i<L.length;i++)
       if(L.elem[i]==e) return i+1;//查找成功
   return 0;//查找失败
}
```

#### 插入

​		在顺序表的第i个位置插入一个新的数据元素e使长度为n的顺序表变成为长度为n+1的顺序表。

<img src="Data Structures & Algorithm.assets\image-20230910152734062.png" alt="image-20230910152734062" style="zoom:67%;" />

插在第 4个数据元素之前，移动 6-4 +1次

插在第 i 个数据元素之前，移动 n-i+1次

```c++
bool ListInsert(SqList & L,int i,ElemType e){
    if(i<1||i>L.length+1)
        return 0;//插入的位置不合理，return 0
    if(L.length==MAXSIZE)
        return 0;//长度达到上限，return 0
    for(int j=L.length-1;j>=i-1;j--)
        L.elem[j+1]=L.elem[j];//插入位置以及之后的元素后移
    L.elem[i-1]=e;//将新元素e放入第i个位置
    ++L.length;//表长+1
    return 1;
}
```

> 插入算法的时间复杂度
>
> 算法时间主要耗费在移动元素的操作上
>
> 要考虑在任意位置插入（共n+1种可能）的平均移动次数
>
> <img src="Data Structures & Algorithm.assets\image-20230910154151907.png" alt="image-20230910154151907" style="zoom:67%;" />
>
> <img src="Data Structures & Algorithm.assets\image-20230910155655223.png" alt="image-20230910155655223" style="zoom:67%;" />

#### 删除

​		删除顺序表第 i 个位置上的数据元素使长度为 n 的顺序表变为长度为 n-1 的顺序表

<img src="Data Structures & Algorithm.assets\image-20230910154340280.png" alt="image-20230910154340280" style="zoom:67%;" />

删除第 4 个数据元素，移动 6 - 4 次

删除第i个数据元素，移动 n - i 次

```c++
bool ListDelete(SqList& L,int i){//删除第i个元素
    if(i<1||i>L.length)
        return 0;//判断i值是否合法
    for(int j=i;j<=L.length-1;j++)
        L.elem[j-1]=L.elem[j];//插入位置以及之后的元素后移
    --L.length;
    return 1;
}
```

> 删除算法的时间复杂度
>
> 算法时间主要耗费在移动元素的操作上
>
> 要考虑在任意位置删除（共n种可能）的平均移动次数
>
> <img src="Data Structures & Algorithm.assets\image-20230910155548396.png" alt="image-20230910155548396" style="zoom:67%;" />
>
> <img src="Data Structures & Algorithm.assets\image-20230910155648885.png" alt="image-20230910155648885" style="zoom:67%;" />

Eg：已知一个长度为n的顺序表L，请写算法将表中所有值为item的数据元素进行删除，要求算法的时间复杂度为0(n)、空间复杂度为0(1)

```c++
void Delete(SqList & L,int item){
    for(int i=0;i<L.length;i++){
        if(L.elem[i]==item){//查找值为item的数据元素
            ListDelete(L,i+1);//删除第i个数据元素
            i=i-1;
        }
    }
}
```

### 2.3 线性表的链式表示和实现

​		**链式存储（链表）**

​		线性表中的数据元素存储在任意存储单元中。

<img src="Data Structures & Algorithm.assets\image-20230912092719745.png" alt="image-20230912092719745" style="zoom:67%;" />

- 结点：数据元素的存储映像。由数据域和指针域两部分组成
- 链表： n 个结点组成一个链表，是线性表的链式存储结构
- 链表: 构成链表的结点中仅包含一个指针域

> 单链表时非随机的存储结构，要取得第i个数据就得从头指针出发链表进行查找

```c++
typedef struct LNode {
	ElemType data;//数据域
	struct LNode* next;//指针域
} LNode, * LinkList;
```

>- `typedef struct LNode { ... } LNode, * LinkList;` 这段代码中的 `typedef` 则是用来为 `struct LNode` 与`struct LNode*` 创建类型别名。
>
>1. `LNode`：将 `struct LNode` 作为类型别名，可以直接使用 `LNode` 来声明结构体变量。
>2. `LinkList`：将 `struct LNode*` 作为类型别名，可以直接使用 `LinkList` 来声明指向结构体 `LNode` 的指针变量。
>
>- `struct LNode*`是一个数据类型，表示指向结构体 `LNode` 的指针类型。

Eg：

<img src="Data Structures & Algorithm.assets\image-20230912095757217.png" alt="image-20230912095757217" style="zoom:67%;" />

> ​		首元结点是指链表中存储第一个数据元素的结点。
>
> ​		头结点附设在首元结点前，指针域指向首元结点，数据域可以不存信息，或者存与数据元素类型相同的其他信息。

```c++
	LinkList A, B, C, D;//一般习惯用LinkList定义链表
	A.next = &B;
	B.next = &C;
	C.next = &D;
	D.next = NULL;
	LNode H;//定义头指针
	H.next = &A;
	LNode* L; L = &H;
```

### 2.4 创建单链表

#### 前插法创建单链表

```c++
void CreateList_H(Linklist& L,int n) {//L为链表的指针，n为数据的个数
	LNode* p;
	//创建一个空表
	L = new LNode;//new关键字用于申请存储空间，返回值是一个指向该存储空间的指针
	L->next = NULL;
	for (int i = n; i > 0; i--) {
		p = new LNode;//又用new关键字申请了一段存储空间
		//生成新结点
		cin >> p->data;
		//前插
		p->next = L->next;
		L->next = p;
	}
}
```

> new关键字用于申请一段新的内存空间

#### 后插法创建单链表

```c++
void CreateList_R(LinkList& L, int n) {
    //初始化L
    L = new LNode;
	L->next = NULL;//L是头指针，L->next是第一个元素的地址
	LNode* p;//定义一个新的结点
	LNode* r = L;//创建尾指针
	for (int i = 0; i < n; i++) {
		p = new LNode;//为新结点分配内存空间，并把分配到的内存空间的地址传递给p指针
		//给新的结点传入数据
		cin >> p->data;
		p->next = NULL;
		r->next = p;//将新的结点插入到链表的尾部
		r = p;//更新尾指针
	}
}
```



### 2.5 单链表的基本操作

#### 初始化

​		构造一个仅包括头结点的空表

```c++
bool InitList(LinkList& L) {//把头指针传入函数，形参为指向LinkList类型的指针的引用
	L = new LNode;//生成新的结点作为头结点，用头指针L指向头结点
	L->next = NULL;//头结点的指针域置空
	return 1;
}
```

> 两行，不如直接在main函数里面实现。

#### 取值

​		获取链表中第i个数据元素的内容

```c++
bool GetElem(LinkList L,int i,int& e) {
	LinkList p = L->next;//设置临时变量p，指向首元结点
	int j = 1;//设置计数器临时变量j，并初始化为1
	while (j < i && p){//通过循环，查找第i个结点的位置
		p = p->next;
		++j;
	}
	if (p == NULL || i < 1)return 0;//判断i的合法性
	e = p->data;//取出第i个数据元素的内容
	return 1;
}
```

> <img src="Data Structures & Algorithm.assets\image-20230913201739348.png" alt="image-20230913201739348" style="zoom:80%;" />
>
> T(n)=O(n)



#### 查找

​		根据数据元素的内容获取数据元素所在的位置

```c++
LNode* LocateElem(LinkList L, int e) {
	LNode* p = L->next;//从首元结点开始查找
	while (p->data != e && p) {
		p = p->next;
	}
	return p;
}
```

><img src="Data Structures & Algorithm.assets\image-20230913201739348.png" alt="image-20230913201739348" style="zoom:80%;" />
>
>T(n)=O(n)



#### 插入

​		将新的数据元素插入到第i个数据元素之前

<img src="Data Structures & Algorithm.assets\image-20230913203445582.png" alt="image-20230913203445582" style="zoom:80%;" />

```c++
bool ListInsert(LinkList& L, int i, int e) {
	LNode* p = L;
	int j = 0;
	while (p && j < i - 1) {//找到要插入节点的上一个结点
		p = p->next; 
		++j;
	}
	LNode* s = new LNode;
	s->data = e;
	if (p == NULL || i < 1) return 0;//判断i值的合法性
	s->next = p->next;//插入操作
	p->next = s;
	return 1;
}
```



#### 删除

​		删除单链表中第i个数据元素

```c++
bool ListDelete(LinkList& L, int i) {
	LNode* p = L;//从头结点开始
	int j = 0;
	while (p->next && j < i - 1) {
		p = p->next;
		++j;
	}
	if (!(p->next) || i < 1)return 0;
	LNode* q = p->next;
	p->next = q->next;
	q->next = NULL;
	delete q;
	return 1;
}
```

#### 数组从大到小存入链表

```c++
bool ListInsertArr(int arr[], int n, LinkList& L) {
	LNode* p = NULL;//新的节点
	LNode* j = L->next; // j指向首元节点
	LNode* Prij = L; // Prij指向j的前一个节点
	for (int i = 0; i < n; i++) {
		p = new LNode;
		p->data = arr[i];
		p->next = NULL;
		j = L->next;
		Prij = L;
		while (j != NULL && p->data < j->data) { // j指向的节点非空
			Prij = j;
			j = j->next;
		}
		Prij->next = p; // 将p节点插入到链表中
		p->next = j; // 将j节点接到p节点的后面
	}
	return 1;
}
```



<img src="Data Structures & Algorithm.assets\image-20230914105217836.png" alt="image-20230914105217836" style="zoom:67%;" />



### 2.6 循环链表

​		循环链表(Circular Linked List)是另一种形式的链式存储结构。其特点是表中最后一个结点的指针域指向头指针，整个链表形成一个环。**由此，从表中任一结点出发均可以找到表中其他结点。**

> 由于循环链表中没有 NULL 指针，故涉及遍历操作时，其终止条件就不再像非循环链表那样判断 p 或p->next 是否为空，而是判断它们是否等于头指针



### 2.7 双向链表

​		以上讨论的链式存储结构的结点中只有一个指示直接后继的指针域，由此，从某个结点出发只能顺指针向后寻查其他结点。若要寻查结点的直接前驱，则必须从表头指针出发。换句话说，在单链表中，查找直接后继的执行时间为0(1)，而查找直接前驱的执行时间为0(n)。为克服单链表这种单向性的缺点，可利用双向链表 (Double Linked List)。
​		顾名思义，在双向链表的结点中有两个指针域，一个指向直接后继，另一个指向直接前驱。

```c++
typedef struct DuLNode {
	ElemType data;
	struct DuLNode* prior;//指向直接前驱
	struct DuLNode* next;//指向直接后驱
}DuLNode, * DuLinkList;
```



### 2.8 顺序表与链表的比较

<img src="Data Structures & Algorithm.assets\image-20230914105352819.png" alt="image-20230914105352819" style="zoom:67%;" />





## 第三章 栈和队列

### 3.1 定义和特点

- 栈和队列是两种常用的、重要的数据结构
- 栈和队列是限定插入和删除只能在表的“端点”进行的**线性表**

> 1. 栈插入只能插入在表尾，删除也只能删除表尾的元素。——后进先出(Last In First Out,LIFO)，相当于叠盘子
>
> 由于栈的操作具有后进先出的固有特性，使得栈成为程序设计中的有用的工具。另外，如果问题求解的过程具有”后进先出”的天然特性的话，则求解的算法中也必然需要利用“栈”。
>
> 2. 队列插入只能插入在表尾，删除只能删除表头的元素。——先进先出
>
> 由于队列的操作具有先进先出的特性，使得队列成为程序设计中解决类似问题排队问题的有用工具。



#### 栈的定义和特点

​		栈（stack）是一种后进先出（Last In First Out----LIFO）的线性表。栈是仅在表尾进行插入、删除操作的线性表。表尾(即an端)称为栈顶 (Top)；表头(即a1端)称为栈底(Base)

​		插入元素到栈顶（即表尾）的操作，称为入栈从栈顶（即表尾），删除最后一个元素的操作，称为出栈

> ”入“=压入=PUSH；”出“=弹出=POP
>
> 由于栈本身是线性表，所以栈也有顺序存储和链式存储两种实现方式：
>
> - 顺序存储：顺序栈
> - 链式存储：链栈



#### 队列的定义和特点

​		队列(queue)是一种先进先出(Frist In Frist Out ----FIFO)的线性表。在表一端插入 (表尾) ，在另一端(表头)删除



### 3.2 栈抽象数据类型定义

<img src="Data Structures & Algorithm.assets\image-20230919202334376.png" alt="image-20230919202334376" style="zoom:67%;" />

> <img src="Data Structures & Algorithm.assets\image-20230919205310598.png" alt="image-20230919205310598" style="zoom:67%;" />



### 3.3 栈的基本操作

#### 顺序栈的表示

```c++
typedef struct {
	SElemType* base;//栈底指针
	SElemType* top;//栈顶指针
	int stacksize;//栈可用最大容量
}SqStack;
```

#### 顺序栈的初始化

```c++
int InitStack(SqStack& S) {
	S.base = new SElemType[MAXSIZE];
	if (!S.base)return 0;//存储分配失败
	//或者：
	//S.base=(SElemType*)malloc(MAXSIZE*sizeof(SElemType));
	S.top = S.base;
	S.stacksize = MAXSIZE;
	return 1;
}
```

#### 求顺序栈长度

```c++
int StackLength(SqStack S) {
	return S.top - S.base;
}
```

#### 清空顺序栈

```c++
bool ClearStack(SqStack S) {
	if (S.base)S.top = S.base;
	return 1;
}
```

#### 销毁顺序栈

```c++
bool DestroyStack(SqStack& S) {
	if (S.base) {
		delete S.base;
		S.stacksize = 0;
		S.base = S.top = NULL;
	}
	return 1;
}
```

#### 顺序栈的入栈

```c++
bool Push(SqStack& S, SElemType e) {
	if (S.top - S.base == S.stacksize)return 0;//先判断栈是否已满
	*(S.top) = e;//元素e压入栈顶
	S.top++;//栈顶指针+1
    return 1;
}
```

#### 顺序栈的出栈

```c++
bool Pop(SqStack& S, SElemType& e) {
	if (S.top == S.base)return 0;//先判断是否为栈空
	--S.top;
	e = *(S.top);
	return 1;
}
```

#### 链栈的表示

![image-20231017164438468](Data Structures & Algorithm.assets\image-20231017164438468.png)

> 注意链栈中指针的方向——栈顶指向栈底

```c++
typedef struct StackNode {
	SElemType data;
	struct StackNode* next;
}StackNode, * LinkStack;
```

>- 链表的头指针就是栈顶
>- 不需要头结点
>- 基本不存在栈满的情况
>- 空栈相当于头指针指向空插入和删除仅在栈顶处执行

#### 链栈的初始化

```c++
void InitStack(LinkStack& S) {
	//构造一个空栈，栈顶指针置为空
	S = NULL;
}
```

#### 链栈的入栈

```c++
bool Push(LinkStack& S, SElemType e) {
	StackNode* p = new StackNode;
	p->data = e;
	p->next = S;//新结点插入栈顶
	S = p;//修改栈顶指针
	return 1;
}
```

#### 链栈的出栈

```c++
int Pop(LinkStack& S, SElemType& e) {
	if (S == NULL)return 0;//空栈无法再出栈
	e = S->data;
	StackNode* p;
	p = S;//为了改变S的指向后可以把要出栈的节点删去
	S = S->next;
	delete p;
	return 1;
}
```

#### 栈与递归

递归：若一个对象部分地包含它自己，或用它自己给自己定义，则称这个对象是递归的



### 3.4 队列的基本操作

<img src="Data Structures & Algorithm.assets\image-20230922113348432.png" alt="image-20230922113348432" style="zoom:67%;" />

#### 顺序队列的表示

```c++
typedef struct {
	QElemType* base;//初始化的动态分配存储空间
	int front;//头指针
	int rear;//尾指针
}SqQueue;
```

#### 队列的初始化

```c++
bool InitQueue(SqQueue& Q) {
	Q.base = new QElemType[MAXQSIZE];//分配数组空间
	if (!Q.base)return 0;//存储分配失败
	Q.front = Q.rear = 0;//头指针尾指针为0，队列为空
	return 1;
}
```

#### 求队列长度

```c++
int QueueLength(SqQueue Q) {
	return Q.rear - Q.front;
}
```

#### 循环队列入队

> 解决假上溢的方法：base[0]接在base[MAXQSIZE-1]之后
>
> 实现方法：模运算

```c++
bool EnQueue(SqQueue& Q, QElemType e) {
	if ((Q.rear + 1) % MAXQSIZE == Q.front)return 0;//队列已满（牺牲一个空间，最后一个空间不用），返回错误
	Q.base[Q.rear] = e;//新元素加入队尾
	Q.rear = (Q.rear + 1) % MAXQSIZE;//队尾指针加1
	return 1;
}
```

#### 循环队列出队

```c++
bool Dequeue(SqQueue& Q, QElemType& e) {
	if (Q.front == Q.rear)return 0;//队空，错误
	e = Q.base[Q.front];
	Q.front = (Q.front + 1) % MAXQSIZE;//队头指针加1
	return 1;
}
```

#### 链队的表示

​		若用户无法估计所用队列的长度，则宜采用链队列

```c++
typedef struct QNode {
	QElemType data;
	struct QNode* next;
}QNode, * QueuePtr;

typedef struct {
	QueuePtr front;//队头指针
	QueuePtr rear;//队尾指针
}LinkQueue;
```

> 链队列中，每一个节点用`QNode`表示，每一个`QNode`节点均有一个数据域和指针域。对于整个链队列，还有一个头指针`front`和一个尾指针`rear`，这两个指针用LinkQueue封装。

<img src="Data Structures & Algorithm.assets\image-20230923101351716.png" alt="image-20230923101351716" style="zoom:67%;" />

#### 链队列的初始化

```c++
bool InitQueue(LinkQueue& Q) {
	Q.front = Q.rear = new QNode;//再内存中为空节点开辟一段空间，地址赋值给front与rear
	if (!Q.front)return 0;
	Q.front->next = NULL;//Q.front相当于指向链表头结点的指针
	return 1;
}
```

#### 销毁链队列

```c++
bool DestroyQueue(LinkQueue& Q) {
	while (Q.front) {
		QNode* p = Q.front->next;
		delete Q.front;
		Q.front = p;
	}
	return 1;
}
```

#### 链队列入队

<img src="Data Structures & Algorithm.assets\image-20230923103515741.png" alt="image-20230923103515741" style="zoom:67%;" />

```c++
bool EnQueue(LinkQueue& Q, QElemType e) {
	QNode* p = new QNode;
	if (!p)return 0;
	p->data = e;
	p->next = NULL;
	Q.rear->next = p;//尾指针指向的节点的next域改为p的地址
	Q.rear = p;
	return 1;
}
```

#### 链队列出队

<img src="Data Structures & Algorithm.assets\image-20230923104242129.png" alt="image-20230923104242129" style="zoom:67%;" />

```c++
bool DeQueue(LinkQueue& Q, QElemType& e) {
	if (Q.front == Q.rear)return 0;//队空，返回错误
	QNode* p = Q.front->next;
	e = p->data;
	Q.front = p->next;
	if (Q.rear == p)Q.rear = Q.front;
	delete p;
	return 1;
}
```



## 第五章 树和二叉树

### 5.1 定义

#### 树的定义

​		**树(Tree) 是 n (n≥0)个结点的有限集。**

- 若 n = 0，称为空树；
- 若 n >0，则它满足如下两个条件：
  - 有且仅有一个特定的称为根(Root) 的结点
  - 其余结点可分为 m (m≥0) 个互不相交的有限集 T1, T2, T3,....Tm，其中每一个集合本身又是一棵树，并称为根的子树(SubTree)。

<img src="Data Structures & Algorithm.assets\image-20231017151147943.png" alt="image-20231017151147943" style="zoom:87%;" />



相关术语：

- 根结点：非空树中无前驱结点的结点
- 结点的度：结点拥有的子树数

> 例如上图中根结点A的度数为3，B结点的度数为2

- 树的度：树内各结点的度的最大值

> 例如上图，树的度为3

- 树的深度：树中结点的最大层次

- 终端结点：叶子，度数为0
- 分支结点：非终端节点，度数≠0
- 内部结点：根结点以外的分支结点
- 孩子：结点的子树的根称为该结点的孩子，该结点称为孩子的**双亲**
- 兄弟：拥有共同双亲的节点称为兄弟
- 堂兄弟：双亲在同一层的节点
- 祖先：从根节点到该节点所经分支上的所有节点
- 子孙：以该节点为根的子树的任意节点

![image-20231017152843647](Data Structures & Algorithm.assets\image-20231017152843647.png)



More：

- 有序树：树中结点的各子树从左至右有次序(最左边的为第一个孩子)
- 无序树：树中结点的各子树无次序
- 森林：m(m≥0)棵互不相交的树的集合

> 一棵树可以看成一个特殊的森林



#### 二叉树的定义

​		二叉树是 n（n≥0） 个结点的有限集，它或者是空集 (n = 0)或者由一个根结点及两棵互不相交的分别称作这个根的左子树和右子树的二又树组成。

​		为何要重点研究每结点最多只有两个“叉” 的树?

- 二又树的结构最简单，规律性最强
- 可以证明，所有树都能转为唯一对应的二叉树，不失一般性
- 普通树 (多叉树）若不转化为二叉树，则运算很难实现

特点：

- 每个结点最多有俩孩子（二叉树中不存在度大于 2的结点）
- 子树有左右之分，其次序不能颠倒
- 二又树可以是空集合，根可以有空的左子树或空的右子树

> 二叉树不是树的特殊情况，是两个不相同的概念
>
> 二叉树结点的子树要区分左子树和右子树，即使只有一棵子树也要区分，说明它是左子树，还是右子树。
>
> 树当结点只有一个孩子时，就无须区分它是左还是右的次序。
>
> 因此二者是不同的。这是二又树与树的最主要的差别。



### 5.2 两种特殊的二叉树

- 满二叉树
- 完全二叉树

> 为什么要研究这两种特殊形式？
>
> 因为它们在顺序存储方式下可以复原。



#### 满二叉树

​	深度为k的二叉树且有 (2^k - 1)个结点（每一层的结点都是满的）

> 特点：
>
> - 每一层上的结点数都是最大结点数 (即每层都满)
> - 叶子节点全部在最底层
>
> 对满二叉树结点位置进行编号编号规则：
>
> 从根结点开始，自上而下，自左而右。每一结点位置都有元素。



#### 完全二叉树

​		深度为k的具有n个结点的二叉树，当且仅当其每一个结点都与深度为k的满二又树中编号为1~n 的结点对

应时，称之为完全二叉树。

![image-20231018185348584](Data Structures & Algorithm.assets\image-20231018185348584.png)

> 满二叉树一定是完全二叉树



### 5.3 二叉树的性质

性质 1：在二叉树的第 i 层上至多有 2^（i-1）个结点

性质 2：深度为k的二叉树至多有 2^k - 1个结点 (k＞1)

性质3：对任何一棵二叉树T如果其叶子数为 n0，度为2的结点数为 n2，则 n0= n2+ 1

<img src="Data Structures & Algorithm.assets\image-20231018190005739.png" alt="image-20231018190005739" style="zoom:80%;" />

> 性质4表明了完全二叉树结点数n与完全二叉树深度k之间的关系

性质5：对于一颗完全二叉树的每一个结点，假设结点的编号为i，左孩子的编号为2i，右孩子的编号为2i+1（根结点从1开始）

> 也有可能左孩子的编号为(i+1)*2-1，右孩子编号为(i+1) * 2（根结点从0开始）



### 5.4 二叉树的存储结构

- 顺序存储结构
- 链式存储结构
  - 二叉链表
  - 三叉链表

#### 顺序存储

​	按满二叉树的结点层次编号，依次存放二叉树中的数据元素。

![image-20231018193129656](Data Structures & Algorithm.assets\image-20231018193129656.png)

```c++
//二叉树顺序存储表示
#define MAXSIZE 100
#define TElemType int
typedef TElemType SqBiTree[MAXSIZE]
SqBiTree bt;
```

缺点：存储密度可能过低

最坏情况：深度为k的且只有k个结点的单支树需要长度为2^k-1的一维数组

<img src="Data Structures & Algorithm.assets\image-20231018193453516.png" alt="image-20231018193453516" style="zoom:67%;" />

> 存储这个树至少需要一个长度为7的一维数组：
>
> 1	0	2	0	0	0	3

特点：结点间关系蕴含在其存储位置中。但是浪费空间，适于存满二叉树和完全二叉树

#### 链式存储

##### 二叉链表

<img src="Data Structures & Algorithm.assets\image-20231018201602220.png" alt="image-20231018201602220" style="zoom:80%;" />

```c++
typedef struct BiTNode {
	TElemType data;//数据本身
	struct BiTNode* lchild, * rchild;//左右孩子指针
}BiTNode, * BiTree;//别名
```

> 在n个结点的二又链表中，有 n+1个空指针域
>
> 分析：
>
> 必有2n个链域。除根结点外每个结点有且仅有一个双亲，所以只会有n - 1个结点的链域存放指针，指向非空子女结点。
>
> 所以，空指针的数目=2n-(n-1)=n+1

##### 三叉链表

<img src="Data Structures & Algorithm.assets\image-20231018203246016.png" alt="image-20231018203246016" style="zoom:67%;" />

```c++
typedef struct TriTNode {
	TElemType data;//数据本身
	struct TriTNode* lchild, * parent, * rchild;//左右孩子，以及双亲指针
}TriTNode, * TriTree;//别名
```



### 5.5 遍历二叉树

- 遍历定义：顺着某一条搜索路径巡访二叉树中的结点，使得每个结点均被访问一次，而且仅被访问一次 (又称周游）

> “访问”的含义很广，可以是对结点作各种处理，如： 输出结点的信息、修改结点的数据值等，但要求这种访问不破坏原来的数据结构。

- 遍历目的：得到树中所有结点的一个线性排列
- 遍历用途：它是树结构插入、删除、修改、查找和排序运算的前提，是二叉树一切运算的基础和核心。



遍历二叉树有三种情况（规定先访问左子树再访问右子树）

- DLR——先（根）序遍历
- LDR——中（根）序遍历
- LRD——后（根）序遍历

<img src="Data Structures & Algorithm.assets\image-20231019143105010.png" alt="image-20231019143105010" style="zoom:80%;" />

> 递归的操作



#### 根据遍历序列确定二叉树

​		若二叉树中各结点的值均不相同，则二叉树结点的先序序列、中序序列和后列序都是唯一的。

​		由二叉树的先序序列和中序序列，或由二叉树的后序序列和中序序列可以确定唯一一棵二又树。

> 一定要知道中序

- 已知先序和中序

<img src="Data Structures & Algorithm.assets\image-20231019151137167.png" alt="image-20231019151137167" style="zoom:80%;" />

​									2、再对左子树CDBFE做出同样的操作，找到左子树CDBFE的根为B，B的左边是CD，B的右边是FE······

​									3、以此类推



#### 递归遍历的算法实现

- 先序遍历

```c++
void PreOrderTraverse(BiTree T) {
	if (T == NULL)return;
	else {
		visit(T);//访问根结点
		PreOrderTraverse(T->lchild);//递归遍历左子树
		PreOrderTraverse(T->rchild);//递归遍历右子树
	}
}
```

- 中序遍历

```c++
void InOrderTraverse(BiTree T) {
	if (T == NULL)return;
	else {
		InOrderTraverse(T->lchild);//递归遍历左子树
		visit(T);//访问根结点
		InOrderTraverse(T->rchild);//递归遍历右子树
	}
}
```

- 后续遍历

```c++
int PostOrderTraverse(BiTree T) {
	if (T == NULL)return;
	else {
		PostOrderTraverse(T->lchild);//递归遍历左子树
		PostOrderTraverse(T->rchild);//递归遍历右子树
		visit(T);//访问根结点
	}
}
```

> 不难看出，如果去掉输出语句，从递归的角度看，三种算法是完全相同的，或说这三种算法的访问路径是相同的，只是访问结点的时机不同

<img src="Data Structures & Algorithm.assets\image-20231019160154445.png" alt="image-20231019160154445" style="zoom:67%;" />

> 从虚线的出发点到终点的路径上，每个结点经过3次。
>
> - 第1次经过时访问=先序遍历
> - 第2次经过时访问=中序遍历
> - 第3次经过时访问=后序遍历

遍历算法的时间复杂度：O(n)	//每个结点仅访问一次

遍历算法的空间复杂度：O(n)	//栈占用的最大的辅助空间



#### 中序遍历非递归算法

基本思想：

(1)建立一个栈

(2) 根结点进栈，遍历左子树

(3)根结点出栈，输出根结点，遍历右子树

```c++
bool InOrderTraverse(BiTree T) {
	BiTree p;
	InitStack(S);
	p = T;
	while (p || StackEmpty(S)) {
		if (p) {
			Push(S, p);//根结点入栈
			p = p->lchild;//指针指向左子树
		}
		else {
			Pop(S, q);//栈顶元素出栈
			cout << q->data << " ";//输出栈顶元素（根结点）
			p = q->rchild;            
		}
	}
	return 1;
}
```



#### 层次遍历

​		对于一颗二叉树，从根结点开始，按从上到下、从左到右的顺序访问每一个结点。

​		每一个结点仅仅访问一次。

算法设计思路：使用一个队列

1. 将根结点进队

2. 队不空时循环：

    从队列中出列一个结点*p，访问它
      	 	若它有左孩子结点，将左孩子结点进队
      		 若它有右孩子结点，将右孩子结点进队

```c++
bool LevelOrder(BiTree T) {
	BiTree p;//声明一个二叉树的指针
	SqQueue qu;
	InitQueue(qu);//初始化队列
	enQueue(qu, T->data);//根结点进入队列
	while (!QueneEmpty(qu)) {//队列不为空
		deQueue(qu, q);//队头元素出队
		cout << p->data << " ";
		if (p->lchild != NULL)
			enQueue(qu, p->lchild);//如果出队的那个结点有左孩子，左孩子入队
		if (p->rchild != NULL)
			enQueue(qu, p->rchild);//如果出队的那个结点有右孩子，右孩子入队
	}
}
```



### 5.6 建立二叉树

```c++
bool CreateBiTree(BiTree& T) {
	char ch;
	cin >> ch;
	if (ch == '#')T = NULL;
	else {
		T = new BiTNode;//为T分配一段内存，地址返回给T
		if (!T)return 0;//分配失败，return 0
		T->data = ch;//生成根结点
        T->lchild=NULL;
        T->rchild=NULL;
		CreateBiTree(T->lchild);//构造左子树
		CreateBiTree(T->rchild);//构造右子树
	}
	return 1;
}
```



### 5.7 复制二叉树

```c++
bool CopyTree(BiTree T, BiTree& NewT) {
	if (T == NULL) {
		NewT = NULL;
		return 0;
	}
	else {
		NewT = new BiTNode;
		NewT->data = T->data;
		CopyTree(T->lchild, NewT->lchild);
		CopyTree(T->rchild, NewT->rchild);
	}
}
```



### 5.8 计算二叉树的深度

​		如果是空树，则深度为0。
​		否则，递归计算左子树的深度记为m，递归计算右子树的深度记为n，二叉树的深度则为m与n的较大者加1。

```c++
int Depth(BiTree T) {
	int m = 0;
	int n = 0;
	if (T == NULL)
		return 0;//空树返回0
	else {
		m = Depth(T->lchild);
		n = Depth(T->rchild);
		if (m > n)return m + 1;
		else return n + 1;
	}
}
```



### 5.9 计算二叉树结点总数

​		如果是空树，则结点个数为0；

​		否则，结点个数为左子树的结点个数+右子树的结点个数再+1

```c++
int NodeConut(BiTree T) {
	if (T == NULL)
		return 0;//空树返回0
	else {
		return NodeConut(T->lchild) + NodeConut(T->rchild) + 1;
	}
}
```



### 5.10 计算二叉树叶子结点数

​		如果是空树，则叶子结点个数为0；

​		否则，为左子树的叶子结点个数+右子树的叶子结点个数

```c++
int LeafCount(BiTree T) {
	if (T == NULL)
		return 0;//空树返回0
	if (T->lchild == NULL && T->rchild == NULL)
			return 1;//如果是叶子，返回1
	else
		return LeafCount(T->lchild) + LeafCount(T->rchild);
}
```



### 5.11 线索二叉树

​		当用二叉链表作为二叉树的存储结构时可以很方便地找到某个结点的左右孩子；但一般情况下，无法直接找到该结点在某种遍历序列中的前驱和后继结点

​	解决的方法：

1. 通过遍历寻找——费时间
2. 再增设前驱、后继指针域——增加了存储负担
3. **利用二叉链表中的空指针域**

> 二叉树链表中空指针域的数量：
> 具有 n 个结点的二叉链表中，一共有 2n 个指针域。因为 n 个结点中有n-1个孩子，即 2n个指针域中，有n-1个用来指示结点的左右孩子，其余n+1 个指针域为空

​		利用二叉链表中的空指针域：
​		如果某个结点的左孩子为空，则将空的左孩子指针域改为指向其前驱；如果某结点的右孩子为空，则将空的右孩子指针域改为指向其后继。这种改变指向的指针称为线索。加上了线索的二叉树称为线索二叉树 (Threaded Binary Tree)

​		对二叉树按某种遍历次序使其变为线索二叉树的过程叫**线索化**。

Example：

![image-20231020160957910](Data Structures & Algorithm.assets\image-20231020160957910.png)

​		为区分`Irchid`和`rchild`指针到底是指向孩子的指针，还是指向前驱或后继的指针，对二叉链表中每个结点增设两个标志域 ltag 和 rtag ，并约定：

- ltag==0		Ichild指向该结点的左孩子
- ltag==1		Ichild指向该结点的前驱
- rtag==0		Ichild指向该结点的右孩子
- rtag==1		Ichild指向该结点的后继

```c++
typedef struct BiThrNode {
	TElemType data;
	int ltag, rtag;
	struct BiThrNode* lchild, * rchild;
}BiThrNode, * BiThrTree;
```



**先序线索二叉树**

![image-20231020162853296](Data Structures & Algorithm.assets\image-20231020162853296.png)

> 中序、后序同理



​	上图存储E的结点的右孩子为空，但在序列中他是最后一个元素，没有后继结点，那么E的rchild就空了。为了避免这种指针悬空的情况，增设了一个头结点，这个头结点的ltag=0，Ichild指向根结点rtag=1，rchild指向遍历序列中最后一个结点遍历序列中第一个结点的lc域和最后一个结点的rc域都指向头结点

<img src="Data Structures & Algorithm.assets\image-20231020162813536.png" alt="image-20231020162813536" style="zoom:67%;" />



### 5.12 树的存储结构

#### 双亲表示法

实现：定义结构数组存放树的结点。每个结点含两个域——数据域以及双亲域

​		数据域：存放结点本身的信息

 		双亲域：指示本结点的双亲结点在数组中的位置。

> 特点：找双亲容易找孩子难

<img src="Data Structures & Algorithm.assets\image-20231026143427959.png" alt="image-20231026143427959" style="zoom:67%;" />

```c++
typedef struct PTNode {
	TElemType data;
	int parent;//双亲位置域
};

typedef struct {
	PTNode nodes[MAX_TREE_SIZE];
	int r, n;//r表示根结点的位置，n表示结点的个数
}PTree;
```



#### 孩子链表

把每个结点的孩子结点排列起来，看成是一个线性表，用单链表存储。

则n个结点有n个孩子链表(叶子的孩子链表为空表)。而n个头指针又组成一个线性表，用顺序表（含n个元素的结构数组）存储。

![image-20231026144144930](Data Structures & Algorithm.assets\image-20231026144144930.png)

> 找孩子容易，找双亲难



```c++
typedef struct {
	int child;
	struct CTNode* next;
}CTNode, * ChildPtr;

typedef struct {
	TElemType data;
	ChildPtr firstchild;//孩子链表头指针
}CTBox;

typedef struct {
	CTBox nodes[MAX_TREE_SIZE];
	int r, n;
}CTree;
```



#### 带双亲的孩子链表

![image-20231026144740827](Data Structures & Algorithm.assets\image-20231026144740827.png)

> 在孩子链表的`CTNode`的定义中加上`int parent;`即可



#### 孩子兄弟表示法

> 又称为二叉树表示法、二叉链表表示法

实现：用二又链表作树的存储结构，链表中每个结点的两个指针域分别指向其第一个孩子结点和下一个兄弟结点

![image-20231026145820222](Data Structures & Algorithm.assets\image-20231026145820222.png)

> 找双亲困难

```c++
typedef struct {
	TElemType data;
	struct CSNode* firstchild, * nextsibling;
}CSNode, * CSTree;
```



### 5.13 树与二叉树的转换

- 将树转化为二叉树进行处理，利用二叉树的算法来实现对树的操作
- 由树和二叉树都可以用二又链表作存储结构，则以二叉链表作媒介可以导出树与二叉树之间的一个对应关系

![image-20231026151818586](Data Structures & Algorithm.assets\image-20231026151818586.png)



- 将树转为二叉树

​		结点的兄弟改为右孩子，孩子改为左孩子

- 将二叉树转为树

​		结点的左孩子改为孩子，结点的右孩子改为兄弟



### 5.14 森林与二叉树的转换

1. 将各棵树分别转换成二叉树
2. 将每棵树的根结点用线相连
3. 以第一棵树根结点为二叉树的根，再以根结点为轴心，顺时针旋转构成二叉树型结构

![image-20231026152513154](Data Structures & Algorithm.assets\image-20231026152513154.png)



### 5.15 树的遍历

#### 先根遍历

​		若树不空，则先访问根结点，然后依次先根遍历各棵子树。

#### 后根遍历

​		若树不空，则先依次后根遍历各棵子树，然后访问根结点。

#### 按层次遍历

​		若树不空，则自上而下自左至右访问树中每个结点



### 5.16 森林的遍历

#### 先序遍历

若森林不空，则：

1. 访问森林中第一棵树的根结点；
2. 先序遍历森林中第一棵树的子树森林;
3. 先序遍历森林中（除第一棵树之外）其余树构成的森林。

> 即从左到右对森林中的每一棵树进行先根遍历

#### 中序遍历

若森林不空，则：

1. 中序遍历森林中第一棵树的子树森林;
2. 访问森林中第一棵树的根结点；
3. 中序遍历森林中（除第一棵树之外）其余树构成的森林。

> 即从左到右对森林中的每一棵树进行后根遍历



### 5.17 哈夫曼树（最优二叉树）

#### 基本概念

- 路径

从树中一个结点到另一个结点之间的分支构成这两个结点间的路径。

- 结点的路径的长度

两结点间路径上的分支数。

- 树的路径长度


从树根到每一个结点的路径长度之和。

> **结点数目相同的二叉树中，完全二叉树是路径长度最短的二叉树**（但是路径最短不一定是完全二叉树）

例如：

<img src="Data Structures & Algorithm.assets\image-20231030002822268.png" alt="image-20231030002822268" style="zoom:50%;" />

​		TL(b)=0+1+1+2+2+2+2+3+3=16，该树为完全二叉树，所以它是路径长度最短的二叉树。但是，当H、I接在E上时，树也是路径长度最短的树，但不是完全二叉树。

- 权

将树中结点赋给一个有着某种含义的数值，则这个数值称为该结点的权。

- 结点的带权路径长度

从根结点到该结点之间的路径长度与该结点的权的乘积。

- 树的带权路径长度

树中所有**叶子结点**的带权路径长度之和。

记作：<img src="Data Structures & Algorithm.assets\image-20231030003155003.png" alt="image-20231030003155003" style="zoom:50%;" />

WPL(Weighted Path Length)

- **哈夫曼树**

​		给定N个权值作为N个叶子结点，构造一棵**二叉树**，若该树的带权路径长度达到最小，称这样的二叉树为最优二叉树，也称为哈夫曼树(Huffman Tree)。哈夫曼树是带权路径长度最短的树，权值较大的结点离根较近。

更多地：

1. 哈夫曼树也可以是k叉的，只是在构造k叉哈夫曼树时需要先进行一些调整。（例如三叉哈夫曼树）
2. 满二叉树不一定是哈夫曼树
3. 哈夫曼树中权越大的叶子离根越近

> 贪心算法:构造哈夫曼树时首先选择权值小的叶子结点

4. 具有相同带权结点的哈夫曼树不唯一
5. 哈夫曼树的结点的度数为0或2，没有度为 1 的结点

​	例如：a、b、c、d四个叶子结点的权分别为7，5，2，4。构造最优二叉树

①<img src="Data Structures & Algorithm.assets\image-20231030003807069.png" alt="image-20231030003807069" style="zoom:40%;" />			②<img src="Data Structures & Algorithm.assets\image-20231030003851089.png" alt="image-20231030003851089" style="zoom:40%;" />		③<img src="Data Structures & Algorithm.assets\image-20231030003948583.png" alt="image-20231030003948583" style="zoom:40%;" />

WPL1=2 * 7+2 * 5+2 * 2+2 * 4=36

WPL2=1 * 7+2 * 5+2 * 3+4 * 3=35

WPL3=1 * 7+2 * 5+2 * 3+4 * 3=35

由此：图一是满二叉树，但它不是最优二叉树，所有满二叉树不一定是最优二叉树。图二图三都是最优二叉树，但是它们不一样。

#### 构造算法

哈夫曼树采用顺序存储结构——一维结构数组进行存储

```c++
// 结点类型定义
typedef struct HTNode{
	int weight;
	int parent,lch,rch;
}HTNode,*HuffmanTree;
```

哈夫曼算法（构造哈夫曼树的方法）

(1)根据n个给定的权值{w1，w2，...，wn}小构成n棵二叉树的森林F={T1，T2，...，Tn}，其中Ti只是一个带权为 wi的根结点

> 构造森林全是根

(2)在F中选取两棵根结点的权值最小的树作为左右子树，构造一棵新的二叉树，且设置新的二叉树的根结点的权值为其左右子树上根结点的权值又树之和。

> 选用两小造新树

(3)在F中删除这两棵树同时将新得到的二叉树加入森林中。

>  删除两小添新树

(4)重复(2)和(3)，直到森林中只有一棵树为止，这棵树即为哈夫曼树

> 重复2 3剩单根

​		包含n棵树的森林要经过n-1次合并才能形成哈夫曼树，共产生n-1个新结点，所以哈夫曼树一共有2n-1个结点

#### 算法的实现

1. 初始化HT [1......2n-1]：lch=rch=parent=0;

> 不用第0号元素

2. 输入初始n个叶子结点：置HT[1.....n]的weight值；

3. 进行n-1次合并，依次产生n-1个结点HT[i]，i=n+1......2n-1：

   a. 在HT[1......i-1]中选两个未被选过（从parent == 0 的结点中选）的weight最小的两个结点HT[s1]和HT[s2],s1、s2为两个最小结点下标；

   b.修改HT[s1]和HTIs21的parent值:：HT[s1].parent=i; HT[s2].parent=i;

   c. 修改新产生的HT[i]：

   HTli].weight=HT[s1].weight + HT[s2].weight ;
   HT[i].lch=s1;       HT[i]. rch=s2;

```c++
//构造哈夫曼树——哈夫曼算法
void CreateHuffmanTree(HuffmanTree HT, int n) {//n为结点的个数
	if (n <= 1)return;//错误输入
	int m = 2 * n - 1;//数组一共有2n-1个元素
	HT = new HTNode[m + 1];//创建一个长度为m+1的结构数组，不用第一个元素，其他每格都存一个结点
	for (int i = 1; i <= m; i++) {//将所有结点的左右孩子以及双亲域赋值为0
		HT[i].lchild = 0;
		HT[i].rchild = 0;
		HT[i].parent = 0;
	}
	for (int i = 1; i <= n; i++) {//输入n个元素的权
		cin >> HT[i].weight;
	}
	//初始化结束，下面开始建立哈夫曼树
	//进行n-1次合并，依次产生n-1个结点HT[i]，i=n+1......2n-1；
	for (int i = n + 1; i <= m; i++) {//合并产生n-1个结点
		Select(HT, i - 1, s1, s2);
		//在HT[k](1≤k≤i-1)中选择两个其双亲域为0且权值最小的结点,并返回它们在HT中的序号s1和s2
		HT[s1].parent = i; HT[s2].parent = i; //表示从HT中删除s1,s2
		HT[i].lchild = s1; HT[i].rchild = s2;//s1,s2分别作为i的左右孩子
		HT[i].weight = HT[s1].weight + HT[s2].weight; //i的权值为左右孩子权值之和
	}
}

//给出Select函数：
void Select(HuffmanTree HT,int n,int &s1,int &s2) {
	int minum;
	int i;
	for(i=1;i<=n;i++){//得先找到一共parent域为0的结点
		if(HT[i].parent == 0){
			minum = i;
			break;
		}
	}
    
	for(i = 1;i<=n;i++){
		if(HT[i].parent == 0){
			if(HT[i].weight<HT[minum].weight){
				minum = i;
			}
		}
	}
	s1 = minum;
    
	for(i=1;i<=n;i++){
		if(HT[i].parent == 0&& i!=s1){
			minum = i;
			break;
		}
	}
    
	for(i = 1;i<=n;i++){
		if(HT[i].parent == 0&& i!=s1){
			if(HT[minum].weight<HT[minum].weight){
				minum = i;
			}
		}
	}
	s2 = minum;
}
```

例如：有n=8，权值为W={7，19，2，6，32，3，21，10}；构造哈夫曼树

​	<img src="Data Structures & Algorithm.assets\image-20231031131912392.png" alt="image-20231031131912392" style="zoom:80%;" />						<img src="Data Structures & Algorithm.assets\image-20231031131939698.png" alt="image-20231031131939698" style="zoom:80%;" />



#### 哈夫曼编码

背景：在远程通讯中，要将待传字符转换成由二进制的字符串。

设：要传送的字符为——ABACCDA，若编码A、B、C、D为00，01，10，11

​		那么ABACCDA为000100101100

​		若将编码设计为长度不等的二进制编码，即让待传字符串中出现次数较多的字符采用尽可能短的编码，则转换的二进制字符串便可能减少。

​		若编码A、B、C、D为0，00，1，01

​		那么ABACCDA为00001101，已经大大减少了二进制字符串的长度但是0000出现了重码，0000可以翻译为AAAA、BB、ABA、BAA，有歧义。

​		关键：要设计长度不等的编码，则必须使任一字符的编码都不是另个字符的编码的前缀（任一字符的编码都不包括其他字符的编码）

> 这种编码称为前缀码

- 哈夫曼编码

1、统计字符集中每个字符在电文中出现的平均概率（越大要求编码越短）
2、利用哈夫曼树的特点：权越大的叶子离根越近；将每个字符的概率值作为权值，构造哈夫曼树。 则概率越大的结点，路径越短
3、在哈夫曼树的每个分支上标上0或1：结点的左分支标0，右分支 1，把从根到每个叶子的路径上的标号连接起来，作为该叶子代表的字符的编码

<img src="Data Structures & Algorithm.assets\image-20231031132718464.png" alt="image-20231031132718464" style="zoom:80%;" />

> 问题一：为什么哈夫曼编码能够保证是前缀编码?
>
> 因为没有一片树叶是另一片树叶的祖先，所以每个叶结点的编码就不可能是其它叶结点编码的前缀
>
> 问题二：为什么哈夫曼编码能够保证字符编码总长最短?
>
> 因为哈夫曼树的带权路径长度最短，故字符编码的总长最短

​		**哈夫曼编码是最优前缀码**

![image-20231118164328426](Data Structures & Algorithm.assets/image-20231118164328426.png)

```c++
//哈夫曼编码算法实现
void CreateHuffmanCode(HuffmanTree HT, char**& HC, int n) {
    //n是要编码的字符的个数,HC为二维字符数组
    //从叶子到根逆向求每个字符的哈夫曼编码，存储在编码表HC中
	HC = new char* [n + 1];//new了n+1个，第一个位置HC[0]不用，HC[1]为第一个字符的编码，HC[2]为第二个字符的编码
	char* cd = new char[n];
    /*这个char数组用于临时存储某一个要编码的字符的哈夫曼编码，
    *假设有n个字符要编码，那么树最高为n-1，所以数组也仅需要有n-1个位置
    *这里new了n个空间，是因为最后一格设为编码结束符\0
    */
	cd[n - 1] = '\0';//最后一位设为编码结束符\0
	for (int i = 1; i <= n; i++) {//从第一个叶子结点开始，逐个求哈夫曼编码
		int start = n - 1;//此时cd[start]='\0'
		int c = i;//c用于存储当前结点的索引
		int f = HT[i].parent;//f用来存储当前结点的双亲的索引
		while (f!=0){
            //如果当前结点的双亲非0，即不是根结点就一直循环下去。（从叶子结点开始向上回溯，直到根结点）
			--start;
			if (HT[f].lchild == c)cd[start] = '0';
			else cd[start] = '1';
			c = f;
			f = HT[f].parent;
		}
		HC[i] = new char[n - start];//为HC[i]分配合适的空间;分配空间的大小为(n-1)-start+1
		strcpy(HC[i], &cd[start]);
	}
	delete cd;//释放临时空间
}
```



## 第六章 图

### 6.1 基本概念与术语

G=(V,E)，其中V是顶点（数据元素）的有穷**非空**集合，E是边的有穷集合

> 图可以没有边但是一定有点
>
> G：Graph
>
> V：Vertex
>
> E：Edge

- 无向图

  每条边都是没有方向的

- 有向图

  每条边都是有方向的

- 完全图

  任意两个点都有边相连

  > 如果是有n个顶点的无向完全图，有n(n-)/2条边
  >
  > 如果是有n个顶点的有向完全图，有n(n-1)条边

- 稀疏图

  有很少边或弧的图 (e<nlogn)

- 稠密图

  有较多边或弧的图

- 网

  边/弧带权的图

- 邻接

  有边/弧相连的两个顶点之间的关系

  >存在(vi, vj)，则称vi和vj互为邻接点
  >存在<vi,vj>，则称vi邻接到vj， vj邻接于vi

- 关联（依附）

  边/弧与顶点之间的关系

  > 存在(vi, vj)/ <vi,vj>， 则称该边/弧关联于vi和vj

- 顶点的度

  与该顶点相关联的边的数目，记为TD(v)

  > 在有向图中，顶点的度等于该顶点的入度与出度之和。
  >
  > 顶点v的入度是以v为终点的有向边的条数记作ID(v)
  >
  > 顶点v的出度是以v为始点的有向边的条数记作OD(v)
  >
  > > 当有向图中仅1个顶点的入度为0，其余顶点的入度均为1，此时为树

- 路径

  接续的边构成的顶点序列

- 路径长度

  路径上边或弧的数目/权值之和

- 回路（环）

  第一个顶点和最后一个顶点相同的路径

- 简单路径

  除路径起点和终点可以相同外，其余顶点均不相同的路径

- 简单回路（简单环）

  除路径起点和终点相同外，其余顶点均不相同的路径

  ![image-20231101185512501](Data Structures & Algorithm.assets\image-20231101185512501.png)

- 连通图 （强连通图）

  在无 (有) 向图G=(V，{E})中，若对任何两个顶点 v、u都存在从v到u的路径，则称G是连通图 （强连通图）

- 连通分量 （强连通分量）

  无向图G的极大连通子图称为G的连通分量

- 极大连通子图

   该子图是 G 连通子图，将G 的何不在该子图中的顶点加入，子图不再连通

  

  ![image-20231101185749481](Data Structures & Algorithm.assets\image-20231101185749481.png)						![image-20231101185805293](Data Structures & Algorithm.assets\image-20231101185805293.png)

  

### 6.2 图的存储结构

#### 邻接矩阵表示法

​		建立一个顶点表 （记录各个顶点信息)和一个邻接矩阵（表示各个顶点之间关系）

![image-20231101190225029](Data Structures & Algorithm.assets\image-20231101190225029.png)

- 无向图

![image-20231101190501091](Data Structures & Algorithm.assets\image-20231101190501091.png)

> 1. 无向图的邻接矩阵是对称的
> 2. 顶点i的度=第i行（列）中1的个数
> 3. 完全图的邻接矩阵除对角线外都是1
>



- 有向图

![image-20231101190853017](Data Structures & Algorithm.assets\image-20231101190853017.png)

> 有向图的邻接矩阵可能不是对称的
>
> 顶点的出度=第i行元素之和
>
> 顶点的入度=第i列元素之和
>
> 顶点的度=第i行元素之和+第i列元素之和



- 网

![image-20231101191347652](Data Structures & Algorithm.assets\image-20231101191347652.png)



#### 邻接矩阵表示法的优劣

好处

1. 直观、简单、好理解

2. 方便检查任意一对顶点间是否存在边

3. 方便找任一顶点的所有“邻接点” （有边直接相连的顶点）

4. 方便计算任一顶点的“度” （从该点发出的边数为“出度”，指向该点的边数为“入度”）

   无向图：对应行 （或列）非0元素的个数

   有向图：对应行非0元素的个数是“出度“，对应列非0元素的个数是”入度“

坏处：

1. 不便于增加和删除顶点

2. 浪费空间——存稀疏图 （点很多而边很少）有大量无效元素

   > 对稠密 (特别是完全图) 还是很合算的

3. 浪费时间——统计稀疏图中一共有多少条边



#### 邻接矩阵的算法实现

以无向网的邻接矩阵为例：

算法思想：
(1)输入总顶点数和总边数

(2) 依次输入点的信息存入顶点表中

(3)初始化邻接矩阵，使每个权值初始化为极大值

(4) 构造邻接矩阵

```c++
//图的声明
#define MaxInt 32767//表示极大值，即∞
#define MVNum 100//最大顶点数
typedef char VerTexType;//定义图的顶点的数据类型为char
typedef int ArcType；//定义图的边的权的数据类型为int
typedef struct {
	VerTexType vexs[MVNum];//顶点表
	ArcType arcs[MVNum][MVNum];//邻接矩阵
	int vexnum, arcnum;//图的当前顶点数与边数
}AMGraph;
```



```c++
//无向网的算法实现
//在图G中查找顶点v，存在则返回顶点表中的下标，否则返回-1
int LocateVex(AMGraph G, int v) {
	int i;
	for (i = 0; i < G.vexnum; i++)
		if (v == G.vexs[i])
			return i;
	return -1;
}

bool CreateUDN(AMGraph& G) {
	int v1, v2;//与边关联的点
	int w;//边的权值
	int x, y;//用于定位
	//采用邻接矩阵表示法，创建无向网G
	cin >> G.vexnum >> G.arcnum;//输入总顶点数、边数
	for (int i = 0; i < G.vexnum; i++)
		cin >> G.vexs[i];//依次输入各点的信息
	//初始化邻接矩阵
	for (int i = 0; i < G.vexnum; i++)
		for (int j = 0; j < G.vexnum; j++)
			G.arcs[i][j] = MaxInt;//边的权值全部置为最大值
	for (int k = 0; k < G.arcnum; k++) {//构造邻接矩阵
		cin >> v1 >> v2 >> w;
		x = LocateVex(G, v1);//函数返回顶点v1的下标
		y = LocateVex(G, v2);//函数返回顶点v2的下标
		G.arcs[x][y] = w;
		G.arcs[y][x] = w;//对称位置相同的值
	}
	return 1;
}
```

​		有向网、无向图、有向图类似

![image-20231101193843403](Data Structures & Algorithm.assets\image-20231101193843403.png)



#### 邻接表表示法（链式）

![image-20231101194534027](Data Structures & Algorithm.assets\image-20231101194534027.png)



​						![image-20231101194641766](Data Structures & Algorithm.assets\image-20231101194641766.png)								![image-20231101194659856](Data Structures & Algorithm.assets\image-20231101194659856.png)

> 如果边有权的话表结点就多一个info域用于存储权值

- 无向图

![image-20231101194929921](Data Structures & Algorithm.assets\image-20231101194929921.png)

特点：

1. 邻接表不唯一
2. 若无向图中有 n个顶点、e条边则其邻接表需 n个头结点和2e 个表结点。
3. 适宜存储稀疏图



- 有向图

![image-20231101195204529](Data Structures & Algorithm.assets\image-20231101195204529.png)



#### 邻接表特点

1. 方便找任一顶点的所有“邻接点“

2. 节约稀疏图的空间
   需要N个头指针 + 2E个结点 （每个结点至少2个域）

3. 方便计算任一顶点的“度”
   对无向图：是的
   对有向图：只能计算“出度”，需要构造“逆邻接表”（存指向自己的边）来方便计算“入度

4. 不方便检查任意一对顶点间是否存在边



#### 邻接表的算法实现

算法思想：

1. 输入总顶点数和总边数

2. 建立顶点表

   依次输入点的信息存入顶点表中

   使每个表头结点的指针域初始化为NULL

3. 创建邻接表

   依次输入每条边依附的两个顶点

   确定两个顶点的序号i和j，建立边结点

   将此边结点分别插入到vi和vj对应的两个边链表的头部
   
   > 头插法

相关定义

```c++
//定义存储边的结点
typedef struct ArcNode {
	int adjvex;//这个边指向的顶点的位置
	ArcNode* nextarc;//指向下一条边的指针
	Otherlnfo info;//和边相关的信息
};

//定义头结点的数组
typedef struct VNode{
	VerTexType data;//顶点信息
	ArcNode* firstarc;//指向第一条依附该结点的边的指针
}VNode, AdjList[MVNum];//AdjList表示邻接表类型
//AdjList v;相当于VNode v[MVNum];
//简洁但是不好理解

//定义图
typedef struct {
	AdjList vertices;
	//AdjList vertices;相当于VNode vertices[MVNum];
	//vertices是vertex的复数
	int vexnum, arcnum;//图当前的顶点数与边数
}ALGraph;
```

- 算法实现

```c++
int LocateVex(ALGraph G, int v) {
	int i;
	for (i = 0; i < G.vexnum; i++)
		if (v == G.vertices[i].data)
			return i;
	return -1;
}

bool CreateUDG(ALGraph& G) {
	cin >> G.vexnum >> G.arcnum;//输入总顶点数、总边数
	int v1, v2;
	int i, j;
	//创建顶点表，data域放入数据，firstarc域置空
	for (int i = 0; i < G.vexnum; i++) {
		cin >> G.vertices[i].data;
		G.vertices[i].firstarc = NULL;
	}
	for (int k = 0; k < G.arcnum; k++) {//输入各边，构造邻接表
		cin >> v1 >> v2;//输入一条边依附的两个顶点
		//找到这两个顶点在顶点表中的位置
		i = LocateVex(G, v1);//边的一个顶点
		j = LocateVex(G, v2);//边的另一个顶点
		ArcNode* p1 = new ArcNode;
		p1->adjvex = j;
		p1->nextarc = G.vertices[i].firstarc;
		G.vertices[i].firstarc = p1;
		ArcNode* p2 = new ArcNode;
		p2->adjvex = i;
		p2->nextarc = G.vertices[j].firstarc;
		G.vertices[j].firstarc = p2;
	}
	return 1;
}
```



#### 邻接表与邻接矩阵的区别与联系

![image-20231102131107826](Data Structures & Algorithm.assets\image-20231102131107826.png)

联系：邻接表中每个链表对应于邻接矩阵中的一行，链表中结点个数等于一行中非零元素的个数。

区别：

1. 对于任一确定的无向图，邻接矩阵是唯一的 （行列号与顶点编号一致），但邻接表不唯一 （链接次序与顶点编号无关）

2. 邻接矩阵的空间复杂度为O(n^2)，而邻接表的空间复杂度为O(n+e)

用途：邻接矩阵多用于稠密图，而邻接表多用稀疏图



#### 十字链表

​		十字链表(Orthogonal List)是有向图的另一种链式存储结构。我们也可以把它看成是将有向图的邻接表和逆邻接表结合起来形成的一种链表。
​		有向图中的每一条弧对应十字链表中的一个弧结点，同时有向图中的每个顶点在十字链表中对应有一个结点，叫做顶点结点。

![image-20231102162028369](Data Structures & Algorithm.assets\image-20231102162028369.png)



#### 邻接多重表

![image-20231102163516565](Data Structures & Algorithm.assets\image-20231102163516565.png)



### 6.3 图的遍历

​		从已给的连通图中某一顶点出发，沿着一些边访遍图中所有的顶点，且使每个顶点仅被访问一次，就叫做图的遍历，它是图的基本运算。

> 遍历的实质：找每个顶点的邻接点的过程

​		图中可能存在回路且图的任一顶点都可能与其它顶点相通，在访问完某个顶点之后可能会沿着某些边又回到了曾经访问过的顶点。

> 为了避免重复访问：
>
> 设置辅助数组 visited[n]，用来标记每个被访问过的顶点，初始状态visited[i]为0
> 顶点i 被访问，改 visited i为1，防止被多次访问



#### 深度优先搜索

​		Depth_First Search——DFS

方法：

1. 在访问图中某一起始顶点v后，由v出发，访问它的任一邻接顶点w1;

2. 再从w1出发，访问与w1邻接但还未被访问过的顶点 w2；

3. 然后再从w2出发，进行类似的访问......

4. 如此进行下去，直至到达所有的邻接顶点都被访问过的顶点u为止

5. 接着，退回一步，退到前一次刚访问过的顶点，看是否还有其它没有被访问的邻接顶点

   - 如果有，则访问此顶点，之后再从此顶点出发，进行与前述类似的访问；

   - 如果没有，就再退回一步进行搜索。重复上述过程，直到连通图中所有顶点都被访问过为止

> 连通图的深度优先遍历类似于树的先根遍历

邻接矩阵表示：

```c++
void DFS(AMGraph G, int v, bool visited[]) {
	visited[v] = true;
    cout << G.vexs[v] << " ";
	for (int i = 0; i < G.vexnum; i++) {
		if (G.arcs[v][i] != 0 && !visited[i]) {
            //G.arcs[v][i]!=0表示存在边，!visited[i]表示没有被访问过
			DFS(G, i, visited);
		}
	}
}

void DFSTraverse(AMGraph G) {
	bool visited[MVNum];
	for (int i = 0; i < G.vexnum; i++)
		visited[i] = false;    
	for (int i = 0; i < G.vexnum; i++) {
		if (!visited[i]) {
			DFS(G, i, visited);
		}
	}
}
```

邻接表表示：

```c++
void DFS(ALGraph& G, int v, bool visited[]) {
    visited[v] = true;
    cout << G.vertices[v].data << " ";
    ArcNode* p = G.vertices[v].firstarc;
    while (p) {
        int w = p->adjvex;
        if (!visited[w]) {
            DFS(G, w, visited);
        }
        p = p->nextarc;
    }
}

void DFSTraverse(ALGraph& G) {
    bool visited[MVNum];
    for (int i = 0; i < G.vexnum; i++) {
        visited[i] = false;
    }

    for (int i = 0; i < G.vexnum; i++) {
        if (!visited[i]) {
            DFS(G, i, visited);
        }
    }
}
```

DFS算法分析：

​		用邻接矩阵来表示图，遍历图中每一个顶点都要从头扫描该顶点所在行，时间复杂度为O(n^2)

​		用邻接表来表示图，虽然有 2e 个表结点，但只需扫描 e 个结点即可完成遍历，加上访问 n个头结点的时间，时间复杂度为O(n+e)
​		结论：
​		**稠密图适于在邻接矩阵上进行深度遍历**

​		**稀疏图适于在邻接表上进行深度遍历**

​		无论图是否连通，这个算法都可以访问图的所有结点，外层for循环可以保证这一点。



#### 广度优先搜索

​		Breadth_Frist Search——BFS

​		方法：从图的某一结点出发，首先依次访问该结点的所有邻点v1,v2,.. vi,再按这些顶点被访问的先后次序依次访问与它们相邻接的所有未被访问的顶点。

​		重复此过程，直至所有顶点均被访问为止。

![image-20231103185523017](Data Structures & Algorithm.assets\image-20231103185523017.png)

遍历次序：a	c	d	e	f	h	k	b	g

​		与树的层次遍历类似的，用队列实现

- 邻接矩阵

```c++
void BFS(AMGraph G, int v) {
    bool visited[MVNum];
    for (int i = 0; i < G.vexnum; i++) {
        visited[i] = false;
    }

    queue<int> q;
    cout << G.vexs[v] << " "; // 访问起始顶点
    visited[v] = true;
    q.push(v);

    while (!q.empty()) {
        int u = q.front();//取队首元素
        q.pop();//队首元素出队

        for (int i = 0; i < G.vexnum; i++) {
            if (G.arcs[u][i] != MaxInt && !visited[i]) {
                cout << G.vexs[i] << " ";
                visited[i] = true;
                q.push(i);//没被访问过就访问它然后让它入队
            }
        }
    }
}
```



- 邻接表实现

```c++
void BreadthFirstSearch(ALGraph& G, int startVertex) {
    bool visited[MVNum]; // 标记顶点是否被访问过
    for (int i = 0; i < G.vexnum; ++i) {
        visited[i] = false;
    }

    queue<int> q; // 队列用于辅助广度优先搜索
    cout << "BFS: ";
    cout << G.vertices[startVertex].data << " ";
    visited[startVertex] = true;
    q.push(startVertex);

    while (!q.empty()) {
        int currentVertex = q.front();
        q.pop();
        ArcNode* arc = G.vertices[currentVertex].firstarc;
        while (arc) {
            int adjVertex = arc->adjvex;
            if (!visited[adjVertex]) {
                cout << G.vertices[adjVertex].data << " ";
                visited[adjVertex] = true;
                q.push(adjVertex);
            }
            arc = arc->nextarc;
        }
    }
}
```



### 6.4 图的应用

#### 最小生成树

##### 定义与性质

​		生成树：所有顶点均由边连接在一起，但不存在回路的图

> 给定一个无向网络，在该网的所有生成树中，使得各边权值之和最小的那棵生成树称为该网的**最小生成树**，也叫**最小代价生成树**
>
> > 最小生成树可能不唯一

​		一个图可以有许多棵不同的生成树，所有生成树具有以下共同特点：

- 生成树的顶点个数与图的顶点个数相同
- 生成树是**图的极小连通子图**，去掉一条边则非连通
- 一个有n个顶点的连通图的生成有 n-1 条边

> 有n个顶点，n-1条边的图不一定是生成树：
>
>    ![image-20231103192629227](Data Structures & Algorithm.assets\image-20231103192629227.png)

- 在生成树中再加一条边必然形成回路
- 生成树中任意两个顶点间的路径是唯一的



- 深度优先生成树

![image-20231104201433885](Data Structures & Algorithm.assets\image-20231104201433885.png)

- 广度优先生成树

![image-20231104201510291](Data Structures & Algorithm.assets\image-20231104201510291.png)

##### 典型用途

​		欲在n个城市间建立通信网，则n个城市应铺n-1条线路。但因为每条线路都会有对应的经济成本，而n个城市最多有n(n-1)/2条线路，那么，如何选择n-1条线路，使总费用最少?

![image-20231104201825807](Data Structures & Algorithm.assets\image-20231104201825807.png)



##### MST性质及解释

**(Minimum Spanning Tree)**

​		设N =(V,E) 是一个**连通网**，U 是顶点集V的一个非空子集。若边(u,v) 是一条具有最小权值的边，其中u∈U，v∈V-U，则必存在一棵包含边(u,v)的最小生成树。

​		在生成树的构造过程中，图中n个顶点分属两个集合

- 已落在生成树上的顶点集：U

- 尚未落在生成树上的顶点集： V-U

![image-20231104203321971](Data Structures & Algorithm.assets\image-20231104203321971.png)



##### 普里姆(Prim)算法

![image-20231104204014418](Data Structures & Algorithm.assets\image-20231104204014418.png)



![image-20231107171337616](Data Structures & Algorithm.assets\image-20231107171337616.png)

![image-20231107171503312](Data Structures & Algorithm.assets\image-20231107171503312.png)

```c++
//基于邻接矩阵的Prim算法
typedef struct {
	int adjvex;//下标
	int cost;//权值
}Lowcost[MVNum];

//定义函数，实现最小权值的查找任务，返回最小权值对应的结点的下标（S的下标）
int MinCost(Lowcost S, int numvex) {
	int temp = Max; 
	int k = -1; 
	for (int i = 0; i < numvex; i++) {
		if (S[i].cost != 0 && S[i].cost < temp) {
			temp = S[i].cost;
			k = i;
		}
	}
	return k;
}

void Prim(AMGraph G, int startvex, Lowcost& S) {
	S[startvex] = { startvex,0 };//将顶点startvex加入数组中
	for (int i = 0; i < G.vexnum; i++)
		if (i != startvex)
			S[i] = { startvex,G.arcs[startvex][i] };//初始化二维数组
	int k = -1;
	for (int i = 1; i < G.vexnum; i++) {
		k = MinCost(S, G.vexnum);//找到权值最小的那个
		cout << S[k].adjvex << " " << k << endl;
		S[k].cost = 0;
		for (int i = 0; i < G.vexnum; i++) {
			if (G.arcs[k][i] < S[i].cost)
				S[i] = { k,G.arcs[k][i] };
		}

	}
}

//我写的Prim算法
//lowCost数组
typedef struct {
    int startIndex;
    int weight;
    int endIndex;
}lowCost[MVNum];


//定义函数，实现最小权值的查找任务，返回最小权值对应的结点的下标（S的下标）
int LocateMin(lowCost S, AMGraph G) {
    int min = MaxInt;
    int k = -1;
    for (int i = 0; i < G.vexnum; i++) {
        if (S[i].weight != 0 && S[i].weight < min) {
            //只有S[i].weight!=0即没有并入U集合中的才在查找范围之内
            min = S[i].weight;
            k = i;
        }
    }
    return k;
}

void myPrim(AMGraph G, lowCost& S) {
    //前面两个for用于初始化S
    //S的startIndex一开始都为U中唯一一个结点——G中顶点表的第一个结点
    for (int i = 0; i < G.vexnum; i++)
        S[i].startIndex = 0;//G中顶点表的第一个结点的下标为0
    //S的endIndex为从0到G中顶点表的最后一个结点的下标的递增序列（因为可以认为S是用来表示在最小生成树的结点与所有结点的weight的关系）
    for (int i = 0; i < G.vexnum; i++) {
        S[i].endIndex = i;
        S[i].weight = G.arcs[0][S[i].endIndex];//初始化weight
        /*  S[0].weight=G.arcs[0][0]
            S[1].weight=G.arcs[0][1]
            S[2].weight=G.arcs[0][2]
            S[3].weight=G.arcs[0][3]
            S[4].weight=G.arcs[0][4]
            S[5].weight=G.arcs[0][5]
            S[6].weight=G.arcs[0][6]
        */
        if (S[i].endIndex == 0)
            S[i].weight = 0;
}

    for (int i = 0; i < G.vexnum; i++) {
        //找到最小的
        int k = LocateMin(S, G);
        S[k].weight = 0;//找到之后，对应的S权值赋值为0，表示已经纳入最小生成树
        //遍历，更新
        for (int i = 0; i < G.vexnum; i++)
            if (G.arcs[k][i] < S[i].weight) {
                //如果新纳入的这个结点到其他未纳入树的结点的距离小于S中原有的数据，就更新
                //那么，为什么if的条件是"G.arcs[k][i] < S[i].weight"呢
                //G.arcs[k][i]表示邻接矩阵中下标为k的那一行
                //如果G.arcs[k][0]<S[0].weight，就表示最小生成树中到以下标为0的那个结点的距离大于下标为k的结点到以下标为0的那个结点的距离
                //其他同理
                S[i].startIndex = k;
                S[i].weight = G.arcs[k][i];
            }
    }
}
```





##### 克鲁斯卡尔 (Kruskal) 算法

![image-20231104204422148](Data Structures & Algorithm.assets\image-20231104204422148.png)



两种算法的比较：

![image-20231104204808384](Data Structures & Algorithm.assets\image-20231104204808384.png)



#### 最短路径

​		在有向网中 A 点 （源点）到达 B 点 （终点）的多条路径中，寻找一条各边权值之和最小的路径，即最短路径

​		最短路径与最小生成树不同，路径上不一定包含n个顶点，也不定包含 n-1条边。

- 单源最短路径——用Diikstra （迪杰斯特拉）算法

- 所有顶点间的最短路径——用Floyd （弗洛伊德）算法

##### Dijlstra算法

![image-20231105234414691](Data Structures & Algorithm.assets\image-20231105234414691.png)

![image-20231105234557329](Data Structures & Algorithm.assets\image-20231105234557329.png)

例如：

![image-20231105234633896](Data Structures & Algorithm.assets\image-20231105234633896.png)



##### Floyd算法

1. 先列出任意两点的直达路径

![image-20231109194028247](Data Structures & Algorithm.assets\image-20231109194028247.png)

2. 引入第一个结点（以引入1为例）

![image-20231109194127119](Data Structures & Algorithm.assets\image-20231109194127119.png)

​		引入1之后，表中（3，2）、（4，2）、（4、3）变得更短了，即以1为中转点，可以缩短3-2、4-2、4-3的路径。

3. 再引入一个结点（以引入2为例）

​		再引入2时，因为2只指向了3，所以引入2只有可能改变以3为终点的路径的长度，它们分别是1到3、4到3。

​		对于1到3：原来是6，以2为中介，长度变为2+3=5，变短了。

​		对于4到3：原来是11，以2为中介，长度变为7+3=10，变短了。

![image-20231109194656195](Data Structures & Algorithm.assets\image-20231109194656195.png)

> 到这里，最短路径有些是直接到达，有些以1为中介，有些以2为中介，有些以1，2为中介

4. 以此类推，引入所有结点，到最后，最短路径可能是直接到达，也可能有几个中转点

![image-20231109194817215](Data Structures & Algorithm.assets\image-20231109194817215.png)



#### 拓扑排序

![image-20231108192621329](Data Structures & Algorithm.assets\image-20231108192621329.png)

​		有向无环图：无环的有向图，简称 DAG图(Directed Acycline Graph)

​		有向无环图常用来描述一个工程或系统的进行过程。（通常把计划施工、生产、程序流程等当成是一个工程）一个工程可以分为若千个子工程，只要完成了这些子工程（活动）就可以导致整个工程的完成

AOV网
		用一个有向图表示一个工程的各子工程及其相互制约的关系，其中**以顶点表示活动**，**弧表示活动之间的优先制约关系**，称这种有向图为顶点表示活动的网，简称 AOV网(Activity On Vertex network) 。

> AOV网解决拓扑排序问题

AOE网
		用一个有向图表示一个工程的各子工程及其相互制约的关系，**以弧表示活动**，**以顶点表示活动的开始或结束事件**，称这种有向图为边表示活动的网，简称为AOE网 (Activity On Edge)。

> AOE网解决关键路径问题

##### AOV网的特点

​		若从i到j有一条有向路径，则i是j的前驱，j是i的后继

​		若<i,j> 是网中有向边，则i是j的直接前驱；j是i的直接后继

​		AOV网中不允许有回路，因为如果有回路存在，则表明某项活动以自己为先决条件，显然这是荒谬的。

##### 拓扑排序

​		在AOV 网没有回路的前提下，我们将全部活动排列成一个线性序列，使得若AOV 网中有弧 <i,j>存在，则在这个序列中，i一定排在j的前面，具有这种性质的线性序列称为拓扑有序序列，相应的拓扑有序排序的算法称为**拓扑排序**

​		算法：

1. 在有向图中选一个没有前驱的顶点且输出之
2. 从图中删除该顶点和所有以它为尾的弧
3. 重复上述两步，直至全部顶点均已输出或者当图中不存在无前驱的顶点为止

![image-20231108192238952](Data Structures & Algorithm.assets\image-20231108192238952.png)

检测AOV网中是否有环：

​		对有向图构造其顶点的拓扑有序序列，若网中所有顶点都在它的拓扑有序序列中，则该 AOV 网必定不存在环

![image-20231108192419436](Data Structures & Algorithm.assets\image-20231108192419436.png)

​		该图构造的拓扑有序序列中，没有C3，C5，C7，C6，C8，所以这个网有环



#### 关键路径

![image-20231108192717018](Data Structures & Algorithm.assets\image-20231108192717018.png)

​		把工程计划表示为边表示活动的网络，即AOE网，用**顶点表示事件，弧表示活动，弧的权表示活动持续时间。**事件表示在它之前的活动已经完成，在它之后的活动可以开始。

​		上述工程的AOE网如图所示：

![image-20231108200035466](Data Structures & Algorithm.assets\image-20231108200035466.png)

​		a1--a9依次表示清空办公室---清扫办公室的活动。

​		AOE-网在工程计划和经营管理中有广泛的应用，针对实际的应用问题，通常需要解决以两个问题：

1. 估算完成整项工程至少需要多少时间；
2. 判断哪些活动是影响工程进度的关键。

​		工程进度控制的关键在于抓住关键活动。在一定范围内，非关键活动的提前完成对于整个工程的进度没有直接的好处，它的稍许拖延也不会影响整个工程的进度。工程的指挥者可以把非关键活动的人力和物力资源暂时调给关键活动，加快其进展速度，以使整个工程提前完工。

​		由于整个工程只有一个开始点和一个完成点，故在正常的情况(无环)下，网中只有一个入度为0的点，称作**源点**，也只有一个出度为0的点，称作**汇点**。在AOE-网中，一条路径各弧上的权值之和称为该路径的**带权路径长度**。要估算整项工程完成的最短时间，就是要找一条从源点到汇点的带权路径长度最长的路径，称为**关键路径**(Critical Path)。关键路径上的活动叫作关键活动，这些活动是影响工程进度的关键，它们的提前或延期将使整个工程提前或延期。

如何确定关键路径，首先定义4个描述量：
(1)事件v的最早发生时间ve(i)
		进入事件v的每一活动都结束，v才可发生，所以ve(i)是从源点到vi的最长路径长度。求ve(i)的值，可根据拓扑顺序从源点开始向汇点递推。通常将工程的开始顶点事件v0的最早

![image-20231108200751334](Data Structures & Algorithm.assets\image-20231108200751334.png)

> 关键在于假设汇点的最早开始时间和最晚开始时间是一样的，然往前推，才能找到最晚-最早=0的活动，才能找到关键路径





# Algorithm

## 第七章 查找

### 7.1 知识回顾

![image-20231114150643749](Data Structures & Algorithm.assets/image-20231114150643749.png)

### 7.2 查找的基本概念

- 查找表

​		查找表是由同一类型的数据元素 (或记录)构成的集合。由于“集合”中的数据元素之间存在着松散的关系，因此查找表是一种应用灵便的结构。

- 关键字

  ​	用来标识一个数据元素 (或记录)的某个数据项的值

  - 主关键字

  可唯一地标识一个记录的关键字是主关键字

  - 次关键字

  用以识别若干记录的关键字是次关键字

- 平均查找长度**ASL(Average Search Length)**

​		查找算法的评价指标

​												![image-20231114151103137](Data Structures & Algorithm.assets/image-20231114151103137.png)		（关键字比较次数的期望值)	

n：记录的个数

pi：查找第i个记录的概率(通常认为pi =1/n)

ci：找到第i个记录所需的比较次数



​		查找的方法取决于查找表的结构，即表中数据元素是依何种关系组织在一起的。

​		由于对查找表来说，在集合中查询或检索一个“特定的”数据元素时若无规律可循，只能对集合中的元素一一加以辨认直至找到为止。

​		而这样的“查询”或“检索”是任何计算机应用系统中使用频度都很高的操作，因此设法提高查找表的查找效率，是本章讨论问题的出发点。

​		为提高查找效率，一个办法就是在构造查找表时，在集合中的数据元素之间人为地加上某种确定的约束关系。



### 7.3 线性表的查找

#### 顺序查找

```c++
//结构类型定义
typedef struct {
	KeyType key;//关键字域
	//其他域
}ElemType;

typedef struct {
	ElemType* R;//表基址
	int length;//表长
}SSTable;///Sequential Search Table
```

查找表中的某个元素，一般这样写：

![image-20231114152613420](Data Structures & Algorithm.assets/image-20231114152613420.png)

```c++
int Search_Seq(SSTable ST, KeyType key) {
	for (int i = ST.length; i >= 1; i--) {//一般把第一个位置空出来不用
		if (ST.R[i].key == key)return i;
	}
	return 0;
}
```

或者这样：

```c++
int Search_Seq(SSTable ST, KeyType key) {
	int i = 0;
	for (i = ST.length;ST.R[i].key!=key; i--)
		if (i <= 0)break;
	if (i > 0) return i;
	else return 0;
	return 0;
}
```

​		以上的写法，每执行一次循环都要进行两次比较，可否改进一下？

改进：

​		把待查关键字key存入表头（哨兵）从后往前逐个比较，可免去查找过程中每一步都要检测是否查找完毕，加快速度。

```c++
int Search_Seq(SSTable ST, KeyType key) {
	ST.R[0].key = key;//设置监视哨
	int i = 0;
	for (i = ST.length; ST.R[i].key != key; i--);//这里的";"很重要
	return i;
}
```

![image-20231114152846049](Data Structures & Algorithm.assets/image-20231114152846049.png)

​		当ST.length较大时，此改进能使进行一次查找所需的平均时间几乎减少一半。

**时间效率分析：**

比较次数与key位置有关，查找第i个元素，需要比较n-i+1次，查找失败，需比较n+1次。

**时间复杂度：O(n)**

ASL(n)=(1+2+3+...+n)/n=(n+1)/2

> 所以时间复杂度为O(n)

**空间复杂度：一个辅助空间，O(1)**

**更多的：**

- 记录的查找概率不相等时如何提高查找效率?

​		查找表存储记录原则一-按查找概率高低存储：

1. 查找概率越高，比较次数越少
2. 查找概率越低，比较次数较多

- 记录的查找概率无法测定时如何提高查找效率？

​		按查找概率动态调整记录顺序：

1. 在每个记录中设一不访问频度域
2. 始终保持记录按非递增有序的次序排列
3. 每次查找后均将刚查到的记录直接移至表头

- 优缺点：

1. 优点：算法简单，逻辑次序无要求，且不同存储结构均适用。
2. 缺点：ASL太长时间效率太低。



#### 折半查找

```c++
int Search_Bin(SSTable ST, KeyType key) {
	int left = 1;
	int right = ST.length;
	int mid = 0;
	while (left <= right) {
		mid = (left + right) / 2;
		if (ST.R[mid].key == key)return mid;
		else if (key < ST.R[mid].key)
			right = mid - 1;
		else
			left = mid + 1;
	}
	return 0;//没找到
}
```

**性能分析 - 判定树**

例如：![image-20231115192229897](Data Structures & Algorithm.assets/image-20231115192229897.png)

判定树如下：

![image-20231115192251401](Data Structures & Algorithm.assets/image-20231115192251401.png)

对于给定的关键字，首先和6比较，如果比6大，和9比较，如果比9大，和10比较...



![image-20231115192424759](Data Structures & Algorithm.assets/image-20231115192424759.png)

> - 对于6号结点，找到它仅用比较1次；3号结点，找到它仅用比较2次；7号结点，找它它仅用比较3次；（比较的次数等于结点的层数，也等于路径上的结点数）
>
> - 由上扩展：比较次数≤判判定树的深度（log2(n)+1）



对于上表，假定每个元素的查找概率相等，ASL=1/11(1+2*2+4*3+4*4)=3

扩展：

![image-20231115193840001](Data Structures & Algorithm.assets/image-20231115193840001.png)

- 优缺点：

1. 优点：效率比顺序查找高
2. 缺点： 只适用于有序表，且限于顺序存储结构（对线性链表无效）



#### 分块查找

![image-20231115194111325](Data Structures & Algorithm.assets/image-20231115194111325.png)



#### 查找方法比较

![image-20231115194128626](Data Structures & Algorithm.assets/image-20231115194128626.png)





### 7.4 树表的查找

​		当表插入、删除操作频繁时，为维护表的有序性，需要移动表中很多记录。此时，就可以改用动态查找表——几种特殊的树

> 表结构在查找过程中动态生成
>
> 对于给定值key：
>
> - 若表中存在，则成功返回
> - 否则，插入关键字等于key 的记录



#### 二叉排序树

##### 定义

​		二叉排序树 (Binary Sort Tree) 又称为二叉搜索树、二叉查找树

​		二叉排序树或是空树，或是满足如下性质的二叉排序树：

1. 若其左子树非空，则左子树上所有结点的值均小于根结点的值
2. 若其右子树非空，则右子树上所有结点的值均大于等于根结点的值
3. 其左右子树本身又各是一颗二叉排序树

例如，一颗二叉排序树：

![image-20231116112604137](Data Structures & Algorithm.assets/image-20231116112604137.png)

中序遍历二叉排序树：3 12 24 37 45 53 61 78 90 100

> 中序遍历非空的二叉排序树所得到的数据元素序列是一个按关键字排列的递增有序序列。

##### 算法实现

```c++
//定义二叉排序树
typedef struct {
	KeyType key;//关键字
	InfoType otherInf;//其他数字域
}ElemType;

typedef struct BSTNode {
	ElemType data;
	BSTNode* lchild, * rchild;
}BSTNNode, * BSTree;
//实际上就是树的定义
```

- 二叉排序树的递归查找

1. 若二叉排序树为空，则查找失败，返回空指针。

2. 若二叉排序树非空，将给定值key与根结点的关键字T->data.key进行比较：

   - 若key等于T->data.key，则查找成功，返回根结点地址

   - 若key小于T->data.key，则进一步查找左子树

   - 若key大于T->data.key，则进一步查找右子树

```c++
BSTree SearchBST(BSTree T, KeyType key) {
	if ((!T) || key == T->data.key)
		return T;//找到key或者树为空，return之
	else if (key < T->data.key)
		return SearchBST(T->lchild, key);//在左子树中找
	else return SearchBST(T->rchild, key);//在右子树中找
}
```

用while的写法：

```c++
BSTree SearchBST2(BSTree T, KeyType key) {
	while (T && key != T->data.key) {
		if (key < T->data.key)
			T = T->lchild;//在左子树中找
		else 
			T = T->rchild;//在右子树中找
	}
	return T;
}
```



##### 比较次数

二叉排序树上查找某关键字等于给定值的结点过程，**其实就是走了一条从根到该结点的路径。**

> 比较关键字的次数=此结点所在层次数
> 最多的比较次数=树的深度

​											![image-20231119154658663](Data Structures & Algorithm.assets/image-20231119154658663.png)  

​		例如上图，查找35需要比较4次（35在第4层)；

​		这个二叉排序树的最多比较次数为5次（树的深度为5）



##### 平均查找长度

![image-20231116114854545](Data Structures & Algorithm.assets/image-20231116114854545.png)

​		含有 n 个结点的二又排序树的平均查找长度和树的形态有关

![image-20231116115136747](Data Structures & Algorithm.assets/image-20231116115136747.png)



##### 插入

![image-20231116123835506](Data Structures & Algorithm.assets/image-20231116123835506.png)

> 插入的元素一定在叶结点上

```c++
//算法实现
void insertBST(BSTree& T, KeyType key) {
	if (T != NULL) {
		if (key < T->data.key)
			insertBST(T->lchild, key);
		else if (key > T->data.key)
			insertBST(T->rchild, key);
		else return;//等于，说明存在相同的数据元素
	}
	else {
        //新建一个结点
		BSTNNode* s = new BSTNNode;
		s->data.key = key;
		s->lchild = NULL;
		s->rchild = NULL;
        //链接
		T = s;
	}
}
//测试main
int main() {
	BSTree T =NULL;
	int num = 7;
	while (num--) {
		int x;
		cin >> x;//45 24 53 45 12 24 90
		insertBST(T, x);
	}
	InOrderTraverse(T);
}
```



##### 生成

​		从空树出发，经过一系列的查找、插入操作之后，可生成一株二叉排序树。

​		例：设查找的关键字序列为：45 24 53 45 12 24 90

​		可生成二叉排序树如下：

![image-20231116124316574](Data Structures & Algorithm.assets/image-20231116124316574.png)

​		一个无序序列可通过构造二叉排序树而变成一个有序序列。构造树的过程就是对无序序列进行排序的过程。
​		插入的结点均为叶子结点，故无需移动其他结点。相当于在有序序列上插入记录而无需移动其他记录。

> 关键字的输入顺序不同，得到的二叉排序树也不同



##### 删除

1. 被删除的结点是叶子结点，直接删去该结点

![image-20231116125252374](Data Structures & Algorithm.assets/image-20231116125252374.png)

2. 被删除的结点只有左子树或者只有右子树，用其左子树或者右子树替它 **(结点替换)** 

> 其双亲结点的相应指针域的值改为“指向被删除结点的左子树或右子树”

3. 被删除的结点既有左子树，也有右子树，以其中序前趋值替换之 (值替换) ，然后再删除该前趋结点前趋是左子树中最大的结点（或者用其后继替换之，然后再删除该后继结点。后继是右子树中最小的结点。）

![image-20231116125534807](Data Structures & Algorithm.assets/image-20231116125534807.png)

![image-20231116125552813](Data Structures & Algorithm.assets/image-20231116125552813.png)

![image-20231116125610498](Data Structures & Algorithm.assets/image-20231116125610498.png)

```c++
void DeleteBST(BSTree& T, int key) {
	//1.查找被删除结点的位置
	//2.获取替换结点的位置
	//3.将替换结点与被删除结点的父结点进行链接
	//4.删除结点
	BSTNode* p, * f, * q;
	p = T;
	f = NULL;
	q = NULL;
	while (q) {//找到要被删除结点的位置
		if (q->data.key == key)
			break;
		f = q;
		if (q->data.key > key)
			q = q->lchild;
		else q = q->rchild;
	}
	if (q->lchild != NULL && q->rchild != NULL) {//如果既有左子树又有右子树
		p = q->lchild; f = q;
		while (p->rchild) {//找到最右边（前驱结点）
			f = p;
			p = p->rchild;
		}
		q->data = p->data;//结点值替换
		q = p;//更新要被删除的位置

	}
	if (q->rchild == NULL)
		p = q->lchild;
	else if (q->lchild == NULL)
		p = q->rchild;
	//将替换结点与被删除结点的父结点进行链接
	if (f == NULL)//链接为树根
		T = p;
	else if (q == f->lchild)//链接为左孩子
		f->lchild = p;
	else f->rchild = p;//链接为右孩子
	delete q;
}
```



#### 平衡二叉树

##### 定义

​		平衡二叉树 (balanced binary tree)，又称AVL树(Adelson-Velskii and Landis)。

​		一棵平衡二叉树或者是空树，或者是具有下列性质的二叉排序树：

- 左子树与右子树的高度之差的绝对值**小于等于1**
- 左子树和右子树也是平衡二叉排序树

​		为了方便起见，给每个结点附加一个数字，给出该结点左子树与右子树的高度差。这个数字称为结点的**平衡因子** (BF)。
​		平衡因子 = 结点左子树的高度 - 结点右子树的高度
​		根据平衡二叉树的定义，平衡二又树上所有结点的平衡因子只能是-1、0，或1。

> ![image-20231119205540187](Data Structures & Algorithm.assets/image-20231119205540187.png)



##### 失衡二叉排序树的分析与调整

​		当我们在一个平衡二叉排序树上插入一个结点时有可能导致失衡，即出现平衡因子绝对值大于1的结点，如：2、-2。

> 如果在一棵 AVL 树中插入一个新结点后造成失衡，则必须重新调整树的结构，使之恢复平衡。

![image-20231119205704589](Data Structures & Algorithm.assets/image-20231119205704589.png)

- LL型

 ![image-20231119205839593](Data Structures & Algorithm.assets/image-20231119205839593.png)	调整后：	![image-20231119205856987](Data Structures & Algorithm.assets/image-20231119205856987.png)

> B结点带左子树a一起上升
>
> A结点成为B的右孩子
>
> 原来B结点的右子树B作为A的左子树



- RR型

 ![image-20231119210012135](Data Structures & Algorithm.assets/image-20231119210012135.png)调整后：![image-20231119210054183](Data Structures & Algorithm.assets/image-20231119210054183.png)

> B结点带右子树B一起上升
>
> A结点成为B的左孩子
>
> 原来B结点的左子树a作为A的右子树



- LR型

  ![image-20231119210655227](Data Structures & Algorithm.assets/image-20231119210655227.png)调整后：<img src="Data Structures & Algorithm.assets/image-20231119210752533.png" alt="image-20231119210752533" style="zoom:85%;" />

> C结点穿过A、B结点上升
>
> B结点成为C的左孩子
>
> A结点成为C的右孩子
>
> 原来C结点的左子树β作为B的右子树，原来C结点的右子树γ作为A的左子树

- RL型

![image-20231119211212691](Data Structures & Algorithm.assets/image-20231119211212691.png)

​		同理



### 7.5 散列表的查找

#### 基本概念

- 基本思想

  记录的存储位置与关键字之间存在对应关系

> 对应关系-hash函数
> Loc(i)=H(keyi)

- 散列方法（杂凑法）

  选取某个函数，依该函数**按关键字计算元素的存储位置**，并按此存放查找时，由同一个函数对给定值k计算地址，将k与地址单元中元素关键码进行比，确定查找是否成功。

- 散列函数（杂凑函数）

  散列方法中使用的转换函数

- 散列表（杂凑表）

  按上述思想构造的表

#### 散列函数的构造方法

​	**使用散列表要解决好两个问题**

1. 构造好的散列函数

   - 所选函数尽可能简单，以便提高转换速度

   - 所选函数对关键码计算出的地址，应在散列地址集中致均匀分布，以减少空间浪费

2. 制定一个好的解决冲突的方案

   查找时，如果从散列函数计算出的地址中查不到关键码，则应当依据解决冲突的规则，有规律地查询其它相关单元

​	**构造散列函数考虑的因素**

- 执行速度（即计算散列函数所需时间）
- 关键字的长度
- 散列表的大小
- 关键字的分布情况
- 查找频率

> 根据元素集合的特性构造
>
> 要求一：n个数据原仅占用n个地址，虽然散列查找是以空间换时间，但仍希望散列的地址空间尽量小
>
> 要求二：无论用什么方法存储，目的都是尽量均匀地存放元素，以避免冲突。

**构造方法**

1. 直接定址法
2. 数字分析法
3. 平方取中法
4. 折叠法
5. **除留余数法**
6. 随机数法

- 直接定址法

![image-20231127161331498](Data Structures & Algorithm.assets/image-20231127161331498.png)

- 除留余数法

Hash(key)=key mod p

> 设表长为m，p≤m且p为质数

![image-20231127161722297](Data Structures & Algorithm.assets/image-20231127161722297.png)

#### 处理冲突的方法

1. 开放定址法 (开地址法)

   基本思想：有冲突时就去寻找下一个空的散列地址，只要散列表足够天空的散列地址总能找到，并将数据元素存入

   例如：除留余数法 H~i~ =(Hash(key)+d~i~ ) mod m

   > d~i~ 为增量序列

   根据d的不同，分为以下方法：
   线性探测法、二次探测法、伪随机探测法

   ![image-20231127162205835](Data Structures & Algorithm.assets/image-20231127162205835.png)

2. 链地址法 （拉链法）

3. 再散列法（双散列函数法）

4. 建立一个公共溢出区

- 线性探测法例：


例:：关键码集为{47，7，29，11，16，92，22，8，3}，散列表的表长为m=11；散列函数为Hash(key)=key mod 11；拟用线性探测法处理冲突，建散列表如下：

![image-20231127163029962](Data Structures & Algorithm.assets/image-20231127163029962.png)

> ASL=(1+2+1+1+1+4+1+2+2)/9=1.67

- 链地址法例

![image-20231127195211207](Data Structures & Algorithm.assets/image-20231127195211207.png)

> 优点：
>
> 1. 非同义词不会冲突，无“聚集”现象
>
> 2. 链表上结点空间动态申请，更适合于表长不确定的情况

#### 查找效率分析

使用平均查找长度ASL来衡量查找算法，ASL取决

- 散列函数

- 处理冲突的方法

- 散列表的装填因子α（$α=\dfrac{表中填入的记录数}{哈希表的长度}$）

  > a越大，表中记录数越多，说明表装得越满，发生冲突的可能性就越大，查找时比较次数就越多。

​		

​		ASL与装填因子a有关! 既不是严格的O(1)，也不是O(n)

- 拉链法：$ASL≈1+\dfrac{α}{2}$
- 线性探测法：$ASL≈\dfrac{1}{2}(1+\dfrac{1}{1-α})$
- 随机探测法$ASL≈-\dfrac{1}{α}ln(1-α)$



几点结论：

- 散列表技术具有很好的平均性能，优于一些传统的技术
- 除留余数法作散列函数优于其它类型函数
- 链地址法优于开地址法



## 第八章 排序

### 8.1 基本概念

- 按数据存储介质
  - 内部排序
  - 外部排序

> <img src="Data Structures & Algorithm.assets/image-20231122155636464.png" alt="image-20231122155636464" style="zoom:67%;" />

- 按比较器个数
  - 串行排序
  - 并行排序

> <img src="Data Structures & Algorithm.assets/image-20231122155729675.png" alt="image-20231122155729675" style="zoom:67%;" />

- 按主要操作
  - 比较排序
  - 基数排序

> 比较排序：用比较的方法，例如插入排序、交换排序、选择排序、归并排序
>
> 基数排序: 不比较元素的大小，仅仅根据元素本身的取值确定其有序位置

- 按辅助空间
  - 原地排序
  - 非原地排序

> <img src="Data Structures & Algorithm.assets/image-20231122160033415.png" alt="image-20231122160033415" style="zoom:67%;" />

- 按稳定性
  - 稳定排序
  - 非稳定排序

> <img src="Data Structures & Algorithm.assets/image-20231122160113059.png" alt="image-20231122160113059" style="zoom:67%;" />
>
> 排序的稳定性只对结构类型数据排序有意义
> 例如：
> n个学生信息 (学号、姓名、语文、数学、英语、总分)
>
> 1. 按数学成绩从高到低排序
>
> 2. 按照总分从高到低排序
>
> 3. 总分相同的情况下，数学成绩高的排在前面
>
> > 排序方法是否稳定，并不能衡量一个排序算法的优劣

- 按自然性
  - 自然排序
  - 非自然排序

> <img src="Data Structures & Algorithm.assets/image-20231122160454858.png" alt="image-20231122160454858" style="zoom:67%;" />



### 8.2 插入排序

​		每步将一个待排序的对象，按其关键码大小，插入到前面已经排好序的一组对象的适当位置上，直到对象全部插入为止。

> 即边插入边排序，保证子序列中随时都是排好序的

<img src="Data Structures & Algorithm.assets/image-20231122161302359.png" alt="image-20231122161302359" style="zoom:67%;" />

#### 基本操作

​		在有序序列中插入一个元素，保持序列有序，有序长度不断增加。

​		起初，a[O]是长度为1的子序列，然后逐一将a[1]至a[n-1]插入到有序子序列中。

> 有序插入

#### 分类

<img src="Data Structures & Algorithm.assets/image-20231122161713391.png" alt="image-20231122161713391" style="zoom:80%;" />

#### 直接插入排序

```c++
void InsertSort(SqList& L) {
	int i, j;
	for (i = 2; i <= L.length; i++) {
		if (L.r[i].key < L.r[i - 1].key) {
            //若小于，需要将L.r[i]插入有序子表，不小于，原来的位置就是应有的位置
			L.r[0].key = L.r[i].key;//复制为哨兵
			for (j = i - 1; L.r[j].key > L.r[0].key; j--)
                //使用哨兵，这里可以少比较一次，即不用判断是否j>=0
				L.r[j + 1] = L.r[j];
			L.r[j + 1] = L.r[0];//插入
		}
	}
}
```

最好情况：

<img src="Data Structures & Algorithm.assets/image-20231122164925133.png" alt="image-20231122164925133" style="zoom:80%;" />

> 每个元素仅需和前面的元素进行比较，第1个元素不用比，第2个和第1个比，第3个和第2个比······，不用复制到哨兵位置，即不用移动

最坏情况：

<img src="Data Structures & Algorithm.assets/image-20231122165202153.png" alt="image-20231122165202153" style="zoom:80%;" />

> 比较：每一个元素（从2号位开始）都要和前面的所有元素进行比较，还要和哨兵进行比较。
>
> 移动：每一个元素（从2号位开始），都要移动到哨兵再从哨兵移动到正确的位置，这里两次。然后每个元素的前面所有元素都要移动。第2个元素移动2+1次，第3个元素移动2+2次······



#### 折半插入排序

```c++
void BInsertSort(SqList& L) {
	for (int i = 2; i <= L.length; i++) {
		L.r[0] = L.r[i];
		int low = 1;
		int high = i - 1;
		int mid = 0;
		while (low <= high) {
			mid = (low + high) / 2;
			if (L.r[0].key < L.r[mid].key)
				high = mid - 1;
			else
				low = mid + 1;
		}//循环结束时，high+1为需要插入的位置
		for (int j = i - 1; j >= high + 1; j--)
			L.r[j + 1] = L.r[j];//移动
		L.r[high + 1] = L.r[0];//插入到正确的位置
	}
}
```



<img src="Data Structures & Algorithm.assets/image-20231122192423999.png" alt="image-20231122192423999" style="zoom:80%;" />

<img src="Data Structures & Algorithm.assets/image-20231122192525167.png" alt="image-20231122192525167" style="zoom:80%;" />

> 时间复杂度：O(n^2)
>
> 空间复杂度：O(1)
>
> 是一种**稳定**的排序方法



#### 希尔排序

​		先将整个待排记录序列分割成若干子序列，分别进行直接插入排序待整个序列中的记录“基本有序”时，再对全体记录进行一次直接插入排序。

例如：

![image-20231122193639620](Data Structures & Algorithm.assets/image-20231122193639620.png)

```c++
void ShellInsert(SqList& L,int dk) {
	int i, j;
	for (i = dk+1; i <= L.length; i++) {
		if (L.r[i].key < L.r[i - dk].key) {
			L.r[0].key = L.r[i].key;//复制为哨兵
			for (j = i - dk; j>0&&(L.r[j].key > L.r[i].key); j=j-dk)
				L.r[j + dk].key = L.r[j].key;
			L.r[j + dk] = L.r[0];//插入
		}
	}
}

void ShellSort(SqList& L, int dlta[], int t) {
	//按增量序列dlta[0..t-1]对顺序表L作希尔排序
	for (int k = 0; k < t; k++) {
		ShellInsert(L, dlta[k]);//一趟增量为dlta[k]的插入排序
	}
}
```

 <img src="Data Structures & Algorithm.assets/image-20231122195628265.png" alt="image-20231122195628265" style="zoom: 67%;" /><img src="Data Structures & Algorithm.assets/image-20231122200137461.png" alt="image-20231122200137461" style="zoom: 67%;" />



### 8.3 交换排序

​		基本思想：两两比较，如果逆序，就交换

​		常见的交换排序方法：

- 冒泡排序
- 快速排序



#### 冒泡排序

​		基本思想：每趟不断将记录两两比较，并按“前小后大” 规则交换

![image-20231125141726670](Data Structures & Algorithm.assets/image-20231125141726670.png)

![image-20231125141750825](Data Structures & Algorithm.assets/image-20231125141750825.png)

> 第一趟，6个元素都参与比较，要比较5次
>
> 第二趟，最后一个元素不再参与比较，有5个元素要比较，两两比较要4次
>
> 同理，第三趟比较3次，第四趟比较2次，第五趟比较一次

总结：

- n个记录，要比较n-1趟
- 第 m 趟需要比较 n-m 次

```c++
//算法实现：
void BubbleSort(SqList& L) {
	int m, j, i;
	RedType temp;//交换时的临时存储
	for (m = 1; m <= L.length - 1; m++) {
		for (j = 1; j <= L.length - m; j++)
			if (L.r[j].key > L.r[j + 1].key) {
				temp = L.r[j];
				L.r[j] = L.r[j + 1];
				L.r[j + 1] = temp;
			}
	}
}
```

> 算法分析：
>
> ​		 每趟结束时，不仅能挤出一个最大值到最后面位置，还能同时部方理顺其他元素；
> 如何提高效率？
> ​		一旦某一趟比较时不出现交换说明已排好序了，就可以结束本算法。

```c++
//算法改进
void BubbleSort(SqList& L) {
	int m, j, i;
	int flag = 1;//用于标记是否有交换
	RedType temp;//交换时的临时存储
	for (m = 1; m <= L.length - 1&&flag==1; m++) {
		flag = 0;
		for (j = 1; j <= L.length - m; j++)
			if (L.r[j].key > L.r[j + 1].key) {
				flag = 1;////发生交换，flag置为1，若本趟没发生交换，flag保持为0
				temp = L.r[j];
				L.r[j] = L.r[j + 1];
				L.r[j + 1] = temp;
			}
	}
}
```



算法分析：

![image-20231125142950135](Data Structures & Algorithm.assets/image-20231125142950135.png)

> 每一次比较，如果符合要移动的情况，需要移动三次：
>
> `temp=x;`
>
> `x=y;`
>
> `y=temp;`



- 冒泡排序最好时间复杂度是O(n)
- 冒泡排序最坏时间复杂度为O(n^2^)
- 冒泡排序平均时间复杂度为O(n^2^)
- 冒泡排序算法中增加一个辅助temp；辅助空间为S(n)=O(1)
- 冒泡排序是稳定的



#### 快速排序

​		改进的交换排序

基本思想：

- 任取一个元素(如：第一个) 为中心（pivot: 枢轴、中心点）
- 所有比它小的元素一律前放，比它大的元素一律后放形成左右两个子表
- 对各子表重新选择中心元素并依此规则调整
- 直到每个子表的元素只剩一个

```c++
//算法实现
int Partition(SqList& L, int low, int high) {
	L.r[0] = L.r[low];//子表的第一个元素放到哨兵位
	int pivotkey = L.r[0].key;//选取第一个元素为中心
	while (low < high) {
		while (low<high && L.r[high].key>=pivotkey)
			high--;//大于的话，就移动high指针，直到找到第一个小于的
		L.r[low] = L.r[high];//找到小于的之后，就把小于的值赋值到前面
		while (low<high && L.r[low].key<=pivotkey)
			low++;//如果low指针指向的元素小于pivotkey，就移动low指针
		L.r[high] = L.r[low];
	}
	L.r[low] = L.r[0];//最后high会与low相等，这个位置是哨兵要回到的位置
	return low;//这个元素在整个表中都是排好了的
}

void QSort(SqList& L, int low, int high) {//对顺序表L进行快速排序
	if (low < high) {//长度大于1
		int pivotloc = Partition(L, low, high);
		// 将L.r[low..high]一分为二，pivotloc为枢轴元素排好序的位置
		QSort(L, low, pivotloc - 1);
		QSort(L, pivotloc+1, high);
	}
}
```

算法分析：

- 时间复杂度

​		可以证明，平均计算时间是O(nlog~2~n)

> Qsort( ): O(log~2~n)
>
> Partition( ): O(n)

​		实验结果表明：就平均计算时间而言，快速排序是我们所讨论的所有内排序方法中最好的一个

- 空间复杂度

​		快速排序不是原地排序
​		由于程序中使用了递归，需要递归调用栈的支持，而栈的长度取决于递归调用的深度。 

>  (即使不用递归，也需要用用户栈)

​		在平均情况下：需要O(logn)的栈空间
​		最坏情况下：栈空间可达O(n)

- 稳定性

​		快速排序是一种不稳定的排序方法。

​		例如: 	

​			  		49，38，49\*，20，97，76

一次划分后:  20，38，49*，49，97，76



![image-20231125151400286](Data Structures & Algorithm.assets/image-20231125151400286.png)

> - 划分元素的选取是影响时间性能的关键
> - 输入数据次序越乱，所选划分元素值的随机性越好，排序速度越快，快速排序不是自然排序方法。
> - 改变划分元素的选取方法，至多只能改变算法平均情况的下的平均性能，无法改变最坏情况下的时间性能。即最坏情况下，快速排序的时间复杂性总是O(n^2^)



### 8.4 选择排序

#### 简单选择排序

​		基本思想：在待排序的数据中选出最大 (小)的元素放在其最终的位置

基本操作：

1. 首先通过n-1次关键字比较，从n个记录中找出关键字最小的记录，将它与第一个记录交换
2. 再通过n-2次比较，从剩余的n-1个记录中找出关键字次小的记录，将它与第二个记录交换
3. 重复上述操作，共进行n-1趟排序后，排序结束

```c++
void SelectSort(SqList& L) {
	for (int i = 1; i < L.length; i++) {
		int k = i;
		for (int j = i + 1; j <= L.length; j++) 
			if (L.r[j].key < L.r[k].key)
				k = j;//记录最小值的位置
		if (k != i) {//交换
			RedType temp = L.r[i];
			L.r[i] = L.r[k];
			L.r[k] = temp;
		}
	}
}
```

- 算法分析

![image-20231125153755386](Data Structures & Algorithm.assets/image-20231125153755386.png)

![image-20231125153819787](Data Structures & Algorithm.assets/image-20231125153819787.png)



#### 堆排序

![image-20231125154935109](Data Structures & Algorithm.assets/image-20231125154935109.png)

​		若在输出堆顶的最小值 (最大值) 后，使得剩余n-1个元素的序列重又建成一个堆，则得到n个元素的次小值 (次大值) ......如此反复，便能得到一个有序序列，这个过程称之为**堆排序**。

- 堆的调整

​		如何在输出堆顶元素后，调整剩余元素为一个新的堆？

​		**以小根堆为例：**

1. 输出堆顶元素之后，以堆中最后一个元素替代之

2. 然后将根结点值与左、右子树的根结点值进行比较，并与其中小者进行交换，

3. 重复上述操作，直至叶子结点，将得到新的堆，称这个从堆顶至叶子的调整过程为“筛选“

```c++
void HeapAdjust(SqList& L, int s, int m) {
	//本函数调整L.r[s]的关键字，使L.r[s].key......L.r[length].key成为一个小根堆
	RedType rc = L.r[s];
	for (int j = 2 * s; j <= m; j *= 2) {// 沿key较小的孩子结点向下筛选
		if (j < m && L.r[j].key > L.r[j + 1].key)
			++j; // 为key较小的记录的下标
		if (rc.key <= L.r[j].key)
			break;
		L.r[s] = L.r[j];
		s = j;// rc应插入在位置s上
	}
	L.r[s] = rc; // 插入
}//HeapAdjust
```

- 堆的建立

​		可以看出：

​		对一个无序序列反复“筛选”就可以得到一个堆，即：从一个无序序列建堆的过程就是一个反复“筛选”的过程。

​		那么：如何由一个无序序列建成一个堆?

​		显然：

1. 单结点的二叉树是堆
2. 在完全二又树中所有以叶子结点 (序号i > n/2) 为根的子树是堆
3. 这样，我们只需依次将以序号为n/2，n/2 - 1，.......1的结点为根的子树均调整为堆即可。
4. 即:对应由n个元素组成的无序序列始“筛选”只需从第n/2个元素开始。

例如：

![image-20231125164506259](Data Structures & Algorithm.assets/image-20231125164506259.png)

调整后：

![image-20231125164605500](Data Structures & Algorithm.assets/image-20231125164605500.png)

```c++
//算法实现
void Heapify(SqList& L) {
	for (int i = L.length / 2; i >= 1; i--)
		HeapAdjust(L, i, L.length);
}
```

- 堆排序

```c++
void Swap(SqList& L, int i, int j) {
    // 交换数组 L.r 中索引为 i 和 j 的元素
    RedType temp = L.r[i];
    L.r[i] = L.r[j];
    L.r[j] = temp;
}

void HeapSort(SqList& L) {
	for (int i = L.length / 2; i >= 1; i--)
		HeapAdjust(L, i, L.length);//建立小根堆（大根堆）
	for (int i = L.length; i > 1; i--) {//进行n-1趟排序
		Swap(L,1,i);//根与最后一个元素交换
		HeapAdjust(L, 1, i-1);//重新建堆
	}
}//HeapSort
```

> 这段代码实现的是堆排序算法。堆排序是一种高效的、基于比较的排序算法，它的主要思想是利用堆的性质进行排序。下面是这个算法的主要步骤和意义：
>
> 1. **Heapify 阶段**：
>
>    ```c++
>    for (int i = L.length / 2; i >= 1; i--)
>        HeapAdjust(L, i, L.length);
>    ```
>    在这一阶段，通过**从最后一个非叶子节点开始**，逐个调整为**大根堆**，实现了对数组的初始化建堆。这确保了整个数组满足堆的性质。
>
> 2. **排序阶段**：
>    
>    ```c++
>    for (int i = L.length; i > 1; i--) {
>        Swap(L); // 根与最后一个元素交换
>        HeapAdjust(L, i, L.length); // 重新建堆
>    }
>    ```
>    在排序阶段，通过不断将根节点与当前未排序部分的最后一个元素交换，并重新调整未排序部分，实现了对数组的排序。每一次交换将当前未排序部分的最大元素移到了正确的位置，最终得到有序数组。
>
> **算法的意义：**
> - **时间复杂度：** 堆排序的平均和最坏时间复杂度都是 O(n log n)，其中 n 是数组的长度。这使得堆排序在大多数情况下都比较高效。
> - **原地排序：** 堆排序是原地排序算法，不需要额外的存储空间，只需要一个与数组规模无关的常数空间用于交换。
> - **不稳定性：** 堆排序是不稳定的排序算法，即相等元素的相对顺序在排序后可能发生改变。
>
> 综上所述，堆排序在排序算法中有着较好的性能，并且相对于其他排序算法，它对于大规模数据的排序相对更为高效。

例如：

![image-20231125195452218](Data Structures & Algorithm.assets/image-20231125195452218.png)



### 8.5 归并排序

​	基本思想：将两个或两个以上的有序子序列“**归并”**为一个有序序列。

​	在内部排序中，通常采用的是**2-路归并排序**。

> 即将两个位置相邻的**有序**子序列R[l....m和R[m+1..n] 归并为一个有序序列R[l......n]。

例：

​	![image-20231206225525976](Data Structures & Algorithm.assets/image-20231206225525976.png)

> 上树称之为**归并树**，趟数为树的高度，整个归并排序仅需要**log~2~n**趟

![image-20231207160001479](Data Structures & Algorithm.assets/image-20231207160001479.png)

```c++
/*这个函数的作用是：
*将A[low..mid] 和 A[mid+1...high]
*这两段数据 进行合并排序 (卡牌算法) 
*这里需要一个临时数组 来存放 A[] 
*/
void merge(ElemType A[],int low,int mid,int high){
	//B里暂存A的数据 
	for(int k = low ; k < high + 1 ; k++){
		B[k] = A[k]; 
	} 
	/*这里对即将合并的两个数组 
	*A[low..mid] 头元素 A[i]和 A[mid+1...high] 头元素  A[j] 
	*进行一个头部的标记, 分别表示为数组片段的第一个元素 
	*k 是目前插入位置。 
	*/ 
	int i = low , j = mid + 1 , k = low; 	
	//只有在这种情况下 才不会越界 
	while(i < mid + 1 && j < high + 1) {
		//A的元素暂存在B里，因为不能再A上原地操作，会打乱数据
		//这也是为什么二路归并排序(合并排序)空间复杂度是O(n)的原因 
		//我们这里把值小的放在前面，最后排序结果就是从小到大 
		if(B[i] > B[j]){
			A[k++] = B[j++]; 
		}else{
			A[k++] = B[i++]; 
		} 	 
	} 
	//循环结束后，会有一个没有遍历结束的数组段。
	while(i < mid + 1) 
		A[k++] = B[i++]; 
	while(j < high + 1) 
		A[k++] = B[j++]; 
}
```



**算法效率分析：**

- 时间效率：O(nlong~2~n)
- 空间效率：O(n)

> 因为需要一个与原始序列同样大小的辅助序列 (R1)。这正是此算法的缺点。

- 稳定性：稳定



### 8.6 基数排序

​		基本思想：分配+收集

​		也叫桶排序或箱排序：设置若干个箱子，将关键字为k的记录放入第k个箱子，然后在按序号将非空的连接。

​		基数排序：数字是有范围的，均由0-9这十个数字组成，则只需设置十个箱子，相继按个、十、百...进行排序

例：

<img src="Data Structures & Algorithm.assets/image-20231207161356040.png" alt="image-20231207161356040" style="zoom:80%;" />

<img src="Data Structures & Algorithm.assets/image-20231207161432659.png" alt="image-20231207161432659" style="zoom:80%;" />

<img src="Data Structures & Algorithm.assets/image-20231207161512042.png" alt="image-20231207161512042" style="zoom:80%;" />

**算法效率分析：**

- 时间效率：O(k*(n+m))

> k：关键字个数
> m：关键字取值范围为m个值

### 8.7 各种排序方法比较

![image-20231207163243373](Data Structures & Algorithm.assets/image-20231207163243373.png)

不稳定的排序：希尔排序、堆排序、选择排序、快速排序

时间复杂度：**快排、堆排序、归并排序**优于**希尔排序**有序**冒泡、选择、直接插入**
