# todo-cli

`todo` は、[GitHub CLI (gh)](https://cli.github.com/) をラップして、特定の GitHub リポジトリやプロジェクトの Issue 管理を爆速にするシェルスクリプトです。

---

## 1. 前提条件 (GitHub CLI のセットアップ)

このツールは内部で **GitHub CLI (`gh`)** を使用します。まだインストールしていない場合は、以下の手順でセットアップを完了させてください。

### インストール
OSに合わせて以下のコマンドを実行してください。

* **macOS**:
    ```bash
    brew install gh
    ```
* **Linux (Debian/Ubuntu系)**:
    ```bash
    sudo apt update && sudo apt install gh
    ```
* **Windows (PowerShell/Winget)**:
    ```bash
    winget install --id GitHub.cli
    ```

### 認証 (必須)
インストール後、GitHub アカウントでログインする必要があります。
```bash
gh auth login
```

> **Note**: プロンプトに従ってブラウザ経由またはトークンで認証を完了させてください。`gh issue list` などのコマンドが正常に動くようになれば準備完了です。

---

## 2. インストール方法

1. このリポジトリをクローンするか、`todo` スクリプトをダウンロードします。
2. スクリプトに実行権限を付与します。
```bash
chmod +x todo

```


3. パスの通ったディレクトリ（例: `/usr/local/bin`）に配置して、どこからでも呼び出せるようにします。
```bash
sudo mv todo /usr/local/bin/

```



---

## 3. 設定方法

使用するリポジトリとプロジェクトを指定するために、`.bashrc` や `.zshrc`（使用しているシェルの設定ファイル）に以下の環境変数を追記してください。

```bash
# 必須：対象のリポジトリ (ユーザー名/リポジトリ名)
export TODO_REPO="your-user/your-repo"

# 任意：対象のプロジェクト名 (GitHub上のプロジェクトボード名)
export TODO_PROJECT="Your Project Name"

```

設定を反映させるのを忘れないでね！

```bash
source ~/.zshrc  # zshの場合

```

---

## 4. 使い方

| コマンド | 内容 |
| --- | --- |
| `todo -h` | ヘルプを表示 |
| `todo -c` | 新しい Issue を作成（対話モード） |
| `todo -l` | 全ての Issue を一覧表示（Open & Closed） |
| `todo -lo` | 未完了 (Open) の Issue のみ表示 |
| `todo -lc` | 完了済 (Closed) の Issue のみ表示 |
| `todo -done [ID]` | 指定した Issue ID を一括クローズ |

### 使用例

```bash
# タスクを登録する
todo -c

# 終わっていないタスクを確認する
todo -lo

# ID 12 と 15 のタスクを一気に完了にする
todo -done 12 15

```

---

