# 数值类

| 类型        | 大小             | 范围（有符号）                                               | 范围（无符号）                                               | 用途               |
| ----------- | ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------ |
| TINYINT     | 1 byte           | (-128,127)                                                   | (0,255)                                                      | 小整数值           |
| SAMLLINT    | 2 bytes          | (-32768,32767)                                               | (0,65535)                                                    | 大整数值           |
| MEDIUMINT   | 3 bytes          | (-8 388 608，8 388 607)                                      | (0，16 777 215)                                              | 大整数值           |
| INT/INTEGER | 4 bytes          | (-2 147 483 648，2 147 483 647)                              | (0，4 294 967 295)                                           | 大整数值           |
| BIGINT      | 8 bytes          | (-9,223,372,036,854,775,808，9 223 372 036 854 775 807)      | (0，18 446 744 073 709 551 615)                              | 极大整数值         |
| FLOAT       | 4 bytes          | (-3.402 823 466 E+38，-1.175 494 351 E-38)，0，(1.175 494 351 E-38，3.402 823 466 351 E+38) | 0，(1.175 494 351 E-38，3.402 823 466 E+38)                  | 单精度<br />浮点数 |
| DOUBLE      | 8 bytes          | (-1.797 693 134 862 315 7 E+308，-2.225 073 858 507 201 4 E-308)，0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308) | 0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308) | 双精度<br />浮点数 |
| DECIMAL     | 实际是字符串类型 |                                                              |                                                              | 小数值             |

# 时间、日志类

| 类型      | 大小（bytes) | 范围                                    | 格式                | 用途            |
| --------- | ------------ | --------------------------------------- | ------------------- | --------------- |
| DATE      | 3            | 1000-01-01/9999-12-31                   | YYYY-MM-DD          | 日期            |
| TIME      | 3            | '-838:59:59'/'838:59:59'                | HH:MM:SS            | 时间            |
| YEAR      | 1            | 1901/2155                               | YYYY                | 年份值          |
| DATETIME  | 8            | 1000-01-01 00:00:00/9999-12-31 23:59:59 | YYYY-MM-DD HH:MM:SS | 时间日期        |
| TIMESTAMP | 4            | 1970-01-01 00:00:00/2038                | YYYY-MM-DD HH:MM:SS | 时间戳\时间日期 |



# 字符类