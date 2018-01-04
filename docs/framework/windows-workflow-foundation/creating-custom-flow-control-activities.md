---
title: "カスタムのフロー制御アクティビティの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27f409f6-2d1d-4cfb-9765-93eb2ad667d5
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57c347043d1bbcf239841bc57c6a406cfc9af7f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="creating-custom-flow-control-activities"></a><span data-ttu-id="ce7c5-102">カスタムのフロー制御アクティビティの作成</span><span class="sxs-lookup"><span data-stu-id="ce7c5-102">Creating custom flow control activities</span></span>
<span data-ttu-id="ce7c5-103">.NET Framework には、抽象化されたプログラミング構造 (<xref:System.Activities.Statements.Flowchart> など) や標準的なプログラミング ステートメント (<xref:System.Activities.Statements.If> など) に対して同様に機能するさまざまなフロー制御アクティビティがあります。</span><span class="sxs-lookup"><span data-stu-id="ce7c5-103">The .Net Framework contains a variety of flow-control activities that function similarly to abstract programming structures (such as <xref:System.Activities.Statements.Flowchart>)   or to standard programming statements (such as <xref:System.Activities.Statements.If>).</span></span> <span data-ttu-id="ce7c5-104">サンプル プロジェクトの 1 つのアーキテクチャについて説明[非ジェネリックの ForEach](../../../docs/framework/windows-workflow-foundation/samples/non-generic-foreach.md)です。</span><span class="sxs-lookup"><span data-stu-id="ce7c5-104">This topic discusses the architecture of one of the sample projects, [Non-Generic ForEach](../../../docs/framework/windows-workflow-foundation/samples/non-generic-foreach.md).</span></span>  
  
## <a name="creating-the-custom-class"></a><span data-ttu-id="ce7c5-105">カスタム クラスの作成</span><span class="sxs-lookup"><span data-stu-id="ce7c5-105">Creating the custom class</span></span>  
 <span data-ttu-id="ce7c5-106">非ジェネリックの ForEach クラスは子アクティビティをスケジュールする必要があるため、<xref:System.Activities.NativeActivity> から派生する必要があります。<xref:System.Workflow.Activities.CodeActivity> から派生したアクティビティにはこの機能がありません。</span><span class="sxs-lookup"><span data-stu-id="ce7c5-106">Since the Non-Generic ForEach class will need to schedule child activities, it will need to derive from <xref:System.Activities.NativeActivity>, since activities that derive from <xref:System.Workflow.Activities.CodeActivity> do not have this functionality.</span></span>  
  
```  
public sealed class ForEach : NativeActivity  
    {  
```  
  
 <span data-ttu-id="ce7c5-107">カスタム クラスには、アクティビティによって使用されているデータを格納し、アクティビティの子アクティビティを実行する機能を提供するためのいくつかのメンバーが必要です。</span><span class="sxs-lookup"><span data-stu-id="ce7c5-107">The custom class requires several members to store data being used by the activity, and to provide functionality to execute the activity’s child activities.</span></span> <span data-ttu-id="ce7c5-108">そのメンバーには以下が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ce7c5-108">These members include:</span></span>  
  
-   <span data-ttu-id="ce7c5-109">`valueEnumerator`: 項目のコレクションを反復処理する非パブリックの <xref:System.Activities.Variable%601> 型の <xref:System.Collections.IEnumerator>。</span><span class="sxs-lookup"><span data-stu-id="ce7c5-109">`valueEnumerator`: The non-public <xref:System.Activities.Variable%601> of type <xref:System.Collections.IEnumerator> used to iterate over the collection of items.</span></span> <span data-ttu-id="ce7c5-110">このメンバーは引数またはパブリック プロパティではなく、アクティビティで内部的に使用されるため、<xref:System.Activities.Variable%601> 型となり、このオブジェクトの発生元がアクティビティの外部にある場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="ce7c5-110">This member is of type <xref:System.Activities.Variable%601> because it is used internally in the activity, rather than an argument or public property, which would be used if this object were to have an origin outside the activity.</span></span>  
  
-   <span data-ttu-id="ce7c5-111">`OnChildComplete`: 各子の実行の完了時に実行されるパブリック <xref:System.Activities.CompletionCallback> プロパティ。</span><span class="sxs-lookup"><span data-stu-id="ce7c5-111">`OnChildComplete`: The public <xref:System.Activities.CompletionCallback> property that executes when each child completes execution.</span></span> <span data-ttu-id="ce7c5-112">このメンバーは、アクティビティの異なるインスタンスごとに値が変わらないため、CLR プロパティとして定義されています。</span><span class="sxs-lookup"><span data-stu-id="ce7c5-112">This member is defined as a CLR property, since its value will not change for different instances of the activity.</span></span>  
  
