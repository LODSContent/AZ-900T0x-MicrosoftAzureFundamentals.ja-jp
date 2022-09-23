---
wts:
  title: 12 - Azure Key Vault の実装 (5 分)
  module: 'Module 04: Describe general security and network security features'
---
# <a name="12---implement-azure-key-vault-5-min"></a>12 - Azure Key Vault の実装 (5 分)

このチュートリアルでは、Azure Key コンテナーを作成してキー コンテナー内にパスワード シークレットを作成し、アプリケーションで使用するために安全に保存され集中管理されたパスワードを提供します。

# <a name="task-1-create-an-azure-key-vault"></a>タスク 1:Azure Key Vault を作成する 

1. [Azure portal](https://portal.azure.com) にサインインします。

2. **[すべてのサービス]** ブレードで、「**キー コンテナー**」と検索してそれを選択し、**[+追加]、[+新規]、[+作成]** のいずれかを選択します。

3. Configure the key vault (replace <bpt id="p1">**</bpt>xxxx<ept id="p1">**</ept> in the name of the key vault with letters and digits such that the name is globally unique). Leave the defaults for everything else.

    | 設定 | 値 | 
    | --- | --- |
    | サブスクリプション | **提供された既定値を使用する** |
    | Resource group | **新しいリソース グループの作成** |
    | キー コンテナー名 | **keyvaulttestxxx** |
    | Location | **米国東部** |
    | 価格レベル | **Standard** |
    
    **注** **xxxx** を置き換えて、一意の名前を見つけます。
4. **[確認と作成]** をクリックし、**[作成]** をクリックします。 

5. Once the new key vault is provisioned, click <bpt id="p1">**</bpt>Go to resource<ept id="p1">**</ept>. Or you can locate your new key vault by searching for it. 

6. Click on the key vault <bpt id="p1">**</bpt>Overview<ept id="p1">**</ept> tab and take note of the <bpt id="p2">**</bpt>Vault URI<ept id="p2">**</ept>. Applications that use your vault through the REST APIs will need this URI.

7. Take a moment to browse through some of the other key vault options. Under <bpt id="p1">**</bpt>Settings<ept id="p1">**</ept> review <bpt id="p2">**</bpt>Keys<ept id="p2">**</ept>, <bpt id="p3">**</bpt>Secrets<ept id="p3">**</ept>, <bpt id="p4">**</bpt>Certificates<ept id="p4">**</ept>, <bpt id="p5">**</bpt>Access Policies<ept id="p5">**</ept>, <bpt id="p6">**</bpt>Firewalls and virtual networks<ept id="p6">**</ept>.

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: Your Azure account is the only one authorized to perform operations on this new vault. You can modify this if you wish in the <bpt id="p1">**</bpt>Settings<ept id="p1">**</ept> and then the <bpt id="p2">**</bpt>Access policies<ept id="p2">**</ept> section.

# <a name="task-2-add-a-secret-to-the-key-vault"></a>タスク 2:Key Vault にシークレットを追加する
        
このタスクでは、キー コンテナーにパスワードを追加します。 

1. **[設定]** で **[シークレット]** を選択してから、**[+ 生成/インポート]** をクリックします。

2. Configure the secret. Leave the other values at their defaults. Notice you can set an activation and expiration date. Notice you can also disable the secret.

    | 設定 | 値 | 
    | --- | --- |
    | Upload options | **手動** |
    | Name | **ExamplePassword** |
    | 値 | **hVFkk96** |

3. **Create** をクリックしてください。

4. シークレットが正常に作成されたら、**[ExamplePassword]** をクリックし、状態が **[有効]** になっていることを確認します。

5. Select the secret you just created, note the the <bpt id="p1">**</bpt>Secret Identifier<ept id="p1">**</ept>. This is the url value that you can now use with applications. It provides a centrally managed and securely stored password. 

6. **[シークレット値の表示]** ボタンをクリックすると、前に指定したパスワードが表示されます。


キー コンテナーを構成します (キー コンテナー名の **xxxx** は、名前がグローバルに一意になる文字と数字に置き換えます)。

その他は既定値のままにします。
