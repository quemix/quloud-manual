========================================
仕様（変更履歴、注意事項）
========================================

|
|

----------------------------------------
仕様変更履歴
----------------------------------------

|
|

**Ver.6.1.2（2026.4.20）**

|

-   招待画面

    -   一度追加した新規ユーザーのメールアドレスを「Deny」ボタンで却下する機能を、Tenant 内のすべての Owner 権限ユーザーが使用できるよう変更

    |

-   画面の自動更新

    -   画面の自動更新を停止

    |

-   Project、Material、Job の名前の重複制限

    -   Project、Material、Job の作成時、名前の重複制限によるエラーが発生した場合でも、作成ダイアログ自体が消えないように修正
    -   作成した Job を、Job 詳細ページの「Copy Job」ボタンでコピーする際にも、Job 名の重複禁止の制御が有効となるよう修正
    -   Job 詳細ページの「Delete Job」ボタンから削除した Job については、名前の重複制限の対象外とし、同一 Material 内で削除した Job と同じ名前の Job が作成できるよう修正

    |

-   Material 作成ダイアログ、Job 作成 / 編集ダイアログでの loading 表示

    -   「Create」もしくは「Save」ボタンをクリックしてから実際に作成 / 編集が完了するまでの間、loading 表示が出て、ユーザーが他の操作を行えないように変更

    |

-   Material 詳細画面

    -   ブラウザリロード時の画面遷移を下記のように変更

        - Property ページでリロード → Property ページに遷移
        - File ページでリロード → File ページに遷移
        - Job 一覧ページでリロード → Job 一覧ページに遷移
        - Job 詳細ページでリロード → Job 詳細ページに遷移

        |

-   Material / Job のファイル編集

    -   Job が存在する Material では、File ページでファイルが編集できないよう変更
    -   ファイル編集時に全角文字を入力し「Save」ボタンで保存すると、その後「Edit」ボタンをクリックしても中身が表示されなくなる問題を解消

    |

-   モデリング画面

    -   Surface 項目にある「Reorient lattice」チェックボックスを削除

    |

-   入力ファイル直接アップロードによる Job 実行

    -   RSDFT の Job 詳細ページの「Site property settings」表示欄を削除
    -   LAMMPS の入力ファイルでの設定内容が Job 詳細ページに反映されるよう修正

    |

-   「Run Job」ボタンからの Job 実行

    -   一度「Run Job」ボタンから Job を実行した直後に、再度「Run Job」ボタンから Job を実行できてしまう問題を解消
    -   一度「Run Job」ボタンから Job を実行した直後に、「Delete Job」ボタンがクリックできてしまう問題を解消

    |

-   Site property settings

    -   Quantum ESPRESSO・OpenMX・RSDFT・FLARE の Edit Job ダイアログに Site property settings 項目を追加
    -   Quantum ESPRESSO・OpenMX・RSDFT・FLARE で、Site property settings 項目の Charge 設定欄を削除
    
    |

