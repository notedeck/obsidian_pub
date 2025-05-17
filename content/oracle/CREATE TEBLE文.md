---
tags:
  - oracle
created: 2025-05-15T20:39
updated: 2025-05-17T21:07
---
## 構文
```
CREATE TABLE table_name (
    column_name datatype [DEFAULT value] [CONSTRAINT constraint_name constraint_type],
    ...
    [CONSTRAINT constraint_name constraint_type (column_name, ...)]
);

```

### 例

```
CREATE TABLE employees (
    emp_id     NUMBER(5) CONSTRAINT emp_pk PRIMARY KEY,
    name       VARCHAR2(100) NOT NULL,
    hire_date  DATE DEFAULT SYSDATE,
    status     VARCHAR2(10)
        DEFAULT 'ACTIVE'
        CONSTRAINT status_chk CHECK (status IN ('ACTIVE', 'INACTIVE')),
    dept_id    NUMBER,
    CONSTRAINT emp_dept_fk FOREIGN KEY (dept_id) REFERENCES departments(dept_id)
);

```

## 注意点
### 制約の指定方法

|制約|列レベルで指定|表レベルで指定|備考|
|---|---|---|---|
|NOT NULL|可能|不可|必ず列レベルで指定する|
|UNIQUE|可能|可能|一意性を保証|
|PRIMARY KEY|可能|可能|主キー制約（NULL不可＋一意）|
|FOREIGN KEY|可能|可能|他テーブルの列との整合性を保つ|
|CHECK|可能|可能|条件に合致する値のみ許容|

### 制約名の指定（CONSTRAINT句）

- CONSTRAINT句で制約に名前を付けることができる。
- 名前を省略した場合、Oracleが自動で生成する。
- 複数の制約を1つの列に対して指定する場合、空白で区切る。
- 表レベル制約はカンマで区切って指定する。

### DEFAULT句に関する注意点
- 一部の組み込み関数（SYSDATE、SYSTIMESTAMP、USERなど）は使用可能。
- 任意のユーザー定義関数は使用できない。
- CHECK制約と組み合わせる順番は任意。DEFAULTを先に書く必要はない。

### CHECK制約の注意点
* 表レベルで指定する場合のみ複数列を使うことができる
* 条件の評価に使われる列が **NULL** の場合、CHECK制約は *違反にならない*
* UPPERなどの決定論的関数は使用可能
決定論的関数とは、同じ入力を与えれば常に同じ出力を返す関数

[deterministic functionってなんだ。 #小川メソッド - Qiita](https://qiita.com/kaizen_nagoya/items/c48dc77397be6b6ed683)


### その他のポイント

- 列名、テーブル名、制約名などは30文字以内にする（Oracleの制限）。
- テーブル作成時には、参照している外部キーのテーブルが既に存在している必要がある。
- 同じ列にNOT NULLとPRIMARY KEYを両方指定する必要はない（PRIMARY KEYに含まれる）。




