------------------------

* [删除链表的中间节点(RemoveMidNode)](#删除链表的中间节点)
* [删除链表a/b处的节点(Removea/bNode)](#扩展)

------------------------


<br>

#### 删除链表的中间节点

    给定指向链表第一个节点的指针 head ，实现删除链表的中间节点的函数。
    
    例如：
        
        不删除任何节点。
        1->2, 删除节点1。
        1->2->3, 删除节点2。
        1->2->3->4, 删除节点2。
        1->2->3->4->5, 删除节点3。



#### 代码

```cpp

    cpp code:
    
        Node* RemoveMidNode(Node*& head)
    	{
    		if (head == NULL || head->_next == NULL)
    			return head;
    
    		int count = 0;                    //记录链表节点个数
    		Node* cur = head;
    
    		while (cur)
    		{
    			++count;
    			cur = cur->_next;
    		}
    
    		if (2 == count)                    //只有两个节点的情况
    		{
    			Node* next = head->_next;
    			delete head;
    			head = next;
    
    			return head;
    		}
    
    		int del = count / 2 + 1;           //两个以上的节点
    		Node* prev = NULL;
    		cur = head;
    		
    		while (--del)
    		{
    			prev = cur;
    			cur = cur->_next;
    		}
    		prev->_next = cur->_next;
    		delete cur;
    		cur = NULL;
    		
    		return head;
    	}
        
        
        
```


<br>

#### 扩展：

    删除链表a/b处的节点：
    
    给定链表指向第一个节点的指针 head 、整数 a 和 b ,实现删除位于 a/b 处节点的函数。
    
    例如：
        
        链表： 1-> 2-> 3-> 4-> 5 , 假设 a/b 的值为 r。
        如果 r 等于 0 ，不删除任何节点。
        如果 r 在区间(0， 1/5]上，删除节点1；
        如果 r 在区间(1/5， 2/5]上，删除节点2；
        如果 r 在区间(2/5， 3/5]上，删除节点3；
        如果 r 在区间(3/5， 4/5]上，删除节点4；
        如果 r 在区间(4/5， 1]上，删除节点5；
        如果 r 大于 1 ,不删除任何节点。
        


#### 代码

```cpp

    cpp code:
    
        Node* RemoveaDivbNode(Node*& head, int a, int b)
    	{
    		if (a<1 || a>b)    
    			return head;
    
    		Node* cur = head;
    		int n = 0;
    
    		while (cur)
    		{
    			++n;
    			cur = cur->_next;
    		}
    
    		n = (int)((double(n*a)) / (double(b)));
    
    		if (1 == n)
    		{
    			Node* next = head->_next;
    			delete head;
    			head = next;
    		}
    		else
    		{
    			Node* prev = NULL;
    			cur = head;
    
    			while (--n)
    			{
    				prev = cur;
    				cur = cur->_next;
    			}
    
    			prev->_next = cur->_next;
    			delete cur;
    			cur = NULL;
    		}
    
    		return head;
    	}
        
        
    
```



