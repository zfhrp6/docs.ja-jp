---
title: 値の範囲で切り替えを行うカスタム アクティビティ
ms.date: 03/30/2017
ms.assetid: 441e0a17-421f-430c-ba97-59e4cc6c88e3
ms.openlocfilehash: 785db08ffaf4ca6fe27d6418878c0bbf4ada44fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517070"
---
# <a name="custom-activity-to-switch-on-a-range-of-values"></a><span data-ttu-id="e4c41-102">値の範囲で切り替えを行うカスタム アクティビティ</span><span class="sxs-lookup"><span data-stu-id="e4c41-102">Custom Activity to Switch on a Range of Values</span></span>
<span data-ttu-id="e4c41-103">このサンプルでは、<xref:System.Activities.Statements.Switch%601> の使用を拡張するカスタム アクティビティを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e4c41-103">This sample demonstrates how to create a custom activity that extends the use of a <xref:System.Activities.Statements.Switch%601>.</span></span> <span data-ttu-id="e4c41-104">従来の <xref:System.Activities.Statements.Switch%601> ステートメントでは、単一の値に基づく切り替えが可能です。</span><span class="sxs-lookup"><span data-stu-id="e4c41-104">A conventional <xref:System.Activities.Statements.Switch%601> statement allows switching based upon a single value.</span></span> <span data-ttu-id="e4c41-105">しかし、ビジネス上のシナリオでは、値の範囲に基づいて切り替えを行う必要があるアクティビティもあります。</span><span class="sxs-lookup"><span data-stu-id="e4c41-105">But, there are business scenarios where an activity must switch based upon a range of values.</span></span> <span data-ttu-id="e4c41-106">たとえば、切り替えの基準となる値が 1 ～ 5 の場合はあるアクションを実行し、6 ～ 10 の場合は別のアクションを実行し、それ以外の値の場合は既定のアクションを実行するようなアクティビティもあります。</span><span class="sxs-lookup"><span data-stu-id="e4c41-106">For example, an activity might execute one action when the value being switched upon is between 1 and 5, another action when the value is between 6 and 10, and a default action for all other values.</span></span> <span data-ttu-id="e4c41-107">このカスタム アクティビティを使用すると、そのようなシナリオが可能になります。</span><span class="sxs-lookup"><span data-stu-id="e4c41-107">This custom activity enables exactly that scenario.</span></span>  
  
## <a name="the-switchrange-activity"></a><span data-ttu-id="e4c41-108">SwitchRange アクティビティ</span><span class="sxs-lookup"><span data-stu-id="e4c41-108">The SwitchRange Activity</span></span>  
 <span data-ttu-id="e4c41-109">`SwitchRange` アクティビティは、式の結果の値がいずれかの `Cases` の範囲内に含まれる場合に子アクティビティをスケジュールします。</span><span class="sxs-lookup"><span data-stu-id="e4c41-109">The `SwitchRange` activity schedules a child activity when the result value of its expression is included within the range of one of its `Cases`.</span></span>  
  
 <span data-ttu-id="e4c41-110">値の範囲に基づいて切り替えを行うカスタム アクティビティのコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e4c41-110">The following code example is a custom activity that switches based upon a range of values.</span></span>  
  
```csharp  
public sealed class SwitchRange<T> : NativeActivity where T : IComparable  
{  
   [RequiredArgument]  
   [DefaultValue(null)]  
   public InArgument<T> Expression { get; set; }  
  
   public IList<CaseRange<T>> Cases  
  
   [DefaultValue(null)]  
   public Activity Default { get; set; }}  
}  
```  
  
