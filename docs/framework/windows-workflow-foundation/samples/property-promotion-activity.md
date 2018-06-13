---
title: プロパティ昇格アクティビティ
ms.date: 03/30/2017
ms.assetid: 802196b7-1159-4c05-b41b-d3bfdfcc88d9
ms.openlocfilehash: 46e74c8c479e545778db92e15de3cb8798dafa11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519926"
---
# <a name="property-promotion-activity"></a><span data-ttu-id="545b1-102">プロパティ昇格アクティビティ</span><span class="sxs-lookup"><span data-stu-id="545b1-102">Property Promotion Activity</span></span>
<span data-ttu-id="545b1-103">このサンプルでは、<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 昇格機能をワークフロー作成に直接統合するエンド ツー エンドのソリューションを示します。</span><span class="sxs-lookup"><span data-stu-id="545b1-103">This sample provides an end-to-end solution that integrates the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Promotion feature directly into the workflow authoring experience.</span></span> <span data-ttu-id="545b1-104">昇格機能の使用を単純化する構成要素、ワークフロー アクティビティ、およびワークフロー拡張機能のコレクションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="545b1-104">A collection of configuration elements, workflow activities, and workflow extensions that simplify the use of the Promotion feature are provided.</span></span> <span data-ttu-id="545b1-105">また、サンプルには、このコレクションの使用方法を示す簡単なワークフローが含まれています。</span><span class="sxs-lookup"><span data-stu-id="545b1-105">Additionally, the sample contains a simple workflow that demonstrates how to use this collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="545b1-106">サンプルは、演習目的で利用するためにのみ提供されています。</span><span class="sxs-lookup"><span data-stu-id="545b1-106">Samples are provided for educational purposes only.</span></span> <span data-ttu-id="545b1-107">サンプルを運用環境で使用することは想定されていないため、運用環境でのサンプルのテストは行われていません。</span><span class="sxs-lookup"><span data-stu-id="545b1-107">They are not intended for a production environment, and have not been tested in a production environment.</span></span> <span data-ttu-id="545b1-108">Microsoft では、これらのサンプルに関する製品サポート情報を提供していません。</span><span class="sxs-lookup"><span data-stu-id="545b1-108">Microsoft does not provide technical support for these samples.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="545b1-109">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="545b1-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="545b1-110">初期化された <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> データベース</span><span class="sxs-lookup"><span data-stu-id="545b1-110">An initialized <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> database</span></span>  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]  
  
## <a name="sample-projects"></a><span data-ttu-id="545b1-111">サンプル プロジェクト</span><span class="sxs-lookup"><span data-stu-id="545b1-111">Sample Projects</span></span>  
  
-   <span data-ttu-id="545b1-112">**PropertyPromotionActivity**プロジェクトには、昇格固有の構成要素、ワークフロー アクティビティ、およびワークフロー拡張機能に関連するファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="545b1-112">The **PropertyPromotionActivity** project contains files pertaining to the promotion-specific configuration elements, workflow activities, and workflow extensions.</span></span>  
  
-   <span data-ttu-id="545b1-113">**CounterServiceApplication**プロジェクトに使用したサンプル ワークフローが含まれています、 **SqlWorkflowInstanceStorePromotion**プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="545b1-113">The **CounterServiceApplication** project contains a sample workflow that uses the **SqlWorkflowInstanceStorePromotion** project.</span></span>  
  
-   <span data-ttu-id="545b1-114"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> データベースに対して実行される必要がある SQL スクリプト (PropertyPromotionActivitySQLSample.sql)。</span><span class="sxs-lookup"><span data-stu-id="545b1-114">A SQL script (PropertyPromotionActivitySQLSample.sql) that must be run against the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> database.</span></span>  
  
-   <span data-ttu-id="545b1-115">2 つの [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] プロジェクトをリンクするソリューション ファイル (`PropertyPromotionActivity.sln`)。</span><span class="sxs-lookup"><span data-stu-id="545b1-115">A solution file that links the two [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] projects (`PropertyPromotionActivity.sln`)</span></span>  
  
## <a name="to-set-up-and-run-the-sample"></a><span data-ttu-id="545b1-116">サンプルをセットアップおよび実行するには</span><span class="sxs-lookup"><span data-stu-id="545b1-116">To set up and run the sample</span></span>  
  
