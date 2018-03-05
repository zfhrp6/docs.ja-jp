---
title: "正規表現での文字クラス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- character classes
- regular expressions, character classes
- characters, matching syntax
- .NET Framework regular expressions, character classes
ms.assetid: 0f8bffab-ee0d-4e0e-9a96-2b4a252bb7e4
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: dfcb0d0ace4bd42d89fe7b4c2dc04098858c2945
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="character-classes-in-regular-expressions"></a><span data-ttu-id="bdd25-102">正規表現での文字クラス</span><span class="sxs-lookup"><span data-stu-id="bdd25-102">Character Classes in Regular Expressions</span></span>
<a name="Top"></a> <span data-ttu-id="bdd25-103">文字クラスは、いずれかが入力文字列に含まれると一致と見なされる文字のセットを定義します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-103">A character class defines a set of characters, any one of which can occur in an input string for a match to succeed.</span></span> <span data-ttu-id="bdd25-104">.NET の正規表現言語では、次の文字クラスがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-104">The regular expression language in .NET supports the following character classes:</span></span>  
  
-   <span data-ttu-id="bdd25-105">文字グループの肯定。</span><span class="sxs-lookup"><span data-stu-id="bdd25-105">Positive character groups.</span></span> <span data-ttu-id="bdd25-106">入力文字列内の文字が指定した文字のセットのいずれかと一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdd25-106">A character in the input string must match one of a specified set of characters.</span></span> <span data-ttu-id="bdd25-107">詳細については、「[文字グループの肯定](#PositiveGroup)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-107">For more information, see [Positive Character Group](#PositiveGroup).</span></span>  
  
-   <span data-ttu-id="bdd25-108">文字グループの否定。</span><span class="sxs-lookup"><span data-stu-id="bdd25-108">Negative character groups.</span></span> <span data-ttu-id="bdd25-109">入力文字列内の文字が指定した文字のセットのいずれかと一致しない必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdd25-109">A character in the input string must not match one of a specified set of characters.</span></span> <span data-ttu-id="bdd25-110">詳細については、「[文字グループの否定](#NegativeGroup)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-110">For more information, see [Negative Character Group](#NegativeGroup).</span></span>  
  
-   <span data-ttu-id="bdd25-111">任意の文字。</span><span class="sxs-lookup"><span data-stu-id="bdd25-111">Any character.</span></span> <span data-ttu-id="bdd25-112">正規表現の `.` (ドットまたはピリオド) 文字は、`\n` を除く任意の文字と一致するワイルドカード文字です。</span><span class="sxs-lookup"><span data-stu-id="bdd25-112">The `.` (dot or period) character in a regular expression is a wildcard character that matches any character except `\n`.</span></span> <span data-ttu-id="bdd25-113">詳細については、「[任意の文字](#AnyCharacter)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-113">For more information, see [Any Character](#AnyCharacter).</span></span>  
  
-   <span data-ttu-id="bdd25-114">Unicode 一般カテゴリまたは名前付きブロック。</span><span class="sxs-lookup"><span data-stu-id="bdd25-114">A general Unicode category or named block.</span></span> <span data-ttu-id="bdd25-115">入力文字列内の文字が一致と見なされるには、その文字が特定の Unicode カテゴリのメンバーであるか、または Unicode 文字の連続した範囲内に含まれる必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdd25-115">A character in the input string must be a member of a particular Unicode category or must fall within a contiguous range of Unicode characters for a match to succeed.</span></span> <span data-ttu-id="bdd25-116">詳細については、「[Unicode カテゴリまたは Unicode ブロック](#CategoryOrBlock)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-116">For more information, see [Unicode Category or Unicode Block](#CategoryOrBlock).</span></span>  
  
-   <span data-ttu-id="bdd25-117">Unicode 一般カテゴリまたは名前付きブロックの否定。</span><span class="sxs-lookup"><span data-stu-id="bdd25-117">A negative general Unicode category or named block.</span></span> <span data-ttu-id="bdd25-118">入力文字列内の文字が一致と見なされるには、その文字が特定の Unicode カテゴリのメンバーでないか、または Unicode 文字の連続した範囲内に含まれない必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdd25-118">A character in the input string must not be a member of a particular Unicode category or must not fall within a contiguous range of Unicode characters for a match to succeed.</span></span> <span data-ttu-id="bdd25-119">詳細については、「[Unicode カテゴリまたは Unicode ブロックの否定](#NegativeCategoryOrBlock)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-119">For more information, see [Negative Unicode Category or Unicode Block](#NegativeCategoryOrBlock).</span></span>  
  
-   <span data-ttu-id="bdd25-120">単語に使用される文字。</span><span class="sxs-lookup"><span data-stu-id="bdd25-120">A word character.</span></span> <span data-ttu-id="bdd25-121">入力文字列内の文字が、単語内の文字に適した Unicode カテゴリのいずれかに属することができます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-121">A character in the input string can belong to any of the Unicode categories that are appropriate for characters in words.</span></span> <span data-ttu-id="bdd25-122">詳細については、「[単語に使用される文字](#WordCharacter)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-122">For more information, see [Word Character](#WordCharacter).</span></span>  
  
-   <span data-ttu-id="bdd25-123">単語に使用されない文字。</span><span class="sxs-lookup"><span data-stu-id="bdd25-123">A non-word character.</span></span> <span data-ttu-id="bdd25-124">入力文字列内の文字が、単語に使用される文字ではない Unicode カテゴリのいずれかに属することができます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-124">A character in the input string can belong to any Unicode category that is not a word character.</span></span> <span data-ttu-id="bdd25-125">詳細については、「[単語に使用されない文字](#NonWordCharacter)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-125">For more information, see [Non-Word Character](#NonWordCharacter).</span></span>  
  
-   <span data-ttu-id="bdd25-126">空白文字。</span><span class="sxs-lookup"><span data-stu-id="bdd25-126">A white-space character.</span></span> <span data-ttu-id="bdd25-127">入力文字列内の文字が、Unicode 区切り記号および各種制御文字のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="bdd25-127">A character in the input string can be any Unicode separator character, as well as any one of a number of control characters.</span></span> <span data-ttu-id="bdd25-128">詳細については、「[空白文字](#WhitespaceCharacter)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-128">For more information, see [White-Space Character](#WhitespaceCharacter).</span></span>  
  
-   <span data-ttu-id="bdd25-129">空白以外の文字。</span><span class="sxs-lookup"><span data-stu-id="bdd25-129">A non-white-space character.</span></span> <span data-ttu-id="bdd25-130">入力文字列内の文字が、空白文字以外の文字のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="bdd25-130">A character in the input string can be any character that is not a white-space character.</span></span> <span data-ttu-id="bdd25-131">詳細については、「[空白以外の文字](#NonWhitespaceCharacter)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-131">For more information, see [Non-White-Space Character](#NonWhitespaceCharacter).</span></span>  
  
-   <span data-ttu-id="bdd25-132">10 進数。</span><span class="sxs-lookup"><span data-stu-id="bdd25-132">A decimal digit.</span></span> <span data-ttu-id="bdd25-133">入力文字列内の文字が、Unicode 10 進数に分類される各種文字のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="bdd25-133">A character in the input string can be any of a number of characters classified as Unicode decimal digits.</span></span> <span data-ttu-id="bdd25-134">詳細については、「[10 進数字](#DigitCharacter)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-134">For more information, see [Decimal Digit Character](#DigitCharacter).</span></span>  
  
-   <span data-ttu-id="bdd25-135">10 進数字以外の文字。</span><span class="sxs-lookup"><span data-stu-id="bdd25-135">A non-decimal digit.</span></span> <span data-ttu-id="bdd25-136">入力文字列内の文字が、Unicode 10 進数以外の文字のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="bdd25-136">A character in the input string can be anything other than a Unicode decimal digit.</span></span> <span data-ttu-id="bdd25-137">詳細については、「[10 進数字](#NonDigitCharacter)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-137">For more information, see [Decimal Digit Character](#NonDigitCharacter).</span></span>  
  
 <span data-ttu-id="bdd25-138">.NET は、文字クラスの減算式をサポートしています。これにより、ある文字クラスから別の文字クラスを除外した結果を文字のセットとして定義できます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-138">.NET supports character class subtraction expressions, which enables you to define a set of characters as the result of excluding one character class from another character class.</span></span> <span data-ttu-id="bdd25-139">詳細については、「[文字クラス減算](#CharacterClassSubtraction)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-139">For more information, see [Character Class Subtraction](#CharacterClassSubtraction).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdd25-140">カテゴリ別の文字に一致する文字クラス (単語文字に一致する [\w](#WordCharacter)、Unicode カテゴリに一致する [\p{}](#CategoryOrBlock) など) は、<xref:System.Globalization.CharUnicodeInfo> クラスを使用して文字カテゴリに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-140">Character classes that match characters by category, such as [\w](#WordCharacter) to match word characters or [\p{}](#CategoryOrBlock) to match a Unicode category, rely on the <xref:System.Globalization.CharUnicodeInfo> class to provide information about character categories.</span></span>  <span data-ttu-id="bdd25-141">[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降の文字カテゴリは、[Unicode 標準バージョン 8.0.0](http://www.unicode.org/versions/Unicode8.0.0/) に基づいています。</span><span class="sxs-lookup"><span data-stu-id="bdd25-141">Starting with the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], character categories are based on [The Unicode Standard, Version 8.0.0](http://www.unicode.org/versions/Unicode8.0.0/).</span></span> <span data-ttu-id="bdd25-142">[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] から [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] の文字カテゴリは、[Unicode 標準バージョン 6.3.0](http://www.unicode.org/versions/Unicode6.3.0/) に基づいています。</span><span class="sxs-lookup"><span data-stu-id="bdd25-142">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] through the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], they are based on [The Unicode Standard, Version 6.3.0](http://www.unicode.org/versions/Unicode6.3.0/).</span></span>  
  
<a name="PositiveGroup"></a>   
## <a name="positive-character-group--"></a><span data-ttu-id="bdd25-143">文字グループの肯定: [ ]</span><span class="sxs-lookup"><span data-stu-id="bdd25-143">Positive Character Group: [ ]</span></span>  
 <span data-ttu-id="bdd25-144">文字グループの肯定では、いずれかが入力文字列に含まれると一致と見なされる文字の一覧を指定します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-144">A positive character group specifies a list of characters, any one of which may appear in an input string for a match to occur.</span></span> <span data-ttu-id="bdd25-145">この文字の一覧は、個別に指定されることも範囲として指定されることも、その両方であることもあります。</span><span class="sxs-lookup"><span data-stu-id="bdd25-145">This list of characters may be specified individually, as a range, or both.</span></span>  
  
 <span data-ttu-id="bdd25-146">個別の文字の一覧を指定する構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bdd25-146">The syntax for specifying a list of individual characters is as follows:</span></span>  
  
 <span data-ttu-id="bdd25-147">[*character_group*]</span><span class="sxs-lookup"><span data-stu-id="bdd25-147">[*character_group*]</span></span>  
  
 <span data-ttu-id="bdd25-148">ここで、*character_group* は、入力文字列に含まれるなら一致と見なされる個別の文字の一覧です。</span><span class="sxs-lookup"><span data-stu-id="bdd25-148">where *character_group* is a list of the individual characters that can appear in the input string for a match to succeed.</span></span> <span data-ttu-id="bdd25-149">*character_group* は、リテラル文字、[エスケープ文字](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md)、または文字クラスを 1 つ以上組み合わせて構成されます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-149">*character_group* can consist of any combination of one or more literal characters, [escape characters](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md), or character classes.</span></span>  
  
 <span data-ttu-id="bdd25-150">文字の範囲を指定する構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bdd25-150">The syntax for specifying a range of characters is as follows:</span></span>  
  
```  
[firstCharacter-lastCharacter]  
```  
  
 <span data-ttu-id="bdd25-151">ここで、*firstCharacter* は範囲の最初の文字で、*lastCharacter* は範囲の最後の文字です。</span><span class="sxs-lookup"><span data-stu-id="bdd25-151">where *firstCharacter* is the character that begins the range and *lastCharacter* is the character that ends the range.</span></span> <span data-ttu-id="bdd25-152">文字範囲は連続する一連の文字で、範囲の最初の文字、ハイフン (-)、および範囲の最後の文字を指定することで定義されます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-152">A character range is a contiguous series of characters defined by specifying the first character in the series, a hyphen (-), and then the last character in the series.</span></span> <span data-ttu-id="bdd25-153">2 つの文字の Unicode コード ポイントが隣接している場合、それらの文字は連続しています。</span><span class="sxs-lookup"><span data-stu-id="bdd25-153">Two characters are contiguous if they have adjacent Unicode code points.</span></span>  
  
 <span data-ttu-id="bdd25-154">文字クラスの肯定を含む一般的な正規表現パターンをいくつか次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-154">Some common regular expression patterns that contain positive character classes are listed in the following table.</span></span>  
  
|<span data-ttu-id="bdd25-155">パターン</span><span class="sxs-lookup"><span data-stu-id="bdd25-155">Pattern</span></span>|<span data-ttu-id="bdd25-156">説明</span><span class="sxs-lookup"><span data-stu-id="bdd25-156">Description</span></span>|  
|-------------|-----------------|  
|`[aeiou]`|<span data-ttu-id="bdd25-157">すべての母音と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-157">Match all vowels.</span></span>|  
|`[\p{P}\d]`|<span data-ttu-id="bdd25-158">すべての句読点および 10 進数字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-158">Match all punctuation and decimal digit characters.</span></span>|  
|`[\s\p{P}]`|<span data-ttu-id="bdd25-159">すべての空白および句読点と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-159">Match all white-space and punctuation.</span></span>|  
  
 <span data-ttu-id="bdd25-160">次の例では、"a" および "e" という文字を含む文字グループの肯定を定義し、入力文字列内で "grey" または "gray" という語の後に別の語が続くと一致と見なされるようにします。</span><span class="sxs-lookup"><span data-stu-id="bdd25-160">The following example defines a positive character group that contains the characters "a" and "e" so that the input string must contain the words "grey" or "gray" followed by another word for a match to occur.</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/positivecharclasses.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/positivecharclasses.vb#1)]  
  
 <span data-ttu-id="bdd25-161">正規表現パターン `gr[ae]y\s\S+?[\s|\p{P}]` は、次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-161">The regular expression `gr[ae]y\s\S+?[\s|\p{P}]` is defined as follows:</span></span>  
  
|<span data-ttu-id="bdd25-162">パターン</span><span class="sxs-lookup"><span data-stu-id="bdd25-162">Pattern</span></span>|<span data-ttu-id="bdd25-163">説明</span><span class="sxs-lookup"><span data-stu-id="bdd25-163">Description</span></span>|  
|-------------|-----------------|  
|`gr`|<span data-ttu-id="bdd25-164">リテラル文字 "gr" と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-164">Match the literal characters "gr".</span></span>|  
|`[ae]`|<span data-ttu-id="bdd25-165">"a" または "e" と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-165">Match either an "a" or an "e".</span></span>|  
|`y\s`|<span data-ttu-id="bdd25-166">リテラル文字 "y" の後に空白文字が続く語と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-166">Match the literal character "y" followed by a white-space character.</span></span>|  
|`\S+?`|<span data-ttu-id="bdd25-167">1 つ以上 (ただし、できるだけ少ない数) の空白以外の文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-167">Match one or more non-white-space characters, but as few as possible.</span></span>|  
|`[\s\p{P}]`|<span data-ttu-id="bdd25-168">空白文字または句読点と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-168">Match either a white-space character or a punctuation mark.</span></span>|  
  
 <span data-ttu-id="bdd25-169">次の例は、大文字で始まる語と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-169">The following example matches words that begin with any capital letter.</span></span> <span data-ttu-id="bdd25-170">部分式 `[A-Z]` を使用して、A から Z の範囲の大文字を表します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-170">It uses the subexpression `[A-Z]` to represent the range of capital letters from A to Z.</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/range.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/range.vb#3)]  
  
 <span data-ttu-id="bdd25-171">正規表現 `\b[A-Z]\w*\b` は、次の表に示すように定義されています。</span><span class="sxs-lookup"><span data-stu-id="bdd25-171">The regular expression `\b[A-Z]\w*\b` is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="bdd25-172">パターン</span><span class="sxs-lookup"><span data-stu-id="bdd25-172">Pattern</span></span>|<span data-ttu-id="bdd25-173">説明</span><span class="sxs-lookup"><span data-stu-id="bdd25-173">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="bdd25-174">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-174">Start at a word boundary.</span></span>|  
|`[A-Z]`|<span data-ttu-id="bdd25-175">A から Z の任意の大文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-175">Match any uppercase character from A to Z.</span></span>|  
|`\w*`|<span data-ttu-id="bdd25-176">0 個以上の単語に使用される文字に一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-176">Match zero or more word characters.</span></span>|  
|`\b`|<span data-ttu-id="bdd25-177">ワード境界に一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-177">Match a word boundary.</span></span>|  
  
 [<span data-ttu-id="bdd25-178">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="bdd25-178">Back to Top</span></span>](#Top)  
  
<a name="NegativeGroup"></a>   
## <a name="negative-character-group-"></a><span data-ttu-id="bdd25-179">文字グループの否定: [^]</span><span class="sxs-lookup"><span data-stu-id="bdd25-179">Negative Character Group: [^]</span></span>  
 <span data-ttu-id="bdd25-180">文字グループの否定では、入力文字列に含まれなければ一致と見なされる文字の一覧を指定します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-180">A negative character group specifies a list of characters that must not appear in an input string for a match to occur.</span></span> <span data-ttu-id="bdd25-181">この文字の一覧は、個別に指定されることも範囲として指定されることも、その両方であることもあります。</span><span class="sxs-lookup"><span data-stu-id="bdd25-181">The list of characters may be specified individually, as a range, or both.</span></span>  
  
 <span data-ttu-id="bdd25-182">個別の文字の一覧を指定する構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bdd25-182">The syntax for specifying a list of individual characters is as follows:</span></span>  
  
 <span data-ttu-id="bdd25-183">[*^character_group*]</span><span class="sxs-lookup"><span data-stu-id="bdd25-183">[*^character_group*]</span></span>  
  
 <span data-ttu-id="bdd25-184">ここで、*character_group* は、入力文字列に含まれない場合に一致と見なされる個別の文字の一覧です。</span><span class="sxs-lookup"><span data-stu-id="bdd25-184">where *character_group* is a list of the individual characters that cannot appear in the input string for a match to succeed.</span></span> <span data-ttu-id="bdd25-185">*character_group* は、リテラル文字、[エスケープ文字](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md)、または文字クラスを 1 つ以上組み合わせて構成されます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-185">*character_group* can consist of any combination of one or more literal characters, [escape characters](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md), or character classes.</span></span>  
  
 <span data-ttu-id="bdd25-186">文字の範囲を指定する構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bdd25-186">The syntax for specifying a range of characters is as follows:</span></span>  
  
 <span data-ttu-id="bdd25-187">[^*firstCharacter*-*lastCharacter*]</span><span class="sxs-lookup"><span data-stu-id="bdd25-187">[^*firstCharacter*-*lastCharacter*]</span></span>  
  
 <span data-ttu-id="bdd25-188">ここで、*firstCharacter* は範囲の最初の文字で、*lastCharacter* は範囲の最後の文字です。</span><span class="sxs-lookup"><span data-stu-id="bdd25-188">where *firstCharacter* is the character that begins the range, and *lastCharacter* is the character that ends the range.</span></span> <span data-ttu-id="bdd25-189">文字範囲は連続する一連の文字で、範囲の最初の文字、ハイフン (-)、および範囲の最後の文字を指定することで定義されます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-189">A character range is a contiguous series of characters defined by specifying the first character in the series, a hyphen (-), and then the last character in the series.</span></span> <span data-ttu-id="bdd25-190">2 つの文字の Unicode コード ポイントが隣接している場合、それらの文字は連続しています。</span><span class="sxs-lookup"><span data-stu-id="bdd25-190">Two characters are contiguous if they have adjacent Unicode code points.</span></span>  
  
 <span data-ttu-id="bdd25-191">複数の文字範囲を連結することもできます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-191">Two or more character ranges can be concatenated.</span></span> <span data-ttu-id="bdd25-192">たとえば、"0" ～ "9" の範囲の 10 進数、"a" ～ "f" の範囲の小文字、および "A" ～ "F" の範囲の大文字を指定するには、`[0-9a-fA-F]` を使用します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-192">For example, to specify the range of decimal digits from "0" through "9", the range of lowercase letters from "a" through "f", and the range of uppercase letters from "A" through "F", use `[0-9a-fA-F]`.</span></span>  
  
 <span data-ttu-id="bdd25-193">文字グループの否定における先頭のキャレット文字 (`^`) は、文字グループが文字グループの肯定ではなく文字グループの否定であることを示し、省略できません。</span><span class="sxs-lookup"><span data-stu-id="bdd25-193">The leading carat character (`^`) in a negative character group is mandatory and indicates the character group is a negative character group instead of a positive character group.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bdd25-194">大規模な正規表現パターンにおける文字グループの否定は、ゼロ幅アサーションではありません。</span><span class="sxs-lookup"><span data-stu-id="bdd25-194">A negative character group in a larger regular expression pattern is not a zero-width assertion.</span></span> <span data-ttu-id="bdd25-195">つまり、正規表現エンジンは、文字グループの否定を評価した後に、入力文字列内で 1 文字進みます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-195">That is, after evaluating the negative character group, the regular expression engine advances one character in the input string.</span></span>  
  
 <span data-ttu-id="bdd25-196">文字グループの否定を含む一般的な正規表現パターンをいくつか次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-196">Some common regular expression patterns that contain negative character groups are listed in the following table.</span></span>  
  
|<span data-ttu-id="bdd25-197">パターン</span><span class="sxs-lookup"><span data-stu-id="bdd25-197">Pattern</span></span>|<span data-ttu-id="bdd25-198">説明</span><span class="sxs-lookup"><span data-stu-id="bdd25-198">Description</span></span>|  
|-------------|-----------------|  
|`[^aeiou]`|<span data-ttu-id="bdd25-199">母音を除くすべての文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-199">Match all characters except vowels.</span></span>|  
|`[^\p{P}\d]`|<span data-ttu-id="bdd25-200">句読点および 10 進数字を除くすべての文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-200">Match all characters except punctuation and decimal digit characters.</span></span>|  
  
 <span data-ttu-id="bdd25-201">次の例は、"th" という文字で始まってその後に "o" が続かない語と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-201">The following example matches any word that begins with the characters "th" and is not followed by an "o".</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/negativecharclasses.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/negativecharclasses.vb#2)]  
  
 <span data-ttu-id="bdd25-202">正規表現 `\bth[^o]\w+\b` は、次の表に示すように定義されています。</span><span class="sxs-lookup"><span data-stu-id="bdd25-202">The regular expression `\bth[^o]\w+\b` is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="bdd25-203">パターン</span><span class="sxs-lookup"><span data-stu-id="bdd25-203">Pattern</span></span>|<span data-ttu-id="bdd25-204">説明</span><span class="sxs-lookup"><span data-stu-id="bdd25-204">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="bdd25-205">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-205">Start at a word boundary.</span></span>|  
|`th`|<span data-ttu-id="bdd25-206">リテラル文字 "th" と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-206">Match the literal characters "th".</span></span>|  
|`[^o]`|<span data-ttu-id="bdd25-207">"o" 以外の任意の文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-207">Match any character that is not an "o".</span></span>|  
|`\w+`|<span data-ttu-id="bdd25-208">1 つ以上の単語文字に一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-208">Match one or more word characters.</span></span>|  
|`\b`|<span data-ttu-id="bdd25-209">ワード境界で終了します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-209">End at a word boundary.</span></span>|  
  
 [<span data-ttu-id="bdd25-210">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="bdd25-210">Back to Top</span></span>](#Top)  
  
<a name="AnyCharacter"></a>   
## <a name="any-character-"></a><span data-ttu-id="bdd25-211">任意の文字: .</span><span class="sxs-lookup"><span data-stu-id="bdd25-211">Any Character: .</span></span>  
 <span data-ttu-id="bdd25-212">ピリオド文字 (.) は、`\n` (改行文字、\u000A) を除く任意の文字と一致しますが、次の 2 つの制限があります。</span><span class="sxs-lookup"><span data-stu-id="bdd25-212">The period character (.) matches any character except `\n` (the newline character, \u000A), with the following two qualifications:</span></span>  
  
-   <span data-ttu-id="bdd25-213">正規表現パターンが <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> オプションで修飾されている場合、または `.` 文字クラスを含むパターンの一部が `s` オプションで修飾されている場合は、`.` は任意の文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-213">If a regular expression pattern is modified by the <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> option, or if the portion of the pattern that contains the `.` character class is modified by the `s` option, `.` matches any character.</span></span> <span data-ttu-id="bdd25-214">詳細については、「[正規表現のオプション](../../../docs/standard/base-types/regular-expression-options.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-214">For more information, see [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
     <span data-ttu-id="bdd25-215">`.` 文字クラスの既定の動作と <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> オプションが指定されている場合の動作の違いの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-215">The following example illustrates the different behavior of the `.` character class by default and with the <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> option.</span></span> <span data-ttu-id="bdd25-216">正規表現 `^.+` は文字列の先頭から開始し、すべての文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-216">The regular expression `^.+` starts at the beginning of the string and matches every character.</span></span> <span data-ttu-id="bdd25-217">既定では、照合は 1 行目の末尾で終了します。正規表現パターンは復帰文字 `\r` (\u000D) と一致しますが、`\n` とは一致しません。</span><span class="sxs-lookup"><span data-stu-id="bdd25-217">By default, the match ends at the end of the first line; the regular expression pattern matches the carriage return character, `\r` or \u000D, but it does not match `\n`.</span></span> <span data-ttu-id="bdd25-218"><xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> オプションは入力文字列全体を単一行として解釈するので、`\n` を含む入力文字列内のすべての文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-218">Because the <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> option interprets the entire input string as a single line, it matches every character in the input string, including `\n`.</span></span>  
  
     [!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
     [!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]  
  
> [!NOTE]
>  <span data-ttu-id="bdd25-219">`.` 文字クラスは `\n` を除く任意の文字と一致するので、このクラスも `\r` (復帰文字、\u000D) と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-219">Because it matches any character except `\n`, the `.` character class also matches `\r` (the carriage return character, \u000D).</span></span>  
  
-   <span data-ttu-id="bdd25-220">文字グループの肯定または文字グループの否定に含まれているピリオドは、文字クラスではなくリテラルのピリオド文字として扱われます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-220">In a positive or negative character group, a period is treated as a literal period character, and not as a character class.</span></span> <span data-ttu-id="bdd25-221">詳細については、このトピックで前述した「[文字グループの肯定](#PositiveGroup)」および「[文字グループの否定](#NegativeGroup)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-221">For more information, see [Positive Character Group](#PositiveGroup) and [Negative Character Group](#NegativeGroup) earlier in this topic.</span></span> <span data-ttu-id="bdd25-222">ピリオド文字 (`.`) を文字クラスとしても文字グループの肯定のメンバーとしても含む正規表現を定義する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-222">The following example provides an illustration by defining a regular expression that includes the period character (`.`) both as a character class and as a member of a positive character group.</span></span> <span data-ttu-id="bdd25-223">正規表現 `\b.*[.?!;:](\s|\z)` はワード境界から開始し、ピリオドを含む 4 つの句読点のいずれかが検出されるまで任意の文字と一致し、空白文字または文字列の末尾と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-223">The regular expression `\b.*[.?!;:](\s|\z)` begins at a word boundary, matches any character until it encounters one of four punctuation marks, including a period, and then matches either a white-space character or the end of the string.</span></span>  
  
     [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any1.cs#4)]
     [!code-vb[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any1.vb#4)]  
  
> [!NOTE]
>  <span data-ttu-id="bdd25-224">`.` 言語要素は任意の文字と一致するので、正規表現パターンが任意の文字と複数回一致する場合に最短一致の量指定子と共によく使用されます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-224">Because it matches any character, the `.` language element is often used with a lazy quantifier if a regular expression pattern attempts to match any character multiple times.</span></span> <span data-ttu-id="bdd25-225">詳細については、「[量指定子](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-225">For more information, see [Quantifiers](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).</span></span>  
  
 [<span data-ttu-id="bdd25-226">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="bdd25-226">Back to Top</span></span>](#Top)  
  
<a name="CategoryOrBlock"></a>   
## <a name="unicode-category-or-unicode-block-p"></a><span data-ttu-id="bdd25-227">Unicode カテゴリまたは Unicode ブロック: \p{}</span><span class="sxs-lookup"><span data-stu-id="bdd25-227">Unicode Category or Unicode Block: \p{}</span></span>  
 <span data-ttu-id="bdd25-228">Unicode 規格では、各文字に一般カテゴリが割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="bdd25-228">The Unicode standard assigns each character a general category.</span></span> <span data-ttu-id="bdd25-229">たとえば、特定の文字は、英大文字 (`Lu` カテゴリで表されます)、10 進数 (`Nd` カテゴリ)、数学記号 (`Sm` カテゴリ)、または段落区切り記号 (`Zl` カテゴリ) に分類できます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-229">For example, a particular character can be an uppercase letter (represented by the `Lu` category), a decimal digit (the `Nd` category), a math symbol (the `Sm` category), or a paragraph separator (the `Zl` category).</span></span> <span data-ttu-id="bdd25-230">また、Unicode 規格の特定の文字セットは、特定の範囲またはブロックの連続したコード ポイントに対応します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-230">Specific character sets in the Unicode standard also occupy a specific range or block of consecutive code points.</span></span> <span data-ttu-id="bdd25-231">たとえば、基本的なラテン語文字セットは \u0000 ～ \u007F で、アラビア語文字セットは \u0600 ～ \u06FF です。</span><span class="sxs-lookup"><span data-stu-id="bdd25-231">For example, the basic Latin character set is found from \u0000 through \u007F, while the Arabic character set is found from \u0600 through \u06FF.</span></span>  
  
 <span data-ttu-id="bdd25-232">正規表現の構成要素</span><span class="sxs-lookup"><span data-stu-id="bdd25-232">The regular expression construct</span></span>  
  
 <span data-ttu-id="bdd25-233">`\p{` *name* `}`</span><span class="sxs-lookup"><span data-stu-id="bdd25-233">`\p{` *name* `}`</span></span>  
  
 <span data-ttu-id="bdd25-234">Unicode 一般カテゴリまたは名前付きブロックに属する任意の文字と一致します。ここで、*name* はカテゴリの省略形または名前付きブロックの名前です。</span><span class="sxs-lookup"><span data-stu-id="bdd25-234">matches any character that belongs to a Unicode general category or named block, where *name* is the category abbreviation or named block name.</span></span> <span data-ttu-id="bdd25-235">カテゴリの省略形の一覧については、このトピックで後述する「[サポートされている Unicode 一般カテゴリ](#SupportedUnicodeGeneralCategories)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-235">For a list of category abbreviations, see the [Supported Unicode General Categories](#SupportedUnicodeGeneralCategories) section later in this topic.</span></span> <span data-ttu-id="bdd25-236">名前付きブロックの一覧については、このトピックで後述する「[サポートされている名前付きブロック](#SupportedNamedBlocks)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-236">For a list of named blocks, see the [Supported Named Blocks](#SupportedNamedBlocks) section later in this topic.</span></span>  
  
 <span data-ttu-id="bdd25-237">`\p{`*name*`}` 構成要素を使用して Unicode 一般カテゴリ (この場合は `Pd` (Punctuation, Dash: 句読点、ダッシュ) カテゴリ) と名前付きブロック (`IsGreek` 名前付きブロックおよび `IsBasicLatin` 名前付きブロック) の両方を照合する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-237">The following example uses the `\p{`*name*`}` construct to match both a Unicode general category (in this case, the `Pd`, or Punctuation,Dash category) and a named block (the `IsGreek` and `IsBasicLatin` named blocks).</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/category1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/category1.vb#6)]  
  
 <span data-ttu-id="bdd25-238">正規表現 `\b(\p{IsGreek}+(\s)?)+\p{Pd}\s(\p{IsBasicLatin}+(\s)?)+` は、次の表に示すように定義されています。</span><span class="sxs-lookup"><span data-stu-id="bdd25-238">The regular expression `\b(\p{IsGreek}+(\s)?)+\p{Pd}\s(\p{IsBasicLatin}+(\s)?)+` is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="bdd25-239">パターン</span><span class="sxs-lookup"><span data-stu-id="bdd25-239">Pattern</span></span>|<span data-ttu-id="bdd25-240">説明</span><span class="sxs-lookup"><span data-stu-id="bdd25-240">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="bdd25-241">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-241">Start at a word boundary.</span></span>|  
|`\p{IsGreek}+`|<span data-ttu-id="bdd25-242">1 つ以上のギリシャ文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-242">Match one or more Greek characters.</span></span>|  
|`(\s)?`|<span data-ttu-id="bdd25-243">0 個または 1 個の空白文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-243">Match zero or one white-space character.</span></span>|  
|`(\p{IsGreek}+(\s)?)+`|<span data-ttu-id="bdd25-244">1 つ以上のギリシャ文字の後に 0 個または 1 個の空白文字が 1 回以上続くパターンに一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-244">Match the pattern of one or more Greek characters followed by zero or one white-space characters one or more times.</span></span>|  
|`\p{Pd}`|<span data-ttu-id="bdd25-245">Punctuation, Dash (句読点、ダッシュ) 文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-245">Match a Punctuation, Dash character.</span></span>|  
|`\s`|<span data-ttu-id="bdd25-246">空白文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-246">Match a white-space character.</span></span>|  
|`\p{IsBasicLatin}+`|<span data-ttu-id="bdd25-247">1 つ以上の基本的なラテン文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-247">Match one or more basic Latin characters.</span></span>|  
|`(\s)?`|<span data-ttu-id="bdd25-248">0 個または 1 個の空白文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-248">Match zero or one white-space character.</span></span>|  
|`(\p{IsBasicLatin}+(\s)?)+`|<span data-ttu-id="bdd25-249">1 つ以上の基本的なラテン文字の後に 0 個または 1 個の空白文字が 1 回以上続くパターンに一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-249">Match the pattern of one or more basic Latin characters followed by zero or one white-space characters one or more times.</span></span>|  
  
 [<span data-ttu-id="bdd25-250">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="bdd25-250">Back to Top</span></span>](#Top)  
  
<a name="NegativeCategoryOrBlock"></a>   
## <a name="negative-unicode-category-or-unicode-block-p"></a><span data-ttu-id="bdd25-251">Unicode カテゴリまたは Unicode ブロックの否定: \P{}</span><span class="sxs-lookup"><span data-stu-id="bdd25-251">Negative Unicode Category or Unicode Block: \P{}</span></span>  
 <span data-ttu-id="bdd25-252">Unicode 規格では、各文字に一般カテゴリが割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="bdd25-252">The Unicode standard assigns each character a general category.</span></span> <span data-ttu-id="bdd25-253">たとえば、特定の文字は、英大文字 (`Lu` カテゴリで表されます)、10 進数 (`Nd` カテゴリ)、数学記号 (`Sm` カテゴリ)、または段落区切り記号 (`Zl` カテゴリ) に分類できます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-253">For example, a particular character can be an uppercase letter (represented by the `Lu` category), a decimal digit (the `Nd` category), a math symbol (the `Sm` category), or a paragraph separator (the `Zl` category).</span></span> <span data-ttu-id="bdd25-254">また、Unicode 規格の特定の文字セットは、特定の範囲またはブロックの連続したコード ポイントに対応します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-254">Specific character sets in the Unicode standard also occupy a specific range or block of consecutive code points.</span></span> <span data-ttu-id="bdd25-255">たとえば、基本的なラテン語文字セットは \u0000 ～ \u007F で、アラビア語文字セットは \u0600 ～ \u06FF です。</span><span class="sxs-lookup"><span data-stu-id="bdd25-255">For example, the basic Latin character set is found from \u0000 through \u007F, while the Arabic character set is found from \u0600 through \u06FF.</span></span>  
  
 <span data-ttu-id="bdd25-256">正規表現の構成要素</span><span class="sxs-lookup"><span data-stu-id="bdd25-256">The regular expression construct</span></span>  
  
 <span data-ttu-id="bdd25-257">`\P{` *name* `}`</span><span class="sxs-lookup"><span data-stu-id="bdd25-257">`\P{` *name* `}`</span></span>  
  
 <span data-ttu-id="bdd25-258">Unicode 一般カテゴリにも名前付きブロックにも属さない任意の文字と一致します。ここで、*name* はカテゴリの省略形または名前付きブロックの名前です。</span><span class="sxs-lookup"><span data-stu-id="bdd25-258">matches any character that does not belong to a Unicode general category or named block, where *name* is the category abbreviation or named block name.</span></span> <span data-ttu-id="bdd25-259">カテゴリの省略形の一覧については、このトピックで後述する「[サポートされている Unicode 一般カテゴリ](#SupportedUnicodeGeneralCategories)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-259">For a list of category abbreviations, see the [Supported Unicode General Categories](#SupportedUnicodeGeneralCategories) section later in this topic.</span></span> <span data-ttu-id="bdd25-260">名前付きブロックの一覧については、このトピックで後述する「[サポートされている名前付きブロック](#SupportedNamedBlocks)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-260">For a list of named blocks, see the [Supported Named Blocks](#SupportedNamedBlocks) section later in this topic.</span></span>  
  
 <span data-ttu-id="bdd25-261">`\P{`*name*`}` 構成要素を使用して通貨記号 (この場合は `Sc` (Symbol, Currency: 記号、通貨) カテゴリ) を数値文字列から削除する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-261">The following example uses the `\P{`*name*`}` construct to remove any currency symbols (in this case, the `Sc`, or Symbol, Currency category) from numeric strings.</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/notcategory1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/notcategory1.vb#7)]  
  
 <span data-ttu-id="bdd25-262">正規表現パターン `(\P{Sc})+` は、通貨記号以外の 1 つ以上の文字と一致し、実質的に結果文字列から通貨記号を削除します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-262">The regular expression pattern `(\P{Sc})+` matches one or more characters that are not currency symbols; it effectively strips any currency symbol from the result string.</span></span>  
  
 [<span data-ttu-id="bdd25-263">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="bdd25-263">Back to Top</span></span>](#Top)  
  
<a name="WordCharacter"></a>   
## <a name="word-character-w"></a><span data-ttu-id="bdd25-264">単語に使用される文字: \w</span><span class="sxs-lookup"><span data-stu-id="bdd25-264">Word Character: \w</span></span>  
 <span data-ttu-id="bdd25-265">`\w` は、単語に使用される任意の文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-265">`\w` matches any word character.</span></span> <span data-ttu-id="bdd25-266">単語に使用される文字は、次の表に示す Unicode カテゴリのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="bdd25-266">A word character is a member of any of the Unicode categories listed in the following table.</span></span>  
  
|<span data-ttu-id="bdd25-267">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="bdd25-267">Category</span></span>|<span data-ttu-id="bdd25-268">説明</span><span class="sxs-lookup"><span data-stu-id="bdd25-268">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="bdd25-269">Ll</span><span class="sxs-lookup"><span data-stu-id="bdd25-269">Ll</span></span>|<span data-ttu-id="bdd25-270">Letter, Lowercase (字、小文字)</span><span class="sxs-lookup"><span data-stu-id="bdd25-270">Letter, Lowercase</span></span>|  
|<span data-ttu-id="bdd25-271">Lu</span><span class="sxs-lookup"><span data-stu-id="bdd25-271">Lu</span></span>|<span data-ttu-id="bdd25-272">Letter, Uppercase (字、大文字)</span><span class="sxs-lookup"><span data-stu-id="bdd25-272">Letter, Uppercase</span></span>|  
|<span data-ttu-id="bdd25-273">Lt</span><span class="sxs-lookup"><span data-stu-id="bdd25-273">Lt</span></span>|<span data-ttu-id="bdd25-274">Letter, Titlecase (字、タイトル文字)</span><span class="sxs-lookup"><span data-stu-id="bdd25-274">Letter, Titlecase</span></span>|  
|<span data-ttu-id="bdd25-275">Lo</span><span class="sxs-lookup"><span data-stu-id="bdd25-275">Lo</span></span>|<span data-ttu-id="bdd25-276">Letter, Other (字、その他)</span><span class="sxs-lookup"><span data-stu-id="bdd25-276">Letter, Other</span></span>|  
|<span data-ttu-id="bdd25-277">Lm</span><span class="sxs-lookup"><span data-stu-id="bdd25-277">Lm</span></span>|<span data-ttu-id="bdd25-278">Letter, Modifier (字、修飾)</span><span class="sxs-lookup"><span data-stu-id="bdd25-278">Letter, Modifier</span></span>|  
|<span data-ttu-id="bdd25-279">Mn</span><span class="sxs-lookup"><span data-stu-id="bdd25-279">Mn</span></span>|<span data-ttu-id="bdd25-280">Mark, Nonspacing (結合文字、幅なし)</span><span class="sxs-lookup"><span data-stu-id="bdd25-280">Mark, Nonspacing</span></span>|  
|<span data-ttu-id="bdd25-281">Nd</span><span class="sxs-lookup"><span data-stu-id="bdd25-281">Nd</span></span>|<span data-ttu-id="bdd25-282">Number, Decimal Digit (数、10 進数字)</span><span class="sxs-lookup"><span data-stu-id="bdd25-282">Number, Decimal Digit</span></span>|  
|<span data-ttu-id="bdd25-283">Pc</span><span class="sxs-lookup"><span data-stu-id="bdd25-283">Pc</span></span>|<span data-ttu-id="bdd25-284">Punctuation, Connector (句読点、接続)。</span><span class="sxs-lookup"><span data-stu-id="bdd25-284">Punctuation, Connector.</span></span> <span data-ttu-id="bdd25-285">このカテゴリには 10 文字が含まれ、そのうち最もよく使用される文字は LOWLINE 文字 (_)、u+005F です。</span><span class="sxs-lookup"><span data-stu-id="bdd25-285">This category includes ten characters, the most commonly used of which is the LOWLINE character (_), u+005F.</span></span>|  
  
 <span data-ttu-id="bdd25-286">ECMAScript 準拠の動作が指定された場合、`\w` は `[a-zA-Z_0-9]` と同じになります。</span><span class="sxs-lookup"><span data-stu-id="bdd25-286">If ECMAScript-compliant behavior is specified, `\w` is equivalent to `[a-zA-Z_0-9]`.</span></span> <span data-ttu-id="bdd25-287">ECMAScript 正規表現の詳細については、「[正規表現のオプション](../../../docs/standard/base-types/regular-expression-options.md)」の「ECMAScript 一致の動作」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-287">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdd25-288">`\w` 言語要素は単語に使用される任意の文字と一致するので、正規表現パターンが単語に使用される任意の文字の後に特定の単語に使用される文字が続く語と複数回一致する場合に最短一致の量指定子と共によく使用されます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-288">Because it matches any word character, the `\w` language element is often used with a lazy quantifier if a regular expression pattern attempts to match any word character multiple times, followed by a specific word character.</span></span> <span data-ttu-id="bdd25-289">詳細については、「[量指定子](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-289">For more information, see [Quantifiers](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="bdd25-290">`\w` 言語要素を使用して単語内の重複する文字を照合する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-290">The following example uses the `\w` language element to match duplicate characters in a word.</span></span> <span data-ttu-id="bdd25-291">この例では、次のように解釈できる正規表現パターン `(\w)\1` を定義しています。</span><span class="sxs-lookup"><span data-stu-id="bdd25-291">The example defines a regular expression pattern, `(\w)\1`, which can be interpreted as follows.</span></span>  
  
|<span data-ttu-id="bdd25-292">要素</span><span class="sxs-lookup"><span data-stu-id="bdd25-292">Element</span></span>|<span data-ttu-id="bdd25-293">説明</span><span class="sxs-lookup"><span data-stu-id="bdd25-293">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bdd25-294">(\w)</span><span class="sxs-lookup"><span data-stu-id="bdd25-294">(\w)</span></span>|<span data-ttu-id="bdd25-295">単語に使用される文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-295">Match a word character.</span></span> <span data-ttu-id="bdd25-296">これが最初のキャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="bdd25-296">This is the first capturing group.</span></span>|  
|<span data-ttu-id="bdd25-297">\1</span><span class="sxs-lookup"><span data-stu-id="bdd25-297">\1</span></span>|<span data-ttu-id="bdd25-298">最初のキャプチャの値と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-298">Match the value of the first capture.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/wordchar1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/wordchar1.vb#8)]  
  
 [<span data-ttu-id="bdd25-299">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="bdd25-299">Back to Top</span></span>](#Top)  
  
<a name="NonWordCharacter"></a>   
## <a name="non-word-character-w"></a><span data-ttu-id="bdd25-300">単語に使用されない文字: \W</span><span class="sxs-lookup"><span data-stu-id="bdd25-300">Non-Word Character: \W</span></span>  
 <span data-ttu-id="bdd25-301">`\W` は、単語に使用される文字以外の任意の文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-301">`\W` matches any non-word character.</span></span> <span data-ttu-id="bdd25-302">\W 言語要素は、次の文字クラスと同じ結果をもたらします。</span><span class="sxs-lookup"><span data-stu-id="bdd25-302">The \W language element is equivalent to the following character class:</span></span>  
  
```  
[^\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]  
```  
  
 <span data-ttu-id="bdd25-303">つまり、次の表に示す Unicode カテゴリの文字を除く任意の文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-303">In other words, it matches any character except for those in the Unicode categories listed in the following table.</span></span>  
  
|<span data-ttu-id="bdd25-304">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="bdd25-304">Category</span></span>|<span data-ttu-id="bdd25-305">説明</span><span class="sxs-lookup"><span data-stu-id="bdd25-305">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="bdd25-306">Ll</span><span class="sxs-lookup"><span data-stu-id="bdd25-306">Ll</span></span>|<span data-ttu-id="bdd25-307">Letter, Lowercase (字、小文字)</span><span class="sxs-lookup"><span data-stu-id="bdd25-307">Letter, Lowercase</span></span>|  
|<span data-ttu-id="bdd25-308">Lu</span><span class="sxs-lookup"><span data-stu-id="bdd25-308">Lu</span></span>|<span data-ttu-id="bdd25-309">Letter, Uppercase (字、大文字)</span><span class="sxs-lookup"><span data-stu-id="bdd25-309">Letter, Uppercase</span></span>|  
|<span data-ttu-id="bdd25-310">Lt</span><span class="sxs-lookup"><span data-stu-id="bdd25-310">Lt</span></span>|<span data-ttu-id="bdd25-311">Letter, Titlecase (字、タイトル文字)</span><span class="sxs-lookup"><span data-stu-id="bdd25-311">Letter, Titlecase</span></span>|  
|<span data-ttu-id="bdd25-312">Lo</span><span class="sxs-lookup"><span data-stu-id="bdd25-312">Lo</span></span>|<span data-ttu-id="bdd25-313">Letter, Other (字、その他)</span><span class="sxs-lookup"><span data-stu-id="bdd25-313">Letter, Other</span></span>|  
|<span data-ttu-id="bdd25-314">Lm</span><span class="sxs-lookup"><span data-stu-id="bdd25-314">Lm</span></span>|<span data-ttu-id="bdd25-315">Letter, Modifier (字、修飾)</span><span class="sxs-lookup"><span data-stu-id="bdd25-315">Letter, Modifier</span></span>|  
|<span data-ttu-id="bdd25-316">Mn</span><span class="sxs-lookup"><span data-stu-id="bdd25-316">Mn</span></span>|<span data-ttu-id="bdd25-317">Mark, Nonspacing (結合文字、幅なし)</span><span class="sxs-lookup"><span data-stu-id="bdd25-317">Mark, Nonspacing</span></span>|  
|<span data-ttu-id="bdd25-318">Nd</span><span class="sxs-lookup"><span data-stu-id="bdd25-318">Nd</span></span>|<span data-ttu-id="bdd25-319">Number, Decimal Digit (数、10 進数字)</span><span class="sxs-lookup"><span data-stu-id="bdd25-319">Number, Decimal Digit</span></span>|  
|<span data-ttu-id="bdd25-320">Pc</span><span class="sxs-lookup"><span data-stu-id="bdd25-320">Pc</span></span>|<span data-ttu-id="bdd25-321">Punctuation, Connector (句読点、接続)。</span><span class="sxs-lookup"><span data-stu-id="bdd25-321">Punctuation, Connector.</span></span> <span data-ttu-id="bdd25-322">このカテゴリには 10 文字が含まれ、そのうち最もよく使用される文字は LOWLINE 文字 (_)、u+005F です。</span><span class="sxs-lookup"><span data-stu-id="bdd25-322">This category includes ten characters, the most commonly used of which is the LOWLINE character (_), u+005F.</span></span>|  
  
 <span data-ttu-id="bdd25-323">ECMAScript 準拠の動作が指定された場合、`\W` は `[^a-zA-Z_0-9]` と同じになります。</span><span class="sxs-lookup"><span data-stu-id="bdd25-323">If ECMAScript-compliant behavior is specified, `\W` is equivalent to `[^a-zA-Z_0-9]`.</span></span> <span data-ttu-id="bdd25-324">ECMAScript 正規表現の詳細については、「[正規表現のオプション](../../../docs/standard/base-types/regular-expression-options.md)」の「ECMAScript 一致の動作」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-324">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdd25-325">`\W` 言語要素は単語に使用されない任意の文字と一致するので、正規表現パターンが単語に使用されない任意の文字の後に特定の単語に使用されない文字が続く語と複数回一致する場合に最短一致の量指定子と共によく使用されます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-325">Because it matches any non-word character, the `\W` language element is often used with a lazy quantifier if a regular expression pattern attempts to match any non-word character multiple times followed by a specific non-word character.</span></span> <span data-ttu-id="bdd25-326">詳細については、「[正規表現での量指定子](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-326">For more information, see [Quantifiers](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="bdd25-327">`\W` 文字クラスの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-327">The following example illustrates the `\W` character class.</span></span>  <span data-ttu-id="bdd25-328">この例では、単語の後に 1 つまたは 2 つの単語に使用されない文字 (空白や句読点など) が続く場合に一致する正規表現パターン `\b(\w+)(\W){1,2}` を定義しています。</span><span class="sxs-lookup"><span data-stu-id="bdd25-328">It defines a regular expression pattern, `\b(\w+)(\W){1,2}`, that matches a word followed by one or two non-word characters, such as white space or punctuation.</span></span> <span data-ttu-id="bdd25-329">この正規表現の解釈を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-329">The regular expression is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="bdd25-330">要素</span><span class="sxs-lookup"><span data-stu-id="bdd25-330">Element</span></span>|<span data-ttu-id="bdd25-331">説明</span><span class="sxs-lookup"><span data-stu-id="bdd25-331">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bdd25-332">\b</span><span class="sxs-lookup"><span data-stu-id="bdd25-332">\b</span></span>|<span data-ttu-id="bdd25-333">ワード境界から照合を開始します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-333">Begin the match at a word boundary.</span></span>|  
|<span data-ttu-id="bdd25-334">(\w+)</span><span class="sxs-lookup"><span data-stu-id="bdd25-334">(\w+)</span></span>|<span data-ttu-id="bdd25-335">1 つ以上の単語文字に一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-335">Match one or more word characters.</span></span> <span data-ttu-id="bdd25-336">これが最初のキャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="bdd25-336">This is the first capturing group.</span></span>|  
|<span data-ttu-id="bdd25-337">(\W){1,2}</span><span class="sxs-lookup"><span data-stu-id="bdd25-337">(\W){1,2}</span></span>|<span data-ttu-id="bdd25-338">単語に使用されない文字と 1 回または 2 回一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-338">Match a non-word character either one or two times.</span></span> <span data-ttu-id="bdd25-339">これが 2 番目のキャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="bdd25-339">This is the second capturing group.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwordchar1.cs#9)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwordchar1.vb#9)]  
  
 <span data-ttu-id="bdd25-340">2 番目のキャプチャ グループの <xref:System.Text.RegularExpressions.Group> オブジェクトには、キャプチャされた単語に使用されない文字が 1 つだけ含まれるので、この例では、<xref:System.Text.RegularExpressions.CaptureCollection> プロパティによって返される <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> オブジェクトから、キャプチャされたすべての単語に使用されない文字を取得します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-340">Because the <xref:System.Text.RegularExpressions.Group> object for the second capturing group contains only a single captured non-word character, the example retrieves all captured non-word characters from the <xref:System.Text.RegularExpressions.CaptureCollection> object that is returned by the <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> property.</span></span>  
  
 [<span data-ttu-id="bdd25-341">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="bdd25-341">Back to Top</span></span>](#Top)  
  
<a name="WhitespaceCharacter"></a>   
## <a name="white-space-character-s"></a><span data-ttu-id="bdd25-342">空白文字: \s</span><span class="sxs-lookup"><span data-stu-id="bdd25-342">White-Space Character: \s</span></span>  
 <span data-ttu-id="bdd25-343">`\s` は、空白文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-343">`\s` matches any white-space character.</span></span> <span data-ttu-id="bdd25-344">次の表に示すエスケープ シーケンスおよび Unicode カテゴリと同じ結果をもたらします。</span><span class="sxs-lookup"><span data-stu-id="bdd25-344">It is equivalent to the escape sequences and Unicode categories listed in the following table.</span></span>  
  
|<span data-ttu-id="bdd25-345">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="bdd25-345">Category</span></span>|<span data-ttu-id="bdd25-346">説明</span><span class="sxs-lookup"><span data-stu-id="bdd25-346">Description</span></span>|  
|--------------|-----------------|  
|`\f`|<span data-ttu-id="bdd25-347">フォーム フィード文字 (\u000C)。</span><span class="sxs-lookup"><span data-stu-id="bdd25-347">The form feed character, \u000C.</span></span>|  
|`\n`|<span data-ttu-id="bdd25-348">改行文字 (\u000A)。</span><span class="sxs-lookup"><span data-stu-id="bdd25-348">The newline character, \u000A.</span></span>|  
|`\r`|<span data-ttu-id="bdd25-349">復帰文字 (\u000D)。</span><span class="sxs-lookup"><span data-stu-id="bdd25-349">The carriage return character, \u000D.</span></span>|  
|`\t`|<span data-ttu-id="bdd25-350">タブ文字 (\u0009)。</span><span class="sxs-lookup"><span data-stu-id="bdd25-350">The tab character, \u0009.</span></span>|  
|`\v`|<span data-ttu-id="bdd25-351">垂直タブ文字 (\u000B)。</span><span class="sxs-lookup"><span data-stu-id="bdd25-351">The vertical tab character, \u000B.</span></span>|  
|`\x85`|<span data-ttu-id="bdd25-352">省略記号または NEXT LINE (NEL) 文字 (…) (\u0085)。</span><span class="sxs-lookup"><span data-stu-id="bdd25-352">The ellipsis or NEXT LINE (NEL) character (…), \u0085.</span></span>|  
|`\p{Z}`|<span data-ttu-id="bdd25-353">任意の区切り記号と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-353">Matches any separator character.</span></span>|  
  
 <span data-ttu-id="bdd25-354">ECMAScript 準拠の動作が指定された場合、`\s` は `[ \f\n\r\t\v]` と同じになります。</span><span class="sxs-lookup"><span data-stu-id="bdd25-354">If ECMAScript-compliant behavior is specified, `\s` is equivalent to `[ \f\n\r\t\v]`.</span></span> <span data-ttu-id="bdd25-355">ECMAScript 正規表現の詳細については、「[正規表現のオプション](../../../docs/standard/base-types/regular-expression-options.md)」の「ECMAScript 一致の動作」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-355">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
 <span data-ttu-id="bdd25-356">`\s` 文字クラスの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-356">The following example illustrates the `\s` character class.</span></span> <span data-ttu-id="bdd25-357">この例では、"s" または "es" で終わる単語の後に空白文字または入力文字列の末尾が続く場合に一致する正規表現パターン `\b\w+(e)?s(\s|$)` を定義しています。</span><span class="sxs-lookup"><span data-stu-id="bdd25-357">It defines a regular expression pattern, `\b\w+(e)?s(\s|$)`, that matches a word ending in either "s" or "es" followed by either a white-space character or the end of the input string.</span></span> <span data-ttu-id="bdd25-358">この正規表現の解釈を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-358">The regular expression is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="bdd25-359">要素</span><span class="sxs-lookup"><span data-stu-id="bdd25-359">Element</span></span>|<span data-ttu-id="bdd25-360">説明</span><span class="sxs-lookup"><span data-stu-id="bdd25-360">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bdd25-361">\b</span><span class="sxs-lookup"><span data-stu-id="bdd25-361">\b</span></span>|<span data-ttu-id="bdd25-362">ワード境界から照合を開始します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-362">Begin the match at a word boundary.</span></span>|  
|<span data-ttu-id="bdd25-363">\w+</span><span class="sxs-lookup"><span data-stu-id="bdd25-363">\w+</span></span>|<span data-ttu-id="bdd25-364">1 つ以上の単語文字に一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-364">Match one or more word characters.</span></span>|  
|<span data-ttu-id="bdd25-365">(e)?</span><span class="sxs-lookup"><span data-stu-id="bdd25-365">(e)?</span></span>|<span data-ttu-id="bdd25-366">"e" と 0 回または 1 回一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-366">Match an "e" either zero or one time.</span></span>|  
|<span data-ttu-id="bdd25-367">s</span><span class="sxs-lookup"><span data-stu-id="bdd25-367">s</span></span>|<span data-ttu-id="bdd25-368">"s" と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-368">Match an "s".</span></span>|  
|<span data-ttu-id="bdd25-369">(\s&#124;$)</span><span class="sxs-lookup"><span data-stu-id="bdd25-369">(\s&#124;$)</span></span>|<span data-ttu-id="bdd25-370">空白文字または入力文字列の末尾と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-370">Match either a whitespace character or the end of the input string.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/whitespace1.cs#10)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/whitespace1.vb#10)]  
  
 [<span data-ttu-id="bdd25-371">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="bdd25-371">Back to Top</span></span>](#Top)  
  
<a name="NonWhitespaceCharacter"></a>   
## <a name="non-white-space-character-s"></a><span data-ttu-id="bdd25-372">空白以外の文字: \S</span><span class="sxs-lookup"><span data-stu-id="bdd25-372">Non-White-Space Character: \S</span></span>  
 <span data-ttu-id="bdd25-373">`\S` は、空白文字以外の任意の文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-373">`\S` matches any non-white-space character.</span></span> <span data-ttu-id="bdd25-374">`[^\f\n\r\t\v\x85\p{Z}]` 正規表現パターン、または空白文字と一致する `\s` に相当する正規表現パターンの逆と同じ結果をもたらします。</span><span class="sxs-lookup"><span data-stu-id="bdd25-374">It is equivalent to the `[^\f\n\r\t\v\x85\p{Z}]` regular expression pattern, or the opposite of the regular expression pattern that is equivalent to `\s`, which matches white-space characters.</span></span> <span data-ttu-id="bdd25-375">詳細については、「[空白文字: \s](#WhitespaceCharacter)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-375">For more information, see [White-Space Character: \s](#WhitespaceCharacter).</span></span>  
  
 <span data-ttu-id="bdd25-376">ECMAScript 準拠の動作が指定された場合、`\S` は `[^ \f\n\r\t\v]` と同じになります。</span><span class="sxs-lookup"><span data-stu-id="bdd25-376">If ECMAScript-compliant behavior is specified, `\S` is equivalent to  `[^ \f\n\r\t\v]`.</span></span> <span data-ttu-id="bdd25-377">ECMAScript 正規表現の詳細については、「[正規表現のオプション](../../../docs/standard/base-types/regular-expression-options.md)」の「ECMAScript 一致の動作」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-377">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
 <span data-ttu-id="bdd25-378">`\S` 言語要素の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-378">The following example illustrates the `\S` language element.</span></span> <span data-ttu-id="bdd25-379">正規表現パターン `\b(\S+)\s?` は、空白文字で区切られた文字列と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-379">The regular expression pattern `\b(\S+)\s?` matches strings that are delimited by white-space characters.</span></span> <span data-ttu-id="bdd25-380">一致部分の <xref:System.Text.RegularExpressions.GroupCollection> オブジェクトの 2 番目の要素に一致する文字列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-380">The second element in the match's <xref:System.Text.RegularExpressions.GroupCollection> object contains the matched string.</span></span> <span data-ttu-id="bdd25-381">この正規表現の解釈を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-381">The regular expression can be interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="bdd25-382">要素</span><span class="sxs-lookup"><span data-stu-id="bdd25-382">Element</span></span>|<span data-ttu-id="bdd25-383">説明</span><span class="sxs-lookup"><span data-stu-id="bdd25-383">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="bdd25-384">ワード境界から照合を開始します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-384">Begin the match at a word boundary.</span></span>|  
|`(\S+)`|<span data-ttu-id="bdd25-385">1 つ以上の空白以外の文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-385">Match one or more non-white-space characters.</span></span> <span data-ttu-id="bdd25-386">これが最初のキャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="bdd25-386">This is the first capturing group.</span></span>|  
|`\s?`|<span data-ttu-id="bdd25-387">0 個または 1 個の空白文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-387">Match zero or one white-space character.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwhitespace1.cs#11)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwhitespace1.vb#11)]  
  
 [<span data-ttu-id="bdd25-388">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="bdd25-388">Back to Top</span></span>](#Top)  
  
<a name="DigitCharacter"></a>   
## <a name="decimal-digit-character-d"></a><span data-ttu-id="bdd25-389">10 進数字: \d</span><span class="sxs-lookup"><span data-stu-id="bdd25-389">Decimal Digit Character: \d</span></span>  
 <span data-ttu-id="bdd25-390">`\d` は、10 進数字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-390">`\d` matches any decimal digit.</span></span> <span data-ttu-id="bdd25-391">標準の 10 進数 0 ～ 9 およびその他の各種文字セットの 10 進数を含む `\p{Nd}` 正規表現パターンと同じ結果をもたらします。</span><span class="sxs-lookup"><span data-stu-id="bdd25-391">It is equivalent to the `\p{Nd}` regular expression pattern, which includes the standard decimal digits 0-9 as well as the decimal digits of a number of other character sets.</span></span>  
  
 <span data-ttu-id="bdd25-392">ECMAScript 準拠の動作が指定された場合、`\d` は `[0-9]` と同じになります。</span><span class="sxs-lookup"><span data-stu-id="bdd25-392">If ECMAScript-compliant behavior is specified, `\d` is equivalent to  `[0-9]`.</span></span> <span data-ttu-id="bdd25-393">ECMAScript 正規表現の詳細については、「[正規表現のオプション](../../../docs/standard/base-types/regular-expression-options.md)」の「ECMAScript 一致の動作」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-393">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
 <span data-ttu-id="bdd25-394">`\d` 言語要素の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-394">The following example illustrates the `\d` language element.</span></span> <span data-ttu-id="bdd25-395">この例では、入力文字列が米国およびカナダの有効な電話番号を表すかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="bdd25-395">It tests whether an input string represents a valid telephone number in the United States and Canada.</span></span> <span data-ttu-id="bdd25-396">正規表現パターン `^(\(?\d{3}\)?[\s-])?\d{3}-\d{4}$` は、次の表に示すように定義されています。</span><span class="sxs-lookup"><span data-stu-id="bdd25-396">The regular expression pattern `^(\(?\d{3}\)?[\s-])?\d{3}-\d{4}$` is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="bdd25-397">要素</span><span class="sxs-lookup"><span data-stu-id="bdd25-397">Element</span></span>|<span data-ttu-id="bdd25-398">説明</span><span class="sxs-lookup"><span data-stu-id="bdd25-398">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="bdd25-399">入力文字列の先頭から照合を開始します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-399">Begin the match at the beginning of the input string.</span></span>|  
|`\(?`|<span data-ttu-id="bdd25-400">0 個または 1 個のリテラル "(" 文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-400">Match zero or one literal "(" character.</span></span>|  
|`\d{3}`|<span data-ttu-id="bdd25-401">3 個の 10 進数と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-401">Match three decimal digits.</span></span>|  
|`\)?`|<span data-ttu-id="bdd25-402">0 個または 1 個のリテラル ")" 文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-402">Match zero or one literal ")" character.</span></span>|  
|`[\s-]`|<span data-ttu-id="bdd25-403">ハイフンまたは空白文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-403">Match a hyphen or a white-space character.</span></span>|  
|`(\(?\d{3}\)?[\s-])?`|<span data-ttu-id="bdd25-404">省略可能な左かっこの後に 3 個の 10 進数が続く部分、省略可能な右かっこ、および空白文字またはハイフンと 0 回または 1 回一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-404">Match an optional opening parenthesis followed by three decimal digits, an optional closing parenthesis, and either a white-space character or a hyphen zero or one time.</span></span> <span data-ttu-id="bdd25-405">これが最初のキャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="bdd25-405">This is the first capturing group.</span></span>|  
|`\d{3}-\d{4}`|<span data-ttu-id="bdd25-406">3 個の 10 進数の後にハイフンおよび 4 個以上の 10 進数が続く場合に一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-406">Match three decimal digits followed by a hyphen and four more decimal digits.</span></span>|  
|`$`|<span data-ttu-id="bdd25-407">入力文字列の末尾と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-407">Match the end of the input string.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/digit1.cs#12)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/digit1.vb#12)]  
  
 [<span data-ttu-id="bdd25-408">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="bdd25-408">Back to Top</span></span>](#Top)  
  
<a name="NonDigitCharacter"></a>   
## <a name="non-digit-character-d"></a><span data-ttu-id="bdd25-409">数字以外の文字: \D</span><span class="sxs-lookup"><span data-stu-id="bdd25-409">Non-Digit Character: \D</span></span>  
 <span data-ttu-id="bdd25-410">`\D` は、数字以外の文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-410">`\D` matches any non-digit character.</span></span> <span data-ttu-id="bdd25-411">`\P{Nd}` 正規表現パターンと同じ結果をもたらします。</span><span class="sxs-lookup"><span data-stu-id="bdd25-411">It is equivalent to the `\P{Nd}` regular expression pattern.</span></span>  
  
 <span data-ttu-id="bdd25-412">ECMAScript 準拠の動作が指定された場合、`\D` は `[^0-9]` と同じになります。</span><span class="sxs-lookup"><span data-stu-id="bdd25-412">If ECMAScript-compliant behavior is specified, `\D` is equivalent to  `[^0-9]`.</span></span> <span data-ttu-id="bdd25-413">ECMAScript 正規表現の詳細については、「[正規表現のオプション](../../../docs/standard/base-types/regular-expression-options.md)」の「ECMAScript 一致の動作」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-413">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
 <span data-ttu-id="bdd25-414">\D 言語要素の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-414">The following example illustrates the \D language element.</span></span> <span data-ttu-id="bdd25-415">部品番号などの文字列が 10 進数および 10 進数以外の文字を適切に組み合わせて構成されているかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="bdd25-415">It tests whether a string such as a part number consists of the appropriate combination of decimal and non-decimal characters.</span></span> <span data-ttu-id="bdd25-416">正規表現パターン `^\D\d{1,5}\D*$` は、次の表に示すように定義されています。</span><span class="sxs-lookup"><span data-stu-id="bdd25-416">The regular expression pattern `^\D\d{1,5}\D*$` is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="bdd25-417">要素</span><span class="sxs-lookup"><span data-stu-id="bdd25-417">Element</span></span>|<span data-ttu-id="bdd25-418">説明</span><span class="sxs-lookup"><span data-stu-id="bdd25-418">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="bdd25-419">入力文字列の先頭から照合を開始します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-419">Begin the match at the beginning of the input string.</span></span>|  
|`\D`|<span data-ttu-id="bdd25-420">数字以外の文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-420">Match a non-digit character.</span></span>|  
|`\d{1,5}`|<span data-ttu-id="bdd25-421">1 ～ 5 個の 10 進数と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-421">Match from one to five decimal digits.</span></span>|  
|`\D*`|<span data-ttu-id="bdd25-422">0 個または 1 個以上の 10 進数以外の文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-422">Match zero, one, or more non-decimal characters.</span></span>|  
|`$`|<span data-ttu-id="bdd25-423">入力文字列の末尾と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-423">Match the end of the input string.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nondigit1.cs#13)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nondigit1.vb#13)]  
  
 [<span data-ttu-id="bdd25-424">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="bdd25-424">Back to Top</span></span>](#Top)  
  
<a name="SupportedUnicodeGeneralCategories"></a>   
## <a name="supported-unicode-general-categories"></a><span data-ttu-id="bdd25-425">サポートされている Unicode 一般カテゴリ</span><span class="sxs-lookup"><span data-stu-id="bdd25-425">Supported Unicode General Categories</span></span>  
 <span data-ttu-id="bdd25-426">Unicode は、次の表に示されている一般カテゴリを定義しています。</span><span class="sxs-lookup"><span data-stu-id="bdd25-426">Unicode defines the general categories listed in the following table.</span></span> <span data-ttu-id="bdd25-427">詳細については、「[Unicode Character Database (Unicode 文字データベース)](http://www.unicode.org/reports/tr44/)」内の「UCD File Format (UCD ファイル形式)」および「General Category Values (一般カテゴリの値)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-427">For more information, see the "UCD File Format" and "General Category Values" subtopics at the [Unicode Character Database](http://www.unicode.org/reports/tr44/).</span></span>  
  
|<span data-ttu-id="bdd25-428">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="bdd25-428">Category</span></span>|<span data-ttu-id="bdd25-429">説明</span><span class="sxs-lookup"><span data-stu-id="bdd25-429">Description</span></span>|  
|--------------|-----------------|  
|`Lu`|<span data-ttu-id="bdd25-430">Letter, Uppercase (字、大文字)</span><span class="sxs-lookup"><span data-stu-id="bdd25-430">Letter, Uppercase</span></span>|  
|`Ll`|<span data-ttu-id="bdd25-431">Letter, Lowercase (字、小文字)</span><span class="sxs-lookup"><span data-stu-id="bdd25-431">Letter, Lowercase</span></span>|  
|`Lt`|<span data-ttu-id="bdd25-432">Letter, Titlecase (字、タイトル文字)</span><span class="sxs-lookup"><span data-stu-id="bdd25-432">Letter, Titlecase</span></span>|  
|`Lm`|<span data-ttu-id="bdd25-433">Letter, Modifier (字、修飾)</span><span class="sxs-lookup"><span data-stu-id="bdd25-433">Letter, Modifier</span></span>|  
|`Lo`|<span data-ttu-id="bdd25-434">Letter, Other (字、その他)</span><span class="sxs-lookup"><span data-stu-id="bdd25-434">Letter, Other</span></span>|  
|`L`|<span data-ttu-id="bdd25-435">すべてのアルファベット文字。</span><span class="sxs-lookup"><span data-stu-id="bdd25-435">All letter characters.</span></span> <span data-ttu-id="bdd25-436">これには、`Lu`、`Ll`、`Lt`、`Lm`、および `Lo` の各文字が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-436">This includes the `Lu`, `Ll`, `Lt`, `Lm`, and `Lo` characters.</span></span>|  
|`Mn`|<span data-ttu-id="bdd25-437">Mark, Nonspacing (結合文字、幅なし)</span><span class="sxs-lookup"><span data-stu-id="bdd25-437">Mark, Nonspacing</span></span>|  
|`Mc`|<span data-ttu-id="bdd25-438">Mark, Spacing Combining (結合文字、幅あり)</span><span class="sxs-lookup"><span data-stu-id="bdd25-438">Mark, Spacing Combining</span></span>|  
|`Me`|<span data-ttu-id="bdd25-439">Mark, Enclosing (結合文字、囲み)</span><span class="sxs-lookup"><span data-stu-id="bdd25-439">Mark, Enclosing</span></span>|  
|`M`|<span data-ttu-id="bdd25-440">すべての分音記号。</span><span class="sxs-lookup"><span data-stu-id="bdd25-440">All diacritic marks.</span></span> <span data-ttu-id="bdd25-441">これには、`Mn`、`Mc`、および `Me` の各カテゴリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-441">This includes the `Mn`, `Mc`, and `Me` categories.</span></span>|  
|`Nd`|<span data-ttu-id="bdd25-442">Number, Decimal Digit (数、10 進数字)</span><span class="sxs-lookup"><span data-stu-id="bdd25-442">Number, Decimal Digit</span></span>|  
|`Nl`|<span data-ttu-id="bdd25-443">Number, Letter (数、字)</span><span class="sxs-lookup"><span data-stu-id="bdd25-443">Number, Letter</span></span>|  
|`No`|<span data-ttu-id="bdd25-444">Number, Other (数、その他)</span><span class="sxs-lookup"><span data-stu-id="bdd25-444">Number, Other</span></span>|  
|`N`|<span data-ttu-id="bdd25-445">すべての数。</span><span class="sxs-lookup"><span data-stu-id="bdd25-445">All numbers.</span></span> <span data-ttu-id="bdd25-446">これには、`Nd`、`Nl`、および `No` の各カテゴリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-446">This includes the `Nd`, `Nl`, and `No` categories.</span></span>|  
|`Pc`|<span data-ttu-id="bdd25-447">Punctuation, Connector (句読点、接続)</span><span class="sxs-lookup"><span data-stu-id="bdd25-447">Punctuation, Connector</span></span>|  
|`Pd`|<span data-ttu-id="bdd25-448">Punctuation, Dash (句読点、ダッシュ)</span><span class="sxs-lookup"><span data-stu-id="bdd25-448">Punctuation, Dash</span></span>|  
|`Ps`|<span data-ttu-id="bdd25-449">Punctuation, Open (句読点、開き)</span><span class="sxs-lookup"><span data-stu-id="bdd25-449">Punctuation, Open</span></span>|  
|`Pe`|<span data-ttu-id="bdd25-450">Punctuation, Close (句読点、閉じ)</span><span class="sxs-lookup"><span data-stu-id="bdd25-450">Punctuation, Close</span></span>|  
|`Pi`|<span data-ttu-id="bdd25-451">Punctuation, Initial quote (句読点、開始引用符。使用状況に応じて Ps または Pe のように動作)</span><span class="sxs-lookup"><span data-stu-id="bdd25-451">Punctuation, Initial quote (may behave like Ps or Pe depending on usage)</span></span>|  
|`Pf`|<span data-ttu-id="bdd25-452">Punctuation, Final quote (句読点、終了引用符。使用状況に応じて Ps または Pe のように動作)</span><span class="sxs-lookup"><span data-stu-id="bdd25-452">Punctuation, Final quote (may behave like Ps or Pe depending on usage)</span></span>|  
|`Po`|<span data-ttu-id="bdd25-453">Punctuation, Other (句読点、その他)</span><span class="sxs-lookup"><span data-stu-id="bdd25-453">Punctuation, Other</span></span>|  
|`P`|<span data-ttu-id="bdd25-454">すべての句読点。</span><span class="sxs-lookup"><span data-stu-id="bdd25-454">All punctuation characters.</span></span> <span data-ttu-id="bdd25-455">これには、`Pc`、`Pd`、`Ps`、`Pe`、`Pi`、`Pf`、および `Po` の各カテゴリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-455">This includes the `Pc`, `Pd`, `Ps`, `Pe`, `Pi`, `Pf`, and `Po` categories.</span></span>|  
|`Sm`|<span data-ttu-id="bdd25-456">Symbol, Math (記号、数学)</span><span class="sxs-lookup"><span data-stu-id="bdd25-456">Symbol, Math</span></span>|  
|`Sc`|<span data-ttu-id="bdd25-457">Symbol, Currency (記号、通貨)</span><span class="sxs-lookup"><span data-stu-id="bdd25-457">Symbol, Currency</span></span>|  
|`Sk`|<span data-ttu-id="bdd25-458">Symbol, Modifier (記号、修飾)</span><span class="sxs-lookup"><span data-stu-id="bdd25-458">Symbol, Modifier</span></span>|  
|`So`|<span data-ttu-id="bdd25-459">Symbol, Other (記号、その他)</span><span class="sxs-lookup"><span data-stu-id="bdd25-459">Symbol, Other</span></span>|  
|`S`|<span data-ttu-id="bdd25-460">すべての記号。</span><span class="sxs-lookup"><span data-stu-id="bdd25-460">All symbols.</span></span> <span data-ttu-id="bdd25-461">これには、`Sm`、`Sc`、`Sk`、および `So` の各カテゴリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-461">This includes the `Sm`, `Sc`, `Sk`, and `So` categories.</span></span>|  
|`Zs`|<span data-ttu-id="bdd25-462">Separator, Space (区切り、空白)</span><span class="sxs-lookup"><span data-stu-id="bdd25-462">Separator, Space</span></span>|  
|`Zl`|<span data-ttu-id="bdd25-463">Separator, Line (区切り、行)</span><span class="sxs-lookup"><span data-stu-id="bdd25-463">Separator, Line</span></span>|  
|`Zp`|<span data-ttu-id="bdd25-464">Separator, Paragraph (区切り、段落)</span><span class="sxs-lookup"><span data-stu-id="bdd25-464">Separator, Paragraph</span></span>|  
|`Z`|<span data-ttu-id="bdd25-465">すべての区切り記号。</span><span class="sxs-lookup"><span data-stu-id="bdd25-465">All separator characters.</span></span> <span data-ttu-id="bdd25-466">これには、`Zs`、`Zl`、および `Zp` の各カテゴリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-466">This includes the `Zs`, `Zl`, and `Zp` categories.</span></span>|  
|`Cc`|<span data-ttu-id="bdd25-467">Other, Control (区切り、制御)</span><span class="sxs-lookup"><span data-stu-id="bdd25-467">Other, Control</span></span>|  
|`Cf`|<span data-ttu-id="bdd25-468">Other, Format (その他、書式)</span><span class="sxs-lookup"><span data-stu-id="bdd25-468">Other, Format</span></span>|  
|`Cs`|<span data-ttu-id="bdd25-469">Other, Surrogate (その他、サロゲート)</span><span class="sxs-lookup"><span data-stu-id="bdd25-469">Other, Surrogate</span></span>|  
|`Co`|<span data-ttu-id="bdd25-470">Other, Private Use (その他、プライベート用途)</span><span class="sxs-lookup"><span data-stu-id="bdd25-470">Other, Private Use</span></span>|  
|`Cn`|<span data-ttu-id="bdd25-471">Other, Not Assigned (その他、未割り当て。このプロパティを持つ文字はありません)</span><span class="sxs-lookup"><span data-stu-id="bdd25-471">Other, Not Assigned (no characters have this property)</span></span>|  
|`C`|<span data-ttu-id="bdd25-472">すべての制御文字。</span><span class="sxs-lookup"><span data-stu-id="bdd25-472">All control characters.</span></span> <span data-ttu-id="bdd25-473">これには、`Cc`、`Cf`、`Cs`、`Co`、および `Cn` の各カテゴリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-473">This includes the `Cc`, `Cf`, `Cs`, `Co`, and `Cn` categories.</span></span>|  
  
 <span data-ttu-id="bdd25-474">特定の文字の Unicode カテゴリを確認するには、その文字を <xref:System.Char.GetUnicodeCategory%2A> メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-474">You can determine the Unicode category of any particular character by passing that character to the <xref:System.Char.GetUnicodeCategory%2A> method.</span></span> <span data-ttu-id="bdd25-475"><xref:System.Char.GetUnicodeCategory%2A> メソッドを使用して、選択したラテン文字を含む配列の各要素のカテゴリを確認する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-475">The following example uses the <xref:System.Char.GetUnicodeCategory%2A> method to determine the category of each element in an array that contains selected Latin characters.</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/getunicodecategory1.cs#14)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/getunicodecategory1.vb#14)]  
  
 [<span data-ttu-id="bdd25-476">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="bdd25-476">Back to Top</span></span>](#Top)  
  
<a name="SupportedNamedBlocks"></a>   
## <a name="supported-named-blocks"></a><span data-ttu-id="bdd25-477">サポートされている名前付きブロック</span><span class="sxs-lookup"><span data-stu-id="bdd25-477">Supported Named Blocks</span></span>  
 <span data-ttu-id="bdd25-478">.NET には、次の表に示す名前付きブロックが用意されています。</span><span class="sxs-lookup"><span data-stu-id="bdd25-478">.NET provides the named blocks listed in the following table.</span></span> <span data-ttu-id="bdd25-479">サポートされている一連の名前付きブロックは、Unicode 4.0 および Perl 5.6 に基づいています。</span><span class="sxs-lookup"><span data-stu-id="bdd25-479">The set of supported named blocks is based on Unicode 4.0 and Perl 5.6.</span></span>  
  
|<span data-ttu-id="bdd25-480">コード ポイント範囲</span><span class="sxs-lookup"><span data-stu-id="bdd25-480">Code point range</span></span>|<span data-ttu-id="bdd25-481">ブロック名</span><span class="sxs-lookup"><span data-stu-id="bdd25-481">Block name</span></span>|  
|----------------------|----------------|  
|<span data-ttu-id="bdd25-482">0000 ～ 007F</span><span class="sxs-lookup"><span data-stu-id="bdd25-482">0000 - 007F</span></span>|`IsBasicLatin`|  
|<span data-ttu-id="bdd25-483">0080 ～ 00FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-483">0080 - 00FF</span></span>|`IsLatin-1Supplement`|  
|<span data-ttu-id="bdd25-484">0100 ～ 017F</span><span class="sxs-lookup"><span data-stu-id="bdd25-484">0100 - 017F</span></span>|`IsLatinExtended-A`|  
|<span data-ttu-id="bdd25-485">0180 ～ 024F</span><span class="sxs-lookup"><span data-stu-id="bdd25-485">0180 - 024F</span></span>|`IsLatinExtended-B`|  
|<span data-ttu-id="bdd25-486">0250 ～ 02AF</span><span class="sxs-lookup"><span data-stu-id="bdd25-486">0250 - 02AF</span></span>|`IsIPAExtensions`|  
|<span data-ttu-id="bdd25-487">02B0 ～ 02FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-487">02B0 - 02FF</span></span>|`IsSpacingModifierLetters`|  
|<span data-ttu-id="bdd25-488">0300 ～ 036F</span><span class="sxs-lookup"><span data-stu-id="bdd25-488">0300 - 036F</span></span>|`IsCombiningDiacriticalMarks`|  
|<span data-ttu-id="bdd25-489">0370 ～ 03FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-489">0370 - 03FF</span></span>|`IsGreek`<br /><br /> <span data-ttu-id="bdd25-490">- または -</span><span class="sxs-lookup"><span data-stu-id="bdd25-490">-or-</span></span><br /><br /> `IsGreekandCoptic`|  
|<span data-ttu-id="bdd25-491">0400 ～ 04FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-491">0400 - 04FF</span></span>|`IsCyrillic`|  
|<span data-ttu-id="bdd25-492">0500 ～ 052F</span><span class="sxs-lookup"><span data-stu-id="bdd25-492">0500 - 052F</span></span>|`IsCyrillicSupplement`|  
|<span data-ttu-id="bdd25-493">0530 ～ 058F</span><span class="sxs-lookup"><span data-stu-id="bdd25-493">0530 - 058F</span></span>|`IsArmenian`|  
|<span data-ttu-id="bdd25-494">0590 ～ 05FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-494">0590 - 05FF</span></span>|`IsHebrew`|  
|<span data-ttu-id="bdd25-495">0600 ～ 06FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-495">0600 - 06FF</span></span>|`IsArabic`|  
|<span data-ttu-id="bdd25-496">0700 ～ 074F</span><span class="sxs-lookup"><span data-stu-id="bdd25-496">0700 - 074F</span></span>|`IsSyriac`|  
|<span data-ttu-id="bdd25-497">0780 ～ 07BF</span><span class="sxs-lookup"><span data-stu-id="bdd25-497">0780 - 07BF</span></span>|`IsThaana`|  
|<span data-ttu-id="bdd25-498">0900 ～ 097F</span><span class="sxs-lookup"><span data-stu-id="bdd25-498">0900 - 097F</span></span>|`IsDevanagari`|  
|<span data-ttu-id="bdd25-499">0980 ～ 09FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-499">0980 - 09FF</span></span>|`IsBengali`|  
|<span data-ttu-id="bdd25-500">0A00 ～ 0A7F</span><span class="sxs-lookup"><span data-stu-id="bdd25-500">0A00 - 0A7F</span></span>|`IsGurmukhi`|  
|<span data-ttu-id="bdd25-501">0A80 ～ 0AFF</span><span class="sxs-lookup"><span data-stu-id="bdd25-501">0A80 - 0AFF</span></span>|`IsGujarati`|  
|<span data-ttu-id="bdd25-502">0B00 ～ 0B7F</span><span class="sxs-lookup"><span data-stu-id="bdd25-502">0B00 - 0B7F</span></span>|`IsOriya`|  
|<span data-ttu-id="bdd25-503">0B80 ～ 0BFF</span><span class="sxs-lookup"><span data-stu-id="bdd25-503">0B80 - 0BFF</span></span>|`IsTamil`|  
|<span data-ttu-id="bdd25-504">0C00 ～ 0C7F</span><span class="sxs-lookup"><span data-stu-id="bdd25-504">0C00 - 0C7F</span></span>|`IsTelugu`|  
|<span data-ttu-id="bdd25-505">0C80 ～ 0CFF</span><span class="sxs-lookup"><span data-stu-id="bdd25-505">0C80 - 0CFF</span></span>|`IsKannada`|  
|<span data-ttu-id="bdd25-506">0D00 ～ 0D7F</span><span class="sxs-lookup"><span data-stu-id="bdd25-506">0D00 - 0D7F</span></span>|`IsMalayalam`|  
|<span data-ttu-id="bdd25-507">0D80 ～ 0DFF</span><span class="sxs-lookup"><span data-stu-id="bdd25-507">0D80 - 0DFF</span></span>|`IsSinhala`|  
|<span data-ttu-id="bdd25-508">0E00 ～ 0E7F</span><span class="sxs-lookup"><span data-stu-id="bdd25-508">0E00 - 0E7F</span></span>|`IsThai`|  
|<span data-ttu-id="bdd25-509">0E80 ～ 0EFF</span><span class="sxs-lookup"><span data-stu-id="bdd25-509">0E80 - 0EFF</span></span>|`IsLao`|  
|<span data-ttu-id="bdd25-510">0F00 ～ 0FFF</span><span class="sxs-lookup"><span data-stu-id="bdd25-510">0F00 - 0FFF</span></span>|`IsTibetan`|  
|<span data-ttu-id="bdd25-511">1000 ～ 109F</span><span class="sxs-lookup"><span data-stu-id="bdd25-511">1000 - 109F</span></span>|`IsMyanmar`|  
|<span data-ttu-id="bdd25-512">10A0 ～ 10FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-512">10A0 - 10FF</span></span>|`IsGeorgian`|  
|<span data-ttu-id="bdd25-513">1100 ～ 11FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-513">1100 - 11FF</span></span>|`IsHangulJamo`|  
|<span data-ttu-id="bdd25-514">1200 ～ 137F</span><span class="sxs-lookup"><span data-stu-id="bdd25-514">1200 - 137F</span></span>|`IsEthiopic`|  
|<span data-ttu-id="bdd25-515">13A0 ～ 13FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-515">13A0 - 13FF</span></span>|`IsCherokee`|  
|<span data-ttu-id="bdd25-516">1400 ～ 167F</span><span class="sxs-lookup"><span data-stu-id="bdd25-516">1400 - 167F</span></span>|`IsUnifiedCanadianAboriginalSyllabics`|  
|<span data-ttu-id="bdd25-517">1680 ～ 169F</span><span class="sxs-lookup"><span data-stu-id="bdd25-517">1680 - 169F</span></span>|`IsOgham`|  
|<span data-ttu-id="bdd25-518">16A0 ～ 16FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-518">16A0 - 16FF</span></span>|`IsRunic`|  
|<span data-ttu-id="bdd25-519">1700 ～ 171F</span><span class="sxs-lookup"><span data-stu-id="bdd25-519">1700 - 171F</span></span>|`IsTagalog`|  
|<span data-ttu-id="bdd25-520">1720 ～ 173F</span><span class="sxs-lookup"><span data-stu-id="bdd25-520">1720 - 173F</span></span>|`IsHanunoo`|  
|<span data-ttu-id="bdd25-521">1740 ～ 175F</span><span class="sxs-lookup"><span data-stu-id="bdd25-521">1740 - 175F</span></span>|`IsBuhid`|  
|<span data-ttu-id="bdd25-522">1760 ～ 177F</span><span class="sxs-lookup"><span data-stu-id="bdd25-522">1760 - 177F</span></span>|`IsTagbanwa`|  
|<span data-ttu-id="bdd25-523">1780 ～ 17FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-523">1780 - 17FF</span></span>|`IsKhmer`|  
|<span data-ttu-id="bdd25-524">1800 ～ 18AF</span><span class="sxs-lookup"><span data-stu-id="bdd25-524">1800 - 18AF</span></span>|`IsMongolian`|  
|<span data-ttu-id="bdd25-525">1900 ～ 194F</span><span class="sxs-lookup"><span data-stu-id="bdd25-525">1900 - 194F</span></span>|`IsLimbu`|  
|<span data-ttu-id="bdd25-526">1950 ～ 197F</span><span class="sxs-lookup"><span data-stu-id="bdd25-526">1950 - 197F</span></span>|`IsTaiLe`|  
|<span data-ttu-id="bdd25-527">19E0 ～ 19FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-527">19E0 - 19FF</span></span>|`IsKhmerSymbols`|  
|<span data-ttu-id="bdd25-528">1D00 ～ 1D7F</span><span class="sxs-lookup"><span data-stu-id="bdd25-528">1D00 - 1D7F</span></span>|`IsPhoneticExtensions`|  
|<span data-ttu-id="bdd25-529">1E00 ～ 1EFF</span><span class="sxs-lookup"><span data-stu-id="bdd25-529">1E00 - 1EFF</span></span>|`IsLatinExtendedAdditional`|  
|<span data-ttu-id="bdd25-530">1F00 ～ 1FFF</span><span class="sxs-lookup"><span data-stu-id="bdd25-530">1F00 - 1FFF</span></span>|`IsGreekExtended`|  
|<span data-ttu-id="bdd25-531">2000 ～ 206F</span><span class="sxs-lookup"><span data-stu-id="bdd25-531">2000 - 206F</span></span>|`IsGeneralPunctuation`|  
|<span data-ttu-id="bdd25-532">2070 ～ 209F</span><span class="sxs-lookup"><span data-stu-id="bdd25-532">2070 - 209F</span></span>|`IsSuperscriptsandSubscripts`|  
|<span data-ttu-id="bdd25-533">20A0 ～ 20CF</span><span class="sxs-lookup"><span data-stu-id="bdd25-533">20A0 - 20CF</span></span>|`IsCurrencySymbols`|  
|<span data-ttu-id="bdd25-534">20D0 ～ 20FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-534">20D0 - 20FF</span></span>|`IsCombiningDiacriticalMarksforSymbols`<br /><br /> <span data-ttu-id="bdd25-535">- または -</span><span class="sxs-lookup"><span data-stu-id="bdd25-535">-or-</span></span><br /><br /> `IsCombiningMarksforSymbols`|  
|<span data-ttu-id="bdd25-536">2100 ～ 214F</span><span class="sxs-lookup"><span data-stu-id="bdd25-536">2100 - 214F</span></span>|`IsLetterlikeSymbols`|  
|<span data-ttu-id="bdd25-537">2150 ～ 218F</span><span class="sxs-lookup"><span data-stu-id="bdd25-537">2150 - 218F</span></span>|`IsNumberForms`|  
|<span data-ttu-id="bdd25-538">2190 ～ 21FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-538">2190 - 21FF</span></span>|`IsArrows`|  
|<span data-ttu-id="bdd25-539">2200 ～ 22FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-539">2200 - 22FF</span></span>|`IsMathematicalOperators`|  
|<span data-ttu-id="bdd25-540">2300 ～ 23FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-540">2300 - 23FF</span></span>|`IsMiscellaneousTechnical`|  
|<span data-ttu-id="bdd25-541">2400 ～ 243F</span><span class="sxs-lookup"><span data-stu-id="bdd25-541">2400 - 243F</span></span>|`IsControlPictures`|  
|<span data-ttu-id="bdd25-542">2440 ～ 245F</span><span class="sxs-lookup"><span data-stu-id="bdd25-542">2440 - 245F</span></span>|`IsOpticalCharacterRecognition`|  
|<span data-ttu-id="bdd25-543">2460 ～ 24FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-543">2460 - 24FF</span></span>|`IsEnclosedAlphanumerics`|  
|<span data-ttu-id="bdd25-544">2500 ～ 257F</span><span class="sxs-lookup"><span data-stu-id="bdd25-544">2500 - 257F</span></span>|`IsBoxDrawing`|  
|<span data-ttu-id="bdd25-545">2580 ～ 259F</span><span class="sxs-lookup"><span data-stu-id="bdd25-545">2580 - 259F</span></span>|`IsBlockElements`|  
|<span data-ttu-id="bdd25-546">25A0 ～ 25FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-546">25A0 - 25FF</span></span>|`IsGeometricShapes`|  
|<span data-ttu-id="bdd25-547">2600 ～ 26FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-547">2600 - 26FF</span></span>|`IsMiscellaneousSymbols`|  
|<span data-ttu-id="bdd25-548">2700 ～ 27BF</span><span class="sxs-lookup"><span data-stu-id="bdd25-548">2700 - 27BF</span></span>|`IsDingbats`|  
|<span data-ttu-id="bdd25-549">27C0 ～ 27EF</span><span class="sxs-lookup"><span data-stu-id="bdd25-549">27C0 - 27EF</span></span>|`IsMiscellaneousMathematicalSymbols-A`|  
|<span data-ttu-id="bdd25-550">27F0 ～ 27FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-550">27F0 - 27FF</span></span>|`IsSupplementalArrows-A`|  
|<span data-ttu-id="bdd25-551">2800 ～ 28FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-551">2800 - 28FF</span></span>|`IsBraillePatterns`|  
|<span data-ttu-id="bdd25-552">2900 ～ 297F</span><span class="sxs-lookup"><span data-stu-id="bdd25-552">2900 - 297F</span></span>|`IsSupplementalArrows-B`|  
|<span data-ttu-id="bdd25-553">2980 ～ 29FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-553">2980 - 29FF</span></span>|`IsMiscellaneousMathematicalSymbols-B`|  
|<span data-ttu-id="bdd25-554">2A00 ～ 2AFF</span><span class="sxs-lookup"><span data-stu-id="bdd25-554">2A00 - 2AFF</span></span>|`IsSupplementalMathematicalOperators`|  
|<span data-ttu-id="bdd25-555">2B00 ～ 2BFF</span><span class="sxs-lookup"><span data-stu-id="bdd25-555">2B00 - 2BFF</span></span>|`IsMiscellaneousSymbolsandArrows`|  
|<span data-ttu-id="bdd25-556">2E80 ～ 2EFF</span><span class="sxs-lookup"><span data-stu-id="bdd25-556">2E80 - 2EFF</span></span>|`IsCJKRadicalsSupplement`|  
|<span data-ttu-id="bdd25-557">2F00 ～ 2FDF</span><span class="sxs-lookup"><span data-stu-id="bdd25-557">2F00 - 2FDF</span></span>|`IsKangxiRadicals`|  
|<span data-ttu-id="bdd25-558">2FF0 ～ 2FFF</span><span class="sxs-lookup"><span data-stu-id="bdd25-558">2FF0 - 2FFF</span></span>|`IsIdeographicDescriptionCharacters`|  
|<span data-ttu-id="bdd25-559">3000 ～ 303F</span><span class="sxs-lookup"><span data-stu-id="bdd25-559">3000 - 303F</span></span>|`IsCJKSymbolsandPunctuation`|  
|<span data-ttu-id="bdd25-560">3040 ～ 309F</span><span class="sxs-lookup"><span data-stu-id="bdd25-560">3040 - 309F</span></span>|`IsHiragana`|  
|<span data-ttu-id="bdd25-561">30A0 ～ 30FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-561">30A0 - 30FF</span></span>|`IsKatakana`|  
|<span data-ttu-id="bdd25-562">3100 ～ 312F</span><span class="sxs-lookup"><span data-stu-id="bdd25-562">3100 - 312F</span></span>|`IsBopomofo`|  
|<span data-ttu-id="bdd25-563">3130 ～ 318F</span><span class="sxs-lookup"><span data-stu-id="bdd25-563">3130 - 318F</span></span>|`IsHangulCompatibilityJamo`|  
|<span data-ttu-id="bdd25-564">3190 ～ 319F</span><span class="sxs-lookup"><span data-stu-id="bdd25-564">3190 - 319F</span></span>|`IsKanbun`|  
|<span data-ttu-id="bdd25-565">31A0 ～ 31BF</span><span class="sxs-lookup"><span data-stu-id="bdd25-565">31A0 - 31BF</span></span>|`IsBopomofoExtended`|  
|<span data-ttu-id="bdd25-566">31F0 ～ 31FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-566">31F0 - 31FF</span></span>|`IsKatakanaPhoneticExtensions`|  
|<span data-ttu-id="bdd25-567">3200 ～ 32FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-567">3200 - 32FF</span></span>|`IsEnclosedCJKLettersandMonths`|  
|<span data-ttu-id="bdd25-568">3300 ～ 33FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-568">3300 - 33FF</span></span>|`IsCJKCompatibility`|  
|<span data-ttu-id="bdd25-569">3400 ～ 4DBF</span><span class="sxs-lookup"><span data-stu-id="bdd25-569">3400 - 4DBF</span></span>|`IsCJKUnifiedIdeographsExtensionA`|  
|<span data-ttu-id="bdd25-570">4DC0 ～ 4DFF</span><span class="sxs-lookup"><span data-stu-id="bdd25-570">4DC0 - 4DFF</span></span>|`IsYijingHexagramSymbols`|  
|<span data-ttu-id="bdd25-571">4E00 ～ 9FFF</span><span class="sxs-lookup"><span data-stu-id="bdd25-571">4E00 - 9FFF</span></span>|`IsCJKUnifiedIdeographs`|  
|<span data-ttu-id="bdd25-572">A000 ～ A48F</span><span class="sxs-lookup"><span data-stu-id="bdd25-572">A000 - A48F</span></span>|`IsYiSyllables`|  
|<span data-ttu-id="bdd25-573">A490 ～ A4CF</span><span class="sxs-lookup"><span data-stu-id="bdd25-573">A490 - A4CF</span></span>|`IsYiRadicals`|  
|<span data-ttu-id="bdd25-574">AC00 ～ D7AF</span><span class="sxs-lookup"><span data-stu-id="bdd25-574">AC00 - D7AF</span></span>|`IsHangulSyllables`|  
|<span data-ttu-id="bdd25-575">D800 ～ DB7F</span><span class="sxs-lookup"><span data-stu-id="bdd25-575">D800 - DB7F</span></span>|`IsHighSurrogates`|  
|<span data-ttu-id="bdd25-576">DB80 ～ DBFF</span><span class="sxs-lookup"><span data-stu-id="bdd25-576">DB80 - DBFF</span></span>|`IsHighPrivateUseSurrogates`|  
|<span data-ttu-id="bdd25-577">DC00 ～ DFFF</span><span class="sxs-lookup"><span data-stu-id="bdd25-577">DC00 - DFFF</span></span>|`IsLowSurrogates`|  
|<span data-ttu-id="bdd25-578">E000 ～ F8FF</span><span class="sxs-lookup"><span data-stu-id="bdd25-578">E000 - F8FF</span></span>|<span data-ttu-id="bdd25-579">`IsPrivateUse` または `IsPrivateUseArea`</span><span class="sxs-lookup"><span data-stu-id="bdd25-579">`IsPrivateUse` or `IsPrivateUseArea`</span></span>|  
|<span data-ttu-id="bdd25-580">F900 ～ FAFF</span><span class="sxs-lookup"><span data-stu-id="bdd25-580">F900 - FAFF</span></span>|`IsCJKCompatibilityIdeographs`|  
|<span data-ttu-id="bdd25-581">FB00 ～ FB4F</span><span class="sxs-lookup"><span data-stu-id="bdd25-581">FB00 - FB4F</span></span>|`IsAlphabeticPresentationForms`|  
|<span data-ttu-id="bdd25-582">FB50 ～ FDFF</span><span class="sxs-lookup"><span data-stu-id="bdd25-582">FB50 - FDFF</span></span>|`IsArabicPresentationForms-A`|  
|<span data-ttu-id="bdd25-583">FE00 ～ FE0F</span><span class="sxs-lookup"><span data-stu-id="bdd25-583">FE00 - FE0F</span></span>|`IsVariationSelectors`|  
|<span data-ttu-id="bdd25-584">FE20 ～ FE2F</span><span class="sxs-lookup"><span data-stu-id="bdd25-584">FE20 - FE2F</span></span>|`IsCombiningHalfMarks`|  
|<span data-ttu-id="bdd25-585">FE30 ～ FE4F</span><span class="sxs-lookup"><span data-stu-id="bdd25-585">FE30 - FE4F</span></span>|`IsCJKCompatibilityForms`|  
|<span data-ttu-id="bdd25-586">FE50 ～ FE6F</span><span class="sxs-lookup"><span data-stu-id="bdd25-586">FE50 - FE6F</span></span>|`IsSmallFormVariants`|  
|<span data-ttu-id="bdd25-587">FE70 ～ FEFF</span><span class="sxs-lookup"><span data-stu-id="bdd25-587">FE70 - FEFF</span></span>|`IsArabicPresentationForms-B`|  
|<span data-ttu-id="bdd25-588">FF00 ～ FFEF</span><span class="sxs-lookup"><span data-stu-id="bdd25-588">FF00 - FFEF</span></span>|`IsHalfwidthandFullwidthForms`|  
|<span data-ttu-id="bdd25-589">FFF0 ～ FFFF</span><span class="sxs-lookup"><span data-stu-id="bdd25-589">FFF0 - FFFF</span></span>|`IsSpecials`|  
  
 [<span data-ttu-id="bdd25-590">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="bdd25-590">Back to Top</span></span>](#Top)  
  
<a name="CharacterClassSubtraction"></a>   
## <a name="character-class-subtraction-basegroup---excludedgroup"></a><span data-ttu-id="bdd25-591">文字クラスの減算: [base_group - [excluded_group]]</span><span class="sxs-lookup"><span data-stu-id="bdd25-591">Character Class Subtraction: [base_group - [excluded_group]]</span></span>  
 <span data-ttu-id="bdd25-592">文字クラスは、文字のセットを定義します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-592">A character class defines a set of characters.</span></span> <span data-ttu-id="bdd25-593">文字クラス減算によって、ある文字クラスから別の文字クラスの文字を除外した文字セットが生成されます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-593">Character class subtraction yields a set of characters that is the result of excluding the characters in one character class from another character class.</span></span>  
  
 <span data-ttu-id="bdd25-594">文字クラス減算式の形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bdd25-594">A character class subtraction expression has the following form:</span></span>  
  
 <span data-ttu-id="bdd25-595">`[` *base_group* `-[` *excluded_group* `]]`</span><span class="sxs-lookup"><span data-stu-id="bdd25-595">`[` *base_group* `-[` *excluded_group* `]]`</span></span>  
  
 <span data-ttu-id="bdd25-596">角かっこ (`[]`) とハイフン (`-`) は省略できません。</span><span class="sxs-lookup"><span data-stu-id="bdd25-596">The square brackets (`[]`) and hyphen (`-`) are mandatory.</span></span> <span data-ttu-id="bdd25-597">*base_group* は、[文字グループの肯定](#PositiveGroup)または[文字グループの否定](#NegativeGroup)です。</span><span class="sxs-lookup"><span data-stu-id="bdd25-597">The *base_group* is a [positive character group](#PositiveGroup) or a [negative character group](#NegativeGroup).</span></span> <span data-ttu-id="bdd25-598">*excluded_group* は、別の文字グループの肯定または文字グループの否定、あるいは別の文字クラス減算式です (つまり文字クラス減算式は入れ子にすることができます)。</span><span class="sxs-lookup"><span data-stu-id="bdd25-598">The *excluded_group* component is another positive or negative character group, or another character class subtraction expression (that is, you can nest character class subtraction expressions).</span></span>  
  
 <span data-ttu-id="bdd25-599">たとえば、"a" ～ "z" の文字範囲で構成される基本グループがあるとします。</span><span class="sxs-lookup"><span data-stu-id="bdd25-599">For example, suppose you have a base group that consists of the character range from "a" through "z".</span></span> <span data-ttu-id="bdd25-600">"m" を除外した基本グループで構成される文字のセットを定義するには、`[a-z-[m]]` を使用します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-600">To define the set of characters that consists of the base group except for the character "m", use `[a-z-[m]]`.</span></span> <span data-ttu-id="bdd25-601">"d"、"j" および "p" の文字を除外した基本グループで構成される文字のセットを定義するには、`[a-z-[djp]]` を使用します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-601">To define the set of characters that consists of the base group except for the set of characters "d", "j", and "p", use `[a-z-[djp]]`.</span></span> <span data-ttu-id="bdd25-602">"m" ～ "p" の文字範囲を除外した基本グループで構成される文字のセットを定義するには、`[a-z-[m-p]]` を使用します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-602">To define the set of characters that consists of the base group except for the character range from "m" through "p", use `[a-z-[m-p]]`.</span></span>  
  
 <span data-ttu-id="bdd25-603">入れ子になった文字クラス減算式 `[a-z-[d-w-[m-o]]]` について考えてみます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-603">Consider the nested character class subtraction expression, `[a-z-[d-w-[m-o]]]`.</span></span> <span data-ttu-id="bdd25-604">この式は、最も内部の文字範囲から順に外側へと評価されます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-604">The expression is evaluated from the innermost character range outward.</span></span> <span data-ttu-id="bdd25-605">まず、"m" ～ "o" の文字範囲が "d" ～ "w" の文字範囲から減算されて、"d" ～ "l" および "p" ～ "w" の文字セットが生成されます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-605">First, the character range from "m" through "o" is subtracted from the character range "d" through "w", which yields the set of characters from "d" through "l" and "p" through "w".</span></span> <span data-ttu-id="bdd25-606">さらにこのセットが "a" ～ "z" の文字範囲から減算されて、`[abcmnoxyz]` という文字セットが生成されます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-606">That set is then subtracted from the character range from "a" through "z", which yields the set of characters `[abcmnoxyz]`.</span></span>  
  
 <span data-ttu-id="bdd25-607">文字クラス減算では、任意の文字クラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="bdd25-607">You can use any character class with character class subtraction.</span></span> <span data-ttu-id="bdd25-608">\u0000 ～ \uFFFF の Unicode 文字から空白文字 (`\s`)、句読点一般カテゴリの文字 (`\p{P}`)、`IsGreek` 名前付きブロック内の文字 (`\p{IsGreek}`)、および Unicode NEXT LINE 制御文字 (\x85) を除いた文字のセットを定義するには、`[\u0000-\uFFFF-[\s\p{P}\p{IsGreek}\x85]]` を使用します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-608">To define the set of characters that consists of all Unicode characters from \u0000 through \uFFFF except white-space characters (`\s`), the characters in the punctuation general category (`\p{P}`), the characters in the `IsGreek` named block (`\p{IsGreek}`), and the Unicode NEXT LINE control character (\x85), use `[\u0000-\uFFFF-[\s\p{P}\p{IsGreek}\x85]]`.</span></span>  
  
 <span data-ttu-id="bdd25-609">有効な結果を生成する文字クラス減算式の文字クラスを選択します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-609">Choose character classes for a character class subtraction expression that will yield useful results.</span></span> <span data-ttu-id="bdd25-610">どの文字にも一致しない空の文字セットを生成する式、または元の基本グループと同じになる式は避けてください。</span><span class="sxs-lookup"><span data-stu-id="bdd25-610">Avoid an expression that yields an empty set of characters, which cannot match anything, or an expression that is equivalent to the original base group.</span></span> <span data-ttu-id="bdd25-611">たとえば、`[\p{IsBasicLatin}-[\x00-\x7F]]` という式は、`IsBasicLatin` 一般カテゴリから `IsBasicLatin` 文字範囲のすべての文字を減算して空のセットを生成します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-611">For example, the empty set is the result of the expression `[\p{IsBasicLatin}-[\x00-\x7F]]`, which subtracts all characters in the `IsBasicLatin` character range from the `IsBasicLatin` general category.</span></span> <span data-ttu-id="bdd25-612">同様に、`[a-z-[0-9]]` という式は元の基本グループと同じセットを生成します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-612">Similarly, the original base group is the result of the expression `[a-z-[0-9]]`.</span></span>  <span data-ttu-id="bdd25-613">これは、"a" ～ "z" の文字範囲である基本グループに、"0" ～ "9" という 10 進数字の文字範囲から成る除外対象グループ内の文字が含まれないためです。</span><span class="sxs-lookup"><span data-stu-id="bdd25-613">This is because the base group, which is the character range of letters from "a" through "z", does not contain any characters in the excluded group, which is the character range of decimal digits from "0" through "9".</span></span>  
  
 <span data-ttu-id="bdd25-614">入力文字列内の 0 および奇数と一致する正規表現 `^[0-9-[2468]]+$` を定義する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-614">The following example defines a regular expression, `^[0-9-[2468]]+$`, that matches zero and odd digits in an input string.</span></span>  <span data-ttu-id="bdd25-615">この正規表現の解釈を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-615">The regular expression is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="bdd25-616">要素</span><span class="sxs-lookup"><span data-stu-id="bdd25-616">Element</span></span>|<span data-ttu-id="bdd25-617">説明</span><span class="sxs-lookup"><span data-stu-id="bdd25-617">Description</span></span>|  
|-------------|-----------------|  
|^|<span data-ttu-id="bdd25-618">入力文字列の先頭から照合を開始します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-618">Begin the match at the start of the input string.</span></span>|  
|`[0-9-[2468]]+`|<span data-ttu-id="bdd25-619">2、4、6、および 8 を除く 0 ～ 9 の文字の 1 回以上の出現と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-619">Match one or more occurrences of any character from 0 to 9 except for 2, 4, 6, and 8.</span></span> <span data-ttu-id="bdd25-620">つまり、0 または奇数の 1 回以上の出現と一致します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-620">In other words, match one or more occurrences of zero or an odd digit.</span></span>|  
|$|<span data-ttu-id="bdd25-621">入力文字列の末尾で照合を終了します。</span><span class="sxs-lookup"><span data-stu-id="bdd25-621">End the match at the end of the input string.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/classsubtraction1.cs#15)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/classsubtraction1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="bdd25-622">参照</span><span class="sxs-lookup"><span data-stu-id="bdd25-622">See Also</span></span>  
 <xref:System.Char.GetUnicodeCategory%2A>  
 [<span data-ttu-id="bdd25-623">正規表現言語 - クイック リファレンス</span><span class="sxs-lookup"><span data-stu-id="bdd25-623">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 [<span data-ttu-id="bdd25-624">正規表現のオプション</span><span class="sxs-lookup"><span data-stu-id="bdd25-624">Regular Expression Options</span></span>](../../../docs/standard/base-types/regular-expression-options.md)
