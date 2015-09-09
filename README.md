## libtable

libtable is a tiny C library for generating
pretty-printed ascii tables.

### Installation

```sh
git clone https://github.com/marchelzo/libtable.git && \
cd libtable && \
make && sudo make install
```

### Example usage

```c
#include <table.h>

int main(void) {
        struct table t;

        table_init(
                &t,
                "Name",  "%s",
                "Age",   "%d",
                "Score", "%.2f",
                NULL
        );

        table_add(
            &t,
            "test this text is going to be really long so as "
            "to potentially find problems in the table drawing "
            "algorithm. it is very long haha "
            "long text long text long text",
            36,
            3.1
        );
        table_add(&t, "Ξεσκεπάζωτὴνψυχοφθόραβδελυγμία", 36, 3.1);
        table_add(&t, "Ξεσκεπάζω τὴν ψυχοφθόρα βδελυγμία", 36, 3.1);
        table_add(&t, "Bob", 18, 1.3123);
        table_add(&t, "Alice", 20, 6.43);
        table_add(&t, "Roger", 18, 12.45);
        table_add(&t, "Larry", 59, 12.52);
        table_add(&t, "Ё Ђ Ѓ Є Ѕ І Ї Ј Љ", 21, 14.12312312);

        table_print(&t, 80, stdout);

        table_free(&t);

        return 0;
}
```

#### Output

```
+------------------------------------------------------------------------------+
| Name                                                           | Age | Score |
*------------------------------------------------------------------------------*
| test this text is going to be really long so as to potentially | 36  | 3.10  |
| find problems in the table drawing algorithm. it is very long  |     |       |
| haha long text long text long text                             |     |       |
|----------------------------------------------------------------|-----|-------|
| Ξεσκεπάζωτὴνψυχοφθόραβδελυγμία                                 | 36  | 3.10  |
|----------------------------------------------------------------|-----|-------|
| Ξεσκεπάζω τὴν ψυχοφθόρα βδελυγμία                              | 36  | 3.10  |
|----------------------------------------------------------------|-----|-------|
| Bob                                                            | 18  | 1.31  |
|----------------------------------------------------------------|-----|-------|
| Alice                                                          | 20  | 6.43  |
|----------------------------------------------------------------|-----|-------|
| Roger                                                          | 18  | 12.45 |
|----------------------------------------------------------------|-----|-------|
| Larry                                                          | 59  | 12.52 |
|----------------------------------------------------------------|-----|-------|
| Ё Ђ Ѓ Є Ѕ І Ї Ј Љ                                              | 21  | 14.12 |
+------------------------------------------------------------------------------+
```
