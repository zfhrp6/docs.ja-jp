---
title: '&lt;プローブ&gt;要素'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/probing
- http://schemas.microsoft.com/.NetConfiguration/v2.0#probing
helpviewer_keywords:
- <probing> element
- container tags, <probing> element
- probing element
ms.assetid: 09c80fc9-1ba5-4192-89f7-3a79b2e4b024
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cab16e83466b5954bfebac07dd79c9a8b5e4594
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745004"
---
# <a name="ltprobinggt-element"></a><span data-ttu-id="e6800-102">&lt;プローブ&gt;要素</span><span class="sxs-lookup"><span data-stu-id="e6800-102">&lt;probing&gt; Element</span></span>
<span data-ttu-id="e6800-103">アプリケーション ベース、共通言語ランタイム アセンブリを読み込むときに検索するサブディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="e6800-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
 <span data-ttu-id="e6800-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e6800-104">\<configuration></span></span>  
<span data-ttu-id="e6800-105">\<ランタイム ></span><span class="sxs-lookup"><span data-stu-id="e6800-105">\<runtime></span></span>  
<span data-ttu-id="e6800-106">\<assemblyBinding></span><span class="sxs-lookup"><span data-stu-id="e6800-106">\<assemblyBinding></span></span>  
<span data-ttu-id="e6800-107">\<probing ></span><span class="sxs-lookup"><span data-stu-id="e6800-107">\<probing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6800-108">構文</span><span class="sxs-lookup"><span data-stu-id="e6800-108">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6800-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e6800-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e6800-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e6800-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6800-111">属性</span><span class="sxs-lookup"><span data-stu-id="e6800-111">Attributes</span></span>  
  
|<span data-ttu-id="e6800-112">属性</span><span class="sxs-lookup"><span data-stu-id="e6800-112">Attribute</span></span>|<span data-ttu-id="e6800-113">説明</span><span class="sxs-lookup"><span data-stu-id="e6800-113">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="e6800-114">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="e6800-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="e6800-115">アセンブリを含めることができるアプリケーションのベース ディレクトリのサブディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="e6800-115">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="e6800-116">各サブディレクトリをセミコロンで区切ります。</span><span class="sxs-lookup"><span data-stu-id="e6800-116">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6800-117">子要素</span><span class="sxs-lookup"><span data-stu-id="e6800-117">Child Elements</span></span>  
 <span data-ttu-id="e6800-118">なし。</span><span class="sxs-lookup"><span data-stu-id="e6800-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6800-119">親要素</span><span class="sxs-lookup"><span data-stu-id="e6800-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e6800-120">要素</span><span class="sxs-lookup"><span data-stu-id="e6800-120">Element</span></span>|<span data-ttu-id="e6800-121">説明</span><span class="sxs-lookup"><span data-stu-id="e6800-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="e6800-122">アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="e6800-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="e6800-123">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="e6800-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e6800-124">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e6800-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e6800-125">例</span><span class="sxs-lookup"><span data-stu-id="e6800-125">Example</span></span>  
 <span data-ttu-id="e6800-126">次の例では、アプリケーションの基本サブディレクトリが、ランタイムがアセンブリを検索する必要がありますを指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e6800-126">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6800-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="e6800-127">See Also</span></span>  
 [<span data-ttu-id="e6800-128">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="e6800-128">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="e6800-129">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="e6800-129">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="e6800-130">アセンブリの場所の指定</span><span class="sxs-lookup"><span data-stu-id="e6800-130">Specifying an Assembly's Location</span></span>](../../../../../docs/framework/configure-apps/specify-assembly-location.md)  
 [<span data-ttu-id="e6800-131">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="e6800-131">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
