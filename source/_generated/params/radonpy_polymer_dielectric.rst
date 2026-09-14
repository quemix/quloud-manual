.. これは tools/gen_master_tables.py が生成したファイルです。手で編集しないでください。
.. 生成元コミット: f83096f2a25c5ea29d3d12606c571002ec1aa3b1 (dev_v700_ji)
.. マスタ取得日時（dump 実行）: 2026-09-14T02:30:46Z
.. マスタ同期日時: 2026-09-13T21:30:52Z
.. 再生成: make dump && make generate

~~~~~~~~~~~~~~
実験パラメータ
~~~~~~~~~~~~~~

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
   * - 交流電場周波数
     - ``radonpy_dielectric_freq``
     - 数値（指数表記）
     - Hz
     - ``1000000000.0``
     - 1.0 以上、必須
     - -
     - -
   * - 電場振幅
     - ``radonpy_dielectric_amplitude``
     - 数値
     - V/Å
     - ``0.01``
     - 0.0001 以上、必須
     - -
     - -

