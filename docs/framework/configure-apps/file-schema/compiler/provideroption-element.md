---
title: '&lt;providerOption&gt;要素'
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fa3410cc2c8812c59528676bfad6cd7e887c5f73
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltprovideroptiongt-element"></a><span data-ttu-id="aefe7-102">&lt;providerOption&gt;要素</span><span class="sxs-lookup"><span data-stu-id="aefe7-102">&lt;providerOption&gt; Element</span></span>
<span data-ttu-id="aefe7-103">言語プロバイダーのコンパイラ バージョン属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="aefe7-103">Specifies the compiler version attributes for a language provider.</span></span>  
  
 <span data-ttu-id="aefe7-104">\<configuration >要素</span><span class="sxs-lookup"><span data-stu-id="aefe7-104">\<configuration Element></span></span>  
<span data-ttu-id="aefe7-105">\<system.codedom>要素</span><span class="sxs-lookup"><span data-stu-id="aefe7-105">\<system.codedom Element></span></span>  
<span data-ttu-id="aefe7-106">\<compilers >要素</span><span class="sxs-lookup"><span data-stu-id="aefe7-106">\<compilers Element></span></span>  
<span data-ttu-id="aefe7-107">\<compiler> 要素</span><span class="sxs-lookup"><span data-stu-id="aefe7-107">\<compiler> Element</span></span>  
<span data-ttu-id="aefe7-108">\<providerOption > 要素</span><span class="sxs-lookup"><span data-stu-id="aefe7-108">\<providerOption> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aefe7-109">構文</span><span class="sxs-lookup"><span data-stu-id="aefe7-109">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aefe7-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="aefe7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="aefe7-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="aefe7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aefe7-112">属性</span><span class="sxs-lookup"><span data-stu-id="aefe7-112">Attributes</span></span>  
  
|<span data-ttu-id="aefe7-113">属性</span><span class="sxs-lookup"><span data-stu-id="aefe7-113">Attribute</span></span>|<span data-ttu-id="aefe7-114">説明</span><span class="sxs-lookup"><span data-stu-id="aefe7-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="aefe7-115">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="aefe7-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="aefe7-116">オプションの名前を指定しますたとえば、"CompilerVersion"です。</span><span class="sxs-lookup"><span data-stu-id="aefe7-116">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="aefe7-117">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="aefe7-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="aefe7-118">オプションの値を指定しますたとえば、"v3.5"とします。</span><span class="sxs-lookup"><span data-stu-id="aefe7-118">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aefe7-119">子要素</span><span class="sxs-lookup"><span data-stu-id="aefe7-119">Child Elements</span></span>  
 <span data-ttu-id="aefe7-120">なし。</span><span class="sxs-lookup"><span data-stu-id="aefe7-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aefe7-121">親要素</span><span class="sxs-lookup"><span data-stu-id="aefe7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="aefe7-122">要素</span><span class="sxs-lookup"><span data-stu-id="aefe7-122">Element</span></span>|<span data-ttu-id="aefe7-123">説明</span><span class="sxs-lookup"><span data-stu-id="aefe7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aefe7-124">\<configuration> 要素</span><span class="sxs-lookup"><span data-stu-id="aefe7-124">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="aefe7-125">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="aefe7-125">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="aefe7-126">\<system.codedom > 要素</span><span class="sxs-lookup"><span data-stu-id="aefe7-126">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="aefe7-127">使用可能な言語プロバイダーのコンパイラ構成設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="aefe7-127">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="aefe7-128">\<compilers> 要素</span><span class="sxs-lookup"><span data-stu-id="aefe7-128">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="aefe7-129">コンパイラ構成要素のコンテナー0 個以上含む`<compiler>`要素。</span><span class="sxs-lookup"><span data-stu-id="aefe7-129">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="aefe7-130">\<compiler> 要素</span><span class="sxs-lookup"><span data-stu-id="aefe7-130">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="aefe7-131">言語プロバイダーのコンパイラ構成属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="aefe7-131">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aefe7-132">コメント</span><span class="sxs-lookup"><span data-stu-id="aefe7-132">Remarks</span></span>  
 <span data-ttu-id="aefe7-133">.NET Framework version 3.5 では、Code Document Object Model (CodeDOM) のコード プロバイダーをサポートしますプロバイダー固有のオプションを使用して、`<providerOption>`要素。</span><span class="sxs-lookup"><span data-stu-id="aefe7-133">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="aefe7-134">.NET Framework 3.5 では、更新された .NET Framework 2.0 アセンブリに含まれてし、新しい型を含む新しいバージョン 3.5 のアセンブリを提供します。</span><span class="sxs-lookup"><span data-stu-id="aefe7-134">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="aefe7-135">Microsoft c# および Visual Basic コード プロバイダーは、.NET Framework 2.0 アセンブリに含まれるが、version 3.5 のコンパイラをサポートするために更新されました。</span><span class="sxs-lookup"><span data-stu-id="aefe7-135">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="aefe7-136">既定では、更新されたコード プロバイダーは、バージョン 2.0 コンパイラ用のコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="aefe7-136">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="aefe7-137">使用することができます、 `<providerOption>` 3.5 をターゲット コンパイラのバージョンを変更する要素。</span><span class="sxs-lookup"><span data-stu-id="aefe7-137">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="aefe7-138">これを行うには、"CompilerVersion"を指定、`name`属性との"v3.5"、`value`属性。</span><span class="sxs-lookup"><span data-stu-id="aefe7-138">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="aefe7-139">小文字の"v"のバージョン番号の前にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="aefe7-139">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="aefe7-140">ことができます、バージョン指定グローバル追加することによって、`<providerOption>`を .NET Framework 2.0 Machine.config またはルートの Web.config ファイルの要素。</span><span class="sxs-lookup"><span data-stu-id="aefe7-140">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="aefe7-141">場合は、Machine.config ファイルに 3.5 に既定のコンパイラのバージョンを更新することができますに変更する戻る、アプリケーションごとに 2.0 を使用して、`<providerOption>`アプリケーション構成ファイル内の要素。</span><span class="sxs-lookup"><span data-stu-id="aefe7-141">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="aefe7-142">CodeDOM コード プロバイダーの実装側を受け取るコンス トラクターを提供することによってカスタム オプションを処理できる、`providerOptions`型のパラメーター<xref:System.Collections.Generic.IDictionary%602>です。</span><span class="sxs-lookup"><span data-stu-id="aefe7-142">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aefe7-143">例</span><span class="sxs-lookup"><span data-stu-id="aefe7-143">Example</span></span>  
 <span data-ttu-id="aefe7-144">次の例では、そのバージョン 3.5 の c# コード プロバイダーを使用する必要がありますを指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="aefe7-144">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
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
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aefe7-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="aefe7-145">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="aefe7-146">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="aefe7-146">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="aefe7-147">\<compilers> 要素</span><span class="sxs-lookup"><span data-stu-id="aefe7-147">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
 [<span data-ttu-id="aefe7-148">完全修飾型名の指定</span><span class="sxs-lookup"><span data-stu-id="aefe7-148">Specifying Fully Qualified Type Names</span></span>](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
 [<span data-ttu-id="aefe7-149">コンパイル (ASP.NET 設定スキーマ) のコンパイラのコンパイラ要素</span><span class="sxs-lookup"><span data-stu-id="aefe7-149">compiler Element for compilers for compilation (ASP.NET Settings Schema)</span></span>](http://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)
