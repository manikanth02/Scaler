[Construction Cost](https://www.scaler.com/academy/mentee-dashboard/class/56503/assignment/problems/9240?navref=cl_tt_lst_nm)


```

// This question is also based on Minimum Spanning Tree and can be solved using Kruskal's Algorithm.

#define p  pair<int,pair<int , int>>
int mod = 1e9 + 7;

int Solution::solve(int N, vector<vector<int> > &B) {

    vector<bool>visited(N + 1, false);
    vector<vector<pair<int,int>>>adjMatrix(N + 1);

    for(int i = 0; i < B.size(); i++){
        int u = B[i][0];
        int v = B[i][1];
        int w = B[i][2];

        adjMatrix[u].push_back({v,w});
        adjMatrix[v].push_back({u,w});
        
    }

    priority_queue<p,vector<p>,greater<p>>minHeap;

    for(int i = 0; i < adjMatrix[1].size(); i++){
        int v = adjMatrix[1][i].first;
        int w = adjMatrix[1][i].second;
        minHeap.push({w, {1, v}});
    }
    visited[1] = true;
    int cost = 0;

    while(minHeap.size() > 0){
        auto ele = minHeap.top();
        minHeap.pop();

        int w = ele.first;
        int u = ele.second.first;
        int v = ele.second.second;

        if(visited[u] == true && visited[v] == true){
            continue;
        }

        if(visited[v] == true){
            continue;
        }
        cost = (cost + w)%mod;
        visited[v] = true;

        for(int i = 0; i < adjMatrix[v].size(); i++){
            minHeap.push({adjMatrix[v][i].second, {v,adjMatrix[v][i].first}});
        }

    } 
    return cost;
}



```
