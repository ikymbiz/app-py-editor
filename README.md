

# 📱 Mobile Python & AI Editor

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)](https://www.python.org/)
[![Pyodide](https://img.shields.io/badge/Pyodide-WebAssembly-blue)](https://pyodide.org/)
[![CodeMirror](https://img.shields.io/badge/CodeMirror-5.65-brightgreen)](https://codemirror.net/5/)

**Mobile Python & AI Editor** は、スマートフォンなどのモバイル端末に最適化された、ブラウザだけで完結するPython開発環境です。サーバー構築は一切不要で、WebAssembly (Pyodide) を用いてブラウザ上でPythonコードを直接実行します。さらに、AIAPIと連携してコードの自動生成を強力にサポートします。

## ✨ 主な機能

*   **⚡️ ブラウザでネイティブ実行 (Pyodide)**
    *   サーバー不要。WebAssemblyを通じてブラウザ上で安全かつ高速にPythonコードを実行。
    *   標準出力・標準エラー出力のエディタ内表示。
    *   `micropip` を用いた外部パッケージの自動インストールに対応。
*   **🤖 AIコーディングアシスタント**
    *   Gemini, OpenAI (GPT-4o), Claude, Grokなど、各種生成AI APIに対応。
    *   エディタ内に `# AI: 1から10まで足す関数` と書いてボタンを押すだけでコードを自動生成。
*   **📱 モバイルファーストUI**
    *   ソフトウェアキーボードでの入力負担を減らす**スニペットボタン**（括弧やクォーテーションの自動補完）。
    *   エディタ長押しで起動する**フローティングキーワードメニュー**（`def`, `class`, `import` などの一発入力）。
*   **📁 強力なファイルマネジメント**
    *   IndexedDBによるブラウザ内での仮想ワークスペース保存。
    *   **File System Access API (FSAA)** 対応。端末のローカルフォルダを直接開き、エディタとして使用可能。
    *   ファイルツリー構造、タブ管理、ZIPでの一括エクスポート/インポート。
*   **🛠️ 充実の開発ツール**
    *   CodeMirrorによるシンタックスハイライト（Darculaテーマ）、オートコンプリート。
    *   PEP8準拠のコード自動整形機能（内部で `black` を実行）。
    *   環境変数 (`.env`) および `requirements.txt` の設定パネル。

## 🚀 使い方

### 1. 起動方法
このプロジェクトは単一のHTMLファイルで構成されています。
`index.html`（ファイル名）をブラウザで開くだけで、すぐにエディタが起動します。ネット上にホスティングするだけでPWA（プログレッシブウェブアプリ）としても動作します。

### 2. Pythonコードの実行
1. サイドバー（📁アイコン）を開き、`main.py` にコードを記述します。
2. 画面下部の **「▶ 実行する」** ボタンをタップします。
3. コードがPyodide上で実行され、結果が下部の黒いコンソール領域に出力されます。

### 3. AIにコードを書かせる
AI機能を使用するには、まず設定画面でAPIキーを登録してください。

**方法 A: 入力欄から指示**
上部のプロンプト入力欄に「〇〇をするコードを書いて」と入力し、「✨ AIに頼む」ボタンを押します。

**方法 B: エディタ内にコメントで指示**
エディタ内の任意の行に `# AI: 〇〇をする処理` と記述し、「✨ AIに頼む」ボタンを押すと、その行の下にAIが生成したコードが挿入されます。

### 4. モバイル専用ジェスチャー
*   **スワイプ**: 上部のツールバーやタブは横スクロールに対応しています。
*   **長押し**: エディタ画面を長押し（0.5秒）すると、Pythonの予約語をワンタップで入力できるメニューが表示されます。

## ⚙️ 設定 (Settings)

画面右上の「⚙️」アイコンからシステム設定を開くことができます。すべての設定はブラウザのローカル（IndexedDB）に安全に保存されます。

| タブ | 設定内容 |
| :--- | :--- |
| **AI設定** | 使用するAIモデルの選択、APIキーの入力、システムプロンプトのカスタマイズ。 |
| **pip** | 実行前に自動でインストールしたいPythonパッケージを改行区切りで指定。 |
| **.env** | `KEY=VALUE` 形式で記述すると、Python実行時に `os.environ` にロードされます。 |
| **データ管理** | ローカルフォルダの読み込み(FSAA)、プロジェクトのZIP保存、読み込み。 |

## 💻 技術スタック

*   **フロントエンド**: HTML5, CSS3 (CSS Variables, Flexbox/Grid), Vanilla JavaScript
*   **エディタエンジン**: [CodeMirror 5](https://codemirror.net/5/)
*   **Pythonランタイム**: [Pyodide](https://pyodide.org/) (v0.25.0)
*   **ファイル操作**: [JSZip](https://stuk.github.io/jszip/), File System Access API, IndexedDB
*   **AI連携**: Fetch API を使用した各社 LLM REST API への直接通信

## ⚠️ 注意事項

*   **APIキーの管理**: 入力されたAPIキーはブラウザのローカルデータベース(IndexedDB)にのみ保存され、外部のサーバーには送信されません（設定したAIプロバイダーのAPIエンドポイントへは直接送信されます）。
*   **ローカルフォルダへのアクセス (FSAA)**: File System Access APIは、Safariや一部のモバイルブラウザでは完全にサポートされていない場合があります。その場合は自動的に仮想ファイルシステムにフォールバックします。
*   **初回実行時の通信**: PyodideコアやPythonパッケージ（`micropip`等）は初回実行時にCDNからダウンロードされるため、初期化にはインターネット接続と数秒の時間がかかります。

---
*Created for Mobile Coders & AI Enthusiasts.*