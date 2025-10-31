==============================
入出力ファイルとログ
==============================

--------------------------------------------------------------
Quantum ESPRESSO
--------------------------------------------------------------

++++++++++++++++++++++++++++
QuloudJob.scf.in
++++++++++++++++++++++++++++

SCF 計算を行うためのファイルです。例えば Material を BaTiO3 として Job を登録すると、以下のようなファイルが作成されます。

**Single-Point SCF、Electron Band Structure、Electron DOS の場合**

::

    &control
     calculation = 'scf'
     prefix = 'QuloudJob'
     tstress = .true.
     tprnfor = .true.
     pseudo_dir = './'
     outdir = './work'
     verbosity = 'high'
    /
    &system
     nat = 5
     ntyp = 3
     ecutwfc = 88.2
     ecutrho = 352.8
     ibrav = 0
     tot_charge = 0
     occupations = 'smearing'
     smearing = 'gauss'
     degauss = 0.01
     nspin = 1
    /
    &electrons
     mixing_beta = 0.7
     conv_thr = 1e-10
     electron_maxstep = 100
    /
    ATOMIC_SPECIES
    Ba 137.327 Ba.pbe-spn-rrkjus_psl.1.0.0.UPF
    Ti 47.867 Ti.pbe-spn-rrkjus_psl.1.0.0.UPF
    O 15.999 O.pbe-nl-rrkjus_psl.1.0.0.UPF
    ATOMIC_POSITIONS {crystal}
    Ba 0.5 0.5 0.58254146
    Ti 0.0 0.0 0.1000427
    O 0.0 0.5 0.06422054
    O 0.5 0.0 0.06422054
    O 0.0 0.0 0.54897175
    CELL_PARAMETERS {angstrom}
    3.99037921 0.0 2.443402563455322e-16
    6.417019188399763e-16 3.99037921 2.443402563455322e-16
    0.0 0.0 4.10265539
    K_POINTS {automatic}
    4 4 4 0 0 0

入力パラメータの詳細は以下の通りです。

-	&control

    -	calculation：計算内容を設定します。デフォルトでは 'scf' となっています。
    -	prefix：入出力ファイルの先頭につける文字列を設定します。デフォルトでは 'QuloudJob' となっています。
    -	tstress： .true. の場合、圧力が計算されます。デフォルトでは .true. となっています。
    -	tprnfor： .true. の場合、力が計算されます。デフォルトでは .true. となっています。
    -	pseudo_dir：擬ポテンシャルファイルが置かれているディレクトリを入力します。
    -	outdir：入出力ファイルやテンポラリを置くディレクトリを指定します。
    -	verbosity：ログ出力の量を設定します。デフォルトでは 'high' となっています。

-	&system

    -	nat：モデルに含まれる原子の総数が表示されます。
    -	ntyp：モデルに含まれる原子の種類の総数が表示されます。
    -	ecutwfc：波動関数のエネルギーカットオフを設定します（単位は Ry）。
    -	ecutrho：電荷密度とポテンシャルのエネルギーカットオフを設定します（単位は Ry）。デフォルトでは ecutwfc の４倍となっています。
    -	ibrav：ブラべ格子の種類を指定します。0 の場合、後述する CELL_PARAMETERS で格子ベクトルを具体的に記述する必要があります。デフォルトでは 0 となっています。
    -	tot_charge：モデル全体の電荷量を設定します。電気的に中性の場合は 0、電子が１つ抜ける場合は +1、電子が１つ追加される場合は -1 とします。デフォルトでは 0 となっています。
    -	occupations：電子の状態数を計算する方法を設定します。デフォルトでは 'smearing' となっています。
    -	smearing：平滑化法の種類を指定します。デフォルトでは 'gauss' となっています。
    -	degauss：ガウシアン平滑化関数の広がりを指定します（単位は Ry）。デフォルトでは 0.01 となっています。
    -	nspin：スピン軌道相互作用を考慮するかどうか設定します。デフォルトでは 1（考慮しない）となっています。

-	&electrons

    -	mixing_beta：SCF 計算で、直前の計算で出てきた電子密度を、次の計算でどの割合で混ぜるかを設定します。デフォルトでは 0.7 となっています。
    -	conv_thr：SCF 計算で、エネルギー誤差がこの数値より小さくなったら、収束したと判定されます。デフォルトでは 1e-10 Ry となっています。
    -	electron_maxstep：SCF 計算での最大繰り返し回数を設定します。デフォルトでは 100 となっています。

-	ATOMIC_SPECIES：元素記号、質量数、擬ポテンシャルファイル名を記載します。

-	ATOMIC_POSITIONS：原子の位置を記載します。デフォルトでは、格子ベクトルを基準とした相対座標で表示されています。

-   CELL_PARAMETERS：前述した ibrav が 0 の場合、ここで格子ベクトルを具体的に記載します。デフォルトではオングストローム（Å）単位で表示されています。

-   K_POINTS：デフォルトでは k 点グリッドが自動生成されます。左の３つの数字は各方向の k 点グリッドの数を表しています。また、右の３つの数字はグリッドオフセットに関する情報で、デフォルトでは 0（オフセットなし）となっています。

**Atomic Structure Opt. の場合**

::
    
    &control
     calculation = 'relax'
     prefix = 'QuloudJob'
     tstress = .true.
     tprnfor = .true.
     pseudo_dir = './'
     outdir = './work'
     verbosity = 'high'
     etot_conv_thr = 0.00001
     forc_conv_thr = 0.0001
     nstep = 50
    /
    &system
     nat = 5
     ntyp = 3
     ecutwfc = 88.2
     ecutrho = 352.8
     ibrav = 0
     tot_charge = 0
     occupations = 'smearing'
     smearing = 'gauss'
     degauss = 0.01
     nspin = 1
    /
    &electrons
     mixing_beta = 0.7
     conv_thr = 1e-10
     electron_maxstep = 100
    /
    &ions
    /
    &cell
    /
    ATOMIC_SPECIES
    Ba 137.327 Ba.pbe-spn-rrkjus_psl.1.0.0.UPF
    Ti 47.867 Ti.pbe-spn-rrkjus_psl.1.0.0.UPF
    O 15.999 O.pbe-nl-rrkjus_psl.1.0.0.UPF
    ATOMIC_POSITIONS {crystal}
    Ba 0.5 0.5 0.58254146
    Ti 0.0 0.0 0.1000427
    O 0.0 0.5 0.06422054
    O 0.5 0.0 0.06422054
    O 0.0 0.0 0.54897175
    CELL_PARAMETERS {angstrom}
    3.99037921 0.0 2.443402563455322e-16
    6.417019188399763e-16 3.99037921 2.443402563455322e-16
    0.0 0.0 4.10265539
    K_POINTS {automatic}
    4 4 4 0 0 0

