========================================
本バージョンの仕様
========================================

本バージョンで利用できる機能の概要と、旧バージョンからの変更点を記載します。

|
|

----------------------------------------
Project
----------------------------------------

Project を Tenant のメンバーと共有する機能を新たに追加しました。

|
|

----------------------------------------
Material
----------------------------------------

使用データベース

-   Crystal：Materials Project
-   Molecule：PubChem

|

アップロード可能なファイル形式

-	CIF
-	XYZ
-	POSCAR（VASP 形式）
-	OpenMX 入力ファイル
-	Quantum ESPRESSO 入力ファイル

|
|

----------------------------------------
モデリング機能
----------------------------------------

モデリングのタイプ

-   Basic（Crystal、Molecule 共通）
-   Slab model（Crystal のみ）
-   Interface（Crystal のみ）
-   Add Molecule（Crystal のみ）
-   Add Cell（Molecule のみ）

**構造最適化時の原子移動の拘束条件 （動く方向を制限したり、完全に動かさないようにしたり）の設定（Constraint）と初期スピン差の設定（Spin difference）機能は、本バージョンでは廃止となりました。**

**また、 Slab model モデリングで追加可能な、終端用の擬水素原子については、結合長や電荷の設定はできなくなりました。**

|
|

----------------------------------------
計算 Job
----------------------------------------

**入力ファイルのアップロードにより計算 Job を登録する機能は、本バージョンでは廃止となりました。**

計算 Job のタイプ

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

以下に、計算 Job 実行時の注意事項をソフトウェアごとに記載します。

|
|

++++++++++++++++++++++++++++++++++++++++++++++++
Quantum ESPRESSO に関する注意事項
++++++++++++++++++++++++++++++++++++++++++++++++

Electron Band Structure と Electron DOS で MPI Process 数を増やすとエラーが出てしまうため、デフォルト設定の 1 のまま実行してください。

また、すべての Job につきまして、Thread 数を増やすと計算時間が長くなる場合がございますのでご注意ください。

|
|

++++++++++++++++++++++++++++++++++++++++++++++++
OpenMX に関する注意事項
++++++++++++++++++++++++++++++++++++++++++++++++

OpenMX では計算の際に擬原子基底関数を用いますが、対応している原子の種類が限定されているため、Job 登録・実行の際には  OpenMX Ver.3.9 ユーザーマニュアル（https://www.openmx-square.org/openmx_man3.9jp/openmx3.9_jp.pdf）の Table 1 と Table 2 をご参照ください。

|
|

++++++++++++++++++++++++++++++++++++++++++++++++
RSDFT に関する注意事項
++++++++++++++++++++++++++++++++++++++++++++++++

モデルのサイズが大きい場合や、重い元素を含む場合には、メモリ不足によりエラーが出てしまいますので、Thread 数を増やして計算を実行してください。ただし、Thread 数を増やすと計算時間が長くなる場合がございますのでご注意ください。
**また、Thread 数を増やし過ぎると、計算が不安定になり、エラーが出てしまう場合もございますので、ユーザー自身で適切な Thread 数を設定してください。**

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