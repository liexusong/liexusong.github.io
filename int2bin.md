```C
#include <stdio.h>
#include <stdlib.h>

void int2bin(int num)
{
    int len = sizeof(int);
    char *p = (char *)&num;
    int i, j;
    char c;

    for (i = len - 1; i >= 0; i--) {
        c = p[i];
        for (j = 7; j >= 0; j--) {
            if (c & (1 << j)) {
                printf("%d", 1);
            } else {
                printf("%d", 0);
            }
        }
        printf(" ");
    }
    printf("\n");
}


int main(int argc, char *argv[])
{
    if (argc != 2) {
        printf("Invaild options: int2bin <number>\n");
        exit(0);
    }

    int2bin(atoi(argv[1]));

    return 0;
}
```