---
title: qiita-cli使い方法（初心者向け）
tags:
  - Qiita
  - GitHub
  - 初心者
  - qiita-cli
private: false
updated_at: '2025-08-14T00:25:14+09:00'
id: 1fb540a19ab6c2c7baea
organization_url_name: null
slide: false
ignorePublish: false
---

# qiita-cli使い方法（初心者向け）

Qiita CLI を使うと、手元の環境でQiitaの記事を執筆・プレビュー・投稿できます。普段お使いのエディタで記事を管理できるようになるため、より効率的に記事作成を進められます。

## 1. 事前準備

Qiita CLI を利用するには、Node.js 20.0.0 以上が必要です。

まだインストールしていない場合は、Node.jsの公式サイトからインストールしてください。

## 2. Qiita CLI のインストール

Qiita のコンテンツを管理したいディレクトリ（例: `/Users/username/qiita-kiji`）で、以下のコマンドを実行して Qiita CLI をインストールします。

```bash
npm install @qiita/qiita-cli --save-dev
```

インストールが完了したら、以下のコマンドでバージョンが表示されるか確認してください。

```bash
npx qiita version
```

## 3. Qiita CLI のセットアップ

以下のコマンドを実行すると、`.gitignore`、GitHub Actions のワークフローファイル、ユーザー設定ファイル（`qiita.config.json`）が生成されます。

```bash
npx qiita init
```

## 4. Qiita トークンの発行とログイン

Qiita CLI を利用して記事の取得や投稿、更新を行うには、Qiita の個人用アクセストークンが必要です。

1. Qiita の設定ページ [https://qiita.com/settings/tokens/new/](https://qiita.com/settings/tokens/new) にアクセスし、新しいトークンを発行します。
2. アクセストークンの説明には任意のテキストを設定し、スコープは `read_qiita` と `write_qiita` にチェックを入れてください。
3. 発行されたトークンをコピーし、以下のコマンドでログインします。

```bash
npx qiita login
```

プロンプトが表示されたら、コピーしたトークンを入力して Enter キーを押してください。

## 5. 記事のプレビュー

記事の執筆中は、ブラウザでリアルタイムにプレビューを確認できます。以下のコマンドを実行すると、Qiita に投稿している記事がダウンロードされ、プレビューサーバーが起動します。

```bash
npx qiita preview
```

デフォルトでは `http://localhost:8888` でプレビュー画面にアクセスできます。

## 6. 記事ファイルの管理

Qiita CLI では、1つの記事を1つのMarkdownファイル（`.md`）で管理します。

記事ファイルは `public` ディレクトリ内に配置する必要があります。

例:
```
.
└─ public
   ├── newArticle001.md
   └── newArticle002.md
```

### 新規記事の作成

Qiita Preview 上の「新規記事作成」ボタンを利用するか、以下のコマンドで新しい記事ファイルを作成できます。

```bash
npx qiita new [記事のファイルのベース名]
```

例: `npx qiita new my-first-article` とすると、`public/my-first-article.md` が作成されます。

### 記事の投稿・更新

記事の内容を変更し、GitHubリポジトリにプッシュすると、GitHub Actions が自動で実行され、Qiita に記事が投稿・更新されます。

Qiita 上との差分があるMarkdownファイルのみが反映されます。

### 記事の削除

Qiita CLI を使った記事の管理では、安全のため記事の削除はできません。Qiita 上から直接記事を削除してください。

これで、Qiita CLI を使って記事を管理する基本的な準備が整いました。快適な執筆ライフをお楽しみください！❤️

## Reference

参考文献：

- [Qiitaの記事をGitHubリポジトリで管理する方法](https://qiita.com/Qiita/items/32c79014509987541130)
- [Qiita CLIのREADME](https://github.com/increments/qiita-cli/blob/main/README.md)
- [Qiitaヘルプ](https://help.qiita.com/entries/236000000000000000)
