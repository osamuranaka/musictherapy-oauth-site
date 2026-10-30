# Music Therapy OAuth Branding Website

Google OAuth のブランディング用の公開静的サイトです。一般向けYouTubeチャンネルWebサイトではありません。認証情報、YouTube Analytics値、Google Sheetsのリンクやレポートは一切公開しません。

- 公開予定ホームページ: https://musictherapy-api.ants-biz.jp/
- プライバシーポリシー: https://musictherapy-api.ants-biz.jp/privacy/
- 利用規約: https://musictherapy-api.ants-biz.jp/terms/
- お問い合わせ: https://me-l.co/oqsfivy6 （稼働確認が必要）

## 導入
1. GitHubの `osamuranaka` で新しい **Public** リポジトリ `musictherapy-oauth-site` を作る（`youtube-analytics` はPrivateのまま）。README初期化ありでOK。
2. `index.html`、`privacy/index.html`、`terms/index.html`、`style.css`、`.nojekyll`、`CNAME` をリポジトリ直下に登録。
3. Settings > Pages > Build and deployment > Deploy from a branch > main / (root) > Save。
4. Settings > Pages > Custom domain に `musictherapy-api.ants-biz.jp` を設定。DNSより先にGitHub Pages側を設定。
5. DNS管理画面で `musictherapy-api` に CNAME `osamuranaka.github.io` を登録。`ants-biz.jp` の既存A/AAAA/MXや `www` は変更しない。
6. GitHub Pagesの `Enforce HTTPS` を有効化し、上記3 URLがHTTPSでアクセス可能か検証。
7. Google Search Consoleで `ants-biz.jp` のドメイン所有権を確認（既に確認済みなら不要）。Google Cloud > Auth Platform > Branding でアプリ名・サポートメール・ホーム・プライバシーURL、Authorized domains に `ants-biz.jp` を設定。
8. 本番環境の公開を行う。必要なブランド/スコープ検証については画面の指示に従う。
9. 本番切替後、運営者のWindowsPCでMusic Therapy専用OAuth認証をやり直し、新しいtoken JSONをGitHub Secretsの `MUSICTHERAPY_YOUTUBE_TOKEN_JSON` に更新する。古いトークンが長期有効になるわけではない。

## 注意点
- Google OAuthを「本番環境」に移しても、センシティブスコープ等の検証が不要になるとは限りません。
- Google/YouTubeポリシーのデータ削除要件に従うよう、運用者はトークン失効/権限取消時の保存データ削除手続きを用意する必要があります。現在の週次取得コードが自動削除に対応していると宣言しないこと。
- 公開前にお問い合わせリンクが動作することを確認してください。
- サイトの内容は実装状態やデータ保管先に変更があれば必ず更新してください。
- リポジトリは静的HTML/CSSだけのPublicとして、トークンJSONやclient_secrets.jsonを決して追加しないでください。

## 参照
- https://developers.google.com/identity/protocols/oauth2/policies
- https://developers.google.com/identity/protocols/oauth2/production-readiness/brand-verification
- https://developers.google.com/youtube/terms/developer-policies
- https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site