Atomic Structure Opt. では、以下のように設定が変更・追加されています。

-	&control

    -   calculation：計算内容を設定します。デフォルトでは 'relax' となっています。
    -	etot_conv_thr：（原子構造または格子定数の）最適化計算で、エネルギー値の変動がこの数値より小さくなったら、収束したと判定されます。デフォルトでは 0.00001 Ry となっています。
    -   forc_conv_thr：最適化計算で、力の値の変動がこの数値より小さくなったら、収束したと判定されます。デフォルトでは 0.0001 Ry/Bohr となっています。

    なお、上記２つの条件がともに満たされた場合にのみ、計算は収束したと判定されます。

    -   nstep：最適化計算のステップ数を設定します。デフォルトでは 50 となっています。

**Lattice Opt. の場合**

::

    &control
     calculation = 'vc-relax'
     prefix = 'QuloudJob'
     tstress = .true.
     tprnfor = .true.
     pseudo_dir = './'
     outdir = './work'
     verbosity = 'high'
     etot_conv_thr = 0.00001
     forc_conv_thr = 0.0001
     nstep = 50
    /
    &system
     nat = 5
     ntyp = 3
     ecutwfc = 88.2
     ecutrho = 352.8
     ibrav = 0
     tot_charge = 0
     occupations = 'smearing'
     smearing = 'gauss'
     degauss = 0.01
     nspin = 1
    /
    &electrons
     mixing_beta = 0.7
     conv_thr = 1e-10
     electron_maxstep = 100
    /
    &ions
    /
    &cell
     press = 0.0
     press_conv_thr = 0.5
    /
    ATOMIC_SPECIES
    Ba 137.327 Ba.pbe-spn-rrkjus_psl.1.0.0.UPF
    Ti 47.867 Ti.pbe-spn-rrkjus_psl.1.0.0.UPF
    O 15.999 O.pbe-nl-rrkjus_psl.1.0.0.UPF
    ATOMIC_POSITIONS {crystal}
    Ba 0.5 0.5 0.58254146
    Ti 0.0 0.0 0.1000427
    O 0.0 0.5 0.06422054
    O 0.5 0.0 0.06422054
    O 0.0 0.0 0.54897175
    CELL_PARAMETERS {angstrom}
    3.99037921 0.0 2.443402563455322e-16
    6.417019188399763e-16 3.99037921 2.443402563455322e-16
    0.0 0.0 4.10265539
    K_POINTS {automatic}
    4 4 4 0 0 0

Lattice Opt. では、以下のように設定が変更・追加されています。

-	&control

    -   calculation：計算内容を設定します。デフォルトでは 'vc-relax' となっています。
    -	etot_conv_thr：（原子構造または格子定数の）最適化計算で、エネルギー値の変動がこの数値より小さくなったら、収束したと判定されます。デフォルトでは 0.00001 Ry となっています。
    -   forc_conv_thr：最適化計算で、力の値の変動がこの数値より小さくなったら、収束したと判定されます。デフォルトでは 0.0001 Ry/Bohr となっています。

    なお、上記２つの条件がともに満たされた場合にのみ、計算は収束したと判定されます。

    -   nstep：最適化計算のステップ数を設定します。デフォルトでは 50 となっています。

-   &cell

    -   press：格子定数の最適化計算で、モデルに加わる圧力の目標値を設定します。デフォルトでは 0.0 Kbar となっています。
    -   press_conv_thr：格子定数の最適化計算で、圧力の値の変動がこの数値より小さくなったら、収束したと判定されます。デフォルトでは 0.5 Kbar となっています。

        なお、上記２つの条件（etot_conv_thr と forc_conv_thr）も併せて満たされた場合にのみ、計算は収束したと判定されます。

++++++++++++++++++++++++++++
QuloudJob.nscf.in
++++++++++++++++++++++++++++

SCF 計算により求められたポテンシャルを用いて、電子バンド計算や電子状態密度計算を行うためのファイルです。例えば Material を BaTiO3 として Job を登録すると、以下のようなファイルが作成されます。

**Electron Band Structure の場合**

::

    &control
     calculation = 'bands'
     prefix = 'QuloudJob'
     tstress = .true.
     tprnfor = .true.
     pseudo_dir = './'
     outdir = './work'
     verbosity = 'high'
    /
    &system
     nat = 5
     ntyp = 3
     nosym = .true.
     ecutwfc = 88.2
     ecutrho = 352.8
     ibrav = 0
     tot_charge = 0
     occupations = 'smearing'
     smearing = 'gauss'
     degauss = 0.01
     nspin = 1
    /
    &electrons
     mixing_beta = 0.7
     conv_thr = 1e-10
     electron_maxstep = 100
    /
    ATOMIC_SPECIES
    Ba 137.327 Ba.pbe-spn-rrkjus_psl.1.0.0.UPF
    Ti 47.867 Ti.pbe-spn-rrkjus_psl.1.0.0.UPF
    O 15.999 O.pbe-nl-rrkjus_psl.1.0.0.UPF
    ATOMIC_POSITIONS {crystal}
    Ba 0.5 0.5 0.58254146
    Ti 0.0 0.0 0.1000427
    O 0.0 0.5 0.06422054
    O 0.5 0.0 0.06422054
    O 0.0 0.0 0.54897175
    CELL_PARAMETERS {angstrom}
    3.99037921 0.0 2.443402563455322e-16
    6.417019188399763e-16 3.99037921 2.443402563455322e-16
    0.0 0.0 4.10265539
    K_POINTS {crystal_b}
    12 #auto
    0.0 0.0 0.0 20 !G
    0.0 0.5 0.0 20 !X
    0.5 0.5 0.0 20 !M
    0.0 0.0 0.0 20 !G
    0.0 0.0 0.5 20 !Z
    0.0 0.5 0.5 20 !R
    0.5 0.5 0.5 20 !A
    0.0 0.0 0.5 20 !Z
    0.0 0.5 0.0 20 !X
    0.0 0.5 0.5 20 !R
    0.5 0.5 0.0 20 !M
    0.5 0.5 0.5 20 !A
    #KPT  G  0.0 0.0 0.0 /
    #KPT  A  0.5 0.5 0.5 /
    #KPT  M  0.5 0.5 0.0 /
    #KPT  R  0.0 0.5 0.5 /
    #KPT  X  0.0 0.5 0.0 /
    #KPT  Z  0.0 0.0 0.5 /

