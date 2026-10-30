# 1970otochan™clock（1970おとーちゃんクロック）

バイクのスマホホルダー用の時計。2か所で公開中:

- GitHub Pages: https://1970otochan.github.io/otochan-clock/ （main に push すると自動で公開）
- Netlify: https://1970otochan-clock.netlify.app/ （GitHub とはつないでいない。直接アップロードで公開）

Netlify は自動では更新されない。変更したら、公開用の6ファイル（index.html, manifest.webmanifest, sw.js, icon-192.png, icon-512.png, apple-touch-icon.png）を「otochan-clock」フォルダに入れた zip をユーザーに渡し、Netlify のプロジェクト「1970otochan-clock」の Deploys 画面へドラッグしてもらう。

## 変更するときのルール（必ず守る）

ユーザーにバージョン番号を聞かない。変更のたびに自動で上げる。

- 小さな直し（文字の大きさ・色・配置・文言・不具合修正）: 2つ目の数字を1つ上げる（Ver.1.0 → Ver.1.1 → Ver.1.2 …）
- 大きな機能の追加や作り直し: 1つ目の数字を上げ、2つ目を0に戻す（Ver.1.5 → Ver.2.0）
- 迷ったら小さな直しとして扱う

バージョンを上げるときは、次の2か所を同じ番号にそろえる:

1. `index.html` の画面下の表示 `1970おとーちゃんクロック　Ver.X.Y`
2. `sw.js` の `const CACHE="otochan-clock-verX.Y";`（これを変えないと、使っている人のスマホが古い版のままになる）

コミットメッセージは日本語で「Ver.X.Y: 変更内容」とする。変更後は main に push する（GitHub Pages が自動で公開する）。

## 仕様メモ

- 背景は黒、文字はすべて白
- 書体はスマホ内蔵のもの（ネットから読み込まない）
- 秒と日付（西暦・曜日つき）を常に表示
- メニューはタップで表示、3秒で自動で消える
- 1日1回、電波があるときにサーバーの時刻で補正する
- 電波がなくても動く（sw.js で保存）
