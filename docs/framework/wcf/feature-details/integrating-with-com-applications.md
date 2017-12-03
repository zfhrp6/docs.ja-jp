---
title: "COM アプリケーションとの統合"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, COM integration
- COM [WCF], Windows Communication Foundation integration
- WCF, reusing code
- Windows Communication Foundation, reusing code
- COM [WCF]
- WCF, COM integration
ms.assetid: c98bda3e-6779-419e-8e6d-9aa94053026d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bfe452b41c39598e237633490d09cd267fda04ec
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="11546-102">COM アプリケーションとの統合</span><span class="sxs-lookup"><span data-stu-id="11546-102">Integrating with COM Applications</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="11546-103"> サービスは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス モニカーを使用することによって既存のコードに直接統合できます。</span><span class="sxs-lookup"><span data-stu-id="11546-103"> services can be integrated directly into your existing code by using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker.</span></span> <span data-ttu-id="11546-104">サービス モニカーは Office VBA、Visual Basic 6.0、または Visual C++ 6.0 などの幅広い COM ベースの開発環境で使用可能です。</span><span class="sxs-lookup"><span data-stu-id="11546-104">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="11546-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="11546-105">In This Section</span></span>  
 [<span data-ttu-id="11546-106">COM アプリケーションの概要との統合</span><span class="sxs-lookup"><span data-stu-id="11546-106">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)  
 <span data-ttu-id="11546-107">統合プロセスの主要部分の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="11546-107">Gives an overview of the major parts of the integration process.</span></span>  
  
 [<span data-ttu-id="11546-108">方法: 登録し、サービス モニカーの構成</span><span class="sxs-lookup"><span data-stu-id="11546-108">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)  
 <span data-ttu-id="11546-109">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス モニカーを COM アプリケーションで使用するには、必要な属性型を COM に登録し、必要なバインディング構成を使用して COM アプリケーションとモニカーを構成します。</span><span class="sxs-lookup"><span data-stu-id="11546-109">To use the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker within a COM application, register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
 [<span data-ttu-id="11546-110">方法: 登録しないと Windows Communication Foundation サービス モニカーを使用します。</span><span class="sxs-lookup"><span data-stu-id="11546-110">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 <span data-ttu-id="11546-111">WSDL (Web Services Definition Language) ドキュメントの形式で、または WS-MetadataExchange エンドポイントからコントラクトの定義を取得する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="11546-111">Explains how to obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document or from a WS-MetadataExchange endpoint.</span></span>  
  
 [<span data-ttu-id="11546-112">方法: WSDL コントラクトと共にサービス モニカーを使用</span><span class="sxs-lookup"><span data-stu-id="11546-112">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 <span data-ttu-id="11546-113">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSDL モニカーを使用して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のサンプルを呼び出す方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="11546-113">Describes how to call a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sample using a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSDL moniker.</span></span>  
  
 [<span data-ttu-id="11546-114">方法: Metadata Exchange コントラクトと共にサービス モニカーを使用</span><span class="sxs-lookup"><span data-stu-id="11546-114">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 <span data-ttu-id="11546-115">Mex エンドポイントを指定する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] モニカーを使用して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のサンプルを呼び出す方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="11546-115">Describes how to call a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sample using a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker that specifies a Mex endpoint.</span></span>  
  
 [<span data-ttu-id="11546-116">方法: チャネルのセキュリティ資格情報の指定</span><span class="sxs-lookup"><span data-stu-id="11546-116">How to: Specify Channel Security Credentials</span></span>](../../../../docs/framework/wcf/feature-details/how-to-specify-channel-security-credentials.md)  
 <span data-ttu-id="11546-117">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス モニカーは、チャネル資格情報を指定するためのさまざまな代替メソッドの使用を許可する `IChannelCredentials` インターフェイスをサポートします。</span><span class="sxs-lookup"><span data-stu-id="11546-117">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker supports the `IChannelCredentials` interface that allows a range of alternate methods for specifying channel credentials.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="11546-118">参照</span><span class="sxs-lookup"><span data-stu-id="11546-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="11546-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="11546-119">See Also</span></span>  
 [<span data-ttu-id="11546-120">COM + アプリケーションとの統合</span><span class="sxs-lookup"><span data-stu-id="11546-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
