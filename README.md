# N-Queen-s-Problem-leetcode
With the help of recurssion i solved n-queeen's problem.


class Solution {
public:
bool isvalid(vector<string>& board,int row,int col,int n){
    // upward
    for(int i=row-1;i>=0;i--){
        if(board[i][col]=='Q') return false;
    }
    // left diagonal
    for(int i=row-1,j=col-1 ; i>=0 && j>=0; i--,j--){
        if(board[i][j]=='Q') return false;
    }
    // right diagonal
    for(int i=row-1,j=col+1 ; i>=0 && j<n; i--,j++){
        if(board[i][j]=='Q') return false;
    }
    return true;
}
    void explore(vector<vector<string>>& ans,int n,int row,vector<string>& board){
        if(row>=n){
            ans.push_back(board);
            return;
        }
        for(int col=0;col<n;col++){
            if(isvalid(board,row,col,n)){
                board[row][col]='Q';
                explore(ans,n,row+1,board);
                board[row][col]='.';  
            }
        }

    }
    vector<vector<string>> solveNQueens(int n) {
       vector<vector<string>>ans;
       vector<string>board(n,string(n,'.'));
       explore(ans,n,0,board);
       return ans;

    }
};
