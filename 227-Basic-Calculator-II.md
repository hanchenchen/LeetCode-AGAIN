# 227-Basic-Calculator-II

*执行用时 :40 ms, 在所有 C++ 提交中击败了15.47%的用户*

*内存消耗 :10.9 MB, 在所有 C++ 提交中击败了38.19%的用户*

```c++
class Solution {
public:
    int calculate(string s) {
        s=s+"+";
        stack<int> num,op;
        unordered_map<char,int> prio;
        prio['+']=prio['-']=1;
        prio['/']=prio['*']=2;
        for(int i=0,j;i<s.size();){
            while(i<s.size()&&!isdigit(s[i]))i++;
            if(i==s.size())break;
            j=i;
            while(isdigit(s[j])||isblank(s[j]))j++;
            int x=stoi(s.substr(i,j-i));
            num.push(x);
            //cout<<x<<" "<<s.substr(i,j-i)<<endl;
            //cout<<(!op.empty()&&prio[op.top()]>=prio[s[j]])<<endl;
            while(!op.empty()&&prio[op.top()]>=prio[s[j]]){
                int b=num.top();num.pop();
                int a=num.top();num.pop();
                if(op.top()=='+'){
                    num.push(a+b);
                }else if(op.top()=='-'){
                    num.push(a-b);
                }else if(op.top()=='*'){
                    num.push(a*b);
                }else if(op.top()=='/'){
                    num.push(a/b);
                }
                op.pop();
            }
            op.push(s[j]);
            i=j;
        }
        return num.top();
    }
};
```

