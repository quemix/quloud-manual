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
   * - 交換相関汎関数
     - ``exchange_correlation``
     - 選択
     - -
     - ``GGA-PBE``
     - 必須
     - LDA-PW（Perdew-Wang 92）（``LDA-PW``） / LDA-PZ（Perdew-Zunger 81、UPFアップロードのみ）（``LDA-PZ``） / GGA-PBE（``GGA-PBE``） / GGA-PBEsol（UPFアップロードのみ）（``GGA-PBEsol``）
     - -

