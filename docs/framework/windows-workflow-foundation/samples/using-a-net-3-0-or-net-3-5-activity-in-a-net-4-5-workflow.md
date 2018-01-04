---
title: ".NET Framework 4.5 ワークフローでの .NET Framework 3.0 または .NET Framework 3.5 アクティビティの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c53fd4c-5dd0-4fb4-ab6b-111302629548
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 05660c3dc91d9d7cdba506670f62711752d7d100
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="using-a-net-framework-30-or-net-framework-35-activity-in-a-net-framework-45-workflow"></a><span data-ttu-id="6bf31-102">.NET Framework 4.5 ワークフローでの .NET Framework 3.0 または .NET Framework 3.5 アクティビティの使用</span><span class="sxs-lookup"><span data-stu-id="6bf31-102">Using a .NET Framework 3.0 or .NET Framework 3.5 Activity in a .NET Framework 4.5 Workflow</span></span>
<span data-ttu-id="6bf31-103"><xref:System.Activities.Statements.Interop> アクティビティでは、[!INCLUDE[wf](../../../../includes/wf-md.md)] ワークフロー内で .NET Framework 3.0 [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] アクティビティを実行できます。</span><span class="sxs-lookup"><span data-stu-id="6bf31-103">The <xref:System.Activities.Statements.Interop> activity allows you to run a .NET Framework 3.0 [!INCLUDE[wf](../../../../includes/wf-md.md)] activity within a [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] workflow.</span></span> <span data-ttu-id="6bf31-104">このサンプルでは、<xref:System.Activities.Statements.Interop> アクティビティを使用して、文字列をカスタムの [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] アクティビティに引数として渡す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6bf31-104">This sample demonstrates how to use the <xref:System.Activities.Statements.Interop> activity to pass a string as an argument to a custom [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] activity.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="6bf31-105">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="6bf31-105">To use this sample</span></span>  
  
1.  <span data-ttu-id="6bf31-106">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、SimpleInterop.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="6bf31-106">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the SimpleInterop.sln solution file.</span></span>  
  
2.  <span data-ttu-id="6bf31-107">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="6bf31-107">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="6bf31-108">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="6bf31-108">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6bf31-109">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="6bf31-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6bf31-110">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="6bf31-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6bf31-111">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="6bf31-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6bf31-112">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="6bf31-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\SimpleInterop`  
  
## <a name="see-also"></a><span data-ttu-id="6bf31-113">参照</span><span class="sxs-lookup"><span data-stu-id="6bf31-113">See Also</span></span>
