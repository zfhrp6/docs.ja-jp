---
title: "WCF セキュリティの暗号化方式の指定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 8b07b23f4428053964fa33150c4300645242f918
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="c6311-102">WCF セキュリティの暗号化方式の指定</span><span class="sxs-lookup"><span data-stu-id="c6311-102">Cryptographic Agility in WCF Security</span></span>
<span data-ttu-id="c6311-103">このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] クライアントおよびサービスで迅速な暗号化実装を提供するために標準またはカスタム アルゴリズムで指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c6311-103">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and service.</span></span> <span data-ttu-id="c6311-104">サンプルは、以下のプロジェクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="c6311-104">The sample is composed of the following projects:</span></span>  
  
 <span data-ttu-id="c6311-105">サービス</span><span class="sxs-lookup"><span data-stu-id="c6311-105">Service</span></span>  
 <span data-ttu-id="c6311-106">これは、自己ホスト型[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]を実装するサービス、`ICalculator`インターフェイスを使用してエンドポイントを保護し、<<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> セキュリティで保護されたセッションと信頼できるセッションは無効にします。</span><span class="sxs-lookup"><span data-stu-id="c6311-106">This is a self-hosted [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that implements the `ICalculator` interface and secures the endpoint using the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> with secure session and reliable session disabled.</span></span> <span data-ttu-id="c6311-107">このサービスは、カスタム `SecurityAlgorithmSuite` クラスを定義し、メッセージのセキュリティを確保するために使用される暗号化アルゴリズムを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6311-107">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>  
  
 <span data-ttu-id="c6311-108">Client</span><span class="sxs-lookup"><span data-stu-id="c6311-108">Client</span></span>  
 <span data-ttu-id="c6311-109">これは、認証が成功した後にサービスにアクセスする [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントです。</span><span class="sxs-lookup"><span data-stu-id="c6311-109">This is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]client that accesses the service after successful authentication.</span></span> <span data-ttu-id="c6311-110">このクライアントは、`ICalculator` インターフェイスによって公開され、サービスによって実装される操作を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c6311-110">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="c6311-111">このクライアントも、同じカスタム `SecurityAlgorithmSuite` クラスを定義し、メッセージのセキュリティを確保するために使用される暗号化アルゴリズムを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6311-111">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="c6311-112">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="c6311-112">To use this sample</span></span>  
  
1.  <span data-ttu-id="c6311-113">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] で CryptoAgility.sln ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="c6311-113">Open the CryptoAgility.sln solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="c6311-114">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="c6311-114">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="c6311-115">開いている[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]\WCF\Basic\Security\CryptoAgility\Service\bin ディレクトリに移動し、service.exe を右クリックして、service.exe ファイルを管理者特権で実行**管理者として実行**です。</span><span class="sxs-lookup"><span data-stu-id="c6311-115">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>  
  
4.  <span data-ttu-id="c6311-116">\WCF\Basic\Security\CryptoAgility\Client\bin ディレクトリに移動して、client.exe ファイルを通常の方法で実行します。</span><span class="sxs-lookup"><span data-stu-id="c6311-116">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c6311-117">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="c6311-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c6311-118">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c6311-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c6311-119">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="c6311-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c6311-120">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c6311-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## <a name="see-also"></a><span data-ttu-id="c6311-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6311-121">See Also</span></span>  
 [<span data-ttu-id="c6311-122">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c6311-122">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
