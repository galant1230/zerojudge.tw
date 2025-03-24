# a015. 矩陣的翻轉
## [a015. 矩陣的翻轉](https://zerojudge.tw/ShowProblem?problemid=a015)

內容
已知一(m x n)矩陣A，我們常常需要用到另一個將A中之行與列調換的矩陣。這個動作叫做矩陣的翻轉。舉例來說，若
```markdown
A =
3 1 2
8 5 4

AT =
3 8	
1 5
2 4
``` 

現在 請您針對所讀取到的矩陣進行翻轉。

### 輸入說明
第一行會有兩個數字，分別為 列(row)<100 和 行(column)<100，緊接著就是這個矩陣的內容

### 輸出說明
直接輸出翻轉後的矩陣

#### 範例輸入 #1
```markdown
2 3
3 1 2
8 5 4
```

#### 範例輸出 #1
```markdown
3 8
1 5
2 4
```

### 提示 ：
* 測資檔會包含多組矩陣資料

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int row, col;

    while (scanf("%d %d", &row, &col) != EOF) {
        // 動態配置記憶體
        int **matrix = (int **)malloc(row * sizeof(int *));
        for (int i = 0; i < row; i++) {
            matrix[i] = (int *)malloc(col * sizeof(int));
        }

        // 輸入矩陣
        for (int i = 0; i < row; i++) {
            for (int j = 0; j < col; j++) {
                scanf("%d", &matrix[i][j]);
            }
        }

        // 輸出轉置矩陣
        for (int j = 0; j < col; j++) {
            for (int i = 0; i < row; i++) {
                printf("%d ", matrix[i][j]);
            }
            printf("\n");
        }

        // 釋放記憶體
        for (int i = 0; i < row; i++) {
            free(matrix[i]);
        }
        free(matrix);
    }

    return 0;
}
```
