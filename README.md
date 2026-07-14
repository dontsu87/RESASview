# 人吉市 RESASメッシュ静的デモ

人吉市の250mメッシュについて、分析ワークスペースで集計した滞在人口と発生集中人口を、GitHub Pagesで配信するための静的サイトです。

## 公開対象

- メッシュ形状（250m）
- 2024/2025年、各月、平日/休日、24時間の滞在人口
- 上記から計算した発生集中人口（次の時間帯との差分。23時は0時との差分）

RESASの生レスポンス、Power Query、取得ログ、分析用の文書は含めません。数値の更新は、親ワークスペースで再集計した後に `scripts/export_github_pages.py` を実行して行います。

## ローカル確認

このフォルダをHTTPサーバーで配信してください。`file://` ではJSONの読み込みがブラウザに拒否される場合があります。

```powershell
python -m http.server 8766 --directory public-sites/hitoyoshi-mobility-demo
```

## GitHub Pages

このフォルダの内容を専用の公開リポジトリのルートに置き、ActionsのPagesデプロイを有効にします。`.github/workflows/pages.yml` はそのための最小構成です。

初回だけ、GitHubリポジトリの **Settings → Pages → Build and deployment → Source** で **GitHub Actions** を選択してください。その後、Actionsの Deploy static demo to GitHub Pages を再実行すると、https://dontsu87.github.io/RESASview/ で公開されます。

## 注意

地理院地図・OpenStreetMapのタイルは外部サービスを参照します。各サービスの利用規約、帰属表示、アクセス制限を確認してください。GitHub Pagesは公開サイトであり、アクセス制御や認証はありません。
