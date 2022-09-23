---
wts:
  title: 04 - 仮想ネットワークの作成 (20 分)
  module: Module 02 - Core Azure Services (Workloads)
---
# <a name="04---create-a-virtual-network-20-min"></a>04 - 仮想ネットワークの作成 (20 分)

このチュートリアルでは、仮想ネットワークを作成し、その仮想ネットワークに 2 台の仮想マシンをデプロイして、仮想ネットワーク経由で一方の仮想マシンから他方の仮想マシンに ping を実行できるように構成します。

# <a name="task-1-create-a-virtual-network"></a>タスク 1: 仮想ネットワークを作成する 

このタスクでは、仮想ネットワークを作成します。 

注: ラボを開始する前に、[スタート] メニュー > [設定] > [ネットワークとインターネット] > [Locate Windows Firewall]\(Windows ファイアウォールの場所を特定する\) を開いて、仮想マシンのパブリック ファイアウォールとプライベート ファイアウォールの両方を無効にします

1. Azure portal (<a href="https://portal.azure.com" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://portal.azure.com</span></a>) にサインインします。

2. **[すべてのサービス]** ブレードで「**仮想ネットワーク**」を検索して選択し、**[+ 追加]、[+ 作成]、[+ 新規]** のいずれかをクリックします。 

3. **[基本]** タブで、次の情報を入力します (その他の情報は既定値のままにします)。

    | 設定 | 値 | 
    | --- | --- |
    | サブスクリプション | **提供される既定値のままにする** |
    | リソース グループ | **新しいリソース グループの作成** |
    | Name | **vnet1** |
    | リージョン | **(米国) 米国東部** |
    
   
4. Click the <bpt id="p1">**</bpt>Review + create<ept id="p1">**</ept> button. Ensure the validation passes. Then hit create to deploy the resource.


# <a name="task-2-create-two-virtual-machines"></a>タスク 2:2 つの仮想マシンを作成する

このタスクでは、仮想ネットワークに 2 つの仮想マシンを作成します。 

1. **[すべてのサービス]** ブレードで「**仮想マシン**」を検索し、ドロップ ダウンから **[+ 追加]、[+ 作成]、[+ 新規]** をクリックして **[+ 仮想マシン]** を選択します。 

2. **[基本]** タブで、次の情報を入力します (その他の情報は既定値のままにします)。

   | 設定 | 値 | 
   | --- | --- |
   | サブスクリプション | **提供された既定値を使用する** |
   | Resource group |  **ドロップ ダウンで既定値を選択する** |
   | 仮想マシン名 | **vm1**|
   | リージョン | **(米国) 米国東部** |
   | Image | **Windows Server 2019 Datacenter - Gen2** |
   | ユーザー名| **azureuser** |
   | Password| **Pa$$w0rd1234** |
   | パブリック受信ポート| **[選択したポートを許可する]** を選択します  |
   | 選択した受信ポート| **RDP (3389)** |
   

3. Select the <bpt id="p1">**</bpt>Networking<ept id="p1">**</ept> tab. Make sure the virtual machine is placed in the <bpt id="p2">**</bpt>vnet1<ept id="p2">**</ept> virtual network. Review the default settings, but do not make any other changes. 

4. Click <bpt id="p1">**</bpt>Review + create<ept id="p1">**</ept>. After the Validation passes, click <bpt id="p1">**</bpt>Create<ept id="p1">**</ept>. Deployment times can vary but it can generally take between three to six minutes to deploy.

5. デプロイを監視しながら、次の手順に進みます。 

6. Create a second virtual machine by repeating steps <bpt id="p1">**</bpt>2 to 4<ept id="p1">**</ept> above. Make sure you use a different virtual machine name, that the virtual machine is in the same virtual network, and is using a new public IP address:

    | 設定 | 値 |
    | --- | --- |
    | Resource group | **ドロップダウンで既定値を選択する (タスク 1 - 3 および タスク 2 - 2 と同じ)** |
    | 仮想マシン名 |  **vm2** |
    | 仮想ネットワーク | **vnet1** |
    | パブリック IP | **vm2-ip** |

7. 両方の仮想マシンがデプロイされ、ステータスが *[実行中]* と表示されるのを待ちます。

# <a name="task-3-test-the-connection"></a>タスク 3:接続をテストする 

In this task, we will try to test whether the virtual machines can communicate (ping) each other. If not we will install a rule to allow an ICMP connection. Usually ICMP connections are automatically blocked.

1. From the <bpt id="p1">**</bpt>All resources<ept id="p1">**</ept> blade, search for <bpt id="p2">**</bpt>vm1<ept id="p2">**</ept>, open its <bpt id="p3">**</bpt>Overview<ept id="p3">**</ept> blade, and make sure its <bpt id="p4">**</bpt>Status<ept id="p4">**</ept> is <bpt id="p5">**</bpt>Running<ept id="p5">**</ept>. You may need to <bpt id="p1">**</bpt>Refresh<ept id="p1">**</ept> the page.

2. **[概要]** ブレードで、 **[接続]** を選択して、ドロップ ダウンから **[RDP]** を選びます。

    **注**:次の手順では、Windows コンピューターから VM に接続する方法を説明しています。 

3. **[RDP に接続]** ブレードで、ポート 3389 経由で IP アドレスで接続する既定のオプションを保持し、**[RDP ファイルのダウンロード]** をクリックします。

4. ダウンロードした RDP ファイル (VM の左下にあります) を開き、プロンプトが表示されたら **[接続]** をクリックします。 

5. **[Windows セキュリティ]** ウィンドウで、ユーザー名「**azureuser**」とパスワード「**Pa$$w0rd1234**」を入力し、**[OK]** をクリックします。

6. You may receive a certificate warning during the sign-in process. Click <bpt id="p1">**</bpt>Yes<ept id="p1">**</ept> to create the connection and connect to your deployed VM. You should connect successfully. Close the Windows Server and Dashboard windows that pop up. You should see a Blue Windows background. You are now in your virtual machine.

7. 新しく作成された**両方**の仮想マシンを RDP 経由で接続し、[スタート] メニュー > [設定] > [ネットワークとインターネット] > [Locate Windows Firewall]\(Windows ファイアウォールの場所を特定する\) を開いて、パブリック ファイアウォールとプライベート ファイアウォールの両方を無効にします。

8. **[スタート]** ボタンをクリックして仮想マシンで PowerShell を開き、検索で「**PowerShell**」と入力し、**[Windows PowerShell]** を右クリックして**管理者として実行します**

9. PowerShell で、次のように入力して vm2 に ping を実行してみます。

   ```PowerShell
   ping vm2
   ```

 10. You should be successful. You have pinged VM2 from VM1.


<bpt id="p1">**</bpt>Congratulations!<ept id="p1">**</ept> You have configured and deployed two virtual machines in a virtual network, and then you were able to connect them.

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click <bpt id="p1">**</bpt>Delete resource group<ept id="p1">**</ept>. Verify the name of the resource group and then click <bpt id="p1">**</bpt>Delete<ept id="p1">**</ept>. Monitor the <bpt id="p1">**</bpt>Notifications<ept id="p1">**</ept> to see how the delete is proceeding.
