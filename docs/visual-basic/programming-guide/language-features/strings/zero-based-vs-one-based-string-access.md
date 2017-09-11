---
title: "0 から始まるとします。Visual Basic における文字列の&1; から始まるアクセス |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
caps.latest.revision: 11
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
ms.openlocfilehash: d8d1000f134fa8f99509d12727b9fbd84cb0e831
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="42e16-102">0 から始まるとします。Visual Basic における文字列の&1; から始まるアクセス</span><span class="sxs-lookup"><span data-stu-id="42e16-102">Zero-based vs. One-based String Access in Visual Basic</span></span>
<span data-ttu-id="42e16-103">このトピックでは比較方法[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]と[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]文字列内の文字へのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="42e16-103">This topic compares how [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] and the [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] provide access to the characters in a string.</span></span> <span data-ttu-id="42e16-104">[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]が常に、文字列内の文字への&0; から始まるアクセスを提供[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]関数によって、0 から始まり、1 つベースのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="42e16-104">The [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] always provides zero-based access to the characters in a string, whereas [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="42e16-105">1 から始まる</span><span class="sxs-lookup"><span data-stu-id="42e16-105">One-Based</span></span>  
 <span data-ttu-id="42e16-106">たとえば&1; から始まるの[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]機能を検討してください、`Mid`関数です。</span><span class="sxs-lookup"><span data-stu-id="42e16-106">For an example of a one-based [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] function, consider the `Mid` function.</span></span> <span data-ttu-id="42e16-107">部分文字列が開始する、位置 1 から始まる文字位置を示す引数を受け取る。</span><span class="sxs-lookup"><span data-stu-id="42e16-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="42e16-108">[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.String.Substring%2A?displayProperty=fullName>メソッドは、文字のインデックスで部分文字列を開始するには、文字列の位置の 0 から開始します</xref:System.String.Substring%2A?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="42e16-108">The [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.String.Substring%2A?displayProperty=fullName> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="42e16-109">したがって、文字列"ABCDE"がある場合、個々 の文字の番号と 1,2,3,4,5 で使用するため、`Mid`関数が 0,1,2,3,4 で使用するため、<xref:System.String.Substring%2A?displayProperty=fullName>メソッド</xref:System.String.Substring%2A?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="42e16-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=fullName> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="42e16-110">0 から始まる</span><span class="sxs-lookup"><span data-stu-id="42e16-110">Zero-Based</span></span>  
 <span data-ttu-id="42e16-111">たとえば、0 から始まるの[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]機能を検討してください、`Split`関数です。</span><span class="sxs-lookup"><span data-stu-id="42e16-111">For an example of a zero-based [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] function, consider the `Split` function.</span></span> <span data-ttu-id="42e16-112">文字列を分割し、これらの部分文字列を含む配列を返します。</span><span class="sxs-lookup"><span data-stu-id="42e16-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="42e16-113">[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.String.Split%2A?displayProperty=fullName>もメソッドは文字列を分割し、部分文字列を含む配列を返します</xref:System.String.Split%2A?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="42e16-113">The [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.String.Split%2A?displayProperty=fullName> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="42e16-114">`Split`関数と<xref:System.String.Split%2A>メソッドの戻り値[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]配列、必要がある&0; から始まる</xref:System.String.Split%2A>。</span><span class="sxs-lookup"><span data-stu-id="42e16-114">Because the `Split` function and <xref:System.String.Split%2A> method return [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42e16-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="42e16-115">See Also</span></span>  
 <span data-ttu-id="42e16-116"><xref:Microsoft.VisualBasic.Strings.Mid%2A></xref:Microsoft.VisualBasic.Strings.Mid%2A></span><span class="sxs-lookup"><span data-stu-id="42e16-116"><xref:Microsoft.VisualBasic.Strings.Mid%2A></span></span>   
 <span data-ttu-id="42e16-117"><xref:Microsoft.VisualBasic.Strings.Split%2A></xref:Microsoft.VisualBasic.Strings.Split%2A></span><span class="sxs-lookup"><span data-stu-id="42e16-117"><xref:Microsoft.VisualBasic.Strings.Split%2A></span></span>   
 <span data-ttu-id="42e16-118"><xref:System.String.Substring%2A></xref:System.String.Substring%2A></span><span class="sxs-lookup"><span data-stu-id="42e16-118"><xref:System.String.Substring%2A></span></span>   
 <span data-ttu-id="42e16-119"><xref:System.String.Split%2A></xref:System.String.Split%2A></span><span class="sxs-lookup"><span data-stu-id="42e16-119"><xref:System.String.Split%2A></span></span>   
<span data-ttu-id="42e16-120"> [Visual Basic における文字列の概要](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)</span><span class="sxs-lookup"><span data-stu-id="42e16-120"> [Introduction to Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)</span></span>
