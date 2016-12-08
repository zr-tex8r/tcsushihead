tcsushihead パッケージ
======================

LaTeX：ページヘッダにスシを流す

意味が分からない場合は、とにかく試してみよう！

### 前提環境

  * フォーマット： LaTeX
  * エンジン： pdfTeX、XeTeX、LuaTeX、およびDVI出力のエンジン全て
  * DVIウェア（DVI出力の場合）： dvipdfmx
  * 依存パッケージ：
      - animate
      - bxcoloremoji

※[bxcoloremoji パッケージ]が必要なのは、その中にあるスシの画像ファイル
（emoji_images/twemoji-pdf/1F363.pdf）を利用するからである。

[bxcoloremoji パッケージ]: https://github.com/zr-tex8r/BXcoloremoji

### インストール

  - `*.sty` → $TEXMF/tex/latex/tcsushihead

### ライセンス

MIT ライセンスが適用される。

### パッケージ読込

    \usepackage[<オプション>,...]{tcsushihead}

以下のオプションが使用できる。

  * `dvipdfmx`：dvipdfmx を使う場合に指定する。
  * `default=true|false`： ページスタイルを既定で `sushihead` に変更
    するか。既定値は `true` である。`default=false` が指定された時は
    ページスタイルは変更されない。この場合でも、`\pagestyle{sushihead}`
    を実行すればページスタイルを変更できる。
  * `\sushiheadsetup` 命令において有効な key-value 指定は全てパッケージ
    オプションでも指定できる。

### 使用法

パッケージを（`default=false` を付けずに）読み込むと既定のページスタイル
が `sushihead` に設定される。このスタイルでは、フッタは空になり、ヘッダ
に流れるスシのアニメーションが配置される。具体的には、一定個数のスシの
並びを一定の間隔をおいて無限に繰り返したものを、左方向に動かす。既定で
は、スシの並びの個数は現在のページ番号と一致する。

注意： PDF 文書におけるアニメーションの表示をサポートする PDF ビューア
（Adobe Reader 等）は非常に少ない。

さらに、以下のユーザ命令が利用できる。

  * `\sushiheadsetup{KEY=VALUE,...}`：スシのアニメーションを調整する。
      - `count=<整数>`： 並んだスシの個数。有効値の範囲は 0～100 で、
        0 は現在ページ番号に一致させることを指定する。何れにしても、
        個数は 100 が上限となる。
      - `size=<長さ>`： スシ画像の（縦横の）サイズ。
      - `gap=<長さ>`： スシの並びの間の間隔。
      - `cycle=<実数>`： アニメーションの周期（秒単位）。0.1 以上で
        なければならない。
      - `ticks=<整数>`： アニメーション周期中のフレーム数。フレーム
        レート（`cycle` と `ticks` から導出される）は秒間 100 コマが
        上限である。（Adobe Reader の性能限界はもっと低いはず。）
      - `file=<パス>`： 使用する画像ファイルのパス。これを指定すると
        他のものを流すことができる。
      - `bb=<bbox値>`： `file` に指定した画像のバウンディングボックス
        （`\includegraphics` 命令の `bb` オプションの値）。この値は
        `dvipdfmx` ドライバ使用時にのみ参照される。extractbb の自動起動
        が利用可能な場合は不要である。

  * `\ShowSushiBar{<長さ>}`： （ヘッダではなく）その場に指定の長さの
    スシのアニメーションを出力する。

更新履歴
--------

  * Version 0.2  ‹2016/12/03›
      - 最初の公開版。

--------------------
Takayuki YATO (aka. "ZR")  
Twitter: @zr_tex8r
