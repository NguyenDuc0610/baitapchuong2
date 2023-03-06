#define N 8

void printBoard(int board[N][N]) {
  for (int i = 0; i < N; i++) {
    for (int j = 0; j < N; j++) {
      cout << board[i][j] << " ";
    }
    cout << endl;
  }
}

bool isSafe(int board[N][N], int row, int col) {
  // Kiểm tra hàng
  for (int i = 0; i < col; i++) {
    if (board[row][i]) {
      return false;
    }
  }
  // Kiểm tra đường chéo chính
  for (int i = row, j = col; i >= 0 && j >= 0; i--, j--) {
    if (board[i][j]) {
      return false;
    }
  }
  // Kiểm tra đường chéo phụ
  for (int i = row, j = col; i < N && j >= 0; i++, j--) {
    if (board[i][j]) {
      return false;
    }
  }
  return true;
}

bool solveNQueens(int board[N][N], int col) {
  if (col == N) {
    printBoard(board);
    return true;
  }
  bool res = false;
  for (int i = 0; i < N; i++) {
    if (isSafe(board, i, col)) {
      board[i][col] = 1;
      res = solveNQueens(board, col + 1) || res;
      board[i][col] = 0;
    }
 
