---
title: "メタデータ形式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d250b57282d24780dcdd1e045f18d7528bd86a90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="metadata-formats"></a><span data-ttu-id="71f27-102">メタデータ形式</span><span class="sxs-lookup"><span data-stu-id="71f27-102">Metadata Formats</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="71f27-103"> では、次の表に示すメタデータ形式をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="71f27-103"> supports the metadata formats in the following table.</span></span>  
  
## <a name="metadata-specifications-and-usage"></a><span data-ttu-id="71f27-104">メタデータの仕様と用途</span><span class="sxs-lookup"><span data-stu-id="71f27-104">Metadata Specifications and Usage</span></span>  
  
|<span data-ttu-id="71f27-105">プロトコル</span><span class="sxs-lookup"><span data-stu-id="71f27-105">Protocol</span></span>|<span data-ttu-id="71f27-106">仕様と用途</span><span class="sxs-lookup"><span data-stu-id="71f27-106">Specification and usage</span></span>|  
|--------------|-----------------------------|  
|<span data-ttu-id="71f27-107">WSDL 1.1</span><span class="sxs-lookup"><span data-stu-id="71f27-107">WSDL 1.1</span></span>|[<span data-ttu-id="71f27-108">Web サービス記述言語 (WSDL) 1.1</span><span class="sxs-lookup"><span data-stu-id="71f27-108">Web Services Description Language (WSDL) 1.1</span></span>](http://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="71f27-109"> では、サービスの記述に Web サービス記述言語 (WSDL) を使用します。</span><span class="sxs-lookup"><span data-stu-id="71f27-109"> uses Web Services Description Language (WSDL) to describe services.</span></span>|  
|<span data-ttu-id="71f27-110">XML スキーマ</span><span class="sxs-lookup"><span data-stu-id="71f27-110">XML Schema</span></span>|<span data-ttu-id="71f27-111">[XML Schema Part 2: Datatypes Second Edition](http://go.microsoft.com/fwlink/?LinkId=94861)と[XML Schema Part 1: Structures Second Edition](http://go.microsoft.com/fwlink/?LinkId=94862)</span><span class="sxs-lookup"><span data-stu-id="71f27-111">[XML Schema Part 2: Datatypes Second Edition](http://go.microsoft.com/fwlink/?LinkId=94861) and [XML Schema Part 1: Structures Second Edition](http://go.microsoft.com/fwlink/?LinkId=94862)</span></span><br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="71f27-112"> では、メッセージ内で使用されるデータ型の記述に XML スキーマを使用します。</span><span class="sxs-lookup"><span data-stu-id="71f27-112"> uses the XML Schema to describe data types used in messages.</span></span>|  
|<span data-ttu-id="71f27-113">WS-Policy</span><span class="sxs-lookup"><span data-stu-id="71f27-113">WS Policy</span></span>|[<span data-ttu-id="71f27-114">Web サービス ポリシー 1.2 - フレームワーク (Ws-policy)</span><span class="sxs-lookup"><span data-stu-id="71f27-114">Web Services Policy 1.2 - Framework (WS-Policy)</span></span>](http://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [<span data-ttu-id="71f27-115">1.5 - Framework web サービス ポリシー</span><span class="sxs-lookup"><span data-stu-id="71f27-115">Web Services Policy 1.5 - Framework</span></span>](http://go.microsoft.com/fwlink/?LinkId=94865)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="71f27-116"> では、ドメイン固有のアサーションと共に WS-Policy 1.2 または 1.5 の仕様を使用して、サービス要件と機能を記述します。</span><span class="sxs-lookup"><span data-stu-id="71f27-116"> uses the WS-Policy 1.2 or 1.5 specifications with domain-specific assertions to describe service requirements and capabilities.</span></span>|  
|<span data-ttu-id="71f27-117">WS-PolicyAttachments</span><span class="sxs-lookup"><span data-stu-id="71f27-117">WS Policy Attachments</span></span>|[<span data-ttu-id="71f27-118">Web サービス ポリシー 1.2: 添付ファイル (Ws-policyattachment)</span><span class="sxs-lookup"><span data-stu-id="71f27-118">Web Services Policy 1.2 - Attachment (WS-PolicyAttachment)</span></span>](http://go.microsoft.com/fwlink/?LinkId=94866)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="71f27-119"> では、WSDL のさまざまなスコープにポリシー表現を関連付けるために、WS-PolicyAttachments が実装されています。</span><span class="sxs-lookup"><span data-stu-id="71f27-119"> implements WS-Policy Attachments to attach policy expressions at various scopes in WSDL.</span></span>|  
|<span data-ttu-id="71f27-120">WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="71f27-120">WS Metadata Exchange</span></span>|[<span data-ttu-id="71f27-121">Web サービス メタデータ交換 (Ws-metadataexchange) バージョン 1.1</span><span class="sxs-lookup"><span data-stu-id="71f27-121">Web Services Metadata Exchange (WS-MetadataExchange) version 1.1</span></span>](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="71f27-122"> では、XML スキーマ、WSDL、WS-Policy を取得するために WS-MetadataExchange が実装されています。</span><span class="sxs-lookup"><span data-stu-id="71f27-122"> implements WS-MetadataExchange to retrieve XML Schema, WSDL, and WS-Policy.</span></span>|  
|<span data-ttu-id="71f27-123">WS Addressing Binding for WSDL</span><span class="sxs-lookup"><span data-stu-id="71f27-123">WS Addressing Binding for WSDL</span></span>|[<span data-ttu-id="71f27-124">Web Services Addressing 1.0 - WSDL バインディング</span><span class="sxs-lookup"><span data-stu-id="71f27-124">Web Services Addressing 1.0 - WSDL Binding</span></span>](http://go.microsoft.com/fwlink/?LinkId=94869)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="71f27-125"> では、WSDL でアドレス指定情報を関連付けるために、WS-Addressing Binding for WSDL が実装されています。</span><span class="sxs-lookup"><span data-stu-id="71f27-125"> implements WS-Addressing Binding for WSDL to attach addressing information in WSDL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="71f27-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="71f27-126">See Also</span></span>  
 [<span data-ttu-id="71f27-127">Web サービスのシステム指定の相互運用性バインディングでサポートされるプロトコル</span><span class="sxs-lookup"><span data-stu-id="71f27-127">Web Services Protocols Supported by System-Provided Interoperability Bindings</span></span>](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
 [<span data-ttu-id="71f27-128">WSDL とポリシー</span><span class="sxs-lookup"><span data-stu-id="71f27-128">WSDL and Policy</span></span>](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
