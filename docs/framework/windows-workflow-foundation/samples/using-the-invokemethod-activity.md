---
title: "InvokeMethod アクティビティの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6643550-d043-4ac7-8069-9c55ebbb4233
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: aacc20bf483877ac501fd8b35c04f6e3f9311afb
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2017
---
# <a name="using-the-invokemethod-activity"></a><span data-ttu-id="15ac0-102">InvokeMethod アクティビティの使用</span><span class="sxs-lookup"><span data-stu-id="15ac0-102">Using the InvokeMethod Activity</span></span>
<span data-ttu-id="15ac0-103">このサンプルを使用する方法を示します、 <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx)パブリック クラス内のパブリック メソッドを呼び出すアクティビティ。</span><span class="sxs-lookup"><span data-stu-id="15ac0-103">This sample demonstrates how to use the <!--zz <xref:System.Activities.Statements.InvokeMethod%601> -->[<code>System.Activities.Statements.InvokeMethod\\`1</code>](https://msdn.microsoft.com/library/dd647677.aspx) activity to invoke public methods in public classes.</span></span> <span data-ttu-id="15ac0-104"><!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx)アクティビティにより、ワークフローをオブジェクトに対してメソッドを呼び出して、パラメーターを渡す、戻り値を取得、ジェネリック メソッドの型を指定し、メソッドは同期型かどうかを指定または非同期です。</span><span class="sxs-lookup"><span data-stu-id="15ac0-104">The <!--zz <xref:System.Activities.Statements.InvokeMethod%601> -->[<code>System.Activities.Statements.InvokeMethod\\`1</code>](https://msdn.microsoft.com/library/dd647677.aspx) activity allows a workflow to call methods against objects, pass in parameters, get the return value, specify types for generic methods, and specify whether the method is synchronous or asynchronous.</span></span> 
  
<span data-ttu-id="15ac0-105">非ジェネリック バージョンがある、<xref:System.Activities.Statements.InvokeMethod>アクティビティに戻り値が設定されている、<xref:System.Activities.Statements.InvokeMethod.Result%2A>プロパティと、ジェネリック バージョンの<!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx)アクティビティの戻り値が返されますを介して、 <!--zz <xref:System.Activities.Statements.InvokeMethod.Result%601.Result%2A> --> [ <code>System.Activities.Statements.InvokeMethod\`1.Result</code> ](https://msdn.microsoft.com/library/dd987724.aspx)型のプロパティ`TResult`です。</span><span class="sxs-lookup"><span data-stu-id="15ac0-105">There is a non-generic version of the <xref:System.Activities.Statements.InvokeMethod> activity where the return value is set to the <xref:System.Activities.Statements.InvokeMethod.Result%2A> property and a generic version of the <!--zz <xref:System.Activities.Statements.InvokeMethod%601> -->[<code>System.Activities.Statements.InvokeMethod\`1</code>](https://msdn.microsoft.com/library/dd647677.aspx) activity where the return value is returned through the <!--zz <xref:System.Activities.Statements.InvokeMethod.Result%601.Result%2A> -->[<code>System.Activities.Statements.InvokeMethod\`1.Result</code>](https://msdn.microsoft.com/library/dd987724.aspx) property of type `TResult`.</span></span> 
  
 <span data-ttu-id="15ac0-106">このサンプルでは、さまざまな型のメソッドの呼び出し方法を示します。</span><span class="sxs-lookup"><span data-stu-id="15ac0-106">This sample demonstrates how to call various method types.</span></span> <span data-ttu-id="15ac0-107">次に、このサンプルに示されているメソッドの型の詳細を示します。</span><span class="sxs-lookup"><span data-stu-id="15ac0-107">The following list details the method types demonstrated in this sample:</span></span>  
  
-   <span data-ttu-id="15ac0-108">パラメーターを指定せずにインスタンス メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="15ac0-108">Invoke an instance method without parameters.</span></span>  
  
-   <span data-ttu-id="15ac0-109">2 つのパラメーター (System.String および System.Int32) を指定してインスタンス メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="15ac0-109">Invoke an instance method with two parameters (System.String and System.Int32).</span></span>  
  
-   <span data-ttu-id="15ac0-110">2 つのパラメーター (System.String および System.Int32) と、型 System.String[] のパラメーター配列を指定してインスタンス メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="15ac0-110">Invoke an instance method with two parameters (System.String and System.Int32) and a parameter array of type System.String[].</span></span>  
  
-   <span data-ttu-id="15ac0-111">2 つのパラメーター (2 つの System.Int32 数値) および System.Int32 型の結果を指定してインスタンス メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="15ac0-111">Invoke an instance method with two parameters (two System.Int32 numbers) and a result of type System.Int32.</span></span>  
  
     <span data-ttu-id="15ac0-112">戻り値は変数にバインドされ、<xref:System.Activities.Statements.WriteLine> アクティビティを使用してコンソールに出力されます。</span><span class="sxs-lookup"><span data-stu-id="15ac0-112">The return value is bound to a variable and printed to the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
-   <span data-ttu-id="15ac0-113">2 つのパラメーター (System.String および System.Int32) を指定して静的メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="15ac0-113">Invoke a static method with two parameters (System.String and System.Int32).</span></span>  
  
-   <span data-ttu-id="15ac0-114">1 つのジェネリック パラメーター (System.String) を指定してインスタンス メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="15ac0-114">Invoke an instance method with one generic parameter (System.String).</span></span>  
  
-   <span data-ttu-id="15ac0-115">2 つのジェネリック パラメーター (System.String および System.Int32) を指定して静的メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="15ac0-115">Invoke a static method with two generic parameters (System.String and System.Int32).</span></span>  
  
-   <span data-ttu-id="15ac0-116">参照渡しされる 1 つのパラメーター (System.String) を持つインスタンス メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="15ac0-116">Invoke an instance method that has one parameter passed by reference (System.String).</span></span>  
  
     <span data-ttu-id="15ac0-117">参照されているパラメーターは変数にバインドされ、<xref:System.Activities.Statements.WriteLine> アクティビティを使用してコンソールに出力されます。</span><span class="sxs-lookup"><span data-stu-id="15ac0-117">The referenced parameter is bound to a variable and printed to the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
-   <span data-ttu-id="15ac0-118">非同期インスタンス メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="15ac0-118">Invoke an asynchronous instance method.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="15ac0-119">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="15ac0-119">To use this sample</span></span>  
  
1.  <span data-ttu-id="15ac0-120">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、InvokeMethodUsage.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="15ac0-120">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file.</span></span>  
  
2.  <span data-ttu-id="15ac0-121">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="15ac0-121">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="15ac0-122">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="15ac0-122">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="15ac0-123">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="15ac0-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="15ac0-124">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="15ac0-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="15ac0-125">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="15ac0-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="15ac0-126">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="15ac0-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`