1.  <span data-ttu-id="545b1-117">ワークフロー永続化データベースを初期化します。</span><span class="sxs-lookup"><span data-stu-id="545b1-117">Initialize a workflow persistence database.</span></span>  
  
    1.  <span data-ttu-id="545b1-118">サンプル ディレクトリ (\WF\Basic\Persistence\PropertyPromotionActivity) に移動して、CreateInstanceStore.cmd を実行します。</span><span class="sxs-lookup"><span data-stu-id="545b1-118">Navigate to the sample directory (\WF\Basic\Persistence\PropertyPromotionActivity) and run CreateInstanceStore.cmd.</span></span>  
  
    2.  <span data-ttu-id="545b1-119">管理特権がない場合は、SQL Server ログインを作成します。</span><span class="sxs-lookup"><span data-stu-id="545b1-119">If Administrator privileges are not available, create a SQL Server login.</span></span> <span data-ttu-id="545b1-120">SQL Server Management Studio でに移動**セキュリティ**、**ログイン**です。</span><span class="sxs-lookup"><span data-stu-id="545b1-120">In SQL Server Management Studio, go to **Security**, **Logins**.</span></span> <span data-ttu-id="545b1-121">右クリック**ログイン**し、新しいログインを作成します。</span><span class="sxs-lookup"><span data-stu-id="545b1-121">Right-click **Logins** and create a new login.</span></span> <span data-ttu-id="545b1-122">開くことによって、自分の ACL ユーザーを SQL ロールに追加**データベース**、 **InstanceStore**、**セキュリティ**です。</span><span class="sxs-lookup"><span data-stu-id="545b1-122">Add your ACL user to the SQL role by opening **Databases**, **InstanceStore**, **Security**.</span></span> <span data-ttu-id="545b1-123">右クリック**ユーザー**選択**新しいユーザー**です。</span><span class="sxs-lookup"><span data-stu-id="545b1-123">Right-click **Users** and select **New user**.</span></span> <span data-ttu-id="545b1-124">設定、**ログイン名**上記で作成したユーザーにします。</span><span class="sxs-lookup"><span data-stu-id="545b1-124">Set the **Login name** to the user created above.</span></span> <span data-ttu-id="545b1-125">そのユーザーを、System.Activities.DurableInstancing.InstanceStoreUsers (およびその他) のデータベース ロールのメンバーシップに追加します。</span><span class="sxs-lookup"><span data-stu-id="545b1-125">Add the user to the Database role membership System.Activities.DurableInstancing.InstanceStoreUsers (and others).</span></span> <span data-ttu-id="545b1-126">ユーザーが既に存在している場合もあります (ユーザー dbo など)。</span><span class="sxs-lookup"><span data-stu-id="545b1-126">Note that the user might exist already (for example, user dbo).</span></span>  
  
2.  <span data-ttu-id="545b1-127">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で PropertyPromotionActivity.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="545b1-127">Open the PropertyPromotionActivity.sln solution file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="545b1-128">ローカルの SQL Server Express 以外のデータベースにインスタンス ストアを作成した場合は、データベース接続文字列を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="545b1-128">If you created the instance store in a database other than a local installation of SQL Server Express, then you must update the database connection string.</span></span> <span data-ttu-id="545b1-129">下の App.config ファイルを変更、 **CounterServiceApplication**の値を設定して、`connectionString`属性を`sqlWorkflowInstanceStorePromotion`ノードが初期化されている永続性データベースを指定するため、手順 1 でします。</span><span class="sxs-lookup"><span data-stu-id="545b1-129">Alter the App.config file under the **CounterServiceApplication** by setting the value of the `connectionString` attribute on the `sqlWorkflowInstanceStorePromotion` node so that it points to the persistence database that was initialized in step 1.</span></span>  
  
4.  <span data-ttu-id="545b1-130">ソリューションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="545b1-130">Build and run the solution.</span></span> <span data-ttu-id="545b1-131">これにより、カウンター WF サービスが開始され、ワークフロー インスタンスが自動的に開始されます。</span><span class="sxs-lookup"><span data-stu-id="545b1-131">This will start the Counter WF service and automatically start a workflow instance.</span></span>  
  