-   Quantum ESPRESSO

    -   Electron Band Structure で、計算結果の Effective Mass (Table) の表が、Job 作成者のみしか閲覧できない問題を解消
    -   X-Spectra の一部の入力パラメータの表示桁数を変更
    -   X-Spectra の一部の入力パラメータを指数表記に変更
    -   X-Spectra の Job 作成時、吸収原子用の GIPAW 擬ポテンシャルファイルがない場合にエラーメッセージが表示されるよう修正
    -   X-Spectra の Job 作成時、吸収サイト以外にも吸収原子用の GIPAW 擬ポテンシャルファイルが設定されてしまう問題を解消
    -   X-Spectra の Job 作成時、入力ファイル「xspectra.in」の末尾に、吸収サイトに関する情報「QULOUD_ABS_SITE_INDEX」が追加されるよう修正
    -   下記の Job で、Create Job ダイアログや Edit Job ダイアログで 設定・編集した通りの情報が、Job 詳細ページの「Settings」項目、および Edit Job ダイアログに正しく表示されない場合がある問題を解消

        -   Energy Barrier (NEB)
        -   X-Spectra
        -   Phonon (ph.x)

        |
    
    -   Energy Barrier (NEB) の計算結果の Atomic Structure Trajectory で、モデル図がマウスで回転できるように修正
    -   Energy Barrier (NEB) で、Create Job ダイアログで終期構造を選択してからすぐに「Create」ボタンをクリックすると、選択した終期構造が入力ファイルに正しく設定されない問題を解消
    -   Energy Barrier (NEB) で、Edit Job ダイアログで終期構造の情報を変更して保存しても、その変更が入力ファイルに反映されない問題を解消
    -   Energy Barrier (NEB) の入力ファイル「neb.in」が、File ページの「Edit」アイコンから編集できない問題を解消
    -   Phonon (ph.x) の Job 作成後、Edit Job ダイアログで Calculation（Phonon Band Dispersion / Phonon DOS）を変更して「Save」ボタンで保存すると、どちらの Calculation の入力ファイルも生成されてしまう問題を解消
    -   Phonon (ph.x) の ph.in 項目の入力パラメータ「epsil」を削除

    |

-   OpenMX

    -   Electron Band Structure で、計算結果の Effective Mass (Table) の表が、Job 作成者のみしか閲覧できない問題を解消
    -   Energy Barrier (NEB) で、Create Job ダイアログで終期構造を選択してからすぐに「Create」ボタンをクリックすると、選択した終期構造が入力ファイルに正しく設定されない問題を解消
    -   Energy Barrier (NEB) で、Create Job ダイアログや Edit Job ダイアログで 設定・編集した終期構造の情報が、Edit Job ダイアログに正しく表示されない問題を解消
    -   Energy Barrier (NEB) で、Edit Job ダイアログを開いて「Save」ボタンで保存すると、終期構造の情報が、強制的に初期構造と同じものに置き換わってしまう問題を解消
    -   下記の Job の計算結果の Atomic Structure Trajectory で、モデル図がマウスで回転できるように修正

        -   Energy Barrier (NEB)
        -   Molecular Dynamics

        |

-   RSDFT

    -   Electron Band Structure の Job 作成時、入力ファイル「rsdft.in」の KPTDIVNUM の行の末尾にスラッシュが追加されるよう修正
    -   Molecular Dynamics の計算結果の Atomic Structure Trajectory で、モデル図がマウスで回転できるように修正
    -   Site property settings 項目での初期スピンの設定が無視されてしまう問題を解消

    |

-   LAMMPS

    -   Molecular Dynamics の計算結果のグラフの縦軸・横軸に単位を追加
    -   Molecular Dynamics で、Create Job ダイアログで 設定した通りの情報が、Job 詳細ページの「Settings」項目に表示されない場合がある問題を解消
    -   Molecular Dynamics で、msd を計算する元素や rdf を計算する元素ペアを限定して Job を作成しても、Edit Job ダイアログではすべての元素や元素ペアにチェックがついてしまう問題を解消
    -   Molecular Dynamics の計算結果の Atomic Structure Trajectory で、モデル図がマウスで回転できるように修正
    -   Molecular Dynamics の計算結果の Atomic Structure Trajectory で、モデル図が強制的に直方体になってしまう問題を解消
    -   Molecular Dynamics の計算結果の Atomic Structure Trajectory で、格子ベクトル a2 と a3 が逆に表示されてしまう問題を解消
    -   Molecular Dynamics の計算結果の Atomic Structure Trajectory で、元素と原子球のカラー / サイズの対応が違ってしまう場合がある問題を解消

    |

-   ASE

    -   Energy Barrier (NEB) で、Create Job ダイアログで終期構造を選択してからすぐに「Create」ボタンをクリックすると、選択した終期構造が入力ファイルに正しく設定されない問題を解消
    -   Energy Barrier (NEB) で、一度作成した Job を、Job 詳細ページの「Edit Job」ボタンから編集する機能が無効となっていた問題を解消
    -   下記の Job の計算結果の Atomic Structure Trajectory で、モデル図がマウスで回転できるように修正

        -   Energy Barrier (NEB)
        -   Molecular Dynamics

        |

