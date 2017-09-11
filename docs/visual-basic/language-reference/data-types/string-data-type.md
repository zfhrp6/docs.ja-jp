---
title: "文字列データ型 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.String
dev_langs:
- VB
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings, string data type
- literals, string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals
- data types [Visual Basic], assigning
- String literals
- identifier type characters, $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5d7a4272169ae7b2749d038e1116818d2cfbad95
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="string-data-type-visual-basic"></a><span data-ttu-id="c44c4-102">文字列型 (String) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c44c4-102">String Data Type (Visual Basic)</span></span>
<span data-ttu-id="c44c4-103">0 ~ 65535 の値の符号なし 16 ビット (2 バイト) コード ポイントのシーケンスの範囲を保持します。</span><span class="sxs-lookup"><span data-stu-id="c44c4-103">Holds sequences of unsigned 16-bit (2-byte) code points that range in value from 0 through 65535.</span></span> <span data-ttu-id="c44c4-104">各*コード ポイントが*、または文字コード&1; つの Unicode 文字を表します。</span><span class="sxs-lookup"><span data-stu-id="c44c4-104">Each *code point*, or character code, represents a single Unicode character.</span></span> <span data-ttu-id="c44c4-105">文字列は、およそ 20億に 0 を含むことができます (2 ^31) の Unicode 文字。</span><span class="sxs-lookup"><span data-stu-id="c44c4-105">A string can contain from 0 to approximately two billion (2 ^ 31) Unicode characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c44c4-106">コメント</span><span class="sxs-lookup"><span data-stu-id="c44c4-106">Remarks</span></span>  
 <span data-ttu-id="c44c4-107">使用して、`String`の配列の管理のオーバーヘッドなしに複数の文字を格納するデータ型`Char()`、配列の`Char`要素。</span><span class="sxs-lookup"><span data-stu-id="c44c4-107">Use the `String` data type to hold multiple characters without the array management overhead of `Char()`, an array of `Char` elements.</span></span>  
  
 <span data-ttu-id="c44c4-108">既定値の`String`は`Nothing`(null 参照)。</span><span class="sxs-lookup"><span data-stu-id="c44c4-108">The default value of `String` is `Nothing` (a null reference).</span></span> <span data-ttu-id="c44c4-109">これはいない空の文字列と同じ (値`""`)。</span><span class="sxs-lookup"><span data-stu-id="c44c4-109">Note that this is not the same as the empty string (value `""`).</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="c44c4-110">Unicode 文字</span><span class="sxs-lookup"><span data-stu-id="c44c4-110">Unicode Characters</span></span>  
 <span data-ttu-id="c44c4-111">Unicode の最初の 128 個のコード ポイント (0 ~ 127) は、文字および記号の標準的な US キーボード上に対応します。</span><span class="sxs-lookup"><span data-stu-id="c44c4-111">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="c44c4-112">これらの最初の 128 個のコード ポイントでは、ASCII 文字セットの定義と同じです。</span><span class="sxs-lookup"><span data-stu-id="c44c4-112">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="c44c4-113">2 番目の 128 個のコード ポイント (128 ~ 255) では、ラテン語系のアルファベット文字、アクセント記号、通貨記号、および分数などの特殊文字を表します。</span><span class="sxs-lookup"><span data-stu-id="c44c4-113">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="c44c4-114">Unicode は、さまざまなシンボルを他のコード ポイント (256 ~&65535;) を使用します。</span><span class="sxs-lookup"><span data-stu-id="c44c4-114">Unicode uses the remaining code points (256-65535) for a wide variety of symbols.</span></span> <span data-ttu-id="c44c4-115">これには、文字、分音文字、および数学と技術的な記号が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c44c4-115">This includes worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="c44c4-116">などのメソッドを使用することができます<xref:System.Char.IsDigit%2A>と<xref:System.Char.IsPunctuation%2A>で個々 の文字で、`String`変数を Unicode の分類を決定します</xref:System.Char.IsPunctuation%2A></xref:System.Char.IsDigit%2A>。</span><span class="sxs-lookup"><span data-stu-id="c44c4-116">You can use methods such as <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on an individual character in a `String` variable to determine its Unicode classification.</span></span>  
  
