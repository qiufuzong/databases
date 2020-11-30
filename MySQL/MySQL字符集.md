

# character

MySQL 8.0版本 默认字符集 utf8mb4

mb4的意思是 most byte 4 专门用来兼容4字节的unicode.

所以utf8mb4是utf8的扩展版，支持更多的字码类型，并且兼容。但是utf8相对utf8mb4更省空间。







# collation(collate)

MySQL 8.0版本 默认字符集 utf8mb4

排序规则，用于指定数据如何排序，以及字符串的比对规则。

比如varchar、char、text 字符类型的列，都需要一个collate 类型来告诉MySQL如何对该列进行排序和比较。

**collate会影响到`ORDER BY`语句的排序，会影响到`WHERE`条件中大于小于筛选出来的结果，也会影响`DISTINCT`、`GROUP BY`、`HAVING`语句的查询结果，如果索引类型是字符类型，也会被影响，总而言之，凡是涉及到字符类型比较和排序的都和collate有关**



utf8_unicode_ci比较准确，utf8_general_ci速度比较快。通常情况下 utf8_general_ci的准确性就够我们用的了，在我看过很多程序源码后，发现它们大多数也用的是utf8_general_ci，所以新建数据库时一般选用utf8_general_ci就可以了
如果是utf8mb4那么对应的就是 utf8mb4_general_ci utf8mb4_unicode_ci

```mysql
-- 查看COLLATION
SHOW COLLATION;
```
