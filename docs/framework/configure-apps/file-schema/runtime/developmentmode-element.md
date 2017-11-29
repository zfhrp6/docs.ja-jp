---
title: "&lt;developmentMode&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4573c3a5e0cf64996f2a4e109736d966b754494a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltdevelopmentmodegt-element"></a><span data-ttu-id="d996f-102">&lt;developmentMode&gt;要素</span><span class="sxs-lookup"><span data-stu-id="d996f-102">&lt;developmentMode&gt; Element</span></span>
<span data-ttu-id="d996f-103">DEVPATH 環境変数によって指定されたディレクトリで、ランタイムがアセンブリの検索を行うかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d996f-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
 <span data-ttu-id="d996f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d996f-104">\<configuration></span></span>  
<span data-ttu-id="d996f-105">\<ランタイム ></span><span class="sxs-lookup"><span data-stu-id="d996f-105">\<runtime></span></span>  
<span data-ttu-id="d996f-106">\<developmentMode ></span><span class="sxs-lookup"><span data-stu-id="d996f-106">\<developmentMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d996f-107">構文</span><span class="sxs-lookup"><span data-stu-id="d996f-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d996f-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d996f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d996f-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d996f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d996f-110">属性</span><span class="sxs-lookup"><span data-stu-id="d996f-110">Attributes</span></span>  
  
|<span data-ttu-id="d996f-111">属性</span><span class="sxs-lookup"><span data-stu-id="d996f-111">Attribute</span></span>|<span data-ttu-id="d996f-112">説明</span><span class="sxs-lookup"><span data-stu-id="d996f-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d996f-113">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="d996f-113">**developerInstallation**</span></span>|<span data-ttu-id="d996f-114">DEVPATH 環境変数によって指定されたディレクトリで、ランタイムがアセンブリの検索を行うかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d996f-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="d996f-115">developerInstallation 属性</span><span class="sxs-lookup"><span data-stu-id="d996f-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="d996f-116">値</span><span class="sxs-lookup"><span data-stu-id="d996f-116">Value</span></span>|<span data-ttu-id="d996f-117">説明</span><span class="sxs-lookup"><span data-stu-id="d996f-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d996f-118">**true**</span><span class="sxs-lookup"><span data-stu-id="d996f-118">**true**</span></span>|<span data-ttu-id="d996f-119">DEVPATH 環境変数で指定したディレクトリ内のアセンブリを検索します。</span><span class="sxs-lookup"><span data-stu-id="d996f-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="d996f-120">**false**</span><span class="sxs-lookup"><span data-stu-id="d996f-120">**false**</span></span>|<span data-ttu-id="d996f-121">DEVPATH 環境変数で指定したディレクトリ内のアセンブリを検索しません。</span><span class="sxs-lookup"><span data-stu-id="d996f-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="d996f-122">これは、既定値です。</span><span class="sxs-lookup"><span data-stu-id="d996f-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d996f-123">子要素</span><span class="sxs-lookup"><span data-stu-id="d996f-123">Child Elements</span></span>  
 <span data-ttu-id="d996f-124">なし。</span><span class="sxs-lookup"><span data-stu-id="d996f-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d996f-125">親要素</span><span class="sxs-lookup"><span data-stu-id="d996f-125">Parent Elements</span></span>  
  
|<span data-ttu-id="d996f-126">要素</span><span class="sxs-lookup"><span data-stu-id="d996f-126">Element</span></span>|<span data-ttu-id="d996f-127">説明</span><span class="sxs-lookup"><span data-stu-id="d996f-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d996f-128">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="d996f-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d996f-129">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d996f-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d996f-130">コメント</span><span class="sxs-lookup"><span data-stu-id="d996f-130">Remarks</span></span>  
 <span data-ttu-id="d996f-131">この設定を使用して、開発時のみです。</span><span class="sxs-lookup"><span data-stu-id="d996f-131">Use this setting only at development time.</span></span> <span data-ttu-id="d996f-132">ランタイムは、DEVPATH で見つかった厳密な名前のアセンブリのバージョンをチェックしません。</span><span class="sxs-lookup"><span data-stu-id="d996f-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="d996f-133">最初に見つかったアセンブリは単に使用します。</span><span class="sxs-lookup"><span data-stu-id="d996f-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d996f-134">例</span><span class="sxs-lookup"><span data-stu-id="d996f-134">Example</span></span>  
 <span data-ttu-id="d996f-135">次の例では、DEVPATH 環境変数で指定したディレクトリ内のアセンブリを検索するランタイムを発生させる方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d996f-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d996f-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="d996f-136">See Also</span></span>  
 [<span data-ttu-id="d996f-137">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="d996f-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="d996f-138">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="d996f-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="d996f-139">方法 : DEVPATH を使用してアセンブリを指定する</span><span class="sxs-lookup"><span data-stu-id="d996f-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)
