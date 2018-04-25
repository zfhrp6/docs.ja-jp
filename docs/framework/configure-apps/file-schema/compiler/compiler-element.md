---
title: '&lt;compiler&gt;要素'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
caps.latest.revision: 20
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 242a4780443026e751d76c7e80dd9a77cbbbddc7
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2018
---
# <a name="ltcompilergt-element"></a><span data-ttu-id="a39ee-102">&lt;compiler&gt;要素</span><span class="sxs-lookup"><span data-stu-id="a39ee-102">&lt;compiler&gt; Element</span></span>
<span data-ttu-id="a39ee-103">言語プロバイダーのコンパイラ構成属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="a39ee-103">Specifies the compiler configuration attributes for a language provider.</span></span>  
  
 <span data-ttu-id="a39ee-104">\<configuration >要素</span><span class="sxs-lookup"><span data-stu-id="a39ee-104">\<configuration Element></span></span>  
<span data-ttu-id="a39ee-105">\<system.codedom>要素</span><span class="sxs-lookup"><span data-stu-id="a39ee-105">\<system.codedom Element></span></span>  
<span data-ttu-id="a39ee-106">\<compilers >要素</span><span class="sxs-lookup"><span data-stu-id="a39ee-106">\<compilers Element></span></span>  
<span data-ttu-id="a39ee-107">\<compiler> 要素</span><span class="sxs-lookup"><span data-stu-id="a39ee-107">\<compiler> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a39ee-108">構文</span><span class="sxs-lookup"><span data-stu-id="a39ee-108">Syntax</span></span>  
  
