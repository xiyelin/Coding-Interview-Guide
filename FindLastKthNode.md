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


<br>
#### 扩展：找到并删除链表的倒数第K个节点

	思路：首先我们先考虑边界情况。
		 
		 1.如果倒数第K个节点刚好是链表的第一个节点，那么我们就需要改变头指针 head 的指向。
		 2.如果 K == 1 ，即删除最后一个节点，直接删除，将倒数第2个节点的 next 置为 NULL。
		 3.倒数第K个节点在链表中间，这是需要一个临时节点指针记住倒数第K个节点的前一个节点。
		 
		 
![image](http://hbimg.b0.upaiyun.com/71613af82db3be383849c37166be35366b5cc034a517-qAtwjW_fw658)


<br>

#### 代码

```cpp

	cpp code:
	
		Node* RemoveLastKthNode(Node*& head, int K)
		{
			if (NULL == head || K < 0)
				return NULL;
			if (0 == K)
				return head;
	
			Node* slow = head;
			Node* fast = head;
			Node* prev = NULL;
	
			while (NULL != fast && K--)
			{
				fast = fast->_next;
			}
			if (K > 0)                     //参数超出了节点总数
				return head;
	
			while (NULL != fast)
			{
				prev = slow;
				slow = slow->_next;
				fast = fast->_next;
			}
			 
			if (slow == head)               //倒数第K个节点为第一个节点
			{
				Node* tmp = head->_next;
	
				delete head;
				head = tmp;
			}
			else if (NULL == slow->_next)   //倒数第K个节点为最后一个节点
			{
				delete slow;
				prev->_next = NULL;
			}
			else                            //倒数第K个节点在链表中间
			{
				prev->_next = slow->_next;
				delete slow;
				slow = NULL;
			}
	
			return head;
		}
		
	
```