## <a name="format-requirements"></a><span data-ttu-id="c44c4-117">書式の要件</span><span class="sxs-lookup"><span data-stu-id="c44c4-117">Format Requirements</span></span>  
 <span data-ttu-id="c44c4-118">囲む必要があります、`String`引用符で囲まれたリテラル (`" "`)。</span><span class="sxs-lookup"><span data-stu-id="c44c4-118">You must enclose a `String` literal within quotation marks (`" "`).</span></span> <span data-ttu-id="c44c4-119">2 つの連続する引用符を使用する場合は、文字列内の文字の&1; つとして、引用符を含める必要があります、(`""`)。</span><span class="sxs-lookup"><span data-stu-id="c44c4-119">If you must include a quotation mark as one of the characters in the string, you use two contiguous quotation marks (`""`).</span></span> <span data-ttu-id="c44c4-120">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="c44c4-120">The following example illustrates this.</span></span>  
  
```  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 <span data-ttu-id="c44c4-121">表す文字列の引用符、二重引用符は開始と終了引用符に依存しないことに注意してください、`String`リテラルです。</span><span class="sxs-lookup"><span data-stu-id="c44c4-121">Note that the contiguous quotation marks that represent a quotation mark in the string are independent of the quotation marks that begin and end the `String` literal.</span></span>  
  
## <a name="string-manipulations"></a><span data-ttu-id="c44c4-122">文字列操作</span><span class="sxs-lookup"><span data-stu-id="c44c4-122">String Manipulations</span></span>  
 <span data-ttu-id="c44c4-123">文字列を代入すると、`String`変数、その文字列は*不変*長さや内容を変更することができることはできません。</span><span class="sxs-lookup"><span data-stu-id="c44c4-123">Once you assign a string to a `String` variable, that string is *immutable*, which means you cannot change its length or contents.</span></span> <span data-ttu-id="c44c4-124">任意の方法で文字列を変更すると、Visual Basic は新しい文字列を作成し、1 つ前を破棄します。</span><span class="sxs-lookup"><span data-stu-id="c44c4-124">When you alter a string in any way, Visual Basic creates a new string and abandons the previous one.</span></span> <span data-ttu-id="c44c4-125">`String`変数をポイントし、新しい文字列。</span><span class="sxs-lookup"><span data-stu-id="c44c4-125">The `String` variable then points to the new string.</span></span>  
  
 <span data-ttu-id="c44c4-126">内容を操作できる、`String`さまざまな文字列関数を使用して変数です。</span><span class="sxs-lookup"><span data-stu-id="c44c4-126">You can manipulate the contents of a `String` variable by using a variety of string functions.</span></span> <span data-ttu-id="c44c4-127">次の例は、<xref:Microsoft.VisualBasic.Strings.Left%2A>関数</xref:Microsoft.VisualBasic.Strings.Left%2A>を示しています。</span><span class="sxs-lookup"><span data-stu-id="c44c4-127">The following example illustrates the <xref:Microsoft.VisualBasic.Strings.Left%2A> function</span></span>  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 <span data-ttu-id="c44c4-128">別のコンポーネントによって作成される文字列は、先頭または末尾のスペースが埋め込まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c44c4-128">A string created by another component might be padded with leading or trailing spaces.</span></span> <span data-ttu-id="c44c4-129">このような文字列が表示される場合を使用できます、 <xref:Microsoft.VisualBasic.Strings.Trim%2A>、 <xref:Microsoft.VisualBasic.Strings.LTrim%2A>、および<xref:Microsoft.VisualBasic.Strings.RTrim%2A>これらのスペースを削除する関数</xref:Microsoft.VisualBasic.Strings.RTrim%2A></xref:Microsoft.VisualBasic.Strings.LTrim%2A></xref:Microsoft.VisualBasic.Strings.Trim%2A>。</span><span class="sxs-lookup"><span data-stu-id="c44c4-129">If you receive such a string, you can use the <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, and <xref:Microsoft.VisualBasic.Strings.RTrim%2A> functions to remove these spaces.</span></span>  
  
 <span data-ttu-id="c44c4-130">文字列操作の詳細については、次を参照してください。[文字列](../../../visual-basic/programming-guide/language-features/strings/index.md)します。</span><span class="sxs-lookup"><span data-stu-id="c44c4-130">For more information about string manipulations, see [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="c44c4-131">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="c44c4-131">Programming Tips</span></span>  
  
-   <span data-ttu-id="c44c4-132">**負の数。**</span><span class="sxs-lookup"><span data-stu-id="c44c4-132">**Negative Numbers.**</span></span> <span data-ttu-id="c44c4-133">文字が保持していることに注意してください`String`署名されておらず、負の値を表すことはできません。</span><span class="sxs-lookup"><span data-stu-id="c44c4-133">Remember that the characters held by `String` are unsigned and cannot represent negative values.</span></span> <span data-ttu-id="c44c4-134">いずれの場合は、使用しないでください`String`数値を格納します。</span><span class="sxs-lookup"><span data-stu-id="c44c4-134">In any case, you should not use `String` to hold numeric values.</span></span>  
  
-   <span data-ttu-id="c44c4-135">**相互運用の考慮事項。**</span><span class="sxs-lookup"><span data-stu-id="c44c4-135">**Interop Considerations.**</span></span> <span data-ttu-id="c44c4-136">オートメーション オブジェクトや COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントとやり取りする場合、他の環境では文字列の文字の別のデータ幅 (8 ビット) ことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c44c4-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that string characters have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="c44c4-137">このようなコンポーネントに 8 ビット文字の文字列引数を渡す場合として宣言`Byte()`、配列の`Byte`、要素の代わりに`String`新しい Visual Basic コードでします。</span><span class="sxs-lookup"><span data-stu-id="c44c4-137">If you are passing a string argument of 8-bit characters to such a component, declare it as `Byte()`, an array of `Byte` elements, instead of `String` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="c44c4-138">**型宣言文字。**</span><span class="sxs-lookup"><span data-stu-id="c44c4-138">**Type Characters.**</span></span> <span data-ttu-id="c44c4-139">識別子の型文字を追加する`$`任意の識別子にリテラルに、`String`データ型。</span><span class="sxs-lookup"><span data-stu-id="c44c4-139">Appending the identifier type character `$` to any identifier forces it to the `String` data type.</span></span> <span data-ttu-id="c44c4-140">`String`リテラルの型文字がありません。</span><span class="sxs-lookup"><span data-stu-id="c44c4-140">`String` has no literal type character.</span></span> <span data-ttu-id="c44c4-141">ただし、コンパイラは、引用符で囲まれたリテラルを扱います (`" "`) として`String`します。</span><span class="sxs-lookup"><span data-stu-id="c44c4-141">However, the compiler treats literals enclosed in quotation marks (`" "`) as `String`.</span></span>  
  
-   <span data-ttu-id="c44c4-142">**Framework のデータ型**</span><span class="sxs-lookup"><span data-stu-id="c44c4-142">**Framework Type.**</span></span> <span data-ttu-id="c44c4-143">.NET Framework において対応する型が<xref:System.String?displayProperty=fullName>クラスです。</xref:System.String?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="c44c4-143">The corresponding type in the .NET Framework is the <xref:System.String?displayProperty=fullName> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c44c4-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="c44c4-144">See Also</span></span>  
 <span data-ttu-id="c44c4-145"><xref:System.String?displayProperty=fullName></xref:System.String?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="c44c4-145"><xref:System.String?displayProperty=fullName></span></span>   
<span data-ttu-id="c44c4-146"> [データ型](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="c44c4-146"> [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="c44c4-147"> [Char データ型](../../../visual-basic/language-reference/data-types/char-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="c44c4-147"> [Char Data Type](../../../visual-basic/language-reference/data-types/char-data-type.md) </span></span>  
<span data-ttu-id="c44c4-148"> [型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="c44c4-148"> [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="c44c4-149"> [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span><span class="sxs-lookup"><span data-stu-id="c44c4-149"> [Conversion Summary](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span></span>  
<span data-ttu-id="c44c4-150"> [方法: 符号なしの型、Windows 関数を呼び出す](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md) </span><span class="sxs-lookup"><span data-stu-id="c44c4-150"> [How to: Call a Windows Function that Takes Unsigned Types](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md) </span></span>  
<span data-ttu-id="c44c4-151"> [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="c44c4-151"> [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)</span></span>

