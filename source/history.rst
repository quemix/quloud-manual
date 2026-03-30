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

**Ver.6.1.1（2026.3.30）**

|

-   入力ファイル直接アップロードによる Job 実行

    -   FLARE の入力ファイルがアップロード不可となっていた問題を修正
    -   Quantum ESPRESSO (PW) で、入力ファイルの &CONTROL フィールドの calculation が 'scf' でない場合にアップロード不可となっていた問題を修正

    |

-   Quantum ESPRESSO

    -   Spin 有りの計算を行う際、入力ファイルの &system のブロックに starting_magnetization 行がデフォルトで入らなくなっていた問題を修正
    -   Electron Band Structure で、計算結果に有効質量の情報が表示されない問題を修正
    
        **※ Effective Mass (Table) につきましては、Job 作成者のみしか閲覧できなくなっています。**

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

一度「Run Job」ボタンから Job を実行した後に、再度「Run Job」ボタンから Job を実行すると、Status が「Failed」になってしまう場合がございますのでご注意ください。

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

Electron Band Structure と Electron DOS では、Exchange Correlation Functional の HSE06 は未対応となっております。詳しくは Quantum ESPRESSO の公式ドキュメント（https://www.quantum-espresso.org/Doc/pw_user_guide/node10.html）をご参照ください。

Atomic Structure Opt. と Lattice Opt. で Exchange Correlation Functional の HSE06 を使用する場合、Pseudopotential Set で Ultrasoft(rrkjus) や Projector Augmented Wave(kjpaw) を使用すると、力の計算が実行できずにエラーが出てしまいますので、Norm-conserving(oncvpsp04) を使用してください。

下記の Job では、Create Job ダイアログで 設定した通りの情報が、Job 詳細ページの「Settings」項目に表示されない場合がございますので、ご注意ください。

-   Energy Barrier (NEB)
-   X-Spectra
-   Phonon (ph.x)

**現在、Electron Band Structure の計算結果のうち、Effective Mass (Table) の表が、Job 作成者のみしか閲覧できなくなっていますので、ご注意ください。**

X-Spectra では、Create Job ダイアログでの入力パラメータの設定に関して下記の不具合がありますので、ご注意ください。

-   XSPECTRA.IN の input_xspectra 項目内の X-ray k vector と X-ray epsilon というパラメータでは、各成分を -1 から 1 までの範囲で、0.1 刻みで調節できますが、Create Job ダイアログでは表示上 -1, 0, 1 の整数値しかとらないように見えます。
-   XSPECTRA.IN の plot 項目内の Gamma mode で variable を選択すると Gamma value というパラメータが現れます。このパラメータの各成分の下限値は 1E-4 ですが、Create Job ダイアログでは表示上 0 になっているように見えます。

|
|

++++++++++++++++++++++++++++++++++++++++++++++++
OpenMX に関する注意事項
++++++++++++++++++++++++++++++++++++++++++++++++

OpenMX では計算の際に擬原子基底関数を用いますが、対応している原子の種類が限定されているため、Job 登録・実行の際には  OpenMX Ver.3.9 ユーザーマニュアル（https://www.openmx-square.org/openmx_man3.9jp/openmx3.9_jp.pdf）の Table 1 と Table 2 をご参照ください。

**また、Exchange Coupling Parameters では、MPI Process 数がデフォルトの 1 のままだとエラーが出てしまいますので、MPI Process 数を増やして実行してください。**

|
|

++++++++++++++++++++++++++++++++++++++++++++++++
RSDFT に関する注意事項
++++++++++++++++++++++++++++++++++++++++++++++++

モデルのサイズが大きい場合や、重い元素を含む場合には、メモリ不足によりエラーが出てしまいますので、Thread 数を増やして計算を実行してください。ただし、Thread 数を増やすと計算時間が長くなる場合がございますのでご注意ください。
**また、Thread 数を増やし過ぎた結果、エラーが出てしまう場合もございますので、ユーザー自身で適切な Thread 数を設定してください。**

**各原子の初期スピンの設定につきまして、Create Job ダイアログの Site property settings の spin & charge 項目での設定は無効となってしまいますので、Initial Spin Difference での設定をお願いいたします。**

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

また、Molecular Dynamics で MD Steps を多くとり過ぎると、メモリ不足により Atomic Structure Trajectory のアニメーションが表示されなくなりますのでご注意ください。

さらに、モデルのサイズが大きい場合、CHGNet のポテンシャルを利用するとメモリ不足によりエラーが出てしまいますので、Thread 数を増やして計算を実行してください。ただし、Thread 数を増やすと計算時間が長くなる場合がございますのでご注意ください。

Ver.6.1 より、Molecular Dynamics の Mean-Squared Displacement (msd) のデータを出力するファイル名が変更となり、その影響で、Ver.6.0 以前での msd のデータがグラフ表示されなくなっております。ご了承ください。

Molecular Dynamics では、Create Job ダイアログで 設定した通りの情報が、Job 詳細ページの「Settings」項目に表示されない場合がございます。
具体的には、actions で npt を選択し、Anisotropy で Triclinic を選択すると、Params3（Pressure1 (bars)、Pressure2 (bars)、Anisotropy）が正しく表示されません。ご注意ください。

|
|

++++++++++++++++++++++++++++++++++++++++++++++++
ASE に関する注意事項
++++++++++++++++++++++++++++++++++++++++++++++++

**機械学習ポテンシャルのプロバイダーで fairchem を指定した場合、MPI Process 数がデフォルトの 1 のままだとエラーが出てしまいますので、MPI Process 数を増やして実行してください。**

**Energy Barrier (NEB) では、セルのデータが初期構造と終期構造で完全に一致していないとエラーが出てしまいますので、ご注意ください。**

Energy Barrier (NEB) では、一度作成した Job を、Job 詳細ページの「Edit Job」ボタンから編集する機能が無効になっておりますので、ご注意ください。

|
|

++++++++++++++++++++++++++++++++++++++++++++++++
FLARE に関する注意事項
++++++++++++++++++++++++++++++++++++++++++++++++

**On-the-Fly MD では、Create Job ダイアログの Site property settings の constraint 項目で、各原子の拘束条件を設定しても無効となってしまいますので、ご注意ください。**

|
|

################################################
その他の注意事項
################################################

Job 詳細ページの「Delete Job」ボタンから Job を削除しても、Job 名の重複禁止の制御は無効化されません。そのため、同一 Material 内では削除した Job と同じ名前の Job も作成できませんのでご注意ください。

作成した Job を、Job 詳細ページの「Copy Job」ボタンでコピーする際には、Job 名の重複禁止の制御が無効となり、同じ名前の Job が作成できてしまうのでご注意ください。

招待画面（トップ画面で「Invitation」をクリックすると移動する画面）で、一度追加した新規ユーザーのメールアドレスを「Deny」ボタンで却下する機能は、そのアドレスを追加した人物のみ使用可能となっています。