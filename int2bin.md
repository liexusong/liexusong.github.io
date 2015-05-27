```C
#include <stdio.h>
#include <stdlib.h>

int hex2bin(char *hex)
{
	int len = strlen(hex);
	char *sta, *cur, *end;
	int num = 0, multiple = 1;

	if (len < 3 || hex[0] != '0' || hex[1] != 'x') {
		return 0;
	}

	sta = hex + 2;
	cur = hex + len - 1;

	while (cur >= sta) {
		if (*cur >= '0' && *cur <= '9') {
			num += (*cur - '0') * multiple;
		} else if (*cur >= 'a' && *cur <= 'f') {
			num += (*cur - 'a' + 10) * multiple;
		} else if (*cur >= 'A' && *cur <= 'F') {
			num += (*cur - 'a' + 10) * multiple;
		} else {
			return 0;
		}

		cur--;
		multiple *= 10;
	}

	return num;
}

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
