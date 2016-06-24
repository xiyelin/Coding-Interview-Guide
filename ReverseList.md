#### 单链表的逆置(ReverseList)

	思路：新建头节点，然后依次遍历链表，遇到一个节点摘一个节点下来，然后插到新头节点的后边。
	
	要求：时间复杂度为 O(N)，空间复杂度为 O(1)。
	
	
![image](http://hbimg.b0.upaiyun.com/d753f9b70ebc858c1a58f95e88bf0f16de374a9011d1b-evOqYE_fw658)


<br>

#### 代码

```cpp

	cpp code:
	
		Node* ReverseList(Node*& head)
		{
			if (NULL == head || NULL == head->_next)    //为空或者只有一个节点不用逆序
				return head;
	
			Node* cur = NULL;
			Node* newhead = NULL;
	
			while (head)
			{
				cur = head;                             //摘节点
				head = head->_next;
	
				cur->_next = newhead;                   //插节点到新头
				newhead = cur;
			}
	
			return head = newhead;
		}
		
		
```



