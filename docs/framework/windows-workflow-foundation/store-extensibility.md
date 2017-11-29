---
title: "ストア拡張"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c3f4a46-4bac-4138-ae6a-a7c7ee0d28f5
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f6700fe67d151e78c8b216d93a4cd7098ed6401d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="store-extensibility"></a><span data-ttu-id="05e0b-102">ストア拡張</span><span class="sxs-lookup"><span data-stu-id="05e0b-102">Store Extensibility</span></span>
<span data-ttu-id="05e0b-103"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> を使用して、永続性データベースのインスタンスをクエリする場合に使用できるカスタムのアプリケーション固有のプロパティを昇格できます。</span><span class="sxs-lookup"><span data-stu-id="05e0b-103"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> allows users to promote custom, application-specific properties that can be used to query for instances in the persistence database.</span></span> <span data-ttu-id="05e0b-104">プロパティを昇格することで、データベース内の特殊なビュー内で値が使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="05e0b-104">The act of promoting a property causes the value to be available within a special view in the database.</span></span> <span data-ttu-id="05e0b-105">これらの昇格したプロパティ (ユーザー クエリで使用できるプロパティ) は、単純型 (Int64、Guid、String、DateTime など) またはシリアル化されたバイナリ型 (byte[]) になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="05e0b-105">These promoted properties (properties that can be used in user queries) can be of simple types such as Int64, Guid, String, and DateTime or of a serialized binary type (byte[]).</span></span>  
  
 <span data-ttu-id="05e0b-106"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> クラスには <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> メソッドがあり、クエリで使用できるプロパティとしてプロパティを昇格するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="05e0b-106">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> class has the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> method that you can use to promote a property as a property that can be used in queries.</span></span> <span data-ttu-id="05e0b-107">次の例は、ストア拡張のエンド ツー エンドの例です。</span><span class="sxs-lookup"><span data-stu-id="05e0b-107">The following example is an end-to-end example of store extensibility.</span></span>  
  
1.  <span data-ttu-id="05e0b-108">この例のシナリオでは、ドキュメント処理 (DP) アプリケーションにワークフローがあり、それぞれがドキュメント処理にカスタム アクティビティを使用しています。</span><span class="sxs-lookup"><span data-stu-id="05e0b-108">In this example scenario, a document processing (DP) application has workflows, each of which uses custom activities for document processing.</span></span> <span data-ttu-id="05e0b-109">これらのワークフローは、エンド ユーザーから見える必要がある一連の状態変数を備えています。</span><span class="sxs-lookup"><span data-stu-id="05e0b-109">These workflows have a set of state variables that need to be made visible to the end user.</span></span> <span data-ttu-id="05e0b-110">これを実現するために、DP アプリケーションには <xref:System.Activities.Persistence.PersistenceParticipant> 型を持つインスタンス拡張機能があり、状態変数を提供するアクティビティによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="05e0b-110">To achieve this, the DP application provides an instance extension of type <xref:System.Activities.Persistence.PersistenceParticipant>, which is used by activities to supply the state variables.</span></span>  
  
    ```  
    class DocumentStatusExtension : PersistenceParticipant  
    {  
        public string DocumentId;  
        public string ApprovalStatus;  
        public string UserName;  
        public DateTime LastUpdateTime;  
    }  
    ```  
  
