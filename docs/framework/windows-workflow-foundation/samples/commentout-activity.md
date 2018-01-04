---
title: "CommentOut アクティビティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 340204c3-f827-45fb-870e-55e2ac457ca5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 900f6647eadb04a783fe0a3a143a71d9c766a48c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="commentout-activity"></a><span data-ttu-id="28cec-102">CommentOut アクティビティ</span><span class="sxs-lookup"><span data-stu-id="28cec-102">CommentOut Activity</span></span>
<span data-ttu-id="28cec-103">このサンプルでは、実行のパスから他のアクティビティを削除し、それらを有効にコメント化するカスタム アクティビティを記述する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="28cec-103">This sample demonstrates how to write a custom activity that removes other activities from the path of execution, effectively commenting them out.</span></span>  
  
## <a name="the-commentout-activity"></a><span data-ttu-id="28cec-104">CommentOut アクティビティ</span><span class="sxs-lookup"><span data-stu-id="28cec-104">The CommentOut Activity</span></span>  
 <span data-ttu-id="28cec-105">CommentOut アクティビティでは、目標を達成するために、<xref:System.Activities.CodeActivity> 基本クラスを継承し、空の <xref:System.Activities.CodeActivity.Execute%2A> メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="28cec-105">To achieve its goal, the CommentOut activity derives from the <xref:System.Activities.CodeActivity> base class and implements an empty <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
}  
```  
  
 <span data-ttu-id="28cec-106">クラスは次の例のように宣言されます。</span><span class="sxs-lookup"><span data-stu-id="28cec-106">The class is declared as shown in the following example.</span></span>  
  
```  
[Designer(typeof(CommentOutDesigner))]  
[ContentProperty("Body")]  
public sealed class CommentOut : CodeActivity  
```  
  
 <span data-ttu-id="28cec-107">`Designer` 属性は、デザイン時にアクティビティのビジュアル インターフェイスを実装するクラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="28cec-107">The `Designer` attribute specifies the class that implements the visual interface of the activity at design time.</span></span> <span data-ttu-id="28cec-108">`ContentProperty` 属性は、このアクティビティのインスタンスの XAML 表現で `"Body"` プロパティを省略できることを宣言します。</span><span class="sxs-lookup"><span data-stu-id="28cec-108">The `ContentProperty` attribute declares that the `"Body"` property can be skipped in the XAML representation of an instance of this activity.</span></span>  
  
```  
<Border x:Uid="Border_1" BorderThickness ="1">  
    <sad:WorkflowItemPresenter   
    x:Uid="sad:WorkflowItemPresenter_1" AutomationProperties.AutomationId="Body" Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"  
    AllowedItemType="{x:Type sa:Activity}"  
    HintText="Drop activity here"   
    Margin="5,5,5,5" />  
</Border>  
```  
  
 <span data-ttu-id="28cec-109">デザイナー クラスでは、XAML はアクティビティのカスタム ビジュアル表現を作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="28cec-109">In the designer class, XAML is used to create a custom visual representation of the activity.</span></span> <span data-ttu-id="28cec-110"><xref:System.Activities.Presentation.WorkflowItemPresenter> はビジュアル エディターを提供するクラスです。</span><span class="sxs-lookup"><span data-stu-id="28cec-110"><xref:System.Activities.Presentation.WorkflowItemPresenter> is a class that provides the visual editor.</span></span>  
  
 <span data-ttu-id="28cec-111">`CommentOut` アクティビティ サーフェイス上には、1 つのアクティビティをドロップできます。</span><span class="sxs-lookup"><span data-stu-id="28cec-111">A single activity can be dropped onto the `CommentOut` activity surface.</span></span> <span data-ttu-id="28cec-112">このサーフェイスに複数のアクティビティを追加する場合は、最初にシーケンス アクティビティをここにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="28cec-112">If you want to add multiple activities to this surface, drag a sequence activity here first.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="28cec-113">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="28cec-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="28cec-114">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で CommentOut.sln を開きます。</span><span class="sxs-lookup"><span data-stu-id="28cec-114">Open CommentOut.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="28cec-115">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="28cec-115">Compile the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="28cec-116">Ctrl キーを押しながら F5 キーを押して、サンプルをデバッグなしで開始します。</span><span class="sxs-lookup"><span data-stu-id="28cec-116">Start the sample without debugging by pressing CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="28cec-117">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="28cec-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="28cec-118">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="28cec-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="28cec-119">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="28cec-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="28cec-120">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="28cec-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\CommentOut`
