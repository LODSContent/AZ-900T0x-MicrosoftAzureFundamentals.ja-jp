---
wts:
  title: 17 - Azure Policy の作成 (10 分)
  module: 'Module 05: Describe identity, governance, privacy, and compliance features'
---
# <a name="17---create-an-azure-policy-10-min"></a>17 - Azure Policy の作成 (10 分)

このチュートリアルでは、Azure リソースのデプロイを特定の場所に制限する Azure Policy を作成します。

# <a name="task-1-create-a-policy-assignment"></a>タスク 1:ポリシー割り当てを作成する 

このタスクでは、許可された場所のポリシーを構成し、サブスクリプションに割り当てます。 

1. [Azure portal](https://portal.azure.com) にサインインします。

2. From the <bpt id="p1">**</bpt>All services<ept id="p1">**</ept> blade, search for and select <bpt id="p2">**</bpt>Policy<ept id="p2">**</ept>, under the <bpt id="p3">**</bpt>Authoring<ept id="p3">**</ept> section click <bpt id="p4">**</bpt>Definitions<ept id="p4">**</ept>.  Take a moment to review the list of built-in policy definitions. For example, in the <bpt id="p1">**</bpt>Category<ept id="p1">**</ept> drop-down select only <bpt id="p2">**</bpt>Compute<ept id="p2">**</ept>. Notice the <bpt id="p1">**</bpt>Allowed virtual machine size SKUs<ept id="p1">**</ept> definition enables you to specify a set of virtual machine SKUs that your organization can deploy.

3. Return to the <bpt id="p1">**</bpt>Policy<ept id="p1">**</ept> page, under the <bpt id="p2">**</bpt>Authoring<ept id="p2">**</ept> section click <bpt id="p3">**</bpt>Assignments<ept id="p3">**</ept>. An assignment is a policy that has been assigned to take place within a specific scope. For example, a definition could be assigned to the subscription scope. 

4. **[ポリシー - 割り当て]** ページの上部にある **[ポリシーの割り当て]** をクリックします。

5. **[ポリシーの割り当て]** ページで、既定のスコープを維持します。

      | 設定 | 値 | 
    | --- | --- |
    | スコープ| **選択された既定値を使用する**|
    | ポリシー定義 | 省略記号をクリックし、「**許可されている場所**」を検索して、**[選択]** をクリックする |
    | 割り当て名 | **許可されている場所** |
    
    ![フィールド値が入力され、[選択] ボタンが強調表示されている [スコープ] ペインのスクリーンショット。 ](../images/1402.png)
6. On the <bpt id="p1">**</bpt>Parameters<ept id="p1">**</ept> tab, select <bpt id="p2">**</bpt>Japan West<ept id="p2">**</ept>. Click <bpt id="p1">**</bpt>Review + create<ept id="p1">**</ept>, and then <bpt id="p2">**</bpt>Create<ept id="p2">**</ept>.

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: A scope determines what resources or grouping of resources the policy assignment applies to. In our case we could assign this policy to a specific resource group, however we chose to assign the policy at subscription level. Be aware that resources can be excluded based on the scope configuration. Exclusions are optional.

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: This <bpt id="p2">**</bpt>Allowed Locations<ept id="p2">**</ept> policy definition will specify a location into which all resources must be deployed. If a different location is chosen, deployment will not be allowed. For more information view the <bpt id="p1">[</bpt>Azure Policy Samples<ept id="p1">](https://docs.microsoft.com/en-us/azure/governance/policy/samples/index)</ept> page.

   ![さまざまなフィールドが強調表示され、[マネージド ディスクを使用していない VM の監査] オプションが選択されている [使用可能な定義] ペインのスクリーンショット。](../images/1403.png)

9. これで、**[許可されている場所]** ポリシーの割り当てが **[ポリシー - 割り当て]** ペインに一覧表示され、配置されました。指定したスコープ レベル (サブスクリプション レベル) でポリシーが適用されます。

# <a name="task-2-test-allowed-location-policy"></a>タスク 2:許可された場所のポリシーをテストする

このタスクでは、許可された場所のポリシーをテストします。 

1. Azure Portal の **[すべてのサービス]** ブレードで、 **[ストレージ アカウント]** を検索して選択し、 **[+ 作成]** をクリックします。

2. Configure the storage account (replace <bpt id="p1">**</bpt>xxxx<ept id="p1">**</ept> in the name of the storage account with letters and digits such that the name is globally unique). Leave the defaults for everything else. 

    | 設定 | 値 | 
    | --- | --- |
    | サブスクリプション | **提供された既定値を使用する** |
    | Resource group | **myRGPolicy** (新規作成) |
    | ストレージ アカウント名 | **storageaccountxxxx** |
    | 場所 | **(米国) 米国東部** |

3. **[Review + create]\(レビュー + 作成\)** をクリックし、 **[作成]** をクリックします。 

4. **[許可されている場所]** ポリシー名を含め、リソースがポリシーによって許可されなかったことを示す **[デプロイの失敗]** エラーが表示されます。

# <a name="task-3-delete-the-policy-assignment"></a>タスク 3:ポリシーの割り当てを削除する

このタスクでは、許可された場所のポリシーの割り当てを削除してテストします。 

ポリシーの割り当てを削除して、今後の作業がブロックされないようにします。

1. **[すべてのサービス]** ブレードで、「**ポリシー**」を検索して選択し、**[許可されている場所]** ポリシーをクリックします。

    **注**: **[ポリシー]** ブレードで、割り当てたさまざまなポリシーのコンプライアンス状態を表示することができます。

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: The Allowed location policy may show non-compliant resources. If so, these are resources created prior to the policy assignment.
 
2. **[許可されている場所]** をクリックします。[[許可されている場所] ポリシー コンプライアンス] ウィンドウが開きます。

3. **[すべてのサービス]** ブレードで、「**ポリシー**」を検索して選択し、**[作成]** セクションで **[定義]** をクリックします。

   ![[割り当ての削除] メニュー項目のスクリーンショット。](../images/1407.png)

4. 別のストレージ アカウントを作成して、ポリシーが無効になっていることを確認してください。

    **注**: **[許可されている場所]** ポリシーが役立つ一般的なシナリオには、次のようなものがあります。 
    - 組み込みのポリシー定義の一覧を確認します。 
    - *データ常駐とセキュリティ コンプライアンス*:データ常駐要件を設定し、顧客ごとまたは特定のワークロードごとにサブスクリプションを作成し、すべてのリソースを特定のデータセンターにデプロイしてデータとセキュリティのコンプライアンス要件を確保することを定義することもできます。

たとえば、**[カテゴリ]** ドロップダウンでは、**[計算]** のみを選択します。

**[許可されている仮想マシン サイズ SKU]** の定義を使用すると、自分の組織がデプロイできる仮想マシン SKU のセットを指定できます。