2.  <span data-ttu-id="05e0b-111">次に、新しい機能拡張がホストに追加されます。</span><span class="sxs-lookup"><span data-stu-id="05e0b-111">The new extension is then added to the host.</span></span>  
  
    ```  
    static Activity workflow = CreateWorkflow();  
    WorkflowApplication application = new WorkflowApplication(workflow);  
    DocumentStatusExtension documentStatusExtension = new DocumentStatusExtension ();  
    application.Extensions.Add(documentStatusExtension);  
    ```  
  
     <span data-ttu-id="05e0b-112">カスタムの永続参加要素を追加する方法の詳細については、次を参照してください。、[永続参加要素](../../../docs/framework/windows-workflow-foundation/persistence-participants.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="05e0b-112">For more details about adding a custom persistence participant, see the [Persistence Participants](../../../docs/framework/windows-workflow-foundation/persistence-participants.md) sample.</span></span>  
  
3.  <span data-ttu-id="05e0b-113">DP アプリケーションでカスタム アクティビティのさまざまな状態フィールドの設定、 **Execute**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="05e0b-113">The custom activities in the DP application populate various status fields in the **Execute** method.</span></span>  
  
    ```  
    public override void Execute(CodeActivityContext context)  
    {  
        // ...  
        context.GetExtension<DocumentStatusExtension>().DocumentId = Guid.NewGuid();  
        context.GetExtension<DocumentStatusExtension>().UserName = "John Smith";  
        context.GetExtension<DocumentStatusExtension>().ApprovalStatus = "Approved";  
        context.GetExtension<DocumentStatusExtension>().LastUpdateTime = DateTime.Now();  
        // ...  
    }  
    ```  
  
4.  <span data-ttu-id="05e0b-114">ワークフロー インスタンスが永続性ポイントに達すると、 **CollectValues**のメソッド、 **DocumentStatusExtension**永続参加要素は、これらのプロパティを永続性データに保存されますコレクションです。</span><span class="sxs-lookup"><span data-stu-id="05e0b-114">When a workflow instance reaches a persistence point, the **CollectValues** method of the **DocumentStatusExtension** persistence participant saves these properties into the persistence data collection.</span></span>  
  
    ```  
    class DocumentStatusExtension : PersistenceParticipant  
    {  
        const XNamespace xNS = XNamespace.Get("http://contoso.com/DocumentStatus");  
  
        protected override void CollectValues(out IDictionary<XName, object> readWriteValues, out IDictionary<XName, object> writeOnlyValues)  
        {  
            readWriteValues = new Dictionary<XName, object>();  
            readWriteValues.Add(xNS.GetName("UserName"), this.UserName);  
            readWriteValues.Add(xNS.GetName("ApprovalStatus"), this.ApprovalStatus);  
            readWriteValues.Add(xNS.GetName("DocumentId"), this.DocumentId);  
            readWriteValues.Add(xNS.GetName("LastModifiedTime"), this.LastUpdateTime);  
  
            writeOnlyValues = null;  
        }  
        // ...  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="05e0b-115">これらすべてのプロパティに渡される**SqlWorkflowInstanceStore**を介して、永続化フレームワークによって、 **SaveWorkflowCommand.InstanceData**コレクション。</span><span class="sxs-lookup"><span data-stu-id="05e0b-115">All these properties are passed to **SqlWorkflowInstanceStore** by the persistence framework through the **SaveWorkflowCommand.InstanceData** collection.</span></span>  
  
5.  <span data-ttu-id="05e0b-116">DP アプリケーションは、SQL Workflow Instance Store を初期化し、呼び出します、**昇格**このデータを昇格する方法です。</span><span class="sxs-lookup"><span data-stu-id="05e0b-116">The DP application initializes the SQL Workflow Instance Store and invokes the **Promote** method to promote this data.</span></span>  
  
    ```  
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);  
  
    List<XName> variantProperties = new List<XName>()   
    {   
        xNS.GetName("UserName"),   
        xNS.GetName("ApprovalStatus"),   
        xNS.GetName("DocumentId"),   
        xNS.GetName("LastModifiedTime")   
    };  
  
    store.Promote("DocumentStatus", variantProperties, null);  
    ```  
  
     <span data-ttu-id="05e0b-117">この昇格情報に基づいて**SqlWorkflowInstanceStore**の列のデータのプロパティを配置、 [InstancePromotedProperties](#InstancePromotedProperties)ビュー。</span><span class="sxs-lookup"><span data-stu-id="05e0b-117">Based on this promotion information, **SqlWorkflowInstanceStore** places the data properties in the columns of the [InstancePromotedProperties](#InstancePromotedProperties) view.</span></span>
  
6.  <span data-ttu-id="05e0b-118">昇格テーブルのデータのサブセットを照会するために、DP アプリケーションによって昇格ビューの上にカスタマイズされたビューが追加されます。</span><span class="sxs-lookup"><span data-stu-id="05e0b-118">To query a subset of the data from the promotion table, the DP application adds a customized view on top of the promotion view.</span></span>  
  
    ```  
    create view [dbo].[DocumentStatus] with schemabinding  
    as  
        select  P.[InstanceId] as [InstanceId],  
            P.Value1 as [UserName],  
            P.Value2 as [ApprovalStatus],  
            P.Value3 as [DocumentId],  
            P.Value4 as [LastUpdatedTime]  
    from [System.Activities.DurableInstancing].[InstancePromotedProperties] as P  
    where P.PromotionName = N'DocumentStatus'  
    go  
    ```  
  
##  <span data-ttu-id="05e0b-119"><a name="InstancePromotedProperties"></a>[System.Activities.DurableInstancing.InstancePromotedProperties] ビュー</span><span class="sxs-lookup"><span data-stu-id="05e0b-119"><a name="InstancePromotedProperties"></a> [System.Activities.DurableInstancing.InstancePromotedProperties] view</span></span>  
  
|<span data-ttu-id="05e0b-120">列名</span><span class="sxs-lookup"><span data-stu-id="05e0b-120">Column Name</span></span>|<span data-ttu-id="05e0b-121">列の型</span><span class="sxs-lookup"><span data-stu-id="05e0b-121">Column Type</span></span>|<span data-ttu-id="05e0b-122">説明</span><span class="sxs-lookup"><span data-stu-id="05e0b-122">Description</span></span>|  
|-----------------|-----------------|-----------------|  
|<span data-ttu-id="05e0b-123">InstanceId</span><span class="sxs-lookup"><span data-stu-id="05e0b-123">InstanceId</span></span>|<span data-ttu-id="05e0b-124">GUID</span><span class="sxs-lookup"><span data-stu-id="05e0b-124">GUID</span></span>|<span data-ttu-id="05e0b-125">この昇格が属するワークフロー インスタンス。</span><span class="sxs-lookup"><span data-stu-id="05e0b-125">The workflow instance that this promotion belongs to.</span></span>|  
|<span data-ttu-id="05e0b-126">PromotionName</span><span class="sxs-lookup"><span data-stu-id="05e0b-126">PromotionName</span></span>|<span data-ttu-id="05e0b-127">nvarchar(400)</span><span class="sxs-lookup"><span data-stu-id="05e0b-127">nvarchar(400)</span></span>|<span data-ttu-id="05e0b-128">昇格自体の名前。</span><span class="sxs-lookup"><span data-stu-id="05e0b-128">The name of the promotion itself.</span></span>|  
|<span data-ttu-id="05e0b-129">Value1、Value2、Value3、…Value32</span><span class="sxs-lookup"><span data-stu-id="05e0b-129">Value1, Value2, Value3,..,Value32</span></span>|<span data-ttu-id="05e0b-130">sql_variant</span><span class="sxs-lookup"><span data-stu-id="05e0b-130">sql_variant</span></span>|<span data-ttu-id="05e0b-131">昇格したプロパティ自体の値。</span><span class="sxs-lookup"><span data-stu-id="05e0b-131">The value of the promoted property itself.</span></span> <span data-ttu-id="05e0b-132">ほとんどの SQL プリミティブ データ型はバイナリ ブロブを除外し、長さが 8,000 バイトを超える文字列は sql_variant に合わせて短縮されます。</span><span class="sxs-lookup"><span data-stu-id="05e0b-132">Most SQL primitive data types except binary blobs and strings over 8000 bytes in length can fit in sql_variant.</span></span>|  
|<span data-ttu-id="05e0b-133">Value33、Value34、Value35、…、Value64</span><span class="sxs-lookup"><span data-stu-id="05e0b-133">Value33, Value34, Value35, …, Value64</span></span>|<span data-ttu-id="05e0b-134">varbinary(max)</span><span class="sxs-lookup"><span data-stu-id="05e0b-134">varbinary(max)</span></span>|<span data-ttu-id="05e0b-135">varbinary(max) として明示的に宣言される昇格したプロパティの値。</span><span class="sxs-lookup"><span data-stu-id="05e0b-135">The value of promoted properties that are explicitly declared as varbinary(max).</span></span>|
