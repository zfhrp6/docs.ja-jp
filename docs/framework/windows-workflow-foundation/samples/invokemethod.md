---
title: InvokeMethod
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 04988eb3-65f8-456d-b1bd-509f5d05a57c
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f988f206fbd84b7b7d47fb3bd540420601ba30c9
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="invokemethod"></a><span data-ttu-id="e9948-102">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="e9948-102">InvokeMethod</span></span>
<span data-ttu-id="e9948-103">このサンプルでは、<xref:System.Activities.Statements.InvokeMethod> アクティビティを使用してクラスのメソッドを呼び出すさまざまな方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e9948-103">This sample shows the different ways of using the <xref:System.Activities.Statements.InvokeMethod> activity to invoke methods of a class.</span></span>  
  
 <span data-ttu-id="e9948-104">メソッドはクラスに属し、含まれる操作のセットを表します。</span><span class="sxs-lookup"><span data-stu-id="e9948-104">A method belongs to a class and represents a contained set of operations.</span></span> <span data-ttu-id="e9948-105"><xref:System.Activities.Statements.InvokeMethod> アクティビティを使用すると、オブジェクトまたは型に対してメソッドを呼び出し、パラメーターを渡して、戻り値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="e9948-105">The <xref:System.Activities.Statements.InvokeMethod> activity gives you the ability to call methods against objects or types, pass in parameters, and get the return value.</span></span> <span data-ttu-id="e9948-106">メソッドは、同期または非同期に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="e9948-106">Methods can be invoked synchronously or asynchronously.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="e9948-107">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="e9948-107">Sample Details</span></span>  
 <span data-ttu-id="e9948-108">このサンプルでは、<xref:System.Activities.Statements.InvokeMethod> アクティビティを使用して次のシナリオを実行します。</span><span class="sxs-lookup"><span data-stu-id="e9948-108">This sample uses the <xref:System.Activities.Statements.InvokeMethod> activity to perform the following scenarios:</span></span>  
  
1.  <span data-ttu-id="e9948-109">パラメーターを指定せずにインスタンス メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e9948-109">Invoke an instance method without parameters.</span></span>  
  
2.  <span data-ttu-id="e9948-110">2 つのパラメーター (<xref:System.String> と <xref:System.Int32>) を指定してインスタンス メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e9948-110">Invoke an instance method with two parameters (<xref:System.String> and <xref:System.Int32>).</span></span>  
  
3.  <span data-ttu-id="e9948-111">2 つのパラメーター (<xref:System.String> と <xref:System.Int32>) および <xref:System.String>[] 型のパラメーター配列を指定してインスタンス メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e9948-111">Invoke an instance method with two parameters (<xref:System.String> and <xref:System.Int32>) and a parameter array of type <xref:System.String>[].</span></span>  
  
4.  <span data-ttu-id="e9948-112"><xref:System.Int32> 型の 2 つのパラメーターおよび <xref:System.Int32> 型の結果を指定してインスタンス メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e9948-112">Invoke an instance method with two parameters of type <xref:System.Int32> and a result of type <xref:System.Int32>.</span></span> <span data-ttu-id="e9948-113">このシナリオでは、結果値は変数にバインドされ、別のアクティビティで使用されます。</span><span class="sxs-lookup"><span data-stu-id="e9948-113">In this scenario, the result value is bound to a variable and used in another activity.</span></span> <span data-ttu-id="e9948-114">この値は、<xref:System.Activities.Statements.WriteLine> アクティビティを使用してコンソールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e9948-114">It is displayed in the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
5.  <span data-ttu-id="e9948-115"><xref:System.String> 型と <xref:System.Int32> 型の 2 つのパラメーターを指定して静的メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e9948-115">Invoke a static method with two parameters of type <xref:System.String> and <xref:System.Int32>.</span></span>  
  
6.  <span data-ttu-id="e9948-116"><xref:System.String> 型の 1 つのジェネリック パラメーターを指定してインスタンス メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e9948-116">Invoke an instance method with one generic parameter of type <xref:System.String>.</span></span>  
  
7.  <span data-ttu-id="e9948-117"><xref:System.String> 型と <xref:System.Int32> 型の 2 つのジェネリック パラメーターを指定して静的メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e9948-117">Invoke a static method with two generic parameters of type <xref:System.String> and <xref:System.Int32>.</span></span>  
  
