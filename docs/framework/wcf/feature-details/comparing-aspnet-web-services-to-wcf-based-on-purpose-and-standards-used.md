---
title: "使用目的と使用標準に基づく ASP.NET Web サービスと WCF との比較"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d3890278-fa9b-4902-91ea-8da73b7143cc
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c6dc444b8a4c19dbe486eb904e0f054e05f6fe6a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used"></a><span data-ttu-id="52378-102">使用目的と使用標準に基づく ASP.NET Web サービスと WCF との比較</span><span class="sxs-lookup"><span data-stu-id="52378-102">Comparing ASP.NET Web Services to WCF Based on Purpose and Standards Used</span></span>
<span data-ttu-id="52378-103">ASP.NET Web サービスは、HTTP 上で SOAP (Simple Object Access Protocol) を使用してメッセージを送受信するアプリケーションを構築するために開発されました。</span><span class="sxs-lookup"><span data-stu-id="52378-103">ASP.NET Web services was developed for building applications that send and receive messages by using the Simple Object Access Protocol (SOAP) over HTTP.</span></span> <span data-ttu-id="52378-104">メッセージ構造は XML スキーマを使用して定義できます。また、.NET Framework オブジェクトに対するメッセージのシリアル化を容易にするツールも提供されています。</span><span class="sxs-lookup"><span data-stu-id="52378-104">The structure of the messages can be defined using an XML Schema, and a tool is provided to facilitate serializing the messages to and from .NET Framework objects.</span></span> <span data-ttu-id="52378-105">このテクノロジを使用すると、Web サービス記述言語 (WSDL) で Web サービスを記述するメタデータが自動で生成されます。また、WSDL から Web サービス用のクライアントを生成する別のツールも用意されています。</span><span class="sxs-lookup"><span data-stu-id="52378-105">The technology can automatically generate metadata to describe Web services in the Web Services Description Language (WSDL), and a second tool is provided for generating clients for Web services from the WSDL.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="52378-106"> を使用すると、.NET Framework アプリケーションで他のソフトウェア エンティティとメッセージを交換できます。</span><span class="sxs-lookup"><span data-stu-id="52378-106"> is for enabling .NET Framework applications to exchange messages with other software entities.</span></span> <span data-ttu-id="52378-107">既定では SOAP が使用されますが、任意の形式のメッセージを使用でき、任意のトランスポート プロトコルを使用してメッセージを伝達できます。</span><span class="sxs-lookup"><span data-stu-id="52378-107">SOAP is used by default, but the messages can be in any format, and conveyed by using any transport protocol.</span></span> <span data-ttu-id="52378-108">メッセージ構造は XML スキーマを使用して定義できます。また、.NET Framework オブジェクトに対するメッセージをシリアル化するさまざまなオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="52378-108">The structure of the messages can be defined using an XML Schema, and there are various options for serializing the messages to and from .NET Framework objects.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="52378-109"> を使用すると、このテクノロジで構築されたアプリケーションを WSDL で記述するメタデータが自動で生成されます。また、WSDL からこのようなアプリケーション用のクライアントを生成するツールも用意されています。</span><span class="sxs-lookup"><span data-stu-id="52378-109"> can automatically generate metadata to describe applications built using the technology in WSDL, and it also provides a tool for generating clients for those applications from the WSDL.</span></span>  
  
 <span data-ttu-id="52378-110">ASP.NET Web サービスによってサポートされる標準については、『 [ASP.NET を使用して作成した XML Web サービス](http://go.microsoft.com/fwlink/?LinkId=94872)です。</span><span class="sxs-lookup"><span data-stu-id="52378-110">The standards supported by ASP.NET Web services are documented in [XML Web Services Created Using ASP.NET](http://go.microsoft.com/fwlink/?LinkId=94872).</span></span> <span data-ttu-id="52378-111">サポートされる標準のより詳細なリスト[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]に記載されて[システム指定の相互運用性バインディングでサポートされる Web サービス プロトコル](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)です。</span><span class="sxs-lookup"><span data-stu-id="52378-111">The more extensive list of standards supported by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are listed at [Web Services Protocols Supported by System-Provided Interoperability Bindings](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52378-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="52378-112">See Also</span></span>  
 [<span data-ttu-id="52378-113">開発に基づいた WCF を ASP.NET Web サービスとの比較</span><span class="sxs-lookup"><span data-stu-id="52378-113">Comparing ASP.NET Web Services to WCF Based on Development</span></span>](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
