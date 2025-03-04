# `.cursorrules` チートシート

## 基本的な記述方法とフォーマット
- **ファイル設置**: プロジェクトのルートディレクトリに **`.cursorrules`** という名前のファイルを作成します。このファイルにプロジェクト専用のルール（AIへの指示）を記述します。  
- **内容の構成**: テキスト形式で、AIに守らせたい指示を書きます。Markdownの見出しや番号付きリストなどを使って整理できます（CursorではMarkdown形式の記述もサポートされています）。例えば見出しや箇条書きを用いて**「一般ガイドライン」**や**「コードスタイル」**といったセクションに分けると見やすくなります。  
- **記述例**: 以下は `.cursorrules` のシンプルな例です（プロジェクトがPythonとReactを使う場合）：  

  ```md
  あなたは本プロジェクト専属のAIアシスタントです。以下のルールに従って回答してください。

  ## コード全般のガイドライン
  1. 可能な限り最新の言語機能を使用する（例: Pythonでは`async/await`を活用）。
  2. セキュリティとエラー処理を徹底する（例: 入力値は常に検証し、例外処理を行う）。

  ## フロントエンド（React）
  - コンポーネントは関数コンポーネント（Functional Component）を使用し、フックを活用する。
  - JSX内でインラインスタイルではなくCSSモジュールまたはTailwind CSSを使用する。

  ## バックエンド（データベース）
  - データベースにアクセスする際は必ず既存のDBユーティリティ関数を使い、生のSQLクエリは直書きしない。
  ```  

  このように、プロジェクトの文脈やコーディング規約を箇条書きやセクションにまとめて記述します。必要に応じてコードブロックを含め、望ましいコード構造の例を示すことも可能です（例: 特定のパターンのテンプレートコードを提示する）。  
- **コメントの使用**: `.cursorrules` 内では `//` を先頭につけてコメントを書くことができます。コメントはAIへの指示としては無視されますが、ファイル内で人間がルールの目的や背景を説明するのに役立ちます。例えば、`// このセクションではReactコンポーネントの規約を定義` のように書いておくと、将来ルールを編集する際の手がかりになります。

## 推奨されるベストプラクティス
- **プロジェクト固有の内容に集中**: ルール内容はそのプロジェクトに特有のガイドラインや注意点に絞りましょう。一般的すぎるプログラミング知識（コーディングの基礎など）はモデル自身が持っているため、重複して指示する必要はありません。代わりに「このプロジェクトではXを採用」「Yというライブラリを使う」など**プロジェクト独自の情報**を盛り込みます。  
- **簡潔かつ明確な言葉遣い**: AIが理解しやすいように、曖昧な表現は避けて簡潔で明確な指示を書きます。専門用語を多用しすぎず、一文を短くまとめましょう（「一度に一つのこと」を伝えるイメージ）。  
- **コーディング規約やスタイルの明示**: プロジェクトのコーディングスタイル（インデント、命名規則、アーキテクチャなど）やベストプラクティスをルール化して記載します。これにより、AIが常にプロジェクトのスタイルガイドに沿ったコードを提案し、一貫性が保てます。例えば「すべての関数にはDocstringを付与する」「変数名はスネークケースを使う」といった規約をリスト化します。  
- **プロジェクトの文脈情報を提供**: そのプロジェクトで頻繁に使われるライブラリ名や主要機能、アーキテクチャ上の決定事項などを記載して、AIに事前知識を与えます。これによりAIは提案時にプロジェクトのコンテキストを考慮し、より適切なコード補完が可能になります。  
- **コメントで補足説明**: 上述のように `//` コメントを活用し、特に複雑なルールや重要な意図には人間向けの注釈を残しましょう。将来的にルールを見直す際や、チームメンバーが内容を理解する際に役立ちます。  
- **定期的な見直しとアップデート**: プロジェクトの進行に伴いルールも更新します。新たな技術を導入した場合はその指示を追加し、不要になった規則は削除します。ルールを最新版に保つことで、AIの提案も最新のプロジェクト状況に適合します。  
- **バージョン管理への追加**: `.cursorrules` ファイル自体をGitなどでバージョン管理することを推奨します。チーム開発の場合、リポジトリにこのファイルを含めて共有することで、全員が同じAIルールの恩恵を受けられます（コードスタイルの統一や知識の共有に繋がります）。  

