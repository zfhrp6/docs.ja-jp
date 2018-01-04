---
title: "WCF Web HTTP プログラミング モデル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web services programming model [WCF]
- POX
- REST
ms.assetid: 2312a8d3-b66e-4623-ba42-978434300c7f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f008cfe874ae9e38a71eb3cf5d6b2ed4e6cbdf7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-web-http-programming-model"></a><span data-ttu-id="d608b-102">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="d608b-102">WCF Web HTTP Programming Model</span></span>
<span data-ttu-id="d608b-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP プログラミング モデルを使用すると、開発者は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス操作を SOAP 以外のエンドポイントに公開できます。</span><span class="sxs-lookup"><span data-stu-id="d608b-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP Programming Model allows developers to expose [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service operations to non-SOAP endpoints.</span></span> <span data-ttu-id="d608b-104">このセクションのトピックでは、この機能について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="d608b-104">The topics in this section examine the feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d608b-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d608b-105">In This Section</span></span>  
 [<span data-ttu-id="d608b-106">WCF Web HTTP プログラミング モデルの概要</span><span class="sxs-lookup"><span data-stu-id="d608b-106">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)  
 <span data-ttu-id="d608b-107">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP プログラミング モデルの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="d608b-107">Provides an overview of the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP Programming Model.</span></span>  
  
 [<span data-ttu-id="d608b-108">WCF Web HTTP プログラミング オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="d608b-108">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)  
 <span data-ttu-id="d608b-109">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP プログラミング モデルおよびその機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="d608b-109">Discusses the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP Programming Model and how it works.</span></span>  
  
 [<span data-ttu-id="d608b-110">方法 : 基本的な WCF Web HTTP サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="d608b-110">How to: Create a Basic WCF Web HTTP Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
 <span data-ttu-id="d608b-111">SOAP 以外のエンドポイントを公開する基本的なサービスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d608b-111">Describes how to write a basic service that exposes a non-SOAP endpoint.</span></span>  
  
 [<span data-ttu-id="d608b-112">方法 : コントラクトを SOAP クライアントおよび Web クライアントに公開する</span><span class="sxs-lookup"><span data-stu-id="d608b-112">How to: Expose a Contract to SOAP and Web Clients</span></span>](../../../../docs/framework/wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md)  
 <span data-ttu-id="d608b-113">SOAP クライアントと SOAP 以外のクライアントの両方に同じコントラクトを公開する基本的なサービスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d608b-113">Describes how to write a basic service that exposes the same contract to both SOAP and non-SOAP clients.</span></span>  
  
 [<span data-ttu-id="d608b-114">UriTemplate と UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="d608b-114">UriTemplate and UriTemplateTable</span></span>](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
 <span data-ttu-id="d608b-115"><xref:System.UriTemplate> および <xref:System.UriTemplateTable> を使用して URI を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d608b-115">Describes how to control URIs using <xref:System.UriTemplate> and <xref:System.UriTemplateTable>.</span></span>  
  
 [<span data-ttu-id="d608b-116">WCF WEB HTTP サービスのキャッシュ サポート</span><span class="sxs-lookup"><span data-stu-id="d608b-116">Caching Support for WCF Web HTTP Services</span></span>](../../../../docs/framework/wcf/feature-details/caching-support-for-wcf-web-http-services.md)  
 <span data-ttu-id="d608b-117">WCF Web HTTP サービスのキャッシュ動作を指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d608b-117">Describes how to specify caching behavior for a WCF Web HTTP service.</span></span>  
  
 [<span data-ttu-id="d608b-118">WCF Web HTTP 形式</span><span class="sxs-lookup"><span data-stu-id="d608b-118">WCF Web HTTP Formatting</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)  
 <span data-ttu-id="d608b-119">WCF Web HTTP サービスからの応答の形式を指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d608b-119">Describes how to specify the format of the response from a WCF Web HTTP service.</span></span>  
  
 [<span data-ttu-id="d608b-120">WCF Web HTTP エラー処理</span><span class="sxs-lookup"><span data-stu-id="d608b-120">WCF Web HTTP Error Handling</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-error-handling.md)  
 <span data-ttu-id="d608b-121">HTTP 状態コードやその他のユーザー定義のエラー データを含むエラーを WCF Web クライアントに返す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d608b-121">Describes how to return errors to WCF Web clients including HTTP status codes and additional user-defined error data.</span></span>  
  
 [<span data-ttu-id="d608b-122">WCF サービスからの REST スタイル サービスの呼び出し</span><span class="sxs-lookup"><span data-stu-id="d608b-122">Calling a REST-style service from a WCF service</span></span>](../../../../docs/framework/wcf/feature-details/calling-a-rest-style-service-from-a-wcf-service.md)  
 <span data-ttu-id="d608b-123">WCF サービス内から REST スタイルのサービスを呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d608b-123">Describes how to call a REST-style service from inside a WCF service.</span></span>