```xml  
<compiler  
  language="languageName[;...;...]"  
  extension="fileExtension[;...;...]"  
  type="typeName, assemblyName"  
  warningLevel="number"  
  compilerOptions="option1 option2"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a39ee-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a39ee-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a39ee-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a39ee-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a39ee-111">属性</span><span class="sxs-lookup"><span data-stu-id="a39ee-111">Attributes</span></span>  
  
|<span data-ttu-id="a39ee-112">属性</span><span class="sxs-lookup"><span data-stu-id="a39ee-112">Attribute</span></span>|<span data-ttu-id="a39ee-113">説明</span><span class="sxs-lookup"><span data-stu-id="a39ee-113">Description</span></span>|  
|---------------|-----------------|  
|`compilerOptions`|<span data-ttu-id="a39ee-114">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="a39ee-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a39ee-115">コンパイルのコンパイラ固有の追加の引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="a39ee-115">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="a39ee-116">値、`compilerOptions`属性は通常はコンパイラのコンパイラ オプションのトピックに表示します。</span><span class="sxs-lookup"><span data-stu-id="a39ee-116">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span> <span data-ttu-id="a39ee-117">Visual Studio 2005 ドキュメントでの「コンパイラ オプション」というキーワードを検索してコンパイラのオプションを検索できます。</span><span class="sxs-lookup"><span data-stu-id="a39ee-117">In the Visual Studio 2005 documentation, you can locate the options for the compiler by looking for "compiler options" in the index.</span></span>|  
|`extension`|<span data-ttu-id="a39ee-118">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="a39ee-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="a39ee-119">言語プロバイダーのソース ファイルによって使用されるファイル名拡張子のセミコロンで区切った一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="a39ee-119">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="a39ee-120">たとえば、".cs"と指定します。</span><span class="sxs-lookup"><span data-stu-id="a39ee-120">For example, ".cs".</span></span>|  
|`language`|<span data-ttu-id="a39ee-121">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="a39ee-121">Required attribute.</span></span><br /><br /> <span data-ttu-id="a39ee-122">言語プロバイダーによってサポートされる言語名のセミコロン区切りの一覧を提供します。</span><span class="sxs-lookup"><span data-stu-id="a39ee-122">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="a39ee-123">たとえば、「c# 以外の場合は cs; csharp」です。</span><span class="sxs-lookup"><span data-stu-id="a39ee-123">For example, "c#;cs;csharp".</span></span>|  
|`type`|<span data-ttu-id="a39ee-124">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="a39ee-124">Required attribute.</span></span><br /><br /> <span data-ttu-id="a39ee-125">プロバイダーの実装を含むアセンブリの名前を含め、言語プロバイダーの型名を指定します。</span><span class="sxs-lookup"><span data-stu-id="a39ee-125">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="a39ee-126">型名で定義されている要件を満たす必要がある[完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)です。</span><span class="sxs-lookup"><span data-stu-id="a39ee-126">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`warningLevel`|<span data-ttu-id="a39ee-127">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="a39ee-127">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a39ee-128">既定のコンパイラ警告レベルを指定しますある言語プロバイダーは、コンパイルの警告をエラーとして扱いますレベルが決まります。</span><span class="sxs-lookup"><span data-stu-id="a39ee-128">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a39ee-129">子要素</span><span class="sxs-lookup"><span data-stu-id="a39ee-129">Child Elements</span></span>  
  
|<span data-ttu-id="a39ee-130">要素</span><span class="sxs-lookup"><span data-stu-id="a39ee-130">Element</span></span>|<span data-ttu-id="a39ee-131">説明</span><span class="sxs-lookup"><span data-stu-id="a39ee-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a39ee-132">\<providerOption > 要素</span><span class="sxs-lookup"><span data-stu-id="a39ee-132">\<providerOption> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|<span data-ttu-id="a39ee-133">言語プロバイダーのコンパイラ バージョン属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="a39ee-133">Specifies compiler version attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a39ee-134">親要素</span><span class="sxs-lookup"><span data-stu-id="a39ee-134">Parent Elements</span></span>  
  
|<span data-ttu-id="a39ee-135">要素</span><span class="sxs-lookup"><span data-stu-id="a39ee-135">Element</span></span>|<span data-ttu-id="a39ee-136">説明</span><span class="sxs-lookup"><span data-stu-id="a39ee-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a39ee-137">\<configuration> 要素</span><span class="sxs-lookup"><span data-stu-id="a39ee-137">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="a39ee-138">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="a39ee-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="a39ee-139">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="a39ee-139">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="a39ee-140">使用可能な言語プロバイダーのコンパイラ構成設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="a39ee-140">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="a39ee-141">\<compilers> 要素</span><span class="sxs-lookup"><span data-stu-id="a39ee-141">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="a39ee-142">コンパイラ構成要素のコンテナー0 個以上含む`<compiler>`要素。</span><span class="sxs-lookup"><span data-stu-id="a39ee-142">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a39ee-143">コメント</span><span class="sxs-lookup"><span data-stu-id="a39ee-143">Remarks</span></span>  
 <span data-ttu-id="a39ee-144">各`<compiler>`要素は、特定の言語プロバイダーのコンパイラ構成属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="a39ee-144">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="a39ee-145">プロバイダーでは、 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> 、特定の言語のクラス、`<compiler>`要素は、コンパイラおよび言語プロバイダーのコード ジェネレーターの設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="a39ee-145">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>  
  
 <span data-ttu-id="a39ee-146">.NET Framework は、マシン構成ファイル (Machine.config) 内でコンパイラの初期設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="a39ee-146">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="a39ee-147">開発者やコンパイラ ベンダーは、新しい <xref:System.CodeDom.Compiler.CodeDomProvider> の実装のために構成設定を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="a39ee-147">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="a39ee-148"><xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> メソッドを使用して、プログラムによってコンピューターの言語プロバイダーとコンパイラ構成の設定を列挙します。</span><span class="sxs-lookup"><span data-stu-id="a39ee-148">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
 <span data-ttu-id="a39ee-149">アプリケーションまたは Web 構成ファイル内のコンパイラ要素では、補完したり、コンピューターの構成ファイル設定を上書きすることができます。</span><span class="sxs-lookup"><span data-stu-id="a39ee-149">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="a39ee-150">1 つ以上のプロバイダー実装が同じ言語の名前または同じのファイル拡張子に対して構成されている場合、最後の一致する構成は、その言語名またはファイル拡張子の前の構成済みのプロバイダーをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="a39ee-150">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="a39ee-151">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="a39ee-151">Configuration File</span></span>  
 <span data-ttu-id="a39ee-152">この要素は、マシン構成ファイルとアプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="a39ee-152">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a39ee-153">例</span><span class="sxs-lookup"><span data-stu-id="a39ee-153">Example</span></span>  
 <span data-ttu-id="a39ee-154">次の例は、一般的なコンパイラ構成要素を示しています。</span><span class="sxs-lookup"><span data-stu-id="a39ee-154">The following example illustrates a typical compiler configuration element.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler  
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=2.0.3600.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a39ee-155">参照</span><span class="sxs-lookup"><span data-stu-id="a39ee-155">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="a39ee-156">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="a39ee-156">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="a39ee-157">\<compilers> 要素</span><span class="sxs-lookup"><span data-stu-id="a39ee-157">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
 [<span data-ttu-id="a39ee-158">完全修飾型名の指定</span><span class="sxs-lookup"><span data-stu-id="a39ee-158">Specifying Fully Qualified Type Names</span></span>](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
 <span data-ttu-id="a39ee-159">[コンパイル (ASP.NET 設定スキーマ) のコンパイラのコンパイラ要素](https://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a39ee-159">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e(v=vs.100))</span></span>
