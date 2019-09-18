# -165-Compare-Version-Numbers-[string]

*执行用时 :8 ms, 在所有 C++ 提交中击败了26.84%的用户*

*内存消耗 :8.7 MB, 在所有 C++ 提交中击败了5.66%的用户*

```c++
class Solution {
public:
    int compareVersion(string version1, string version2) {
        vector<int> v1,v2;
        for(int i=0,j;i<version1.size();i++){
            j=version1.find('.',i);
            if(j==string::npos)j=version1.size();
            //cout<<version1.substr(i,j-i)<<endl;
            v1.push_back(stoi(version1.substr(i,j-i)));
            i=j;
        }
        for(int i=0,j;i<version2.size();i++){
            j=version2.find('.',i);
            if(j==string::npos)j=version2.size();
            v2.push_back(stoi(version2.substr(i,j-i)));
            i=j;
        }
        while(v1.size()<v2.size())v1.push_back(0);
        while(v1.size()>v2.size())v2.push_back(0);
        for(int i=0;i<v2.size();i++){
            if(v1[i]!=v2[i])return v1[i]>v2[i]?1:-1;
        }
        return 0;
    }
};
```

