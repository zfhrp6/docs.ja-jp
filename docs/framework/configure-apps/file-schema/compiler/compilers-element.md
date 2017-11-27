---
title: "&lt;コンパイラ&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: bea78fe5086a73e4cc588973764ac9bbef2fadc4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltcompilersgt-element"></a><span data-ttu-id="0a4ca-102">&lt;コンパイラ&gt;要素</span><span class="sxs-lookup"><span data-stu-id="0a4ca-102">&lt;compilers&gt; Element</span></span>
<span data-ttu-id="0a4ca-103">0 個以上の [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) 要素を含むコンパイラ構成要素のコンテナー。</span><span class="sxs-lookup"><span data-stu-id="0a4ca-103">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>  
  
 <span data-ttu-id="0a4ca-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0a4ca-104">\<configuration></span></span>  
<span data-ttu-id="0a4ca-105">\<system.codedom ></span><span class="sxs-lookup"><span data-stu-id="0a4ca-105">\<system.codedom></span></span>  
<span data-ttu-id="0a4ca-106">\<コンパイラ > 要素</span><span class="sxs-lookup"><span data-stu-id="0a4ca-106">\<compilers> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a4ca-107">構文</span><span class="sxs-lookup"><span data-stu-id="0a4ca-107">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a4ca-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="0a4ca-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0a4ca-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0a4ca-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a4ca-110">属性</span><span class="sxs-lookup"><span data-stu-id="0a4ca-110">Attributes</span></span>  
 <span data-ttu-id="0a4ca-111">なし。</span><span class="sxs-lookup"><span data-stu-id="0a4ca-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0a4ca-112">子要素</span><span class="sxs-lookup"><span data-stu-id="0a4ca-112">Child Elements</span></span>  
  
|<span data-ttu-id="0a4ca-113">要素</span><span class="sxs-lookup"><span data-stu-id="0a4ca-113">Element</span></span>|<span data-ttu-id="0a4ca-114">説明</span><span class="sxs-lookup"><span data-stu-id="0a4ca-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a4ca-115">\<compiler> 要素</span><span class="sxs-lookup"><span data-stu-id="0a4ca-115">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="0a4ca-116">言語プロバイダーのコンパイラ構成属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="0a4ca-116">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0a4ca-117">親要素</span><span class="sxs-lookup"><span data-stu-id="0a4ca-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0a4ca-118">要素</span><span class="sxs-lookup"><span data-stu-id="0a4ca-118">Element</span></span>|<span data-ttu-id="0a4ca-119">説明</span><span class="sxs-lookup"><span data-stu-id="0a4ca-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a4ca-120">\<configuration> 要素</span><span class="sxs-lookup"><span data-stu-id="0a4ca-120">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="0a4ca-121">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="0a4ca-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="0a4ca-122">\<system.codedom > 要素</span><span class="sxs-lookup"><span data-stu-id="0a4ca-122">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="0a4ca-123">使用可能な言語プロバイダーのコンパイラ構成設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="0a4ca-123">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a4ca-124">コメント</span><span class="sxs-lookup"><span data-stu-id="0a4ca-124">Remarks</span></span>  
 <span data-ttu-id="0a4ca-125">[\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)要素には、コンピューター上の言語プロバイダーの構成設定コンパイラにはが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0a4ca-125">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="0a4ca-126">各[\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)要素は、特定の言語プロバイダーのコンパイラ構成属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="0a4ca-126">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="0a4ca-127">.NET Framework は、マシン構成ファイル (Machine.config) で、初期のコンパイラおよび言語プロバイダー設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="0a4ca-127">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="0a4ca-128">開発者やコンパイラ ベンダーは、新しい <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> の実装のために構成設定を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="0a4ca-128">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="0a4ca-129"><xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> メソッドを使用して、プログラムによってコンピューターの言語プロバイダーとコンパイラ構成の設定を列挙します。</span><span class="sxs-lookup"><span data-stu-id="0a4ca-129">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="0a4ca-130">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="0a4ca-130">Configuration File</span></span>  
 <span data-ttu-id="0a4ca-131">この要素は、マシン構成ファイルとアプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="0a4ca-131">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a4ca-132">例</span><span class="sxs-lookup"><span data-stu-id="0a4ca-132">Example</span></span>  
 <span data-ttu-id="0a4ca-133">次の例は、一般的なコンパイラ構成要素を示しています。</span><span class="sxs-lookup"><span data-stu-id="0a4ca-133">The following example illustrates a typical compiler configuration element.</span></span>  
  
```xml  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler   
          language="c#;cs;csharp"   
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
          compilerOptions=""    
          warningLevel="1" />  
     </compilers>  
   </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a4ca-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="0a4ca-134">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="0a4ca-135">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="0a4ca-135">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="0a4ca-136">コンパイラおよび言語プロバイダー設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="0a4ca-136">Compiler and Language Provider Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 [<span data-ttu-id="0a4ca-137">\<compiler> 要素</span><span class="sxs-lookup"><span data-stu-id="0a4ca-137">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
