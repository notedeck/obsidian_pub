---
created: 2025-05-20T23:08
updated: 2025-05-20T23:15
---

## やり方
ターミナルを起動し以下のコマンドを実行するだけ。

```
defaults write com.apple.screencaptureui "thumbnailExpiration" -float 3 && killall SystemUIServer
```

デフォルトだと5秒くらい。

必要が上のコマンドの3の部分を好きな秒数に変更する

フローティングがいらないのであれば
```
defaults write com.apple.screencapture show-thumbnail -bool false && killall SystemUIServer
```
かもしくはcommad shift 5でオプションから「フローティングサムネイルを表示」のチェックボタンを外せば良い