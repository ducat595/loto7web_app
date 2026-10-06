# LOTO7 数字研究室 — GitHub Pages版

HTML・JavaScript・JSONのみで動くWebアプリです。PythonサーバーやAPIキー、ビルドは不要です。

## GitHub Pagesで公開
1. GitHubで新しいリポジトリ（例: loto7-web）を作成します。無料アカウントではPublicを選びます。
2. ZIPを解凍し、index.html、app.js、data.json、.nojekyll、README.mdをリポジトリの一番上にアップロードしてコミットします。ZIP自体をアップロードしないでください。
3. リポジトリの Settings → Pages を開きます。
4. Build and deployment の Source を Deploy from a branch に設定します。
5. Branchを main、フォルダーを / (root) にして Save を押します。
6. 公開処理が完了するとPages画面に表示されるURLから利用できます。

※ファイルを1つのフォルダーごとアップロードせず、index.htmlがリポジトリ直下にあることを確認してください。
※Windowsなどで.nojekyllが表示されない場合はGitHubの Add file → Create new file で .nojekyll を作成します。静的ファイル名にはアンダースコアを使用していないため、省略しても通常は動作します。

公式手順:
https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site

## 機能
- 5・10・20口の参考候補生成
- CSV入れ替え（UTF-8 / Shift_JIS対応）
- 完全ランダム10口とのバックテスト比較
- 候補・検証結果・全履歴のCSV保存
- スマホ・PC対応

## データと計算
初期データは添付の第1〜695回（2026/09/18）までです。自動更新はありません。
初期表示の10口は元のPythonプログラムで候補50,000組・シード20260928から生成した結果です。
設定変更やCSV入れ替え後の生成は元の採点式をJavaScriptで実行します。乱数生成器がPythonと異なるため、同じシードでも候補が異なります。
過去検証画面の初期値は添付のPython検証結果495回分です。Webで再実行した結果とは乱数が異なります。
スコアは当せん確率ではありません。ボーナス数字・等級・当せん金・収支は判定しません。

## ファイル
- index.html: 画面とスタイル
- app.js: 採点・生成・検証・CSV処理
- data.json: 初期履歴、Python生成の候補、添付バックテスト結果
- .nojekyll: Jekyllの処理を無効化

外部ライブラリ依存はなく、ファイル参照は相対パスなのでリポジトリ名付きのPages URLに対応しています。
CSV入れ替えはブラウザ内だけで処理し、サーバーに送信しません。再読み込みすると初期データに戻ります。
公開サイトの初期データを差し替えるにはdata.jsonを更新し、初期候補・バックテストも合わせて更新してください。

## PCで確認
ファイルのダブルクリックではdata.jsonの読み込みが制限される場合があります。
Pythonがある場合は解凍先で次を実行し、http://localhost:8000 を開きます。

    python -m http.server 8000

GitHub Pages上ではこの操作は不要です。
