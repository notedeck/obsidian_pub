---
created: 2025-03-27T16:12
updated: 2025-05-19T03:52
tags:
  - obsidian
---
 #問題解決 


`obsidian-simple-embeds` を使おうとして「有効化に失敗しました」と表示される場合、いくつかの原因が考えられます。

### **✅ 1. `main.js` が存在しない**

他のプラグインと違い、`obsidian-simple-embeds` フォルダには `main.js` ではなく `main.ts`（TypeScriptファイル）があります。  
これは **ビルドが必要** なことを意味します。

#### **🔧 解決策**

1. **Node.js をインストール**
    
    - [Node.js](https://nodejs.org/) をインストール（推奨: LTSバージョン）
        
2. **プラグインフォルダへ移動**  
    ターミナル（またはコマンドプロンプト）を開いて、以下のコマンドを実行：

```bash
cd <Vault>/.obsidian/plugins/obsidian-simple-embeds
```


3.  **必要なライブラリをインストール**
```bash
npm install
```
4. **プラグインをビルド** 

```bash
npm run build
```
- **生成された `main.js` を確認** `main.js` が `obsidian-simple-embeds` フォルダ内に生成されているか確認する。
    
- **Obsidianを再起動して、プラグインを有効化**