-   <span data-ttu-id="ce7c5-113">`Values`: 子アクティビティの反復処理に使用される入力のコレクション。</span><span class="sxs-lookup"><span data-stu-id="ce7c5-113">`Values`: The collection of inputs used for the iterations of the child activity.</span></span> <span data-ttu-id="ce7c5-114">このメンバーは、データの発生元がアクティビティの外部にあり、アクティビティの実行中にコレクションの内容の変更が想定されないため、<xref:System.Activities.InArgument%601> 型です。</span><span class="sxs-lookup"><span data-stu-id="ce7c5-114">This member is of type <xref:System.Activities.InArgument%601>, since the origin of the data is outside the activity, but the contents of the collection is not expected to change during the execution of the activity.</span></span> <span data-ttu-id="ce7c5-115">アクティビティの実行中に、アクティビティ (たとえば、追加または削除) のためにこのコレクションの内容を変更する機能が必要な場合、このメンバーは <xref:System.Activities.ActivityAction> として定義されます。この場合、メンバーはアクセスするたびに評価され、変更をアクティビティに反映できます。</span><span class="sxs-lookup"><span data-stu-id="ce7c5-115">If the activity needed the functionality to change the contents of this collection while the activity was executing (to add or remove activities, for instance), this member would have been defined as an <xref:System.Activities.ActivityAction>, which then would have been evaluated every time it was accessed, so that changes would be available to the activity.</span></span>  
  
-   <span data-ttu-id="ce7c5-116">`Body`: このメンバーはアクティビティを `Values` コレクションの項目ごとに実行されるように定義します。</span><span class="sxs-lookup"><span data-stu-id="ce7c5-116">`Body`: This member defines the activity to be executed for each item in the `Values` collection.</span></span> <span data-ttu-id="ce7c5-117">このメンバーは、アクセスするたびに評価されるように <xref:System.Activities.ActivityAction> として定義されます。</span><span class="sxs-lookup"><span data-stu-id="ce7c5-117">This member is defined as an <xref:System.Activities.ActivityAction> so that it is evaluated every time it is accessed.</span></span>  
  
-   <span data-ttu-id="ce7c5-118">`Execute`: このメソッドは `InternalExecute`、`OnForEachComplete`、および `GetStateAndExecute` の非パブリック メンバーを使用して実行をスケジュールし、Body メンバーに定義された子アクティビティの完了ハンドラーを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ce7c5-118">`Execute`: This method uses the `InternalExecute`, `OnForEachComplete`, and `GetStateAndExecute` non-public members to schedule the execution and assign the completion handler of the child activity defined in the Body member.</span></span>  
  
-   <span data-ttu-id="ce7c5-119">`CacheMetadata`: このメンバーはアクティビティの実行に必要な情報をランタイムに提供します。</span><span class="sxs-lookup"><span data-stu-id="ce7c5-119">`CacheMetadata`: This member provides the runtime with the information it needs to execute the activity.</span></span> <span data-ttu-id="ce7c5-120">既定では、アクティビティの `CacheMetadata` メソッドはランタイムにアクティビティのすべてのパブリック メンバーを通知しますが、このアクティビティは一部の機能にプライベート メンバーを使用するため、ランタイムにプライベート メンバーの存在を通知して認識されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce7c5-120">By default, an activity’s `CacheMetadata` method will inform the runtime of all public members of the activity, but since this activity uses private members for some functionality, it needs to inform the runtime of their existence so that the runtime can be aware of them.</span></span> <span data-ttu-id="ce7c5-121">この場合、`CacheMetadata` 関数はオーバーライドされ、プライベートの `valueEnumerator` メンバーにアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="ce7c5-121">In this case, the `CacheMetadata` function is overridden so that the private `valueEnumerator` member can be accessed.</span></span> <span data-ttu-id="ce7c5-122">このメンバーはアクティビティの値の引数も作成し、実行時にアクティビティに渡すことができるようにします。</span><span class="sxs-lookup"><span data-stu-id="ce7c5-122">This member also creates an argument for the values for the activity so that they can be passed in to the activity during execution.</span></span>