## よくあるミスとその回避策
- **ルールの一般化しすぎ**: あまりに包括的で汎用的すぎる指示（例：「バグのないコードを書く」程度の漠然とした要求）のみを書いても効果は薄いです。具体性に欠けるルールはモデルが無視しやすいため、具体的で実行可能な内容に落とし込みましょう（「例外処理を必ず書く」「入力値は全てバリデーションする」など具体的な形で記載）。  
- **矛盾した指示**: `.cursorrules` 内で前後で矛盾するルールを記載すると、モデルが混乱し望ましくない出力になる可能性があります。同様に、グローバルなUser Rules（後述）と内容が食い違う場合も**結果が不定**になります。例えばグローバル設定で「常に英語で回答」としているのに `.cursorrules` に「日本語でドキュメントを書くコード例を出す」と書くと、出力言語が安定しない恐れがあります。回避策として、ルール間で一貫性を保ち、重複する指示はどちらか一方にまとめるようにしてください。  
- **過剰に長いプロンプト**: `.cursorrules` に大量の段落や項目を詰め込みすぎると、AIコンテキストの一部を圧迫し、本来の質問内容に割ける注意力が下がる場合があります。重要な点を厳選し、簡潔にまとめることが肝心です（必要なら箇条書きにして読み飛ばされにくくする）。「すべてを書きたい」衝動は抑え、**ルールはプロジェクト運用上特に重要な部分に絞る**よう心がけましょう。  
- **配置場所・ファイル名のミス**: `.cursorrules` ファイル名のスペルミスや、ルートディレクトリではない場所に置いてしまうケースも散見されます。この場合Cursorがルールを認識しません。正しい名前「`.cursorrules`」（ドットから始まりsが複数形であることに注意）でプロジェクト直下に設置してください。  
- **プロジェクト無関係なルール**: 特定プロジェクトには無関係な指示（他プロジェクトの名残やテンプレートのままの内容）を残してしまうと、AIの動作に悪影響を及ぼします。例えばPythonのプロジェクトなのに「TypeScriptを使え」というルールが残っている等は典型的ミスです。新しいプロジェクトを始める際は前の `.cursorrules` を流用せず、そのプロジェクト用に見直しましょう。  
- **グローバルルールとの混同**: `.cursorrules` はあくまで「リポジトリ固有のルール」であり、Cursorの設定画面で指定するグローバルなUser Rulesとは用途を分ける必要があります。プロジェクト個別の規則（使用ライブラリやコード規約）は `.cursorrules` へ、どのプロジェクトにも共通する嗜好（回答言語や口調など）はUser Rulesへ、と役割分担すると管理しやすくなります。逆にそれを混同すると、例えばグローバルには不要な細かいプロジェクト事情を常に読み込ませることになり非効率です。  