5.  <span data-ttu-id="545b1-132">永続化データベースの [dbo].[CounterService] ビューですべての行をすばやく選択します (このビューは、手順 1. の CreateInstanceStore.cmd の実行により追加されました)。</span><span class="sxs-lookup"><span data-stu-id="545b1-132">Quickly select all the rows in the [dbo].[CounterService] view in your persistence database (this view was added by running CreateInstanceStore.cmd in step 1).</span></span> <span data-ttu-id="545b1-133">以下と同様の結果セットが生成されます。</span><span class="sxs-lookup"><span data-stu-id="545b1-133">You will see a result set similar to the following:</span></span>  
  
    |<span data-ttu-id="545b1-134">InstanceId</span><span class="sxs-lookup"><span data-stu-id="545b1-134">InstanceId</span></span>|<span data-ttu-id="545b1-135">CounterValue</span><span class="sxs-lookup"><span data-stu-id="545b1-135">CounterValue</span></span>|<span data-ttu-id="545b1-136">CounterValueLastUpdated</span><span class="sxs-lookup"><span data-stu-id="545b1-136">CounterValueLastUpdated</span></span>|  
    |----------------|------------------|-----------------------------|  
    |<span data-ttu-id="545b1-137">2FA2C302-929E-4C0D-8C25-768A3DA20CE5</span><span class="sxs-lookup"><span data-stu-id="545b1-137">2FA2C302-929E-4C0D-8C25-768A3DA20CE5</span></span>|<span data-ttu-id="545b1-138">12</span><span class="sxs-lookup"><span data-stu-id="545b1-138">12</span></span>|<span data-ttu-id="545b1-139">2010-02-18 22:48:01.740</span><span class="sxs-lookup"><span data-stu-id="545b1-139">2010-02-18 22:48:01.740</span></span>|  
  
     <span data-ttu-id="545b1-140">ビューの更新を続行すると、CounterValue および CounterValueLastUpdated が 2 秒ごとに変更されます。</span><span class="sxs-lookup"><span data-stu-id="545b1-140">As you keep refreshing the view, you will notice that CounterValue and CounterValueLastUpdated change every two seconds.</span></span> <span data-ttu-id="545b1-141">これは、カウンターがカウンター自身を更新する間隔です。</span><span class="sxs-lookup"><span data-stu-id="545b1-141">This is the interval at which the counter updates itself.</span></span> <span data-ttu-id="545b1-142">CounterValue と CounterValueLastUpdated は、このワークフローの昇格されたプロパティを表します。</span><span class="sxs-lookup"><span data-stu-id="545b1-142">CounterValue and CounterValueLastUpdated represent promoted properties for this workflow.</span></span>  
  
## <a name="to-remove-the-sample"></a><span data-ttu-id="545b1-143">サンプルを削除するには</span><span class="sxs-lookup"><span data-stu-id="545b1-143">To remove the sample</span></span>  
  
-   <span data-ttu-id="545b1-144">サンプル ディレクトリ (\WF\Basic\Persistence\PropertyPromotionActivity) で RemoveInstanceStore.cmd を実行します。</span><span class="sxs-lookup"><span data-stu-id="545b1-144">Run RemoveInstanceStore.cmd in the sample directory (\WF\Basic\Persistence\PropertyPromotionActivity).</span></span>  
  
## <a name="understanding-this-sample"></a><span data-ttu-id="545b1-145">このサンプルについて</span><span class="sxs-lookup"><span data-stu-id="545b1-145">Understanding This Sample</span></span>  
 <span data-ttu-id="545b1-146">サンプルには、次の 2 つのプロジェクトと SQL ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="545b1-146">The sample contains two projects and an SQL file:</span></span>  
  
-   <span data-ttu-id="545b1-147">**CounterServiceApplication**単純なカウンター WF サービスをホストするコンソール アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="545b1-147">**CounterServiceApplication** is a console application that hosts a simple Counter WF service.</span></span> <span data-ttu-id="545b1-148">`Start` エンドポイントを通して一方向のメッセージを受信すると、ワークフローは 0 から 29 までをカウントし、2 秒ごとにカウンター変数がインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="545b1-148">Upon receiving a one-way message through the `Start` endpoint, the workflow counts from 0 to 29, incrementing a counter variable every two seconds.</span></span> <span data-ttu-id="545b1-149">カウンターがインクリメントされるたびに、ワークフローが永続化され、昇格されたプロパティは [dbo].[CounterService] ビューで更新されます。</span><span class="sxs-lookup"><span data-stu-id="545b1-149">After every counter increment, the workflow persists, and the promoted properties are updated in the [dbo].[CounterService] view.</span></span> <span data-ttu-id="545b1-150">コンソール アプリケーションが実行されると、WF サービスをホストし、メッセージを `Start` エンドポイントに送信して、カウンター WF インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="545b1-150">When the console application is run, it hosts the WF service and sends a message to the `Start` endpoint, creating a Counter WF instance.</span></span>  
  
