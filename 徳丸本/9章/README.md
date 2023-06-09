# 9章　安全なWebアプリケーションのための開発マネジメント
## 9.1 開発マネジメントにおけるセキュリティ施策の全体像
開発マネジメントは、開発体制と開発プロセスの両面から抑える必要がある。
安全なアプリケーションの開発マネジメントの全体像
- プロジェクト開始以前 (9.2)
- 企画 (9.3.1)
- 発注 (9.3.2)
- 要件定義 (9.3.3)
- 基本設計 (9.3.4)
- 詳細設計 (9.3.5)
- プログラミング (9.3.5)
- テスト (9.3.7)
- 検収 (9.3.8)
- 運用・保守 (9.3.9)

## 9.2 開発体制
### 開発標準の策定
良い開発標準の条件
- 厚すぎないこと（実効性の高い項目に絞る）
- 参照すべきパージがすぐ見つかること
- 実施すべき内容が明確であること
- 継続的に改善していること

セキュリティ項目として記載すべき重要項目
- 脆弱性ごとの対処法
- 認証、セッション管理、ログ出力などの実装方式
- 各フレーズでのレビューとテストの方法（いつ、誰が、何を、どうやって）
- 出荷（公開）判定基準（誰が、いつ、どの基準で許可するか）

### 教育
開発基準を守らせるポイント
- 開発標準自体の工夫（前述）
- チームないの開発標準教育
- 設計レビュー、コードレビューによる遵守状況チェック

教育内容
- 事件事例の紹介（対策モチベーション向上のため）
- 主要な脆弱性の原理と影響
- 遵守すべき事項

セキュリティ担当者の主な業務
- 開発標準の作成、メンテナンス
- 開発標準の教育
- レビューへの参加
- セキュリティテスト
- 脆弱性情報の監視

## 9.3 開発プロセス
### 9.3.1 企画段階の留意点
企画段階では、安全なアプリケーション開発に必要な予算を見積もり、確保することが重要

予算を見積もるために、セキュリティ要件についての概要を検討する

アプリケーションを外注する場合、セキュリティ製品を外部調達する場合、この段階でRFI(Request For Information: 情報提供要求書)を作成する

### 9.3.2 発注時の留意点
アプリケーションの発注にあたって、RFP(Request For Proposal: 提案依頼書)を作成し、提案と見積もりを要求する

セキュリティ要件も記述し、以下のように具体的に要求する
- 対処の必要な脆弱性名を列挙する
- 検収方法・基準を明示する
- 追加で必要な対策があれば提案するように求めるセキュリティテスト方法の提案を求め、テスト結果を成果物として要求する
- 検収後に発見された脆弱性の対応方法と費用負担を明確にする
- 開発体制についての説明を求める
- 開発基準とセキュリティテスト報告書のサンプルを要求する

（
脆弱性に対する責任の所在
システム仕様書に明確に記載していないものに対しては瑕疵（かし）にはならない　←　発注者は自衛のために契約書と仕様書にセキュリティ上の要件を明記する必要がある
）

### 9.3.3 要件定義時の留意点
セキュリティ機能については、発注仕様から要件を定義する

次に、セキュリティバグ対策については、受注者の開発基準をベースにする　← 開発者の再教育が必要となるため

顧客のRFPや発注仕様書に書かれたセキュリティ要件と開発標準を突き合わせてギャップ分析を行い、プロジェクトの開発基準を作成する（図9-2）

要件定義時には以下を中心に検討する
- 認証、アカウント管理、認可の要件（5.1 ~ 5.3節参照）
- ログ管理の要件（5.4節）
- その他のセキュリティ機能についての要件
- 基盤ソフトウェアの選定とパッチ適用の方針決定（８.1.3項参照）
- 開発基準のセキュリティ要件に対するギャップ分析

### 9.3.4 基本設計の進め方
基本設計で実施すべき重要項目は以下の通り
- セキュリティ機能に対する具体化
- 方針設計として開発標準の詳細化、テスト方式の決定
- 画面設計時のセキュリティ機能の確認
  - CSRFの必要な画面の洗い出し
  - HTTPSにするページの洗い出し
  - 認可制御を要するページの洗い出し

### 9.3.5 詳細設計・プログラミング時の留意点
フェーズごとに設計レビュー、コードレビューを実施し、開発標準や開発方針が守られていることを確認する

### 9.3.6 セキュリティテストの重要性と方法
セキュリティテストの方法
- 専門家に依頼する　（専門家の診断は精度が高いが、検査コストが高くなる）
- 専門ツールを用いて診断する　（初期費用の投資が必要）
- 自力で診断する　（無料の診断ツールの活用）

### 9.3.7 受注者側
脆弱性の大半はページ単位でのテストが可能なので、ページ単位で実行できるようになった時点からセキュリティテストを実施することが推奨

早期にセキュリティテストを実施することで手戻りを減らし、開発コストの低減につながる　→ アジャイル型開発プロセスと相性が良い

### 9.3.8 発注者側テスト
発注時に提示した要件は検収としてチェックすべき

セキュリティ要件に対する検収の方法は以下が考えられる
- 受注者のセキュリティ検査報告書を精査する（書類チェック） ← 客観性の観点からおすすめしない
- 第三者（専門家）に検査を依頼する　← コストが高くなる
- 自ら検査する　← 予算に余裕がない場合

### 9.3.9 運用フェーズの留意点
重要な項目
- ログの監視
- 脆弱性対処

定期的に診断する目的
- 前回の診断以降に追加されたページや機能に対する診断
- 新しく発見された攻撃手法への対応チェック

アプリケーションの脆弱性が判明する経路
- 定期的な脆弱性診断で判明する
- ログ分析から判明する
- 外部からの指摘により判明する

いずれの場合も早期に把握　→ 対処することが重要

### 9.3.10 アジャイル型開発プロセスへの適用
スピード感を損なわずにセキュリティを高めるために、
- イテレーションの外で実施できるポリシー策定や教育はあらかじめ済ませておく
- テストなど自動化できる箇所を極力自動化する

#### セキュリティ施策の優先度とスケジュール策定
必要不可欠なものについては、Webサイトのリリースまでには実現しておく必要があるが、追加的なものについては逐次のリリースに向けて、リスクを細かく分析して、セキュリティ施策投入後の優先度を決め、スケジュールを計画すると良い

ただし、全体工数が増えるので、セキュリティ施策についてはリリース当初から最終系で導入するという考え方もある

#### 脆弱性対処
脆弱性対処の工数を減らすためには、フレームワークの選定とテストの自動化が効果的

開発前にやり方を決めておくべき

#### セキュリティ機能（要件）
認証・認可などは必要不可欠なセキュリティ機能なので、リリースまでには実現しておく必要がある

2段階認証などはリリース後に実装することもできる

プロジェクトの早い段階で見通しを立てておくべき

#### プラットフォームのセキュリティ
セキュリティソリューションについては逐次投入が可能で、サービスの利用状況あら判断して導入を決めることもある

#### 脆弱性テスト

アジャイル開発ではリリースの頻度が高くなるため、リリースのたびにアプリケーション全体の脆弱性テストを実施することは現実的ではない

脆弱性テストの自動化の主なアプローチ
- 汎用の脆弱性診断ツールを用いる
- 継続的テストに特化したツール・サービスを用いる
- ソースコード診断ツールを用いる

### 9.4 まとめ