"QuloudJob.scf.in" と異なる点は以下の通りです。

-	&control

    -	calculation：計算内容を設定します。デフォルトでは 'bands' となっています。

-	&system

    -	nosym：.true. の場合、k 点の対称化は行われず、入力ファイルの k 点リストがそのまま用いられます。また、電荷密度の対称化も行われません。デフォルトでは .true. となっています。

-   K_POINTS：電子バンドを計算する際の k 点の経路を設定します。上の例では G → X → M → G → Z → R → A → Z → X → R → M → A の経路に沿って電子バンド計算が行われます。各 k 点の座標は、逆格子ベクトルを基準とした相対座標で表示されています。なお、k 点座標の右の数字は、次の k 点とを結ぶ線上で何点サンプリングするかを表します。例えば最初の G 点の場合、座標の右の数字は 20 なので、G → X 間の k 点サンプリング数は 20 となります。

**Electron DOS の場合**

::

    &control
     calculation = 'nscf'
     prefix = 'QuloudJob'
     tstress = .true.
     tprnfor = .true.
     pseudo_dir = './'
     outdir = './work'
     verbosity = 'high'
    /
    &system
     nat = 5
     ntyp = 3
     ecutwfc = 88.2
     ecutrho = 352.8
     ibrav = 0
     tot_charge = 0
     occupations = 'tetrahedra'
     nspin = 1
    /
    &electrons
     mixing_beta = 0.7
     conv_thr = 1e-10
     electron_maxstep = 100
    /
    ATOMIC_SPECIES
    Ba 137.327 Ba.pbe-spn-rrkjus_psl.1.0.0.UPF
    Ti 47.867 Ti.pbe-spn-rrkjus_psl.1.0.0.UPF
    O 15.999 O.pbe-nl-rrkjus_psl.1.0.0.UPF
    ATOMIC_POSITIONS {crystal}
    Ba 0.5 0.5 0.58254146
    Ti 0.0 0.0 0.1000427
    O 0.0 0.5 0.06422054
    O 0.5 0.0 0.06422054
    O 0.0 0.0 0.54897175
    CELL_PARAMETERS {angstrom}
    3.99037921 0.0 2.443402563455322e-16
    6.417019188399763e-16 3.99037921 2.443402563455322e-16
    0.0 0.0 4.10265539
    K_POINTS {automatic}
    1 1 1 0 0 0

"QuloudJob.scf.in" と異なる点は以下の通りです。

-	&control

    -	calculation：計算内容を設定します。デフォルトでは 'nscf' となっています。

-	&system

    -	occupations：電子の状態数を計算する方法を設定します。デフォルトでは 'tetrahedra' となっています。

++++++++++++++++++++++++++++
QuloudJob.bands.in
++++++++++++++++++++++++++++

電子バンド計算（Electron Band Structure）に用いるファイルです。

::

    &bands
     outdir = './work'
     prefix='QuloudJob'
     filband='QuloudJob.bands'
    /

入力パラメータの詳細は以下の通りです。

-	&bands

    -	outdir：入出力ファイルやテンポラリを置くディレクトリを指定します。
    -	prefix：入出力ファイルの先頭につける文字列を設定します。デフォルトでは 'QuloudJob' となっています。
    -	filband：電子バンド計算の結果を出力するファイルの名前を指定します。デフォルトでは 'QuloudJob.bands' となっています。

++++++++++++++++++++++++++++
QuloudJob.dos.in
++++++++++++++++++++++++++++

電子状態密度計算（Electron DOS）に用いるファイルです。

::

    &dos
     outdir = './work'
     prefix='QuloudJob'
     fildos='QuloudJob.dos'
    /

入力パラメータの詳細は以下の通りです。

-	&dos

    -	outdir：入出力ファイルやテンポラリを置くディレクトリを指定します。
    -	prefix：入出力ファイルの先頭につける文字列を設定します。デフォルトでは 'QuloudJob' となっています。
    -	fildos：電子状態密度計算の結果を出力するファイルの名前を指定します。デフォルトでは 'QuloudJob.dos' となっています。

--------------------------------------------------------------
OpenMX
--------------------------------------------------------------

++++++++++++++++++++++++++++
openmx.in
++++++++++++++++++++++++++++

例えば Material を BaTiO3 として Job を登録すると、以下のようなファイルが作成されます。

**Single-Point SCF の場合**

