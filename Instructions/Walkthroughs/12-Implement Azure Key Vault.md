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

3. キー コンテナーを構成します (キー コンテナー名の **xxxx** は、名前がグローバルに一意になる文字と数字に置き換えます)。 その他は既定値のままにします。

    | 設定 | 値 | 
    | --- | --- |
    | サブスクリプション | **提供された既定値を使用する** |
    | Resource group | **新しいリソース グループの作成** |
    | キー コンテナー名 | **keyvaulttestxxx** |
    | Location | **米国東部** |
    | 価格レベル | **Standard** |
    
    **注** **xxxx** を置き換えて、一意の名前を見つけます。
4. **[確認と作成]** をクリックし、**[作成]** をクリックします。 

5. 新しいキー コンテナーをプロビジョニングしたら、**[リソースに移動]** をクリックします。 新しいキー コンテナーを検索して見つけることもできます。 

6. キー コンテナーの **[概要]** タブをクリックし、**Vault URI** を書き留めます。 REST API を介してコンテナーを使用するアプリケーションには、この URI が必要になります。

7. その他のキー コンテナー オプションの一部を参照します。 **[設定]** で、**[キー]**、**[シークレット]**、**[証明書]**、**[アクセス ポリシー]**、**[ファイアウォールと仮想ネットワーク]** を確認します。

    **注**:Azure アカウントは、この新しい コンテナーで操作を実行できる唯一のアカウントです。 **[設定]** セクションと **[アクセス ポリシー]** セクションで必要に応じて変更できます。

# <a name="task-2-add-a-secret-to-the-key-vault"></a>タスク 2:Key Vault にシークレットを追加する
        
このタスクでは、キー コンテナーにパスワードを追加します。 

1. **[設定]** で **[シークレット]** を選択してから、**[+ 生成/インポート]** をクリックします。

2. シークレットを構成します。 その他の値はデフォルトのままにします。 ライセンス認証と有効期限を設定できることを確認してください。 シークレットを無効にすることもできます。

    | 設定 | 値 | 
    | --- | --- |
    | Upload options | **手動** |
    | Name | **ExamplePassword** |
    | 値 | **hVFkk96** |

3. **Create** をクリックしてください。

4. シークレットが正常に作成されたら、**[ExamplePassword]** をクリックし、状態が **[有効]** になっていることを確認します。

5. 作成したシークレットを選択し、**シークレット識別子**をメモします。 これは、アプリケーションで使用できる URL 値です。 一元管理され、安全に保存されたパスワードを提供します。 

6. **[シークレット値の表示]** ボタンをクリックすると、前に指定したパスワードが表示されます。


おめでとうございます! Azure Key コンテナーを作成し、キー コンテナー内にパスワード シークレットを作成し、アプリケーションで使用するための安全に保存された集中管理パスワードを提供します。

**注**:追加コストを回避するには、オプションでこのリソース グループを削除します。 リソース グループを検索し、リソース グループをクリックして、**[リソース グループの削除]** をクリックします。 リソース グループの名前を確認し、**[削除]** をクリックします。 **通知**を監視して、削除の進行状況を確認します。
