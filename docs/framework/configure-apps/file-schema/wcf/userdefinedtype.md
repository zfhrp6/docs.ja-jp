---
title: '&lt;userDefinedType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0baac8dc6a9899261a490a257dbae0e7eb4d2ced
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltuserdefinedtypegt"></a><span data-ttu-id="69be4-102">&lt;userDefinedType&gt;</span><span class="sxs-lookup"><span data-stu-id="69be4-102">&lt;userDefinedType&gt;</span></span>
<span data-ttu-id="69be4-103">サービス コントラクトに含まれるユーザー定義型 (UDT) を表します。</span><span class="sxs-lookup"><span data-stu-id="69be4-103">Represents a User Defined Type (UDT) that is to be included in the service contract.</span></span>  
  
 <span data-ttu-id="69be4-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="69be4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="69be4-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="69be4-105">\<comContracts></span></span>  
<span data-ttu-id="69be4-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="69be4-106">\<comContract></span></span>  
<span data-ttu-id="69be4-107">\<userDefinedTypes ></span><span class="sxs-lookup"><span data-stu-id="69be4-107">\<userDefinedTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69be4-108">構文</span><span class="sxs-lookup"><span data-stu-id="69be4-108">Syntax</span></span>  
  
```xml  
<comContracts>  
  <comContract>  
      <userDefinedTypes>  
         <userDefinedType name="string"  
            typeLibID="string"  
            typeLibVersion="string"  
            typeDefID="string">  
         </userDefinedType>  
      </userDefinedTypes>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69be4-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="69be4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="69be4-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="69be4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69be4-111">属性</span><span class="sxs-lookup"><span data-stu-id="69be4-111">Attributes</span></span>  
  
|<span data-ttu-id="69be4-112">属性</span><span class="sxs-lookup"><span data-stu-id="69be4-112">Attribute</span></span>|<span data-ttu-id="69be4-113">説明</span><span class="sxs-lookup"><span data-stu-id="69be4-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="69be4-114">判読可能な型名を提供する文字列を含む省略可能な属性。</span><span class="sxs-lookup"><span data-stu-id="69be4-114">An optional attribute that contains a string that provides the readable type name.</span></span> <span data-ttu-id="69be4-115">これは、ランタイムでは使用されませんが、リーダーが型を区別するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="69be4-115">This is not used by the runtime but helps a reader to distinguish the types.</span></span>|  
|`TypeDefID`|<span data-ttu-id="69be4-116">登録されているタイプ ライブラリ内の特定の UDT 型を識別する GUID 文字列。</span><span class="sxs-lookup"><span data-stu-id="69be4-116">A GUID string that identifies the specific UDT type within the registered type library.</span></span>|  
|`TypeLibID`|<span data-ttu-id="69be4-117">型を定義する登録されているタイプ ライブラリを識別する GUID 文字列。</span><span class="sxs-lookup"><span data-stu-id="69be4-117">A GUID string that identifies the registered type library that defines the type.</span></span>|  
|`TypeLibVersion`|<span data-ttu-id="69be4-118">型を定義するタイプ ライブラリ バージョンを識別する文字列。</span><span class="sxs-lookup"><span data-stu-id="69be4-118">A string that identifies the type library version that defines the type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69be4-119">子要素</span><span class="sxs-lookup"><span data-stu-id="69be4-119">Child Elements</span></span>  
 <span data-ttu-id="69be4-120">なし。</span><span class="sxs-lookup"><span data-stu-id="69be4-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="69be4-121">親要素</span><span class="sxs-lookup"><span data-stu-id="69be4-121">Parent Elements</span></span>  
  
|<span data-ttu-id="69be4-122">要素</span><span class="sxs-lookup"><span data-stu-id="69be4-122">Element</span></span>|<span data-ttu-id="69be4-123">説明</span><span class="sxs-lookup"><span data-stu-id="69be4-123">Description</span></span>|  
|-------------|-----------------|  
|`userDefinedTypes`|<span data-ttu-id="69be4-124">`userDefinedType` 要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="69be4-124">A collection of `userDefinedType` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69be4-125">コメント</span><span class="sxs-lookup"><span data-stu-id="69be4-125">Remarks</span></span>  
 <span data-ttu-id="69be4-126">COM+ 統合ランタイムは、タイプ ライブラリを調べることによってサービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="69be4-126">The COM+ integration runtime creates services by inspecting the type library.</span></span> <span data-ttu-id="69be4-127">COM+ コンポーネントに VARIANT を渡すメソッドが含まれている場合、システムでは、渡される実際の型を実行前に判断することはできません。</span><span class="sxs-lookup"><span data-stu-id="69be4-127">When a COM+ component contains methods that pass a VARIANT, the system cannot determine the actual types to be passed prior to runtime.</span></span> <span data-ttu-id="69be4-128">したがって、VARIANT としてユーザー定義型 (UDT) を渡そうとしても、シリアル化で認識できる型ではないので失敗します。</span><span class="sxs-lookup"><span data-stu-id="69be4-128">Therefore, when you attempt to pass a User Defined Type (UDT) within a VARIANT, it fails because it is not a known type for serialization.</span></span>  
  
 <span data-ttu-id="69be4-129">この問題を回避するには、UDT を構成ファイルに追加して、適切なサービス コントラクトで既知の型として含まれるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="69be4-129">To circumvent this problem, you can add the UDTs to the configuration file so that they can be included as known types on the appropriate service contract.</span></span> <span data-ttu-id="69be4-130">このためには、UDT およびコントラクト、つまりそれを使用する元の COM インターフェイスを一意に識別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69be4-130">In order to do so, you have to uniquely identify the UDT and the contract(s), that is, the original COM interface(s) that uses it.</span></span>  
  
 <span data-ttu-id="69be4-131">この目的で、2 つの特定の UDT を構成ファイルの <`userDefinedTypes`> セクションに追加するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="69be4-131">The following example demonstrates adding two specific UDTs to the <`userDefinedTypes`> section of the configuration file for this purpose.</span></span>  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
      <userDefinedTypes>  
         <userDefinedType name="CustomerType"  
            typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"  
            typeLibVersion="1.0"  
            typeDefID="{D129765C-F211-434e-825A-9A63198C41F2}">  
         </userDefinedType>  
         <userDefinedType name="AddressType"  
            typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"  
            typeLibVersion="1.0"  
            typeDefID="{4616AE0D-687A-43B7-BC63-141AE3DFD099}">  
         </userDefinedType>  
      </userDefinedTypes>  
      <exposedMethods>  
         <exposedMethod name="BuyStock" />  
         <exposedMethod name="SellStock" />  
         <exposedMethod name="ExecuteTransaction" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
 <span data-ttu-id="69be4-132">サービスを初期化する場合、統合ランタイムは、指定された型を検索し、指定されたコントラクトで既知の型のコレクションにそれらを追加します。</span><span class="sxs-lookup"><span data-stu-id="69be4-132">When the service is initialized, the integration runtime looks up the specified types and adds them to the known types collection for the specified contracts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69be4-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="69be4-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>  
 <xref:System.ServiceModel.Configuration.ComUdtElementCollection>  
 <xref:System.ServiceModel.Configuration.ComUdtElement>  
 [<span data-ttu-id="69be4-134">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="69be4-134">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="69be4-135">COM + アプリケーションとの統合</span><span class="sxs-lookup"><span data-stu-id="69be4-135">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="69be4-136">方法: COM + サービス設定の構成</span><span class="sxs-lookup"><span data-stu-id="69be4-136">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
