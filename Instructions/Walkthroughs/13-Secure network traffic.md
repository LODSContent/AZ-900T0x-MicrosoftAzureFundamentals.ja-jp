---
wts:
  title: 13 - セキュリティ保護されたネットワーク トラフィック (10 分)
  module: 'Module 04: Describe general security and network security features'
---
# <a name="13---secure-network-traffic-10-min"></a>13 - セキュリティ保護されたネットワーク トラフィック (10 分)

このチュートリアルでは、ネットワーク セキュリティ グループを作成します。

# <a name="task-1-create-a-virtual-machine"></a>タスク 1:仮想マシンを作成する

このタスクでは、Windows Server 2019 Datacenter 仮想マシンを作成します。 

1. [Azure portal](https://portal.azure.com) にサインインします。

2. **[すべてのサービス]** ブレードで「**仮想マシン**」を検索して選択し、仮想マシンの **[+ 追加]、[+ 作成]、[+ 新規]** のいずれかをクリックします。

3. **[基本]** タブで、次の情報を入力します (その他の情報は既定値のままにします)。

    | 設定 | 値 |
    |  -- | -- |
    | サブスクリプション | **提供される既定値を使用する** |
    | Resource group | **新しいリソース グループの作成** |
    | 仮想マシン名 | **SimpleWinVM** |
    | リージョン | **(米国) 米国東部**|
    | Image | **Windows Server 2019 Datacenter Gen 2**|
    | サイズ | **Standard D2s v3**|
    | 管理者アカウントのユーザー名 | **azureuser** |
    | 管理者アカウントのパスワード | **Pa$$w0rd1234**|
    | 受信ポートの規則 | **なし**|

4. **[ネットワーク]** タブに切り替えて、次の設定を構成します。

    | 設定 | 値 |
    | -- | -- |
    | NIC ネットワーク セキュリティ グループ | **なし**|

5. **[管理]** タブに切り替え、 **[監視]** セクションで次の設定を選択します。

    | 設定 | 値 |
    | -- | -- |
    | ブート診断 | **無効化**|

6. その他の既定値はそのままにして、ページの下部にある **[確認および作成]** ボタンをクリックします。

7. 検証できたら、**[作成]** ボタンをクリックします。 仮想マシンのデプロイには約 5 分かかる場合があります。

8. 展開を監視します。 リソース グループと仮想マシンが作成されるまでに数分かかる場合があります。 

9. デプロイ ブレードまたは通知領域から、 **[リソースに移動]** をクリックします。 

10. **[SimpleWinVM]** 仮想マシンブレードで **[ネットワーク]** をクリックし、 **[受信ポート規則]** タブを確認します。仮想マシンのネットワーク インターフェイスまたはネットワーク インターフェイスが接続されているサブネットに、ネットワーク セキュリティ グループが関連付けられていないことを確認してください。

    **注**:ネットワーク インターフェイスの名前を特定します。 この名前は、次のタスクで必要になります。

# <a name="task-2-create-a-network-security-group"></a>タスク 2:ネットワーク セキュリティ グループを作成する

このタスクでは、ネットワーク セキュリティ グループを作成し、ネットワーク インターフェイスに関連付けます。 

1. **[すべてのサービス]** ブレードで、 **[ネットワーク セキュリティ グループ]** を検索して選択し、 **[+ 追加]、[+ 作成]、[+ 新規]** をクリックします。

2. **[ネットワークセキュリティグループの作成]** ブレードの **[基本]** タブで、次の設定を指定します。

    | 設定 | 値 |
    | -- | -- |
    | サブスクリプション | **既定のサブスクリプションを使用する** |
    | Resource group | **ドロップ ダウンから既定値を選択する** |
    | Name | **myNSGSecure** |
    | リージョン | **(米国) 米国東部**  |

3. **[確認と作成]** をクリックし、検証後、**[作成]** をクリックします。

4. NSG が作成されたら、 **[リソースに移動]** をクリックします。

5. **[設定]** の **[ネットワーク インターフェイス]** をクリックしてから、**[関連付け]** をクリックします。

6. 前のタスクで特定したネットワーク インターフェイスを選択します。 

# <a name="task-3-configure-an-inbound-security-port-rule-to-allow-rdp"></a>タスク 3:RDP を許可する受信セキュリティ ポートの規則を構成する

このタスクでは、受信セキュリティ ポートの規則を構成して、仮想マシンに RDP トラフィックを許可します。 

1. Azure portal で、**SimpleWinVM** 仮想マシンのブレードに移動します。 

2. **[概要]** ウィンドウで、 **[接続]** をクリックします。

3. RDP を選択し、実行中の RDP ファイルをダウンロードして、仮想マシンへの接続を試みます。 既定では、ネットワーク セキュリティ グループで RDP は許可されていません。 エラー ウィンドウを閉じます。 


    ![仮想マシン接続が失敗したことを示すエラー メッセージのスクリーンショット。](../images/1201.png)

4. 仮想マシンのブレードで **[設定]** セクションまでスクロールし、 **[ネットワーク]** をクリックして、ネットワーク セキュリティ グループ **[myNSGSecure (ネットワーク インターフェイスに接続: myVMNic)]** の受信規則で、仮想ネットワーク内のトラフィックとロードバランサー プローブを除くすべての受信トラフィックを拒否していることを確認します。

5. **[受信ポート規則]** タブで、 **[受信ポート規則の追加]** をクリックします。 選択したら、**[追加]** をクリックします。 

    | 設定 | 値 |
    | -- | -- |
    | source | **[任意]**|
    | Source port ranges | **\*** |
    | 到着地 | **[任意]** |
    | 宛先ポート範囲 | **3389** |
    | Protocol | **TCP** |
    | アクション | **許可** |
    | Priority | **300** |
    | Name | **AllowRDP** |

6. **[追加]** を選択し、ルールがプロビジョニングされるのを待ってから、**[接続]** に戻って仮想マシンへの RDP を再試行します。今回は成功するはずです。 ユーザーは "**azureuser**" で、パスワードは "**Pa$$w0rd1234**" です。

# <a name="task-4-configure-an-outbound-security-port-rule-to-deny-internet-access"></a>タスク 4:インターネット アクセスを拒否するように送信セキュリティ ポートの規則を構成する

このタスクでは、インターネット アクセスを拒否する NSG 送信ポート規則を作成し、規則が機能していることを確認するためにテストします。

1. 仮想マシンへの RDP セッションを続行します。 

2. コンピューターが起動したら、**Internet Explorer** ブラウザーを開きます。 

3. **https://www.bing.com** にアクセスできることを確認してから、Internet Explorer を閉じます。 IE の強化されたセキュリティ ポップアップを操作する必要があります。 

    **注**:送信インターネット アクセスを拒否するルールを構成します。 

4. Azure portal に戻り、**SimpleWinVM** 仮想マシンのブレードに戻ります。 

5. **[設定]** で **[ネットワーク]** をクリックし、 **[送信ポートの規則]** をクリックします。

6. **[インターネットへの送信を許可する]** という規則があることを確認します。 これは既定の規則であり、削除できません。 

7. ネットワークセキュリティグループ **[myNSGSecure (ネットワーク インターフェイスに接続: myVMNic)]** の右側にある **[出力ポート規則の追加]** をクリックし、より優先度の高い、インターネット トラフィックを拒否する新しい出力セキュリティ規則を構成します。 完了したら、 **[追加]** をクリックします。 

    | 設定 | 値 |
    | -- | -- |
    | source | **[任意]**|
    | Source port ranges | **\*** |
    | 到着地 | **サービス タグ** |
    | 宛先サービス タグ | **Internet** |
    | 宛先ポート範囲 | **\*** |
    | Protocol | **TCP** |
    | アクション | **Deny** |
    | 優先順位 | **4000** |
    | Name | **DenyInternet** |

8. **[追加]** をクリックして、RDP の VM に戻ります。 

9. **https://www.microsoft.com** にアクセスします。 ページは表示されません。 IE の強化されたセキュリティ ポップアップを操作することが必要になる場合があります。  

**注**:追加コストを回避するには、オプションでこのリソース グループを削除します。 リソース グループを検索し、リソース グループをクリックして、**[リソース グループの削除]** をクリックします。 リソース グループの名前を確認し、**[削除]** をクリックします。 **通知**を監視して、削除の進行状況を確認します。
