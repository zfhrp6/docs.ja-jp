---
title: CommentOut アクティビティ
ms.date: 03/30/2017
ms.assetid: 340204c3-f827-45fb-870e-55e2ac457ca5
ms.openlocfilehash: 7847f4e1d77c2927a27be6b83f4016a22e4e3b32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515197"
---
# <a name="commentout-activity"></a><span data-ttu-id="e3ec3-102">CommentOut アクティビティ</span><span class="sxs-lookup"><span data-stu-id="e3ec3-102">CommentOut Activity</span></span>
<span data-ttu-id="e3ec3-103">このサンプルでは、実行のパスから他のアクティビティを削除し、それらを有効にコメント化するカスタム アクティビティを記述する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e3ec3-103">This sample demonstrates how to write a custom activity that removes other activities from the path of execution, effectively commenting them out.</span></span>  
  
## <a name="the-commentout-activity"></a><span data-ttu-id="e3ec3-104">CommentOut アクティビティ</span><span class="sxs-lookup"><span data-stu-id="e3ec3-104">The CommentOut Activity</span></span>  
 <span data-ttu-id="e3ec3-105">CommentOut アクティビティでは、目標を達成するために、<xref:System.Activities.CodeActivity> 基本クラスを継承し、空の <xref:System.Activities.CodeActivity.Execute%2A> メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="e3ec3-105">To achieve its goal, the CommentOut activity derives from the <xref:System.Activities.CodeActivity> base class and implements an empty <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
}  
```  
  
 <span data-ttu-id="e3ec3-106">クラスは次の例のように宣言されます。</span><span class="sxs-lookup"><span data-stu-id="e3ec3-106">The class is declared as shown in the following example.</span></span>  
  
```  
[Designer(typeof(CommentOutDesigner))]  
[ContentProperty("Body")]  
public sealed class CommentOut : CodeActivity  
```  
  
 <span data-ttu-id="e3ec3-107">`Designer` 属性は、デザイン時にアクティビティのビジュアル インターフェイスを実装するクラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="e3ec3-107">The `Designer` attribute specifies the class that implements the visual interface of the activity at design time.</span></span> <span data-ttu-id="e3ec3-108">`ContentProperty` 属性は、このアクティビティのインスタンスの XAML 表現で `"Body"` プロパティを省略できることを宣言します。</span><span class="sxs-lookup"><span data-stu-id="e3ec3-108">The `ContentProperty` attribute declares that the `"Body"` property can be skipped in the XAML representation of an instance of this activity.</span></span>  
  
```  
<Border x:Uid="Border_1" BorderThickness ="1">  
    <sad:WorkflowItemPresenter   
    x:Uid="sad:WorkflowItemPresenter_1" AutomationProperties.AutomationId="Body" Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"  
    AllowedItemType="{x:Type sa:Activity}"  
    HintText="Drop activity here"   
    Margin="5,5,5,5" />  
</Border>  
```  
  
 <span data-ttu-id="e3ec3-109">デザイナー クラスでは、XAML はアクティビティのカスタム ビジュアル表現を作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e3ec3-109">In the designer class, XAML is used to create a custom visual representation of the activity.</span></span> <span data-ttu-id="e3ec3-110"><xref:System.Activities.Presentation.WorkflowItemPresenter> はビジュアル エディターを提供するクラスです。</span><span class="sxs-lookup"><span data-stu-id="e3ec3-110"><xref:System.Activities.Presentation.WorkflowItemPresenter> is a class that provides the visual editor.</span></span>  
  
 <span data-ttu-id="e3ec3-111">`CommentOut` アクティビティ サーフェイス上には、1 つのアクティビティをドロップできます。</span><span class="sxs-lookup"><span data-stu-id="e3ec3-111">A single activity can be dropped onto the `CommentOut` activity surface.</span></span> <span data-ttu-id="e3ec3-112">このサーフェイスに複数のアクティビティを追加する場合は、最初にシーケンス アクティビティをここにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e3ec3-112">If you want to add multiple activities to this surface, drag a sequence activity here first.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="e3ec3-113">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="e3ec3-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="e3ec3-114">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で CommentOut.sln を開きます。</span><span class="sxs-lookup"><span data-stu-id="e3ec3-114">Open CommentOut.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="e3ec3-115">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="e3ec3-115">Compile the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="e3ec3-116">Ctrl キーを押しながら F5 キーを押して、サンプルをデバッグなしで開始します。</span><span class="sxs-lookup"><span data-stu-id="e3ec3-116">Start the sample without debugging by pressing CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e3ec3-117">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="e3ec3-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e3ec3-118">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="e3ec3-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e3ec3-119">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="e3ec3-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e3ec3-120">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="e3ec3-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\CommentOut`
