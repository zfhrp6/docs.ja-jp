---
title: "一般的な名前付け規則"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], conflicts
- type names, conflicts
- language-specific type names
- names [.NET Framework], about naming guidelines
- names [.NET Framework], abbreviations
- abbreviation naming guidelines
- acronym naming guidelines
- Hungarian notation
- names [.NET Framework], type names
- names [.NET Framework], acronyms
ms.assetid: d3a77ea1-75d2-4969-a8c3-3e1e3e1aaedc
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dde3adbb7640978829dea4b977ed14eec38a9077
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="general-naming-conventions"></a><span data-ttu-id="4bbaa-102">一般的な名前付け規則</span><span class="sxs-lookup"><span data-stu-id="4bbaa-102">General Naming Conventions</span></span>
<span data-ttu-id="4bbaa-103">このセクションでは、一般的な名前付け規則単語の選択に関連する言語固有の名前を使用しないようにする方法の省略形と頭字語、および推奨事項の使用に関するガイドラインについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-103">This section describes general naming conventions that relate to word choice, guidelines on using abbreviations and acronyms, and recommendations on how to avoid using language-specific names.</span></span>  
  
## <a name="word-choice"></a><span data-ttu-id="4bbaa-104">単語の選択</span><span class="sxs-lookup"><span data-stu-id="4bbaa-104">Word Choice</span></span>  
 <span data-ttu-id="4bbaa-105">**✓ しないで**読みやすい識別子の名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-105">**✓ DO** choose easily readable identifier names.</span></span>  
  
 <span data-ttu-id="4bbaa-106">という名前のプロパティなど、`HorizontalAlignment`は英語 - よりも読みやすく`AlignmentHorizontal`です。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-106">For example, a property named `HorizontalAlignment` is more English-readable than `AlignmentHorizontal`.</span></span>  
  
 <span data-ttu-id="4bbaa-107">**✓ しないで**簡潔さよりも読みやすさを優先します。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-107">**✓ DO** favor readability over brevity.</span></span>  
  
 <span data-ttu-id="4bbaa-108">プロパティ名`CanScrollHorizontally`がよりも良い`ScrollableX`(x 軸にあいまいな参照)。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-108">The property name `CanScrollHorizontally` is better than `ScrollableX` (an obscure reference to the X-axis).</span></span>  
  
 <span data-ttu-id="4bbaa-109">**X しないで**アンダー スコア、ハイフン、またはその他の英数字以外の文字を使用します。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-109">**X DO NOT** use underscores, hyphens, or any other nonalphanumeric characters.</span></span>  
  
 <span data-ttu-id="4bbaa-110">**X しないで**ハンガリアン記法を使用します。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-110">**X DO NOT** use Hungarian notation.</span></span>  
  
 <span data-ttu-id="4bbaa-111">**避け x**広くのキーワードと競合する識別子を使用してプログラミング言語を使用します。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-111">**X AVOID** using identifiers that conflict with keywords of widely used programming languages.</span></span>  
  
 <span data-ttu-id="4bbaa-112">ルール 4 の共通言語仕様 (CLS)、に従って準拠のすべての言語は、その言語のキーワードを識別子として使用する名前付きの項目にアクセスできるようにするメカニズムを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-112">According to Rule 4 of the Common Language Specification (CLS), all compliant languages must provide a mechanism that allows access to named items that use a keyword of that language as an identifier.</span></span> <span data-ttu-id="4bbaa-113">C# の場合、たとえば、使用して、@ ここではエスケープ メカニズムとしてマークします。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-113">C#, for example, uses the @ sign as an escape mechanism in this case.</span></span> <span data-ttu-id="4bbaa-114">ただし、勧めまだメソッドを使用して、エスケープ シーケンスが指定されていない場合よりも非常に困難になっているために、一般的なキーワードを回避することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-114">However, it is still a good idea to avoid common keywords because it is much more difficult to use a method with the escape sequence than one without it.</span></span>  
  