-   FLARE

    -   On-the-Fly MD の計算結果の Atomic Structure Trajectory で、モデル図がマウスで回転できるように修正

|
|

**Ver.6.1.1（2026.3.30）**

|

-   入力ファイル直接アップロードによる Job 実行

    -   FLARE の入力ファイルがアップロード不可となっていた問題を修正
    -   Quantum ESPRESSO (PW) で、入力ファイルの &CONTROL フィールドの calculation が 'scf' でない場合にアップロード不可となっていた問題を修正

    |

-   Quantum ESPRESSO

    -   Spin 有りの計算を行う際、入力ファイルの &system のブロックに starting_magnetization 行がデフォルトで入らなくなっていた問題を修正
    -   Electron Band Structure で、計算結果に有効質量の情報が表示されない問題を修正
    
        **※ Effective Mass (Table) につきましては、Job 作成者のみしか閲覧できなくなっています。（OpenMX でも同様です。）**

    -   X-Spectra の Job を実行するとエラーが出てしまう場合がある問題を一部解消
        
        **※ 計算が走らない場合もございますので、引き続き、試験的運用とさせていただきます。**

    |

-   OpenMX

    -   Create Job ダイアログの Site property settings の spin & charge 項目で各原子の初期電荷の設定を行うと、無効な入力ファイルが生成されてしまう問題を修正
    -   Energy Barrier (NEB) で、初期スピン設定が初期／終期構造で違ってしまう問題を修正

    |

-   LAMMPS

    -   ２つの入力ファイル「QuloudJob.lmp」と「in.QuloudJob」での元素ナンバリングが必ず一致するよう修正
    -   Molecular Dynamics で、Mean-Squared Displacement を計算する元素や、Radial Distribution Function を計算する元素ペアを限定すると「Create」ボタンがクリックできなくなる問題を修正
    -   Molecular Dynamics で、計算結果のAtomic Structure Trajectory が表示されない問題を修正
    -   Molecular Dynamics で、計算結果の Radial Distribution Function のグラフのデータ ラベルに誤りが生じる場合がある問題を修正

|
|

**Ver.6.1.0（2026.3.16）**

|

-   認証タイムアウト

    -   サインインしてから８時間経過後にサインアウトするよう修正

    |

-   UI/UX

    -   ダッシュボード

        -   ダッシュボードのシステムバー（Points、Expiration Date、Storageが表示されていた箇所）を削除
        -   ヘッドメニューにボードアイコンを追加し、クリックすると Points、Expiration Date、Storage をダイアログで表示するよう変更
        -   Project ボタン位置変更（上部 → 下部）
        -   Material 一覧の Edit ボタンを変更（ボタン → アイコン）
        -   Job 一覧の Edit ボタンを変更（ボタン → アイコン）

        |

    -   Material 詳細画面

        -   画面サイズによらずサイドメニューが表示されるよう修正
        -   Property ページ

            -   Job 選択を削除し、Property 選択を追加
            -   Property 選択には、完了しているかつ表示許可されている Job のみ表示
            -   Structure 選択を削除（Job が選択された場合は Final を自動選択）
            -   Job Detail ボタンを追加（クリックで Job 詳細ページに遷移）
            -   Files ボタンを追加（クリックで File ページに遷移）
            -   Modeling/Save As (Save As Matrial)/Create Job の位置とアイコンを調整
            -   ページ内リンク（TABLE OF CONTENT）を削除
            -   Lattice、Chemical、Description の位置を調整

            |

        -   Job ページ

            -   Job 一覧ページを追加

                -   表示データはダッシュボードと同様
                -   View アイコンをクリックすると Property ページでの表示切替を行う
                -   Files アイコンをクリックすると File ページに遷移
                -   Edit ボタンをクリックすると Job の名称と説明を編集するダイアログを表示
                -   Job 名称をクリックすると Job 詳細ページに遷移

                |

            -   Job 詳細ページ

                -   Job 選択、Structure 選択を削除

                |

            -   File ページ

                -   Structure 選択を削除（Job が選択された場合は Final を自動選択）

    |

