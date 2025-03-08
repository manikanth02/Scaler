[Pair Sum Divisible by M](https://www.scaler.com/academy/mentee-dashboard/class/34490/assignment/problems/4110/?navref=cl_pb_nv_tb)

```

int MOD = 1e9 + 7;
int Solution::solve(vector<int> &A, int B) {
    int n = A.size();
    //Size of frequency array is B - 1
    vector<int>frequency(B,0);

    //Store frequency
    for(int i = 0; i < n; i++){
        frequency[A[i]%B]++;
    }

    long long ans = 0;
    int x = frequency[0];
    //case 1 => counts of pairs whose remainder is 0
    ans = (ans + ((1LL * x * (x - 1))/2)%MOD)%MOD;

    //case 2 => counts of pairs whose remainder is B/2
    if(B % 2 == 0){
        x = frequency[B/2];
        ans = (ans + ((1LL * x * (x-1))/2)%MOD)%MOD;
    }
    
    int i = 1;
    int j = B - 1;

    while(i < j){
        ans = (ans + frequency[i]*frequency[B - i])%MOD;
        i++;
        j--;
    }
    return ans;
}


```
