---
title: "0 から始まる vs です。Visual Basic で文字列の 1 つに基づいたアクセス"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 911f063d6ca9a3f5d88a1f50d9df7f908a488f66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="24826-102">0 から始まる vs です。Visual Basic で文字列の 1 つに基づいたアクセス</span><span class="sxs-lookup"><span data-stu-id="24826-102">Zero-based vs. One-based String Access in Visual Basic</span></span>
<span data-ttu-id="24826-103">このトピックでは比較方法[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]と[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]文字列の文字へのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="24826-103">This topic compares how [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] provide access to the characters in a string.</span></span> <span data-ttu-id="24826-104">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]常に対し、文字列の文字に 0 から始まるアクセスを提供[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]関数によって、および 0 から始まる 1 ベースのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="24826-104">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] always provides zero-based access to the characters in a string, whereas [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="24826-105">1 から始まる</span><span class="sxs-lookup"><span data-stu-id="24826-105">One-Based</span></span>  
 <span data-ttu-id="24826-106">1 から始まるの例については[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]機能を考慮してください、`Mid`関数。</span><span class="sxs-lookup"><span data-stu-id="24826-106">For an example of a one-based [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] function, consider the `Mid` function.</span></span> <span data-ttu-id="24826-107">位置 1 から始まる、部分文字列を開始する文字位置を示す引数を受け取る。</span><span class="sxs-lookup"><span data-stu-id="24826-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="24826-108">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType>メソッドは、文字のインデックスを開始するには、部分文字列を文字列 0 の位置から開始します。</span><span class="sxs-lookup"><span data-stu-id="24826-108">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="24826-109">したがって、文字列"ABCDE"がある場合、個々 の文字の番号と 1,2,3,4,5 で使用するため、`Mid`関数が 0,1,2,3,4 で使用するため、<xref:System.String.Substring%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="24826-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="24826-110">0 から始まる</span><span class="sxs-lookup"><span data-stu-id="24826-110">Zero-Based</span></span>  
 <span data-ttu-id="24826-111">0 から始まるの例については[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]機能を考慮してください、`Split`関数。</span><span class="sxs-lookup"><span data-stu-id="24826-111">For an example of a zero-based [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] function, consider the `Split` function.</span></span> <span data-ttu-id="24826-112">文字列を分割し、各部分文字列を含む配列を返します。</span><span class="sxs-lookup"><span data-stu-id="24826-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="24826-113">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType>もメソッドは文字列を分割し、部分文字列を含む配列を返します。</span><span class="sxs-lookup"><span data-stu-id="24826-113">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="24826-114">`Split`関数と<xref:System.String.Split%2A>メソッドの戻り値[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]配列、する必要がある 0 から始まる。</span><span class="sxs-lookup"><span data-stu-id="24826-114">Because the `Split` function and <xref:System.String.Split%2A> method return [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24826-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="24826-115">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 <xref:Microsoft.VisualBasic.Strings.Split%2A>  
 <xref:System.String.Substring%2A>  
 <xref:System.String.Split%2A>  
 [<span data-ttu-id="24826-116">Visual Basic の文字列の概要</span><span class="sxs-lookup"><span data-stu-id="24826-116">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
