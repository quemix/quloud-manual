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
    -   Micro-Magnetic Simulation（Quloud-Mag-LLG）（Job 登録時の Option Magnetic 選択欄は廃止）

    **Gilbert Damping Parameter、Transport Property、Monte Carlo (Snapshot of magnetic moments)、UppASD は、本バージョンでは廃止となりました。**

|
|

++++++++++++++++++++++++++++++++++++++++++++++++
OpenMX に関する注意事項
++++++++++++++++++++++++++++++++++++++++++++++++

OpenMX では計算の際に擬原子基底関数を用いますが、対応している原子の種類が限定されているため、Job 登録・実行の際には  OpenMX Ver.3.9 ユーザーマニュアル（https://www.openmx-square.org/openmx_man3.9jp/openmx3.9_jp.pdf）の Table 1 と Table 2 をご参照ください。

|
|

++++++++++++++++++++++++++++++++++++++++++++++++
LAMMPS に関する注意事項
++++++++++++++++++++++++++++++++++++++++++++++++

計算 Job 登録時に原子間ポテンシャルファイルをユーザー自身でアップロードする場合、アップロード可能なファイル形式が下記に限定されておりますのでご注意ください。