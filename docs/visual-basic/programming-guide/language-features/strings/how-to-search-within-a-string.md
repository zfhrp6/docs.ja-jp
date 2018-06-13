---
title: '方法 : 文字列内を検索する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: 08a005f2927a76c9b29c1ff0092ea8282188b2b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647684"
---
# <a name="how-to-search-within-a-string-visual-basic"></a><span data-ttu-id="472d6-102">方法 : 文字列内を検索する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="472d6-102">How to: Search Within a String (Visual Basic)</span></span>
<span data-ttu-id="472d6-103">この例では、<xref:System.String.IndexOf%2A>メソッドを<xref:System.String>部分文字列の最初に見つかった位置のインデックスを報告するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="472d6-103">This example calls the <xref:System.String.IndexOf%2A> method on a <xref:System.String> object to report the index of the first occurrence of a substring.</span></span>  
  
## <a name="example"></a><span data-ttu-id="472d6-104">例</span><span class="sxs-lookup"><span data-stu-id="472d6-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#71](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-search-within-a-string_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="472d6-105">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="472d6-105">Compiling the Code</span></span>  
 <span data-ttu-id="472d6-106">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="472d6-106">This example requires:</span></span>  
  
-   <span data-ttu-id="472d6-107">`Imports`ステートメントを指定する、<xref:System>名前空間。</span><span class="sxs-lookup"><span data-stu-id="472d6-107">An `Imports` statement specifying the <xref:System> namespace.</span></span> <span data-ttu-id="472d6-108">詳細については、「[Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="472d6-108">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="472d6-109">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="472d6-109">Robust Programming</span></span>  
 <span data-ttu-id="472d6-110"><xref:System.String.IndexOf%2A>メソッドは、最初に見つかった部分文字列の最初の文字の位置を報告します。</span><span class="sxs-lookup"><span data-stu-id="472d6-110">The <xref:System.String.IndexOf%2A> method reports the location of the first character of the first occurrence of the substring.</span></span> <span data-ttu-id="472d6-111">インデックスには、文字列の最初の文字が 0 のインデックスは、0 から始まります。</span><span class="sxs-lookup"><span data-stu-id="472d6-111">The index is 0-based, which means the first character of a string has an index of 0.</span></span>  
  
 <span data-ttu-id="472d6-112">場合<xref:System.String.IndexOf%2A>、部分文字列が見つからない-1 を返します。</span><span class="sxs-lookup"><span data-stu-id="472d6-112">If <xref:System.String.IndexOf%2A> does not find the substring, it returns -1.</span></span>  
  
 <span data-ttu-id="472d6-113"><xref:System.String.IndexOf%2A>メソッドは大文字小文字を区別し、現在のカルチャを使用します。</span><span class="sxs-lookup"><span data-stu-id="472d6-113">The <xref:System.String.IndexOf%2A> method is case-sensitive and uses the current culture.</span></span>  
  
 <span data-ttu-id="472d6-114">最適なエラー コントロールの文字列の検索をする可能性があります、`Try`のブロック、[を再試行してください.キャッチしてください.Finally ステートメント](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)構築します。</span><span class="sxs-lookup"><span data-stu-id="472d6-114">For optimal error control, you might want to enclose the string search in the `Try` block of a [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) construction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="472d6-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="472d6-115">See Also</span></span>  
 <xref:System.String.IndexOf%2A>  
 [<span data-ttu-id="472d6-116">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="472d6-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="472d6-117">Visual Basic の文字列の概要</span><span class="sxs-lookup"><span data-stu-id="472d6-117">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [<span data-ttu-id="472d6-118">文字列</span><span class="sxs-lookup"><span data-stu-id="472d6-118">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
