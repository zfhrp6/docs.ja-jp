---
title: "External Data Exchange での Interop の使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96f6fe26-5305-494f-9119-7748e0c4b3fa
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f62d5a468e3730ec4f636d57cb9d0c6c3973a8d3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="using-interop-with-external-data-exchange"></a><span data-ttu-id="40bf4-102">External Data Exchange での Interop の使用</span><span class="sxs-lookup"><span data-stu-id="40bf4-102">Using Interop with External Data Exchange</span></span>
<span data-ttu-id="40bf4-103"><xref:System.Activities.Statements.Interop> アクティビティを使用して、[!INCLUDE[wf](../../../../includes/wf-md.md)] および [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] (WF3) の [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] からアクティビティを実行し、[!INCLUDE[wf2](../../../../includes/wf2-md.md)] (WF4) の [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] からワークフローを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="40bf4-103">The <xref:System.Activities.Statements.Interop> activity can be used to execute activities from [!INCLUDE[wf](../../../../includes/wf-md.md)] in [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] and [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF3), and workflows within [!INCLUDE[wf2](../../../../includes/wf2-md.md)] in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF4).</span></span> <span data-ttu-id="40bf4-104">このサンプルは、WF4 ワークフロー サービスの <xref:System.Workflow.Activities.ExternalDataExchangeService> アクティビティを使用して、<xref:System.Activities.Statements.Interop> (およびメソッドを呼び出してイベントを処理するための対応するカスタム アクティビティ) を使用する WF3 ワークフローを設定および実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="40bf4-104">This sample shows how to configure and run a WF3 workflow that uses <xref:System.Workflow.Activities.ExternalDataExchangeService> (and corresponding custom activities for calling methods and handling events) by using the <xref:System.Activities.Statements.Interop> activity in a WF4 workflow service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="40bf4-105">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="40bf4-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="40bf4-106">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="40bf4-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="40bf4-107">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="40bf4-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="40bf4-108">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="40bf4-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\ExternalDataExchange`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="40bf4-109">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="40bf4-109">To use this sample</span></span>  
  
1.  <span data-ttu-id="40bf4-110">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で ExternalDataExchange.sln ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="40bf4-110">Open the ExternalDataExchange.sln file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="40bf4-111">サンプルをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="40bf4-111">To build the sample, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="40bf4-112">サンプルを実行するには、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="40bf4-112">To run the sample, press F5.</span></span>