## <a name="using-abbreviations-and-acronyms"></a><span data-ttu-id="4bbaa-115">略称や頭字語を使用します。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-115">Using Abbreviations and Acronyms</span></span>  
 <span data-ttu-id="4bbaa-116">**X しないで**識別子名の一部としての省略形または短縮形を使用します。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-116">**X DO NOT** use abbreviations or contractions as part of identifier names.</span></span>  
  
 <span data-ttu-id="4bbaa-117">たとえば、使用して`GetWindow`なく`GetWin`です。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-117">For example, use `GetWindow` rather than `GetWin`.</span></span>  
  
 <span data-ttu-id="4bbaa-118">**X しないで**広く受け入れられていると偶数の場合は、必要な場合にのみではない任意の頭字語を使用します。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-118">**X DO NOT** use any acronyms that are not widely accepted, and even if they are, only when necessary.</span></span>  
  
## <a name="avoiding-language-specific-names"></a><span data-ttu-id="4bbaa-119">言語固有の名前の回避</span><span class="sxs-lookup"><span data-stu-id="4bbaa-119">Avoiding Language-Specific Names</span></span>  
 <span data-ttu-id="4bbaa-120">**✓ しないで**型名に言語固有のキーワードではなく、意味的にわかりやすい名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-120">**✓ DO** use semantically interesting names rather than language-specific keywords for type names.</span></span>  
  
 <span data-ttu-id="4bbaa-121">たとえば、`GetLength`よりも優れた名前は、`GetInt`です。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-121">For example, `GetLength` is a better name than `GetInt`.</span></span>  
  
 <span data-ttu-id="4bbaa-122">**✓ しないで**まれなケース識別子には、その型以外の意味があるない場合に言語固有の名前ではなく、汎用の CLR 型名を使用します。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-122">**✓ DO** use a generic CLR type name, rather than a language-specific name, in the rare cases when an identifier has no semantic meaning beyond its type.</span></span>  
  
 <span data-ttu-id="4bbaa-123">たとえば、メソッドへの変換<xref:System.Int64>という名前を付ける必要があります`ToInt64`ではなく、 `ToLong` (ため<xref:System.Int64>、c# の CLR 名です-特定のエイリアス`long`)。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-123">For example, a method converting to <xref:System.Int64> should be named `ToInt64`, not `ToLong` (because <xref:System.Int64> is a CLR name for the C#-specific alias `long`).</span></span> <span data-ttu-id="4bbaa-124">次の表は、CLR 型名 (だけでなく c#、Visual Basic、および C++ の対応する型名) を使用していくつかの基本データ型を示します。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-124">The following table presents several base data types using the CLR type names (as well as the corresponding type names for C#, Visual Basic, and C++).</span></span>  
  
|<span data-ttu-id="4bbaa-125">C#</span><span class="sxs-lookup"><span data-stu-id="4bbaa-125">C#</span></span>|<span data-ttu-id="4bbaa-126">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4bbaa-126">Visual Basic</span></span>|<span data-ttu-id="4bbaa-127">C++</span><span class="sxs-lookup"><span data-stu-id="4bbaa-127">C++</span></span>|<span data-ttu-id="4bbaa-128">CLR</span><span class="sxs-lookup"><span data-stu-id="4bbaa-128">CLR</span></span>|  
|---------|------------------|-----------|---------|  
|<span data-ttu-id="4bbaa-129">**sbyte**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-129">**sbyte**</span></span>|<span data-ttu-id="4bbaa-130">**SByte**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-130">**SByte**</span></span>|<span data-ttu-id="4bbaa-131">**char**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-131">**char**</span></span>|<span data-ttu-id="4bbaa-132">**SByte**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-132">**SByte**</span></span>|  
|<span data-ttu-id="4bbaa-133">**byte**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-133">**byte**</span></span>|<span data-ttu-id="4bbaa-134">**Byte**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-134">**Byte**</span></span>|<span data-ttu-id="4bbaa-135">**unsigned char**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-135">**unsigned char**</span></span>|<span data-ttu-id="4bbaa-136">**Byte**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-136">**Byte**</span></span>|  
|<span data-ttu-id="4bbaa-137">**short**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-137">**short**</span></span>|<span data-ttu-id="4bbaa-138">**Short**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-138">**Short**</span></span>|<span data-ttu-id="4bbaa-139">**short**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-139">**short**</span></span>|<span data-ttu-id="4bbaa-140">**Int16**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-140">**Int16**</span></span>|  
|<span data-ttu-id="4bbaa-141">**ushort**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-141">**ushort**</span></span>|<span data-ttu-id="4bbaa-142">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-142">**UInt16**</span></span>|<span data-ttu-id="4bbaa-143">**unsigned short**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-143">**unsigned short**</span></span>|<span data-ttu-id="4bbaa-144">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-144">**UInt16**</span></span>|  
|<span data-ttu-id="4bbaa-145">**int**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-145">**int**</span></span>|<span data-ttu-id="4bbaa-146">**Integer**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-146">**Integer**</span></span>|<span data-ttu-id="4bbaa-147">**int**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-147">**int**</span></span>|<span data-ttu-id="4bbaa-148">**Int32**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-148">**Int32**</span></span>|  
|<span data-ttu-id="4bbaa-149">**uint**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-149">**uint**</span></span>|<span data-ttu-id="4bbaa-150">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-150">**UInt32**</span></span>|<span data-ttu-id="4bbaa-151">**unsigned int**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-151">**unsigned int**</span></span>|<span data-ttu-id="4bbaa-152">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-152">**UInt32**</span></span>|  
|<span data-ttu-id="4bbaa-153">**long**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-153">**long**</span></span>|<span data-ttu-id="4bbaa-154">**Long**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-154">**Long**</span></span>|<span data-ttu-id="4bbaa-155">**__int64**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-155">**__int64**</span></span>|<span data-ttu-id="4bbaa-156">**Int64**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-156">**Int64**</span></span>|  
|<span data-ttu-id="4bbaa-157">**ulong**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-157">**ulong**</span></span>|<span data-ttu-id="4bbaa-158">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-158">**UInt64**</span></span>|<span data-ttu-id="4bbaa-159">**unsigned __int64**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-159">**unsigned __int64**</span></span>|<span data-ttu-id="4bbaa-160">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-160">**UInt64**</span></span>|  
|<span data-ttu-id="4bbaa-161">**float**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-161">**float**</span></span>|<span data-ttu-id="4bbaa-162">**Single**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-162">**Single**</span></span>|<span data-ttu-id="4bbaa-163">**float**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-163">**float**</span></span>|<span data-ttu-id="4bbaa-164">**Single**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-164">**Single**</span></span>|  
|<span data-ttu-id="4bbaa-165">**double**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-165">**double**</span></span>|<span data-ttu-id="4bbaa-166">**Double**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-166">**Double**</span></span>|<span data-ttu-id="4bbaa-167">**double**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-167">**double**</span></span>|<span data-ttu-id="4bbaa-168">**Double**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-168">**Double**</span></span>|  
|<span data-ttu-id="4bbaa-169">**bool**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-169">**bool**</span></span>|<span data-ttu-id="4bbaa-170">**Boolean**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-170">**Boolean**</span></span>|<span data-ttu-id="4bbaa-171">**bool**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-171">**bool**</span></span>|<span data-ttu-id="4bbaa-172">**Boolean**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-172">**Boolean**</span></span>|  
|<span data-ttu-id="4bbaa-173">**char**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-173">**char**</span></span>|<span data-ttu-id="4bbaa-174">**Char**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-174">**Char**</span></span>|<span data-ttu-id="4bbaa-175">**wchar_t**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-175">**wchar_t**</span></span>|<span data-ttu-id="4bbaa-176">**Char**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-176">**Char**</span></span>|  
|<span data-ttu-id="4bbaa-177">**string**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-177">**string**</span></span>|<span data-ttu-id="4bbaa-178">**String**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-178">**String**</span></span>|<span data-ttu-id="4bbaa-179">**String**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-179">**String**</span></span>|<span data-ttu-id="4bbaa-180">**String**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-180">**String**</span></span>|  
|<span data-ttu-id="4bbaa-181">**object**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-181">**object**</span></span>|<span data-ttu-id="4bbaa-182">**オブジェクト**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-182">**Object**</span></span>|<span data-ttu-id="4bbaa-183">**オブジェクト**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-183">**Object**</span></span>|<span data-ttu-id="4bbaa-184">**オブジェクト**</span><span class="sxs-lookup"><span data-stu-id="4bbaa-184">**Object**</span></span>|  
  
 <span data-ttu-id="4bbaa-185">**✓ しないで**など、共通名を使用して`value`または`item`、まれなケース識別子は特別な意味を持たないし、パラメーターの型が重要でないときに、型名を繰り返しではなくです。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-185">**✓ DO**  use a common name, such as `value` or `item`, rather than repeating the type name, in the rare cases when an identifier has no semantic meaning and the type of the parameter is not important.</span></span>  
  
## <a name="naming-new-versions-of-existing-apis"></a><span data-ttu-id="4bbaa-186">既存の Api の新しいバージョンの名前を付ける</span><span class="sxs-lookup"><span data-stu-id="4bbaa-186">Naming New Versions of Existing APIs</span></span>  
 <span data-ttu-id="4bbaa-187">**✓ しないで**既存の API の新しいバージョンを作成するときに、古い API への名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-187">**✓ DO** use a name similar to the old API when creating new versions of an existing API.</span></span>  
  
 <span data-ttu-id="4bbaa-188">これにより、Api の間のリレーションシップを強調表示します。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-188">This helps to highlight the relationship between the APIs.</span></span>  
  
 <span data-ttu-id="4bbaa-189">**✓ しないで**を既存の API の新しいバージョンを示すプレフィックスではなく、サフィックスを追加することを希望します。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-189">**✓ DO** prefer adding a suffix rather than a prefix to indicate a new version of an existing API.</span></span>  
  
 <span data-ttu-id="4bbaa-190">これは、役立ちます探索ドキュメントについてを参照するときに Intellisense を使用してまたはします。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-190">This will assist discovery when browsing documentation, or using Intellisense.</span></span> <span data-ttu-id="4bbaa-191">古いバージョンの API はほとんどのブラウザーおよび Intellisense は、アルファベット順に識別子を表示するため、新しい Api の近くに編成できます。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-191">The old version of the API will be organized close to the new APIs, because most browsers and Intellisense show identifiers in alphabetical order.</span></span>  
  
 <span data-ttu-id="4bbaa-192">**✓ を検討してください**サフィックスまたはプリフィックスを追加する代わりに、まったく新しいが意味のある識別子を使用します。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-192">**✓ CONSIDER** using a brand new, but meaningful identifier, instead of adding a suffix or a prefix.</span></span>  
  
 <span data-ttu-id="4bbaa-193">**✓ しないで**の数値のサフィックスを使用して、既存の API の新しいバージョンを指定する、API の既存の名前 (つまり、業界標準である) 場合は、意味のある唯一の名前は、どの意味を追加する場合は、サフィックス (または、名前を変更する) アプリの場合に特にropriate オプション。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-193">**✓ DO** use a numeric suffix to indicate a new version of an existing API, particularly if the existing name of the API is the only name that makes sense (i.e., if it is an industry standard) and if adding any meaningful suffix (or changing the name) is not an appropriate option.</span></span>  
  
 <span data-ttu-id="4bbaa-194">**X しないで**"Ex"(または類似した) を使用して、同じ API の以前のバージョンと区別する識別子のサフィックスです。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-194">**X DO NOT** use the "Ex" (or a similar) suffix for an identifier to distinguish it from an earlier version of the same API.</span></span>  
  
 <span data-ttu-id="4bbaa-195">**✓ しないで**32 ビット整数の代わりに 64 ビット整数 (長整数) で動作する Api のバージョンを導入するときに、「64」サフィックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-195">**✓ DO** use the "64" suffix when introducing versions of APIs that operate on a 64-bit integer (a long integer) instead of a 32-bit integer.</span></span> <span data-ttu-id="4bbaa-196">のみ、既存の 32 ビット API が存在する場合に、この方法を実行する必要があります。しないことを 64 ビット バージョンのみでの新しい api です。</span><span class="sxs-lookup"><span data-stu-id="4bbaa-196">You only need to take this approach when the existing 32-bit API exists; don’t do it for brand new APIs with only a 64-bit version.</span></span>  
  
 <span data-ttu-id="4bbaa-197">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="4bbaa-197">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="4bbaa-198">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="4bbaa-198">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bbaa-199">関連項目</span><span class="sxs-lookup"><span data-stu-id="4bbaa-199">See Also</span></span>  
 [<span data-ttu-id="4bbaa-200">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="4bbaa-200">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="4bbaa-201">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="4bbaa-201">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
