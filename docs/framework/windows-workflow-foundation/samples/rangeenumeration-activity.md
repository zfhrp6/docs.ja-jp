---
title: "RangeEnumeration アクティビティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca5b78f4-94fa-4aa7-830d-26039ac422c8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7dc793d57718dbc68f304d3eb5031a9fa96b00cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="rangeenumeration-activity"></a><span data-ttu-id="2ba6a-102">RangeEnumeration アクティビティ</span><span class="sxs-lookup"><span data-stu-id="2ba6a-102">RangeEnumeration Activity</span></span>
<span data-ttu-id="2ba6a-103">このサンプルでは、数値のコレクションを反復処理するカスタム アクティビティを作成する方法を示します。次の表で、このサンプルに含まれるメイン ファイルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2ba6a-103">This sample demonstrates how to create a custom activity that iterates over a collection of numbers.The following table details the main files included in the sample.</span></span>  
  
|<span data-ttu-id="2ba6a-104">ファイル名</span><span class="sxs-lookup"><span data-stu-id="2ba6a-104">File name</span></span>|<span data-ttu-id="2ba6a-105">説明</span><span class="sxs-lookup"><span data-stu-id="2ba6a-105">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2ba6a-106">RangeEnumeration.cs</span><span class="sxs-lookup"><span data-stu-id="2ba6a-106">RangeEnumeration.cs</span></span>|<span data-ttu-id="2ba6a-107">`RangeEnumeration` クラスをオーバーライドし、一連の数値をループする <xref:System.Activities.NativeActivity> というカスタム アクティビティを定義します。</span><span class="sxs-lookup"><span data-stu-id="2ba6a-107">Defines a custom activity named `RangeEnumeration` that overrides the <xref:System.Activities.NativeActivity> class and loops through a series of numbers.</span></span>|  
|<span data-ttu-id="2ba6a-108">RangeEnumerationSample.cs</span><span class="sxs-lookup"><span data-stu-id="2ba6a-108">RangeEnumerationSample.cs</span></span>|<span data-ttu-id="2ba6a-109">`RangeEnumeration` アクティビティを使用して数値のコレクションを反復処理するクライアント アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="2ba6a-109">A client application that uses the `RangeEnumeration` activity to iterate over a collection of numbers.</span></span>|  
  
 <span data-ttu-id="2ba6a-110">次の表で、`RangeEnumeration` アクティビティのプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2ba6a-110">The following table details the properties of the `RangeEnumeration` activity.</span></span>  
  
|<span data-ttu-id="2ba6a-111">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2ba6a-111">Property</span></span>|<span data-ttu-id="2ba6a-112">説明</span><span class="sxs-lookup"><span data-stu-id="2ba6a-112">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="2ba6a-113">[開始]</span><span class="sxs-lookup"><span data-stu-id="2ba6a-113">Start</span></span>|<span data-ttu-id="2ba6a-114">ループの開始位置を示す整数。</span><span class="sxs-lookup"><span data-stu-id="2ba6a-114">The integer to start the loop from.</span></span>|  
|<span data-ttu-id="2ba6a-115">Stop</span><span class="sxs-lookup"><span data-stu-id="2ba6a-115">Stop</span></span>|<span data-ttu-id="2ba6a-116">ループの停止位置を示す整数。</span><span class="sxs-lookup"><span data-stu-id="2ba6a-116">The integer to stop the loop at.</span></span>|  
|<span data-ttu-id="2ba6a-117">手順</span><span class="sxs-lookup"><span data-stu-id="2ba6a-117">Step</span></span>|<span data-ttu-id="2ba6a-118">各反復処理の反復回数を指定します。</span><span class="sxs-lookup"><span data-stu-id="2ba6a-118">Specifies how much to iterate each time.</span></span>|  
|<span data-ttu-id="2ba6a-119">Body</span><span class="sxs-lookup"><span data-stu-id="2ba6a-119">Body</span></span>|<span data-ttu-id="2ba6a-120">各反復処理中に実行するコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="2ba6a-120">Specifies the code to execute during each iteration.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="2ba6a-121">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="2ba6a-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="2ba6a-122">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、RangeEnumeration.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="2ba6a-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RangeEnumeration.sln solution file.</span></span>  
  
2.  <span data-ttu-id="2ba6a-123">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2ba6a-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="2ba6a-124">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2ba6a-124">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2ba6a-125">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="2ba6a-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2ba6a-126">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2ba6a-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2ba6a-127">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="2ba6a-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2ba6a-128">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="2ba6a-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`