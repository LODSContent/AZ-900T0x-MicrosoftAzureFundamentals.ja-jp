---
wts:
  title: 14 - RBAC を使用したアクセスの管理 (5 分)
  module: 'Module 05: Describe identity, governance, privacy, and compliance features'
---
# <a name="14---manage-access-with-rbac-5-min"></a>14 - RBAC を使用したアクセスの管理 (5 分)

このチュートリアルでは、リソースに権限のロールを割り当て、ログを表示します。

# <a name="task-1-view-and-assign-roles"></a>タスク 1:ロールを表示および割り当てます

このタスクでは、仮想マシンの共同作成者ロールを割り当てます。 

1. [Azure portal](https://portal.azure.com) にサインインします。

2. **[すべてのサービス]** ブレードで、「**リソース グループ**」を検索して選択し、**[+ 追加]、[+ 新規]、[+ 作成]** のいずれかをクリックします。

3. Create a new resource group. Click <bpt id="p1">**</bpt>Create<ept id="p1">**</ept> when you are finished. 

    | 設定 | 値 |
    | -- | -- |
    | サブスクリプション | **提供される既定値を使用する** |
    | Resource group | **myRGRBAC** |
    | リージョン | **(米国) 米国東部** |
   

4. **[確認および作成]** を選択し、**[作成]** をクリックします。

5. リソース グループ ページを **[最新の情報に更新]** して、新しく作成したリソース グループを表すエントリをクリックします。

6. Click on the <bpt id="p1">**</bpt>Access control (IAM)<ept id="p1">**</ept> blade, and then switch to the <bpt id="p2">**</bpt>Roles<ept id="p2">**</ept> tab. Scroll through the large number of roles definitions that are available. Use the Informational icons to get an idea of each role's permissions. Notice there is also information on the number of users and groups that are assigned to each role.
7. 
![image](https://user-images.githubusercontent.com/89808319/144266949-f19d91ab-31d6-4c8b-af36-c00035925cf0.png)

7. Switch to the <bpt id="p1">**</bpt>Role assignments<ept id="p1">**</ept> tab of the <bpt id="p2">**</bpt>myRGRBAC - Access control (IAM)<ept id="p2">**</ept> blade, click <bpt id="p3">**</bpt>+ Add<ept id="p3">**</ept> and then click <bpt id="p4">**</bpt>Add role assignment<ept id="p4">**</ept>. Search for the Virtual Machine Contributor role and select. Switch to the "Members" tab and Assign access to: User, group, or service principal. Then click + Select members and type in your name to the popup search function and hit 'select.' Then hit 'Review and Assign'

    
    ![image](https://user-images.githubusercontent.com/89808319/144266255-3a0f8574-9358-4c21-8f95-3503747e77c8.png)

 

    **注:**  仮想マシン共同作成者のロールでは仮想マシンを管理できますが、そのオペレーティング システムにアクセスしたり、接続先の仮想ネットワークやストレージ アカウントを管理したりすることはできません。

  

8. [ロールの割り当て] ページを **[更新]** し、仮想マシンの共同作成者として表示されていることを確認します。 

    **注**:共同制作者ロールに関連する権限すべてを有する所有者のロールをアカウントがすでに有しているため、この割り当てにより付加的な権限が付与される訳ではありません。

# <a name="task-2-monitor-role-assignments-and-remove-a-role"></a>タスク 2:ロールの割り当てを確認し、ロールを削除する

このタスクでは、アクティビティ ログを表示してロールの割り当てを確認し、ロールを削除します。 

1. [myRGRBAC リソース グループ] ブレードで、**[アクティビティ ログ]** をクリックします。

2. **[フィルターの追加]** をクリックして **[操作]** を選択し、**[ロールの割り当てを作成]** をクリックします。

    ![フィルターが構成された [アクティビティ ログ] ページのスクリーンショット。](../images/1503.png)

3. アクティビティ ログにロールの割り当てが表示されていることを確認します。 

    **注**:ロールの割り当てを削除する方法は分かりますか。

Congratulations! You created a resource group, assigned an access role to it and viewed activity logs. 

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click <bpt id="p1">**</bpt>Delete resource group<ept id="p1">**</ept>. Verify the name of the resource group and then click <bpt id="p1">**</bpt>Delete<ept id="p1">**</ept>. Monitor the <bpt id="p1">**</bpt>Notifications<ept id="p1">**</ept> to see how the delete is proceeding.

