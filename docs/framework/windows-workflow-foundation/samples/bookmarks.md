---
title: Bookmarks2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 035fadb2-49fa-4ac7-b398-daf138f66e87
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3b06ab0e3b80fded2abf3a27d9cf08e499267902
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="bookmarks"></a><span data-ttu-id="ae82b-102">ブックマーク</span><span class="sxs-lookup"><span data-stu-id="ae82b-102">Bookmarks</span></span>
<span data-ttu-id="ae82b-103">このサンプルでは、外部入力を受信するためのブックマークを作成するカスタム アクティビティを記述する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ae82b-103">This sample demonstrates how to write a custom activity that creates a bookmark to receive external input.</span></span> <span data-ttu-id="ae82b-104">また、このサンプルでは、基本的なコンソール アプリケーションによってワークフローでカスタム アクティビティを使用し、実行中のワークフロー インスタンスに関連付けられたブックマークを探索および再開する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ae82b-104">The sample also includes a basic console application that uses the custom activity in a workflow and shows how to discover and resume bookmarks associated with a running workflow instance.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ae82b-105">ブックマークを参照してください[ブックマーク](../../../../docs/framework/windows-workflow-foundation/bookmarks.md)です。</span><span class="sxs-lookup"><span data-stu-id="ae82b-105"> bookmarks, see [Bookmarks](../../../../docs/framework/windows-workflow-foundation/bookmarks.md).</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ae82b-106">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="ae82b-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ae82b-107">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で Bookmarks.sln サンプル ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="ae82b-107">Open the Bookmarks.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="ae82b-108">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="ae82b-108">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="ae82b-109">サンプルを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="ae82b-109">To run the sample, press CTRLl + F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ae82b-110">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="ae82b-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ae82b-111">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ae82b-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ae82b-112">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="ae82b-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ae82b-113">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="ae82b-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CodeBodied\Bookmarks`