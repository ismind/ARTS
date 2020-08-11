有两三周没写，主要是没有抽出时间，重新拾起来，继续计算天数

## T:
1. 最近遇到数据在查询时，怎么都得不到正确结果，原来数据带有空格，trim就好了。
2. 查询带逗号分隔的字符串， instr(',' || 入参 || ',','' || 列名 || ',')
3. 建游标语句，需要改相应的用户：
```javascript
create or replace package dmp.types
as
type cursortype is ref cursor;
end;
```
4. 执行F8，存储过程编译报错——不存在这张表，但是表确实存在，原来是该用户权限不足。
