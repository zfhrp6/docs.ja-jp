---
title: -langversion (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: 523636663744acbbc85a08ebe3535f066e7dc160
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-langversion-c-compiler-options"></a><span data-ttu-id="1da6a-102">-langversion (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="1da6a-102">-langversion (C# Compiler Options)</span></span>
<span data-ttu-id="1da6a-103">コンパイラが、選択した C# 言語仕様に含まれている構文のみを受け入れるようにします。</span><span class="sxs-lookup"><span data-stu-id="1da6a-103">Causes the compiler to accept only syntax that is included in the chosen C# language specification.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1da6a-104">構文</span><span class="sxs-lookup"><span data-stu-id="1da6a-104">Syntax</span></span>  
  
```console  
-langversion:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="1da6a-105">引数</span><span class="sxs-lookup"><span data-stu-id="1da6a-105">Arguments</span></span>  
 `option`  
 <span data-ttu-id="1da6a-106">有効な値は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1da6a-106">The following values are valid:</span></span>  
  
|<span data-ttu-id="1da6a-107">オプション</span><span class="sxs-lookup"><span data-stu-id="1da6a-107">Option</span></span>|<span data-ttu-id="1da6a-108">説明</span><span class="sxs-lookup"><span data-stu-id="1da6a-108">Meaning</span></span>|  
|------------|-------------|  
|<span data-ttu-id="1da6a-109">default</span><span class="sxs-lookup"><span data-stu-id="1da6a-109">default</span></span>|<span data-ttu-id="1da6a-110">コンパイラは、最新のメジャー バージョンからサポートできるすべての有効な言語構文を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="1da6a-110">The compiler accepts all valid language syntax from the latest major version that it can support.</span></span> <span data-ttu-id="1da6a-111"><sup id="TDefault">[Default](#FDefault)</sup></span><span class="sxs-lookup"><span data-stu-id="1da6a-111"><sup id="TDefault">[Default](#FDefault)</sup></span></span>| 
|<span data-ttu-id="1da6a-112">ISO-1</span><span class="sxs-lookup"><span data-stu-id="1da6a-112">ISO-1</span></span>|<span data-ttu-id="1da6a-113">コンパイラは、ISO/IEC 23270:2003 C# (1.0/1.1) に含まれている構文のみを受け入れます<sup id="TISO1">[ISO1](#FISO1)</sup></span><span class="sxs-lookup"><span data-stu-id="1da6a-113">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.1) <sup id="TISO1">[ISO1](#FISO1)</sup></span></span>|  
|<span data-ttu-id="1da6a-114">ISO-2</span><span class="sxs-lookup"><span data-stu-id="1da6a-114">ISO-2</span></span>|<span data-ttu-id="1da6a-115">コンパイラは、ISO/IEC 23270:2006 C# (2.0) に含まれている構文のみを受け入れます<sup id="TISO2">[ISO2](#FISO2)</sup></span><span class="sxs-lookup"><span data-stu-id="1da6a-115">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0) <sup id="TISO2">[ISO2](#FISO2)</sup></span></span>|
|<span data-ttu-id="1da6a-116">3</span><span class="sxs-lookup"><span data-stu-id="1da6a-116">3</span></span>|<span data-ttu-id="1da6a-117">コンパイラは、C# 3.0 以下に含まれている構文のみを受け入れます<sup id="TCS3">[CS3](#FCS3)</sup></span><span class="sxs-lookup"><span data-stu-id="1da6a-117">The compiler accepts only syntax that is included in C# 3.0 or lower <sup id="TCS3">[CS3](#FCS3)</sup></span></span>|
|<span data-ttu-id="1da6a-118">4</span><span class="sxs-lookup"><span data-stu-id="1da6a-118">4</span></span>|<span data-ttu-id="1da6a-119">コンパイラは、C# 4.0 以下に含まれている構文のみを受け入れます<sup id="TCS4">[CS4](#FCS4)</sup></span><span class="sxs-lookup"><span data-stu-id="1da6a-119">The compiler accepts only syntax that is included in C# 4.0 or lower <sup id="TCS4">[CS4](#FCS4)</sup></span></span>|
|<span data-ttu-id="1da6a-120">5</span><span class="sxs-lookup"><span data-stu-id="1da6a-120">5</span></span>|<span data-ttu-id="1da6a-121">コンパイラは、C# 5.0 以下に含まれている構文のみを受け入れます<sup id="TCS5">[CS5](#FCS5)</sup></span><span class="sxs-lookup"><span data-stu-id="1da6a-121">The compiler accepts only syntax that is included in C# 5.0 or lower <sup id="TCS5">[CS5](#FCS5)</sup></span></span>|
|<span data-ttu-id="1da6a-122">6</span><span class="sxs-lookup"><span data-stu-id="1da6a-122">6</span></span>|<span data-ttu-id="1da6a-123">コンパイラは、C# 6.0 以下に含まれている構文のみを受け入れます<sup id="TCS6">[CS6](#FCS6)</sup></span><span class="sxs-lookup"><span data-stu-id="1da6a-123">The compiler accepts only syntax that is included in C# 6.0 or lower <sup id="TCS6">[CS6](#FCS6)</sup></span></span>|
|<span data-ttu-id="1da6a-124">7</span><span class="sxs-lookup"><span data-stu-id="1da6a-124">7</span></span>|<span data-ttu-id="1da6a-125">コンパイラは、C# 7.0 以下に含まれている構文のみを受け入れます<sup id="TCS7">[CS7](#FCS7)</sup></span><span class="sxs-lookup"><span data-stu-id="1da6a-125">The compiler accepts only syntax that is included in C# 7.0 or lower <sup id="TCS7">[CS7](#FCS7)</sup></span></span>|
|<span data-ttu-id="1da6a-126">latest</span><span class="sxs-lookup"><span data-stu-id="1da6a-126">latest</span></span>|<span data-ttu-id="1da6a-127">コンパイラは、サポートできるすべての有効な言語の構文を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="1da6a-127">The compiler accepts all valid language syntax that it can support.</span></span> <span data-ttu-id="1da6a-128"><sup id="TLatest">[Latest](#FLatest)</sup></span><span class="sxs-lookup"><span data-stu-id="1da6a-128"><sup id="TLatest">[Latest](#FLatest)</sup></span></span>|
<!--- Uncomment and move these above
|latest| once they're officially released
|7.1|The compiler accepts only syntax that is included in C# 7.1 or lower <sup id="TCS71">[CS71](#FCS71)</sup>|
|7.2|The compiler accepts only syntax that is included in C# 7.2 or lower <sup id="TCS71">[CS72](#FCS72)</sup>|
|8|The compiler accepts only syntax that is included in C# 8 or lower <sup id="TCS71">[CS8](#FCS8)</sup>|
-->

  
## <a name="remarks"></a><span data-ttu-id="1da6a-129">コメント</span><span class="sxs-lookup"><span data-stu-id="1da6a-129">Remarks</span></span>  
 <span data-ttu-id="1da6a-130">C# アプリケーションで参照されるメタデータは、**-langversion** コンパイラ オプションの対象になりません。</span><span class="sxs-lookup"><span data-stu-id="1da6a-130">Metadata referenced by your C# application is not subject to **-langversion** compiler option.</span></span>  
  
 <span data-ttu-id="1da6a-131">C# コンパイラのバージョンごとに言語仕様の拡張機能が含まれているため、**-langversion** は、コンパイラの以前のバージョンと同じ機能を提供しません。</span><span class="sxs-lookup"><span data-stu-id="1da6a-131">Because each version of the C# compiler contains extensions to the language specification, **-langversion** does not give you the equivalent functionality of an earlier version of the compiler.</span></span>  
 
 <span data-ttu-id="1da6a-132">さらに、C# バージョンの更新は、一般的に主要な .Net Framework のリリースと一致しますが、新しい構文および機能は必ずしも特定のフレームワーク バージョンに関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="1da6a-132">Additionally, while C# version updates generally coincide with major .Net Framework releases, the new syntax and features are not necessarily tied to that specific framework version.</span></span> <span data-ttu-id="1da6a-133">新機能では、C# リビジョンと共にリリースされる新しいコンパイラの更新プログラムを確実に必要としますが、各特定機能には、独自の最小の .Net API または共通言語ランタイムの要件があり、この要件によって、NuGet パッケージやその他のライブラリを含めることで下位レベルのフレームワークで実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1da6a-133">While the new features will definitely require a new compiler update that is also released alongside the C# revision, each specific feature has its own minimum .Net API or common language runtime requirements that may allow it to run on downlevel frameworks by including NuGet packages or other libraries.</span></span>
  
 <span data-ttu-id="1da6a-134">使用する **-langversion** の設定に関係なく、現在のバージョンの共通言語ランタイムを使用して .exe や .dll を作成します。</span><span class="sxs-lookup"><span data-stu-id="1da6a-134">Regardless of which **-langversion** setting you use, you will use the current version of the common language runtime to create your .exe or .dll.</span></span> <span data-ttu-id="1da6a-135">1 つの例外は、**-langversion:ISO-1** の下で機能する、フレンド アセンブリと [-moduleassemblyname (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) です。</span><span class="sxs-lookup"><span data-stu-id="1da6a-135">One exception is friend assemblies and [-moduleassemblyname (C# Compiler Option)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), which work under **-langversion:ISO-1**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="1da6a-136">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="1da6a-136">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="1da6a-137">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="1da6a-137">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="1da6a-138">**[ビルド]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1da6a-138">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="1da6a-139">**[詳細設定]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1da6a-139">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="1da6a-140">**言語バージョン**プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="1da6a-140">Modify the **Language Version** property.</span></span>  
  
 <span data-ttu-id="1da6a-141">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1da6a-141">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span></span>  
    
## <a name="see-also"></a><span data-ttu-id="1da6a-142">参照</span><span class="sxs-lookup"><span data-stu-id="1da6a-142">See Also</span></span>  
 [<span data-ttu-id="1da6a-143">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="1da6a-143">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="1da6a-144">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="1da6a-144">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 
### <a name="c-language-specification"></a><span data-ttu-id="1da6a-145">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="1da6a-145">C# Language Specification</span></span>
 <span data-ttu-id="1da6a-146">[C# 言語仕様リファレンス](../../../csharp/language-reference/language-specification/index.md): .NET Foundation</span><span class="sxs-lookup"><span data-stu-id="1da6a-146">[C# Language Specification Reference](../../../csharp/language-reference/language-specification/index.md) : .NET Foundation</span></span>  
 <span data-ttu-id="1da6a-147">C# 1.0/1.1 [ISO/IEC 23270:2003](https://www.iso.org/standard/36768.html) 情報技術 -- C# 言語仕様: ISO カタログ</span><span class="sxs-lookup"><span data-stu-id="1da6a-147">C# 1.0/1.1 [ISO/IEC 23270:2003](https://www.iso.org/standard/36768.html) Information technology -- C# Language Specification : ISO Catalogue</span></span>  
 <span data-ttu-id="1da6a-148">C# 2.0 [ISO/IEC 23270:2006](https://www.iso.org/standard/42926.html) 情報技術 -- C# 言語仕様: ISO カタログ</span><span class="sxs-lookup"><span data-stu-id="1da6a-148">C# 2.0 [ISO/IEC 23270:2006](https://www.iso.org/standard/42926.html) Information technology -- C# Language Specification : ISO Catalogue</span></span>  
 <span data-ttu-id="1da6a-149">C# 2.0 [c042926_ISO_IEC_23270_2006(E).zip](http://standards.iso.org/ittf/PubliclyAvailableStandards/c042926_ISO_IEC_23270_2006(E).zip) ISO/IEC 23270:2006 (PDF 形式) : 自由に利用可能な標準 ISO</span><span class="sxs-lookup"><span data-stu-id="1da6a-149">C# 2.0 [c042926_ISO_IEC_23270_2006(E).zip](http://standards.iso.org/ittf/PubliclyAvailableStandards/c042926_ISO_IEC_23270_2006(E).zip) ISO/IEC 23270:2006 in PDF format : ISO Freely Available Standards</span></span>  
 <span data-ttu-id="1da6a-150">C# 3.0 [CSharp Language Specification.doc](http://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc) C# 言語仕様バージョン 3.0 : Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="1da6a-150">C# 3.0 [CSharp Language Specification.doc](http://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc) C# Language Specification Version 3.0 : Microsoft Corporation</span></span>  
 <span data-ttu-id="1da6a-151">C# 4.0 [Ecma-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-334.pdf) Standard ECMA-334 4th Edition</span><span class="sxs-lookup"><span data-stu-id="1da6a-151">C# 4.0 [Ecma-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-334.pdf) Standard ECMA-334 4th Edition</span></span>    
 <span data-ttu-id="1da6a-152">C# 5.0 [CSharp Language Specification.docx](https://www.microsoft.com/download/details.aspx?id=7029) C# 言語仕様バージョン 5.0 : Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="1da6a-152">C# 5.0 [CSharp Language Specification.docx](https://www.microsoft.com/download/details.aspx?id=7029) C# Language Specification Version 5.0 : Microsoft Corporation</span></span>  
 <span data-ttu-id="1da6a-153">C# 6.0 [README.md](https://github.com/dotnet/csharplang/blob/master/spec/README.md) C# 言語仕様バージョン 6 - 非公式ドラフト: .NET Foundation</span><span class="sxs-lookup"><span data-stu-id="1da6a-153">C# 6.0 [README.md](https://github.com/dotnet/csharplang/blob/master/spec/README.md) C# Language Specification Version 6 - Unofficial Draft : .NET Foundation</span></span>  
 <span data-ttu-id="1da6a-154">C# 7.0 (現在使用できません)</span><span class="sxs-lookup"><span data-stu-id="1da6a-154">C# 7.0 (not currently available)</span></span>  

<!--- Uncomment and add to the above when they become officially released
 C# 7.1 (spec is not yet finished)  
 C# 7.2 (spec is not yet finished)  
 C# 8.0 (spec is not yet finished)  
-->

### <a name="minimum-compiler-version-needed-to-support-all-language-features"></a><span data-ttu-id="1da6a-155">すべての言語機能をサポートするために必要な最小コンパイラ バージョン</span><span class="sxs-lookup"><span data-stu-id="1da6a-155">Minimum compiler version needed to support all language features</span></span>   
<span data-ttu-id="1da6a-156">[↩](#TDefault)<a name="FDefault">既定</a>、<a name="FISO1">ISO1</a>: Microsoft Visual Studio/Build Tools .Net 2002 またはバンドルされている .Net Framework 1.0 コンパイラ</span><span class="sxs-lookup"><span data-stu-id="1da6a-156">[↩](#TDefault)<a name="FDefault">Default</a>, <a name="FISO1">ISO1</a>: Microsoft Visual Studio/Build Tools .Net 2002 or bundled .Net Framework 1.0 compiler</span></span>     
<span data-ttu-id="1da6a-157">[↩](#TISO2)<a name="FISO2">ISO2</a>: Microsoft Visual Studio/Build Tools 2005 またはバンドルされている .Net Framework 2.0 コンパイラ</span><span class="sxs-lookup"><span data-stu-id="1da6a-157">[↩](#TISO2)<a name="FISO2">ISO2</a>: Microsoft Visual Studio/Build Tools 2005 or bundled .Net Framework 2.0 compiler</span></span>    
<span data-ttu-id="1da6a-158">[↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio/Build Tools 2008 またはバンドルされている .Net Framework 3.5 コンパイラ</span><span class="sxs-lookup"><span data-stu-id="1da6a-158">[↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio/Build Tools 2008 or bundled .Net Framework 3.5 compiler</span></span>    
<span data-ttu-id="1da6a-159">[↩](#TCS4)<a name="FCS4">CS4</a>: Microsoft Visual Studio/Build Tools 2010 またはバンドルされている .Net Framework 4.0 コンパイラ</span><span class="sxs-lookup"><span data-stu-id="1da6a-159">[↩](#TCS4)<a name="FCS4">CS4</a>: Microsoft Visual Studio/Build Tools 2010 or bundled .Net Framework 4.0 compiler</span></span>    
<span data-ttu-id="1da6a-160">[↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio/Build Tools 2012 またはバンドルされている .Net Framework 4.5 コンパイラ</span><span class="sxs-lookup"><span data-stu-id="1da6a-160">[↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio/Build Tools 2012 or bundled .Net Framework 4.5 compiler</span></span>    
<span data-ttu-id="1da6a-161">[↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio/Build Tools 2015</span><span class="sxs-lookup"><span data-stu-id="1da6a-161">[↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio/Build Tools 2015</span></span>    
<span data-ttu-id="1da6a-162">[↩](#TCS7)<a name="FCS7">CS7</a>, <a name="FLatest">Latest</a>: Microsoft Visual Studio/Build Tools 2017</span><span class="sxs-lookup"><span data-stu-id="1da6a-162">[↩](#TCS7)<a name="FCS7">CS7</a>, <a name="FLatest">Latest</a>: Microsoft Visual Studio/Build Tools 2017</span></span>   

<!--- Uncomment and add to the above when they become officially released
[↩](#TCS71)<a name="FCS71">CS71</a>: Microsoft Visual Studio/Build Tools 20??    
[↩](#TCS72)<a name="FCS72">CS72</a>: Microsoft Visual Studio/Build Tools 20??    
[↩](#TCS8)<a name="FCS71">CS8</a>: Microsoft Visual Studio/Build Tools 20??    
-->
