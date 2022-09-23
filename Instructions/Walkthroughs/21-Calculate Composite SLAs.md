---
wts:
  title: 21 - 複合 SLA の計算 (5分)
  module: 'Module 06: Describe Azure cost management and service level agreements'
---
# <a name="21---calculate-composite-slas-5-min"></a>21 - 複合 SLA の計算 (5分)

このチュートリアルでは、Azure サービスの可用性 SLA を決定し、アプリケーション複合 SLA ベースの推定可用性を計算します。

Our example application consists of these Azure services. We will not go in to deep architectural configuration and considerations, the intention here is to give an high level example.

+ **App Services**:アプリケーションをホストします。
+ **Azure AD B2C**:ユーザー ログインを認証し、プロファイルを管理します。
+ **Application Gateway**:アプリケーション アクセスやスケーリングを管理します。 
+ **Azure SQL Database**:アプリケーション データを格納します。 

# <a name="task-1-determine-the-sla-uptime-percentage-values-for-our-application"></a>タスク 1:アプリケーションの SLA アップタイムのパーセンテージ値を決定します。

1. ブラウザーで、[[Azure サービスの SLA サマリー]](https://azure.microsoft.com/en-us/support/legal/sla/summary/) ページに移動します。

2. Locate the <bpt id="p1">**</bpt>App Service<ept id="p1">**</ept> SLA uptime value, <bpt id="p2">**</bpt>99.95%<ept id="p2">**</ept>. Click <bpt id="p1">**</bpt>View full details<ept id="p1">**</ept>, and then expand <bpt id="p2">**</bpt>SLA details<ept id="p2">**</ept>. Notice the <bpt id="p1">**</bpt>Monthly uptime percentages<ept id="p1">**</ept> and <bpt id="p2">**</bpt>Service Credits<ept id="p2">**</ept>.

3. SLA Web ページに戻り、 **[Azure Active Directory B2C]** サービスを見つけて、SLA アップタイムの値 **[99.9%]** を確認します。 

4. **Application Gateway** の SLA アップタイム値 **99.95%** を確認します。 

5. The Azure SQL database uses Premium tiers but is not configured for Zone Redundant Deployments. Locate the <bpt id="p1">**</bpt>Azure SQL Database<ept id="p1">**</ept> SLA uptime value, <bpt id="p2">**</bpt>99.99%<ept id="p2">**</ept>. 

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: There are different uptime values for different configurations and deployments of Azure SQL Database. It is important you are clear on your required uptime values, when planning and costing your deployment and configuration. Small changes in uptime can have impact on service costs as well as potentially increase complexity in configuration. Some other services that may be of interest on the Azure SLA summary web page would include <bpt id="p1">**</bpt>Virtual Machines<ept id="p1">**</ept>, <bpt id="p2">**</bpt>Storage Accounts<ept id="p2">**</ept> and <bpt id="p3">**</bpt>Cosmos DB<ept id="p3">**</ept>.

# <a name="task-2-calculate-the-application-composite-sla-percentage-uptime"></a>タスク 2:アプリケーションの複合 SLA のアップタイム率を計算する

1. このサンプル アプリケーションは、次の Azure サービスで構成されています。

    **アプリ サービスのアップタイム率** X **Azure AD B2C のアップタイム率** X  **Azure Application Gateway のアップタイム率** X **Azure SQL Database のアップタイム率** = **合計アップタイム率**

    パーセントで表すと次のとおりです。

    **99.95%** X **99.9%** X **99.95%** X **99.99%**  = **99.79%**

    これは、現在のサービスおよびアーキテクチャを使用したアプリケーションの SAL ベースの推定可用性です。

ここでは、高レベルの例を提供することとし、アーキテクチャーの詳細な構成や考慮事項については割愛します。
