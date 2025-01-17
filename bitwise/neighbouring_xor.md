```C++
class Solution {
public:
    bool doesValidArrayExist(vector<int>& derived) {
        // approach since binary let's try out both ways
        // no need to keep a vector, just have the start value, end value
        int n=derived.size();
        // starting from taking as 0
        int start=0,curr=0,next=0;
        for(int i=0;i<n-1;++i){
            if(derived[i]==1){
                if(curr==0){
                    next=1; //because is start 0, then next has to be 1
                    curr=next;
                }else{
                    next=0;
                    curr=next;
                }
            }else{
                next=curr;
            }
        }

        if(derived[n-1]==1){
            if(curr != start)
            return true;
        }else{
            if(curr==start)
            return true;
        }

        return false;
    }
};

/*THE LAST ONE IS THE DECISIVE ONE*/
```