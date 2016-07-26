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

```cpp
	cpp code:
	
		# include <iostream>
		using namespace std;
		
		struct ListNode
		{
		    int _data;
		    ListNode* _next;
		
		    ListNode(const int x)
		        :_data(x)
		        ,_next(NULL)
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
		
		bool JudgePalindromeList(ListNode* head)
		{
		    
		}
		
		
		int main()
		{
		    ListNode* head = NULL;
		    Push_Back(head, 1);
		    Push_Back(head, 2);
		    Push_Back(head, 3);
		    Push_Back(head, 4);
		    Push_Back(head, 5);
		
		    PrintList(head);
		
		    cout << JudgePalindromeList(head) << endl;
		
		    system("pause");
		    return 0;
		}


```
	



