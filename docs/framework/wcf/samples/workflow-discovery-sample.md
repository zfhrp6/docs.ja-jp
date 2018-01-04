---
title: "ワークフローの探索のサンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3cf150562beaacb56596b90e1680adca97dd24a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-discovery-sample"></a><span data-ttu-id="6dda7-102">ワークフローの探索のサンプル</span><span class="sxs-lookup"><span data-stu-id="6dda7-102">Workflow Discovery Sample</span></span>
<span data-ttu-id="6dda7-103">このサンプルでは、ワークフロー サービスを探索可能にする方法と、特定のサービスを検索するカスタム コード アクティビティを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6dda7-103">This sample demonstrates how to make a workflow service discoverable and how to author a custom code activity that searches for a particular service.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="6dda7-104">使用例</span><span class="sxs-lookup"><span data-stu-id="6dda7-104">Demonstrates</span></span>  
 <span data-ttu-id="6dda7-105">探索検索アクティビティとワークフローの使用方法</span><span class="sxs-lookup"><span data-stu-id="6dda7-105">Discovery Find Activity and Workflow Usage</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="6dda7-106">説明</span><span class="sxs-lookup"><span data-stu-id="6dda7-106">Discussion</span></span>  
 <span data-ttu-id="6dda7-107">サンプルの最初の部分では、構成を使用してワークフロー サービスを探索可能にしています。</span><span class="sxs-lookup"><span data-stu-id="6dda7-107">In the first part of the sample, a workflow service is made discoverable using configuration.</span></span> <span data-ttu-id="6dda7-108">また、カスタム メタデータ (スコープなど) と共に構成を使用すると、サービスを適切に適用することができます。</span><span class="sxs-lookup"><span data-stu-id="6dda7-108">Configuration can also be used to apply the service appropriately with custom metadata (such as scopes).</span></span> <span data-ttu-id="6dda7-109">このサンプルは、クライアントでカスタム コード アクティビティを使用します。カスタム コード アクティビティは、探索を使用して、特定のコントラクトに一致するサービスを検索します。</span><span class="sxs-lookup"><span data-stu-id="6dda7-109">On the client, the sample uses a custom code activity, which uses Discovery to search for a service matching a particular contract.</span></span> <span data-ttu-id="6dda7-110">コード アクティビティは URI を出力します。この URI は、後で送信アクティビティで使用されます。</span><span class="sxs-lookup"><span data-stu-id="6dda7-110">The code activity outputs a URI, which is later used by a send activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6dda7-111">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="6dda7-111">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="6dda7-112">このサンプルを実行する適切な URL Acl を持つ必要がある HTTP エンドポイントを使用して (を参照してください[を構成する HTTP および HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353)詳細)。</span><span class="sxs-lookup"><span data-stu-id="6dda7-112">This sample uses HTTP endpoints, which must have proper URL ACLs to run (see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details).</span></span> <span data-ttu-id="6dda7-113">権限のレベルが高いコマンド プロンプトで次のコマンドを実行すると、適切な ACL が追加されます。</span><span class="sxs-lookup"><span data-stu-id="6dda7-113">Executing the following command at an elevated command prompt should add the appropriate ACLs.</span></span> <span data-ttu-id="6dda7-114">使用中のシェルで変数の形式を使用できない場合は、代わりに、ドメインとユーザー名を引数に指定してください。</span><span class="sxs-lookup"><span data-stu-id="6dda7-114">Substitute your Domain and Username for the following arguments if your shell does not understand the variable format.</span></span>  
  
     <span data-ttu-id="6dda7-115">**netsh http 追加 urlacl url = http://+: 8000/ユーザー ドメイン % =\\%username%**</span><span class="sxs-lookup"><span data-stu-id="6dda7-115">**netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\\%UserName%**</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6dda7-116">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="6dda7-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6dda7-117">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="6dda7-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6dda7-118">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="6dda7-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6dda7-119">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="6dda7-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
