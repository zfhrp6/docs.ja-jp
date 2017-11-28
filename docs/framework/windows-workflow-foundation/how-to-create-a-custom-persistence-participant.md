---
title: "カスタム永続参加要素を作成する方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d9cc47a-8966-4286-94d5-4221403d9c06
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4c690a0233a425a706ead7441447f589d8330bc0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-custom-persistence-participant"></a><span data-ttu-id="e2561-102">カスタム永続参加要素を作成する方法</span><span class="sxs-lookup"><span data-stu-id="e2561-102">How to: Create a Custom Persistence Participant</span></span>
<span data-ttu-id="e2561-103">次の手順では、永続参加要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="e2561-103">The following procedure has steps to create a persistence participant.</span></span> <span data-ttu-id="e2561-104">参照してください、[永続化に参加している](http://go.microsoft.com/fwlink/?LinkID=177735)サンプルと[ストア拡張](../../../docs/framework/windows-workflow-foundation/store-extensibility.md)永続参加要素のサンプルの実装に関するトピック。</span><span class="sxs-lookup"><span data-stu-id="e2561-104">See the [Participating in Persistence](http://go.microsoft.com/fwlink/?LinkID=177735) sample and [Store Extensibility](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) topic for sample implementations of persistence participants.</span></span>  
  
1.  <span data-ttu-id="e2561-105"><xref:System.Activities.Persistence.PersistenceParticipant> または <xref:System.Activities.Persistence.PersistenceIOParticipant> クラスから派生するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e2561-105">Create a class deriving from the <xref:System.Activities.Persistence.PersistenceParticipant> or the <xref:System.Activities.Persistence.PersistenceIOParticipant> class.</span></span> <span data-ttu-id="e2561-106">PersistenceIOParticipant クラスには、IO 操作に参加できることに加え、PersistenceParticipant クラスと同じ拡張ポイントが備わっています。</span><span class="sxs-lookup"><span data-stu-id="e2561-106">The PersistenceIOParticipant class offers the same extensibility points as the PersistenceParticipant class in addition to being able to participate in IO operations.</span></span> <span data-ttu-id="e2561-107">次のうち、必要な手順を行います。</span><span class="sxs-lookup"><span data-stu-id="e2561-107">Follow one or more of the following steps.</span></span>  
  
2.  <span data-ttu-id="e2561-108"><xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="e2561-108">Implement the <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> method.</span></span> <span data-ttu-id="e2561-109">**CollectValues**メソッドが 2 つのディクショナリ パラメーター、読み取り/書き込み値を格納するため、1 つは他の (後でクエリで使用)、書き込み専用の値を格納します。</span><span class="sxs-lookup"><span data-stu-id="e2561-109">The **CollectValues** method has two dictionary parameters, one for storing read/write values and the other one for storing write-only values (used later in queries).</span></span> <span data-ttu-id="e2561-110">このメソッドでは、永続参加要素に固有のデータをこれらのディクショナリに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2561-110">In this method, you should populate these dictionaries with data that is specific to a persistence participant.</span></span> <span data-ttu-id="e2561-111">各ディクショナリには、値の名前がキーとして格納されているほか、値そのものが <xref:System.Runtime.DurableInstancing.InstanceValue> オブジェクトとして格納されています。</span><span class="sxs-lookup"><span data-stu-id="e2561-111">Each dictionary contains the name of the value as the key and the value itself as an <xref:System.Runtime.DurableInstancing.InstanceValue> object.</span></span>  
  
     <span data-ttu-id="e2561-112">ReadWriteValues ディクショナリ内の値としてパッケージ化**InstanceValue**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e2561-112">The values in the readWriteValues dictionary are packaged as **InstanceValue** objects.</span></span> <span data-ttu-id="e2561-113">書き込み専用のディクショナリ内の値としてパッケージ化**InstanceValue** InstanceValueOptions.Optional および InstanceValueOption.WriteOnly セットを持つオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e2561-113">The values in the write-only dictionary are packaged as **InstanceValue** objects with InstanceValueOptions.Optional and InstanceValueOption.WriteOnly set.</span></span> <span data-ttu-id="e2561-114">各**InstanceValue**によって提供される、 **CollectValues**すべての永続参加要素の間での実装は名前が一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2561-114">Each **InstanceValue** provided by the **CollectValues** implementations across all persistence participants must have a unique name.</span></span>  
  
    ```  
    protected virtual void CollectValues (out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
3.  <span data-ttu-id="e2561-115"><xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="e2561-115">Implement the <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> method.</span></span> <span data-ttu-id="e2561-116">**MapValues**メソッドは、パラメーターに似ている 2 つのパラメーターを**CollectValues**メソッドは受信します。</span><span class="sxs-lookup"><span data-stu-id="e2561-116">The **MapValues** method takes two parameters that are similar to the parameters that the **CollectValues** method receives.</span></span> <span data-ttu-id="e2561-117">収集されたすべての値、 **CollectValues**ステージはこれらのディクショナリ パラメーターを通じて渡されます。</span><span class="sxs-lookup"><span data-stu-id="e2561-117">All the values collected in the **CollectValues** stage are passed through these dictionary parameters.</span></span> <span data-ttu-id="e2561-118">によって追加された新しい値、 **MapValues**ステージは、書き込み専用値に追加されます。</span><span class="sxs-lookup"><span data-stu-id="e2561-118">The new values added by the **MapValues** stage are added to the write-only values.</span></span>  <span data-ttu-id="e2561-119">書き込み専用のディクショナリが、インスタンスの値に直接関連付けられていない外部ソースにデータを提供するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e2561-119">The write-only dictionary is used to provide data to an external source not directly associated with the instance values.</span></span> <span data-ttu-id="e2561-120">実装によって形成されるそれぞれの値、 **MapValues**すべての永続参加要素の間でのメソッドは名前が一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2561-120">Each value provided by implementations of the **MapValues** method across all persistence participants must have a unique name.</span></span>  
  
    ```  
    protected virtual IDictionary<XName,Object> MapValues (IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
     <span data-ttu-id="e2561-121"><xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> メソッドは <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> が提供しない機能を提供し、<xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> が処理しなかった別の永続参加により提供される、別の値への依存関係が許可されます。</span><span class="sxs-lookup"><span data-stu-id="e2561-121">The <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> method provides functionality that <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> does not, in that it allows for a dependency on another value provided by another persistence participant that hasn’t been processed by <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> yet.</span></span>  
  
4.  <span data-ttu-id="e2561-122">実装、 **PublishValues**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e2561-122">Implement the **PublishValues** method.</span></span> <span data-ttu-id="e2561-123">**PublishValues**メソッドは、永続化ストアから読み込まれたすべての値を含むディクショナリを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e2561-123">The **PublishValues** method receives a dictionary containing all the values loaded from the persistence store.</span></span>  
  
    ```  
    protected virtual void PublishValues (IDictionary<XName,Object> readWriteValues)  
    ```  
  
5.  <span data-ttu-id="e2561-124">実装、 **BeginOnSave**メソッド、参加要素が永続 IO 参加要素の場合。</span><span class="sxs-lookup"><span data-stu-id="e2561-124">Implement the **BeginOnSave** method if the participant is a persistence IO participant.</span></span> <span data-ttu-id="e2561-125">このメソッドは保存操作中に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e2561-125">This method is called during a Save operation.</span></span> <span data-ttu-id="e2561-126">このメソッドでは、永続化 (保存) しているワークフロー インスタンスに付随する IO を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2561-126">In this method, you should perform IO adjunct to the persisting (saving) workflow instances.</span></span>  <span data-ttu-id="e2561-127">ホストが、対応する永続化コマンドのトランザクションを使用している場合、同じトランザクションが Transaction.Current で確立されます。</span><span class="sxs-lookup"><span data-stu-id="e2561-127">If the host is using a transaction for the corresponding persistence command, the same transaction is provided in Transaction.Current.</span></span>  <span data-ttu-id="e2561-128">さらに、PersistenceIOParticipant はトランザクションの一貫性の要件を通知することがあります。この場合、ホストはほかに使用されなければ、永続化のトランザクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="e2561-128">Additionally, PersistenceIOParticipants may advertise a transactional consistency requirement, in which case the host creates a transaction for the persistence episode if one would not otherwise be used.</span></span>  
  
    ```  
    protected virtual IAsyncResult BeginOnSave (IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```  
  
6.  <span data-ttu-id="e2561-129">実装、 **BeginOnLoad**メソッド、参加要素が永続 IO 参加要素の場合。</span><span class="sxs-lookup"><span data-stu-id="e2561-129">Implement the **BeginOnLoad** method if the participant is a persistence IO participant.</span></span> <span data-ttu-id="e2561-130">このメソッドは読み込み操作中に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e2561-130">This method is called during a Load operation.</span></span> <span data-ttu-id="e2561-131">このメソッドでは、ワークフロー インスタンスの読み込みに付随する IO を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2561-131">In this method, you should perform IO adjunct to the loading of workflow instances.</span></span> <span data-ttu-id="e2561-132">ホストが、対応する永続化コマンドのトランザクションを使用している場合、同じトランザクションが Transaction.Current で確立されます。</span><span class="sxs-lookup"><span data-stu-id="e2561-132">If the host is using a transaction for the corresponding persistence command, the same transaction is provided in Transaction.Current.</span></span> <span data-ttu-id="e2561-133">さらに、PersistenceIOParticipant はトランザクションの一貫性の要件を通知することがあります。この場合、ホストはほかに使用されなければ、永続化のトランザクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="e2561-133">Additionally, Persistence IO participants may advertise a transactional consistency requirement, in which case the host creates a transaction for the persistence episode if one would not otherwise be used.</span></span>  
  
    ```  
    protected virtual IAsyncResult BeginOnLoad (IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```
