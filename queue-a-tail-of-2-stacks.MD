### Queues: A Tale of Two Stacks

<https://www.hackerrank.com/challenges/ctci-queue-using-two-stacks>

```C++
class MyQueue {
  
    public:
        stack<int> stack_newest_on_top, stack_oldest_on_top;   
        void push(int x) {
            stack_newest_on_top.push(x);
        }

        void pop() {
            MoveToOldest();
            
            if (!stack_oldest_on_top.empty()) {
                stack_oldest_on_top.pop();
            }
        }

        int front() {
            MoveToOldest();

            return stack_oldest_on_top.top();
        }
    
    private:
        void MoveToOldest() {
            if (!stack_oldest_on_top.empty()) {
                return;
            }

            while (!stack_newest_on_top.empty()) {
                int item = stack_newest_on_top.top();
                stack_newest_on_top.pop();
                stack_oldest_on_top.push(item);
            }
        }
};
```
