---
title: "&lt;コマンド パラメーター&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: efd4f37adb19940e81109924c3ec313d71bf6e7f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltcommonparametersgt"></a><span data-ttu-id="2cdde-102">&lt;コマンド パラメーター&gt;</span><span class="sxs-lookup"><span data-stu-id="2cdde-102">&lt;commonParameters&gt;</span></span>
<span data-ttu-id="2cdde-103">複数のサービスでグローバルに使用されるパラメーターのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="2cdde-103">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="2cdde-104">このコレクションには通常、永続性サービスによって共有されるデータベース接続文字列が格納されます。</span><span class="sxs-lookup"><span data-stu-id="2cdde-104">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="2cdde-105">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="2cdde-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="2cdde-106">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="2cdde-106">\<behaviors></span></span>  
<span data-ttu-id="2cdde-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="2cdde-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="2cdde-108">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="2cdde-108">\<behavior></span></span>  
<span data-ttu-id="2cdde-109">\<workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="2cdde-109">\<workflowRuntime></span></span>  
<span data-ttu-id="2cdde-110">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="2cdde-110">\<commonParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cdde-111">構文</span><span class="sxs-lookup"><span data-stu-id="2cdde-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>  
   <commonParameters>  
      <add name="String" value="String" />  
   </commonParameters>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2cdde-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2cdde-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2cdde-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2cdde-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2cdde-114">属性</span><span class="sxs-lookup"><span data-stu-id="2cdde-114">Attributes</span></span>  
 <span data-ttu-id="2cdde-115">なし。</span><span class="sxs-lookup"><span data-stu-id="2cdde-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2cdde-116">子要素</span><span class="sxs-lookup"><span data-stu-id="2cdde-116">Child Elements</span></span>  
  
|<span data-ttu-id="2cdde-117">要素</span><span class="sxs-lookup"><span data-stu-id="2cdde-117">Element</span></span>|<span data-ttu-id="2cdde-118">説明</span><span class="sxs-lookup"><span data-stu-id="2cdde-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2cdde-119">\<add></span><span class="sxs-lookup"><span data-stu-id="2cdde-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)|<span data-ttu-id="2cdde-120">サービスによって使用される共通パラメーターの名前と値のペアをコレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="2cdde-120">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2cdde-121">親要素</span><span class="sxs-lookup"><span data-stu-id="2cdde-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2cdde-122">要素</span><span class="sxs-lookup"><span data-stu-id="2cdde-122">Element</span></span>|<span data-ttu-id="2cdde-123">説明</span><span class="sxs-lookup"><span data-stu-id="2cdde-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2cdde-124">\<workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="2cdde-124">\<workflowRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|<span data-ttu-id="2cdde-125">ワークフロー ベースの <xref:System.Workflow.Runtime.WorkflowRuntime> サービスをホストする [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] のインスタンスの設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="2cdde-125">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cdde-126">コメント</span><span class="sxs-lookup"><span data-stu-id="2cdde-126">Remarks</span></span>  
 <span data-ttu-id="2cdde-127">最初の要素 `<commonParameters>` は、複数のサービスでグローバルに使用されるパラメーターを定義します (たとえば `ConnectionString` を使用する場合の <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>)。</span><span class="sxs-lookup"><span data-stu-id="2cdde-127">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2cdde-128">SQL 追跡サービスでは、`ConnectionString` セクションに `<commonParameters>` 値を指定しても、その値が常に使用されるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="2cdde-128">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="2cdde-129">`StateMachineWorkflowInstance.StateHistory` プロパティの取得のように、操作によっては失敗する場合があります。</span><span class="sxs-lookup"><span data-stu-id="2cdde-129">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="2cdde-130">これを回避するには、次の例に示すように、追跡プロバイダーの構成セクションで `ConnectionString` 属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="2cdde-130">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
 <span data-ttu-id="2cdde-131"><xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> や <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> など、作業バッチを永続的ストアにコミットするサービスでは、`EnableRetries` パラメーターを次の例のように使用することで、トランザクションの再試行を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="2cdde-131">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
```xml  
<WorkflowRuntime Name="SampleApplication" UnloadOnIdle="false">  
    <commonParameters>  
        <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />  
        <add name="EnableRetries" value="True" />  
    </commonParameters>  
    <Services>  
        <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" EnableRetries="False" />   
     </Services>  
</WorkflowRuntime>  
```  
  
 <span data-ttu-id="2cdde-132">注意して、`EnableRetries`グローバル レベルでいずれかのパラメーターを設定することができます (のように、 *CommonParameters*セクション)、または個々 のサービスをサポートする`EnableRetries`(で示すように、 *Services*セクション)。</span><span class="sxs-lookup"><span data-stu-id="2cdde-132">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="2cdde-133">共通パラメーターをプログラムによって変更する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="2cdde-133">The following sample code shows how to change the common parameters programmatically.</span></span>  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="2cdde-134">動作を制御する構成ファイルの使用の詳細については、<xref:System.Workflow.Runtime.WorkflowRuntime>オブジェクトの Windows Workflow Foundation ホスト アプリケーションでは、次を参照してください。[ワークフロー構成ファイル](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)です。</span><span class="sxs-lookup"><span data-stu-id="2cdde-134">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cdde-135">例</span><span class="sxs-lookup"><span data-stu-id="2cdde-135">Example</span></span>  
  
```xml  
<commonParameters>  
   <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;"/>  
   <add name="EnableRetries" value="true"/>  
</commonParameters>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2cdde-136">参照</span><span class="sxs-lookup"><span data-stu-id="2cdde-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>  
 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>  
 [<span data-ttu-id="2cdde-137">ワークフロー構成ファイル</span><span class="sxs-lookup"><span data-stu-id="2cdde-137">Workflow Configuration Files</span></span>](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)  
 [<span data-ttu-id="2cdde-138">\<add></span><span class="sxs-lookup"><span data-stu-id="2cdde-138">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)
