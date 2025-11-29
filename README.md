# brewfile-2025

## 備忘

### macOS の Homebrew パッケージを一括で書き出して Brewfile を作る手順とよく使うコマンド例です。

手順（想定：macOS + Homebrew インストール済み）
1. ターミナルを開く
2. インストール済みのパッケージと cask を Brewfile に書き出す：
   ```
   brew bundle dump --file=~/Brewfile --force
   ```
   - これでホームディレクトリに Brewfile が作成されます。既存ファイルがある場合は --force で上書きします。

3. 必要なら不要なエントリを編集（手動でテキスト編集）

Brewfile からの復元（別のマシンへ移行する場合など）
1. Brewfile を転送してから実行：
   ```
   brew bundle --file=~/Brewfile
   ```

よく使うオプション・コマンド
- 現在の Homebrew の状態を確認：
  ```
  brew list
  brew list --cask
  brew leaves
  ```
- Brewfile を指定場所に保存：
  ```
  brew bundle dump --file=./Brewfile
  ```
- Brewfile に含める内容を制御する（例：タップのみ、cask を除外など）：
  - タップのみ：
    ```
    brew tap
    ```
  - cask を含めたくない場合は生成後に手動で cask 行を削除

Brewfile の例（参考）
```
tap "homebrew/core"
tap "homebrew/cask"

brew "git"
brew "wget"

cask "google-chrome"
cask "visual-studio-code"
```

備考
- brew bundle dump は tap・brew・cask・mas（App Store）・artifact などを自動で書き出します。
- Homebrew / macOS のバージョン違いで動作が異なることがあるため、移行先で brew update を先に実行します。


---
