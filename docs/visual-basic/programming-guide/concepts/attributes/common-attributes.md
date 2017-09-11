---
title: "一般的な属性 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9adb5cb378701c8d06a3fa28bad44dc857026b5a
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="common-attributes-visual-basic"></a><span data-ttu-id="5b024-102">一般的な属性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b024-102">Common Attributes (Visual Basic)</span></span>
<span data-ttu-id="5b024-103">このトピックでは、Visual Basic プログラムで最もよく使用される属性について説明します。</span><span class="sxs-lookup"><span data-stu-id="5b024-103">This topic describes the attributes that are most commonly used in Visual Basic programs.</span></span>  
  
-   [<span data-ttu-id="5b024-104">グローバル属性</span><span class="sxs-lookup"><span data-stu-id="5b024-104">Global Attributes</span></span>](#Global)  
  
-   [<span data-ttu-id="5b024-105">旧式で属性</span><span class="sxs-lookup"><span data-stu-id="5b024-105">Obsolete Attribute</span></span>](#Obsolete)  
  
-   [<span data-ttu-id="5b024-106">条件付きの属性</span><span class="sxs-lookup"><span data-stu-id="5b024-106">Conditional Attribute</span></span>](#Conditional)  
  
-   [<span data-ttu-id="5b024-107">呼び出し元情報属性</span><span class="sxs-lookup"><span data-stu-id="5b024-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
-   [<span data-ttu-id="5b024-108">Visual Basic の属性</span><span class="sxs-lookup"><span data-stu-id="5b024-108">Visual Basic Attributes</span></span>](#VB)  
  
##  <span data-ttu-id="5b024-109"><a name="Global"></a>グローバル属性</span><span class="sxs-lookup"><span data-stu-id="5b024-109"><a name="Global"></a> Global Attributes</span></span>  
 <span data-ttu-id="5b024-110">ほとんどの属性は、クラスやメソッドなどの特定の言語要素に適用されます。ただし、いくつかの属性がグローバルななど、アセンブリ全体またはモジュールに適用します。</span><span class="sxs-lookup"><span data-stu-id="5b024-110">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="5b024-111">たとえば、<xref:System.Reflection.AssemblyVersionAttribute>属性は、次のように、アセンブリにバージョン情報を埋め込むを使用することができます:</xref:System.Reflection.AssemblyVersionAttribute></span><span class="sxs-lookup"><span data-stu-id="5b024-111">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```vb  
<Assembly: AssemblyVersion("1.0.0.0")>  
```  
  
 <span data-ttu-id="5b024-112">グローバル属性は、いずれかの後、ソース コードに表示されます。 最上位`Imports`ステートメントと型、モジュール、または名前空間宣言の前にします。</span><span class="sxs-lookup"><span data-stu-id="5b024-112">Global attributes appear in the source code after any top-level`Imports` statements and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="5b024-113">グローバル属性が複数のソース ファイルで使用できますが、1 つのコンパイルのパスでファイルをコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b024-113">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="5b024-114">Visual Basic プロジェクトで、一般に (Visual Studio でプロジェクトを作成するときに、ファイルが自動的に作成されます) AssemblyInfo.vb ファイル内にグローバル属性が配置されています。</span><span class="sxs-lookup"><span data-stu-id="5b024-114">For Visual Basic projects, global attributes are generally put in the AssemblyInfo.vb file (the file is created automatically when you create a project in Visual Studio).</span></span>  
  
 <span data-ttu-id="5b024-115">アセンブリの属性は、アセンブリに関する情報を提供する値です。</span><span class="sxs-lookup"><span data-stu-id="5b024-115">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="5b024-116">これらは、次のカテゴリに分類されます。</span><span class="sxs-lookup"><span data-stu-id="5b024-116">They fall into the following categories:</span></span>  
  
-   <span data-ttu-id="5b024-117">アセンブリの id 属性</span><span class="sxs-lookup"><span data-stu-id="5b024-117">Assembly identity attributes</span></span>  
  
-   <span data-ttu-id="5b024-118">情報属性</span><span class="sxs-lookup"><span data-stu-id="5b024-118">Informational attributes</span></span>  
  
-   <span data-ttu-id="5b024-119">アセンブリ マニフェスト属性</span><span class="sxs-lookup"><span data-stu-id="5b024-119">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="5b024-120">アセンブリ ID 属性</span><span class="sxs-lookup"><span data-stu-id="5b024-120">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="5b024-121">(厳密な名前で、該当する場合) の&3; つの属性がアセンブリの id を決定します。 名前、バージョン、およびカルチャ。</span><span class="sxs-lookup"><span data-stu-id="5b024-121">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="5b024-122">これらの属性は、アセンブリの完全名を形成され、コードで参照するときに必要なれます。</span><span class="sxs-lookup"><span data-stu-id="5b024-122">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="5b024-123">アセンブリのバージョンと属性を使用してカルチャを設定することができます。</span><span class="sxs-lookup"><span data-stu-id="5b024-123">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="5b024-124">ただし、name の値をコンパイラは、Visual Studio IDE では設定、[アセンブリ情報 ダイアログ ボックス](https://docs.microsoft.com/visualstudio/ide/reference/assembly-information-dialog-box)、またはアセンブリ リンカー (Al.exe) アセンブリが作成されると、アセンブリ マニフェストを含むファイルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="5b024-124">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="5b024-125"><xref:System.Reflection.AssemblyFlagsAttribute>属性は、アセンブリの複数のコピーが共存できるかどうかを指定します</xref:System.Reflection.AssemblyFlagsAttribute>。</span><span class="sxs-lookup"><span data-stu-id="5b024-125">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="5b024-126">次の表は、id 属性を示します。</span><span class="sxs-lookup"><span data-stu-id="5b024-126">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="5b024-127">属性</span><span class="sxs-lookup"><span data-stu-id="5b024-127">Attribute</span></span>|<span data-ttu-id="5b024-128">目的</span><span class="sxs-lookup"><span data-stu-id="5b024-128">Purpose</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="5b024-129"><xref:System.Reflection.AssemblyName></xref:System.Reflection.AssemblyName></span><span class="sxs-lookup"><span data-stu-id="5b024-129"><xref:System.Reflection.AssemblyName></span></span>|<span data-ttu-id="5b024-130">アセンブリの id を完全に記述します。</span><span class="sxs-lookup"><span data-stu-id="5b024-130">Fully describes the identity of an assembly.</span></span>|  
|<span data-ttu-id="5b024-131"><xref:System.Reflection.AssemblyVersionAttribute></xref:System.Reflection.AssemblyVersionAttribute></span><span class="sxs-lookup"><span data-stu-id="5b024-131"><xref:System.Reflection.AssemblyVersionAttribute></span></span>|<span data-ttu-id="5b024-132">アセンブリのバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="5b024-132">Specifies the version of an assembly.</span></span>|  
|<span data-ttu-id="5b024-133"><xref:System.Reflection.AssemblyCultureAttribute></xref:System.Reflection.AssemblyCultureAttribute></span><span class="sxs-lookup"><span data-stu-id="5b024-133"><xref:System.Reflection.AssemblyCultureAttribute></span></span>|<span data-ttu-id="5b024-134">アセンブリがサポートするカルチャを指定します。</span><span class="sxs-lookup"><span data-stu-id="5b024-134">Specifies which culture the assembly supports.</span></span>|  
|<span data-ttu-id="5b024-135"><xref:System.Reflection.AssemblyFlagsAttribute></xref:System.Reflection.AssemblyFlagsAttribute></span><span class="sxs-lookup"><span data-stu-id="5b024-135"><xref:System.Reflection.AssemblyFlagsAttribute></span></span>|<span data-ttu-id="5b024-136">アセンブリが同じプロセスで、または同じアプリケーション ドメインでは、同じコンピューターにサイド バイ サイド実行をサポートするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5b024-136">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="5b024-137">情報属性</span><span class="sxs-lookup"><span data-stu-id="5b024-137">Informational Attributes</span></span>  
 <span data-ttu-id="5b024-138">情報属性は、追加の会社情報または製品情報をアセンブリに指定する場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="5b024-138">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="5b024-139">次の表に、情報の属性で定義されている、<xref:System.Reflection?displayProperty=fullName>名前空間</xref:System.Reflection?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="5b024-139">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=fullName> namespace.</span></span>  
  
|<span data-ttu-id="5b024-140">属性</span><span class="sxs-lookup"><span data-stu-id="5b024-140">Attribute</span></span>|<span data-ttu-id="5b024-141">目的</span><span class="sxs-lookup"><span data-stu-id="5b024-141">Purpose</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="5b024-142"><xref:System.Reflection.AssemblyProductAttribute></xref:System.Reflection.AssemblyProductAttribute></span><span class="sxs-lookup"><span data-stu-id="5b024-142"><xref:System.Reflection.AssemblyProductAttribute></span></span>|<span data-ttu-id="5b024-143">アセンブリ マニフェストの製品名を指定するカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="5b024-143">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<span data-ttu-id="5b024-144"><xref:System.Reflection.AssemblyTrademarkAttribute></xref:System.Reflection.AssemblyTrademarkAttribute></span><span class="sxs-lookup"><span data-stu-id="5b024-144"><xref:System.Reflection.AssemblyTrademarkAttribute></span></span>|<span data-ttu-id="5b024-145">アセンブリ マニフェストの商標を指定するカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="5b024-145">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<span data-ttu-id="5b024-146"><xref:System.Reflection.AssemblyInformationalVersionAttribute></xref:System.Reflection.AssemblyInformationalVersionAttribute></span><span class="sxs-lookup"><span data-stu-id="5b024-146"><xref:System.Reflection.AssemblyInformationalVersionAttribute></span></span>|<span data-ttu-id="5b024-147">アセンブリ マニフェストの補足バージョンを指定するカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="5b024-147">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<span data-ttu-id="5b024-148"><xref:System.Reflection.AssemblyCompanyAttribute></xref:System.Reflection.AssemblyCompanyAttribute></span><span class="sxs-lookup"><span data-stu-id="5b024-148"><xref:System.Reflection.AssemblyCompanyAttribute></span></span>|<span data-ttu-id="5b024-149">アセンブリ マニフェストの会社名を指定するカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="5b024-149">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<span data-ttu-id="5b024-150"><xref:System.Reflection.AssemblyCopyrightAttribute></xref:System.Reflection.AssemblyCopyrightAttribute></span><span class="sxs-lookup"><span data-stu-id="5b024-150"><xref:System.Reflection.AssemblyCopyrightAttribute></span></span>|<span data-ttu-id="5b024-151">アセンブリ マニフェストの著作権情報を指定するカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="5b024-151">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<span data-ttu-id="5b024-152"><xref:System.Reflection.AssemblyFileVersionAttribute></xref:System.Reflection.AssemblyFileVersionAttribute></span><span class="sxs-lookup"><span data-stu-id="5b024-152"><xref:System.Reflection.AssemblyFileVersionAttribute></span></span>|<span data-ttu-id="5b024-153">Win32 ファイルのバージョンのリソースの特定のバージョン番号を使用するコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="5b024-153">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<span data-ttu-id="5b024-154"><xref:System.CLSCompliantAttribute></xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="5b024-154"><xref:System.CLSCompliantAttribute></span></span>|<span data-ttu-id="5b024-155">アセンブリが共通言語仕様 (CLS) に準拠しているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="5b024-155">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="5b024-156">アセンブリ マニフェスト属性</span><span class="sxs-lookup"><span data-stu-id="5b024-156">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="5b024-157">アセンブリ マニフェスト属性を使用すると、アセンブリ マニフェストで情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5b024-157">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="5b024-158">これには、タイトル、説明、既定のエイリアス、および構成が含まれます。</span><span class="sxs-lookup"><span data-stu-id="5b024-158">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="5b024-159">次の表で定義されているアセンブリのマニフェスト属性、<xref:System.Reflection?displayProperty=fullName>名前空間</xref:System.Reflection?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="5b024-159">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=fullName> namespace.</span></span>  
  
|<span data-ttu-id="5b024-160">属性</span><span class="sxs-lookup"><span data-stu-id="5b024-160">Attribute</span></span>|<span data-ttu-id="5b024-161">目的</span><span class="sxs-lookup"><span data-stu-id="5b024-161">Purpose</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="5b024-162"><xref:System.Reflection.AssemblyTitleAttribute></xref:System.Reflection.AssemblyTitleAttribute></span><span class="sxs-lookup"><span data-stu-id="5b024-162"><xref:System.Reflection.AssemblyTitleAttribute></span></span>|<span data-ttu-id="5b024-163">アセンブリ マニフェストのアセンブリのタイトルを指定するカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="5b024-163">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<span data-ttu-id="5b024-164"><xref:System.Reflection.AssemblyDescriptionAttribute></xref:System.Reflection.AssemblyDescriptionAttribute></span><span class="sxs-lookup"><span data-stu-id="5b024-164"><xref:System.Reflection.AssemblyDescriptionAttribute></span></span>|<span data-ttu-id="5b024-165">アセンブリ マニフェストのアセンブリの説明を指定するカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="5b024-165">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<span data-ttu-id="5b024-166"><xref:System.Reflection.AssemblyConfigurationAttribute></xref:System.Reflection.AssemblyConfigurationAttribute></span><span class="sxs-lookup"><span data-stu-id="5b024-166"><xref:System.Reflection.AssemblyConfigurationAttribute></span></span>|<span data-ttu-id="5b024-167">アセンブリ マニフェストを (製品版またはデバッグ) などのアセンブリの構成を指定するカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="5b024-167">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<span data-ttu-id="5b024-168"><xref:System.Reflection.AssemblyDefaultAliasAttribute></xref:System.Reflection.AssemblyDefaultAliasAttribute></span><span class="sxs-lookup"><span data-stu-id="5b024-168"><xref:System.Reflection.AssemblyDefaultAliasAttribute></span></span>|<span data-ttu-id="5b024-169">アセンブリ マニフェストのわかりやすい既定のエイリアスを定義します。</span><span class="sxs-lookup"><span data-stu-id="5b024-169">Defines a friendly default alias for an assembly manifest</span></span>|  
  
##  <span data-ttu-id="5b024-170"><a name="Obsolete"></a>旧式で属性</span><span class="sxs-lookup"><span data-stu-id="5b024-170"><a name="Obsolete"></a> Obsolete Attribute</span></span>  
 <span data-ttu-id="5b024-171">`Obsolete`属性は、いずれかの使用は推奨されなくプログラム エンティティをマークします。</span><span class="sxs-lookup"><span data-stu-id="5b024-171">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="5b024-172">不使用とマーク エンティティの使用、警告または属性の構成方法に応じて、エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="5b024-172">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="5b024-173">例:</span><span class="sxs-lookup"><span data-stu-id="5b024-173">For example:</span></span>  
  
```vb  
<System.Obsolete("use class B")>   
Class A  
    Sub Method()  
    End Sub  
End Class  
  
Class B  
    <System.Obsolete("use NewMethod", True)>   
    Sub OldMethod()  
    End Sub  
  
    Sub NewMethod()  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="5b024-174">この例では、`Obsolete`クラスに属性が適用される`A`とメソッドに`B.OldMethod`します。</span><span class="sxs-lookup"><span data-stu-id="5b024-174">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="5b024-175">属性コンス トラクターの&2; 番目の引数が適用されるので`B.OldMethod`に設定されている`true`、クラスを使用する一方、このメソッドは、コンパイラ エラーになります`A`生成だけを警告されます。</span><span class="sxs-lookup"><span data-stu-id="5b024-175">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="5b024-176">呼び出す`B.NewMethod`で警告またはエラー。</span><span class="sxs-lookup"><span data-stu-id="5b024-176">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="5b024-177">属性コンス トラクターの&1; 番目の引数として指定された文字列が警告またはエラーの一部として表示されます。</span><span class="sxs-lookup"><span data-stu-id="5b024-177">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="5b024-178">たとえば、前の定義と共に使用する場合、次のコードには&2; つの警告と&1; つのエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="5b024-178">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```vb  
' Generates 2 warnings:  
' Dim a As New A  
' Generate no errors or warnings:  
  
Dim b As New B  
b.NewMethod()  
  
' Generates an error, terminating compilation:  
' b.OldMethod()  
```  
  
 <span data-ttu-id="5b024-179">クラスの&2; つの警告`A`生成: クラスの参照の宣言の&1; つ、クラス コンス トラクターのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="5b024-179">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="5b024-180">`Obsolete`引数を指定せずに属性を使用できますが、理由の説明を含む、アイテムは今後使用しませんし、代わりに使用するをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5b024-180">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="5b024-181">`Obsolete`属性は、単一目的の属性であり、属性を使用するすべてのエンティティに適用できます。</span><span class="sxs-lookup"><span data-stu-id="5b024-181">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="5b024-182">`Obsolete`<xref:System.ObsoleteAttribute>。</xref:System.ObsoleteAttribute>エイリアスします。</span><span class="sxs-lookup"><span data-stu-id="5b024-182">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
##  <span data-ttu-id="5b024-183"><a name="Conditional"></a>条件付きの属性</span><span class="sxs-lookup"><span data-stu-id="5b024-183"><a name="Conditional"></a> Conditional Attribute</span></span>  
 <span data-ttu-id="5b024-184">`Conditional`属性は、メソッドの実行をプリプロセッサ識別子に依存します。</span><span class="sxs-lookup"><span data-stu-id="5b024-184">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="5b024-185">`Conditional`属性は、エイリアスを<xref:System.Diagnostics.ConditionalAttribute>、メソッド、または属性クラスに適用できると</xref:System.Diagnostics.ConditionalAttribute></span><span class="sxs-lookup"><span data-stu-id="5b024-185">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="5b024-186">この例では`Conditional`を有効にする、またはプログラム固有の診断情報の表示を無効にするメソッドに適用します。</span><span class="sxs-lookup"><span data-stu-id="5b024-186">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
```vb  
#Const TRACE_ON = True  
Imports System  
Imports System.Diagnostics  
Module TestConditionalAttribute  
    Public Class Trace  
        <Conditional("TRACE_ON")>   
        Public Shared Sub Msg(ByVal msg As String)  
            Console.WriteLine(msg)  
        End Sub  
  
    End Class  
  
    Sub Main()  
        Trace.Msg("Now in Main...")  
        Console.WriteLine("Done.")  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="5b024-187">場合、`TRACE_ON`識別子が定義されていませんが、トレース出力は表示されません。</span><span class="sxs-lookup"><span data-stu-id="5b024-187">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="5b024-188">`Conditional`属性は子と共によく使用、`DEBUG`次のようなトレースとデバッグ ビルドでは、内にないリリース ビルドのログ機能を有効にする識別子。</span><span class="sxs-lookup"><span data-stu-id="5b024-188">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```vb  
<Conditional("DEBUG")>   
Shared Sub DebugMethod()  
  
End Sub  
```  
  
 <span data-ttu-id="5b024-189">条件付きとしてマークされたメソッドが呼び出されると、指定のプリプロセッサ シンボルの有無は、呼び出しが含まれているか、省略したかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="5b024-189">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="5b024-190">シンボルが定義されている、呼び出しが行われます。それ以外の場合、呼び出しは省略されます。</span><span class="sxs-lookup"><span data-stu-id="5b024-190">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="5b024-191">使用して`Conditional`は明快では、内のメソッドを囲む代わりに洗練され、エラーが減り`#if…#endif`ブロックは、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="5b024-191">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```vb  
#If DEBUG Then  
    Sub ConditionalMethod()  
    End Sub  
#End If  
```  
  
 <span data-ttu-id="5b024-192">条件付きメソッドでは、クラスまたは構造体の宣言のメソッドである必要があり、戻り値を持つことはできません。</span><span class="sxs-lookup"><span data-stu-id="5b024-192">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="5b024-193">複数の識別子を使用します。</span><span class="sxs-lookup"><span data-stu-id="5b024-193">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="5b024-194">メソッドに複数`Conditional`属性、メソッドの呼び出しが含まれる少なくとも&1; つの条件付きのシンボルが定義されている場合 (つまり、シンボルが論理的に一緒にリンク OR 演算子を使用して)。</span><span class="sxs-lookup"><span data-stu-id="5b024-194">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="5b024-195">この例では、いずれかの存在に`A`または`B`メソッドの呼び出しになります。</span><span class="sxs-lookup"><span data-stu-id="5b024-195">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```vb  
<Conditional("A"), Conditional("B")>   
Shared Sub DoIfAorB()  
  
End Sub  
```  
  
 <span data-ttu-id="5b024-196">AND 演算子を使用してシンボルを論理的にリンクの効果を実現するのには、シリアルの条件付きメソッドを定義できます。</span><span class="sxs-lookup"><span data-stu-id="5b024-196">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="5b024-197">場合にだけの次の&2; つ目のメソッドの実行など`A`と`B`が定義されています。</span><span class="sxs-lookup"><span data-stu-id="5b024-197">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
```vb  
<Conditional("A")>   
Shared Sub DoIfA()  
    DoIfAandB()  
End Sub  
  
<Conditional("B")>   
Shared Sub DoIfAandB()  
    ' Code to execute when both A and B are defined...  
End Sub  
```  
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="5b024-198">属性クラスでの条件の使用</span><span class="sxs-lookup"><span data-stu-id="5b024-198">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="5b024-199">`Conditional`属性は、属性クラスの定義にも適用できます。</span><span class="sxs-lookup"><span data-stu-id="5b024-199">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="5b024-200">この例では、カスタム属性で`Documentation`デバッグが定義されている場合、メタデータに情報を追加のみができます。</span><span class="sxs-lookup"><span data-stu-id="5b024-200">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
```vb  
<Conditional("DEBUG")>   
Public Class Documentation  
    Inherits System.Attribute  
    Private text As String  
    Sub New(ByVal doc_text As String)  
        text = doc_text  
    End Sub  
End Class  
  
Class SampleClass  
    ' This attribute will only be included if DEBUG is defined.  
    <Documentation("This method displays an integer.")>   
    Shared Sub DoWork(ByVal i As Integer)  
        System.Console.WriteLine(i)  
    End Sub  
End Class  
```  
  
##  <span data-ttu-id="5b024-201"><a name="CallerInfo"></a>呼び出し元情報属性</span><span class="sxs-lookup"><span data-stu-id="5b024-201"><a name="CallerInfo"></a> Caller Info Attributes</span></span>  
 <span data-ttu-id="5b024-202">呼び出し元情報の属性を使用すると、メソッドへの呼び出し元に関する情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="5b024-202">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="5b024-203">ソース コードのファイル パス、ソース コードと、呼び出し元のメンバー名の行番号を取得できます。</span><span class="sxs-lookup"><span data-stu-id="5b024-203">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="5b024-204">呼び出し元情報を取得するには、省略可能なパラメーターに適用される属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="5b024-204">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="5b024-205">省略可能な各パラメーターでは、既定値を指定します。</span><span class="sxs-lookup"><span data-stu-id="5b024-205">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="5b024-206">次の表に、呼び出し元情報属性で定義されている、<xref:System.Runtime.CompilerServices?displayProperty=fullName>名前空間:</xref:System.Runtime.CompilerServices?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="5b024-206">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=fullName> namespace:</span></span>  
  
|<span data-ttu-id="5b024-207">属性</span><span class="sxs-lookup"><span data-stu-id="5b024-207">Attribute</span></span>|<span data-ttu-id="5b024-208">説明</span><span class="sxs-lookup"><span data-stu-id="5b024-208">Description</span></span>|<span data-ttu-id="5b024-209">型</span><span class="sxs-lookup"><span data-stu-id="5b024-209">Type</span></span>|  
|---|---|---|  
|<span data-ttu-id="5b024-210"><xref:System.Runtime.CompilerServices.CallerFilePathAttribute></xref:System.Runtime.CompilerServices.CallerFilePathAttribute></span><span class="sxs-lookup"><span data-stu-id="5b024-210"><xref:System.Runtime.CompilerServices.CallerFilePathAttribute></span></span>|<span data-ttu-id="5b024-211">呼び出し元を含むソース ファイルのフル パスです。</span><span class="sxs-lookup"><span data-stu-id="5b024-211">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="5b024-212">これは、コンパイル時にパスです。</span><span class="sxs-lookup"><span data-stu-id="5b024-212">This is the path at compile time.</span></span>|`String`|  
|<span data-ttu-id="5b024-213"><xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></span><span class="sxs-lookup"><span data-stu-id="5b024-213"><xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></span></span>|<span data-ttu-id="5b024-214">メソッドの呼び出し元のソース ファイルの行番号。</span><span class="sxs-lookup"><span data-stu-id="5b024-214">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<span data-ttu-id="5b024-215"><xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></span><span class="sxs-lookup"><span data-stu-id="5b024-215"><xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></span></span>|<span data-ttu-id="5b024-216">メソッド名または呼び出し元のプロパティ名。</span><span class="sxs-lookup"><span data-stu-id="5b024-216">Method name or property name of the caller.</span></span> <span data-ttu-id="5b024-217">詳細については、次を参照してください。[呼び出し元情報 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md)します。</span><span class="sxs-lookup"><span data-stu-id="5b024-217">For more information, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="5b024-218">呼び出し元情報属性の詳細については、次を参照してください。[呼び出し元情報 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md)します。</span><span class="sxs-lookup"><span data-stu-id="5b024-218">For more information about the Caller Info attributes, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>  
  
##  <span data-ttu-id="5b024-219"><a name="VB"></a>Visual Basic の属性</span><span class="sxs-lookup"><span data-stu-id="5b024-219"><a name="VB"></a> Visual Basic Attributes</span></span>  
 <span data-ttu-id="5b024-220">次の表は、Visual Basic に固有の属性を示します。</span><span class="sxs-lookup"><span data-stu-id="5b024-220">The following table lists the attributes that are specific to Visual Basic.</span></span>  
  
|<span data-ttu-id="5b024-221">属性</span><span class="sxs-lookup"><span data-stu-id="5b024-221">Attribute</span></span>|<span data-ttu-id="5b024-222">目的</span><span class="sxs-lookup"><span data-stu-id="5b024-222">Purpose</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="5b024-223"><xref:Microsoft.VisualBasic.ComClassAttribute></xref:Microsoft.VisualBasic.ComClassAttribute></span><span class="sxs-lookup"><span data-stu-id="5b024-223"><xref:Microsoft.VisualBasic.ComClassAttribute></span></span>|<span data-ttu-id="5b024-224">クラスを COM オブジェクトとして公開する必要があることをコンパイラを示します。</span><span class="sxs-lookup"><span data-stu-id="5b024-224">Indicates to the compiler that the class should be exposed as a COM object.</span></span>|  
|<span data-ttu-id="5b024-225"><xref:Microsoft.VisualBasic.HideModuleNameAttribute></xref:Microsoft.VisualBasic.HideModuleNameAttribute></span><span class="sxs-lookup"><span data-stu-id="5b024-225"><xref:Microsoft.VisualBasic.HideModuleNameAttribute></span></span>|<span data-ttu-id="5b024-226">モジュール メンバー モジュールに必要な修飾子のみを使用してアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="5b024-226">Allows module members to be accessed using only the qualification needed for the module.</span></span>|  
|<span data-ttu-id="5b024-227"><xref:Microsoft.VisualBasic.VBFixedStringAttribute></xref:Microsoft.VisualBasic.VBFixedStringAttribute></span><span class="sxs-lookup"><span data-stu-id="5b024-227"><xref:Microsoft.VisualBasic.VBFixedStringAttribute></span></span>|<span data-ttu-id="5b024-228">固定長文字列のサイズを使用するための構造での入力し、出力ファイルを使用して指定の関数です。</span><span class="sxs-lookup"><span data-stu-id="5b024-228">Specifies the size of a fixed-length string in a structure for use with file input and output functions.</span></span>|  
|<span data-ttu-id="5b024-229"><xref:Microsoft.VisualBasic.VBFixedArrayAttribute></xref:Microsoft.VisualBasic.VBFixedArrayAttribute></span><span class="sxs-lookup"><span data-stu-id="5b024-229"><xref:Microsoft.VisualBasic.VBFixedArrayAttribute></span></span>|<span data-ttu-id="5b024-230">固定長配列のサイズを使用するための構造での入力し、出力ファイルを使用して指定の関数です。</span><span class="sxs-lookup"><span data-stu-id="5b024-230">Specifies the size of a fixed array in a structure for use with file input and output functions.</span></span>|  
  
### <a name="comclassattribute"></a><span data-ttu-id="5b024-231">大きく</span><span class="sxs-lookup"><span data-stu-id="5b024-231">COMClassAttribute</span></span>  
 <span data-ttu-id="5b024-232">使用`COMClassAttribute`を Visual Basic から COM コンポーネントを作成するプロセスを簡略化します。</span><span class="sxs-lookup"><span data-stu-id="5b024-232">Use `COMClassAttribute` to simplify the process of creating COM components from Visual Basic.</span></span> <span data-ttu-id="5b024-233">COM オブジェクトは、.NET Framework アセンブリおよびせずにかなり異なる`COMClassAttribute`さまざまな Visual Basic から COM オブジェクトを生成する手順に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b024-233">COM objects are considerably different from .NET Framework assemblies, and without `COMClassAttribute`, you need to follow a number of steps to generate a COM object from Visual Basic.</span></span> <span data-ttu-id="5b024-234">マークされたクラスの`COMClassAttribute`コンパイラは、次の手順の多くを自動的に実行します。</span><span class="sxs-lookup"><span data-stu-id="5b024-234">For classes marked with `COMClassAttribute`, the compiler performs many of these steps automatically.</span></span>  
  
### <a name="hidemodulenameattribute"></a><span data-ttu-id="5b024-235">HideModuleNameAttribute</span><span class="sxs-lookup"><span data-stu-id="5b024-235">HideModuleNameAttribute</span></span>  
 <span data-ttu-id="5b024-236">使用`HideModuleNameAttribute`モジュール メンバー モジュールに必要な修飾子のみを使用してアクセスを許可するようにします。</span><span class="sxs-lookup"><span data-stu-id="5b024-236">Use `HideModuleNameAttribute` to allow module members to be accessed by using only the qualification needed for the module.</span></span>  
  
### <a name="vbfixedstringattribute"></a><span data-ttu-id="5b024-237">VBFixedStringAttribute</span><span class="sxs-lookup"><span data-stu-id="5b024-237">VBFixedStringAttribute</span></span>  
 <span data-ttu-id="5b024-238">使用`VBFixedStringAttribute`固定長文字列を作成する Visual Basic を強制的にします。</span><span class="sxs-lookup"><span data-stu-id="5b024-238">Use `VBFixedStringAttribute` to force Visual Basic to create a fixed-length string.</span></span> <span data-ttu-id="5b024-239">既定では、可変長の文字列し、この属性は、ファイルに文字列を格納するときに便利です。</span><span class="sxs-lookup"><span data-stu-id="5b024-239">Strings are of variable length by default, and this attribute is useful when storing strings to files.</span></span> <span data-ttu-id="5b024-240">次のコードでは、これを示しています。</span><span class="sxs-lookup"><span data-stu-id="5b024-240">The following code demonstrates this:</span></span>  
  
```vb  
Structure Worker  
    ' The runtime uses VBFixedString to determine   
    ' if the field should be written out as a fixed size.  
    <VBFixedString(10)> Public LastName As String  
    <VBFixedString(7)> Public Title As String  
    <VBFixedString(2)> Public Rank As String  
End Structure  
```  
  
### <a name="vbfixedarrayattribute"></a><span data-ttu-id="5b024-241">VBFixedArrayAttribute</span><span class="sxs-lookup"><span data-stu-id="5b024-241">VBFixedArrayAttribute</span></span>  
 <span data-ttu-id="5b024-242">使用`VBFixedArrayAttribute`サイズに固定されている配列を宣言します。</span><span class="sxs-lookup"><span data-stu-id="5b024-242">Use `VBFixedArrayAttribute` to declare arrays that are fixed in size.</span></span> <span data-ttu-id="5b024-243">Visual Basic の文字列のような配列は、既定では可変長のこと。</span><span class="sxs-lookup"><span data-stu-id="5b024-243">Like Visual Basic strings, arrays are of variable length by default.</span></span> <span data-ttu-id="5b024-244">この属性は、シリアル化またはファイルにデータを書き込む場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="5b024-244">This attribute is useful when serializing or writing data to files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b024-245">関連項目</span><span class="sxs-lookup"><span data-stu-id="5b024-245">See Also</span></span>  
 <span data-ttu-id="5b024-246"><xref:System.Reflection></xref:System.Reflection></span><span class="sxs-lookup"><span data-stu-id="5b024-246"><xref:System.Reflection></span></span>   
 <span data-ttu-id="5b024-247"><xref:System.Attribute></xref:System.Attribute></span><span class="sxs-lookup"><span data-stu-id="5b024-247"><xref:System.Attribute></span></span>   
<span data-ttu-id="5b024-248"> [Visual Basic のプログラミング ガイド](../../../../visual-basic/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="5b024-248"> [Visual Basic Programming Guide](../../../../visual-basic/programming-guide/index.md) </span></span>  
<span data-ttu-id="5b024-249"> [属性](https://msdn.microsoft.com/library/5x6cd29c) </span><span class="sxs-lookup"><span data-stu-id="5b024-249"> [Attributes](https://msdn.microsoft.com/library/5x6cd29c) </span></span>  
<span data-ttu-id="5b024-250"> [リフレクション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="5b024-250"> [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span></span>  
<span data-ttu-id="5b024-251"> [リフレクション (Visual Basic) を使用して属性へのアクセス](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="5b024-251"> [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)</span></span>