::

    #
    #    File Name
    #

    System.CurrrentDirectory ./
    System.Name QuloudJob
    DATA.PATH /usr/local/rsdft/DFT_DATA19

    #
    # Definition of Atomic Species
    #

    Species.Number 3
    <Definition.of.Atomic.Species
     Ba Ba10.0-s3p2d2 Ba_PBE19
     O O6.0-s2p2d1 O_PBE19
     Ti Ti7.0-s3p2d1 Ti_PBE19
    Definition.of.Atomic.Species>

    #
    # Atoms
    #

    Atoms.Number 5
    Atoms.SpeciesAndCoordinates.Unit FRAC
    <Atoms.SpeciesAndCoordinates
     1 Ba 0.5 0.5 0.58254146 5.0 5.0
     2 Ti 0.0 0.0 0.1000427 6.0 6.0
     3 O 0.0 0.5 0.06422054 3.0 3.0
     4 O 0.5 0.0 0.06422054 3.0 3.0
     5 O 0.0 0.0 0.54897175 3.0 3.0
    Atoms.SpeciesAndCoordinates>
    Atoms.UnitVectors.Unit Ang
    <Atoms.UnitVectors
     3.99037921 0.0 2.443402563455322e-16
     6.417019188399763e-16 3.99037921 2.443402563455322e-16
     0.0 0.0 4.10265539
    Atoms.UnitVectors>

    #atomic.orbital Standard 
    ###
    ### SCF or Electronic System
    ###

    scf.XcType GGA-PBE 
    scf.SpinPolarization off 
    scf.ElectronicTemperature  300 
    scf.energycutoff 224.94602771541878 
    # scf.Ngrid 36 36 36 
    scf.maxIter 100 
    scf.EigenvalueSolver band 
    scf.Kgrid 4 4 4 
    scf.criterion 1e-10 
    scf.system.charge 0 
    scf.Mixing.Type rmm-diisk 
    scf.Init.Mixing.Weight 0.3 
    scf.Min.Mixing.Weight 0.001 
    scf.Max.Mixing.Weight 0.4 
    scf.Mixing.History 5 
    scf.Mixing.StartPulay 6 
    scf.Electric.Field 0 0 0 

入力パラメータの詳細は以下の通りです。

-	File Name

    -	System.CurrrentDirectory：出力ファイルを置くディレクトリを指定します。デフォルトでは ./ となっています。
    -	System.Name：出力ファイルのファイル名を指定します。デフォルトでは QuloudJob となっています。
    -	DATA.PATH：VPS および PAO ディレクトリへのパスを指定します。デフォルトでは /usr/local/rsdft/DFT_DATA19 となっています。

-	Definition of Atomic Species

    -	Species.Number：モデルに含まれる原子の種類の総数を指定します。
    -	Definition.of.Atomic.Species：モデルに含まれる原子の種類を指定します。
    
        記述は <Definition.of.Atomic.Species で始まり、Definition.of.Atomic.Species> で終わります。

        １番目の列では原子の種類の名前を指定します。この名前は、後述する Atoms.SpeciesAndCoordinates にて原子座標を指定するのに使います。
        
        ２番目の列では擬原子基底関数の拡張子無しのファイル名と、プリミティブ基底関数の数および縮約された基底関数の数を指定します。このファイルは DFT_DATA19/PAO ディレクトリに置く必要があります。上の例では、Ba の基底関数は Ba10.0-s3p2d2 となっていますが、Ba10.0 が DFT_DATA19/PAO ディレクトリにある擬原子基底関数の拡張子無しのファイル名を示します。s3 は s3>3 の略記であり、３つの s 軌道のプリミティブ軌道から３つの最適化された軌道が作られていることに対応します。つまり縮約は行わないことを意味します。縮約が無い場合、s3>3 と記述する代わりに s3 という簡単な記法を使用できます。p2、d2 も同様で、それぞれ p2>2、d2>2 の略記です。つまり、Ba10.0-s3p2d2 は Ba10.0-s3>3p2>2d2>2 と同等です。
        
        ３番目の列では擬ポテンシャルの拡張子無しのファイル名を指定します。このファイルは DFT_DATA19/VPS ディレクトリに置く必要があります。

-	Atoms

    -	Atoms.Number：モデルに含まれる原子の総数を指定します。
    -   Atoms.SpeciesAndCoordinates.Unit：原子座標の単位を指定します。デフォルトでは FRAC となっています。FRAC の場合には、後述する Atoms.UnitVectors で与えられた格子ベクトル a、b、c を基準とした相対座標になります。その際には 0.0 ～ 1.0 の範囲で座標が設定可能で、この範囲を超える座標は入力ファイルの読み込み後に自動的に調整されます。
    -   Atoms.SpeciesAndCoordinates：原子座標および各スピン毎の電子数を指定します。
        
        記述は <Atoms.SpeciesAndCoordinates で始まり、Atoms.SpeciesAndCoordinates> で終わります。

        １列目には原子を特定する連番を記述します。

        ２列目には事前に Definition.of.Atomic.Species の１列目で定義した原子の種類の名前を指定します。

        ３～５列目には、それぞれ x、y、z 座標を指定します。前述した Atoms.SpeciesAndCoordinates.Unit で FRAC を指定している場合は、３～５列目はそれぞれ a、b、c 軸を基準とした相対座標になり、値は 0.0 ～ 1.0 の範囲で指定します。この範囲を外れる数値は入力ファイルが読み込まれる段階で自動的に調整されます。

        ６および７列目には、各原子のアップスピンとダウンスピン状態のそれぞれの初期電子数を設定します。アップスピン電子数とダウンスピン電子数の合計は原子の価電子の数に等しくなるようにします。原子の価電子数は OpenMX Ver.3.9 ユーザーマニュアル（https://www.openmx-square.org/openmx_man3.9jp/openmx3.9_jp.pdf）の Table 1 と Table 2 に記載されています。LSDA-CA、 LSDA-PW、あるいは GGA-PBE を使用してスピン分極系を計算する場合、６および７列目の指定によって各原子に初期スピンを指定することができます。これにより強磁性状態や反強磁性状態などの計算が可能です。

    -   Atoms.UnitVectors.Unit：格子ベクトルの単位を指定します。デフォルトでは Ang（オングストローム（Å）単位）となっています。

    -   Atoms.UnitVectors：格子ベクトル a、b、c を指定します。
        
        記述は <Atoms.UnitVectors で始まり、Atoms.UnitVectors> で終わります。
        
        第１～３行はそれぞれ格子ベクトル a、b、c に対応します。

