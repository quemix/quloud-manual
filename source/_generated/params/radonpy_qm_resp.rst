.. これは tools/gen_master_tables.py が生成したファイルです。手で編集しないでください。
.. 生成元コミット: f83096f2a25c5ea29d3d12606c571002ec1aa3b1 (dev_v700_ji)
.. マスタ取得日時（dump 実行）: 2026-09-14T02:30:46Z
.. マスタ同期日時: 2026-09-13T21:30:52Z
.. 再生成: make dump && make generate

~~~~~~~~~~
物理モデル
~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 18 16 8 6 12 16 22 22

   * - 項目名
     - キー
     - 型
     - 単位
     - 既定値
     - 範囲・制約
     - 選択肢
     - 表示条件
   * - SMILES（モノマー繰り返し単位）
     - ``radonpy_smiles``
     - 文字列
     - -
     - -
     - 必須
     - -
     - -
   * - QM手法
     - ``exchange_correlation``
     - 選択
     - -
     - ``wb97m-d3bj``
     - 必須
     - ωB97M-D3BJ（推奨）（``wb97m-d3bj``） / B3LYP-D3BJ（``b3lyp-d3bj``） / HF（高速）（``hf``） / CAM-B3LYP（``cam-b3lyp``）
     - -