-   入力ファイル直接アップロードによる Job 実行

    -   Material 作成ダイアログに Software の項目を追加
    -   Software の項目が選択された場合に File Upload で同時に Job を作成

    **※ 現時点では、FLARE の入力ファイルがアップロード不可となっております。また、Quantum ESPRESSO (PW) では、入力ファイルの &CONTROL フィールドの calculation が 'scf' でない場合にはアップロード不可となっております。ご了承ください。**

    |

-   Project、Material、Job の名前の重複制限

    -   Project 作成、更新に名前重複禁止の制御を追加（Tenant 毎）
    -   Material 作成、更新に名前重複禁止の制御を追加（Project 毎）
    -   Job 作成、更新に名前重複禁止の制御を追加（Material 毎）

    |

-   計算機能

    -   下記の Job を新たに追加

        -   Quantum ESPRESSO

            -   X-Spectra   **（試験的運用）**
            -   Phonon (ph.x)
            -   Energy Barrier (NEB)

            |

        -   ASE

            -   Energy Barrier (NEB)

        |

    -   OpenMX の Lattice Opt. の Optimization Method に以下の選択肢を追加

        -   Lattice Constants Optimization (\|a1\| = \|a2\| ≠ \|a3\|) by Steepest Descent (OptC4)

    |

-   Create Job ダイアログ

    -   作成する Job を選択する際、Types、Software、Workflows のどこからでも絞り込みが行えるよう変更
    -   下記の Software で Site propery settings 項目を追加し、各原子の拘束条件や初期スピンを設定できるよう変更

        -   Quantum ESPRESSO
        -   OpenMX
        -   RSDFT
        -   FLARE

        **※ OpenMX では、spin & charge 項目での各原子の初期電荷の設定を行うと、無効な入力ファイルが生成されてしまいますので、行わないようご注意ください。**

        **※ RSDFT では、spin & charge 項目での各原子の初期スピンの設定が無効となりますので、Initial Spin Difference での設定をお願いいたします。**

        **※ FLARE (On-the-Fly MD) では、constraint 項目での各原子の拘束条件の設定が無効となりますので、ご了承ください。**

    |

-   モデリング

    -   モデリングタイプの分類（Basic、Slab model、Interface、Add Molecule、Add Cell）を廃止し、あらゆる機能を一つの画面に集約
    -   Atomic Coordinates 項目を追加し、各原子の相対座標を設定できるよう変更
    -   Relative atomic position 項目を追加し、各原子を各方向に一括で移動できるよう変更
    -   Interface 項目では、追加する Film を「Add Crystal」で選択するよう変更
    -   Packmol 項目を追加（セルの格子ベクトル間角度がすべて 90 度の Crystal でのみ使用可能）

    |

-   ボタンの名称

    -   「Submit」ボタンの名称を、「Run」「Create」「Save」「Delete」「Copy」など、操作内容に即した名称に変更

|
|

**Ver.6.0.1（2025.12.12）**

|

-   UI/UX

    -   「Edit Job」ボタン表示の不具合を修正
    -   「Delete Job」ボタン表示の不具合を修正
    -   スペルミスを修正
    -   Job 検索時の Software 表示の不具合を修正
    -   ダッシュボードの Job 一覧の Software 名、Job Type 名表示の不具合を修正

    |

-   データベース検索

    -   不要な文字列が表示されていた不具合を修正

    |

-   モデリング

    -   原子サイズの不具合を修正
    -   分子モデリング時の原子移動の不具合を修正

    |

-   Quantum ESPRESSO

    -   擬ポテンシャルに応じたカットオフ推奨値設定の不具合を修正
    -   Job 設定編集・表示の不具合を修正
    -   収束性表示の不具合を修正

    |

-   OpenMX

    -   Job 設定情報表示の不具合を修正
    -   結果表示の不具合を修正
    -   収束性表示の不具合を修正

    |