8.  <span data-ttu-id="e9948-118"><xref:System.String> 型の参照渡しされる 1 つのパラメーターを持つインスタンス メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e9948-118">Invoke an instance method that has one parameter passed by reference of type <xref:System.String>.</span></span> <span data-ttu-id="e9948-119">このシナリオでは、参照パラメーターは変数 (`outParam`) にバインドされ、別のアクティビティで使用されます。</span><span class="sxs-lookup"><span data-stu-id="e9948-119">In this scenario, the reference parameter is bound to a variable (`outParam`) and used in another activity.</span></span> <span data-ttu-id="e9948-120">この値は、<xref:System.Activities.Statements.WriteLine> アクティビティを使用してコンソールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e9948-120">It is displayed on the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
9. <span data-ttu-id="e9948-121">非同期インスタンス メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e9948-121">Invoke an asynchronous instance method.</span></span>  
  
10. <span data-ttu-id="e9948-122">2 つの <xref:System.Activities.Statements.InvokeMethod> アクティビティを使用して、1 つのオブジェクトの同じインスタンスで 2 つの異なるメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e9948-122">Invoke two different methods on the same instance of an object using two <xref:System.Activities.Statements.InvokeMethod> activities.</span></span>  
  
11. <span data-ttu-id="e9948-123">オブジェクトのインスタンスに値を格納します。</span><span class="sxs-lookup"><span data-stu-id="e9948-123">Store a value in an instance of an object.</span></span>  
  
12. <span data-ttu-id="e9948-124">オブジェクトのインスタンスから値を取得します。</span><span class="sxs-lookup"><span data-stu-id="e9948-124">Retrieve a value from an instance of an object.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="e9948-125">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="e9948-125">To use this sample</span></span>  
 <span data-ttu-id="e9948-126">このサンプルには、2 つのバージョンが用意されています。</span><span class="sxs-lookup"><span data-stu-id="e9948-126">This sample is provided in two versions.</span></span> <span data-ttu-id="e9948-127">このサンプルの最初のバージョンは、の使用法を示しています<xref:System.Activities.Statements.InvokeMethod>c# コードから Windows Workflow Foundation (WF) のプログラミング モデルを使用して、Codedworkflow \cs フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="e9948-127">The first version of this sample demonstrates the usage of <xref:System.Activities.Statements.InvokeMethod> through C# code using the Windows Workflow Foundation (WF) programming model and can be found under the CodedWorkflow\CS folder.</span></span> <span data-ttu-id="e9948-128">第 2 のバージョンでは、XAML で <xref:System.Activities.Statements.InvokeMethod> を使用する方法を示します。これは、DesignerWorkflow\CS フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="e9948-128">The second version demonstrates the usage of <xref:System.Activities.Statements.InvokeMethod> using XAML and can be found under the DesignerWorkflow\CS folder.</span></span>  
  
#### <a name="to-run-the-coded-workflow-sample"></a><span data-ttu-id="e9948-129">コード化されたワークフロー サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="e9948-129">To run the coded workflow sample</span></span>  
  
1.  <span data-ttu-id="e9948-130">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、CodedWorkflow\CS フォルダーにある InvokeMethodUsage.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="e9948-130">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file in the CodedWorkflow\CS folder.</span></span>  
  
2.  <span data-ttu-id="e9948-131">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="e9948-131">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="e9948-132">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="e9948-132">To run the solution, press CTRL+F5.</span></span>  
  
#### <a name="to-run-the-designer-workflow-sample"></a><span data-ttu-id="e9948-133">デザイナー ワークフロー サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="e9948-133">To run the designer workflow sample</span></span>  
  
1.  <span data-ttu-id="e9948-134">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、DesignerWorkflow\CS フォルダーにある InvokeMethodUsage.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="e9948-134">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file in the DesignerWorkflow\CS folder.</span></span>  
  
2.  <span data-ttu-id="e9948-135">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="e9948-135">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="e9948-136">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="e9948-136">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e9948-137">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="e9948-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e9948-138">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="e9948-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e9948-139">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="e9948-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e9948-140">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="e9948-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`