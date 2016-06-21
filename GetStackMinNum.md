

------------------------------------------------------------------------------------------------------------------------------------------

	1.1：设计一个有getMin功能的栈

	题目：实现一个特殊栈，在实现栈的基本功能的基础上，在实现返回栈中最小元素的操作。

	要求：
		 （1）：Pop、Push、getMin的操作的时间复杂度是O(1)
		 （2）：设计的栈类型可以使用现成的栈结构

	思路：我们可以使用两个栈来保存数据，其中StackData用来保存正常的栈的数据，另一个StackMin用来保存当前栈中的最小值。

------------------------------------------------------------------------------------------------------------------------------------------



#### 解法一：
        先将数据压入StackData中，然后判断StackMin是否为空，为空则把data压入栈中；下一次进栈时，如果data的值小于或等
    于StackMin栈顶的值，则将data压入到StackMin中；如果data的值大于StackMin栈顶的值，则不用压栈。
        出栈的时候，将StackData的栈顶元素和StackMin的栈顶元素比较，如果StackData小于或等于StackMin的的栈顶元素栈顶
    元素，则同时Pop掉StackMin的栈顶元素，否则，只需要Pop掉StackData的栈顶元素。


```cpp

代码：
            # include <iostream>
            using namespace std;
            # include <vector>
            
            template<class T>
            class GetMinStackNum
            {
            public:
            	void PrintStack()
            	{
            		size_t size = StackData.size();
            
            		if (StackData.empty())
            		{
            			cout << "Stack is empty !" << endl;
            		}
            		else
            		{
            			size_t i = 0;
            			while (size--)
            			{
            				cout << "   " << StackData[i++] << endl;
            			}
            			cout << endl;
            		}
            	}
            
            	void Push(const T& data)
            	{
            		size_t size = StackMin.size();
            
            		if (0 == size)
            		{
            			StackData.push_back(data);
            			
            			if (StackMin.empty())
            			{
            				StackMin.push_back(data);
            			}
            		}
            		else
            		{
            			StackData.push_back(data);
            
            			if (data < StackMin[size - 1])
            			{
            				StackMin.push_back(data);
            			}
            		}
            	}
            
            	void Pop()
            	{
            		size_t size = StackMin.size();
            
            		if (StackData.size() > 0)
            		{
            			if (StackData[size - 1] =< StackMin[size - 1])
            			{
            				StackMin.pop_back();
            			}
            			StackData.pop_back();
            		}
            	}
            
            	T& getMin()
            	{
            		size_t size = StackMin.size();
            
            		if (StackMin.size() > 0)
            		{
            			return StackMin[size - 1];
            		}
            	}
            
            private:
            	vector<T> StackData;                //利用Vector维护的数据栈
            	vector<T> StackMin;                 //利用Vector维护的最小栈
            };

```

------------------------------------------------------------------------------------------------------------------------------------------

#### 解法二：
        同样使用两个栈来存储数据，却别在于，如果data的值大于StackMin栈顶的值得时候，将StackMin栈顶的值再压栈一次，这
    样我们在Pop的时候，就两个栈同时Pop不用做比较。


```cpp

代码：
            # include <iostream>
            using namespace std;
            # include <stack>
            
            template<class T>
            class GetMinStackNum
            {
            public:
            	void Push(const T& data)
            	{
            		StackData.push(data);
            		if (StackMin.empty())
            		{
            			StackMin.push(data);
            		}
            		else
            		{
            			if (data <= StackMin.top())
            				StackMin.push(data);
            			else
            				StackMin.push(StackMin.top());
            		}
            	}
            
            	void Pop()
            	{
            		if (StackData.empty())
            			cout << "Pop : The stack is empty !" << endl;
            		else
            		{
            			StackData.pop();
            			StackMin.pop();
            		}
            	}
            
            	T& getMin()
            	{
            		if (!StackMin.empty())
            			return StackMin.top();
            	}
            
            	void PrintStack()
            	{
            		size_t size = StackData.size();
            
            		if (0 == size)
            			cout << "PrintStack : The Stack is empty !" << endl;
            		else
            		{
            			stack<T> tmp = StackData;               //创建tmp避免打印栈的时候破坏掉原来的栈
            			while (size--)
            			{
            				cout << tmp.top() << endl;
            				tmp.pop();
            			}
            			cout << endl;
            		}
            	}
            
            private:
            	stack<T> StackData;                             //直接使用栈维护数据栈和最小栈
            	stack<T> StackMin;
            };


```

------------------------------------------------------------------------------------------------------------------------------------------

#### 比较：

        当数据元素的个数很多的时候，解法一的实现方法可以节省很多空间，但是每一次Pop的时候都会去比较，比较浪费时间。
        
    而解法二Pop的时候则不用比较，节省了时间，但是浪费掉了一部分空间。这也算一种典型的“以空间换时间的做法，提高的执
    
    行的效率”。共同点是这两种实现的方法都满足所有操作的时间复杂度是O(1)，空间复杂度是O(N)。


------------------------------------------------------------------------------------------------------------------------------------------


