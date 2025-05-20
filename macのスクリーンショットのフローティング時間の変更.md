---
created: 2025-05-20T23:08
updated: 2025-05-20T23:10
---

## やり方
ターミナルを起動し以下のコマンドを実行するだけ

```
defaults write com.apple.screencaptureui "thumbnailExpiration" -float 3 && killall SystemUIServer
```

デフォルトだと5秒くらい。

必要があr