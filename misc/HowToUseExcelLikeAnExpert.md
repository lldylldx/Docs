#### 生成随机字，随机数字

```
=CHAR((INT(16+RAND()*38+160)*256)+int(94*RAND())+160)

随机小写字母：=CHAR(INT(RAND()*25+97))

随机大写字母：=CHAR(INT(RAND()*25+65))

随机数字：=CHAR(INT(RAND()*9+48))

=IF(ISBLANK(G2),"甲乙",LEFT(G2,LEN(G2)-1)&CHAR((INT(16+RAND()*38+160)*256)+int(94*RAND())+160))
```
