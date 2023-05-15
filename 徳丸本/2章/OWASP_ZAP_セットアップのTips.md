- owsap zapインストール時にエラーが発生する問題
  - 状況
    - [https://www.java.com/ja/download](https://www.java.com/ja/download)からWindows Offline (64bit)をダウンロードし、実行．その後、[https://www.zaproxy.org/download/](https://www.zaproxy.org/download/)からWindows (64) Installerをダウンロードし、実行．インストール作業中に、以下のエラーが発生．
  ```
  install4jウィザードは、お使いのシステムでjava(tm)実行環境を見つけられませんでした。適切な64ビットJREを探してください。
  ```
  - 原因
    - 不明
  - 解決策
    - Eclipse Temurinというもの(?)をダウンロード
      - https://adoptopenjdk.net/index.html?variant=openjdk8&jvmVariant=hotspot
    - インストーラを再実行
  - 参考
    - https://zenn.dev/fukutashuntaro/scraps/4d0aa28a81ff35
- owsap zapインストール後，起動時にエラーが発生する問題
  - 状況
    - owsap zapインストール後，アプリのアイコンをクリックして起動．起動が完了する前に以下のエラーが発生．
  ```
  This application requires a Java Runtime Environment 11.0.0
  ```
  - 原因
    - JREのバージョンが古かったことが原因だと思われる（バージョン8がインストールされてた）
  - 解決策
    - [https://www.oracle.com/in/java/technologies/javase/jdk11-archive-downloads.html](https://www.oracle.com/in/java/technologies/javase/jdk11-archive-downloads.html)にアクセス
    - `Windows x64 Installer`をインストール
    - OWASP ZAPを起動
  - 参考
    - https://stackoverflow.com/questions/67968805/problem-starting-owasp-zap-with-openjdk-11-installed
