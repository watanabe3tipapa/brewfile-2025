# brewfile-2025

## 概要

macOS の Homebrew に関する備忘録です。インストール済みのパッケージや cask を一括で書き出して Brewfile を作成する手順や、Brewfile からパッケージを復元する際によく使うコマンド例をまとめています。

## 前提

- 対象は macOS 環境で、Homebrew がインストール済みであることを想定しています（想定環境はREADME内の手順に明記されています）。

## 使い方（基本手順）

### インストール済みパッケージと cask を Brewfile に書き出す

1. ターミナルを開く
2. 次のコマンドでホームディレクトリに Brewfile を作成します（既存ファイルがある場合は --force で上書きします）：

```bash
brew bundle dump --file=~/Brewfile --force
```

3. 必要なら生成された Brewfile をテキストエディタ等で手動編集して不要なエントリを削除してください。

### Brewfile から復元する（別のマシンへ移行する場合など）

1. Brewfile を移行先マシンに転送する
2. 次のコマンドを実行して Brewfile に記載の内容をインストールします：

```bash
brew bundle --file=~/Brewfile
```

## よく使うコマンド例

- 現在の Homebrew の状態確認：

```bash
brew list
brew list --cask
brew leaves
```

- Brewfile をカレントディレクトリなど指定の場所に保存：

```bash
brew bundle dump --file=./Brewfile
```

- Brewfile に含める内容を制御する際の補助
  - タップ一覧の確認：

```bash
brew tap
```

  - cask を含めたくない場合は生成後に手動で Brewfile 内の cask 行を削除してください。

## Brewfile の例

参考例としての記述例：

```
tap "homebrew/core"
tap "homebrew/cask"

brew "git"
brew "wget"

cask "google-chrome"
cask "visual-studio-code"
```

## 備考 / 注意点

- brew bundle dump は tap・brew・cask・mas（App Store）・artifact などを自動で書き出します（Homebrew 側の動作に依存します）。
- Homebrew / macOS のバージョン差により動作が異なることがあるため、移行先で事前に brew update を実行することが推奨されます。

## リポジトリ構成（確認できるもの）

- ルートに含まれるファイル例：
  - MBP04
  - README.md

## 開発・保守状態

- GitHub リポジトリはアーカイブされていません（公開リポジトリ）。
- デフォルトブランチ: main
- 主な言語（リポジトリ情報に基づく）: Ruby

## ライセンス

- README 内およびリポジトリ情報から特定のライセンス情報は確認できませんでした。ライセンス情報を確認するにはリポジトリ内の LICENSE ファイル等をご確認ください。
