---
title: AJAX の統合と JSON のサポート
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0d62da8cf67fb8f996f341018c39146b51e308c3
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="bd316-102">AJAX の統合と JSON のサポート</span><span class="sxs-lookup"><span data-stu-id="bd316-102">AJAX Integration and JSON Support</span></span>
<span data-ttu-id="bd316-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] が ASP.NET AJAX (Asynchronous JavaScript and XML) と JSON (JavaScript Object Notation) データ形式をサポートするため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは AJAX クライアントに操作を公開できます。</span><span class="sxs-lookup"><span data-stu-id="bd316-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services to expose operations to AJAX clients.</span></span> <span data-ttu-id="bd316-104">AJAX クライアントは、JavaScript コードを実行し、HTTP 要求を使用してこのような [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスにアクセスする Web ページです。</span><span class="sxs-lookup"><span data-stu-id="bd316-104">AJAX clients are Web pages running JavaScript code and accessing these [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services using HTTP requests.</span></span> <span data-ttu-id="bd316-105">このセクションのトピックでは、このサポートと実装方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bd316-105">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 <span data-ttu-id="bd316-106">詳細については、ASP.NET AJAX との統合を ASP.NET 2.0 では、次を参照してください。 [ASP.NET AJAX 概要](http://go.microsoft.com/fwlink/?LinkId=96725)です。</span><span class="sxs-lookup"><span data-stu-id="bd316-106">For more information about ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](http://go.microsoft.com/fwlink/?LinkId=96725).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bd316-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="bd316-107">In This Section</span></span>  
 [<span data-ttu-id="bd316-108">ASP.NET AJAX 用の WCF サービスの作成</span><span class="sxs-lookup"><span data-stu-id="bd316-108">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="bd316-109">構成によって、または、自動的に AJAX エンドポイントを構成するサービス ホストを生成するようにカスタマイズされたサービス ホスト ファクトリを使用することによって適切な AJAX エンドポイントを追加することで、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを AJAX クライアントに公開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bd316-109">Describes how an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="bd316-110">ASP.NET を使用せずに WCF AJAX サービスを作成する方法</span><span class="sxs-lookup"><span data-stu-id="bd316-110">Creating WCF AJAX Services without ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="bd316-111">ASP.NET を使用しないで [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bd316-111">Describes how to create an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="bd316-112">JSON などのデータ転送形式のサポート</span><span class="sxs-lookup"><span data-stu-id="bd316-112">Support for JSON and Other Data Transfer Formats</span></span>](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="bd316-113">ASP.NET AJAX サービスとのメッセージングで、XML の代わりに一般に使用される JSON 形式のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="bd316-113">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="bd316-114">方法 : AJAX 対応 ASP.NET Web サービスを WCF に移行する</span><span class="sxs-lookup"><span data-stu-id="bd316-114">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="bd316-115">AJAX 対応の ASP.NET Web サービスを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web サービスに移行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bd316-115">Describes how to migrate an AJAX-enabled ASP.NET Web service to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd316-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="bd316-116">See Also</span></span>  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>  
 [<span data-ttu-id="bd316-117">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="bd316-117">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
