.. _property-section:

==============================
Property の登録
==============================

:ref:`jobdetail-section`\ にある Select Property より、初期構造（initial）の他に、\
その Material に対して実行されたジョブのうち、Status = Succeeded で終了したものも選べるようになります。\
Quloud では、これを（その Material の）Property と呼びます。 

.. image:: images/screenshot_0229.png

左サイドメニューの Job をクリックすると、下図のような、\
その Material に関して作成・実行されたジョブの一覧が表示できます\
（もし直接一覧画面が表示されない場合は、画面上部に出る「一覧に戻る」をクリックしてください）。

.. image:: images/screenshot_0230.png

Succeeded で終了したジョブはデフォルトで、Property として登録されてしまうようになっています。\
もし Property として登録したくない（Select Property の選択肢に出さないようにしたい）場合は、\
ジョブ一覧の View 列のアイコンをクリックして下図のようにしてください。

.. image:: images/screenshot_0231.png

そうすると、Property 画面（\ :ref:`jobdetail-section`\ のトップ）の Select Property
の選択肢から除外されるようになります（Succeeded 以外のジョブは、アイコンを切り替えても何も起こりません）。

.. image:: images/screenshot_0232.png
