---
wts:
  title: 20 - Azure TCO 計算ツールを使用する (10 分)
  module: 'Module 06: Describe Azure cost management and service level agreements'
---
# <a name="20---use-the-azure-tco-calculator-10-min"></a>20 - Azure TCO 計算ツールを使用する (10 分)


このチュートリアルでは、総保有コスト (TCO) 計算ツールを使用して、オンプレミス環境とのコスト比較レポートを作成します。

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: This walkthrough provides example definitions of on-premises infrastructure and workloads for a typical datacenter. To create a TCO Calculator report, use the example definitions or provide details of your <bpt id="p1">*</bpt>actual<ept id="p1">*</ept> on-premises infrastructure and workloads.

# <a name="task-1-configure-the-tco-calculator"></a>タスク 1:TCO 計算ツールを構成する

このタスクでは、計算ツールにインフラストラクチャ情報を追加します。 

1. ブラウザーで、[総保有コスト (TCO) 計算ツール](https://azure.microsoft.com/en-us/pricing/tco/calculator/) ページに移動します。

2. オンプレミスのサーバー インフラストラクチャに関する詳細を追加するには、 **[ワークロードの定義]** ペインの **[+ サーバー ワークロードの追加]** をクリックします。

    | 設定 | 値 |
    | -- | -- |
    | 名前 | **サーバー: Windows VM** |
    | ワークロード | **Windows/Linux サーバー** |
    | 環境 | **Virtual Machines** |
    | オペレーティング システム | **Windows** |  
    | VM | **50** |
    | 仮想化 | **Hyper-V** |
    | コア | **8**|
    | RAM (GB) | **16** |
    | 最適化の方法 | **CPU** |
    | Windows Server 2008/2008 R2 | "**オフ**" |

3. **[+ サーバー ワークロードの追加]** を選択して、新しいサーバー ワークロード定義の行を作成します。 

    | 設定 | 値 |
    | -- | -- |
    | 名前 | **サーバー: Linux VM** |
    | ワークロード | **Windows/Linux サーバー** |
    | 環境 | **Virtual Machines** |
    | オペレーティング システム | **Linux** |  
    | VM | **50** |
    | 仮想化 | **VMware** |
    | コア | **8**|
    | RAM (GB) | **16** |
    | 最適化の方法 | **CPU** |
    | Windows Server 2008/2008 R2 | "**オフ**" |

4. **[ストレージ]** ウィンドウで、 **[記憶域の追加]** をクリックします。

    | 設定 | 値 |
    | -- | -- |
    | 名前 | **サーバー ストレージ** |
    | ストレージの種類 | **ローカル ディスク/SAN** |
    | ディスクの種類 | **HDD** |
    | 容量 | **60 TB** |  
    | Backup | **120 TB** |
    | アーカイブ | **0 TB** |

5. **[ネットワーク]** ウィンドウで、帯域幅を追加します。 

    | 設定 | 値 |
    | -- | -- |
    | アウトバウンド帯域幅 | 15 TB|

6. **[次へ]** をクリックします。

7. オプションを確認し、必要な調整を行います。 

    | 設定 | 値 |
    | -- | -- |
    | Currency | **ユーロ** |

8. **[次へ]** をクリックします。

# <a name="task-2-review-the-results-and-save-a-copy"></a>タスク 2:結果を確認し、コピーを保存する

このタスクでは、コスト削減の推奨事項を確認し、レポートをダウンロードします。 

1. Azure のコスト削減に関する推奨事項と視覚化を確認します。

    | 設定 | 値 |
    | -- | -- |
    | 期間| **3 年** |
    | リージョン | **北ヨーロッパ** |

2. 入力した情報を変更するには、ページの最下部にスクロールして **[戻る]** をクリックします。 

3. レポートの PDF コピーを保存または印刷するには、 **[ダウンロード]** をクリックします。

    ![Screenshot of the report pane of the tco calculator in Azure. The highlighted and completed input fields indicates how set the tco calculator timeframe to three years and the region to north europe. A graph shows the cost of on-premises infrastructure and workloads off-set against the reduced cost of using Azure.](../images/2001.png)

Congratulations! You have used the TCO Calculator to generate a cost comparison report for an on-premises environment.
