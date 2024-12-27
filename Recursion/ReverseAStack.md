```C++
class Solution{
public:
    void insertAtBottom(stack<int> &St, int top){
        //base case
        if(St.empty()){
            St.push(top);
            return;
        }
        
        int temp=St.top();
        St.pop();
        insertAtBottom(St,top);
        St.push(temp);
    }
    void Reverse(stack<int> &St){
        //base case;
        if(St.empty())
        return;
        
        //task 1
        int top=St.top();
        St.pop();
        
        //recursive call;
        Reverse(St);
        insertAtBottom(St,top);
    }
    
};




```
