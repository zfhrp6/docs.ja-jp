---
title: -langversion (C# コンパイラ オプション)
ms.date: 05/14/2018
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: 299ff121bab87482b7cdcaebc8b43cb8a1b559ec
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
---
# <a name="-langversion-c-compiler-options"></a><span data-ttu-id="c19d8-102">-langversion (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="c19d8-102">-langversion (C# Compiler Options)</span></span>
<span data-ttu-id="c19d8-103">コンパイラが、選択した C# 言語仕様に含まれている構文のみを受け入れるようにします。</span><span class="sxs-lookup"><span data-stu-id="c19d8-103">Causes the compiler to accept only syntax that is included in the chosen C# language specification.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c19d8-104">構文</span><span class="sxs-lookup"><span data-stu-id="c19d8-104">Syntax</span></span>  
  
```console  
-langversion:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="c19d8-105">引数</span><span class="sxs-lookup"><span data-stu-id="c19d8-105">Arguments</span></span>  
 `option`  
 <span data-ttu-id="c19d8-106">有効な値は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c19d8-106">The following values are valid:</span></span>  
  
|<span data-ttu-id="c19d8-107">オプション</span><span class="sxs-lookup"><span data-stu-id="c19d8-107">Option</span></span>|<span data-ttu-id="c19d8-108">説明</span><span class="sxs-lookup"><span data-stu-id="c19d8-108">Meaning</span></span>|  
|------------|-------------|  
|<span data-ttu-id="c19d8-109">default</span><span class="sxs-lookup"><span data-stu-id="c19d8-109">default</span></span>|<span data-ttu-id="c19d8-110">コンパイラは、最新のメジャー バージョンからサポートできるすべての有効な言語構文を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="c19d8-110">The compiler accepts all valid language syntax from the latest major version that it can support.</span></span>|
|<span data-ttu-id="c19d8-111">ISO-1</span><span class="sxs-lookup"><span data-stu-id="c19d8-111">ISO-1</span></span>|<span data-ttu-id="c19d8-112">コンパイラは、ISO/IEC 23270:2003 C# (1.0/1.2) に含まれている構文のみを受け入れます<sup id="TISO1">[ISO1](#FISO1)</sup></span><span class="sxs-lookup"><span data-stu-id="c19d8-112">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2) <sup id="TISO1">[ISO1](#FISO1)</sup></span></span>|  
|<span data-ttu-id="c19d8-113">ISO-2</span><span class="sxs-lookup"><span data-stu-id="c19d8-113">ISO-2</span></span>|<span data-ttu-id="c19d8-114">コンパイラは、ISO/IEC 23270:2006 C# (2.0) に含まれている構文のみを受け入れます<sup id="TISO2">[ISO2](#FISO2)</sup></span><span class="sxs-lookup"><span data-stu-id="c19d8-114">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0) <sup id="TISO2">[ISO2](#FISO2)</sup></span></span>|
|<span data-ttu-id="c19d8-115">3</span><span class="sxs-lookup"><span data-stu-id="c19d8-115">3</span></span>|<span data-ttu-id="c19d8-116">コンパイラは、C# 3.0 以下に含まれている構文のみを受け入れます<sup id="TCS3">[CS3](#FCS3)</sup></span><span class="sxs-lookup"><span data-stu-id="c19d8-116">The compiler accepts only syntax that is included in C# 3.0 or lower <sup id="TCS3">[CS3](#FCS3)</sup></span></span>|
|<span data-ttu-id="c19d8-117">4</span><span class="sxs-lookup"><span data-stu-id="c19d8-117">4</span></span>|<span data-ttu-id="c19d8-118">コンパイラは、C# 4.0 以下に含まれている構文のみを受け入れます<sup id="TCS4">[CS4](#FCS4)</sup></span><span class="sxs-lookup"><span data-stu-id="c19d8-118">The compiler accepts only syntax that is included in C# 4.0 or lower <sup id="TCS4">[CS4](#FCS4)</sup></span></span>|
|<span data-ttu-id="c19d8-119">5</span><span class="sxs-lookup"><span data-stu-id="c19d8-119">5</span></span>|<span data-ttu-id="c19d8-120">コンパイラは、C# 5.0 以下に含まれている構文のみを受け入れます<sup id="TCS5">[CS5](#FCS5)</sup></span><span class="sxs-lookup"><span data-stu-id="c19d8-120">The compiler accepts only syntax that is included in C# 5.0 or lower <sup id="TCS5">[CS5](#FCS5)</sup></span></span>|
|<span data-ttu-id="c19d8-121">6</span><span class="sxs-lookup"><span data-stu-id="c19d8-121">6</span></span>|<span data-ttu-id="c19d8-122">コンパイラは、C# 6.0 以下に含まれている構文のみを受け入れます<sup id="TCS6">[CS6](#FCS6)</sup></span><span class="sxs-lookup"><span data-stu-id="c19d8-122">The compiler accepts only syntax that is included in C# 6.0 or lower <sup id="TCS6">[CS6](#FCS6)</sup></span></span>|
|<span data-ttu-id="c19d8-123">7</span><span class="sxs-lookup"><span data-stu-id="c19d8-123">7</span></span>|<span data-ttu-id="c19d8-124">コンパイラは、C# 7.0 以下に含まれている構文のみを受け入れます<sup id="TCS7">[CS7](#FCS7)</sup></span><span class="sxs-lookup"><span data-stu-id="c19d8-124">The compiler accepts only syntax that is included in C# 7.0 or lower <sup id="TCS7">[CS7](#FCS7)</sup></span></span>|
|<span data-ttu-id="c19d8-125">7.1</span><span class="sxs-lookup"><span data-stu-id="c19d8-125">7.1</span></span>|<span data-ttu-id="c19d8-126">コンパイラは、C# 7.1 以下に含まれている構文のみを受け入れます<sup id="TCS71">[CS71](#FCS71)</sup></span><span class="sxs-lookup"><span data-stu-id="c19d8-126">The compiler accepts only syntax that is included in C# 7.1 or lower <sup id="TCS71">[CS71](#FCS71)</sup></span></span>|
|<span data-ttu-id="c19d8-127">7.2</span><span class="sxs-lookup"><span data-stu-id="c19d8-127">7.2</span></span>|<span data-ttu-id="c19d8-128">コンパイラは、C# 7.2 以下に含まれている構文のみを受け入れます<sup id="TCS72">[CS72](#FCS72)</sup></span><span class="sxs-lookup"><span data-stu-id="c19d8-128">The compiler accepts only syntax that is included in C# 7.2 or lower <sup id="TCS72">[CS72](#FCS72)</sup></span></span>|
|<span data-ttu-id="c19d8-129">7.3</span><span class="sxs-lookup"><span data-stu-id="c19d8-129">7.3</span></span>|<span data-ttu-id="c19d8-130">コンパイラは、C# 7.3 以下に含まれている構文のみを受け入れます<sup id="TCS73">[CS73](#FCS73)</sup></span><span class="sxs-lookup"><span data-stu-id="c19d8-130">The compiler accepts only syntax that is included in C# 7.3 or lower <sup id="TCS73">[CS73](#FCS73)</sup></span></span>|
|<span data-ttu-id="c19d8-131">latest</span><span class="sxs-lookup"><span data-stu-id="c19d8-131">latest</span></span>|<span data-ttu-id="c19d8-132">コンパイラは、サポートできるすべての有効な言語の構文を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="c19d8-132">The compiler accepts all valid language syntax that it can support.</span></span>|

<!--- Uncomment and move these above
|8|The compiler accepts only syntax that is included in C# 8 or lower <sup id="TCS8">[CS8](#FCS8)</sup>|
-->

  
## <a name="remarks"></a><span data-ttu-id="c19d8-133">コメント</span><span class="sxs-lookup"><span data-stu-id="c19d8-133">Remarks</span></span>  
 <span data-ttu-id="c19d8-134">C# アプリケーションで参照されるメタデータは、**-langversion** コンパイラ オプションの対象になりません。</span><span class="sxs-lookup"><span data-stu-id="c19d8-134">Metadata referenced by your C# application is not subject to **-langversion** compiler option.</span></span>  
  
 <span data-ttu-id="c19d8-135">C# コンパイラのバージョンごとに言語仕様の拡張機能が含まれているため、**-langversion** は、コンパイラの以前のバージョンと同じ機能を提供しません。</span><span class="sxs-lookup"><span data-stu-id="c19d8-135">Because each version of the C# compiler contains extensions to the language specification, **-langversion** does not give you the equivalent functionality of an earlier version of the compiler.</span></span>  
 
 <span data-ttu-id="c19d8-136">さらに、C# バージョンの更新は、一般的に主要な .Net Framework のリリースと一致しますが、新しい構文および機能は必ずしも特定のフレームワーク バージョンに関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="c19d8-136">Additionally, while C# version updates generally coincide with major .Net Framework releases, the new syntax and features are not necessarily tied to that specific framework version.</span></span> <span data-ttu-id="c19d8-137">新機能では、C# リビジョンと共にリリースされる新しいコンパイラの更新プログラムを確実に必要としますが、各特定機能には、独自の最小の .Net API または共通言語ランタイムの要件があり、この要件によって、NuGet パッケージやその他のライブラリを含めることで下位レベルのフレームワークで実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c19d8-137">While the new features will definitely require a new compiler update that is also released alongside the C# revision, each specific feature has its own minimum .Net API or common language runtime requirements that may allow it to run on downlevel frameworks by including NuGet packages or other libraries.</span></span>
  
 <span data-ttu-id="c19d8-138">使用する **-langversion** の設定に関係なく、現在のバージョンの共通言語ランタイムを使用して .exe や .dll を作成します。</span><span class="sxs-lookup"><span data-stu-id="c19d8-138">Regardless of which **-langversion** setting you use, you will use the current version of the common language runtime to create your .exe or .dll.</span></span> <span data-ttu-id="c19d8-139">1 つの例外は、**-langversion:ISO-1** の下で機能する、フレンド アセンブリと [-moduleassemblyname (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) です。</span><span class="sxs-lookup"><span data-stu-id="c19d8-139">One exception is friend assemblies and [-moduleassemblyname (C# Compiler Option)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), which work under **-langversion:ISO-1**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="c19d8-140">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="c19d8-140">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="c19d8-141">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="c19d8-141">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="c19d8-142">**[ビルド]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c19d8-142">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="c19d8-143">**[詳細設定]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c19d8-143">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="c19d8-144">**言語バージョン**プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="c19d8-144">Modify the **Language Version** property.</span></span>  
  
 <span data-ttu-id="c19d8-145">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c19d8-145">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span></span>  
    
## <a name="see-also"></a><span data-ttu-id="c19d8-146">参照</span><span class="sxs-lookup"><span data-stu-id="c19d8-146">See Also</span></span>  
 [<span data-ttu-id="c19d8-147">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="c19d8-147">C# Compiler Options</span></span>](index.md)  
 [<span data-ttu-id="c19d8-148">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="c19d8-148">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 
### <a name="c-language-specification"></a><span data-ttu-id="c19d8-149">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="c19d8-149">C# Language Specification</span></span>

|<span data-ttu-id="c19d8-150">Version</span><span class="sxs-lookup"><span data-stu-id="c19d8-150">Version</span></span>|<span data-ttu-id="c19d8-151">リンク</span><span class="sxs-lookup"><span data-stu-id="c19d8-151">Link</span></span>|<span data-ttu-id="c19d8-152">説明</span><span class="sxs-lookup"><span data-stu-id="c19d8-152">Description</span></span>|
|-------|----|-----------|
|<span data-ttu-id="c19d8-153">C# 1.0</span><span class="sxs-lookup"><span data-stu-id="c19d8-153">C# 1.0</span></span>|[<span data-ttu-id="c19d8-154">DOC のダウンロード</span><span class="sxs-lookup"><span data-stu-id="c19d8-154">Download DOC</span></span>](http://download.microsoft.com/download/a/9/e/a9e229b9-fee5-4c3e-8476-917dee385062/csharp%20language%20specification%20v1.0.doc)|<span data-ttu-id="c19d8-155">C# 言語仕様バージョン 1.0: Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="c19d8-155">C# Language Specification Version 1.0: Microsoft Corporation</span></span>|
|<span data-ttu-id="c19d8-156">C# 1.2</span><span class="sxs-lookup"><span data-stu-id="c19d8-156">C# 1.2</span></span>|[<span data-ttu-id="c19d8-157">DOC のダウンロード</span><span class="sxs-lookup"><span data-stu-id="c19d8-157">Download DOC</span></span>](http://download.microsoft.com/download/5/e/5/5e58be0a-b02b-41ac-a4a3-7a22286214ff/csharp%20language%20specification%20v1.2.doc)|<span data-ttu-id="c19d8-158">C# 言語仕様バージョン 1.2: Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="c19d8-158">C# Language Specification Version 1.2: Microsoft Corporation</span></span>|
|<span data-ttu-id="c19d8-159">C# 2.0</span><span class="sxs-lookup"><span data-stu-id="c19d8-159">C# 2.0</span></span>|[<span data-ttu-id="c19d8-160">PDF のダウンロード</span><span class="sxs-lookup"><span data-stu-id="c19d8-160">Download PDF</span></span>](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/Ecma-334%204th%20edition%20June%202006.pdf)|<span data-ttu-id="c19d8-161">Standard ECMA-334 4th Edition</span><span class="sxs-lookup"><span data-stu-id="c19d8-161">Standard ECMA-334 4th Edition</span></span>|
|<span data-ttu-id="c19d8-162">C# 3.0</span><span class="sxs-lookup"><span data-stu-id="c19d8-162">C# 3.0</span></span>|[<span data-ttu-id="c19d8-163">DOC のダウンロード</span><span class="sxs-lookup"><span data-stu-id="c19d8-163">Download DOC</span></span>](http://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc)|<span data-ttu-id="c19d8-164">C# 言語仕様バージョン 3.0: Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="c19d8-164">C# Language Specification Version 3.0: Microsoft Corporation</span></span>|
|<span data-ttu-id="c19d8-165">C# 5.0</span><span class="sxs-lookup"><span data-stu-id="c19d8-165">C# 5.0</span></span>|[<span data-ttu-id="c19d8-166">PDF のダウンロード</span><span class="sxs-lookup"><span data-stu-id="c19d8-166">Download PDF</span></span>](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-334.pdf)|<span data-ttu-id="c19d8-167">Standard ECMA-334 5th Edition</span><span class="sxs-lookup"><span data-stu-id="c19d8-167">Standard ECMA-334 5th Edition</span></span>|
|<span data-ttu-id="c19d8-168">C# 6.0</span><span class="sxs-lookup"><span data-stu-id="c19d8-168">C# 6.0</span></span>|[<span data-ttu-id="c19d8-169">リンク</span><span class="sxs-lookup"><span data-stu-id="c19d8-169">Link</span></span>](../language-specification/index.md)|<span data-ttu-id="c19d8-170">C# 言語仕様バージョン 6 - 非公式ドラフト: .NET Foundation</span><span class="sxs-lookup"><span data-stu-id="c19d8-170">C# Language Specification Version 6 - Unofficial Draft: .NET Foundation</span></span>|
|<span data-ttu-id="c19d8-171">C# 7.0 以降</span><span class="sxs-lookup"><span data-stu-id="c19d8-171">C# 7.0 and later</span></span>||<span data-ttu-id="c19d8-172">現在使用できません</span><span class="sxs-lookup"><span data-stu-id="c19d8-172">not currently available</span></span>|

### <a name="minimum-compiler-version-needed-to-support-all-language-features"></a><span data-ttu-id="c19d8-173">すべての言語機能をサポートするために必要な最小コンパイラ バージョン</span><span class="sxs-lookup"><span data-stu-id="c19d8-173">Minimum compiler version needed to support all language features</span></span>   
<span data-ttu-id="c19d8-174">[↩](#TISO1)<a name="FISO1">ISO1</a>: Microsoft Visual Studio/Build Tools .Net 2002 またはバンドルされている .Net Framework 1.0 コンパイラ</span><span class="sxs-lookup"><span data-stu-id="c19d8-174">[↩](#TISO1)<a name="FISO1">ISO1</a>: Microsoft Visual Studio/Build Tools .Net 2002 or bundled .Net Framework 1.0 compiler</span></span>     
<span data-ttu-id="c19d8-175">[↩](#TISO2)<a name="FISO2">ISO2</a>: Microsoft Visual Studio/Build Tools 2005 またはバンドルされている .Net Framework 2.0 コンパイラ</span><span class="sxs-lookup"><span data-stu-id="c19d8-175">[↩](#TISO2)<a name="FISO2">ISO2</a>: Microsoft Visual Studio/Build Tools 2005 or bundled .Net Framework 2.0 compiler</span></span>    
<span data-ttu-id="c19d8-176">[↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio/Build Tools 2008 またはバンドルされている .Net Framework 3.5 コンパイラ</span><span class="sxs-lookup"><span data-stu-id="c19d8-176">[↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio/Build Tools 2008 or bundled .Net Framework 3.5 compiler</span></span>    
<span data-ttu-id="c19d8-177">[↩](#TCS4)<a name="FCS4">CS4</a>: Microsoft Visual Studio/Build Tools 2010 またはバンドルされている .Net Framework 4.0 コンパイラ</span><span class="sxs-lookup"><span data-stu-id="c19d8-177">[↩](#TCS4)<a name="FCS4">CS4</a>: Microsoft Visual Studio/Build Tools 2010 or bundled .Net Framework 4.0 compiler</span></span>    
<span data-ttu-id="c19d8-178">[↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio/Build Tools 2012 またはバンドルされている .Net Framework 4.5 コンパイラ</span><span class="sxs-lookup"><span data-stu-id="c19d8-178">[↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio/Build Tools 2012 or bundled .Net Framework 4.5 compiler</span></span>    
<span data-ttu-id="c19d8-179">[↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio/Build Tools 2015</span><span class="sxs-lookup"><span data-stu-id="c19d8-179">[↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio/Build Tools 2015</span></span>    
<span data-ttu-id="c19d8-180">[↩](#TCS7)<a name="FCS7">CS7</a>: Microsoft Visual Studio/Build Tools 2017</span><span class="sxs-lookup"><span data-stu-id="c19d8-180">[↩](#TCS7)<a name="FCS7">CS7</a>: Microsoft Visual Studio/Build Tools 2017</span></span>   
<span data-ttu-id="c19d8-181">[↩](#TCS71)<a name="FCS71">CS71</a>: Microsoft Visual Studio/Build Tools 2017、バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="c19d8-181">[↩](#TCS71)<a name="FCS71">CS71</a>: Microsoft Visual Studio/Build Tools 2017, version 15.3</span></span>    
<span data-ttu-id="c19d8-182">[↩](#TCS72)<a name="FCS72">CS72</a>: Microsoft Visual Studio/Build Tools 2017、バージョン 15.5</span><span class="sxs-lookup"><span data-stu-id="c19d8-182">[↩](#TCS72)<a name="FCS72">CS72</a>: Microsoft Visual Studio/Build Tools 2017, version 15.5</span></span>    
<span data-ttu-id="c19d8-183">[↩](#TCS73)<a name="FCS73">CS73</a>: Microsoft Visual Studio/Build Tools 2017、バージョン 15.7</span><span class="sxs-lookup"><span data-stu-id="c19d8-183">[↩](#TCS73)<a name="FCS73">CS73</a>: Microsoft Visual Studio/Build Tools 2017, version 15.7</span></span>    

<!--- Uncomment and add to the above when they become officially released
[↩](#TCS8)<a name="FCS8">CS8</a>: Microsoft Visual Studio/Build Tools 20??    
-->
