# ログインボタンからGithubログインをしようとすると404エラー

**作成日**: 2025/09/13
**最終更新**: 2025/09/14

## 問題
- ユーザーから以下連絡あり
	- Android上でログインを試すとエラーが発生。
	- エラーメッセージ
		- `Not found. Authentication passthru.`
		- ![image.png](https://raw.githubusercontent.com/kei2kei/learning-posts/main/wakannyai_posts/7/images/20250917225050_image.png)

## 試したこと
- 現時点での予想
	- 開発中にもしばらく同様のエラーに遭遇したことがあった。
	- 原因としては、恐らくcsrf-token関連だと思われる。
	- 自身の経験を参考にレスポンシブヘッダのturbo周りを確認する。
	- [自身のGithubのcsrf対策](https://github.com/kei2kei/til/blob/main/202509/20250906.md)

## 解決方法
レスポンシブヘッダーのURLがGithub認証のログインに直接飛んでいたので、CSRFトークンの影響を受け、404エラーになっていた模様。
ログイン画面に接続させることで解消


## まとめ
- 真因
	- レスポンシブ対応で変更されるデザインでのテスト不足
- 暫定対応
	- レスポンシブヘッダーのURL遷移先改修
- 恒久対応
	- CIテストにスマートフォンでのテスト追加
