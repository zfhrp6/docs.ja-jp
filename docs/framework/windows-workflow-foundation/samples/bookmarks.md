---
title: Bookmarks2
ms.date: 03/30/2017
ms.assetid: 035fadb2-49fa-4ac7-b398-daf138f66e87
ms.openlocfilehash: 61abc1d1a5084018511975e27fa96311c168eb69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514161"
---
# <a name="bookmarks"></a><span data-ttu-id="43507-102">ブックマーク</span><span class="sxs-lookup"><span data-stu-id="43507-102">Bookmarks</span></span>
<span data-ttu-id="43507-103">このサンプルでは、外部入力を受信するためのブックマークを作成するカスタム アクティビティを記述する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="43507-103">This sample demonstrates how to write a custom activity that creates a bookmark to receive external input.</span></span> <span data-ttu-id="43507-104">また、このサンプルでは、基本的なコンソール アプリケーションによってワークフローでカスタム アクティビティを使用し、実行中のワークフロー インスタンスに関連付けられたブックマークを探索および再開する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="43507-104">The sample also includes a basic console application that uses the custom activity in a workflow and shows how to discover and resume bookmarks associated with a running workflow instance.</span></span> <span data-ttu-id="43507-105">ブックマークの詳細については、次を参照してください。[ブックマーク](../../../../docs/framework/windows-workflow-foundation/bookmarks.md)です。</span><span class="sxs-lookup"><span data-stu-id="43507-105">For more information about bookmarks, see [Bookmarks](../../../../docs/framework/windows-workflow-foundation/bookmarks.md).</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="43507-106">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="43507-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="43507-107">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で Bookmarks.sln サンプル ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="43507-107">Open the Bookmarks.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="43507-108">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="43507-108">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="43507-109">サンプルを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="43507-109">To run the sample, press CTRLl + F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="43507-110">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="43507-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="43507-111">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="43507-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="43507-112">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="43507-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="43507-113">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="43507-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CodeBodied\Bookmarks`