---
title: "&lt;プローブ&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/probing
- http://schemas.microsoft.com/.NetConfiguration/v2.0#probing
helpviewer_keywords:
- <probing> element
- container tags, <probing> element
- probing element
ms.assetid: 09c80fc9-1ba5-4192-89f7-3a79b2e4b024
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e846cb1386dc64161d91ab50b6a04e5560e9c6da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltprobinggt-element"></a><span data-ttu-id="11bf8-102">&lt;プローブ&gt;要素</span><span class="sxs-lookup"><span data-stu-id="11bf8-102">&lt;probing&gt; Element</span></span>
<span data-ttu-id="11bf8-103">アプリケーション ベース、共通言語ランタイム アセンブリを読み込むときに検索するサブディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="11bf8-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
 <span data-ttu-id="11bf8-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="11bf8-104">\<configuration></span></span>  
<span data-ttu-id="11bf8-105">\<ランタイム ></span><span class="sxs-lookup"><span data-stu-id="11bf8-105">\<runtime></span></span>  
<span data-ttu-id="11bf8-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="11bf8-106">\<assemblyBinding></span></span>  
<span data-ttu-id="11bf8-107">\<probing ></span><span class="sxs-lookup"><span data-stu-id="11bf8-107">\<probing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11bf8-108">構文</span><span class="sxs-lookup"><span data-stu-id="11bf8-108">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11bf8-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="11bf8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="11bf8-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="11bf8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11bf8-111">属性</span><span class="sxs-lookup"><span data-stu-id="11bf8-111">Attributes</span></span>  
  
|<span data-ttu-id="11bf8-112">属性</span><span class="sxs-lookup"><span data-stu-id="11bf8-112">Attribute</span></span>|<span data-ttu-id="11bf8-113">説明</span><span class="sxs-lookup"><span data-stu-id="11bf8-113">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="11bf8-114">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="11bf8-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="11bf8-115">アセンブリを含めることができるアプリケーションのベース ディレクトリのサブディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="11bf8-115">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="11bf8-116">各サブディレクトリをセミコロンで区切ります。</span><span class="sxs-lookup"><span data-stu-id="11bf8-116">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11bf8-117">子要素</span><span class="sxs-lookup"><span data-stu-id="11bf8-117">Child Elements</span></span>  
 <span data-ttu-id="11bf8-118">なし。</span><span class="sxs-lookup"><span data-stu-id="11bf8-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="11bf8-119">親要素</span><span class="sxs-lookup"><span data-stu-id="11bf8-119">Parent Elements</span></span>  
  
|<span data-ttu-id="11bf8-120">要素</span><span class="sxs-lookup"><span data-stu-id="11bf8-120">Element</span></span>|<span data-ttu-id="11bf8-121">説明</span><span class="sxs-lookup"><span data-stu-id="11bf8-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="11bf8-122">アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="11bf8-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="11bf8-123">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="11bf8-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="11bf8-124">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="11bf8-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="11bf8-125">例</span><span class="sxs-lookup"><span data-stu-id="11bf8-125">Example</span></span>  
 <span data-ttu-id="11bf8-126">次の例では、アプリケーションの基本サブディレクトリが、ランタイムがアセンブリを検索する必要がありますを指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="11bf8-126">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="11bf8-127">参照</span><span class="sxs-lookup"><span data-stu-id="11bf8-127">See Also</span></span>  
 [<span data-ttu-id="11bf8-128">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="11bf8-128">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="11bf8-129">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="11bf8-129">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="11bf8-130">アセンブリの場所の指定</span><span class="sxs-lookup"><span data-stu-id="11bf8-130">Specifying an Assembly's Location</span></span>](../../../../../docs/framework/configure-apps/specify-assembly-location.md)  
 [<span data-ttu-id="11bf8-131">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="11bf8-131">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
