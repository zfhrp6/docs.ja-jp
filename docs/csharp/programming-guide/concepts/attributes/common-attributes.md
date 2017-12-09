---
title: "共通属性 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aded9c9b2e8c253eebd6c71782f0bff6ca0104ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="common-attributes-c"></a><span data-ttu-id="f6aa7-102">共通属性 (C#)</span><span class="sxs-lookup"><span data-stu-id="f6aa7-102">Common Attributes (C#)</span></span>
<span data-ttu-id="f6aa7-103">このトピックでは、C# プログラムで最もよく使用される属性について説明します。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-103">This topic describes the attributes that are most commonly used in C# programs.</span></span>  
  
-   [<span data-ttu-id="f6aa7-104">グローバル属性</span><span class="sxs-lookup"><span data-stu-id="f6aa7-104">Global Attributes</span></span>](#Global)  
  
-   [<span data-ttu-id="f6aa7-105">Obsolete 属性</span><span class="sxs-lookup"><span data-stu-id="f6aa7-105">Obsolete Attribute</span></span>](#Obsolete)  
  
-   [<span data-ttu-id="f6aa7-106">Conditional 属性</span><span class="sxs-lookup"><span data-stu-id="f6aa7-106">Conditional Attribute</span></span>](#Conditional)  
  
-   [<span data-ttu-id="f6aa7-107">呼び出し元情報属性</span><span class="sxs-lookup"><span data-stu-id="f6aa7-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
##  <a name="Global"></a> <span data-ttu-id="f6aa7-108">グローバル属性</span><span class="sxs-lookup"><span data-stu-id="f6aa7-108">Global Attributes</span></span>  
 <span data-ttu-id="f6aa7-109">ほとんどの属性は、クラスやメソッドなど、特定の言語要素に適用されます。ただし、属性の中にはグローバルなものがあり、アセンブリまたはモジュール全体に適用されます。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-109">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="f6aa7-110">たとえば、<xref:System.Reflection.AssemblyVersionAttribute> 属性は、次のように、バージョン情報をアセンブリに埋め込むときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-110">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 <span data-ttu-id="f6aa7-111">ソース コードでは、グローバル属性は、トップレベルの `using` ディレクティブより後、型、モジュール、または名前空間の宣言より前に指定します。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-111">Global attributes appear in the source code after any top-level `using` directives and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="f6aa7-112">グローバル属性は複数のソース ファイルに指定できますが、それらのファイルは、1 つのコンパイル パスでコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-112">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="f6aa7-113">C# プロジェクトでは、グローバル属性は AssemblyInfo.cs ファイルに配置されます。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-113">In C# projects, global attributes are put in the AssemblyInfo.cs file.</span></span>  
  
 <span data-ttu-id="f6aa7-114">アセンブリの属性は、アセンブリに関する情報を提供する値です。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-114">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="f6aa7-115">これらは次のカテゴリに分けられます。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-115">They fall into the following categories:</span></span>  
  
-   <span data-ttu-id="f6aa7-116">アセンブリ ID 属性</span><span class="sxs-lookup"><span data-stu-id="f6aa7-116">Assembly identity attributes</span></span>  
  
-   <span data-ttu-id="f6aa7-117">情報属性</span><span class="sxs-lookup"><span data-stu-id="f6aa7-117">Informational attributes</span></span>  
  
-   <span data-ttu-id="f6aa7-118">アセンブリ マニフェスト属性</span><span class="sxs-lookup"><span data-stu-id="f6aa7-118">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="f6aa7-119">アセンブリ ID 属性</span><span class="sxs-lookup"><span data-stu-id="f6aa7-119">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="f6aa7-120">アセンブリの ID は、名前、バージョン、カルチャの 3 つの属性によって識別されます (適用できる場合は厳密な名前も使用されます)。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-120">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="f6aa7-121">アセンブリの完全な名前を形成するこれらの属性は、コード内でアセンブリを参照するときに必要になります。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-121">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="f6aa7-122">アセンブリのバージョンとカルチャは、属性を使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-122">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="f6aa7-123">ただし名前の値は、コンパイラ、Visual Studio IDE の [[アセンブリ情報]](/visualstudio/ide/reference/assembly-information-dialog-box) ダイアログ ボックス、またはアセンブリ リンカー (AI.exe) によってアセンブリの作成時に設定されます。このとき、設定はアセンブリ マニフェストが含まれたファイルに基づきます。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-123">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="f6aa7-124"><xref:System.Reflection.AssemblyFlagsAttribute> 属性は、アセンブリの複数のコピーが共存できるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-124">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="f6aa7-125">次の表に ID 属性を示します。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-125">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="f6aa7-126">属性</span><span class="sxs-lookup"><span data-stu-id="f6aa7-126">Attribute</span></span>|<span data-ttu-id="f6aa7-127">目的</span><span class="sxs-lookup"><span data-stu-id="f6aa7-127">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="f6aa7-128">アセンブリの ID を完全に記述します。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-128">Fully describes the identity of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="f6aa7-129">アセンブリのバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-129">Specifies the version of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="f6aa7-130">アセンブリがサポートするカルチャを指定します。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-130">Specifies which culture the assembly supports.</span></span>|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="f6aa7-131">同じコンピューター、同じプロセス、または同じアプリケーション ドメインでの side-by-side 実行をアセンブリがサポートするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-131">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="f6aa7-132">情報属性</span><span class="sxs-lookup"><span data-stu-id="f6aa7-132">Informational Attributes</span></span>  
 <span data-ttu-id="f6aa7-133">情報属性は、追加の会社情報または製品情報をアセンブリに指定する場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-133">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="f6aa7-134">次の表は、<xref:System.Reflection?displayProperty=nameWithType> 名前空間で定義されている情報属性を示しています。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-134">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="f6aa7-135">属性</span><span class="sxs-lookup"><span data-stu-id="f6aa7-135">Attribute</span></span>|<span data-ttu-id="f6aa7-136">目的</span><span class="sxs-lookup"><span data-stu-id="f6aa7-136">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="f6aa7-137">アセンブリ マニフェストの製品名を指定するカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-137">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="f6aa7-138">アセンブリ マニフェストの商標を指定するカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-138">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="f6aa7-139">アセンブリ マニフェストの補足バージョンを指定するカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-139">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="f6aa7-140">アセンブリ マニフェストの会社名を指定するカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-140">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="f6aa7-141">アセンブリ マニフェストの著作権を指定するカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-141">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="f6aa7-142">Win32 ファイル バージョン リソースの特定のバージョン番号を使用するようコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-142">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="f6aa7-143">アセンブリが共通言語仕様 (CLS) に準拠しているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-143">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="f6aa7-144">アセンブリ マニフェスト属性</span><span class="sxs-lookup"><span data-stu-id="f6aa7-144">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="f6aa7-145">アセンブリ マニフェスト属性を使用すると、アセンブリ マニフェストの情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-145">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="f6aa7-146">ここには、タイトル、説明、既定の別名、構成が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-146">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="f6aa7-147">次の表は、<xref:System.Reflection?displayProperty=nameWithType> 名前空間で定義されているアセンブリ マニフェスト属性を示しています。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-147">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="f6aa7-148">属性</span><span class="sxs-lookup"><span data-stu-id="f6aa7-148">Attribute</span></span>|<span data-ttu-id="f6aa7-149">目的</span><span class="sxs-lookup"><span data-stu-id="f6aa7-149">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="f6aa7-150">アセンブリ マニフェストのアセンブリのタイトルを指定するカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-150">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="f6aa7-151">アセンブリ マニフェストのアセンブリの説明を指定するカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-151">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="f6aa7-152">アセンブリ マニフェストのアセンブリの構成 (製品版やデバッグなど) を指定するカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-152">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="f6aa7-153">アセンブリ マニフェストのわかりやすい既定の別名を定義します。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-153">Defines a friendly default alias for an assembly manifest</span></span>|  
  
##  <a name="Obsolete"></a> <span data-ttu-id="f6aa7-154">Obsolete 属性</span><span class="sxs-lookup"><span data-stu-id="f6aa7-154">Obsolete Attribute</span></span>  
 <span data-ttu-id="f6aa7-155">`Obsolete` 属性は、使用が推奨されなくなったプログラム エンティティをマークします。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-155">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="f6aa7-156">その後、非推奨の印が付いたエンティティが使用されるたびに、この属性の構成に従って警告かエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-156">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="f6aa7-157">例:</span><span class="sxs-lookup"><span data-stu-id="f6aa7-157">For example:</span></span>  
  
```csharp  
[System.Obsolete("use class B")]  
class A  
{  
    public void Method() { }  
}  
class B  
{  
    [System.Obsolete("use NewMethod", true)]  
    public void OldMethod() { }  
    public void NewMethod() { }  
}  
```  
  
 <span data-ttu-id="f6aa7-158">この例では、`Obsolete` 属性はクラス `A` とメソッド `B.OldMethod` に適用されています。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-158">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="f6aa7-159">`B.OldMethod` に適用された属性コンストラクターの 2 番目の引数が `true` に設定されているため、このメソッドではコンパイル エラーが発生します。一方、クラス `A` が使用されると、警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-159">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="f6aa7-160">しかし、`B.NewMethod` の呼び出しでは、警告もエラーも生成されません。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-160">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="f6aa7-161">最初の引数として属性コンストラクターに指定された文字列は、警告またはエラーの一部として表示されます。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-161">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="f6aa7-162">たとえば、前の定義でこれを使用すると、次のコードで 2 つの警告と 1 つのエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-162">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 <span data-ttu-id="f6aa7-163">クラス `A` の警告が 2 つ生成されます。1 つはクラス参照の宣言の警告で、もう 1 つはクラス コンストラクターの警告です。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-163">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="f6aa7-164">`Obsolete` 属性は引数なしで使用できますが、対象の項目が古い理由と代用する項目の説明を加えておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-164">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="f6aa7-165">`Obsolete` 属性は、1 回だけ使用できる属性であり、属性を使用できる任意のエンティティに適用できます。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-165">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="f6aa7-166">`Obsolete` は <xref:System.ObsoleteAttribute> の別名です。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-166">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
##  <a name="Conditional"></a> <span data-ttu-id="f6aa7-167">Conditional 属性</span><span class="sxs-lookup"><span data-stu-id="f6aa7-167">Conditional Attribute</span></span>  
 <span data-ttu-id="f6aa7-168">`Conditional` 属性を使用すると、プリプロセス識別子に依存したメソッドの実行を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-168">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="f6aa7-169">`Conditional` 属性は <xref:System.Diagnostics.ConditionalAttribute> の別名であり、メソッドまたは属性クラスに適用できます。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-169">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="f6aa7-170">この例では、`Conditional` は、プログラム固有の診断情報の表示を有効または無効にするメソッドに適用されています。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-170">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
```csharp  
#define TRACE_ON  
using System;  
using System.Diagnostics;  
  
public class Trace  
{  
    [Conditional("TRACE_ON")]  
    public static void Msg(string msg)  
    {  
        Console.WriteLine(msg);  
    }  
}  
  
public class ProgramClass  
{  
    static void Main()  
    {  
        Trace.Msg("Now in Main...");  
        Console.WriteLine("Done.");  
    }  
}  
```  
  
 <span data-ttu-id="f6aa7-171">`TRACE_ON` 識別子が定義されていない場合、トレース出力は表示されません。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-171">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="f6aa7-172">`Conditional` 属性は、(リリース ビルドではなく) デバッグ ビルドのトレース機能とログ機能を有効にするために、`DEBUG` 識別子と共によく使用されます。これは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-172">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 <span data-ttu-id="f6aa7-173">条件付きの印が付いたメソッドが呼び出されると、指定のプリプロセッサ シンボルの有無に従って、呼び出しの実行か省略が決定されます。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-173">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="f6aa7-174">シンボルが定義されている場合は呼び出しが実行され、定義されていない場合は省略されます。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-174">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="f6aa7-175">次のように、`#if…#endif` ブロック内でメソッドを囲むよりも `Conditional` を使用した方が、すっきりとして洗練されているうえ、エラーも少なくなります。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-175">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 <span data-ttu-id="f6aa7-176">条件付きメソッドは、クラスまたは構造体の宣言内のメソッドである必要があります。また、戻り値を持つことはできません。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-176">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="f6aa7-177">複数の識別子の使用</span><span class="sxs-lookup"><span data-stu-id="f6aa7-177">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="f6aa7-178">メソッドに複数の `Conditional` 属性が付いている場合、そのメソッドの呼び出しは、1 つ以上の条件付きシンボルが定義されているときに実行されます (つまり、シンボルは OR 演算子によって論理的にリンクされています)。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-178">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="f6aa7-179">この例では、`A` と `B` のどちらかがあると、メソッドの呼び出しが実行されます。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-179">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 <span data-ttu-id="f6aa7-180">AND 演算子で論理的にリンクされたシンボルの効果を実現するには、条件付きメソッドを連続して定義します。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-180">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="f6aa7-181">たとえば、次の 2 番目のメソッドは、`A` と `B` が両方定義されている場合にのみ実行されます。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-181">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
```csharp
[Conditional("A")]  
static void DoIfA()  
{  
    DoIfAandB();  
}  
  
[Conditional("B")]  
static void DoIfAandB()  
{  
    // Code to execute when both A and B are defined...  
}  
```  
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="f6aa7-182">属性クラスでの Conditional の使用</span><span class="sxs-lookup"><span data-stu-id="f6aa7-182">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="f6aa7-183">`Conditional` 属性は、属性クラスの定義にも適用できます。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-183">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="f6aa7-184">この例では、カスタム属性 `Documentation` は、DEBUG が定義されている場合にのみ、情報をメタデータに追加します。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-184">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
```csharp  
[Conditional("DEBUG")]  
public class Documentation : System.Attribute  
{  
    string text;  
  
    public Documentation(string text)  
    {  
        this.text = text;  
    }  
}  
  
class SampleClass  
{  
    // This attribute will only be included if DEBUG is defined.  
    [Documentation("This method displays an integer.")]  
    static void DoWork(int i)  
    {  
        System.Console.WriteLine(i.ToString());  
    }  
}  
```  
  
##  <a name="CallerInfo"></a> <span data-ttu-id="f6aa7-185">呼び出し元情報属性</span><span class="sxs-lookup"><span data-stu-id="f6aa7-185">Caller Info Attributes</span></span>  
 <span data-ttu-id="f6aa7-186">呼び出し元情報の属性を使用すると、メソッドへの呼び出し元に関する情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-186">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="f6aa7-187">ソース コードのファイル パス、ソース コードの行番号、呼び出し元のメンバー名を取得できます。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-187">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="f6aa7-188">メンバー呼び出し元情報を取得するには、省略可能なパラメーターに適用される属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-188">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="f6aa7-189">省略可能な各パラメーターでは既定値が指定されます。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-189">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="f6aa7-190">次の表は、<xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 名前空間で定義されている呼び出し元情報の属性の一覧です。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-190">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="f6aa7-191">属性</span><span class="sxs-lookup"><span data-stu-id="f6aa7-191">Attribute</span></span>|<span data-ttu-id="f6aa7-192">説明</span><span class="sxs-lookup"><span data-stu-id="f6aa7-192">Description</span></span>|<span data-ttu-id="f6aa7-193">型</span><span class="sxs-lookup"><span data-stu-id="f6aa7-193">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="f6aa7-194">呼び出し元を含むソース ファイルのフル パスです。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-194">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="f6aa7-195">これはコンパイル時のパスです。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-195">This is the path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="f6aa7-196">メソッドの呼び出し元であるソース ファイルの行番号。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-196">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="f6aa7-197">呼び出し元のメソッド名またはプロパティ名。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-197">Method name or property name of the caller.</span></span> <span data-ttu-id="f6aa7-198">詳細については、「[呼び出し元情報 (C#)](../../../../csharp/programming-guide/concepts/caller-information.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-198">For more information, see [Caller Information (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="f6aa7-199">呼び出し元情報属性の詳細については、「[呼び出し元情報 (C#)](../../../../csharp/programming-guide/concepts/caller-information.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6aa7-199">For more information about the Caller Info attributes, see [Caller Information (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6aa7-200">関連項目</span><span class="sxs-lookup"><span data-stu-id="f6aa7-200">See Also</span></span>  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [<span data-ttu-id="f6aa7-201">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="f6aa7-201">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f6aa7-202">属性</span><span class="sxs-lookup"><span data-stu-id="f6aa7-202">Attributes</span></span>](https://msdn.microsoft.com/library/5x6cd29c)  
 [<span data-ttu-id="f6aa7-203">リフレクション (C#)</span><span class="sxs-lookup"><span data-stu-id="f6aa7-203">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="f6aa7-204">リフレクションを使用した属性へのアクセス (C#)</span><span class="sxs-lookup"><span data-stu-id="f6aa7-204">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
