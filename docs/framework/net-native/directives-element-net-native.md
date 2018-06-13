---
title: '&lt;Directives&gt; 要素 (.NET ネイティブ)'
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd571255f924c9f3878c00a2bc01397d63e6d777
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394447"
---
# <a name="ltdirectivesgt-element-net-native"></a><span data-ttu-id="513de-102">&lt;Directives&gt; 要素 (.NET ネイティブ)</span><span class="sxs-lookup"><span data-stu-id="513de-102">&lt;Directives&gt; Element (.NET Native)</span></span>
<span data-ttu-id="513de-103">[!INCLUDE[net_native](../../../includes/net-native-md.md)]のすべてのランタイム ディレクティブ ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="513de-103">The root element in every runtime directives file for [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="513de-104">**\<ディレクティブ xmlns ="http://schemas.microsoft.com/netfx/2013/01/metadata">**</span><span class="sxs-lookup"><span data-stu-id="513de-104">**\<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="513de-105">構文</span><span class="sxs-lookup"><span data-stu-id="513de-105">Syntax</span></span>  
  
```xml  
      <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="513de-106">属性</span><span class="sxs-lookup"><span data-stu-id="513de-106">Attributes</span></span>  
  
|<span data-ttu-id="513de-107">属性</span><span class="sxs-lookup"><span data-stu-id="513de-107">Attribute</span></span>|<span data-ttu-id="513de-108">説明</span><span class="sxs-lookup"><span data-stu-id="513de-108">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="513de-109">XML 名前空間。</span><span class="sxs-lookup"><span data-stu-id="513de-109">The XML namespace.</span></span> <span data-ttu-id="513de-110">その値は常に **"http://schemas.microsoft.com/netfx/2013/01/metadata"** です。</span><span class="sxs-lookup"><span data-stu-id="513de-110">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="513de-111">子要素</span><span class="sxs-lookup"><span data-stu-id="513de-111">Child elements</span></span>  
  
|<span data-ttu-id="513de-112">要素</span><span class="sxs-lookup"><span data-stu-id="513de-112">Element</span></span>|<span data-ttu-id="513de-113">説明</span><span class="sxs-lookup"><span data-stu-id="513de-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="513de-114">\<Application></span><span class="sxs-lookup"><span data-stu-id="513de-114">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)|<span data-ttu-id="513de-115">リフレクションで使用可能なメタデータを持つアプリケーション全体の型と型のメンバーのコンテナーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="513de-115">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="513de-116">\<Library></span><span class="sxs-lookup"><span data-stu-id="513de-116">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)|<span data-ttu-id="513de-117">実行時にメタデータを必要とする子型と型のメンバーを持つアセンブリを定義します。</span><span class="sxs-lookup"><span data-stu-id="513de-117">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="513de-118">コメント</span><span class="sxs-lookup"><span data-stu-id="513de-118">Remarks</span></span>  
 <span data-ttu-id="513de-119">各ランタイム ディレクティブ ファイルには、`<Directives>` 要素を 1 つのみ含めることができます。</span><span class="sxs-lookup"><span data-stu-id="513de-119">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="513de-120">`<Directives>` 要素には、0 または 1 個の [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 要素と、0 個以上の [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 要素を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="513de-120">The `<Directives>` element can contain zero or one [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element, and zero, one, or more [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="513de-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="513de-121">See Also</span></span>  
 [<span data-ttu-id="513de-122">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="513de-122">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="513de-123">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="513de-123">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
