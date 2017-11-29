---
title: "Like 演算子 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- Like
- vb.Like
helpviewer_keywords:
- similar to
- pattern matching
- Like operator [Visual Basic]
- '? symbol, wildcard character'
- string comparison [Visual Basic], Like operator
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- symbols, wildcard
- wildcards, Like operator
- strings [Visual Basic], matching
- string comparison [Visual Basic], sorting data
- data [Visual Basic], sorting
- text [Visual Basic], comparing
- operators [Visual Basic], pattern-matching
- data [Visual Basic], string comparisons
- string comparison [Visual Basic], Like operators
ms.assetid: 966283ec-80e2-4294-baa8-c75baff804f9
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ad5729515362bfd52b0c3b401f218a49f569726e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="like-operator-visual-basic"></a><span data-ttu-id="44757-102">Like 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44757-102">Like Operator (Visual Basic)</span></span>
<span data-ttu-id="44757-103">文字列をパターンと比較します。</span><span class="sxs-lookup"><span data-stu-id="44757-103">Compares a string against a pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44757-104">構文</span><span class="sxs-lookup"><span data-stu-id="44757-104">Syntax</span></span>  
  
```  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="44757-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="44757-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="44757-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="44757-106">Required.</span></span> <span data-ttu-id="44757-107">どの`Boolean`変数。</span><span class="sxs-lookup"><span data-stu-id="44757-107">Any `Boolean` variable.</span></span> <span data-ttu-id="44757-108">結果は、`Boolean`を示す値かどうか、`string`満たす、`pattern`です。</span><span class="sxs-lookup"><span data-stu-id="44757-108">The result is a `Boolean` value indicating whether or not the `string` satisfies the `pattern`.</span></span>  
  
 `string`  
 <span data-ttu-id="44757-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="44757-109">Required.</span></span> <span data-ttu-id="44757-110">任意のブール型 (`String`) の式を指定します。</span><span class="sxs-lookup"><span data-stu-id="44757-110">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="44757-111">必須です。</span><span class="sxs-lookup"><span data-stu-id="44757-111">Required.</span></span> <span data-ttu-id="44757-112">どの`String`「解説」で説明したパターン マッチの規則に適合させる式</span><span class="sxs-lookup"><span data-stu-id="44757-112">Any `String` expression conforming to the pattern-matching conventions described in "Remarks."</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44757-113">コメント</span><span class="sxs-lookup"><span data-stu-id="44757-113">Remarks</span></span>  
 <span data-ttu-id="44757-114">場合の値`string`に含まれているパターンを満たす`pattern`、`result`は`True`します。</span><span class="sxs-lookup"><span data-stu-id="44757-114">If the value in `string` satisfies the pattern contained in `pattern`, `result` is `True`.</span></span> <span data-ttu-id="44757-115">文字列は、パターンが満たされない場合`result`は`False`します。</span><span class="sxs-lookup"><span data-stu-id="44757-115">If the string does not satisfy the pattern, `result` is `False`.</span></span> <span data-ttu-id="44757-116">両方`string`と`pattern`空の文字列は、結果は`True`します。</span><span class="sxs-lookup"><span data-stu-id="44757-116">If both `string` and `pattern` are empty strings, the result is `True`.</span></span>  
  
## <a name="comparison-method"></a><span data-ttu-id="44757-117">比較メソッド</span><span class="sxs-lookup"><span data-stu-id="44757-117">Comparison Method</span></span>  
 <span data-ttu-id="44757-118">動作、`Like`演算子によって異なります、 [Option Compare ステートメント](../../../visual-basic/language-reference/statements/option-compare-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="44757-118">The behavior of the `Like` operator depends on the [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span> <span data-ttu-id="44757-119">各ソース ファイルの既定の文字列比較メソッドが`Option Compare Binary`です。</span><span class="sxs-lookup"><span data-stu-id="44757-119">The default string comparison method for each source file is `Option Compare Binary`.</span></span>  
  
## <a name="pattern-options"></a><span data-ttu-id="44757-120">パターンのオプション</span><span class="sxs-lookup"><span data-stu-id="44757-120">Pattern Options</span></span>  
 <span data-ttu-id="44757-121">組み込みのパターンに一致する文字列比較のための多機能なツールを提供します。</span><span class="sxs-lookup"><span data-stu-id="44757-121">Built-in pattern matching provides a versatile tool for string comparisons.</span></span> <span data-ttu-id="44757-122">内の各文字に一致することは、パターン マッチング機能`string`に対して特定の文字やワイルドカード文字、文字一覧は、文字の範囲です。</span><span class="sxs-lookup"><span data-stu-id="44757-122">The pattern-matching features allow you to match each character in `string` against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="44757-123">次の表で使用できる文字`pattern`一致したとします。</span><span class="sxs-lookup"><span data-stu-id="44757-123">The following table shows the characters allowed in `pattern` and what they match.</span></span>  
  
|<span data-ttu-id="44757-124">内の文字`pattern`</span><span class="sxs-lookup"><span data-stu-id="44757-124">Characters in `pattern`</span></span>|<span data-ttu-id="44757-125">内の一致`string`</span><span class="sxs-lookup"><span data-stu-id="44757-125">Matches in `string`</span></span>|  
|-----------------------------|-------------------------|  
|`?`|<span data-ttu-id="44757-126">任意の 1 文字</span><span class="sxs-lookup"><span data-stu-id="44757-126">Any single character</span></span>|  
|`*`|<span data-ttu-id="44757-127">0 個以上の文字</span><span class="sxs-lookup"><span data-stu-id="44757-127">Zero or more characters</span></span>|  
|`#`|<span data-ttu-id="44757-128">任意の 1 つの数字 (0 ~ 9)</span><span class="sxs-lookup"><span data-stu-id="44757-128">Any single digit (0–9)</span></span>|  
|`[charlist]`|<span data-ttu-id="44757-129">内の任意の 1 文字`charlist`</span><span class="sxs-lookup"><span data-stu-id="44757-129">Any single character in `charlist`</span></span>|  
|`[!charlist]`|<span data-ttu-id="44757-130">内にない任意の 1 文字`charlist`</span><span class="sxs-lookup"><span data-stu-id="44757-130">Any single character not in `charlist`</span></span>|  
  
