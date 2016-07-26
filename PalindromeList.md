## 判断一个链表是否为回文链表

----------------------------------------

### 题目：给定一个指向链表第一个节点的指针 head，判断该链表是否为回文链表
>例如：

>> 1->2->1,    返回true;  <br>
>> 1->2->2->1, 返回true;  <br>
>> 15->6->15,  返回true;  <br>
>> 1->2->3,    返回false;  <br>

>进阶：如果链表长度为N，时间复杂度达到O(N), 额外空间复杂度O(1)。

<br>
<br>

### 方法一：

	借助栈stack<int> s来完成判断，我们可以先遍历一遍原来的链表，边遍历边压栈，我们知道栈是先进后出的结构，所以
	出栈的顺序正好和从头遍历原链表的顺序相反。如果该链表是回文链表，则它们的每个元素都相等，否则，不是回文链表。
	该方法的空间复杂度为 O(N)；


```cpp
	cpp code:
	
		# include <iostream>
		using namespace std;
		# include <stack>
		
		struct ListNode
		{
		    int _data;
		    ListNode* _next;
		
		    ListNode(const int x)
		        :_data(x)                //数据域
		        ,_next(NULL)             //指向下一个节点
		    {}
		};
		
		void Push_Back(ListNode*& head, const int x)
		{
		    if (NULL == head)
		    {
		        head = new ListNode(x);
		        return;
		    }
		
		    ListNode* tmp = new ListNode(x);
		    ListNode* cur = head;
		
		    while (cur && cur->_next)
		        cur = cur->_next;
		    cur->_next = tmp;
		}
		
		void PrintList(ListNode* head)
		{
		    while (head)
		    {
		        cout << head->_data << "->";
		        head = head->_next;
		    }
		    cout << "NULL" << endl;
		}
		
		bool JudgePalindromeList(ListNode* head)                //判断是否为回文链表
		{
		    stack<int> s;
		    ListNode* cur = head;
		
		    while (cur)
		    {
		        s.push(cur->_data);
		        cur = cur->_next;
		    }
		
		    while (head)
		    {
		        int s_data = s.top();
		        if (head->_data == s_data)
		        {
		            s.pop();
		            head = head->_next;
		        }
		        else
		            return false;
		    }
		
		    return true;
		}
		
		
		int main()
		{
		    ListNode* head = NULL;
		    Push_Back(head, 1);
		    Push_Back(head, 2);
		    Push_Back(head, 3);
		    Push_Back(head, 2);
		    Push_Back(head, 1);
		
		    PrintList(head);
		
		    cout << JudgePalindromeList(head) << endl;
		
		    system("pause");
		    return 0;
		}



```

### 方法二：

	如果一个链表是回文链表，那么它左右两边的元素都相等；所以在方法一的基础上，可以进一步优化，使空间复杂度为O(N/2)。
	
	第一步：找到中间节点；
	第二步：将中间以前（即左边）的元素压栈；
	第三步：比较出栈元素和链表中剩余的元素；都相等，则是回文，否则不是回文链表。
	
<br>
<br>

### 方法三：进阶解法

	例如： 1->2->3->2->1
	
	1.先将链表右半边的指针指向反转，反转后的链表为： 1->2->3<-2<-1 ; 如下图：

![image]()

	2.我们将leftstart和rightstart同时向中间移动并比较其值是否相等，如果都相等，则是回文链表；
	
	3.不管最后是不是回文链表，我们都应该将链表恢复为原来的样子；
	
	4.在恢复完链表之后，在进行返回检查结果。

<br>

```cpp
	cpp code:
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
```



		

	
	
	
	
	
	
	
	
	
	
	
	
	



