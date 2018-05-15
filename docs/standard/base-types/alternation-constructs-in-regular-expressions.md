---
title: 正規表現での代替構成体
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- either/or matching
- alternative matching patterns
- regular expressions, alternation constructs
- alternation constructs
- optional matching patterns
- constructs, alternation
- .NET Framework regular expressions, alternation constructs
ms.assetid: 071e22e9-fbb0-4ecf-add1-8d2424f9f2d1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 956d16b47fb31549de8f25c513d73c43ab41c267
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="alternation-constructs-in-regular-expressions"></a><span data-ttu-id="c4b16-102">正規表現での代替構成体</span><span class="sxs-lookup"><span data-stu-id="c4b16-102">Alternation Constructs in Regular Expressions</span></span>
<a name="top"></a> <span data-ttu-id="c4b16-103">代替構成体は、択一条件または条件一致を有効にするように正規表現を変更します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-103">Alternation constructs modify a regular expression to enable either/or or conditional matching.</span></span> <span data-ttu-id="c4b16-104">.NET では、次の 3 つの代替構成体がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c4b16-104">.NET supports three alternation constructs:</span></span>  
  
-   [<span data-ttu-id="c4b16-105">&#124; を使用したパターン マッチング</span><span class="sxs-lookup"><span data-stu-id="c4b16-105">Pattern matching with &#124;</span></span>](#Either_Or)  
  
-   [<span data-ttu-id="c4b16-106">(?(expression)yes&#124;no) を使用した条件一致</span><span class="sxs-lookup"><span data-stu-id="c4b16-106">Conditional matching with (?(expression)yes&#124;no)</span></span>](#Conditional_Expr)  
  
-   [<span data-ttu-id="c4b16-107">有効なキャプチャ グループに基づく条件一致</span><span class="sxs-lookup"><span data-stu-id="c4b16-107">Conditional matching based on a valid captured group</span></span>](#Conditional_Group)  
  
<a name="Either_Or"></a>   
## <a name="pattern-matching-with-124"></a><span data-ttu-id="c4b16-108">&#124; を使用したパターン マッチング</span><span class="sxs-lookup"><span data-stu-id="c4b16-108">Pattern Matching with &#124;</span></span>  
 <span data-ttu-id="c4b16-109">縦棒 (`|`) 文字を使って、`|` 文字で各パターンを区切った一連のパターンのいずれかと照合できます。</span><span class="sxs-lookup"><span data-stu-id="c4b16-109">You can use the vertical bar (`|`) character to match any one of a series of patterns, where the `|` character separates each pattern.</span></span>  
  
 <span data-ttu-id="c4b16-110">肯定的文字クラスと同じように、 `|` 文字を使うと、複数の文字のいずれか 1 文字と照合できます。</span><span class="sxs-lookup"><span data-stu-id="c4b16-110">Like the positive character class, the `|` character can be used to match any one of a number of single characters.</span></span> <span data-ttu-id="c4b16-111">次の例は、肯定的文字クラスと `|` 文字との択一パターン マッチを使って、文字列から単語 "gray"や "grey" を検索します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-111">The following example uses both a positive character class and either/or pattern matching with the `|` character to locate occurrences of the words "gray" or "grey" in a string.</span></span> <span data-ttu-id="c4b16-112">この場合、 `|` 文字を使うと、より詳細な正規表現が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c4b16-112">In this case, the `|` character produces a regular expression that is more verbose.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
 [!code-vb[RegularExpressions.Language.Alternation#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]  
  
 <span data-ttu-id="c4b16-113">`|` 文字を使う正規表現 `\bgr(a|e)y\b`の解釈を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-113">The regular expression that uses the `|` character, `\bgr(a|e)y\b`, is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="c4b16-114">パターン</span><span class="sxs-lookup"><span data-stu-id="c4b16-114">Pattern</span></span>|<span data-ttu-id="c4b16-115">説明</span><span class="sxs-lookup"><span data-stu-id="c4b16-115">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="c4b16-116">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-116">Start at a word boundary.</span></span>|  
|`gr`|<span data-ttu-id="c4b16-117">文字 "gr" と一致します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-117">Match the characters "gr".</span></span>|  
|<code>(a&#124;e)</code>|<span data-ttu-id="c4b16-118">"a" または "e" と一致します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-118">Match either an "a" or an "e".</span></span>|  
|`y\b`|<span data-ttu-id="c4b16-119">ワード境界にある "y" と一致します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-119">Match a "y" on a word boundary.</span></span>|  
  
 <span data-ttu-id="c4b16-120">また、`|` 文字を使って、複数の文字や部分式との択一照合を実行できます。これは、文字リテラルと正規表現言語要素を自由に組み合わせて使うことができます </span><span class="sxs-lookup"><span data-stu-id="c4b16-120">The `|` character can also be used to perform an either/or match with multiple characters or subexpressions, which can include any combination of character literals and regular expression language elements.</span></span> <span data-ttu-id="c4b16-121">(文字クラスにこの機能はありません)。次の例では、`|` 文字を使って、米国の社会保障番号 (SSN) (*ddd*-*dd*-*dddd* という形式の 9 桁の数字)、または米国の雇用者番号 (EIN) (*dd*-*ddddddd* という形式の 9 桁の数字) のいずれかを抽出します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-121">(The character class does not provide this functionality.) The following example uses the `|` character to extract either a U.S. Social Security Number (SSN), which is a 9-digit number with the format *ddd*-*dd*-*dddd*, or a U.S. Employer Identification Number (EIN), which is a 9-digit number with the format *dd*-*ddddddd*.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
 [!code-vb[RegularExpressions.Language.Alternation#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  
  
 <span data-ttu-id="c4b16-122">この正規表現 `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` の解釈を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-122">The regular expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="c4b16-123">パターン</span><span class="sxs-lookup"><span data-stu-id="c4b16-123">Pattern</span></span>|<span data-ttu-id="c4b16-124">説明</span><span class="sxs-lookup"><span data-stu-id="c4b16-124">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="c4b16-125">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-125">Start at a word boundary.</span></span>|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|<span data-ttu-id="c4b16-126">「2 桁と 7 桁の 10 進数がハイフンでつながれた文字列」または「3 桁、2 桁、4 桁の 10 進数がそれぞれハイフンでつながれた文字列」のいずれかと一致します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-126">Match either of the following: two decimal digits followed by a hyphen followed by seven decimal digits; or three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\d`|<span data-ttu-id="c4b16-127">ワード境界で照合を終了します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-127">End the match at a word boundary.</span></span>|  
  
 [<span data-ttu-id="c4b16-128">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="c4b16-128">Back to top</span></span>](#top)  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a><span data-ttu-id="c4b16-129">式を使用した条件一致</span><span class="sxs-lookup"><span data-stu-id="c4b16-129">Conditional Matching with an Expression</span></span>  
 <span data-ttu-id="c4b16-130">この言語要素では、最初のパターンに一致するかどうかに応じて、2 つのパターンのいずれかの照合を実行します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-130">This language element attempts to match one of two patterns depending on whether it can match an initial pattern.</span></span> <span data-ttu-id="c4b16-131">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c4b16-131">Its syntax is:</span></span>  
  
 <span data-ttu-id="c4b16-132">`(?(` *expression* `)` *yes* `|` *no* `)`</span><span class="sxs-lookup"><span data-stu-id="c4b16-132">`(?(` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="c4b16-133">ここで、 *expression* は照合する最初のパターン、 *yes* は *expression* が一致した場合に照合するパターン、 *no* は *expression* が一致しなかった場合に照合するパターン (省略可能) です。</span><span class="sxs-lookup"><span data-stu-id="c4b16-133">where *expression* is the initial pattern to match, *yes* is the pattern to match if *expression* is matched, and *no* is the optional pattern to match if *expression* is not matched.</span></span> <span data-ttu-id="c4b16-134">*expression* は正規表現エンジンによってゼロ幅アサーションとして処理されるので、 *expression*が評価された後、正規表現エンジンによる入力ストリーム内の評価位置は前に進みません。</span><span class="sxs-lookup"><span data-stu-id="c4b16-134">The regular expression engine treats *expression* as a zero-width assertion; that is, the regular expression engine does not advance in the input stream after it evaluates *expression*.</span></span> <span data-ttu-id="c4b16-135">そのため、この構成体は次の構成体と同じです。</span><span class="sxs-lookup"><span data-stu-id="c4b16-135">Therefore, this construct is equivalent to the following:</span></span>  
  
 <span data-ttu-id="c4b16-136">`(?(?=` *式* `)` *可* `|` *no* `)`</span><span class="sxs-lookup"><span data-stu-id="c4b16-136">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="c4b16-137">ここで、`(?=`*expression*`)` はゼロ幅アサーションの構成体として解釈されます </span><span class="sxs-lookup"><span data-stu-id="c4b16-137">where `(?=`*expression*`)` is a zero-width assertion construct.</span></span> <span data-ttu-id="c4b16-138">(詳しくは、「[正規表現でのグループ化構成体](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)」をご覧ください)。正規表現エンジンによって *expression* はアンカー (ゼロ幅アサーション) として解釈されるので、*expression* は、ゼロ幅アサーション (詳しくは「[正規表現のアンカー](../../../docs/standard/base-types/anchors-in-regular-expressions.md)」を参照) か、*yes* にも含まれている部分式のいずれかである必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4b16-138">(For more information, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Because the regular expression engine interprets *expression* as an anchor (a zero-width assertion), *expression* must either be a zero-width assertion (for more information, see [Anchors](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) or a subexpression that is also contained in *yes*.</span></span> <span data-ttu-id="c4b16-139">それ以外の場合、*yes* パターンには一致しません。</span><span class="sxs-lookup"><span data-stu-id="c4b16-139">Otherwise, the *yes* pattern cannot be matched.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4b16-140">*expression*が名前付きキャプチャ グループや番号付きキャプチャ グループである場合、代替構成体はキャプチャ テストとして解釈されます。詳しくは、次のセクション「 [有効なキャプチャ グループに基づく条件一致](#Conditional_Group)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c4b16-140">If *expression*is a named or numbered capturing group, the alternation construct is interpreted as a capture test; for more information, see the next section, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span></span> <span data-ttu-id="c4b16-141">つまり、正規表現エンジンは、キャプチャした部分文字列を照合しようとはせず、代わりにグループが存在するかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="c4b16-141">In other words, the regular expression engine does not attempt to match the captured substring, but instead tests for the presence or absence of the group.</span></span>  
  
 <span data-ttu-id="c4b16-142">次の例は、前の「[&#124; を使用したパターン マッチング](#Either_Or)」セクションで説明した例を少し変更したものです。</span><span class="sxs-lookup"><span data-stu-id="c4b16-142">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="c4b16-143">条件一致を使用して、ワード境界の後の最初の 3 文字が「2 桁の数字の後にハイフン」であるかどうかを判定します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-143">It uses conditional matching to determine whether the first three characters after a word boundary are two digits followed by a hyphen.</span></span> <span data-ttu-id="c4b16-144">一致した場合は、米国の雇用者番号 (EIN) との照合を試みます。</span><span class="sxs-lookup"><span data-stu-id="c4b16-144">If they are, it attempts to match a U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="c4b16-145">一致しない場合は、米国の社会保険番号 (SSN) との照合を試みます。</span><span class="sxs-lookup"><span data-stu-id="c4b16-145">If not, it attempts to match a U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
 [!code-vb[RegularExpressions.Language.Alternation#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]  
  
 <span data-ttu-id="c4b16-146">この正規表現パターン `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` の解釈を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-146">The regular expression pattern `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="c4b16-147">パターン</span><span class="sxs-lookup"><span data-stu-id="c4b16-147">Pattern</span></span>|<span data-ttu-id="c4b16-148">説明</span><span class="sxs-lookup"><span data-stu-id="c4b16-148">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="c4b16-149">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-149">Start at a word boundary.</span></span>|  
|`(?(\d{2}-)`|<span data-ttu-id="c4b16-150">次の 3 文字が「2 桁の数字の後にハイフン」で構成されているかどうかを判定します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-150">Determine whether the next three characters consist of two digits followed by a hyphen.</span></span>|  
|`\d{2}-\d{7}`|<span data-ttu-id="c4b16-151">前のパターンに一致する場合は、「2 桁の数字の後にハイフン、その後に 7 桁の数字」を照合します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-151">If the previous pattern matches, match two digits followed by a hyphen followed by seven digits.</span></span>|  
|`\d{3}-\d{2}-\d{4}`|<span data-ttu-id="c4b16-152">前のパターンに一致しない場合は、「3 桁の 10 進数、ハイフン、2 桁の 10 進数、もう 1 つのハイフン、および 4 桁の 10 進数」を照合します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-152">If the previous pattern does not match, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="c4b16-153">ワード境界に一致します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-153">Match a word boundary.</span></span>|  
  
 [<span data-ttu-id="c4b16-154">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="c4b16-154">Back to top</span></span>](#top)  
  
<a name="Conditional_Group"></a>   
## <a name="conditional-matching-based-on-a-valid-captured-group"></a><span data-ttu-id="c4b16-155">有効なキャプチャ グループに基づく条件一致</span><span class="sxs-lookup"><span data-stu-id="c4b16-155">Conditional Matching Based on a Valid Captured Group</span></span>  
 <span data-ttu-id="c4b16-156">この言語要素では、指定されたキャプチャ グループに一致するかどうかに応じて、2 つのパターンのいずれかを照合します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-156">This language element attempts to match one of two patterns depending on whether it has matched a specified capturing group.</span></span> <span data-ttu-id="c4b16-157">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c4b16-157">Its syntax is:</span></span>  
  
 <span data-ttu-id="c4b16-158">`(?(` *name* `)` *可* `|` *no* `)`</span><span class="sxs-lookup"><span data-stu-id="c4b16-158">`(?(` *name* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="c4b16-159">または</span><span class="sxs-lookup"><span data-stu-id="c4b16-159">or</span></span>  
  
 <span data-ttu-id="c4b16-160">`(?(` *number* `)` *可* `|` *no* `)`</span><span class="sxs-lookup"><span data-stu-id="c4b16-160">`(?(` *number* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="c4b16-161">ここで、 *name* はキャプチャ グループの名前、 *number* はキャプチャ グループの番号です。 *yes* は、 *name* または *number* が一致する場合に照合する式です。 *no* き、一致しない場合に照合する式 (省略可能) です。</span><span class="sxs-lookup"><span data-stu-id="c4b16-161">where *name* is the name and *number* is the number of a capturing group, *yes* is the expression to match if *name* or *number* has a match, and *no* is the optional expression to match if it does not.</span></span>  
  
 <span data-ttu-id="c4b16-162">*name* が正規表現パターンで使用されているキャプチャ グループの名前に一致しない場合、その代替構成体は式のテスト (前のセクションで説明したもの) として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="c4b16-162">If *name* does not correspond to the name of a capturing group that is used in the regular expression pattern, the alternation construct is interpreted as an expression test, as explained in the previous section.</span></span> <span data-ttu-id="c4b16-163">通常、これは *expression* が `false`に評価されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-163">Typically, this means that *expression* evaluates to `false`.</span></span> <span data-ttu-id="c4b16-164">*number* が正規表現パターンで使用されている番号付きキャプチャ グループに対応しない場合は、正規表現エンジンが <xref:System.ArgumentException>をスローします。</span><span class="sxs-lookup"><span data-stu-id="c4b16-164">If *number* does not correspond to a numbered capturing group that is used in the regular expression pattern, the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="c4b16-165">次の例は、前の「[&#124; を使用したパターン マッチング](#Either_Or)」セクションで説明した例を少し変更したものです。</span><span class="sxs-lookup"><span data-stu-id="c4b16-165">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="c4b16-166">「2 桁の数字の後にハイフン」で構成される `n2` という名前付きキャプチャ グループを使用しています。</span><span class="sxs-lookup"><span data-stu-id="c4b16-166">It uses a capturing group named `n2` that consists of two digits followed by a hyphen.</span></span> <span data-ttu-id="c4b16-167">代替構成体により、このキャプチャ グループが入力文字列に一致したかどうかテストされます。</span><span class="sxs-lookup"><span data-stu-id="c4b16-167">The alternation construct tests whether this capturing group has been matched in the input string.</span></span> <span data-ttu-id="c4b16-168">一致した場合は、場合に、米国の 9 桁の雇用者番号 (EIN) との照合を試みます。</span><span class="sxs-lookup"><span data-stu-id="c4b16-168">If it has, the alternation construct attempts to match the last seven digits of a nine-digit U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="c4b16-169">一致しなかった場合は、米国の 9 桁の社会保険番号 (SSN) との照合を試みます。</span><span class="sxs-lookup"><span data-stu-id="c4b16-169">If it has not, it attempts to match a nine-digit U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
 [!code-vb[RegularExpressions.Language.Alternation#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]  
  
 <span data-ttu-id="c4b16-170">この正規表現パターン `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` の解釈を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-170">The regular expression pattern `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="c4b16-171">パターン</span><span class="sxs-lookup"><span data-stu-id="c4b16-171">Pattern</span></span>|<span data-ttu-id="c4b16-172">説明</span><span class="sxs-lookup"><span data-stu-id="c4b16-172">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="c4b16-173">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-173">Start at a word boundary.</span></span>|  
|`(?<n2>\d{2}-)?`|<span data-ttu-id="c4b16-174">「2 桁の数字の後にハイフン」の 0 個または 1 個の出現と照合します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-174">Match zero or one occurrence of two digits followed by a hyphen.</span></span> <span data-ttu-id="c4b16-175">このキャプチャ グループに `n2`という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="c4b16-175">Name this capturing group `n2`.</span></span>|  
|`(?(n2)`|<span data-ttu-id="c4b16-176">`n2` への一致が入力文字列内に見つかるかどうかテストします。</span><span class="sxs-lookup"><span data-stu-id="c4b16-176">Test whether `n2` was matched in the input string.</span></span>|  
|`)\d{7}`|<span data-ttu-id="c4b16-177">`n2` が一致した場合は、7 桁の 10 進数を照合します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-177">If `n2` was matched, match seven decimal digits.</span></span>|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|<span data-ttu-id="c4b16-178">`n2` が一致しなかった場合は、「3 桁の 10 進数、ハイフン、2 桁の 10 進数、もう 1 つのハイフン、および 4 桁の 10 進数」を照合します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-178">If `n2` was not matched, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="c4b16-179">ワード境界に一致します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-179">Match a word boundary.</span></span>|  
  
 <span data-ttu-id="c4b16-180">この例を少し変更して、名前付きグループではなく番号付きグループを使用する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c4b16-180">A variation of this example that uses a numbered group instead of a named group is shown in the following example.</span></span> <span data-ttu-id="c4b16-181">正規表現パターンは `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b` です。</span><span class="sxs-lookup"><span data-stu-id="c4b16-181">Its regular expression pattern is `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
 [!code-vb[RegularExpressions.Language.Alternation#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="c4b16-182">参照</span><span class="sxs-lookup"><span data-stu-id="c4b16-182">See Also</span></span>  
 [<span data-ttu-id="c4b16-183">正規表現言語 - クイック リファレンス</span><span class="sxs-lookup"><span data-stu-id="c4b16-183">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