-   <span data-ttu-id="545b1-151">**PropertyPromotionActivity**構成要素、ワークフロー アクティビティ、およびワークフロー拡張機能を含むクラス ライブラリを**CounterServiceApplication**を使用します。</span><span class="sxs-lookup"><span data-stu-id="545b1-151">**PropertyPromotionActivity** is a class library that contains the configuration elements, workflow activities, and workflow extensions that the **CounterServiceApplication** uses.</span></span>  
  
-   <span data-ttu-id="545b1-152">**PropertyPromotionActivitySQLSample.sql**を作成し、ビュー [dbo] を追加します [。CounterService]、データベースにします。</span><span class="sxs-lookup"><span data-stu-id="545b1-152">**PropertyPromotionActivitySQLSample.sql** creates and adds the view [dbo].[CounterService] to the database.</span></span>  
  
### <a name="counterserviceapplication"></a><span data-ttu-id="545b1-153">CounterServiceApplication</span><span class="sxs-lookup"><span data-stu-id="545b1-153">CounterServiceApplication</span></span>  
  
#### <a name="using-the-sqlworkflowinstancestorepromotion-configuration-element"></a><span data-ttu-id="545b1-154">SqlWorkflowInstanceStorePromotion 構成要素の使用</span><span class="sxs-lookup"><span data-stu-id="545b1-154">Using the SqlWorkflowInstanceStorePromotion Configuration Element</span></span>  
 <span data-ttu-id="545b1-155">`SqlWorkflowInstanceStorePromotion` 構成要素は `SqlWorkflowInstanceStore` 構成要素から継承されますが、`promotionSets` という追加の構成要素が追加されます。</span><span class="sxs-lookup"><span data-stu-id="545b1-155">The `SqlWorkflowInstanceStorePromotion` configuration element inherits from the `SqlWorkflowInstanceStore` configuration element, but adds an additional configuration element called `promotionSets`.</span></span> <span data-ttu-id="545b1-156">`promotionSets` 要素は、ユーザーが構成を通して昇格されたプロパティを指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="545b1-156">The `promotionSets` element enables the user to specify promoted properties through configuration.</span></span> <span data-ttu-id="545b1-157">これは、サンプルで使用される構成ファイルです。</span><span class="sxs-lookup"><span data-stu-id="545b1-157">This is the configuration file that is used by the sample:</span></span>  
  
```xml  
<sqlWorkflowInstanceStorePromotion connectionString ="Data Source=.;Initial Catalog=SqlWorkflowInstanceStoreTest;Integrated Security=True;">  
  <promotionSets>  
    <promotionSet name="CounterService">  
      <promotedValue propertyName="Count"/>  
      <promotedValue propertyName="LastIncrementedAt"/>  
    </promotionSet>  
  </promotionSets>  
</sqlWorkflowInstanceStorePromotion>  
```  
  
 <span data-ttu-id="545b1-158">[dbo].[CounterService] ビューの定義を確認します。</span><span class="sxs-lookup"><span data-stu-id="545b1-158">Examine the definition for the [dbo].[CounterService] view.</span></span>  
  