## 便利なテクニック（高度な設定やカスタマイズ例）
- **コード例の提示**: ルール内で「望ましいコード」の例をコードブロックとして示すことで、AIに具体的なお手本を示すことができます。例えばSwiftUIプロジェクトであれば、新規Viewのひな型コードを `.cursorrules` に含めておくと、AIはコード生成時にその構造を参考にします。このように具体例を示すことで、抽象的な指示よりも強力にAIの出力を誘導できます。  
- **セクション分けで文脈を明示**: `.cursorrules` 内をセクション（見出し）で区切り、「どのような場面で適用すべきルールか」を明示できます。例えば「## フロントエンド関連」「## データベース関連」などの見出しを作り、それぞれの下に該当場面向けのガイドラインを書くと、AIは自身が今関与している箇所に関連する指示を見つけやすくなります。これは新しいProject Rules機能（複数ファイルによるルール管理）の簡易版と言え、厳密なファイルパターン適用はできないものの、**ルールを論理的にグループ化**しておくことでAIの理解を助けます。  
- **既知のバグや禁止事項を列挙**: プロジェクト内で「やってはいけないこと」や「既知の問題への対処法」を予め書いておくことで、AIにミスを犯させにくくできます。例えば「バージョン1.2.3のライブラリXにはバグがあるので関数Yは使用しないこと」や「SQLインジェクションを防ぐために直接SQLを書かず必ずZ関数を使う」等です。**プロジェクトの地雷を事前共有**するイメージで、AIがその知識を持った上でコードを書いてくれるため安心します。  
- **アウトプットの形式指定**: 回答のフォーマットについて細かな好みがある場合も `.cursorrules` で指定できます。例えば「すべてのコードブロックには言語名を指定する（```python など）」「出力の最後に参考文献セクションを含める」等です。これらはプロジェクトのドキュメント生成やコーディング規約に関わる場合に有効です。ただし、あまり細かく指示しすぎるとAIが柔軟性を欠く恐れもあるため、テンプレート化したい部分に絞ると良いでしょう。  
- **新しいProject Rulesへの移行**: Cursor v0.45以降では `.cursor/rules/` ディレクトリに複数ファイルのルールを置ける**プロジェクトルール機能**が導入されています。高度な条件付け（特定のパスやファイルタイプへの適用等）が可能で、今後 `.cursorrules` は非推奨になる予定です。現在 `.cursorrules` を使っている場合でも、将来的には新方式への移行を検討しましょう。例えば大規模プロジェクトでは、言語ごと・モジュールごとにルールファイルを分割することで管理しやすくなります。現行バージョンでも、`.cursorrules` に書いた内容は新ルールシステムに**自動的に追加**されて動作します（裏でグローバルルールと結合されます）。移行期間中は `.cursorrules` を使いつつ、徐々に新機能に慣れていくと良いでしょう。

## 具体的なユースケース（活用シーン）
- **フレームワークやライブラリごとのコード指針**: プロジェクトが特定のフレームワークを使う場合、そのベストプラクティスをルール化できます。例として「React + TypeScriptプロジェクト」であれば「関数コンポーネントのみを使用」「Propsの型定義を厳格に行う」といった指示が考えられます。実際、Cursorのルール機能は「特定ファイル拡張子に対するフレームワーク固有の指示（例：`.tsx`ファイルではSolidJSの流儀に従う等）を適用できる」よう設計されています。このように技術スタックに合わせたルールで、AI提案をプロジェクトに適したものに調整できます。  
- **コードアーキテクチャの維持**: プロジェクト固有のフォルダ構成やアーキテクチャパターンがある場合、その遵守をAIに促せます。例えば「コンポーネントは `src/components` ディレクトリ下に作成する」「サービスクラスとコントローラを分離する」といったルールです。実例として、Cursorのルールで*「決められたフォルダ構成に沿ってファイルを生成するよう指示する」*ことも可能です。これによりAIが提案する新規ファイルの配置先や構成もプロジェクト標準に揃えられます。  
- **セキュリティ・品質の強制**: 開発におけるセキュリティ標準や品質基準をルール化することで、自動的にベストプラクティスを適用できます。例えば「データベースアクセスは必ずORM経由にする」「全ての公開APIには入力検証を入れる」「未実装の関数には必ずTODOコメントを付記する」等です。AIがコード生成時にこれらを考慮するため、レビュー時の指摘事項が減り安全性が高まります。  
- **モダンなコードへのアップデート**: レガシーな記法を避け最新の言語機能を使うことをルールで指示し、コードベースのモダナイズを図れます。例えば「コールバックではなく常にasync/awaitを使う」「古いAPI `X`ではなく新しいAPI `Y`を使う」といった具合です。実際にiOS開発の例では、Cursorに**「常に `NavigationView` ではなく `NavigationStack` を使う」**など最新APIを優先させるルールを組み込むことで、古い習慣に基づくコード提案を避けたケースがあります。このようにルールを活用すれば、自動的にコードのアップデートを促進できます。  
- **チーム開発でのスタイル統一**: 複数人で開発するプロジェクトでは、`.cursorrules` を共有することでチーム全体でAIの出力スタイルを統一できます。各開発者がバラバラの設定を持つのではなく、リポジトリ内の `.cursorrules` を共通の「開発ルール」として扱うことで、誰がAI補助を使っても一貫したコードスタイル・構成になります。結果としてコードレビューが容易になり、チームのコーディング規約遵守率も高まります。  
- **ドメイン固有知識の共有**: プロジェクトの分野に特有な知識（業務ルールや専門用語、使用するアルゴリズムの前提など）がある場合、それを `.cursorrules` に記載しておくと有用です。AIが回答やコード生成時にその知識を踏まえた上で提案するため、より実践的で役立つ回答が得られます。例えば金融システムのプロジェクトなら「小数計算は常に高精度クラスを使う」「約定のルールAに従う必要がある」などを書いておくことで、AIはそうしたドメイン制約を破らない回答をしてくれるでしょう。