-   RSDFT

    -   Car-Parrinello MD の Job 設定時の k 点数の上限値を変更（Γ点のみ）
    -   結果表示の不具合を修正
    -   大きすぎる Threads 並列数指定時の Job 実行停止
    -   波動関数（Kohn-Sham Orbitals）プロットの条件変更

    |

-   LAMMPS

    -   Job 設定情報表示の不具合を修正
    -   Job 設定編集機能の不具合を修正
    -   Atomic Structure Opt. 計算設定の不具合を修正
    -   Radial Distribution Function 計算設定の不具合を修正
    -   Radial Distribution Function および Mean-Squared Displacement 結果表示の不具合を修正

    |

-   FLARE

    -   バージョンを FLARE-1.4.1 に変更
    -   FLARE → LAMMPS の Job 引継ぎの不具合を修正

    |

-   ASE

    -   計算結果表示の不具合を修正

    |

-   Quloud-Mag

    -   パラメータ設定・表示の不具合を修正
    -   計算結果表示の不具合を修正

    |

-   その他

    -   Job 収束性（conv）の表示を第一原理計算（Quantum ESPRESSO, OpenMX, RSDFT）のみに変更

|
|

**Ver.6.0.0（2025.12.1）**

|

本バージョンで利用できる機能の概要と、旧バージョン（Ver. 5.1.5）からの変更点を記載します。

|
|

- Project

    - Project を Tenant のメンバーと共有する機能を新たに追加しました。

    |

- Material

    - 使用データベース

        -   Crystal：Materials Project
        -   Molecule：PubChem

        |

- アップロード可能なファイル形式

    -	CIF
    -	XYZ
    -	POSCAR（VASP 形式）
    -	OpenMX 入力ファイル
    -	Quantum ESPRESSO 入力ファイル

    |

- モデリング機能

    - モデリングのタイプ

        -   Basic（Crystal、Molecule 共通）
        -   Slab model（Crystal のみ）
        -   Interface（Crystal のみ）
        -   Add Molecule（Crystal のみ）
        -   Add Cell（Molecule のみ）

        **構造最適化時の原子移動の拘束条件 （動く方向を制限したり、完全に動かさないようにしたり）の設定（Constraint）と初期スピン差の設定（Spin difference）機能は、本バージョンでは廃止となりました。**

        **また、 Slab model モデリングで追加可能な、終端用の擬水素原子については、結合長や電荷の設定はできなくなりました。**

        |

- 計算 Job

**入力ファイルのアップロードにより計算 Job を登録する機能は、本バージョンでは廃止となりました。**

    - 計算 Job のタイプ

        -   First-Principles Calculation

            -   Single-Point SCF（Quantum ESPRESSO、OpenMX、RSDFT）
            -   Atomic Structure Opt.（Quantum ESPRESSO、OpenMX、RSDFT）
            -   Lattice Opt.（Quantum ESPRESSO、OpenMX、RSDFT）
            -   Electron Band Structure（Quantum ESPRESSO、OpenMX、RSDFT）
            -   Electron DOS（Quantum ESPRESSO、OpenMX、RSDFT）
            -   Energy Barrier (NEB)（OpenMX）
            -   First-Principles MD（OpenMX、RSDFT）
            -   Exchange Coupling Parameters（OpenMX）

            **Band Unfolding は、本バージョンでは廃止となりました。**

            |

        -   Classical Molecular Dynamics Simulation

            -   Atomic Structure Opt.（LAMMPS）
            -   Molecular Dynamics（LAMMPS）
                **※ dipole（双極子モーメント）の計算は、本バージョンではできなくなりました。**

            **Phonon Calculation は、本バージョンでは廃止となりました。**

            |

        -   Advanced Classical MD

            -   On-the-Fly MD（FLARE）
            -   Machine-Learning MD (Pretraind Potential)（ASE-MD）

            |

        -   Quloud-Mag

            -   First-Principles SCF（SPRKKR）
            -   Exchange Coupling Parameters（SPRKKR）
            -   Monte Carlo（Quloud-Mag）
            -   Micro-Magnetic Simulation（Quloud-Mag-LLG）
                **※ Job 登録時の Option Magnetic 選択欄は、本バージョンでは廃止となりました。**

            **Gilbert Damping Parameter、Transport Property、Monte Carlo (Snapshot of magnetic moments)、UppASD は、本バージョンでは廃止となりました。**

