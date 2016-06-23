#### 用一个栈实现另一个栈的排序

	要求：一个栈中元素类型为整型，现在想要把该栈中从栈顶到栈底的元素按照从大到小排序，只允许申请一个栈。除此之外，
	     
	      可以申请新变量，但不能申请额外的数据结构。
	      
<br>

	思路：要源栈记作 StackSort, 申请一个栈 StackHelp, 先将 StackSrc 的栈顶元素压入 StackHelp, 下一次压入的时候将元
	
		  素和 StackHelp 的栈顶元素比较，如果比栈顶元素小，则压栈。否则将 StackHelp 的栈顶元素弹出，继续进行比较。
		  
		  重复上述过程，知道 StackSrc 为空时，再将 StackHelp 的元素依次压入 StackSrc 即完成排序。
		  
		  

#### 代码

```cpp

	cpp code:
	
		# include <iostream>
		using namespace std;
		# include <stack>
		
		void SortStackByStack(stack<int>& StackSrc)
		{
			stack<int> StackHelp;
		
			while (!StackSrc.empty())                               //从小到大排序
			{
				int cur = StackSrc.top();
				StackSrc.pop();
		
				while (!StackHelp.empty() && cur > StackHelp.top())
				{
					int tmp = StackHelp.top();
					StackHelp.pop();
					StackSrc.push(tmp);
				}
		
				StackHelp.push(cur);
			}
		
			while (!StackHelp.empty())                              //将有序栈逆序
			{
				int top = StackHelp.top();
				StackHelp.pop();
				StackSrc.push(top);
			}
		}
		
		
		
```

