---
title: "&lt;qualifyAssembly&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 521bbccd83f224cc824dae41309715d65472454e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltqualifyassemblygt-element"></a><span data-ttu-id="43ff9-102">&lt;qualifyAssembly&gt;要素</span><span class="sxs-lookup"><span data-stu-id="43ff9-102">&lt;qualifyAssembly&gt; Element</span></span>
<span data-ttu-id="43ff9-103">部分名が使用された場合に動的に読み込む必要があるアセンブリの完全名を指定します。</span><span class="sxs-lookup"><span data-stu-id="43ff9-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
 <span data-ttu-id="43ff9-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="43ff9-104">\<configuration></span></span>  
<span data-ttu-id="43ff9-105">\<ランタイム ></span><span class="sxs-lookup"><span data-stu-id="43ff9-105">\<runtime></span></span>  
<span data-ttu-id="43ff9-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="43ff9-106">\<assemblyBinding></span></span>  
<span data-ttu-id="43ff9-107">\<qualifyAssembly ></span><span class="sxs-lookup"><span data-stu-id="43ff9-107">\<qualifyAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43ff9-108">構文</span><span class="sxs-lookup"><span data-stu-id="43ff9-108">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43ff9-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="43ff9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="43ff9-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="43ff9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43ff9-111">属性</span><span class="sxs-lookup"><span data-stu-id="43ff9-111">Attributes</span></span>  
  
|<span data-ttu-id="43ff9-112">属性</span><span class="sxs-lookup"><span data-stu-id="43ff9-112">Attribute</span></span>|<span data-ttu-id="43ff9-113">説明</span><span class="sxs-lookup"><span data-stu-id="43ff9-113">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="43ff9-114">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="43ff9-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="43ff9-115">コードに表示されるアセンブリの部分名を指定します。</span><span class="sxs-lookup"><span data-stu-id="43ff9-115">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="43ff9-116">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="43ff9-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="43ff9-117">グローバル アセンブリ キャッシュに表示されるアセンブリの完全な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="43ff9-117">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43ff9-118">子要素</span><span class="sxs-lookup"><span data-stu-id="43ff9-118">Child Elements</span></span>  
 <span data-ttu-id="43ff9-119">なし。</span><span class="sxs-lookup"><span data-stu-id="43ff9-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43ff9-120">親要素</span><span class="sxs-lookup"><span data-stu-id="43ff9-120">Parent Elements</span></span>  
  
|<span data-ttu-id="43ff9-121">要素</span><span class="sxs-lookup"><span data-stu-id="43ff9-121">Element</span></span>|<span data-ttu-id="43ff9-122">説明</span><span class="sxs-lookup"><span data-stu-id="43ff9-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="43ff9-123">アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="43ff9-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="43ff9-124">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="43ff9-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="43ff9-125">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="43ff9-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43ff9-126">コメント</span><span class="sxs-lookup"><span data-stu-id="43ff9-126">Remarks</span></span>  
 <span data-ttu-id="43ff9-127">呼び出す、<xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>部分アセンブリ名を使用して、メソッド、共通言語ランタイムによってのみ、アプリケーション ベース ディレクトリ内のアセンブリを探すようにします。</span><span class="sxs-lookup"><span data-stu-id="43ff9-127">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="43ff9-128">使用して、  **\<qualifyAssembly >** (名前、バージョン、公開キー トークン、およびカルチャ) の完全なアセンブリ情報を提供し、により、共通言語ランタイムを検索するアプリケーション構成ファイル内の要素グローバル アセンブリ キャッシュにアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="43ff9-128">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="43ff9-129">**FullName**属性がアセンブリ id の 4 つのフィールドを含める必要があります。 名前、バージョン、公開キー トークン、およびカルチャ。</span><span class="sxs-lookup"><span data-stu-id="43ff9-129">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="43ff9-130">**それよりも**属性では、アセンブリは参照部分的にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="43ff9-130">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="43ff9-131">アセンブリのテキストの名前 (最も一般的なケース) を少なくとも指定する必要がありますが、バージョン、公開キー トークン、またはカルチャ (または、4 つが、すべての 4 つの任意の組み合わせ) にも含めることができます。</span><span class="sxs-lookup"><span data-stu-id="43ff9-131">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="43ff9-132">**それよりも**の呼び出しで指定された名前に一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="43ff9-132">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="43ff9-133">たとえば、指定することはできません`"math"`として、**それよりも**構成ファイルと呼び出し属性`Assembly.Load("math, Version=3.3.3.3")`コードにします。</span><span class="sxs-lookup"><span data-stu-id="43ff9-133">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43ff9-134">例</span><span class="sxs-lookup"><span data-stu-id="43ff9-134">Example</span></span>  
 <span data-ttu-id="43ff9-135">次の例は、呼び出しを論理的にオンに`Assembly.Load("math")`に`Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`です。</span><span class="sxs-lookup"><span data-stu-id="43ff9-135">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"   
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="43ff9-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="43ff9-136">See Also</span></span>  
 [<span data-ttu-id="43ff9-137">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="43ff9-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="43ff9-138">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="43ff9-138">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="43ff9-139">NIB: 部分アセンブリ参照</span><span class="sxs-lookup"><span data-stu-id="43ff9-139">NIB: Partial Assembly References</span></span>](http://msdn.microsoft.com/en-us/ec90f07a-398c-4306-9401-0fc5ff9cb59f)
