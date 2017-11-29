---
title: "方法 : Visual Basic で文字列の文字にアクセスする"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 54d604fc08dd97e0e31f9bcec148431374e8ef8f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="98d40-102">方法 : Visual Basic で文字列の文字にアクセスする</span><span class="sxs-lookup"><span data-stu-id="98d40-102">How to: Access Characters in Strings in Visual Basic</span></span>
<span data-ttu-id="98d40-103">この例で使用する方法、<xref:System.String.Chars%2A>文字列で指定した場所にある文字にアクセスするプロパティです。</span><span class="sxs-lookup"><span data-stu-id="98d40-103">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98d40-104">例</span><span class="sxs-lookup"><span data-stu-id="98d40-104">Example</span></span>  
 <span data-ttu-id="98d40-105">文字、文字列と、文字列内の文字の位置に関するデータが存在すると便利ですがあります。</span><span class="sxs-lookup"><span data-stu-id="98d40-105">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="98d40-106">文字の配列として文字列の考えることができます (`Char`インスタンス); 特定の文字を取得するには、その文字のインデックスを参照する、<xref:System.String.Chars%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="98d40-106">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 [!code-vb[VbVbalrStrings#49](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-access-characters-in-strings_1.vb)]  
  
 <span data-ttu-id="98d40-107">`index`のパラメーター、<xref:System.String.Chars%2A>プロパティは 0 から始まる。</span><span class="sxs-lookup"><span data-stu-id="98d40-107">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="98d40-108">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="98d40-108">Robust Programming</span></span>  
 <span data-ttu-id="98d40-109"><xref:System.String.Chars%2A>プロパティが指定した位置にある文字を返します。</span><span class="sxs-lookup"><span data-stu-id="98d40-109">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="98d40-110">ただし、Unicode 文字の一部は、1 つ以上の文字によって表されることができます。</span><span class="sxs-lookup"><span data-stu-id="98d40-110">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="98d40-111">Unicode 文字を使用する方法の詳細については、次を参照してください。[する方法: 文字列、配列の文字を変換](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)です。</span><span class="sxs-lookup"><span data-stu-id="98d40-111">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="98d40-112"><xref:System.String.Chars%2A>プロパティがスローされます、<xref:System.IndexOutOfRangeException>例外場合、`index`パラメーターは、文字列の長さ以上には 0 より小さい場合、または</span><span class="sxs-lookup"><span data-stu-id="98d40-112">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98d40-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="98d40-113">See Also</span></span>  
 <xref:System.String.Chars%2A>  
 [<span data-ttu-id="98d40-114">方法 : 文字列を文字の配列に変換する</span><span class="sxs-lookup"><span data-stu-id="98d40-114">How to: Convert a String to an Array of Characters</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)  
 [<span data-ttu-id="98d40-115">Visual Basic で、文字列型とその他のデータ型との変換を行う</span><span class="sxs-lookup"><span data-stu-id="98d40-115">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [<span data-ttu-id="98d40-116">文字列</span><span class="sxs-lookup"><span data-stu-id="98d40-116">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