```sql  
create view [dbo].[CounterService] as  
      select [InstanceId],  
 [Value1] as [CounterValue],  
 [Value2] as [CounterValueLastUpdated]  
      from [System.Activities.DurableInstancing].[InstancePromotedProperties]  
      where [PromotionName] = 'CounterService'  
go  
```  
  
 <span data-ttu-id="545b1-159">ワークフロー インスタンスが永続化されると、構成で定義された各 `InstancePromotedProperties` の `PromotionSet` ビューに行が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="545b1-159">When a workflow instance persists, a row is inserted into the `InstancePromotedProperties` view for each `PromotionSet` defined in the configuration.</span></span> <span data-ttu-id="545b1-160">この行には、`PromotionSet` のすべての昇格されたプロパティが含まれます (列ごとに 1 つの昇格されたプロパティ)。</span><span class="sxs-lookup"><span data-stu-id="545b1-160">This row contains all the promoted properties of the `PromotionSet` (one promoted property per column).</span></span> <span data-ttu-id="545b1-161">この `PromotionSet` は、`InstanceId, PromotionName` のタプルによってキー指定されます。</span><span class="sxs-lookup"><span data-stu-id="545b1-161">This `PromotionSet` is keyed by the tuple: `InstanceId, PromotionName`.</span></span> <span data-ttu-id="545b1-162">このサンプルには、名前属性が `PromotionSet` である構成で定義されている 1 つの `CounterService` があります。</span><span class="sxs-lookup"><span data-stu-id="545b1-162">In this sample, we have one `PromotionSet` defined in configuration whose name attribute is `CounterService`.</span></span> <span data-ttu-id="545b1-163">`PromotionName` 列の値が `PromotionSet` 要素の名前属性と等しいことがわかります。</span><span class="sxs-lookup"><span data-stu-id="545b1-163">Note how the `PromotionName` column value is equal to the name attribute of the `PromotionSet` element.</span></span>  
  
 <span data-ttu-id="545b1-164">`promotedValue` 要素の順序は、`InstancePromotedProperties` ビューの昇格されたプロパティの位置と相関しています。</span><span class="sxs-lookup"><span data-stu-id="545b1-164">The order of the `promotedValue` elements correlates with the placement of the promoted properties in the `InstancePromotedProperties` view.</span></span> <span data-ttu-id="545b1-165">`Count` は最初の `promotedValue` 要素です。</span><span class="sxs-lookup"><span data-stu-id="545b1-165">`Count` is the first `promotedValue` element.</span></span> <span data-ttu-id="545b1-166">その結果、`Value1` ビューの `InstancePromotedProperties` 列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="545b1-166">As a result, it is mapped to the `Value1` column in the `InstancePromotedProperties` view.</span></span> <span data-ttu-id="545b1-167">`LastIncrementedAt` は 2 番目の `promotedValue` 要素です。</span><span class="sxs-lookup"><span data-stu-id="545b1-167">`LastIncrementedAt` is the second `promotedValue` element.</span></span> <span data-ttu-id="545b1-168">その結果、`Value2` ビューの `InstancePromotedProperties` 列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="545b1-168">As a result, it is mapped to the `Value2` column in the `InstancePromotedProperties` view.</span></span>  
  
