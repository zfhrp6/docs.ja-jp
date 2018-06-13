---
title: '方法 : Visual Basic で文字列を文字の配列に変換する'
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: c109143601e304b1ec15a60c71d65fe6bd15aae8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648620"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a><span data-ttu-id="22904-102">方法 : Visual Basic で文字列を文字の配列に変換する</span><span class="sxs-lookup"><span data-stu-id="22904-102">How to: Convert a String to an Array of Characters in Visual Basic</span></span>
<span data-ttu-id="22904-103">文字、文字列および文字列を解析する際など、文字列内の文字の位置に関するデータが存在すると便利ですがあります。</span><span class="sxs-lookup"><span data-stu-id="22904-103">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string, such as when you are parsing a string.</span></span> <span data-ttu-id="22904-104">この例を呼び出して、文字列の文字列の文字の配列を取得する方法を示しています。<xref:System.String.ToCharArray%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="22904-104">This example shows how you can get an array of the characters in a string by calling the string's <xref:System.String.ToCharArray%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22904-105">例</span><span class="sxs-lookup"><span data-stu-id="22904-105">Example</span></span>  
 <span data-ttu-id="22904-106">文字列を分割する方法を示します、`Char`に文字列を分割する方法と、配列、 `String` Unicode テキスト文字の配列。</span><span class="sxs-lookup"><span data-stu-id="22904-106">This example demonstrates how to split a string into a `Char` array, and how to split a string into a `String` array of its Unicode text characters.</span></span> <span data-ttu-id="22904-107">この違いの理由は 2 つ以上の Unicode テキスト文字を構成することできます`Char`文字 (サロゲート ペアなど、組み合わせ文字のシーケンス)。</span><span class="sxs-lookup"><span data-stu-id="22904-107">The reason for this distinction is that Unicode text characters can be composed of two or more `Char` characters (such as a surrogate pair or a combining character sequence).</span></span> <span data-ttu-id="22904-108">詳細については、次を参照してください。 <xref:System.Globalization.TextElementEnumerator> "で Unicode 標準"とhttp://www.unicode.orgです。</span><span class="sxs-lookup"><span data-stu-id="22904-108">For more information, see <xref:System.Globalization.TextElementEnumerator> and "The Unicode Standard" at http://www.unicode.org.</span></span>  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="22904-109">例</span><span class="sxs-lookup"><span data-stu-id="22904-109">Example</span></span>  
 <span data-ttu-id="22904-110">Unicode テキスト文字、文字列に分割することは困難ですが、これは、文字列のビジュアル表現に関する情報が必要な場合。</span><span class="sxs-lookup"><span data-stu-id="22904-110">It is more difficult to split a string into its Unicode text characters, but this is necessary if you need information about the visual representation of a string.</span></span> <span data-ttu-id="22904-111">この例では、<xref:System.Globalization.StringInfo.SubstringByTextElements%2A>メソッド (string) を構成する Unicode 文字に関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="22904-111">This example uses the <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> method to get information about the Unicode text characters that make up a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="22904-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="22904-112">See Also</span></span>  
 <xref:System.String.Chars%2A>  
 <xref:System.Globalization.StringInfo?displayProperty=nameWithType>  
 [<span data-ttu-id="22904-113">方法 : 文字列の文字にアクセスする</span><span class="sxs-lookup"><span data-stu-id="22904-113">How to: Access Characters in Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)  
 [<span data-ttu-id="22904-114">Visual Basic で、文字列型とその他のデータ型との変換を行う</span><span class="sxs-lookup"><span data-stu-id="22904-114">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [<span data-ttu-id="22904-115">文字列</span><span class="sxs-lookup"><span data-stu-id="22904-115">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
