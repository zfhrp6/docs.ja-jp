---
title: "&lt;system.codedom&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: bf2e041f9ae9661a9b6f8ecd5883ac7d1b0f0dec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemcodedomgt-element"></a><span data-ttu-id="9c48b-102">&lt;system.codedom&gt;要素</span><span class="sxs-lookup"><span data-stu-id="9c48b-102">&lt;system.codedom&gt; Element</span></span>
<span data-ttu-id="9c48b-103">使用可能な言語プロバイダーのコンパイラ構成設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="9c48b-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
 <span data-ttu-id="9c48b-104">\<configuration > 要素</span><span class="sxs-lookup"><span data-stu-id="9c48b-104">\<configuration> Element</span></span>  
<span data-ttu-id="9c48b-105">\<system.codedom > 要素</span><span class="sxs-lookup"><span data-stu-id="9c48b-105">\<system.codedom> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c48b-106">構文</span><span class="sxs-lookup"><span data-stu-id="9c48b-106">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c48b-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="9c48b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="9c48b-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="9c48b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c48b-109">属性</span><span class="sxs-lookup"><span data-stu-id="9c48b-109">Attributes</span></span>  
 <span data-ttu-id="9c48b-110">なし。</span><span class="sxs-lookup"><span data-stu-id="9c48b-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9c48b-111">子要素</span><span class="sxs-lookup"><span data-stu-id="9c48b-111">Child Elements</span></span>  
  
|<span data-ttu-id="9c48b-112">要素</span><span class="sxs-lookup"><span data-stu-id="9c48b-112">Element</span></span>|<span data-ttu-id="9c48b-113">説明</span><span class="sxs-lookup"><span data-stu-id="9c48b-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c48b-114">\<compilers></span><span class="sxs-lookup"><span data-stu-id="9c48b-114">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="9c48b-115">0 個以上の [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) 要素を含むコンパイラ構成要素のコンテナー。</span><span class="sxs-lookup"><span data-stu-id="9c48b-115">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9c48b-116">親要素</span><span class="sxs-lookup"><span data-stu-id="9c48b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="9c48b-117">要素</span><span class="sxs-lookup"><span data-stu-id="9c48b-117">Element</span></span>|<span data-ttu-id="9c48b-118">説明</span><span class="sxs-lookup"><span data-stu-id="9c48b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c48b-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="9c48b-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="9c48b-120">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="9c48b-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c48b-121">コメント</span><span class="sxs-lookup"><span data-stu-id="9c48b-121">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="9c48b-122">.NET framework Version 2.0</span><span class="sxs-lookup"><span data-stu-id="9c48b-122">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="9c48b-123">[ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)要素にはなど、.NET Framework と共にインストールされる既定のプロバイダーだけでなく、コンピューターにインストールされている言語プロバイダーのコンパイラ構成設定が含まれています、<xref:Microsoft.CSharp.CSharpCodeProvider>と<xref:Microsoft.VisualBasic.VBCodeProvider>です。</span><span class="sxs-lookup"><span data-stu-id="9c48b-123">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="9c48b-124">[\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)要素は、0 個以上含まれています。 [\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)要素。</span><span class="sxs-lookup"><span data-stu-id="9c48b-124">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="9c48b-125">各[\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)要素は、特定の言語プロバイダーのコンパイラ構成属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="9c48b-125">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="9c48b-126">開発者やコンパイラ ベンダーできます構成設定を追加、マシン構成ファイル (Machine.config) に、新しい<xref:System.CodeDom.Compiler.CodeDomProvider>実装します。</span><span class="sxs-lookup"><span data-stu-id="9c48b-126">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="9c48b-127">使用して、<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>プログラムで、既定の言語プロバイダーと、コンピューターのコンパイラ構成設定によって識別される言語プロバイダーを列挙するメソッド。</span><span class="sxs-lookup"><span data-stu-id="9c48b-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c48b-128">.NET Framework version 1.0 および 1.1 では、既定の言語で、.NET Framework で提供されるプロバイダーを識別、 [\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)要素。</span><span class="sxs-lookup"><span data-stu-id="9c48b-128">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element.</span></span> <span data-ttu-id="9c48b-129">.NET framework version 2.0 では、既定の言語プロバイダーとして指定されていないで、 [\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)要素を使用して列挙できますが、<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="9c48b-129">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="9c48b-130">.NET framework のバージョン 1.0 および 1.1</span><span class="sxs-lookup"><span data-stu-id="9c48b-130">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="9c48b-131">[ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)要素には、コンピューター上の言語プロバイダーの構成設定コンパイラにはが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9c48b-131">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="9c48b-132">[\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)要素は、0 個以上含まれています。 [\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)要素。</span><span class="sxs-lookup"><span data-stu-id="9c48b-132">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="9c48b-133">各[\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)要素は、特定の言語プロバイダーのコンパイラ構成属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="9c48b-133">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="9c48b-134">.NET Framework は、マシン構成ファイル (Machine.config) 内でコンパイラの初期設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="9c48b-134">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="9c48b-135">開発者やコンパイラ ベンダーは、新しい <xref:System.CodeDom.Compiler.CodeDomProvider> の実装のために構成設定を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="9c48b-135">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="9c48b-136"><xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> メソッドを使用して、プログラムによってコンピューターの言語プロバイダーとコンパイラ構成の設定を列挙します。</span><span class="sxs-lookup"><span data-stu-id="9c48b-136">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="9c48b-137">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="9c48b-137">Configuration File</span></span>  
 <span data-ttu-id="9c48b-138">この要素は、マシン構成ファイルとアプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="9c48b-138">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c48b-139">例</span><span class="sxs-lookup"><span data-stu-id="9c48b-139">Example</span></span>  
 <span data-ttu-id="9c48b-140">次の例は、一般的なコンパイラ構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="9c48b-140">The following example illustrates a typical compiler configuration.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler   
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=1.0.5000.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions=""  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9c48b-141">参照</span><span class="sxs-lookup"><span data-stu-id="9c48b-141">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="9c48b-142">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="9c48b-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="9c48b-143">コンパイラおよび言語プロバイダー設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="9c48b-143">Compiler and Language Provider Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 [<span data-ttu-id="9c48b-144">\<compiler> 要素</span><span class="sxs-lookup"><span data-stu-id="9c48b-144">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