|<span data-ttu-id="e4c41-111">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e4c41-111">Property</span></span>|<span data-ttu-id="e4c41-112">説明</span><span class="sxs-lookup"><span data-stu-id="e4c41-112">Description</span></span>|  
|-|-|  
|<span data-ttu-id="e4c41-113">式</span><span class="sxs-lookup"><span data-stu-id="e4c41-113">Expression</span></span>|<span data-ttu-id="e4c41-114">評価されて Cases リストの範囲と比較される式です。</span><span class="sxs-lookup"><span data-stu-id="e4c41-114">This is the expression to be evaluated and compared against the ranges in the Cases list.</span></span> <span data-ttu-id="e4c41-115">式の結果は T 型です。</span><span class="sxs-lookup"><span data-stu-id="e4c41-115">The result of the expression is of type T.</span></span>|  
|<span data-ttu-id="e4c41-116">Cases</span><span class="sxs-lookup"><span data-stu-id="e4c41-116">Cases</span></span>|<span data-ttu-id="e4c41-117">各ケースは、範囲 (From および To) とアクティビティ (Body) で構成されます。</span><span class="sxs-lookup"><span data-stu-id="e4c41-117">Each case consists of a range (From and To) and an activity (Body).</span></span> <span data-ttu-id="e4c41-118">式が評価されて範囲と比較され、</span><span class="sxs-lookup"><span data-stu-id="e4c41-118">The expression is evaluated and compared against the ranges.</span></span> <span data-ttu-id="e4c41-119">式の結果がいずれかのケースの範囲内の値になると、対応するアクティビティが実行されます。</span><span class="sxs-lookup"><span data-stu-id="e4c41-119">If the result of the expression is within the range of one of the cases, the corresponding activity is executed.</span></span>|  
|<span data-ttu-id="e4c41-120">既定値</span><span class="sxs-lookup"><span data-stu-id="e4c41-120">Default</span></span>|<span data-ttu-id="e4c41-121">一致するケースがない場合に実行されるアクティビティです。</span><span class="sxs-lookup"><span data-stu-id="e4c41-121">The activity that is executed when no case is matched.</span></span> <span data-ttu-id="e4c41-122">`null` に設定されている場合、アクションは実行されません。</span><span class="sxs-lookup"><span data-stu-id="e4c41-122">When set to `null`, no action is taken.</span></span>|  
  
## <a name="caserange-class"></a><span data-ttu-id="e4c41-123">CaseRange クラス</span><span class="sxs-lookup"><span data-stu-id="e4c41-123">CaseRange Class</span></span>  
 <span data-ttu-id="e4c41-124">`CaseRange` クラスは、`SwitchRange` アクティビティ内の範囲を表します。</span><span class="sxs-lookup"><span data-stu-id="e4c41-124">The `CaseRange` class represents a range within a `SwitchRange` activity.</span></span> <span data-ttu-id="e4c41-125">`CaseRange` の各インスタンスには、範囲 (`From` および `To`) と、`Body` の式の評価結果が範囲内の値になった場合にスケジュールされる `SwitchRange` アクティビティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e4c41-125">Every instance of `CaseRange` contains a range (composed of a `From` and a `To`) and a `Body` activity that is scheduled if the expression in the `SwitchRange` is evaluated within the range.</span></span>  
  
 <span data-ttu-id="e4c41-126">`CaseRange` クラスの定義のコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e4c41-126">The following code example is the definition for the `CaseRange` class.</span></span>  
  
```  
public class CaseRange<T> where T : IComparable  
{  
    public T From { get; set; }  
  
    public T To { get; set; }  
  
    public Activity Action { get; set; }  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="e4c41-127">このサンプルで定義されている `SwitchRange` クラスと `CaseRange` クラスはどちらも、`IComparable` クラスと同様に、<xref:System.Activities.Statements.Switch%601> を実装する任意の型で実行できるジェネリック クラスです。</span><span class="sxs-lookup"><span data-stu-id="e4c41-127">Both the `SwitchRange` and `CaseRange` classes, which are defined in the sample are generic classes that can work with any type that implements `IComparable`, like the <xref:System.Activities.Statements.Switch%601> class.</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="e4c41-128">サンプルの使用方法</span><span class="sxs-lookup"><span data-stu-id="e4c41-128">Sample Usage</span></span>  
 <span data-ttu-id="e4c41-129">`SwitchRange` アクティビティの使用方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="e4c41-129">The following code example demonstrates how to use the `SwitchRange` activity.</span></span>  
  
```csharp  
Activity SwitchRange = new SwitchRange<int>  
{  
    Expression = new InArgument<int>(value),  
    Cases =   
    {  
        new CaseRange<int>                      
        {  
            From = 1,  
            To = 5,  
            Action = new WriteLine  
            {  
                Text = "Case 1-5 selected",  
            }  
        },  
        new CaseRange<int>  
        {  
            From = 6,  
            To = 10,  
            Action = new WriteLine  
            {  
                Text = "Case 6-10 selected",  
            }  
        }  
    },  
    Default = new WriteLine { Text = "Default Case selected" }  
};  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="e4c41-130">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="e4c41-130">To use this sample</span></span>  
  
1.  <span data-ttu-id="e4c41-131">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、SwitchRange.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="e4c41-131">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the SwitchRange.sln solution file.</span></span>  
  
2.  <span data-ttu-id="e4c41-132">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="e4c41-132">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="e4c41-133">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="e4c41-133">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e4c41-134">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="e4c41-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e4c41-135">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="e4c41-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e4c41-136">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="e4c41-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e4c41-137">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="e4c41-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SwitchRange`