#### <a name="using-the-promotevalue-activity"></a><span data-ttu-id="545b1-169">PromoteValue アクティビティの使用</span><span class="sxs-lookup"><span data-stu-id="545b1-169">Using the PromoteValue Activity</span></span>  
 <span data-ttu-id="545b1-170">Windows Workflow Foundation Designer で CounterService.xamlx ファイルを調べます。</span><span class="sxs-lookup"><span data-stu-id="545b1-170">Examine the CounterService.xamlx file in the Windows Workflow Foundation Designer.</span></span> <span data-ttu-id="545b1-171">WF の定義には、`PromoteValue<DateTime>` および `PromoteValue<Int32>` の 2 つの特別なアクティビティがあります。</span><span class="sxs-lookup"><span data-stu-id="545b1-171">Notice that there are two special activities in the WF definition: `PromoteValue<DateTime>` and `PromoteValue<Int32>`.</span></span>  
  
 <span data-ttu-id="545b1-172">`PromoteValue<Int32>` アクティビティには、`Name` として定義されているその `Count` メンバーがあります。</span><span class="sxs-lookup"><span data-stu-id="545b1-172">The `PromoteValue<Int32>` activity has its `Name` member defined as `Count`.</span></span> <span data-ttu-id="545b1-173">これは、構成の最初の `promotedValue` 要素と一致し、`Value` ワークフロー変数として定義されているその `Counter` があります。</span><span class="sxs-lookup"><span data-stu-id="545b1-173">This matches with the first `promotedValue` element in the configuration, and has its `Value` defined as the `Counter` workflow variable.</span></span> <span data-ttu-id="545b1-174">ワークフローが永続化されると、`Counter` ワークフロー変数は昇格されたプロパティとして `Value1` ビューの `InstancePromotedProperties` 列に保存されます。</span><span class="sxs-lookup"><span data-stu-id="545b1-174">When the workflow persists, the `Counter` workflow variable is persisted as a promoted property into the `Value1` column of the `InstancePromotedProperties` view.</span></span>  
  
 <span data-ttu-id="545b1-175">`PromoteValue<DateTime>` アクティビティには、`Name` として定義されているその `LastIncrementedAt` メンバーがあります。</span><span class="sxs-lookup"><span data-stu-id="545b1-175">The `PromoteValue<DateTime>` activity has its `Name` member defined as `LastIncrementedAt`.</span></span> <span data-ttu-id="545b1-176">これは、構成の 2 番目の `promotedValue` 要素と一致し、`Value` ワークフロー変数として定義されているその `TimeLastIncremented` があります。</span><span class="sxs-lookup"><span data-stu-id="545b1-176">This matches with the second `promotedValue` element in the configuration, and has its `Value` defined as the `TimeLastIncremented` workflow variable.</span></span> <span data-ttu-id="545b1-177">これは、ワークフローが永続化されると、`TimeLastIncremented` ワークフロー変数の値が昇格されたプロパティとして `Value2` ビューの  `InstancePromotedProperties` 列に保存されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="545b1-177">This means that when the workflow persists, the value for the `TimeLastIncremented` workflow variable will be persisted as a promoted property into the `Value2` column of the `InstancePromotedProperties` view.</span></span>  
  
 <span data-ttu-id="545b1-178">`PromotedValue` アクティビティには、`ClearExistingPromotedData` というブール型のメンバーもあります。</span><span class="sxs-lookup"><span data-stu-id="545b1-178">Note that the `PromotedValue` activity also has a Boolean member called `ClearExistingPromotedData`.</span></span> <span data-ttu-id="545b1-179">このメンバーを `true` に設定すると、ワークフローのその時点までのすべての昇格されたプロパティ値が消去されます。</span><span class="sxs-lookup"><span data-stu-id="545b1-179">When this member is set to `true`, this clears all the promoted property values up to that point in the workflow.</span></span> <span data-ttu-id="545b1-180">たとえば、Sequence アクティビティが次のように定義されているとします。</span><span class="sxs-lookup"><span data-stu-id="545b1-180">For example, if a Sequence activity is defined as follows:</span></span>  
  
1.  <span data-ttu-id="545b1-181">PromoteValue {名前 =「カウント」、値 3 を =}</span><span class="sxs-lookup"><span data-stu-id="545b1-181">PromoteValue { Name = "Count", Value = 3}</span></span>  
  
2.  <span data-ttu-id="545b1-182">PromoteValue {名前 = 値"LastIncrementedAt"1-1-2000 の =}</span><span class="sxs-lookup"><span data-stu-id="545b1-182">PromoteValue {Name = "LastIncrementedAt", Value = 1-1-2000 }</span></span>  
  
3.  <span data-ttu-id="545b1-183">永続化</span><span class="sxs-lookup"><span data-stu-id="545b1-183">Persist</span></span>  
  
4.  <span data-ttu-id="545b1-184">PromoteValue {名前「カウント」、値 = 4、ClearExistingPromotedData を = = true}</span><span class="sxs-lookup"><span data-stu-id="545b1-184">PromoteValue {Name = "Count", Value = 4, ClearExistingPromotedData = true}</span></span>  
  
5.  <span data-ttu-id="545b1-185">永続化</span><span class="sxs-lookup"><span data-stu-id="545b1-185">Persist</span></span>  
  
 <span data-ttu-id="545b1-186">2 番目の永続化では、`Count` の昇格された値は 4 になります。</span><span class="sxs-lookup"><span data-stu-id="545b1-186">On the second persist, the promoted value for `Count` will be 4.</span></span> <span data-ttu-id="545b1-187">ただし、昇格された値の`LastIncrementedAt`なります`NULL`です。</span><span class="sxs-lookup"><span data-stu-id="545b1-187">However, the promoted value for `LastIncrementedAt` will be `NULL`.</span></span> <span data-ttu-id="545b1-188">手順 4. で `ClearExistingPromotedData` を `true` に設定しなかった場合は、2 番目の永続化の後、Count の昇格された値は 4 になります。</span><span class="sxs-lookup"><span data-stu-id="545b1-188">If `ClearExistingPromotedData` was not set to `true` for step 4, then after the second persist, the promoted value for Count would be 4.</span></span> <span data-ttu-id="545b1-189">その結果、`LastIncrementedAt` の昇格された値は 1-1-2000 のままです。</span><span class="sxs-lookup"><span data-stu-id="545b1-189">As a result, the promoted value for `LastIncrementedAt` would still be 1-1-2000.</span></span>  
  
