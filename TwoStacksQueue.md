#### 用两个栈实现一个队列

	思路：栈的特点是先进后出，队列是先进先出。我们用两个栈刚好可以把顺序反过来实现类似队列的操作。我们可以设置栈 StackPush 
	
		 作为压入栈，压入的时候只往这个栈压入数据。StackPop 作为弹出栈。在弹出数据的时候只从这个栈弹出数据。
	
	
![image](http://hbimg.b0.upaiyun.com/b8f7544c4fca869aaefd7febac391e9bd7a12eb862fd-8oIAzo_fw658)


	注意：
	
			1.从StackPush往StackPop中压入数据的过程中，必须一次性全部压入StackPop中。
			
			2.如果StackPop不为空，则不能压入数据。
			
			违反这两点都会发生错误！！！
			


#### 代码

```cpp

	cpp code:
	
		# include <iostream>
		using namespace std;
		# include <stack>
		
		
		template<class T>
		class TwoStackQueue
		{
		public:
			void Push(const T& data)
			{
				StackPush.push(data);
			}
			void Pop()
			{
				if (StackPush.empty() && StackPop.empty())
				{
					cout << "Queue is empty !\n" << endl;
					return;
				}
		
				if (StackPop.empty())                     //如果StackPop不为空不压入
				{
					while (!StackPush.empty())            //必须一次性将StackPush的所有数据压入
					{
						T data = StackPush.top();
						StackPush.pop();
						StackPop.push(data);
					}
				}
		
				StackPop.pop();
			}
		
		private:
			stack<T> StackPush;         //压入栈
			stack<T> StackPop;          //弹出栈
		};
		
		
```




