# 1. notebook実行前に以下を行ってください

ご自身の環境にPython3.11以上をインストールしてください。
以下をコマンドプロンプト（またはPowerShell）で実行してください。
`pip install uv`でuvをインストールしておいてください

1. `cd <このカレントディレクトリ>` を実行し、`TopologicalDataAnalysis/`まで移動
2. `uv venv .venv --python 3.12` を実行(仮想環境を作成)
3. `.venv\Scripts\activate` を実行(仮想環境を有効化)
4. `uv pip install -r pyproject.toml` を実行
5. `uv pip install --upgrade --force-reinstall ipykernel`

開発者向け。上の操作の前に以下を行う。
1. pyproject.toml を編集
2. `uv lock` で pyproject.toml から uv.lock を作成

notebook使用時は、ご自身のグローバル環境を汚さないためにこのvenv環境を用いてください。

# 2. 1の操作の解説

- TopologicalDataAnalysisフォルダ内に独立したPython実行環境（仮想環境）を作成しています。実行後、TopologicalDataAnalysis/venvの中に TopologicalDataAnalysis/.venv/Scripts/python.exe などが生成されます。
- 仮想環境を有効化しないまま `pip install ...` するとグローバル環境にインストールされてしまうので注意してください。
- Jupyter Notebookを起動する際も、仮想環境を有効化した状態で `jupyter notebook` を実行すると安心です。

# 参考文献
- PythonのライブラリGudhi`https://gudhi.inria.fr/index.html`
- PYthonのライブラリBiopython: `https://biopython.org/`
- 池 祐一, E.G. ESCOLAR, 大林 一平, 鍛冶 静雄, 位相的データ解析から構造発見へ, サイエンス社, 2023
- N. Scoville, 中川 征樹(訳), 離散モース理論, 丸善出版, 2024
- WebサイトAlgebraic Topology: `http://pantodon.jp/index.rb?body=index`
  - Vietoris-Rips複体: `http://pantodon.jp/index.rb?body=Rips_complex`
- 斎藤 成也, ゲノム進化を考える, サイエンス社, 2007
  - 正誤表: `http://www.saitou-naruya-laboratory.org/My_books/Saiensusha_0007.html`
- 平岡 裕章, タンパク質構造とトポロジー, 共立出版, 2013