### <a name="propertypromotionactivity"></a><span data-ttu-id="545b1-190">PropertyPromotionActivity</span><span class="sxs-lookup"><span data-stu-id="545b1-190">PropertyPromotionActivity</span></span>  
 <span data-ttu-id="545b1-191">このクラス ライブラリには、<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 昇格機能の使用を単純化する次のパブリック クラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="545b1-191">This class library contains the following public classes to simplify use of the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Promotion feature.</span></span>  
  
#### <a name="promotevalue-class"></a><span data-ttu-id="545b1-192">PromoteValue クラス</span><span class="sxs-lookup"><span data-stu-id="545b1-192">PromoteValue Class</span></span>  
 <span data-ttu-id="545b1-193">このクラスは 1 つのプロパティを昇格します。</span><span class="sxs-lookup"><span data-stu-id="545b1-193">This class promotes one property.</span></span> <span data-ttu-id="545b1-194">昇格されたプロパティの名前は、構成の `promotedValue` 要素の名前属性と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="545b1-194">The name of the promoted property should match a name attribute of a `promotedValue` element in the configuration.</span></span> <span data-ttu-id="545b1-195">このアクティビティは、ワークフロー デザイナーで使用できます。</span><span class="sxs-lookup"><span data-stu-id="545b1-195">This activity can be used in the Workflow Designer.</span></span> <span data-ttu-id="545b1-196">使用例については、「CounterServiceApplication」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="545b1-196">See the CounterServiceApplication for an example usage.</span></span>  
  
```csharp  
public class PromoteValue<T> : CodeActivity  
{  
    public PromoteValue()  
    {  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public string Name { get; set; }  
    public InArgument<T> Value { get; set; }  
}  
```  
  
 <span data-ttu-id="545b1-197">ClearExistingPromotedData (Bool)</span><span class="sxs-lookup"><span data-stu-id="545b1-197">ClearExistingPromotedData (Bool)</span></span>  
 <span data-ttu-id="545b1-198">このアクティビティの前に昇格されたすべての値を消去します。</span><span class="sxs-lookup"><span data-stu-id="545b1-198">Clears all values that were promoted before this activity.</span></span>  
  
 <span data-ttu-id="545b1-199">Name (string)</span><span class="sxs-lookup"><span data-stu-id="545b1-199">Name (string)</span></span>  
 <span data-ttu-id="545b1-200">このプロパティを表す名前。</span><span class="sxs-lookup"><span data-stu-id="545b1-200">The name that represents this property.</span></span> <span data-ttu-id="545b1-201">これはの name 属性と一致する必要があります、 \<promotedValue > 構成内の要素。</span><span class="sxs-lookup"><span data-stu-id="545b1-201">This should match the name attribute of a \<promotedValue> element in the configuration.</span></span>  
  
 <span data-ttu-id="545b1-202">値 (InArgument\<T >)</span><span class="sxs-lookup"><span data-stu-id="545b1-202">Value (InArgument\<T>)</span></span>  
 <span data-ttu-id="545b1-203">列に格納する変数/値。</span><span class="sxs-lookup"><span data-stu-id="545b1-203">The variable / value that you want to store in the column.</span></span>  
  
