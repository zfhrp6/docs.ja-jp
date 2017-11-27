---
title: "&lt;Directives&gt; 要素 (.NET ネイティブ)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a55048ea5b2889da82b10ac2a51865d945635143
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltdirectivesgt-element-net-native"></a><span data-ttu-id="79eed-102">&lt;Directives&gt; 要素 (.NET ネイティブ)</span><span class="sxs-lookup"><span data-stu-id="79eed-102">&lt;Directives&gt; Element (.NET Native)</span></span>
<span data-ttu-id="79eed-103">[!INCLUDE[net_native](../../../includes/net-native-md.md)]のすべてのランタイム ディレクティブ ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="79eed-103">The root element in every runtime directives file for [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="79eed-104">**\<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">**</span><span class="sxs-lookup"><span data-stu-id="79eed-104">**\<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79eed-105">構文</span><span class="sxs-lookup"><span data-stu-id="79eed-105">Syntax</span></span>  
  
```xml  
      <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="79eed-106">属性</span><span class="sxs-lookup"><span data-stu-id="79eed-106">Attributes</span></span>  
  
|<span data-ttu-id="79eed-107">属性</span><span class="sxs-lookup"><span data-stu-id="79eed-107">Attribute</span></span>|<span data-ttu-id="79eed-108">説明</span><span class="sxs-lookup"><span data-stu-id="79eed-108">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="79eed-109">XML 名前空間。</span><span class="sxs-lookup"><span data-stu-id="79eed-109">The XML namespace.</span></span> <span data-ttu-id="79eed-110">値は常に **"http://schemas.microsoft.com/netfx/2013/01/metadata"** です。</span><span class="sxs-lookup"><span data-stu-id="79eed-110">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="79eed-111">子要素</span><span class="sxs-lookup"><span data-stu-id="79eed-111">Child elements</span></span>  
  
|<span data-ttu-id="79eed-112">要素</span><span class="sxs-lookup"><span data-stu-id="79eed-112">Element</span></span>|<span data-ttu-id="79eed-113">説明</span><span class="sxs-lookup"><span data-stu-id="79eed-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79eed-114">\<Application></span><span class="sxs-lookup"><span data-stu-id="79eed-114">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)|<span data-ttu-id="79eed-115">リフレクションで使用可能なメタデータを持つアプリケーション全体の型と型のメンバーのコンテナーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="79eed-115">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="79eed-116">\<Library></span><span class="sxs-lookup"><span data-stu-id="79eed-116">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)|<span data-ttu-id="79eed-117">実行時にメタデータを必要とする子型と型のメンバーを持つアセンブリを定義します。</span><span class="sxs-lookup"><span data-stu-id="79eed-117">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79eed-118">コメント</span><span class="sxs-lookup"><span data-stu-id="79eed-118">Remarks</span></span>  
 <span data-ttu-id="79eed-119">各ランタイム ディレクティブ ファイルには、`<Directives>` 要素を 1 つのみ含めることができます。</span><span class="sxs-lookup"><span data-stu-id="79eed-119">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="79eed-120">`<Directives>` 要素には、0 または 1 個の [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 要素と、0 個以上の [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 要素を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="79eed-120">The `<Directives>` element can contain zero or one [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element, and zero, one, or more [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79eed-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="79eed-121">See Also</span></span>  
 [<span data-ttu-id="79eed-122">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="79eed-122">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="79eed-123">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="79eed-123">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