## <a name="character-lists"></a><span data-ttu-id="44757-131">文字の一覧</span><span class="sxs-lookup"><span data-stu-id="44757-131">Character Lists</span></span>  
 <span data-ttu-id="44757-132">1 つ以上の文字グループ (`charlist`) 角かっこで囲む (`[ ]`) 任意の 1 文字に一致に使用できる`string`桁の数字を含む、ほぼすべての文字コードを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="44757-132">A group of one or more characters (`charlist`) enclosed in brackets (`[ ]`) can be used to match any single character in `string` and can include almost any character code, including digits.</span></span>  
  
 <span data-ttu-id="44757-133">感嘆符 (`!`) の先頭に`charlist`内の文字を除く任意の文字の場合、一致が行われたことを意味`charlist`で見つかった`string`です。</span><span class="sxs-lookup"><span data-stu-id="44757-133">An exclamation point (`!`) at the beginning of `charlist` means that a match is made if any character except the characters in `charlist` is found in `string`.</span></span> <span data-ttu-id="44757-134">使用すると、角かっこの外側、感嘆符文字自体と一致します。</span><span class="sxs-lookup"><span data-stu-id="44757-134">When used outside brackets, the exclamation point matches itself.</span></span>  
  
## <a name="special-characters"></a><span data-ttu-id="44757-135">特殊文字</span><span class="sxs-lookup"><span data-stu-id="44757-135">Special Characters</span></span>  
 <span data-ttu-id="44757-136">特殊文字の左角かっこの一致するように (`[`)、疑問符 (?) (`?`)、番号記号 (`#`)、およびアスタリスク (`*`)、角かっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="44757-136">To match the special characters left bracket (`[`), question mark (`?`), number sign (`#`), and asterisk (`*`), enclose them in brackets.</span></span> <span data-ttu-id="44757-137">右の角かっこ (`]`) 自体を一致するように、グループ内で使用できませんが、グループの外側で個々 の文字として使用することができます。</span><span class="sxs-lookup"><span data-stu-id="44757-137">The right bracket (`]`) cannot be used within a group to match itself, but it can be used outside a group as an individual character.</span></span>  
  
 <span data-ttu-id="44757-138">文字シーケンス`[]`は長さ 0 の文字列と見なされます (`""`)。</span><span class="sxs-lookup"><span data-stu-id="44757-138">The character sequence `[]` is considered a zero-length string (`""`).</span></span> <span data-ttu-id="44757-139">ただし、角かっこで囲まれた文字の一覧の一部にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="44757-139">However, it cannot be part of a character list enclosed in brackets.</span></span> <span data-ttu-id="44757-140">内の位置かどうかを確認する場合`string`1 つを使用できる文字または文字のグループの`Like`2 回クリックします。</span><span class="sxs-lookup"><span data-stu-id="44757-140">If you want to check whether a position in `string` contains one of a group of characters or no character at all, you can use `Like` twice.</span></span> <span data-ttu-id="44757-141">例については、次を参照してください。[する方法: 文字列をパターンに一致](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)です。</span><span class="sxs-lookup"><span data-stu-id="44757-141">For an example, see [How to: Match a String against a Pattern](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span></span>  
  
## <a name="character-ranges"></a><span data-ttu-id="44757-142">文字範囲</span><span class="sxs-lookup"><span data-stu-id="44757-142">Character Ranges</span></span>  
 <span data-ttu-id="44757-143">ハイフンを使用して (`–`) 下と、範囲の上限を分離する`charlist`文字の範囲を指定できます。</span><span class="sxs-lookup"><span data-stu-id="44757-143">By using a hyphen (`–`) to separate the lower and upper bounds of the range, `charlist` can specify a range of characters.</span></span> <span data-ttu-id="44757-144">たとえば、`[A–Z]`場合は、対応する文字の位置で一致する結果`string`範囲内で任意の文字が含まれています`A`–`Z`、および`[!H–L]`結果と一致する場合は、対応する文字の位置範囲外の任意の文字を含む`H`–`L`です。</span><span class="sxs-lookup"><span data-stu-id="44757-144">For example, `[A–Z]` results in a match if the corresponding character position in `string` contains any character within the range `A`–`Z`, and `[!H–L]` results in a match if the corresponding character position contains any character outside the range `H`–`L`.</span></span>  
  
 <span data-ttu-id="44757-145">文字の範囲を指定する場合は、昇順で並べ替え、つまり、昇順に表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="44757-145">When you specify a range of characters, they must appear in ascending sort order, that is, from lowest to highest.</span></span> <span data-ttu-id="44757-146">したがって、`[A–Z]`は有効なパターンが`[Z–A]`はありません。</span><span class="sxs-lookup"><span data-stu-id="44757-146">Thus, `[A–Z]` is a valid pattern, but `[Z–A]` is not.</span></span>  
  
### <a name="multiple-character-ranges"></a><span data-ttu-id="44757-147">複数の文字範囲</span><span class="sxs-lookup"><span data-stu-id="44757-147">Multiple Character Ranges</span></span>  
 <span data-ttu-id="44757-148">同じ文字の位置の複数の範囲を指定するには、区切り記号は任意の同じ角かっこ内でそれらを配置します。</span><span class="sxs-lookup"><span data-stu-id="44757-148">To specify multiple ranges for the same character position, put them within the same brackets without delimiters.</span></span> <span data-ttu-id="44757-149">たとえば、`[A–CX–Z]`場合は、対応する文字の位置で一致する結果`string`、いずれかの範囲内の任意の文字が含まれています`A`–`C`または範囲`X`–`Z`です。</span><span class="sxs-lookup"><span data-stu-id="44757-149">For example, `[A–CX–Z]` results in a match if the corresponding character position in `string` contains any character within either the range `A`–`C` or the range `X`–`Z`.</span></span>  
  
### <a name="usage-of-the-hyphen"></a><span data-ttu-id="44757-150">ハイフンの使用</span><span class="sxs-lookup"><span data-stu-id="44757-150">Usage of the Hyphen</span></span>  
 <span data-ttu-id="44757-151">ハイフン (`–`) が先頭 (感嘆符、存在する場合)、またはの最後に表示される`charlist`自体を一致するようにします。</span><span class="sxs-lookup"><span data-stu-id="44757-151">A hyphen (`–`) can appear either at the beginning (after an exclamation point, if any) or at the end of `charlist` to match itself.</span></span> <span data-ttu-id="44757-152">その他の任意の場所では、ハイフンはハイフンの両側の文字が区切り文字の範囲を識別します。</span><span class="sxs-lookup"><span data-stu-id="44757-152">In any other location, the hyphen identifies a range of characters delimited by the characters on either side of the hyphen.</span></span>  
  
## <a name="collating-sequence"></a><span data-ttu-id="44757-153">照合順序</span><span class="sxs-lookup"><span data-stu-id="44757-153">Collating Sequence</span></span>  
 <span data-ttu-id="44757-154">指定された範囲の意味は、文字によって決定される、実行時に順序によって異なります。`Option``Compare`システムのロケール設定で、コードが実行されているとします。</span><span class="sxs-lookup"><span data-stu-id="44757-154">The meaning of a specified range depends on the character ordering at run time, as determined by `Option``Compare` and the locale setting of the system the code is running on.</span></span> <span data-ttu-id="44757-155">`Option``Compare``Binary`、範囲`[A–E]`と一致する`A`、 `B`、 `C`、 `D`、および`E`です。</span><span class="sxs-lookup"><span data-stu-id="44757-155">With `Option``Compare``Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.</span></span> <span data-ttu-id="44757-156">`Option``Compare``Text`、`[A–E]`と一致する`A`、 `a`、 `À`、 `à`、 `B`、 `b`、 `C`、 `c`、 `D`、 `d`、 `E`、および`e`です。</span><span class="sxs-lookup"><span data-stu-id="44757-156">With `Option``Compare``Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.</span></span> <span data-ttu-id="44757-157">範囲と一致しません`Ê`または`ê`アクセント記号付き文字が並べ替え順序でアクセントのない文字の後に照合します。</span><span class="sxs-lookup"><span data-stu-id="44757-157">The range does not match `Ê` or `ê` because accented characters collate after unaccented characters in the sort order.</span></span>  
  
## <a name="digraph-characters"></a><span data-ttu-id="44757-158">Digraph 文字</span><span class="sxs-lookup"><span data-stu-id="44757-158">Digraph Characters</span></span>  
 <span data-ttu-id="44757-159">一部の言語では、2 つの文字を表すアルファベットの文字があります。</span><span class="sxs-lookup"><span data-stu-id="44757-159">In some languages, there are alphabetic characters that represent two separate characters.</span></span> <span data-ttu-id="44757-160">たとえば、複数の言語が文字を使用して`æ`、文字を表す`a`と`e`一緒に表示されます。</span><span class="sxs-lookup"><span data-stu-id="44757-160">For example, several languages use the character `æ` to represent the characters `a` and `e` when they appear together.</span></span> <span data-ttu-id="44757-161">`Like`演算子は、1 つ digraph 文字と 2 つの個別の文字が同等であるを認識します。</span><span class="sxs-lookup"><span data-stu-id="44757-161">The `Like` operator recognizes that the single digraph character and the two individual characters are equivalent.</span></span>  
  
 <span data-ttu-id="44757-162">Digraph 文字を使用する言語がシステムのロケール設定で指定されている場合、いずれかで 1 つ digraph 文字の発生`pattern`または`string`他の文字列で同等の 2 文字シーケンスと一致します。</span><span class="sxs-lookup"><span data-stu-id="44757-162">When a language that uses a digraph character is specified in the system locale settings, an occurrence of the single digraph character in either `pattern` or `string` matches the equivalent two-character sequence in the other string.</span></span> <span data-ttu-id="44757-163">同様に、digraph の文字`pattern`角かっこで囲む (単独で、一覧、または範囲) に同等の 2 文字のシーケンスと一致`string`です。</span><span class="sxs-lookup"><span data-stu-id="44757-163">Similarly, a digraph character in `pattern` enclosed in brackets (by itself, in a list, or in a range) matches the equivalent two-character sequence in `string`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="44757-164">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="44757-164">Overloading</span></span>  
 <span data-ttu-id="44757-165">`Like`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。</span><span class="sxs-lookup"><span data-stu-id="44757-165">The `Like` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="44757-166">コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義された動作を理解することを確認します。</span><span class="sxs-lookup"><span data-stu-id="44757-166">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="44757-167">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="44757-167">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="44757-168">例</span><span class="sxs-lookup"><span data-stu-id="44757-168">Example</span></span>  
 <span data-ttu-id="44757-169">この例では、`Like`をさまざまなパターン文字列を比較する演算子です。</span><span class="sxs-lookup"><span data-stu-id="44757-169">This example uses the `Like` operator to compare strings to various patterns.</span></span> <span data-ttu-id="44757-170">結果が入ります、`Boolean`各文字列がパターンを満たすかどうかを示す変数。</span><span class="sxs-lookup"><span data-stu-id="44757-170">The results go into a `Boolean` variable indicating whether each string satisfies the pattern.</span></span>  
  
 [!code-vb[VbVbalrOperators#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/like-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="44757-171">関連項目</span><span class="sxs-lookup"><span data-stu-id="44757-171">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>  
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>  
 [<span data-ttu-id="44757-172">比較演算子</span><span class="sxs-lookup"><span data-stu-id="44757-172">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [<span data-ttu-id="44757-173">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="44757-173">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="44757-174">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="44757-174">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="44757-175">Option Compare ステートメント</span><span class="sxs-lookup"><span data-stu-id="44757-175">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="44757-176">演算子および式</span><span class="sxs-lookup"><span data-stu-id="44757-176">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="44757-177">方法 : 文字列がパターンに一致するかを調べる</span><span class="sxs-lookup"><span data-stu-id="44757-177">How to: Match a String against a Pattern</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
