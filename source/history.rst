========================================
仕様変更履歴
========================================

|
|

----------------------------------------
Ver.6.0.1 (2025.12.10)
----------------------------------------

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

    -   ジョブ収束性（conv）の表示を第一原理計算（Quantum ESPERSSO, OpenMX, RSDFT）のみに変更