|
|

----------------------------------------
注意事項
----------------------------------------

|
|

################################################
計算 Job 実行時の注意事項（全般）
################################################

AWS の計算リソースの在庫切れにより、「Run」ボタンをクリックしても数時間 Status が「Preprared」のままになる場合がございます。

Job が失敗しているにもかかわらず、Status が Succeeded になってしまう場合がありますのでご注意ください。

|
|

################################################
ソフトウェア別注意事項
################################################

以下、注意事項をソフトウェア毎に記載します。

|
|

++++++++++++++++++++++++++++++++++++++++++++++++
Quantum ESPRESSO に関する注意事項
++++++++++++++++++++++++++++++++++++++++++++++++

Electron Band Structure と Electron DOS では、MPI Process 数を増やし過ぎると、エラーが出てしまいますのでご注意ください。

また、すべての Job につきまして、Thread 数を増やすと計算時間が長くなる場合がございますのでご注意ください。

Electron Band Structure と Electron DOS では、計算結果の Total Energy Information の表で、Elapsed Time (s) と CPU Time (s) の表示が不正確になっておりますので、ご注意ください。

Electron Band Structure と Electron DOS では、Exchange Correlation Functional の HSE06 は未対応となっております。詳しくは Quantum ESPRESSO の公式ドキュメント（https://www.quantum-espresso.org/Doc/pw_user_guide/node10.html）をご参照ください。

Atomic Structure Opt. と Lattice Opt. で Exchange Correlation Functional の HSE06 を使用する場合、Pseudopotential Set で Ultrasoft(rrkjus) や Projector Augmented Wave(kjpaw) を使用すると、力の計算が実行できずにエラーが出てしまいますので、Norm-conserving(oncvpsp04) を使用してください。

**Site property settings の spin 項目では、初期スピンは原則として元素ごとにしか設定できません。もし同じ元素で、原子ごとに異なる値を設定した場合には、その平均値が採用されるため、意図しない設定になってしまうおそれがありますのでご注意ください。**

**X-Spectra では、Ver.6.1.1 以前の入力ファイルを読み込むと、吸収サイトの情報が正しく反映されませんので、計算を実行する場合には Ver.6.1.2 で新しく Job を作成してください。**

X-Spectra では、Core.wfc ファイルが読み込まれず、エラーが出てしまう場合がありますのでご注意ください。

**Energy Barrier (NEB) では、初期 / 終期構造の Property 選択欄で initial 以外の構造を指定しても、その設定が正しく反映されず、initial の構造が入力されてしまう場合がありますのでご注意ください。**

Energy Barrier (NEB) では、Site property settings の constraints 項目で拘束条件を設定しても、その設定が「neb.in」ファイルには反映されませんので、NEB 計算で拘束条件を設定する場合には、「neb.in」ファイルの ATOMIC_POSITIONS セクションで、「QuloudJob.scf.in」ファイルと同様の拘束条件を設定してください。

|
|

++++++++++++++++++++++++++++++++++++++++++++++++
OpenMX に関する注意事項
++++++++++++++++++++++++++++++++++++++++++++++++

OpenMX では計算の際に擬原子基底関数を用いますが、対応している原子の種類が限定されているため、Job 登録・実行の際には  OpenMX Ver.3.9 ユーザーマニュアル（https://www.openmx-square.org/openmx_man3.9jp/openmx3.9_jp.pdf）の Table 1 と Table 2 をご参照ください。

**Exchange Coupling Parameters では、MPI Process 数がデフォルトの 1 のままだとエラーが出てしまいますので、MPI Process 数を増やして実行してください。**

**Energy Barrier (NEB) では、初期 / 終期構造の Property 選択欄で initial 以外の構造を指定しても、その設定が正しく反映されず、initial の構造が入力されてしまう場合がありますのでご注意ください。**

