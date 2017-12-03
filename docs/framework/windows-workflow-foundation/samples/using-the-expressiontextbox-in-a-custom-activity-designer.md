---
title: "カスタム アクティビティ デザイナーでの ExpressionTextBox の使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 85fe8dcbd0ef5e774ab81ed167ff937ec2e09d83
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a><span data-ttu-id="820bf-102">カスタム アクティビティ デザイナーでの ExpressionTextBox の使用</span><span class="sxs-lookup"><span data-stu-id="820bf-102">Using the ExpressionTextBox in a Custom Activity Designer</span></span>
<span data-ttu-id="820bf-103">このサンプルでは、カスタム アクティビティ デザイナーで <xref:System.Activities.Presentation.View.ExpressionTextBox> を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="820bf-103">This sample shows how to use the <xref:System.Activities.Presentation.View.ExpressionTextBox> in a custom activity designer.</span></span> <span data-ttu-id="820bf-104">カスタム アクティビティ `MultiAssign` は、2 つの文字列値を 2 つの文字列変数に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="820bf-104">The custom activity, `MultiAssign`, assigns two string values to two string variables.</span></span> <span data-ttu-id="820bf-105"><xref:System.Activities.Presentation.View.ExpressionTextBox> コントロールには、<xref:System.Activities.InArgument> にバインドされるものと <xref:System.Activities.OutArgument> にバインドされるものがあります。</span><span class="sxs-lookup"><span data-stu-id="820bf-105">Some <xref:System.Activities.Presentation.View.ExpressionTextBox> controls bind to <xref:System.Activities.InArgument>s and some bind to <xref:System.Activities.OutArgument>s.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="820bf-106">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="820bf-106">Sample details</span></span>  
 <span data-ttu-id="820bf-107">`ArgumentToExpressionConverter` は、式を引数にバインドするときに使用される型コンバーターです。</span><span class="sxs-lookup"><span data-stu-id="820bf-107">The `ArgumentToExpressionConverter` is the type converter used when binding expressions to arguments.</span></span> <span data-ttu-id="820bf-108">`ConverterParameter` は、必要に応じて、`In` または `Out` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="820bf-108">The `ConverterParameter` must be set to `In` or `Out` as appropriate.</span></span> <span data-ttu-id="820bf-109">`InOut` がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="820bf-109">`InOut` is not supported.</span></span>  
  
 <span data-ttu-id="820bf-110">`UseLocationExpression`属性を使用`OutArgument`の式が左辺値 (「左辺値」または「位置値」) 式を指定する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="820bf-110">The `UseLocationExpression` attribute is used on `OutArgument`s to specify that the expression should be an L-value ("left value" or "location value") expression.</span></span> <span data-ttu-id="820bf-111">ほとんど場合、L 値式は、返される `OutArgument` が変数または引数の名前であることを示すために使用される有効な Visual Basic 識別子です。</span><span class="sxs-lookup"><span data-stu-id="820bf-111">In most cases, an L-value expression is a valid Visual Basic identifier used to indicate that the `OutArgument` being returned is a variable or argument name.</span></span>  
  
 <span data-ttu-id="820bf-112">この例では、`MaxLines` 属性は 1 に設定され、`MinLines` は設定されていません。</span><span class="sxs-lookup"><span data-stu-id="820bf-112">The `MaxLines` attribute is set to one in this example and `MinLines` is not set.</span></span> <span data-ttu-id="820bf-113">つまり、ユーザーによって入力されるテキストの量に関係なく、<xref:System.Activities.Presentation.View.ExpressionTextBox> のサイズが 1 行に固定されることを示しています。</span><span class="sxs-lookup"><span data-stu-id="820bf-113">This indicates that the <xref:System.Activities.Presentation.View.ExpressionTextBox> is a fixed size of one line regardless of the amount of text typed by the user.</span></span> <span data-ttu-id="820bf-114"><xref:System.Activities.Presentation.View.ExpressionTextBox> がユーザーの入力に合わせて拡大されるようにするには、`MaxLines` に `MinLines` より大きい値を設定します。</span><span class="sxs-lookup"><span data-stu-id="820bf-114">To allow the <xref:System.Activities.Presentation.View.ExpressionTextBox> to grow to fit user input, set `MaxLines` greater than `MinLines`.</span></span>  
  
 <span data-ttu-id="820bf-115">ExpressionTextBox は、引数にのみバインドできます。CLR プロパティにはバインドできません。</span><span class="sxs-lookup"><span data-stu-id="820bf-115">An ExpressionTextBox can only be bound to arguments, and cannot be bound to CLR properties.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="820bf-116">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="820bf-116">To use this sample</span></span>  
  
1.  <span data-ttu-id="820bf-117">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、ExpressionTextBoxSample.sln ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="820bf-117">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ExpressionTextBoxSample.sln file.</span></span>  
  
2.  <span data-ttu-id="820bf-118">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="820bf-118">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="820bf-119">このサンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="820bf-119">To run this sample</span></span>  
  
1.  <span data-ttu-id="820bf-120">新しいワークフロー コンソール アプリケーションをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="820bf-120">Add a new Workflow Console Application to the solution.</span></span>  
  
2.  <span data-ttu-id="820bf-121">参照を追加、 **ExpressionTextBoxSample**新しいワークフロー コンソール アプリケーション プロジェクトからプロジェクト。</span><span class="sxs-lookup"><span data-stu-id="820bf-121">Add a reference to the **ExpressionTextBoxSample** project from the new Workflow Console Application project.</span></span>  
  
3.  <span data-ttu-id="820bf-122">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="820bf-122">Build the solution.</span></span>  
  
4.  <span data-ttu-id="820bf-123">ドラッグ、 **MultiAssign**アクティビティをツールボックスし、ワークフローにドロップします。</span><span class="sxs-lookup"><span data-stu-id="820bf-123">Drag the **MultiAssign** activity from the toolbox and drop it into the workflow.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="820bf-124">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="820bf-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="820bf-125">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="820bf-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="820bf-126">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="820bf-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="820bf-127">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="820bf-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a><span data-ttu-id="820bf-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="820bf-128">See Also</span></span>  
 <xref:System.Activities.Presentation.View.ExpressionTextBox>  
 [<span data-ttu-id="820bf-129">ワークフロー デザイナーを使用したアプリケーションの開発</span><span class="sxs-lookup"><span data-stu-id="820bf-129">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
