---
tags: 
created: 2025-05-15T20:39
updated: 2025-05-19T03:52
---
## trancate

表に格納された全ての行を削除

ロールバック不可

索引は削除される

read onlyの際削除できない

DDL

高速

## drop table

表を削除
索引は削除
ビューは消えない

制約も消える


read onlyの際削除できる

DDL

プラッシュバック可


delete

read onlyの際削除できない


ロールバック可

DML

![[Pasted image 20250517234946.png]]