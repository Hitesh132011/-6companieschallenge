# -6companieschallenge
Complete the challnege with in 30 days

class Solution {
public:
int solve(vector<vector<vector<int>>>&dp,int k,vector<int>prices,int i,int b,int n)
{
    if(i==n || k==0)
    return 0;
    if(dp[i][b][k]!=-1)
    return dp[i][b][k];
    int profit=0;
    if(b==0)
    profit=max(-prices[i]+solve(dp,k,prices,i+1,1,n),solve(dp,k,prices,i+1,0,n));
    else
    profit=max(prices[i]+solve(dp,k-1,prices,i+1,0,n),solve(dp,k,prices,i+1,1,n));
    dp[i][b][k]=profit;
    return dp[i][b][k];
}
    int maxProfit(int k, vector<int>& prices) {
        int n=prices.size();
        vector<vector<vector<int>>> dp(n, vector<vector<int>>(2, vector<int>(k + 1, -1)));
        return solve(dp,k,prices,0,0,n);
    }
};