-   SCF or Electronic System

    -   scf.XcType：交換相関ポテンシャルを指定します。Quloud では LSDA-CA、LSDA-PW、GGA-PBE から選択できます。ここで LSDA-CA は Ceperley-Alder の局所スピン密度関数、LSDA-PW は、その GGA 形式において密度勾配をゼロとした PerdewWang 局所スピン密度関数です。GGA-PBE は Perdew らが提案する GGA 汎関数です。デフォルトでは GGA-PBE となっています。
    -   scf.SpinPolarization：電子系でスピン分極の計算を行う場合は ON を指定し、非スピン分極の計算を行う場合は OFF を指定します。scf.XcType で LDA を使用する場合は OFF に設定して下さい。前述の２つのオプションの他、ノンコリニア DFT 計算を行う場合には NC というオプションを指定して下さい。この計算については OpenMX Ver.3.9 ユーザーマニュアル（https://www.openmx-square.org/openmx_man3.9jp/openmx3.9_jp.pdf）の「ノンコリニア DFT」の章もご参照下さい。デフォルトでは OFF となっています。
    -   scf.ElectronicTemperature：電子温度（K）を設定します。デフォルトでは 300 となっています。
    -   scf.energycutoff：積分グリッド間隔を決定するカットオフエネルギーを指定します（単位は Ryd）。この積分グリッドは差電子クーロンポテンシャルと交換相関ポテンシャルに対する行列要素の計算および高速フーリエ変換（FFT）を用いた Poisson 方程式の解法のために使用されます。
    -   scf.maxIter：SCF の最大反復回数を設定します。SCF 反復ループは、収束条件が満たされない場合でもここで指定した回数で終了します。デフォルト値は 100 です。
    -   scf.EigenvalueSolver：固有値問題の計算手法を指定します。デフォルトでは Band（バンド計算）となっています。
    -   scf.Kgrid：scf.EigenvalueSolver により Band を指定した場合、k 空間の第１ブリルアンゾーンを等間隔メッシュにより離散化するためのグリッド数（n1, n2, n3）を指定する必要があります。ここでは n1 n2 n3 のように指定して下さい。
    -   scf.criterion：SCF 計算の収束条件を指定します（Hartree 単位）。SCF 反復は、dUele < scf.criterion という条件が満たされると終了します。ここで dUele とは、現在の SCF 反復とひとつ前の反復とのバンドエネルギーの絶対差です。デフォルト値は 1e-10 です。
    -   scf.system.charge：電子および正孔のドーピングの量を指定します。プラス・マイナス符号はそれぞれ正孔と電子のドーピングを表します。デフォルト値は 0 です。
    -   scf.Mixing.Type：SCF 計算の次の反復ステップに入力される電子密度（もしくは密度行列）を生成するための電子密度混合法を指定します。Quloud では、単純混合法（Simple）、RMM-DIISK 法のいずれかを指定することができます。RMM-DIISK 法を指定した場合、計算の初めでは Kerker 混合法を用いてある程度まで収束させ、その後 RMM-DIISK 法に切り替えます。切り替えるタイミングは、後述する scf.Mixing.StartPulay で指定することができます。デフォルトでは RMM-DIISK となっています。
    -   scf.Init.Mixing.Weight：初期の電子密度混合比を指定します。RMM-DIISK 法を指定した場合は、計算初期の Kerker 混合法での混合比を指定することになります。有効な範囲は 0 < scf.Init.Mixing.Weight < 1 で、デフォルト値は 0.3 です。
    -   scf.Min.Mixing.Weight：単純混合法および Kerker 混合法における混合比の下限を指定します。デフォルトでは 0.001 に設定されています。
    -   scf.Max.Mixing.Weight：単純混合法および Kerker 混合法における混合比の上限を指定します。デフォルトでは 0.4 に設定されています。
    -   scf.Mixing.History：RMM-DIISK 法では、SCF の次の反復ステップにおける入力電子密度（ハミルトニアン）を、過去の SCF 反復の電子密度（ハミルトニアン）に基づき推定します。scf.Mixing.History は、この推定に使用する過去の SCF 反復ステップ数を指定します。例えば、scf.Mixing.History を 3 に設定した場合、６回目の SCF 反復では過去の第５、４、３ステップの電子密度（ハミルトニアン）が考慮されます。OpenMX Ver.3.9 ユーザーマニュアル（https://www.openmx-square.org/openmx_man3.9jp/openmx3.9_jp.pdf）では 30 程度の値が推奨されていますが、Quloud でのデフォルト値は 5 となっています。
    -   scf.Mixing.StartPulay：RMM-DIISK 法を開始する SCF ステップを指定します。これらの方法を開始するまでの SCF ステップでは Kerker 混合法が使用されます。デフォルトでは 6 に設定されています。
    -   scf.Electric.Field：のこぎり波形で表される外部均一電場を導入することが可能です。例えば、a 軸に沿って 1.0 GV/m（10^9 V/m）の電場を適用するには、次のように指定します。

        ::

            scf.Electric.Field 1.0 0.0 0.0 # default=0.0 0.0 0.0 (GV/m)

        電場の符号は電子に作用するものとして定義されています。デフォルト値は 0 0 0 です。

**Atomic Structure Opt. の場合**

::

    #
    #    File Name
    #

    System.CurrrentDirectory ./
    System.Name QuloudJob
    DATA.PATH /usr/local/rsdft/DFT_DATA19

    #
    # Definition of Atomic Species
    #

    Species.Number 3
    <Definition.of.Atomic.Species
     Ba Ba10.0-s3p2d2 Ba_PBE19
     O O6.0-s2p2d1 O_PBE19
     Ti Ti7.0-s3p2d1 Ti_PBE19
    Definition.of.Atomic.Species>

    #
    # Atoms
    #

    Atoms.Number 5
    Atoms.SpeciesAndCoordinates.Unit FRAC
    <Atoms.SpeciesAndCoordinates
     1 Ba 0.5 0.5 0.58254146 5.0 5.0
     2 Ti 0.0 0.0 0.1000427 6.0 6.0
     3 O 0.0 0.5 0.06422054 3.0 3.0
     4 O 0.5 0.0 0.06422054 3.0 3.0
     5 O 0.0 0.0 0.54897175 3.0 3.0
    Atoms.SpeciesAndCoordinates>
    Atoms.UnitVectors.Unit Ang
    <Atoms.UnitVectors
     3.99037921 0.0 2.443402563455322e-16
     6.417019188399763e-16 3.99037921 2.443402563455322e-16
     0.0 0.0 4.10265539
    Atoms.UnitVectors>

    #atomic.orbital Standard 
    ###
    ### SCF or Electronic System
    ###

    scf.XcType GGA-PBE 
    scf.SpinPolarization off 
    scf.ElectronicTemperature  300 
    scf.energycutoff 224.94602771541878 
    # scf.Ngrid 36 36 36 
    scf.maxIter 100 
    scf.EigenvalueSolver band 
    scf.Kgrid 4 4 4 
    scf.criterion 1e-10 
    scf.system.charge 0 
    scf.Mixing.Type rmm-diisk 
    scf.Init.Mixing.Weight 0.3 
    scf.Min.Mixing.Weight 0.001 
    scf.Max.Mixing.Weight 0.4 
    scf.Mixing.History 5 
    scf.Mixing.StartPulay 6 
    scf.Electric.Field 0 0 0 
    ### 
    ### Opt
    ###
    MD.Type RF
    MD.maxIter 100
    MD.Opt.criterion 0.00029953
    MD.Opt.StartDIIS 10
    MD.Opt.DIIS.History 4

