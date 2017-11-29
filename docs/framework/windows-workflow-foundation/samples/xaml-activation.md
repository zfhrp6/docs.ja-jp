---
title: "XAML アクティベーション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 486760e2-bb10-4ed5-8c02-fe7472498d2d
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f513b10c84de968d5a18b800037b512aad90399e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="xaml-activation"></a><span data-ttu-id="8d300-102">XAML アクティベーション</span><span class="sxs-lookup"><span data-stu-id="8d300-102">XAML Activation</span></span>
<span data-ttu-id="8d300-103">このサンプルでは、宣言型ワークフローを IIS でホストする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8d300-103">This sample demonstrates how to host a declarative workflow in IIS.</span></span> <span data-ttu-id="8d300-104">このサンプルは、1 つの操作を持つ、`EchoService` という名前の基本的なワークフローです。</span><span class="sxs-lookup"><span data-stu-id="8d300-104">The sample is a basic workflow called `EchoService` that has one operation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8d300-105">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="8d300-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8d300-106">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8d300-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8d300-107">このディレクトリが存在しない場合は、ダウンロード ページに移動して、すべての [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サンプルおよび [!INCLUDE[wf1](../../../../includes/wf1-md.md)] サンプルをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="8d300-107">If this directory does not exist, go to (download page) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8d300-108">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="8d300-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLActivation`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8d300-109">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="8d300-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="8d300-110">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で XAMLActivation.sln ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="8d300-110">Open the XAMLActivation.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="8d300-111">キーを押して、ソリューションをビルド**f5 キーを押して**です。</span><span class="sxs-lookup"><span data-stu-id="8d300-111">Build the solution by pressing **F5**.</span></span>  
  
3.  <span data-ttu-id="8d300-112">WcfTestClient.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="8d300-112">Run WcfTestClient.exe.</span></span> <span data-ttu-id="8d300-113">コマンド プロンプトで、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="8d300-113">From a command prompt, type in the following:</span></span>  
  
    1.  <span data-ttu-id="8d300-114">cd %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE</span><span class="sxs-lookup"><span data-stu-id="8d300-114">cd %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE</span></span>  
  
    2.  <span data-ttu-id="8d300-115">WcfTestClient.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="8d300-115">Run WcfTestClient.exe.</span></span>  
  
4.  <span data-ttu-id="8d300-116">WcfTestClient.exe でサービスのアドレスを設定します。これを行うには、Ctrl と Shift キーを押しながら A キーを押して、サービス アドレスを http://localhost:56133/Service.xamlx に設定します。</span><span class="sxs-lookup"><span data-stu-id="8d300-116">Set the address of the service on WcfTestClient.exe by pressing CTRL+SHIFT+A and setting the service address to http://localhost:56133/Service.xamlx.</span></span>  
  
5.  <span data-ttu-id="8d300-117">エコー操作を実行してサービスをテストします。</span><span class="sxs-lookup"><span data-stu-id="8d300-117">Perform the echo operation to test the service.</span></span>  
  
6.  <span data-ttu-id="8d300-118">管理者権限で実行したコマンド プロンプトから DeployToIIS.Bat を使用して、IIS にサービスを配置します。</span><span class="sxs-lookup"><span data-stu-id="8d300-118">Deploy the Service in IIS using DeployToIIS.Bat in a command prompt with administrator privileges.</span></span>  
  
7.  <span data-ttu-id="8d300-119">クライアントでサービスのアドレスを http://localhost/XAMLActivation/Service.xamlx に更新し、WcfTestClient.exe を使用してサービスを再度テストします。</span><span class="sxs-lookup"><span data-stu-id="8d300-119">Update the service address in the client to http://localhost/XAMLActivation/Service.xamlx and test the service again using WcfTestClient.exe.</span></span>
