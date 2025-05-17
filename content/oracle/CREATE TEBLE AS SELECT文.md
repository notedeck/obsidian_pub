---
tags: 
created: 2025-05-15T20:39
updated: 2025-05-17T20:19
---

## 構文
```
CREATE TABLE new_table_name AS
SELECT ... FROM old_table_name;
```


### 既存の employees 表から一部の列だけをコピーして新しい表を作成
```
CREATE TABLE emp_copy AS
SELECT employee_id, first_name, salary
FROM employees
WHERE department_id = 10;
```


###  列に別名を付けて作成
```
CREATE TABLE emp_summary AS
SELECT department_id AS dept_id, AVG(salary) AS avg_sal
FROM employees
GROUP BY department_id;

```

関数を使用する場合は列別名を必ずつけること

### データはコピーしないがテーブル構(NOT NULL制約、データ型)だけコピーする
```
CREATE TABLE emp_copy AS
SELECT employee_id, first_name, salary
FROM employees
WHERE 1 = 0
```

## 特徴

| 項目        | 内容                                 |
| --------- | ---------------------------------- |
| 列構造       | SELECTの列名とデータ型に基づく                 |
| データのコピー   | SELECT文の結果の**全行が新しい表に挿入される**       |
| 制約の引き継ぎ   | **制約（PRIMARY KEY、外部キーなど）は引き継がれない** |
| デフォルト値    | **DEFAULT句も引き継がれない**               |
| 列名        | SELECT句の別名（AS）を使えば、任意の列名を付けられる     |
| NULL制約の扱い | 明示的なNOT NULLでなければ基本的にNULL許容        |
| インデックスの扱い | インデックスは作成されない                      |