Atomic Structure Opt. では、以下の設定が追加されています。

-   Opt

    -   MD.Type：原子構造最適化のタイプを指定します。Quloud では Opt（最急降下法）、DIIS（反復部分空間法）、BFGS（Broyden-Fletcher-Goldfarb-Shanno 法）、RF（合理的関数法）、EF（固有ベクトル追跡法）が選択できます。デフォルトでは RF となっています。
    -   MD.maxIter：原子構造最適化計算における最大の反復回数を指定します。デフォルトでは 100 となっています。
    -   MD.Opt.criterion：原子構造最適化計算の収束条件を設定します。原子にかかる力の最大絶対値がここで指定した値より小さくなった場合に、最適化計算は終了します。デフォルトでは 0.00029953 Hartree/Bohr となっています。
    -   MD.Opt.StartDIIS：DIIS、BFGS、RF、EF による原子構造最適化を開始するステップを指定します。これらの方法を開始する以前のステップでは最急降下法が使用されます。デフォルトでは 10 となっています。
    -   MD.Opt.DIIS.History：原子構造最適化のために参照する過去のステップ数を指定します。デフォルトでは 4 となっています。

**Lattice Opt. の場合**

::

    #
    #    File Name
    #

    System.CurrrentDirectory ./
    System.Name QuloudJob
    DATA.PATH /usr/local/rsdft/DFT_DATA19

    #
    # Definition of Atomic Species
    #

    Species.Number 3
    <Definition.of.Atomic.Species
     Ba Ba10.0-s3p2d2 Ba_PBE19
     O O6.0-s2p2d1 O_PBE19
     Ti Ti7.0-s3p2d1 Ti_PBE19
    Definition.of.Atomic.Species>

    #
    # Atoms
    #

    Atoms.Number 5
    Atoms.SpeciesAndCoordinates.Unit FRAC
    <Atoms.SpeciesAndCoordinates
     1 Ba 0.5 0.5 0.58254146 5.0 5.0
     2 Ti 0.0 0.0 0.1000427 6.0 6.0
     3 O 0.0 0.5 0.06422054 3.0 3.0
     4 O 0.5 0.0 0.06422054 3.0 3.0
     5 O 0.0 0.0 0.54897175 3.0 3.0
    Atoms.SpeciesAndCoordinates>
    Atoms.UnitVectors.Unit Ang
    <Atoms.UnitVectors
     3.99037921 0.0 2.443402563455322e-16
     6.417019188399763e-16 3.99037921 2.443402563455322e-16
     0.0 0.0 4.10265539
    Atoms.UnitVectors>

    #atomic.orbital Standard 
    ###
    ### SCF or Electronic System
    ###

    scf.XcType GGA-PBE 
    scf.SpinPolarization off 
    scf.ElectronicTemperature  300 
    scf.energycutoff 224.94602771541878 
    # scf.Ngrid 36 36 36 
    scf.maxIter 100 
    scf.EigenvalueSolver band 
    scf.Kgrid 4 4 4 
    scf.criterion 1e-10 
    scf.system.charge 0 
    scf.Mixing.Type rmm-diisk 
    scf.Init.Mixing.Weight 0.3 
    scf.Min.Mixing.Weight 0.001 
    scf.Max.Mixing.Weight 0.4 
    scf.Mixing.History 5 
    scf.Mixing.StartPulay 6 
    scf.Electric.Field 0 0 0 
    level.of.stdout                   1
    level.of.fileout                  1
    ### 
    ### Lattice Opt
    ###
    MD.Type RFC5
    MD.maxIter 100
    MD.Opt.criterion 0.00029953
    MD.Opt.StartDIIS 10
    MD.Opt.DIIS.History 4

Lattice Opt. では、以下の設定が追加されています。

-   Lattice Opt

    -   MD.Type：格子定数最適化のタイプを指定します。Quloud で選択できるオプションは以下の通りです。
                
            -   OptC1：原子座標を固定したまま、格子ベクトルに拘束をかけずに最適化を行います。最適化は、最急降下法によって行われます。
            -   OptC5：原子座標、格子ベクトルともに拘束をかけずに同時に最適化を行います。最適化は、最急降下法によって行われます。
            -   RFC5：原子座標、格子ベクトルともに拘束をかけずに同時に最適化を行います。最適化は、RF 法、DIIS 法、BFGS 法によって行われます。
        
        デフォルトでは RFC5 となっています。

    -   MD.maxIter：格子定数最適化計算における最大の反復回数を指定します。デフォルトでは 100 となっています。
    -   MD.Opt.criterion：格子定数最適化計算の収束条件を設定します。原子にかかる力の最大絶対値がここで指定した値より小さくなった場合に、最適化計算は終了します。デフォルトでは 0.00029953 Hartree/Bohr となっています。
    -   MD.Opt.StartDIIS：RF、DIIS、BFGS による格子定数最適化を開始するステップを指定します。これらの方法を開始する以前のステップでは最急降下法が使用されます。デフォルトでは 10 となっています。
    -   MD.Opt.DIIS.History：格子定数最適化のために参照する過去のステップ数を指定します。デフォルトでは 4 となっています。

**Electron Band Structure の場合**

