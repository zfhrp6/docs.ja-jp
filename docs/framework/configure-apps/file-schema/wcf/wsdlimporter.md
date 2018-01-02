---
title: '&lt;wsdlImporter&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc85c93dc73918d661195e33ce5094622db36af4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltwsdlimportergt"></a><span data-ttu-id="18623-102">&lt;wsdlImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="18623-102">&lt;wsdlImporter&gt;</span></span>
<span data-ttu-id="18623-103">WS-Policy が添付された Web サービス記述言語 (WSDL) 1.1 メタデータをインポートするすべての WSDL インポーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="18623-103">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="18623-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="18623-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="18623-105">\<クライアント ></span><span class="sxs-lookup"><span data-stu-id="18623-105">\<client></span></span>  
<span data-ttu-id="18623-106">\<メタデータ ></span><span class="sxs-lookup"><span data-stu-id="18623-106">\<metadata></span></span>  
<span data-ttu-id="18623-107">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="18623-107">\<wsdlImporters></span></span>  
<span data-ttu-id="18623-108">\<wsdlImporter ></span><span class="sxs-lookup"><span data-stu-id="18623-108">\<wsdlImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18623-109">構文</span><span class="sxs-lookup"><span data-stu-id="18623-109">Syntax</span></span>  
  
```xml  
<metadata>  
  <wsdlImporters>  
    <wsdlImporter type="string" />  
  </wsdlImporters>  
</metadata>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18623-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="18623-110">Attributes and Elements</span></span>  
 <span data-ttu-id="18623-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="18623-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18623-112">属性</span><span class="sxs-lookup"><span data-stu-id="18623-112">Attributes</span></span>  
  
|<span data-ttu-id="18623-113">属性</span><span class="sxs-lookup"><span data-stu-id="18623-113">Attribute</span></span>|<span data-ttu-id="18623-114">説明</span><span class="sxs-lookup"><span data-stu-id="18623-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="18623-115">この要素の型です。</span><span class="sxs-lookup"><span data-stu-id="18623-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18623-116">子要素</span><span class="sxs-lookup"><span data-stu-id="18623-116">Child Elements</span></span>  
 <span data-ttu-id="18623-117">なし。</span><span class="sxs-lookup"><span data-stu-id="18623-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="18623-118">親要素</span><span class="sxs-lookup"><span data-stu-id="18623-118">Parent Elements</span></span>  
  
|<span data-ttu-id="18623-119">要素</span><span class="sxs-lookup"><span data-stu-id="18623-119">Element</span></span>|<span data-ttu-id="18623-120">説明</span><span class="sxs-lookup"><span data-stu-id="18623-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18623-121">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="18623-121">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="18623-122">WS-Policy が添付された Web サービス記述言語 (WSDL) 1.1 メタデータをインポートするすべての WSDL インポーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="18623-122">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18623-123">コメント</span><span class="sxs-lookup"><span data-stu-id="18623-123">Remarks</span></span>  
 <span data-ttu-id="18623-124">WSDL インポーターは、メタデータのインポートに加えて、コントラクトおよびエンドポイント情報を表すさまざまなクラスにその情報を変換するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="18623-124">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="18623-125">コントラクトおよびエンドポイントの情報やプロパティを選択的にインポートできます。これらは、任意のインポート エラーを公開し、インポートおよび変換プロセスに関連する型情報を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="18623-125">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="18623-126">また、任意のポリシー ドキュメント、WSDL ドキュメント、WSDL 拡張、および XML スキーマ ドキュメントにアクセスするためのバインディング情報およびプロパティのインポートもサポートします。</span><span class="sxs-lookup"><span data-stu-id="18623-126">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18623-127">参照</span><span class="sxs-lookup"><span data-stu-id="18623-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [<span data-ttu-id="18623-128">WCF クライアントの構成</span><span class="sxs-lookup"><span data-stu-id="18623-128">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="18623-129">クライアント</span><span class="sxs-lookup"><span data-stu-id="18623-129">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
