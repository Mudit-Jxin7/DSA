```
class Solution {
public:
    bool isPossible(vector<string> &board , int row , int col , int n){
        int dupRow = row;
        int dupCol = col;

        //upper diagonal
        while(row >= 0 && col >= 0){
            if(board[row][col] == 'Q') return 0;
            row--;
            col--;
        }

        //lower diagonal
        row = dupRow;
        col = dupCol;

        while(col >= 0 && row < n){
            if(board[row][col] == 'Q') return 0;
            row++;
            col--;
        }

        //left side
        row = dupRow;
        col = dupCol;

        while(col >= 0){
            if(board[row][col] == 'Q') return 0;
            col--;
        }

        return 1;

    }

    void f(int col , vector <string> &board , vector<vector<string>> &ans , int n){
        if(col == n){
            ans.push_back(board);
            return;
        }

        for(int row = 0 ; row < n ; row++){
            if(isPossible(board , row , col , n)){
                board[row][col] = 'Q';
                f(col + 1 , board , ans , n);
                board[row][col] = '.';
            }
        }
    }

    vector<vector<string>> solveNQueens(int n) {
        vector<vector<string>> ans;
        vector <string> board(n);
        string s(n , '.');
        for(int i = 0 ; i < n ; i++){
            board[i] = s;
        }

        f(0 , board , ans , n);
        return ans;         
    }
};
