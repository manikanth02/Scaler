[Array with Consectuvies Elements](https://www.scaler.com/academy/mentee-dashboard/class/34517/assignment/problems/4072?navref=cl_tt_nv)


```
int Solution::solve(vector<int> &A) {
    sort(A.begin(),A.end());
    for(int i = 1; i < A.size(); i++){
        if(A[i] != A[i - 1] + 1)return 0;
    }
    return 1;
}


```
