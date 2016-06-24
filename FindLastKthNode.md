#### 找链表的倒数第K个节点(FindLastKthNode)

	思路：单链表只能从 head 往后遍历，要想找到倒数第K个节点。我们没有办法从 tail 开始找到第k个节点。但是我们可以借用
	
		  快慢指针的方式解决这个问题。
		  
		  0.如果 head == NULL 或者 K < 0 ，直接返回 head；
		  1.slow 一开始指向链表的第一个节点。
		  2.fast 先从第一个节点向后走K步，如果fast不为空的话。
		  3.接着 fast 和 siow 同时向后移动，知道 fast为空。这时，slow 刚好指向倒数第k个节点，返回 slow。
		  

#### 代码

```cpp

	cpp code:
	
		Node* FindLastKthNode(Node* head, int K)
		{
			if (NULL == head || K < 0)
				return NULL;
	
			Node* slow = head;
			Node* fast = head;
	
			while (NULL != fast && K--)
			{
				fast = fast->_next;
			}
			if (K > 0)                     //参数超出了节点总数
				return head;
	
			while (NULL != fast)
			{
				slow = slow->_next;
				fast = fast->_next;
			}
	
			return slow;
		}
		
		
		
```