::

    #
    #    File Name
    #

    System.CurrrentDirectory ./
    System.Name QuloudJob
    DATA.PATH /usr/local/rsdft/DFT_DATA19

    #
    # Definition of Atomic Species
    #

    Species.Number 3
    <Definition.of.Atomic.Species
     Ba Ba10.0-s3p2d2 Ba_PBE19
     O O6.0-s2p2d1 O_PBE19
     Ti Ti7.0-s3p2d1 Ti_PBE19
    Definition.of.Atomic.Species>

    #
    # Atoms
    #

    Atoms.Number 5
    Atoms.SpeciesAndCoordinates.Unit FRAC
    <Atoms.SpeciesAndCoordinates
     1 Ba 0.5 0.5 0.58254146 5.0 5.0
     2 Ti 0.0 0.0 0.1000427 6.0 6.0
     3 O 0.0 0.5 0.06422054 3.0 3.0
     4 O 0.5 0.0 0.06422054 3.0 3.0
     5 O 0.0 0.0 0.54897175 3.0 3.0
    Atoms.SpeciesAndCoordinates>
    Atoms.UnitVectors.Unit Ang
    <Atoms.UnitVectors
     3.99037921 0.0 2.443402563455322e-16
     6.417019188399763e-16 3.99037921 2.443402563455322e-16
     0.0 0.0 4.10265539
    Atoms.UnitVectors>

    #atomic.orbital Standard 
    ###
    ### SCF or Electronic System
    ###

    scf.XcType GGA-PBE 
    scf.SpinPolarization off 
    scf.ElectronicTemperature  300 
    scf.energycutoff 224.94602771541878 
    # scf.Ngrid 36 36 36 
    scf.maxIter 100 
    scf.EigenvalueSolver band 
    scf.Kgrid 4 4 4 
    scf.criterion 1e-10 
    scf.system.charge 0 
    scf.Mixing.Type rmm-diisk 
    scf.Init.Mixing.Weight 0.3 
    scf.Min.Mixing.Weight 0.001 
    scf.Max.Mixing.Weight 0.4 
    scf.Mixing.History 5 
    scf.Mixing.StartPulay 6 
    scf.Electric.Field 0 0 0 
    ### 
    ### Band
    ###
    Band.dispersion on
    Band.Nkpath 11 #auto
    <Band.kpath
      20 0.0 0.0 0.0   0.0 0.5 0.0 G X
      20 0.0 0.5 0.0   0.5 0.5 0.0 X M
      20 0.5 0.5 0.0   0.0 0.0 0.0 M G
      20 0.0 0.0 0.0   0.0 0.0 0.5 G Z
      20 0.0 0.0 0.5   0.0 0.5 0.5 Z R
      20 0.0 0.5 0.5   0.5 0.5 0.5 R A
      20 0.5 0.5 0.5   0.0 0.0 0.5 A Z
      20 0.0 0.0 0.5   0.0 0.5 0.0 Z X
      20 0.0 0.5 0.0   0.0 0.5 0.5 X R
      20 0.0 0.5 0.5   0.5 0.5 0.0 R M
      20 0.5 0.5 0.0   0.5 0.5 0.5 M A
    Band.kpath>
    #KPT  G  0.0 0.0 0.0 /
    #KPT  A  0.5 0.5 0.5 /
    #KPT  M  0.5 0.5 0.0 /
    #KPT  R  0.0 0.5 0.5 /
    #KPT  X  0.0 0.5 0.0 /
    #KPT  Z  0.0 0.0 0.5 /
    #KPTLABEL   G X M G Z R A Z X R M A  /

Electron Band Structure では、以下の設定が追加されています。

-   Band

    -   Band.dispersion：バンド分散を評価する場合、ON に設定します。
    -   Band.Nkpath：バンド分散の計算における経路の数を指定します。デフォルトでは 11 となっています。
    -   Band.kpath：バンド分散の経路を指定します。

        記述は <Band.kpath で始まり、Band.kpath> で終わります。行数は Band.Nkpath で指定した数と同じにする必要があります。

        第１列には経路上で固有値を計算する格子の数を指定します。
        
        続く n1, n2, n3 および n1’, n2’, n3’ は、逆格子ベクトルを基底とする第１ブリルアンゾーンの経路の開始および終了の k 点を指定します。逆格子ベクトルは Atoms.UnitVectors で指定した格子ベクトルを用いて計算されます。
        
        最後の２つの英文字は経路の開始および終了の k 点の名前を指定します。

**Electron DOS の場合**

::

    #
    #    File Name
    #

    System.CurrrentDirectory ./
    System.Name QuloudJob
    DATA.PATH /usr/local/rsdft/DFT_DATA19

    #
    # Definition of Atomic Species
    #

    Species.Number 3
    <Definition.of.Atomic.Species
     Ba Ba10.0-s3p2d2 Ba_PBE19
     O O6.0-s2p2d1 O_PBE19
     Ti Ti7.0-s3p2d1 Ti_PBE19
    Definition.of.Atomic.Species>

    #
    # Atoms
    #

    Atoms.Number 5
    Atoms.SpeciesAndCoordinates.Unit FRAC
    <Atoms.SpeciesAndCoordinates
     1 Ba 0.5 0.5 0.58254146 5.0 5.0
     2 Ti 0.0 0.0 0.1000427 6.0 6.0
     3 O 0.0 0.5 0.06422054 3.0 3.0
     4 O 0.5 0.0 0.06422054 3.0 3.0
     5 O 0.0 0.0 0.54897175 3.0 3.0
    Atoms.SpeciesAndCoordinates>
    Atoms.UnitVectors.Unit Ang
    <Atoms.UnitVectors
     3.99037921 0.0 2.443402563455322e-16
     6.417019188399763e-16 3.99037921 2.443402563455322e-16
     0.0 0.0 4.10265539
    Atoms.UnitVectors>

    #atomic.orbital Standard 
    ###
    ### SCF or Electronic System
    ###

    scf.XcType GGA-PBE 
    scf.SpinPolarization off 
    scf.ElectronicTemperature  300 
    scf.energycutoff 224.94602771541878 
    # scf.Ngrid 36 36 36 
    scf.maxIter 100 
    scf.EigenvalueSolver band 
    scf.Kgrid 4 4 4 
    scf.criterion 1e-10 
    scf.system.charge 0 
    scf.Mixing.Type rmm-diisk 
    scf.Init.Mixing.Weight 0.3 
    scf.Min.Mixing.Weight 0.001 
    scf.Max.Mixing.Weight 0.4 
    scf.Mixing.History 5 
    scf.Mixing.StartPulay 6 
    scf.Electric.Field 0 0 0 
    ### 
    ### DOS
    ###
    Dos.fileout on
    Dos.Erange -20 20
    Dos.Kgrid 1 1 1 

