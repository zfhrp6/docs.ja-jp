---
title: '&lt;メタデータ&gt;'
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 7e314ae56ed7a1b532bb8946fbb28802e72d3e20
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltmetadatagt"></a><span data-ttu-id="f2a84-102">&lt;メタデータ&gt;</span><span class="sxs-lookup"><span data-stu-id="f2a84-102">&lt;metadata&gt;</span></span>
<span data-ttu-id="f2a84-103">サービス メタデータを処理する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="f2a84-103">Specifies how service metadata can be processed.</span></span>  
  
 <span data-ttu-id="f2a84-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f2a84-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f2a84-105">\<client></span><span class="sxs-lookup"><span data-stu-id="f2a84-105">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2a84-106">構文</span><span class="sxs-lookup"><span data-stu-id="f2a84-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
        <metadata>  
                   <policyImporters>  
                          <policyImporter type="string" />  
                   </policyImporters  
                 <wsdlImporters>  
                      <wsdlImporter type="string" />  
                 </wsdlImporters>  
        </metadata>  
    </client>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2a84-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f2a84-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f2a84-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f2a84-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2a84-109">属性</span><span class="sxs-lookup"><span data-stu-id="f2a84-109">Attributes</span></span>  
 <span data-ttu-id="f2a84-110">なし。</span><span class="sxs-lookup"><span data-stu-id="f2a84-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f2a84-111">子要素</span><span class="sxs-lookup"><span data-stu-id="f2a84-111">Child Elements</span></span>  
  
|<span data-ttu-id="f2a84-112">要素</span><span class="sxs-lookup"><span data-stu-id="f2a84-112">Element</span></span>|<span data-ttu-id="f2a84-113">説明</span><span class="sxs-lookup"><span data-stu-id="f2a84-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2a84-114">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="f2a84-114">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="f2a84-115">バインディングに関するカスタム ポリシー アサーションのインポートを制御するすべてのポリシー インポーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="f2a84-115">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="f2a84-116">ポリシー インポーターは、バインディング機能についてのカスタム ポリシー アサーションの検索、およびアサーションで必要となる機能を実装するカスタム バインディング要素の結び付けに使用されます。</span><span class="sxs-lookup"><span data-stu-id="f2a84-116">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[<span data-ttu-id="f2a84-117">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="f2a84-117">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="f2a84-118">WS-Policy が添付された Web サービス記述言語 (WSDL) 1.1 メタデータをインポートするすべての WSDL インポーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="f2a84-118">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="f2a84-119">WSDL インポーターは、メタデータのインポートに加えて、コントラクトおよびエンドポイント情報を表すさまざまなクラスにその情報を変換するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f2a84-119">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="f2a84-120">コントラクトおよびエンドポイントの情報やプロパティを選択的にインポートできます。これらは、任意のインポート エラーを公開し、インポートおよび変換プロセスに関連する型情報を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="f2a84-120">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="f2a84-121">また、任意のポリシー ドキュメント、WSDL ドキュメント、WSDL 拡張、および XML スキーマ ドキュメントにアクセスするためのバインディング情報およびプロパティのインポートもサポートします。</span><span class="sxs-lookup"><span data-stu-id="f2a84-121">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f2a84-122">親要素</span><span class="sxs-lookup"><span data-stu-id="f2a84-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f2a84-123">要素</span><span class="sxs-lookup"><span data-stu-id="f2a84-123">Element</span></span>|<span data-ttu-id="f2a84-124">説明</span><span class="sxs-lookup"><span data-stu-id="f2a84-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2a84-125">\<クライアント ></span><span class="sxs-lookup"><span data-stu-id="f2a84-125">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="f2a84-126">クライアントが接続可能なエンドポイントの一覧を定義するクライアント セクション。</span><span class="sxs-lookup"><span data-stu-id="f2a84-126">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2a84-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2a84-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [<span data-ttu-id="f2a84-128">WCF クライアントの構成</span><span class="sxs-lookup"><span data-stu-id="f2a84-128">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="f2a84-129">クライアント</span><span class="sxs-lookup"><span data-stu-id="f2a84-129">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
