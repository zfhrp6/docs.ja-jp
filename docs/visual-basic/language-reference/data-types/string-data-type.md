---
title: 文字列型 (String) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.String
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings [Visual Basic], string data type
- literals [Visual Basic], string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals [Visual Basic]
- data types [Visual Basic], assigning
- String literals [Visual Basic]
- identifier type characters [Visual Basic], $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
ms.openlocfilehash: 894638bbe50dad2cae1f74a2f7b7fe006f029d1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592120"
---
# <a name="string-data-type-visual-basic"></a><span data-ttu-id="7de02-102">文字列型 (String) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7de02-102">String Data Type (Visual Basic)</span></span>
<span data-ttu-id="7de02-103">0 ~ 65535 の値の符号なし 16 ビット (2 バイト) コード ポイントのシーケンスの範囲を保持します。</span><span class="sxs-lookup"><span data-stu-id="7de02-103">Holds sequences of unsigned 16-bit (2-byte) code points that range in value from 0 through 65535.</span></span> <span data-ttu-id="7de02-104">各*コード ポイントが*、または文字コードを 1 つの Unicode 文字を表します。</span><span class="sxs-lookup"><span data-stu-id="7de02-104">Each *code point*, or character code, represents a single Unicode character.</span></span> <span data-ttu-id="7de02-105">文字列は、0 からおよそ 20億を含めることができます (2 ^31) の Unicode 文字。</span><span class="sxs-lookup"><span data-stu-id="7de02-105">A string can contain from 0 to approximately two billion (2 ^ 31) Unicode characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7de02-106">コメント</span><span class="sxs-lookup"><span data-stu-id="7de02-106">Remarks</span></span>  
 <span data-ttu-id="7de02-107">使用して、`String`の配列の管理オーバーヘッドがなく、複数の文字を格納するデータ型`Char()`、配列の`Char`要素。</span><span class="sxs-lookup"><span data-stu-id="7de02-107">Use the `String` data type to hold multiple characters without the array management overhead of `Char()`, an array of `Char` elements.</span></span>  
  
 <span data-ttu-id="7de02-108">既定値の`String`は`Nothing`(null 参照)。</span><span class="sxs-lookup"><span data-stu-id="7de02-108">The default value of `String` is `Nothing` (a null reference).</span></span> <span data-ttu-id="7de02-109">これはいない空の文字列と同じ (値`""`)。</span><span class="sxs-lookup"><span data-stu-id="7de02-109">Note that this is not the same as the empty string (value `""`).</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="7de02-110">Unicode 文字</span><span class="sxs-lookup"><span data-stu-id="7de02-110">Unicode Characters</span></span>  
 <span data-ttu-id="7de02-111">Unicode の最初の 128 個のコード ポイント (0 ~ 127) は、文字および記号の標準的な US キーボード上に対応します。</span><span class="sxs-lookup"><span data-stu-id="7de02-111">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="7de02-112">これらの最初の 128 個のコード ポイントと同じ、ASCII 文字セットを定義します。</span><span class="sxs-lookup"><span data-stu-id="7de02-112">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="7de02-113">2 番目の 128 個のコード ポイント (128 ~ 255) では、ラテン語系のアルファベット文字、アクセント記号、通貨記号、および分数などの特殊文字を表します。</span><span class="sxs-lookup"><span data-stu-id="7de02-113">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="7de02-114">Unicode は、さまざまなシンボルを他のコード ポイント (256 ~ 65535) を使用します。</span><span class="sxs-lookup"><span data-stu-id="7de02-114">Unicode uses the remaining code points (256-65535) for a wide variety of symbols.</span></span> <span data-ttu-id="7de02-115">これには、世界中のテキスト文字、分音文字、および数学と技術的な記号が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7de02-115">This includes worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="7de02-116">などのメソッドを使用することができます<xref:System.Char.IsDigit%2A>と<xref:System.Char.IsPunctuation%2A>で個々 の文字で、`String`の Unicode の分類を決定する変数。</span><span class="sxs-lookup"><span data-stu-id="7de02-116">You can use methods such as <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on an individual character in a `String` variable to determine its Unicode classification.</span></span>  
  