|
|

++++++++++++++++++++++++++++++++++++++++++++++++
RSDFT に関する注意事項
++++++++++++++++++++++++++++++++++++++++++++++++

モデルのサイズが大きい場合や、重い元素を含む場合には、メモリ不足によりエラーが出てしまいますので、Thread 数を増やして計算を実行してください。ただし、Thread 数を増やすと計算時間が長くなる場合がございますのでご注意ください。
**また、Thread 数を増やし過ぎた結果、エラーが出てしまう場合もございますので、ユーザー自身で適切な Thread 数を設定してください。**

**入力ファイルの直接アップロードによる Job 実行に関しまして、初期スピン設定ファイル「fort.980」がアップロードできない状態となっておりますのでご注意ください。**

|
|

++++++++++++++++++++++++++++++++++++++++++++++++
LAMMPS に関する注意事項
++++++++++++++++++++++++++++++++++++++++++++++++

計算 Job 登録時に原子間ポテンシャルファイルをユーザー自身でアップロードする場合、アップロード可能なファイル形式（拡張子）が下記に限定されておりますのでご注意ください。

-   '.eam'
-    '.meam'
-    '.tersoff'
-    '.tersoff.mod'
-    '.tersoff.modc'
-    '.ann'
-    '.flare'

モデルのサイズが大きい場合、CHGNet のポテンシャルを利用するとメモリ不足によりエラーが出てしまいますので、Thread 数を増やして計算を実行してください。ただし、Thread 数を増やすと計算時間が長くなる場合がございますのでご注意ください。

Molecular Dynamics では、下記の点にご注意ください。

- MD Steps を多くとり過ぎると、メモリ不足により Atomic Structure Trajectory のアニメーションが表示されなくなります。

- Ver.6.1 より、Mean-Squared Displacement (msd) のデータを出力するファイル名が変更となり、その影響で、Ver.6.0 以前での msd のデータがグラフ表示されなくなっております。

|
|

++++++++++++++++++++++++++++++++++++++++++++++++
ASE に関する注意事項
++++++++++++++++++++++++++++++++++++++++++++++++

**機械学習ポテンシャルのプロバイダーで fairchem を指定した場合、MPI Process 数がデフォルトの 1 のままだとエラーが出てしまいますので、MPI Process 数を増やして実行してください。**

**Energy Barrier (NEB) では、セルのデータが初期構造と終期構造で完全に一致していないとエラーが出てしまいますのでご注意ください。**

**Energy Barrier (NEB) では、初期 / 終期構造の Property 選択欄で initial 以外の構造を指定しても、その設定が正しく反映されず、initial の構造が入力されてしまう場合がありますのでご注意ください。**

|
|

++++++++++++++++++++++++++++++++++++++++++++++++
FLARE に関する注意事項
++++++++++++++++++++++++++++++++++++++++++++++++

**On-the-Fly MD では、Site property settings の spin 項目での各原子の初期スピンの設定、および constraint 項目での各原子の拘束条件の設定が無効となりますので、ご注意ください。**

|
|

################################################
モデリングに関する注意事項
################################################

モデリング機能に関して、下記の不具合がありますのでご注意ください。

-   Supercell 項目

    -   Supercell の値を増やしてから 1×1×1 に戻しても、モデルのサイズが元に戻りません。

    |

-   Sueface 項目

    -   原子を追加 / 削除してからスラブモデルを生成すると、原子の個数がおかしくなります。
    -   原子を追加 / 削除してからスラブモデルを生成後、Undo ボタンで原子追加 / 削除前の状態に戻り、原子を追加 / 削除せずにスラブモデルを生成すると、以前追加 / 削除した原子が再度追加 / 削除されてしまいます。

    |

-   Packmol 項目

    -   バルク構造の原子数を増やしてから、Packmol でモデルを生成すると、バルク構造の原子数が元に戻ってしまいます。
    -   Packmol でモデルを生成後、Undo ボタンが効かなくなります。