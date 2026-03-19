

# 📱 Mobile Python AI Editor

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Pyodide](https://img.shields.io/badge/Pyodide-3776AB?style=flat&logo=python&logoColor=white)](https://pyodide.org/)
[![CodeMirror](https://img.shields.io/badge/CodeMirror-D33833?style=flat&logoColor=white)](https://codemirror.net/)

**サーバー構築不要。ブラウザだけで完結する、AIアシスト搭載のモバイル向けPythonエディタ。**

単一のHTMLファイルで動作し、[Pyodide](https://pyodide.org/) を利用してブラウザ上で直接Pythonコードを実行します。モバイル端末でのコーディングに最適化されたUIと、GeminiやChatGPTなどのAIによる強力なコード生成・エラー解析機能を備えています。

## ✨ 主な機能

### 🚀 ブラウザ上でPythonを完全実行
* **Pyodide搭載**: サーバーを介さず、ブラウザのWebAssembly上で安全かつ高速にPythonを実行します。
* **自動パッケージ管理**: コード内の `import` を自動検知し、不足しているパッケージを `micropip` で自動インストールします（設定から事前指定も可能）。

### 🤖 強力なAIアシスタント機能
* **コード自動生成**: 指示を入力してボタンを押すか、エディタ内で `# AI: 1から10まで足す関数` のようにコメントを書いて実行するだけでAIがコードを生成します。
* **AI自動エラー分析**: コード実行時にエラーが発生すると、AIが即座に原因を分析。**修正済みの完全なコードを提示**し、ワンクリックでエディタに反映できます。
* **複数モデル対応**: Gemini (1.5-Pro / 2.5-Flash), OpenAI (GPT-4o), Grok など、お好みのAPIキーを設定して利用可能です。

### 📁 高度なファイル＆ワークスペース管理
* **ローカルフォルダ連携 (FSAA)**: File System Access API対応ブラウザ（Chrome/Edgeなど）なら、端末内のフォルダを直接開いて編集・保存が可能です。
* **仮想ファイルシステム**: ローカルフォルダを開かなくても、ブラウザ内 (IndexedDB) に複数のファイルやフォルダを作成し、タブで切り替えて編集できます。
* **ZIPエクスポート**: プロジェクト全体をいつでもZIP形式でダウンロード・インポート可能です。

### 📱 モバイルに最適化されたエディタ (CodeMirror 5)
* ダークテーマ (Darcula風) の美しいシンタックスハイライト。
* スマホのソフトウェアキーボードで打ちにくい `()` `[]` `{}` `""` `:` `=` や、インデントをワンタップで入力できる補助ツールバー。
* **長押しキーワードメニュー**: エディタ画面を長押しすると、`def`, `class`, `import`, `for` などの頻出キーワードを瞬時に入力できるフローティングメニューが表示されます。

---

## 🛠️ 使い方

### セットアップ
このエディタは**単一のHTMLファイル**で構成されています。
リポジトリをクローンまたはダウンロードし、ブラウザで `index.html` を開くだけですぐに利用を開始できます。

### AIの設定
1. 画面右上の ⚙️ (設定アイコン) をクリックします。
2. 「AI設定」タブから利用したいモデルを選択し、該当するサービスの **APIキー** を入力します。
   * *※ APIキーはブラウザのローカル(IndexedDB)にのみ安全に保存され、外部サーバーには送信されません。*
3. 「設定を保存」をクリックします。

### コードの実行とエラー修正
1. 画面下部の **「▶ 実行する」** ボタンを押すと、コードが評価されコンソールに結果が出力されます。
2. エラーが発生した場合、自動的に「🤖 AI エラー分析」モーダルが立ち上がります。
3. AIが提示した「修正案コード」を確認し、**「✨ 反映」** ボタンを押すだけでコードが自動修正されます。

### 外部モジュール・環境変数の利用
* **pip パッケージ**: 設定画面の「pip」タブに、利用したいパッケージ名を改行区切りで入力しておくと、実行前に自動インストールされます。
* **環境変数 (`.env`)**: 設定画面の「.env」タブに `KEY=VALUE` の形式で入力すると、Pythonスクリプト実行時に `os.environ` に自動で読み込まれます。

---

## 💻 技術スタック

* **フロントエンド**: HTML5, CSS3, Vanilla JavaScript
* **エディタエンジン**: CodeMirror 5
* **Python実行環境**: Pyodide (WebAssembly)
* **ストレージ**: IndexedDB (設定・履歴・仮想ファイル保存)
* **ファイルシステム連携**: File System Access API
* **ZIP処理**: JSZip

---

## 🔒 セキュリティとプライバシー

* 本アプリは**バックエンドサーバーを持たない完全なクライアントサイドアプリケーション**です。
* 入力したコード、ファイルデータ、APIキーなどはすべてお使いのデバイスのブラウザ内（IndexedDB等）に保存されます。
* AI機能を利用する際のみ、指定したAIプロバイダー（GoogleやOpenAIなど）の公式APIエンドポイントへ直接データが送信されます。

---

## 📄 ライセンス

このプロジェクトは [MIT License](LICENSE) のもとで公開されています。自由に改変してご利用ください。