## <a name="format-requirements"></a><span data-ttu-id="7de02-117">書式の要件</span><span class="sxs-lookup"><span data-stu-id="7de02-117">Format Requirements</span></span>  
 <span data-ttu-id="7de02-118">囲む必要があります、`String`引用符で囲まれたリテラル (`" "`)。</span><span class="sxs-lookup"><span data-stu-id="7de02-118">You must enclose a `String` literal within quotation marks (`" "`).</span></span> <span data-ttu-id="7de02-119">2 つの連続する引用符を使用する場合は、文字列内の文字の 1 つとして、引用符を含める必要があります、(`""`)。</span><span class="sxs-lookup"><span data-stu-id="7de02-119">If you must include a quotation mark as one of the characters in the string, you use two contiguous quotation marks (`""`).</span></span> <span data-ttu-id="7de02-120">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="7de02-120">The following example illustrates this.</span></span>  
  
```  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 <span data-ttu-id="7de02-121">表す文字列の引用符、二重引用符は作業を開始および終了すると、引用符に依存しないことに注意してください、`String`リテラルです。</span><span class="sxs-lookup"><span data-stu-id="7de02-121">Note that the contiguous quotation marks that represent a quotation mark in the string are independent of the quotation marks that begin and end the `String` literal.</span></span>  
  
## <a name="string-manipulations"></a><span data-ttu-id="7de02-122">文字列操作</span><span class="sxs-lookup"><span data-stu-id="7de02-122">String Manipulations</span></span>  
 <span data-ttu-id="7de02-123">文字列を代入すると、`String`変数、その文字列は*不変*長さや内容を変更することができることはできません。</span><span class="sxs-lookup"><span data-stu-id="7de02-123">Once you assign a string to a `String` variable, that string is *immutable*, which means you cannot change its length or contents.</span></span> <span data-ttu-id="7de02-124">任意の方法で文字列を変更するときに、Visual Basic は新しい文字列を作成し、前の 1 つを破棄します。</span><span class="sxs-lookup"><span data-stu-id="7de02-124">When you alter a string in any way, Visual Basic creates a new string and abandons the previous one.</span></span> <span data-ttu-id="7de02-125">`String`変数は、新しい文字列を指します。</span><span class="sxs-lookup"><span data-stu-id="7de02-125">The `String` variable then points to the new string.</span></span>  
  
 <span data-ttu-id="7de02-126">内容を操作することができます、`String`さまざまな文字列関数を使用して変数。</span><span class="sxs-lookup"><span data-stu-id="7de02-126">You can manipulate the contents of a `String` variable by using a variety of string functions.</span></span> <span data-ttu-id="7de02-127">次の例を示しています、<xref:Microsoft.VisualBasic.Strings.Left%2A>関数</span><span class="sxs-lookup"><span data-stu-id="7de02-127">The following example illustrates the <xref:Microsoft.VisualBasic.Strings.Left%2A> function</span></span>  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 <span data-ttu-id="7de02-128">別のコンポーネントによって作成される文字列は、先頭または末尾の空白が埋め込まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7de02-128">A string created by another component might be padded with leading or trailing spaces.</span></span> <span data-ttu-id="7de02-129">このような文字列を受信する場合を使用できます、 <xref:Microsoft.VisualBasic.Strings.Trim%2A>、 <xref:Microsoft.VisualBasic.Strings.LTrim%2A>、および<xref:Microsoft.VisualBasic.Strings.RTrim%2A>をこれらのスペースを削除する関数。</span><span class="sxs-lookup"><span data-stu-id="7de02-129">If you receive such a string, you can use the <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, and <xref:Microsoft.VisualBasic.Strings.RTrim%2A> functions to remove these spaces.</span></span>  
  
 <span data-ttu-id="7de02-130">文字列操作の詳細については、次を参照してください。[文字列](../../../visual-basic/programming-guide/language-features/strings/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="7de02-130">For more information about string manipulations, see [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="7de02-131">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="7de02-131">Programming Tips</span></span>  
  
-   <span data-ttu-id="7de02-132">**負の数。**</span><span class="sxs-lookup"><span data-stu-id="7de02-132">**Negative Numbers.**</span></span> <span data-ttu-id="7de02-133">文字が保持していることに注意してください`String`署名されていないと、負の値を表すことはできません。</span><span class="sxs-lookup"><span data-stu-id="7de02-133">Remember that the characters held by `String` are unsigned and cannot represent negative values.</span></span> <span data-ttu-id="7de02-134">いずれの場合は、使用しないで`String`数値の値を保持します。</span><span class="sxs-lookup"><span data-stu-id="7de02-134">In any case, you should not use `String` to hold numeric values.</span></span>  
  
-   <span data-ttu-id="7de02-135">**相互運用の考慮事項。**</span><span class="sxs-lookup"><span data-stu-id="7de02-135">**Interop Considerations.**</span></span> <span data-ttu-id="7de02-136">オートメーション オブジェクトや COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントとやり取りする場合、他の環境では文字列の文字の別のデータ幅 (8 ビット) ことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7de02-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that string characters have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="7de02-137">このようなコンポーネントを 8 ビット文字の文字列引数を渡す場合として宣言`Byte()`、配列の`Byte`要素の代わりに`String`新しい Visual Basic コードでします。</span><span class="sxs-lookup"><span data-stu-id="7de02-137">If you are passing a string argument of 8-bit characters to such a component, declare it as `Byte()`, an array of `Byte` elements, instead of `String` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="7de02-138">**型宣言文字。**</span><span class="sxs-lookup"><span data-stu-id="7de02-138">**Type Characters.**</span></span> <span data-ttu-id="7de02-139">識別子の型文字を付加`$`任意の識別子を強制的に、`String`データ型。</span><span class="sxs-lookup"><span data-stu-id="7de02-139">Appending the identifier type character `$` to any identifier forces it to the `String` data type.</span></span> <span data-ttu-id="7de02-140">`String` リテラルの型文字がありません。</span><span class="sxs-lookup"><span data-stu-id="7de02-140">`String` has no literal type character.</span></span> <span data-ttu-id="7de02-141">ただし、コンパイラに引用符で囲まれたリテラル (`" "`) として`String`です。</span><span class="sxs-lookup"><span data-stu-id="7de02-141">However, the compiler treats literals enclosed in quotation marks (`" "`) as `String`.</span></span>  
  
-   <span data-ttu-id="7de02-142">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="7de02-142">**Framework Type.**</span></span> <span data-ttu-id="7de02-143">.NET Framework において対応する型は、<xref:System.String?displayProperty=nameWithType>クラスです。</span><span class="sxs-lookup"><span data-stu-id="7de02-143">The corresponding type in the .NET Framework is the <xref:System.String?displayProperty=nameWithType> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7de02-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="7de02-144">See Also</span></span>  
 <xref:System.String?displayProperty=nameWithType>  
 [<span data-ttu-id="7de02-145">データの種類</span><span class="sxs-lookup"><span data-stu-id="7de02-145">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="7de02-146">Char データ型</span><span class="sxs-lookup"><span data-stu-id="7de02-146">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [<span data-ttu-id="7de02-147">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="7de02-147">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="7de02-148">変換の概要</span><span class="sxs-lookup"><span data-stu-id="7de02-148">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="7de02-149">方法 : 符号なしの型を使用する Windows の機能を呼び出す</span><span class="sxs-lookup"><span data-stu-id="7de02-149">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="7de02-150">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="7de02-150">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
