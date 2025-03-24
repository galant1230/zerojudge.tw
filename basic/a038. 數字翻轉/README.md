# a038. 數字翻轉
## 題目來源 : [a038. 數字翻轉](https://zerojudge.tw/ShowProblem?problemid=a038)
### 內容
輸入任意數字，並將其數字全部倒轉

### 輸入說明
輸入一行包含一個整數，且不超過 

### 輸出說明
輸出翻轉過後的數字

#### 範例輸入 #1
12345
#### 範例輸出 #1
54321
#### 範例輸入 #2
5050
#### 範例輸出 #2
505


---

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main() {
    char num[100];
    scanf("%s", num);

    int len = strlen(num);
    int* digits = (int*)malloc(len * sizeof(int));

    // 把每個數字轉成 int，倒著存
    for (int i = 0; i < len; i++) {
        digits[i] = num[len - 1 - i] - '0';
    }

    // 找到第一個不是 0 的位置
    int start = 0;
    while (start < len && digits[start] == 0) {
        start++;
    }

    // 如果全部都是 0（例如 0000）
    if (start == len) {
        printf("0\n");
    } else {
        for (int i = start; i < len; i++) {
            printf("%d", digits[i]);
        }
        printf("\n");
    }

    free(digits);
    return 0;
}
```
