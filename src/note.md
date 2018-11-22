1. [Flexible array member](https://en.wikipedia.org/wiki/Flexible_array_member)

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

