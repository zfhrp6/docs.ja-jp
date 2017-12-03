---
title: "Flowchart のワークフロー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0a3475c-d22f-49eb-8912-973c960aebf5
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d5975cff014c1d74b9935a7cc95a6b2f25359db5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="flowchart-workflows"></a><span data-ttu-id="5cf11-102">Flowchart のワークフロー</span><span class="sxs-lookup"><span data-stu-id="5cf11-102">Flowchart Workflows</span></span>
<span data-ttu-id="5cf11-103">フローチャートは、プログラムを診断するための既知のパラダイムです。</span><span class="sxs-lookup"><span data-stu-id="5cf11-103">A flowchart is a well-known paradigm for designing programs.</span></span> <span data-ttu-id="5cf11-104">通常、Flowchart アクティビティはシーケンシャル以外のワークフローを実装するために使用されますが、`FlowDecision` ノードが使用されない場合は、シーケンシャル ワークフローにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="5cf11-104">The Flowchart activity is typically used to implement non-sequential workflows, but can be used for sequential workflows if no `FlowDecision` nodes are used.</span></span>  
  
## <a name="flowchart-workflow-structure"></a><span data-ttu-id="5cf11-105">Flowchart のワークフロー構造</span><span class="sxs-lookup"><span data-stu-id="5cf11-105">Flowchart Workflow Structure</span></span>  
 <span data-ttu-id="5cf11-106">Flowchart アクティビティは、実行されるアクティビティのコレクションを含むアクティビティです。</span><span class="sxs-lookup"><span data-stu-id="5cf11-106">A Flowchart activity is an activity that contains a collection of activities to be executed.</span></span>  <span data-ttu-id="5cf11-107">フローチャートには、変数の値に基づいて含まれているアクティビティ間の実行を指示する、<xref:System.Activities.Statements.FlowDecision> や <xref:System.Activities.Statements.FlowSwitch%601> などのフロー制御要素も含まれています。</span><span class="sxs-lookup"><span data-stu-id="5cf11-107">Flowcharts also contain flow control elements such as <xref:System.Activities.Statements.FlowDecision> and <xref:System.Activities.Statements.FlowSwitch%601> that direct execution between contained activities based on the values of variables.</span></span>  
  
## <a name="types-of-flow-nodes"></a><span data-ttu-id="5cf11-108">フロー ノードの種類</span><span class="sxs-lookup"><span data-stu-id="5cf11-108">Types of Flow Nodes</span></span>  
 <span data-ttu-id="5cf11-109">要素の実行時に必要なフロー制御の種類に応じて、さまざまな種類の要素が使用されます。</span><span class="sxs-lookup"><span data-stu-id="5cf11-109">Different types of elements are used depending on the type of flow control required when the element executes.</span></span> <span data-ttu-id="5cf11-110">フローチャート要素には次のような種類があります。</span><span class="sxs-lookup"><span data-stu-id="5cf11-110">Types of flowchart elements include:</span></span>  
  
-   <span data-ttu-id="5cf11-111">`FlowStep` - フローチャートの実行の 1 ステップをモデル化します。</span><span class="sxs-lookup"><span data-stu-id="5cf11-111">`FlowStep` - Models one step of execution in the flowchart.</span></span>  
  
-   <span data-ttu-id="5cf11-112">`FlowDecision` - <xref:System.Activities.Statements.If> と同様に、ブール条件に基づいて実行を分岐します。</span><span class="sxs-lookup"><span data-stu-id="5cf11-112">`FlowDecision` - Branches execution based on a Boolean condition, similar to <xref:System.Activities.Statements.If>.</span></span>  
  
-   <span data-ttu-id="5cf11-113">`FlowSwitch` - <xref:System.Activities.Statements.Switch%601> と同様に、排他的スイッチに基づいて実行を分岐します。</span><span class="sxs-lookup"><span data-stu-id="5cf11-113">`FlowSwitch` – Branches execution based on an exclusive switch, similar to <xref:System.Activities.Statements.Switch%601>.</span></span>  
  
 <span data-ttu-id="5cf11-114">各リンクには、子アクティビティの実行に使用できる `Action` を定義した <xref:System.Activities.ActivityAction> プロパティと、現在の要素の実行が完了したときに実行する 1 つ以上の要素を定義した 1 つ以上の `Next` プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="5cf11-114">Each link has an `Action` property that defines a <xref:System.Activities.ActivityAction> that can be used to execute child activities, and one or more `Next` properties that define which element or elements to execute when the current element finishes execution.</span></span>  
  
### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a><span data-ttu-id="5cf11-115">FlowStep ノードによる基本的な Activity Sequence の作成</span><span class="sxs-lookup"><span data-stu-id="5cf11-115">Creating a Basic Activity Sequence with a FlowStep Node</span></span>  
 <span data-ttu-id="5cf11-116">2 つのアクティビティを連続して実行する基本的なシーケンスをモデル化するには、`FlowStep` 要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="5cf11-116">To model a basic sequence in which two activities execute in turn, the `FlowStep` element is used.</span></span> <span data-ttu-id="5cf11-117">次の例では、2 つの `FlowStep` 要素を使用して 2 つのアクティビティを連続して実行しています。</span><span class="sxs-lookup"><span data-stu-id="5cf11-117">In the following example, two `FlowStep` elements are used to execute two activities in sequence.</span></span>  
  
```xml  
<Flowchart>  
  <FlowStep>      
  <Assign DisplayName="Get Name">  
    <Assign.To>  
      <OutArgument x:TypeArguments="x:String">[result]</OutArgument>  
    </Assign.To>  
    <Assign.Value>  
      <InArgument x:TypeArguments="x:String">["User"]</InArgument>  
    </Assign.Value>  
  </Assign>  
    <FlowStep.Next>  
      <FlowStep>  
        <WriteLine Text="["Hello, " & result]"/>  
</FlowStep>  
    </FlowStep.Next>  
  </FlowStep>  
</Flowchart>  
```  
  
### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a><span data-ttu-id="5cf11-118">FlowDecision ノードによる条件付きフローの作成</span><span class="sxs-lookup"><span data-stu-id="5cf11-118">Creating a Conditional Flowchart with a FlowDecision Node</span></span>  
 <span data-ttu-id="5cf11-119">フローチャート ワークフローの条件付きフロー ノードをモデル化するには (つまり、従来のフローチャートの決定シンボルとして機能するリンクを作成するには)、<xref:System.Activities.Statements.FlowDecision> ノードを使用します。</span><span class="sxs-lookup"><span data-stu-id="5cf11-119">To model a conditional flow node in a flowchart workflow (that is, to create a link that functions as a traditional flowchart's decision symbol), a <xref:System.Activities.Statements.FlowDecision> node is used.</span></span> <span data-ttu-id="5cf11-120">ノードの <xref:System.Activities.Statements.FlowDecision.Condition%2A> プロパティは、条件を定義する式に設定されます。また、<xref:System.Activities.Statements.FlowDecision.True%2A> プロパティと <xref:System.Activities.Statements.FlowDecision.False%2A> プロパティは、式が <xref:System.Activities.Statements.FlowNode> または `true` に評価された場合に実行される `false` インスタンスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="5cf11-120">The <xref:System.Activities.Statements.FlowDecision.Condition%2A> property of the node is set to an expression that defines the condition, and the <xref:System.Activities.Statements.FlowDecision.True%2A> and <xref:System.Activities.Statements.FlowDecision.False%2A> properties are set to <xref:System.Activities.Statements.FlowNode> instances to be executed if the expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="5cf11-121">次の例では、<xref:System.Activities.Statements.FlowDecision> ノードを使用するワークフローを定義する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5cf11-121">The following example shows how to define a workflow that uses a <xref:System.Activities.Statements.FlowDecision> node.</span></span>  
  
```xml  
<Flowchart>  
  <FlowStep>  
    <Read Result="[s]"/>  
    <FlowStep.Next>  
      <FlowDecision>  
        <IsEmpty Input="[s]" />  
        <FlowDecision.True>  
    <FlowStep>  
            <Write Text="Empty"/>  
    </FlowStep>  
        </FlowDecision.True>  
        <FlowDecision.False>  
    <FlowStep>  
            <Write Text="Non-Empty"/>  
          </FlowStep>  
        </FlowDecision.False>  
      </FlowDecision>  
    </FlowStep.Next>  
  </FlowStep>  
</Flowchart>  
```  
  
### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a><span data-ttu-id="5cf11-122">FlowSwitch ノードによる排他的スイッチの作成</span><span class="sxs-lookup"><span data-stu-id="5cf11-122">Creating an Exclusive Switch with a FlowSwitch Node</span></span>  
 <span data-ttu-id="5cf11-123">一致する値に基づいて 1 つの排他的パスを選択するフローチャートをモデル化するには、<xref:System.Activities.Statements.FlowSwitch%601> ノードを使用します。</span><span class="sxs-lookup"><span data-stu-id="5cf11-123">To model a flowchart in which one exclusive path is selected based on a matching value, the <xref:System.Activities.Statements.FlowSwitch%601> node is used.</span></span> <span data-ttu-id="5cf11-124"><xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> プロパティは、選択に対して一致する値を定義する <xref:System.Activities.Activity%601> の型パラメーターを持つ <xref:System.Object> に設定されます。</span><span class="sxs-lookup"><span data-stu-id="5cf11-124">The <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> property is set to a <xref:System.Activities.Activity%601> with a type parameter of <xref:System.Object> that defines the value to match choices against.</span></span> <span data-ttu-id="5cf11-125"><xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> プロパティは、条件式に対して一致する、キーと <xref:System.Activities.Statements.FlowNode> オブジェクトのディクショナリと、特定のケースが条件式に一致する場合のフローの実行方法を定義する <xref:System.Activities.Statements.FlowNode> オブジェクトのセットを定義します。</span><span class="sxs-lookup"><span data-stu-id="5cf11-125">The <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> property defines a dictionary of keys and <xref:System.Activities.Statements.FlowNode> objects to match against the conditional expression, and a set of <xref:System.Activities.Statements.FlowNode> objects that define how execution should flow if the given case matches the conditional expression.</span></span> <span data-ttu-id="5cf11-126">また、<xref:System.Activities.Statements.FlowSwitch%601> は、条件式に一致するケースがない場合の実行フローを定義する <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> プロパティも定義します。</span><span class="sxs-lookup"><span data-stu-id="5cf11-126">The <xref:System.Activities.Statements.FlowSwitch%601> also defines a <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> property that defines how execution should flow if no cases match the condition expression.</span></span> <span data-ttu-id="5cf11-127">次のコードは、<xref:System.Activities.Statements.FlowSwitch%601> 要素を使用するワークフローを定義する方法の例です。</span><span class="sxs-lookup"><span data-stu-id="5cf11-127">The following example demonstrates how to define a workflow that uses a <xref:System.Activities.Statements.FlowSwitch%601> element.</span></span>  
  
```xml  
<Flowchart>  
    <FlowSwitch>  
      <FlowStep x:Key="Red">  
        <WriteRed/>  
      </FlowStep>  
      <FlowStep x:Key="Blue">  
        <WriteBlue/>  
      </FlowStep>  
      <FlowStep x:Key="Green">  
        <WriteGreen/>  
      </FlowStep>  
    </FlowSwitch>  
</Flowchart>  
```