Electron DOS では、以下の設定が追加されています。

-   DOS

    -   Dos.fileout：状態密度を評価する場合、ON に設定します。
    -   Dos.Erange：状態密度計算におけるエネルギーの範囲を eV 単位で指定します。デフォルトでは -20 eV ～ 20 eV となっています。
    -   Dos.Kgrid：状態密度計算を行う上で、第１ブリルアンゾーンを離散化するために（n1, n2, n3）の格子点を指定します。

**Energy Barrier (NEB) の場合**

::

    #
    #    File Name
    #

    System.CurrrentDirectory ./
    System.Name QuloudJob
    DATA.PATH /usr/local/rsdft/DFT_DATA19

    #
    # Definition of Atomic Species
    #

    Species.Number 3
    <Definition.of.Atomic.Species
     Ba Ba10.0-s3p2d2 Ba_PBE19
     O O6.0-s2p2d1 O_PBE19
     Ti Ti7.0-s3p2d1 Ti_PBE19
    Definition.of.Atomic.Species>

    #
    # Atoms
    #

    Atoms.Number 5
    Atoms.SpeciesAndCoordinates.Unit FRAC
    <Atoms.SpeciesAndCoordinates
     1 Ba 0.5 0.5 0.58254146 5.0 5.0
     2 Ti 0.0 0.0 0.1000427 6.0 6.0
     3 O 0.0 0.5 0.06422054 3.0 3.0
     4 O 0.5 0.0 0.06422054 3.0 3.0
     5 O 0.0 0.0 0.54897175 3.0 3.0
    Atoms.SpeciesAndCoordinates>
    Atoms.UnitVectors.Unit Ang
    <Atoms.UnitVectors
     3.99037921 0.0 2.443402563455322e-16
     6.417019188399763e-16 3.99037921 2.443402563455322e-16
     0.0 0.0 4.10265539
    Atoms.UnitVectors>

    <NEB.Atoms.SpeciesAndCoordinates
     1 Ba 0.5 0.5 0.58254146 5.0 5.0
     2 Ti 0.0 0.0 0.1000427 6.0 6.0
     3 O 0.0 0.5 0.06422054 3.0 3.0
     4 O 0.5 0.0 0.06422054 3.0 3.0
     5 O 0.0 0.0 0.54897175 3.0 3.0
    NEB.Atoms.SpeciesAndCoordinates>
    #atomic.orbital Standard 
    ###
    ### SCF or Electronic System
    ###

    scf.XcType GGA-PBE 
    scf.SpinPolarization off 
    scf.ElectronicTemperature  300 
    scf.energycutoff 224.94602771541878 
    # scf.Ngrid 36 36 36 
    scf.maxIter 100 
    scf.EigenvalueSolver band 
    scf.Kgrid 4 4 4 
    scf.criterion 1e-10 
    scf.system.charge 0 
    scf.Mixing.Type rmm-diisk 
    scf.Init.Mixing.Weight 0.3 
    scf.Min.Mixing.Weight 0.001 
    scf.Max.Mixing.Weight 0.4 
    scf.Mixing.History 5 
    scf.Mixing.StartPulay 6 
    scf.Electric.Field 0 0 0 
    MD.Type NEB
    MD.NEB.Number.Images 10
    MD.NEB.Spring.Const 0.1
    MD.maxIter 100
    MD.Opt.criterion 0.01
    MD.Opt.StartDIIS 5
    MD.Opt.DIIS.History 3

Energy Barrier (NEB) では、以下の設定が追加されています。

-   Atoms

    -   NEB.Atoms.SpeciesAndCoordinates：生成物の原子座標および各スピン毎の電子数を指定します。記述の方法は Atoms.SpeciesAndCoordinates（反応物の場合）と同様です。

-   その他のパラメータ

    -   MD.Type：NEB 計算を行う場合、NEB に設定します。
    -   MD.NEB.Number.Images：エネルギー経路中のイメージ数を指定します。ただし、２つの終端構造（反応物と生成物）はイメージの数から除きます。デフォルトでは 10 となっています。
    -   MD.NEB.Spring.Const：バネ定数を設定します。デフォルトでは 0.1 となっています。
    -   MD.maxIter：エネルギー経路の最適化計算における最大の反復回数を指定します。デフォルトでは 100 となっています。
    -   MD.Opt.criterion：エネルギー経路の最適化計算の収束条件を設定します。原子にかかる力の最大絶対値がここで指定した値より小さくなった場合に、最適化計算は終了します。デフォルトでは 0.01 Hartree/Bohr となっています。
    -   MD.Opt.StartDIIS：エネルギー経路の最適化はハイブリッド最適化法（DIIS + BFGS）によって行います。ここでは、ハイブリッド最適化法を開始するステップを指定します。それ以前のステップでは最急降下法が使用されます。デフォルトでは 5 となっています。
    -   MD.Opt.DIIS.History：エネルギー経路の最適化のために参照する過去のステップ数を指定します。デフォルトでは 3 となっています。

--------------------------------------------------------------
RSDFT
--------------------------------------------------------------

--------------------------------------------------------------
LAMMPS
--------------------------------------------------------------

--------------------------------------------------------------
FLARE
--------------------------------------------------------------

++++++++++++++++++++++++++++
QuloudJob.yaml
++++++++++++++++++++++++++++

--------------------------------------------------------------
ASE-MD
--------------------------------------------------------------

--------------------------------------------------------------
SPRKKR
--------------------------------------------------------------

--------------------------------------------------------------
Quloud-Mag-LLG
--------------------------------------------------------------


--------------------------------------------------------------
ログ
--------------------------------------------------------------


