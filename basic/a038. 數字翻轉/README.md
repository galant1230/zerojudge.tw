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

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main() {
    char num[100];
    scanf("%s", num);

    int len = strlen(num);
    //練習一下malloc 
    char* reversed = (char*)malloc((len + 1) * sizeof(char));  // +1 給 \0

    // 反轉字串
    for (int i = 0; i < len; i++) {
        reversed[i] = num[len - 1 - i];
    }
    reversed[len] = '\0';  // 加上結尾的 \0

    int result = atoi(reversed);
    printf("%d\n", result);

    free(reversed);
    return 0;
}
```

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main() {
  char str[1000];
  scanf("%s", str);

  int len = strlen(str);

  // 反轉字串
  for (int i = 0; i < len / 2; i++) {
    char temp = str[i];
    str[i] = str[len - i - 1];
    str[len - i - 1] = temp;
  }

  // 轉換為整數，去除前導零
  int result = atoi(str);
  printf("%d\n", result);

  return 0;
}
```
