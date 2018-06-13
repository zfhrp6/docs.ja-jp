---
title: 文字列関数 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- string functions
ms.assetid: f1bf9ac2-cbcf-4298-ae51-53182076bdc8
ms.openlocfilehash: f6c7f28cee03c2d5ac258cf1e2c8956225334f7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604147"
---
# <a name="string-functions-visual-basic"></a><span data-ttu-id="65fb6-102">文字列関数 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65fb6-102">String Functions (Visual Basic)</span></span>
<span data-ttu-id="65fb6-103">Visual Basic で文字列の検索と操作のために用意されている関数の一覧を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-103">The following table lists the functions that Visual Basic provides to search and manipulate strings.</span></span>  
  
|<span data-ttu-id="65fb6-104">.NET Framework メソッド</span><span class="sxs-lookup"><span data-stu-id="65fb6-104">.NET Framework method</span></span>|<span data-ttu-id="65fb6-105">説明</span><span class="sxs-lookup"><span data-stu-id="65fb6-105">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="65fb6-106"><xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A></span><span class="sxs-lookup"><span data-stu-id="65fb6-106"><xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A></span></span>|<span data-ttu-id="65fb6-107">文字に対応する文字コードを表す `Integer` 値を返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-107">Returns an `Integer` value representing the character code corresponding to a character.</span></span>|  
|<span data-ttu-id="65fb6-108"><xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A></span><span class="sxs-lookup"><span data-stu-id="65fb6-108"><xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A></span></span>|<span data-ttu-id="65fb6-109">指定された文字コードに対応する文字を返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-109">Returns the character associated with the specified character code.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Filter%2A>|<span data-ttu-id="65fb6-110">指定されたフィルター条件に基づいた文字列 (`String`) 配列のサブセットを含むゼロ ベースの配列を返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-110">Returns a zero-based array containing a subset of a `String` array based on specified filter criteria.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Format%2A>|<span data-ttu-id="65fb6-111">書式指定文字列 (`String`) 式に含まれる指示に従って書式設定された文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-111">Returns a string formatted according to instructions contained in a format `String` expression.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.FormatCurrency%2A>|<span data-ttu-id="65fb6-112">システムの [コントロール パネル] で定義されている通貨記号を使って通貨形式の文字列に書式設定して返す文字列処理関数です。</span><span class="sxs-lookup"><span data-stu-id="65fb6-112">Returns an expression formatted as a currency value using the currency symbol defined in the system control panel.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|<span data-ttu-id="65fb6-113">日時の値を表す文字列式を返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-113">Returns a string expression representing a date/time value.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.FormatNumber%2A>|<span data-ttu-id="65fb6-114">数値形式の文字列に書式設定して返す文字列処理関数です。</span><span class="sxs-lookup"><span data-stu-id="65fb6-114">Returns an expression formatted as a number.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.FormatPercent%2A>|<span data-ttu-id="65fb6-115">パーセント記号 (%) が付加されたパーセント形式 (100 で乗算した) の文字列に書式設定して返す文字列処理関数です。</span><span class="sxs-lookup"><span data-stu-id="65fb6-115">Returns an expression formatted as a percentage (that is, multiplied by 100) with a trailing % character.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.InStr%2A>|<span data-ttu-id="65fb6-116">ある文字列の中から指定した文字列を検索し、最初に見つかった文字列の開始位置を示す整数型の値を返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-116">Returns an integer specifying the start position of the first occurrence of one string within another.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.InStrRev%2A>|<span data-ttu-id="65fb6-117">ある文字列の中から指定された文字列を最後の文字位置から検索を開始し、最初に見つかった文字位置 (先頭からその位置までの文字数) を返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-117">Returns the position of the first occurrence of one string within another, starting from the right side of the string.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Join%2A>|<span data-ttu-id="65fb6-118">配列に含まれる多数の部分文字列を結合して作成される文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-118">Returns a string created by joining a number of substrings contained in an array.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.LCase%2A>|<span data-ttu-id="65fb6-119">小文字に変換した文字列または文字を返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-119">Returns a string or character converted to lowercase.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Left%2A>|<span data-ttu-id="65fb6-120">指定された文字数を含む文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-120">Returns a string containing a specified number of characters from the left side of a string.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Len%2A>|<span data-ttu-id="65fb6-121">文字列内の文字数を含む整数を返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-121">Returns an integer that contains the number of characters in a string.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.LSet%2A>|<span data-ttu-id="65fb6-122">指定の文字列が含まれている文字列を左寄せで指定の長さに調整して返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-122">Returns a left-aligned string containing the specified string adjusted to the specified length.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.LTrim%2A>|<span data-ttu-id="65fb6-123">指定された文字列から、先頭の空白を除いたコピーを格納する文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-123">Returns a string containing a copy of a specified string with no leading spaces.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Mid%2A>|<span data-ttu-id="65fb6-124">文字列から指定された文字数分の文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-124">Returns a string containing a specified number of characters from a string.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Replace%2A>|<span data-ttu-id="65fb6-125">指定された文字列の一部を指定された回数分別の部分文字列で置換した文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-125">Returns a string in which a specified substring has been replaced with another substring a specified number of times.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Right%2A>|<span data-ttu-id="65fb6-126">文字列の右端から指定された文字数分の文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-126">Returns a string containing a specified number of characters from the right side of a string.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.RSet%2A>|<span data-ttu-id="65fb6-127">文字列と長さが指定され、その長さに調整された文字列右揃えにして文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-127">Returns a right-aligned string containing the specified string adjusted to the specified length.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.RTrim%2A>|<span data-ttu-id="65fb6-128">指定された文字列から、末尾の空白を除いたコピーを格納する文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-128">Returns a string containing a copy of a specified string with no trailing spaces.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Space%2A>|<span data-ttu-id="65fb6-129">指定された数のスペースから成る文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-129">Returns a string consisting of the specified number of spaces.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Split%2A>|<span data-ttu-id="65fb6-130">部分文字列ごとに区切られた文字列からゼロ ベースの 1 次元配列を作成し、返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-130">Returns a zero-based, one-dimensional array containing a specified number of substrings.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.StrComp%2A>|<span data-ttu-id="65fb6-131">文字列比較の結果により、-1、0、または 1 のいずれかを返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-131">Returns -1, 0, or 1, based on the result of a string comparison.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.StrConv%2A>|<span data-ttu-id="65fb6-132">指定に従って変換された文字列型の値を返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-132">Returns a string converted as specified.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.StrDup%2A>|<span data-ttu-id="65fb6-133">指定された文字が指定された回数繰り返されている文字列型またはオブジェクト型の値を返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-133">Returns a string or object consisting of the specified character repeated the specified number of times.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.StrReverse%2A>|<span data-ttu-id="65fb6-134">指定された文字列の文字の並び順を逆にした文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-134">Returns a string in which the character order of a specified string is reversed.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Trim%2A>|<span data-ttu-id="65fb6-135">指定された文字列から、先頭または末尾の空白を除いたコピーを格納する文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-135">Returns a string containing a copy of a specified string with no leading or trailing spaces.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.UCase%2A>|<span data-ttu-id="65fb6-136">指定された文字列を大文字に変換して文字列型または char 型の値を返します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-136">Returns a string or character containing the specified string converted to uppercase.</span></span>|  
  
 <span data-ttu-id="65fb6-137">使用することができます、 [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)文字列の大文字と小文字のテキストを使用して比較するかどうかを設定するステートメントの並べ替え順序は、システムのロケールによって決まります (`Text`) または文字 (の内部バイナリ表現で`Binary`).</span><span class="sxs-lookup"><span data-stu-id="65fb6-137">You can use the [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) statement to set whether strings are compared using a case-insensitive text sort order determined by your system's locale (`Text`) or by the internal binary representations of the characters (`Binary`).</span></span> <span data-ttu-id="65fb6-138">既定のテキスト比較方法は `Binary` です。</span><span class="sxs-lookup"><span data-stu-id="65fb6-138">The default text comparison method is `Binary`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65fb6-139">例</span><span class="sxs-lookup"><span data-stu-id="65fb6-139">Example</span></span>  
 <span data-ttu-id="65fb6-140">`UCase` 関数を使って文字列を大文字に変換して返す例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-140">This example uses the `UCase` function to return an uppercase version of a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#31](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="65fb6-141">例</span><span class="sxs-lookup"><span data-stu-id="65fb6-141">Example</span></span>  
 <span data-ttu-id="65fb6-142">この例では、文字列変数から、`LTrim` 関数を使って先頭の空白を除去し、`RTrim` 関数を使って後続の空白を除去しています。</span><span class="sxs-lookup"><span data-stu-id="65fb6-142">This example uses the `LTrim` function to strip leading spaces and the `RTrim` function to strip trailing spaces from a string variable.</span></span> <span data-ttu-id="65fb6-143">また、`Trim` 関数を使って両方のタイプの空白を除去しています。</span><span class="sxs-lookup"><span data-stu-id="65fb6-143">It uses the `Trim` function to strip both types of spaces.</span></span>  
  
 [!code-vb[VbVbalrStrings#25](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="65fb6-144">例</span><span class="sxs-lookup"><span data-stu-id="65fb6-144">Example</span></span>  
 <span data-ttu-id="65fb6-145">`Mid` 関数を使って、文字列から指定された字数を返す例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-145">This example uses the `Mid` function to return a specified number of characters from a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#17](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="65fb6-146">例</span><span class="sxs-lookup"><span data-stu-id="65fb6-146">Example</span></span>  
 <span data-ttu-id="65fb6-147">`Len` 関数を使って文字列の文字数を返す例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-147">This example uses `Len` to return the number of characters in a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#33](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="65fb6-148">例</span><span class="sxs-lookup"><span data-stu-id="65fb6-148">Example</span></span>  
 <span data-ttu-id="65fb6-149">`InStr` 関数を使って、ある文字列の中から指定された文字列を検索し、最初に見つかった文字位置を返す例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-149">This example uses the `InStr` function to return the position of the first occurrence of one string within another.</span></span>  
  
 [!code-vb[VbVbalrStrings#8](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_5.vb)]  
  
## <a name="example"></a><span data-ttu-id="65fb6-150">例</span><span class="sxs-lookup"><span data-stu-id="65fb6-150">Example</span></span>  
 <span data-ttu-id="65fb6-151">`Format` の書式指定とユーザー定義の書式指定の両方を使って値の書式を指定する、`String` 関数のさまざまな使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="65fb6-151">This example shows various uses of the `Format` function to format values using both `String` formats and user-defined formats.</span></span> <span data-ttu-id="65fb6-152">日付の区切り記号 (`/`)、時刻の区切り記号 (`:`)、および午前/午後を示す文字 (`t` および `tt`) について、システムで実際に表示される書式は、コードが使用するロケール設定によって決まります。</span><span class="sxs-lookup"><span data-stu-id="65fb6-152">For the date separator (`/`), time separator (`:`), and the AM/PM indicators (`t` and `tt`), the actual formatted output displayed by your system depends on the locale settings the code is using.</span></span> <span data-ttu-id="65fb6-153">時刻と日付を開発環境で表示する場合は、コード ロケールの短い時刻書式と短い日付書式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="65fb6-153">When times and dates are displayed in the development environment, the short time format and short date format of the code locale are used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65fb6-154">24 時間制を使用するロケールでは、午前/午後を示す記号 (`t` および `tt`) では何も表示されません。</span><span class="sxs-lookup"><span data-stu-id="65fb6-154">For locales that use a 24-hour clock, the AM/PM indicators (`t` and `tt`) display nothing.</span></span>  
  
 [!code-vb[VbVbalrStrings#27](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="65fb6-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="65fb6-155">See Also</span></span>  
 [<span data-ttu-id="65fb6-156">キーワード</span><span class="sxs-lookup"><span data-stu-id="65fb6-156">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="65fb6-157">Visual Basic ランタイム ライブラリのメンバー</span><span class="sxs-lookup"><span data-stu-id="65fb6-157">Visual Basic Runtime Library Members</span></span>](../../../visual-basic/language-reference/runtime-library-members.md)  
 [<span data-ttu-id="65fb6-158">文字列操作の概要</span><span class="sxs-lookup"><span data-stu-id="65fb6-158">String Manipulation Summary</span></span>](../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)
