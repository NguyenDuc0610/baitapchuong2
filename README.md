void hoanVi(int arr[], bool mark[], int n, int len) {
  if (len == n) {
    // In ra hoán vị tương ứng với arr
    for (int i = 0; i < n; i++) {
      cout << arr[i] << " ";
    }
    cout << endl;
    return;
  }
  for (int i = 1; i <= n; i++) {
    if (!mark[i]) {
      mark[i] = true;
      arr[len] = i;
      hoanVi(arr, mark, n, len + 1);
      mark[i] = false;
      arr[len] = 0;
    }
  }
}
