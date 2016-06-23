#### 打印两个有序链表的公共部分

	思路： 因为是有序链表，所以只需要从头开始依次往后比较：
	
		  1.如果 head1 的值小于 head2 的值，则 head1 往下移动。
		  
		  2.如果 head1 的值大于 head2 的值，则 head2 往下移动。
		  
		  3.如果 head1 的值等于 head2 的值，则 head1 和 head2 一起往下移动。
		  
		  4.如果 head1 或者 head2 有任何一个移动到 NULL ，则整个过程结束。 



#### 代码

```cpp

	cpp code:
		
		struct ListNode                     //链表节点
		{
			int _data;
			ListNode* _next;
		
			ListNode(int data = 0)
				:_data(data)
				,_next(NULL)
			{}
		};
		
		typedef ListNode Node;
		
		void PrintListCommonPart(Node* head1, Node* head2)
		{
			if (NULL == head1 || NULL == head2)
			{
				cout << "NULL" << endl;
				return;
			}
		
			Node* cur1 = head1;
			Node* cur2 = head2;
		
			while (cur1 && cur2)
			{
				if (cur1->_data > cur2->_data)
					cur2 = cur2->_next;
				else if (cur1->_data < cur2->_data)
					cur1 = cur1->_next;
				else
				{
					cout << cur1->_data << "->";
					cur1 = cur1->_next;
					cur2 = cur2->_next;
				}
			}
		}
		
		
```



    