#### <a name="promotevalues-class"></a><span data-ttu-id="545b1-204">PromoteValues クラス</span><span class="sxs-lookup"><span data-stu-id="545b1-204">PromoteValues Class</span></span>  
 <span data-ttu-id="545b1-205">複数のプロパティを昇格します。</span><span class="sxs-lookup"><span data-stu-id="545b1-205">Promotes multiple properties.</span></span> <span data-ttu-id="545b1-206">昇格されたプロパティの名前は、構成の `promotedValue` 要素のすべての名前属性と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="545b1-206">The names of the promoted properties should match all name attributes in the `promotedValue` elements in the configuration.</span></span> <span data-ttu-id="545b1-207">使用方法は、`PromoteValue` アクティビティと似ていますが、複数のプロパティを同時に昇格できる点が異なります。</span><span class="sxs-lookup"><span data-stu-id="545b1-207">Usage is similar to the `PromoteValue` activity, except for the fact that multiple properties can be promoted at the same time.</span></span> <span data-ttu-id="545b1-208">このアクティビティは、ワークフロー デザイナーでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="545b1-208">This activity cannot be used in the Workflow Designer.</span></span>  
  
```  
public class PromoteValues : CodeActivity  
{  
    public PromoteValues()  
    {  
        this.ValuesToPromote = new Dictionary<string, InArgument>();  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public IDictionary<string, InArgument> ValuesToPromote { get; set; }  
}  
```  
  
#### <a name="sqlworkflowinstancestorepromotionbehavior"></a><span data-ttu-id="545b1-209">SqlWorkflowInstanceStorePromotionBehavior</span><span class="sxs-lookup"><span data-stu-id="545b1-209">SqlWorkflowInstanceStorePromotionBehavior</span></span>  
 <span data-ttu-id="545b1-210">`SqlWorkflowInstanceStoreBehavior` から派生します。</span><span class="sxs-lookup"><span data-stu-id="545b1-210">Derives from `SqlWorkflowInstanceStoreBehavior`.</span></span> <span data-ttu-id="545b1-211">この派生クラスは、カスタムの永続化参加要素 (このライブラリの一部でもあります) をワークフロー拡張機能として追加します。</span><span class="sxs-lookup"><span data-stu-id="545b1-211">This derived class adds a custom persistence participant (also a part of this library) as a workflow extension.</span></span> <span data-ttu-id="545b1-212">前の 2 つのワークフロー アクティビティの実装は、このカスタムの永続化参加要素に依存しています。</span><span class="sxs-lookup"><span data-stu-id="545b1-212">The implementation of the previous two workflow activities relies on this custom persistence participant.</span></span>  
  
```  
public class SqlWorkflowInstanceStorePromotionBehavior :  
             SqlWorkflowInstanceStoreBehavior, IServiceBehavior  
{  
        public void Promote(string name, IEnumerable<string> promoteAsSqlVariant,  
                            IEnumerable<string> promoteAsBinary)  
  
}  
```  
  
 <span data-ttu-id="545b1-213">このクラス ライブラリには、`ConfigurationElement` の `SqlWorkflowInstanceStorePromotionElement` 実装と前の昇格アクティビティで使用されたカスタムの永続化参加要素も含まれています。</span><span class="sxs-lookup"><span data-stu-id="545b1-213">This class library also contains the `ConfigurationElement` implementation for the `SqlWorkflowInstanceStorePromotionElement` and a custom persistence participant used by the previous promotion activities.</span></span>  
  
### <a name="propertypromotionactivitysqlsample"></a><span data-ttu-id="545b1-214">PropertyPromotionActivitySQLSample</span><span class="sxs-lookup"><span data-stu-id="545b1-214">PropertyPromotionActivitySQLSample</span></span>  
 <span data-ttu-id="545b1-215">この SQL ファイルでは、CounterService 昇格セットを持つすべてのインスタンスをクエリするために `[dbo].[CounterService]` ビューのほかに `[InstancePromotedProperties]` ビューも作成されます。</span><span class="sxs-lookup"><span data-stu-id="545b1-215">This SQL file creates a `[dbo].[CounterService]` view in addition to the `[InstancePromotedProperties]` view for querying all instances that have a CounterService Promotion set.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="545b1-216">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="545b1-216">The samples may already be installed on your computer.</span></span> <span data-ttu-id="545b1-217">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="545b1-217">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="545b1-218">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="545b1-218">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="545b1-219">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="545b1-219">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\PropertyPromotionActivity`  
  
## <a name="see-also"></a><span data-ttu-id="545b1-220">関連項目</span><span class="sxs-lookup"><span data-stu-id="545b1-220">See Also</span></span>  
 [<span data-ttu-id="545b1-221">AppFabric ホスティングと永続性のサンプル</span><span class="sxs-lookup"><span data-stu-id="545b1-221">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
