---
title: 非ジェネリックの ParallelForEach
ms.date: 03/30/2017
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
ms.openlocfilehash: 0bdaaac04162cf065d847f5071ba21953f042223
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519390"
---
# <a name="non-generic-parallelforeach"></a><span data-ttu-id="43982-102">非ジェネリックの ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="43982-102">Non-Generic ParallelForEach</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="43982-103"> などの制御フロー アクティビティのセットのツールボックスに付属<xref:System.Activities.Statements.ParallelForEach%601>、反復処理に使用できるように<!--zz <xref:System.Collections.IEnumerable%601> -->`System.Collections.IEnumerable`コレクション。</span><span class="sxs-lookup"><span data-stu-id="43982-103"> ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ParallelForEach%601>, which allows iterating through <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` collections.</span></span>  
  
 <span data-ttu-id="43982-104"><xref:System.Activities.Statements.ParallelForEach%601> 必要があります、<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>プロパティの型を<!--zz <xref:System.Collections.IEnumerable%601> -->`System.Collections.IEnumerable`です。</span><span class="sxs-lookup"><span data-stu-id="43982-104"><xref:System.Activities.Statements.ParallelForEach%601> requires its <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> property to be of type <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`.</span></span> <span data-ttu-id="43982-105">そのため、ユーザーを実装するデータ構造を繰り返し処理してから<!--zz <xref:System.Collections.IEnumerable%601> -->`System.Collections.IEnumerable`インターフェイス (たとえば、 <xref:System.Collections.ArrayList>)。</span><span class="sxs-lookup"><span data-stu-id="43982-105">This precludes users from iterating over data structures that implement <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="43982-106"><xref:System.Activities.Statements.ParallelForEach%601> の非ジェネリック バージョンにはこの要件はありませんが、コレクション内の値の型の互換性を確保するために実行時の複雑さが増します。</span><span class="sxs-lookup"><span data-stu-id="43982-106">The non-generic version of <xref:System.Activities.Statements.ParallelForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>  
  
 <span data-ttu-id="43982-107">このサンプルでは、非ジェネリックの <xref:System.Activities.Statements.ParallelForEach%601> アクティビティとそのデザイナーを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="43982-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ParallelForEach%601> activity and its designer.</span></span> <span data-ttu-id="43982-108">このアクティビティは、<xref:System.Collections.ArrayList> の反復処理に使用できます。</span><span class="sxs-lookup"><span data-stu-id="43982-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>  
  
## <a name="parallelforeach-activity"></a><span data-ttu-id="43982-109">ParallelForEachT アクティビティ</span><span class="sxs-lookup"><span data-stu-id="43982-109">ParallelForEach Activity</span></span>  
 <span data-ttu-id="43982-110">C# および VB の `foreach` ステートメントは、コレクションの要素を列挙し、コレクションの各要素に対して埋め込みステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="43982-110">The C#/VB `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="43982-111">このステートメントに相当する [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のアクティビティは、<xref:System.Activities.Statements.ForEach%601> および <xref:System.Activities.Statements.ParallelForEach%601> です。</span><span class="sxs-lookup"><span data-stu-id="43982-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="43982-112"><xref:System.Activities.Statements.ForEach%601> アクティビティには、値のリストと本体が含まれます。</span><span class="sxs-lookup"><span data-stu-id="43982-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="43982-113">実行時に、リストが反復処理されて、リスト内の値ごとに本体が実行されます。</span><span class="sxs-lookup"><span data-stu-id="43982-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>  
  
 <span data-ttu-id="43982-114"><xref:System.Activities.Statements.ParallelForEach%601> には <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> があります。そのため、<xref:System.Activities.Statements.ParallelForEach%601> の評価が <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> を返した場合、`true` アクティビティは早期に完了することがあります。</span><span class="sxs-lookup"><span data-stu-id="43982-114"><xref:System.Activities.Statements.ParallelForEach%601> has a <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, so that the <xref:System.Activities.Statements.ParallelForEach%601> activity could complete early if the evaluation of the <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> returns `true`.</span></span> <span data-ttu-id="43982-115"><xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> は、各イテレーションの完了後に評価されます。</span><span class="sxs-lookup"><span data-stu-id="43982-115">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> is evaluated after each iteration is completed.</span></span>  
  
 <span data-ttu-id="43982-116">ほとんどの場合、ジェネリック バージョンのアクティビティを使用することをお勧めします。ジェネリック バージョンのアクティビティは、そのアクティビティを使用するシナリオの大半に対応し、コンパイル時の型チェックを提供するためです。</span><span class="sxs-lookup"><span data-stu-id="43982-116">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it is used and provides type checking at compile time.</span></span> <span data-ttu-id="43982-117">非ジェネリック バージョンは、非ジェネリックの <xref:System.Collections.IEnumerable> インターフェイスを実装する型を反復処理するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="43982-117">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>  
  
## <a name="class-definition"></a><span data-ttu-id="43982-118">クラス定義</span><span class="sxs-lookup"><span data-stu-id="43982-118">Class Definition</span></span>  
 <span data-ttu-id="43982-119">次のコード例は、非ジェネリックの `ParallelForEach` アクティビティの定義を示しています。</span><span class="sxs-lookup"><span data-stu-id="43982-119">The following code example shows the definition of a non-generic `ParallelForEach` activity is.</span></span>  
  
```  
[ContentProperty("Body")]  
public class ParallelForEach : NativeActivity  
{  
    [RequiredArgument]  
    [DefaultValue(null)]  
    InArgument<IEnumerable> Values { get; set; }  
  
    [DefaultValue(null)]  
    [DependsOn("Values")]  
    public Activity<bool> CompletionCondition  
    [DefaultValue(null)]  
    [DependsOn("CompletionCondition")]  
    ActivityAction<object> Body { get; set; }   
}  
```  
  
 <span data-ttu-id="43982-120">Body (省略可能)</span><span class="sxs-lookup"><span data-stu-id="43982-120">Body (optional)</span></span>  
 <span data-ttu-id="43982-121">コレクション内の要素ごとに実行される <xref:System.Activities.ActivityAction> 型の <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="43982-121">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="43982-122">各要素は、Argument プロパティを使用して Body に渡されます。</span><span class="sxs-lookup"><span data-stu-id="43982-122">Each individual element is passed into the Body through its Argument property.</span></span>  
  
 <span data-ttu-id="43982-123">Values (省略可能)</span><span class="sxs-lookup"><span data-stu-id="43982-123">Values (optional)</span></span>  
 <span data-ttu-id="43982-124">反復処理される要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="43982-124">The collection of elements that are iterated over.</span></span> <span data-ttu-id="43982-125">コレクションのすべての要素の型が互換性のある型であることが実行時に確認されます。</span><span class="sxs-lookup"><span data-stu-id="43982-125">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>  
  
 <span data-ttu-id="43982-126">CompletionCondition (省略可能)</span><span class="sxs-lookup"><span data-stu-id="43982-126">CompletionCondition (optional)</span></span>  
 <span data-ttu-id="43982-127"><xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> プロパティは、イテレーションの完了後に評価されます。</span><span class="sxs-lookup"><span data-stu-id="43982-127">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> property is evaluated after any iteration completes.</span></span> <span data-ttu-id="43982-128">`true` であると評価する場合、スケジュールされた保留イテレーションはキャンセルされます。</span><span class="sxs-lookup"><span data-stu-id="43982-128">If it evaluates to `true`, then the scheduled pending iterations are canceled.</span></span> <span data-ttu-id="43982-129">このプロパティが設定されていない場合、分岐コレクション内のすべてのアクティビティは完了するまで実行されます。</span><span class="sxs-lookup"><span data-stu-id="43982-129">If this property is not set, all activities in the Branches collection execute until completion.</span></span>  
  
## <a name="example-of-using-parallelforeach"></a><span data-ttu-id="43982-130">ParallelForEach の使用例</span><span class="sxs-lookup"><span data-stu-id="43982-130">Example of Using ParallelForEach</span></span>  
 <span data-ttu-id="43982-131">アプリケーションでの ParallelForEach アクティビティの使用方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="43982-131">The following code demonstrates how to use the ParallelForEach activity in an application.</span></span>  
  
```  
string[] names = { "bill", "steve", "ray" };  
  
DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };  
  
Activity sampleUsage =  
    new ParallelForEach  
    {  
       Values = new InArgument<IEnumerable>(c=> names),  
       Body = new ActivityAction<object>   
       {                          
           Argument = iterationVariable,  
           Handler = new WriteLine  
           {  
               Text = new InArgument<string>(env => string.Format("Hello {0}",                                                               iterationVariable.Get(env)))  
           }  
       }  
   };  
```  
  
## <a name="parallelforeach-designer"></a><span data-ttu-id="43982-132">ParallelForEach デザイナー</span><span class="sxs-lookup"><span data-stu-id="43982-132">ParallelForEach Designer</span></span>  
 <span data-ttu-id="43982-133">サンプルのアクティビティ デザイナーは、組み込みの <xref:System.Activities.Statements.ParallelForEach%601> アクティビティ用に提供されているデザイナーに外観が似ています。</span><span class="sxs-lookup"><span data-stu-id="43982-133">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span> <span data-ttu-id="43982-134">デザイナーは、ツールボックス、**サンプル**、**非ジェネリック アクティビティ**カテゴリ。</span><span class="sxs-lookup"><span data-stu-id="43982-134">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="43982-135">デザイナーの名前は**ParallelForEachWithBodyFactory**ツールボックスでアクティビティによって公開されるため、<xref:System.Activities.Presentation.IActivityTemplateFactory>を適切に構成されたアクティビティを作成し、ツールボックスに<xref:System.Activities.ActivityAction>です。</span><span class="sxs-lookup"><span data-stu-id="43982-135">The designer is named **ParallelForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox that creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>  
  
```  
public sealed class ParallelForEachWithBodyFactory : IActivityTemplateFactory  
{  
    public Activity Create(DependencyObject target)  
    {  
        return new Microsoft.Samples.Activities.Statements.ParallelForEach()  
        {  
            Body = new ActivityAction<object>()  
            {  
                Argument = new DelegateInArgument<object>()  
                {  
                    Name = "item"  
                }  
            }  
        };  
    }  
}  
```  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="43982-136">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="43982-136">To run the sample</span></span>  
  
1.  <span data-ttu-id="43982-137">選択したプロジェクトをソリューションのスタートアップ プロジェクトに設定します。</span><span class="sxs-lookup"><span data-stu-id="43982-137">Set the project of your choice as the startup project of the solution.</span></span>  
  
    1.  <span data-ttu-id="43982-138">**CodeTestClient**コードを使用して、アクティビティを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="43982-138">**CodeTestClient** shows how to use the activity using code.</span></span>  
  
    2.  <span data-ttu-id="43982-139">**DesignerTestClient**デザイナー内でアクティビティを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="43982-139">**DesignerTestClient** shows how to use the activity within the designer.</span></span>  
  
2.  <span data-ttu-id="43982-140">プロジェクトをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="43982-140">Build and run the project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="43982-141">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="43982-141">The samples may already be installed on your machine.</span></span> <span data-ttu-id="43982-142">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="43982-142">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="43982-143">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="43982-143">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="43982-144">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="43982-144">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
