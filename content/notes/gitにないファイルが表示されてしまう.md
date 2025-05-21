---
created: 2025-05-21T20:32
updated: 2025-05-21T20:36
tags:
  - git
  - quartz
---
前にビルドした結果が残ってしまうのが原因。

deploy.ymlに追記する

```
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
      - run: npm install -g pnpm
      - run: pnpm install
      - run: pnpm quartz build
      - uses: actions/upload-pages-artifact@v3
        with:
          path: public
```

```
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
      - run: npm install -g pnpm
      - run: pnpm install
      - name: Clean public folder # この2行を追記
        run: rm -rf public/* # この2行を追記
      - run: pnpm quartz build
      - uses: actions/upload-pages-artifact@v3
        with:
          path: public
```
