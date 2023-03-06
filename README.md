#define N 8

void printBoard(int board[N][N]) {
  for (int i = 0; i < N; i++) {
    for (int j = 0; j < N; j++) {
      cout << board[i][j] << " ";
    }
    cout << endl;
  }
}

bool isSafe(int board[N][N], int x, int y) {
  if (x >= 0 && x < N && y >= 0 && y < N && board[x][y] == -1) {
    return true;
  }
  return false;
}

bool solveKTUtil(int board[N][N], int x, int y, int movei) {
  if (movei == N*N) {
    printBoard(board);
    return true;
  }
  int xMove[] = {2, 1, -1, -2, -2, -1, 1, 2};
  int yMove[] = {1, 2, 2, 1, -1, -2, -2, -1};
  for (int k = 0; k < 8; k++) {
    int nextX = x + xMove[k];
    int nextY = y + yMove[k];
    if (isSafe(board, nextX, nextY)) {
      board[nextX][nextY] = movei;
      if (solveKTUtil(board, nextX, nextY, movei + 1)) {
        return true;
      }
      board[nextX][nextY] = -1;
    }
  }
  return false;
}

bool solveKT() {
  int board[N][N];
  memset(board, -1, sizeof(board));
  board[0][0] = 0;
  if (!solveKTUtil(board, 0, 0, 1)) {
    cout << "Solution does not exist." << endl;
    return false;
  }
  return true;
}
