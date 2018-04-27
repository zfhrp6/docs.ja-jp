---
title: Hello World カスタム アクティビティ
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 72b1dd0a-9aad-47d5-95a9-a1024ee1d0a1
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fa441a3019b0ef6df31dc0a46be7ea7e8e00a4b8
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="hello-world-custom-activity"></a><span data-ttu-id="9dc01-102">Hello World カスタム アクティビティ</span><span class="sxs-lookup"><span data-stu-id="9dc01-102">Hello World Custom Activity</span></span>
<span data-ttu-id="9dc01-103">このサンプルでは、いくつかの主要機能の Windows Workflow Foundation (WF)、単純なカスタム アクティビティを作成する方法などを示します。</span><span class="sxs-lookup"><span data-stu-id="9dc01-103">This sample demonstrates several key features of Windows Workflow Foundation (WF), including how to create a simple custom activity.</span></span> <span data-ttu-id="9dc01-104">このサンプルで示す機能では、C# でカスタム アクティビティを作成し、`in` 引数と `out` 引数 (<xref:System.Activities.InArgument> と <xref:System.Activities.OutArgument>) を使用します。</span><span class="sxs-lookup"><span data-stu-id="9dc01-104">Some of the features demonstrated in this sample are creating a custom activity in C# and using `in` and `out` arguments (<xref:System.Activities.InArgument> and <xref:System.Activities.OutArgument>).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9dc01-105">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="9dc01-105">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9dc01-106">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="9dc01-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9dc01-107">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="9dc01-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9dc01-108">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="9dc01-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\HelloWorld`  
  
## <a name="creating-a-workflow-in-code"></a><span data-ttu-id="9dc01-109">コードでのワークフローの作成</span><span class="sxs-lookup"><span data-stu-id="9dc01-109">Creating a Workflow in Code</span></span>  
 <span data-ttu-id="9dc01-110">このサンプルでは、C# コードを使用して、2 つのカスタム アクティビティを作成します。</span><span class="sxs-lookup"><span data-stu-id="9dc01-110">In this sample, two custom activities are created using C# code.</span></span> <span data-ttu-id="9dc01-111">どちらのカスタム アクティビティも、<xref:System.Activities.Activity%601> から直接または間接に継承して、1 つの値を返します。</span><span class="sxs-lookup"><span data-stu-id="9dc01-111">Both custom activities inherit directly or indirectly from <xref:System.Activities.Activity%601> to return a single value.</span></span> <span data-ttu-id="9dc01-112">非ジェネリック クラス <xref:System.Activities.Activity> から継承する代わりにジェネリックな戻り値を使用する利点は、特定のアクティビティ (<xref:System.Activities.Statements.Assign> など) が、作成されるアクティビティの一部として使用する場合に戻り値にアクセスできることです。</span><span class="sxs-lookup"><span data-stu-id="9dc01-112">The advantage of using the generic return value, instead of inheriting from the non-generic <xref:System.Activities.Activity> class, is that some activities (such as <xref:System.Activities.Statements.Assign>) are able to access the return value when used as part of a composed activity.</span></span>  
  
 <span data-ttu-id="9dc01-113">AppendString</span><span class="sxs-lookup"><span data-stu-id="9dc01-113">AppendString</span></span>  
 <span data-ttu-id="9dc01-114">このアクティビティは、<xref:System.Activities.Activity%601> から継承し、2 つの文字列を 1 つに連結する <xref:System.Activities.Statements.Assign> アクティビティを使用します。</span><span class="sxs-lookup"><span data-stu-id="9dc01-114">This activity inherits from <xref:System.Activities.Activity%601>, and uses an <xref:System.Activities.Statements.Assign> activity that concatenates two strings together.</span></span>  
  
 <span data-ttu-id="9dc01-115">Prepend String</span><span class="sxs-lookup"><span data-stu-id="9dc01-115">Prepend String</span></span>  
 <span data-ttu-id="9dc01-116">このアクティビティは、<xref:System.Activities.CodeActivity%601> から直接継承し、`AppendString` アクティビティと同様の機能を作成します。この機能は、既存のアクティビティから構成されるのではなく、コードに実装されているロジックを使用します。</span><span class="sxs-lookup"><span data-stu-id="9dc01-116">This activity inherits directly from <xref:System.Activities.CodeActivity%601>, and creates similar functionality to the `AppendString` activity, which uses logic implemented in code rather than being composed of a pre-existing activity.</span></span>  
  
 <span data-ttu-id="9dc01-117">このプロジェクトには、次のファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="9dc01-117">The following files are included in this project.</span></span>  
  
 <span data-ttu-id="9dc01-118">AppendString.cs</span><span class="sxs-lookup"><span data-stu-id="9dc01-118">AppendString.cs</span></span>  
 <span data-ttu-id="9dc01-119">複数の文字列を 1 つにするカスタム アクティビティです。</span><span class="sxs-lookup"><span data-stu-id="9dc01-119">The custom activity that appends strings together.</span></span> <span data-ttu-id="9dc01-120">文字列を受け取りし、リテラル テキスト文字列を出力として完全なメッセージを"says hello world"に結合します。</span><span class="sxs-lookup"><span data-stu-id="9dc01-120">It takes in a string and combines it with a literal text string " says hello world" to form a complete message as output.</span></span>  
  
 <span data-ttu-id="9dc01-121">PrependString.cs</span><span class="sxs-lookup"><span data-stu-id="9dc01-121">PrependString.cs</span></span>  
 <span data-ttu-id="9dc01-122">このアクティビティは、定義済みの文字列を入力文字列の先頭に付けます。</span><span class="sxs-lookup"><span data-stu-id="9dc01-122">This activity prefixes a predefined string to an input string.</span></span>  
  
 <span data-ttu-id="9dc01-123">Sequence1.xaml</span><span class="sxs-lookup"><span data-stu-id="9dc01-123">Sequence1.xaml</span></span>  
 <span data-ttu-id="9dc01-124">`AppendString` カスタム アクティビティと `PrependString` カスタム アクティビティを使用するワークフローです。</span><span class="sxs-lookup"><span data-stu-id="9dc01-124">A workflow that uses the `AppendString` and `PrependString` custom activities.</span></span>  
  
 <span data-ttu-id="9dc01-125">Program.cs</span><span class="sxs-lookup"><span data-stu-id="9dc01-125">Program.cs</span></span>  
 <span data-ttu-id="9dc01-126">ワークフローを実行するプログラムです。</span><span class="sxs-lookup"><span data-stu-id="9dc01-126">A program that runs the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="9dc01-127">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="9dc01-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="9dc01-128">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、HelloWorld.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="9dc01-128">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the HelloWorld.sln solution file.</span></span>  
  
2.  <span data-ttu-id="9dc01-129">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="9dc01-129">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="9dc01-130">ソリューションを実行するには、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="9dc01-130">To run the solution, press F5.</span></span>