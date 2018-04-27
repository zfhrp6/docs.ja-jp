---
title: External Data Exchange での Interop の使用
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96f6fe26-5305-494f-9119-7748e0c4b3fa
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4acec4209ddadd181774ae754cb1d6b94a21685e
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="using-interop-with-external-data-exchange"></a><span data-ttu-id="1462b-102">External Data Exchange での Interop の使用</span><span class="sxs-lookup"><span data-stu-id="1462b-102">Using Interop with External Data Exchange</span></span>
<span data-ttu-id="1462b-103"><xref:System.Activities.Statements.Interop>から Windows Workflow Foundation (WF) にアクティビティを実行するアクティビティを使用する[!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]と[!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)](WF3)、および Windows Workflow Foundation の内のワークフロー [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF4)。</span><span class="sxs-lookup"><span data-stu-id="1462b-103">The <xref:System.Activities.Statements.Interop> activity can be used to execute activities from Windows Workflow Foundation (WF) in [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] and [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF3), and workflows within Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF4).</span></span> <span data-ttu-id="1462b-104">このサンプルは、WF4 ワークフロー サービスの <xref:System.Workflow.Activities.ExternalDataExchangeService> アクティビティを使用して、<xref:System.Activities.Statements.Interop> (およびメソッドを呼び出してイベントを処理するための対応するカスタム アクティビティ) を使用する WF3 ワークフローを設定および実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1462b-104">This sample shows how to configure and run a WF3 workflow that uses <xref:System.Workflow.Activities.ExternalDataExchangeService> (and corresponding custom activities for calling methods and handling events) by using the <xref:System.Activities.Statements.Interop> activity in a WF4 workflow service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1462b-105">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="1462b-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1462b-106">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1462b-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1462b-107">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="1462b-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1462b-108">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="1462b-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\ExternalDataExchange`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="1462b-109">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="1462b-109">To use this sample</span></span>  
  
1.  <span data-ttu-id="1462b-110">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で ExternalDataExchange.sln ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="1462b-110">Open the ExternalDataExchange.sln file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="1462b-111">サンプルをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="1462b-111">To build the sample, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="1462b-112">サンプルを実行するには、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="1462b-112">To run the sample, press F5.</span></span>
