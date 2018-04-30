---
title: Expressions2
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 43a85905-77b5-4893-bb38-1cb9b293d69d
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c8470a3bb93385724f50e18d25c148ee609c3a77
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="expressions"></a><span data-ttu-id="f7865-102">式</span><span class="sxs-lookup"><span data-stu-id="f7865-102">Expressions</span></span>
<span data-ttu-id="f7865-103">このサンプルでは、基本的な式をワークフローで使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f7865-103">This sample demonstrates how to use basic expressions in a workflow.</span></span> <span data-ttu-id="f7865-104">このサンプルは、架空の会社の 2 人の従業員の基本給を計算するワークフローで構成されます。</span><span class="sxs-lookup"><span data-stu-id="f7865-104">It consists of a workflow that calculates basic salary statistics for two employees of a fictitious company.</span></span> <span data-ttu-id="f7865-105">`Employee` および `SalaryStats` という 2 つのクラスが Employee.cs と SalaryStats.cs で定義されています。</span><span class="sxs-lookup"><span data-stu-id="f7865-105">Two classes, `Employee` and `SalaryStats`, are defined in Employee.cs and SalaryStats.cs.</span></span> <span data-ttu-id="f7865-106">これらのクラスをワークフローで使用して、複合型の変数のプロパティに対する単純な数値演算と文字列操作を実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f7865-106">These classes are used in a workflow that shows how to perform simple arithmetic and string operations on properties of variables of complex types.</span></span>  
  
 <span data-ttu-id="f7865-107">給与計算ワークフローは、2 つの作成スタイルを示すために XAML と C# の両方で定義されています。</span><span class="sxs-lookup"><span data-stu-id="f7865-107">The salary calculation workflow is defined both in XAML and in C# to demonstrate the two authoring styles.</span></span> <span data-ttu-id="f7865-108">XAML バージョンは SalaryCalculation.xaml にあり、ワークフロー デザイナーで表示および編集できます。</span><span class="sxs-lookup"><span data-stu-id="f7865-108">The XAML version is contained in SalaryCalculation.xaml and can be viewed and edited in the workflow designer.</span></span> <span data-ttu-id="f7865-109">C# バージョンは Program.cs にあります。</span><span class="sxs-lookup"><span data-stu-id="f7865-109">The C# version resides in Program.cs.</span></span> <span data-ttu-id="f7865-110">XAML で使用されている式は Visual Basic 構文に準拠しており、<xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> 式アクティビティと <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> 式アクティビティを使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="f7865-110">The expressions used in XAML conform to Visual Basic syntax, and use <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> expression activities to execute.</span></span> <span data-ttu-id="f7865-111">詳細については、Visual Basic 式「 [Visual Basic 式](http://go.microsoft.com/fwlink/?LinkId=165912)です。</span><span class="sxs-lookup"><span data-stu-id="f7865-111">For more information about Visual Basic expressions see, [Visual Basic Expressions](http://go.microsoft.com/fwlink/?LinkId=165912).</span></span> <span data-ttu-id="f7865-112">一方、C# の式はラムダ式で記述されており、<xref:System.Activities.Expressions.LambdaValue%601> 式アクティビティと <xref:System.Activities.Expressions.LambdaReference%601> 式アクティビティが使用されます。</span><span class="sxs-lookup"><span data-stu-id="f7865-112">On the other hand, expressions in C# are written as lambda expressions and use <xref:System.Activities.Expressions.LambdaValue%601> and <xref:System.Activities.Expressions.LambdaReference%601> expression activities.</span></span> <span data-ttu-id="f7865-113">ラムダ式で記述されているため、C# コンパイラで構文の強調表示や静的な検証を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="f7865-113">Writing expressions as lambda expressions allows the C# compiler to provide syntax highlighting and static verification.</span></span> <span data-ttu-id="f7865-114">C# でのラムダ式の詳細については、次を参照してください。[ラムダ式 (c# プログラミング ガイド)](http://go.microsoft.com/fwlink/?LinkId=182082)です。</span><span class="sxs-lookup"><span data-stu-id="f7865-114">For more information about lambda expressions in C#, see [Lambda Expressions (C# Programming Guide)](http://go.microsoft.com/fwlink/?LinkId=182082).</span></span> <span data-ttu-id="f7865-115">ワークフローの作成時に Visual Basic でコードを記述すると、Visual Basic ラムダ式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f7865-115">If a workflow is authored in code using Visual Basic, then Visual Basic lambda expressions are used.</span></span> <span data-ttu-id="f7865-116">Visual Basic のラムダ式の詳細については、次を参照してください。[ラムダ式 (Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=152437)です。</span><span class="sxs-lookup"><span data-stu-id="f7865-116">For more information about lambda expressions in Visual Basic, see [Lambda Expressions (Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=152437).</span></span> <span data-ttu-id="f7865-117">コードを使用してワークフローの作成に関する詳細については、次を参照してください。[オーサリング ワークフロー、アクティビティ、および命令型コードを使用して式](../../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)です。</span><span class="sxs-lookup"><span data-stu-id="f7865-117">For more information about about authoring workflows using code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](../../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="f7865-118">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="f7865-118">To run the sample</span></span>  
  
1.  <span data-ttu-id="f7865-119">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で Expressions.sln ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="f7865-119">Open the Expressions.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="f7865-120">ソリューションをビルドまたは選択するには CTRL + SHIFT + B キーを押して**ソリューションのビルド**から、**ビルド**メニュー。</span><span class="sxs-lookup"><span data-stu-id="f7865-120">Press CTRL+SHIFT+B to build the solution or select **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f7865-121">Visual Studio デザイナーで SalaryCalculation.xaml を開くには、先にプロジェクトをコンパイルして、`Employee` クラスと `SalaryStats` クラスをデザイナーで使用できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7865-121">To open SalaryCalculation.xaml in the Visual Studio designer, you must first compile your project to ensure that `Employee` and `SalaryStats` classes are available to the designer.</span></span>  
  
3.  <span data-ttu-id="f7865-122">F5 キーを押してビルドが成功した後、または選択**デバッグの開始**から、**デバッグ**メニュー。</span><span class="sxs-lookup"><span data-stu-id="f7865-122">Once the build has succeeded, press F5 or select **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="f7865-123">または ctrl キーを押しながら f5 キーを押してまたは選択**デバッグなしで開始**から、**デバッグ**] メニューの [デバッグなしで実行します。</span><span class="sxs-lookup"><span data-stu-id="f7865-123">Alternatively you can press Ctrl+F5 or select **Start Without Debugging** from the **Debug** menu to run without debugging.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f7865-124">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="f7865-124">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f7865-125">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f7865-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f7865-126">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="f7865-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f7865-127">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="f7865-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Expressions`