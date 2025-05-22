# 1. notebook実行前に以下を行ってください

ご自身の環境にPython3.12以上をインストールしてください。
以下をコマンドプロンプト（またはPowerShell）で実行してください。

1. `cd <このカレントディレクトリ>` を実行し、`TopologicalDataAnalysis/`まで移動
2. `python -m venv venv` を実行
3. `./venv/Scripts/activate` を実行
4. `pip install -r .binder/requirements.txt` を実行

notebook使用時は、ご自身のグローバル環境を汚さないためにこのvenv環境を用いてください。

# 2. 1の操作の解説

2. TopologicalDataAnalysisフォルダ内に独立したPython実行環境（仮想環境）を作成しています。実行後、TopologicalDataAnalysis/venvの中に TopologicalDataAnalysis/venv/Scripts/python.exe などが生成されます。
3. 以降の pip install や python コマンドは「venv」フォルダ内のPython環境で動作します。
4. TopologicalDataAnalysis/.binder/requirements.txt に書いてあるライブラリを仮想環境にインストールします。

- `python -m venv venv` で使われるPythonのバージョンは、コマンド実行時に呼び出されるPythonです。複数バージョンがある場合は `py -3.12 -m venv venv` のようにバージョン指定も可能です。ただし、ご自身の環境に指定したバージョンのpythonが存在している必要があるため事前にダウンロードしてください。
- 仮想環境を有効化しないまま `pip install ...` するとグローバル環境にインストールされてしまうので注意してください。
- Jupyter Notebookを起動する際も、仮想環境を有効化した状態で `jupyter notebook` を実行すると安心です。

# 参考文献
- `https://gudhi.inria.fr/index.html`
  - simplexについて: `https://gudhi.inria.fr/python/latest/simplex_tree_ref.html`
- 池 祐一, E.G. ESCOLAR, 大林 一平, 鍛冶 静雄, 位相的データ解析から構造発見へ, サイエンス社, 2023
- N. Scoville, 中川 征樹(訳), 離散モース理論, 丸善出版, 2024