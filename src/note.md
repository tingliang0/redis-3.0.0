# Flexible array member

```C
typedef char *sds;

struct sdshdr {
    unsigned int len;
    unsigned int free;
    char buf[];
};

static inline size_t sdslen(const sds s) {
    struct sdshdr *sh = (void*)(s-(sizeof(struct sdshdr)));
    return sh->len;
}
```
Flexible array member是C99的一个特性，标志是struct最后一个字段是一个未指定大小的array，当使用sizeof时，最后一个字段视为0。

wiki
[Flexible array member](https://en.wikipedia.org/wiki/Flexible_array_member)


# stdarg
```C
#include <stdarg.h>

void va_start(va_list ap, last);
type va_arg(va_list ap, type);
void va_end(va_list ap);
void va_copy(va_list dest, va_list src);
```
C语言如何实现可变参数列表，`man stdarg`

