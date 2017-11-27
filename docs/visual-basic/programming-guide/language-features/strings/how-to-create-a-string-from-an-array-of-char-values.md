---
title: "方法: Char 値の配列から文字列を作成する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 06e5c6923c26f3cb84b38475d6680523853d727d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a><span data-ttu-id="caa25-102">方法: Char 値の配列から文字列を作成する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="caa25-102">How to: Create a String from An Array of Char Values (Visual Basic)</span></span>
<span data-ttu-id="caa25-103">この例では、個別の文字から文字列"abcd"を作成します。</span><span class="sxs-lookup"><span data-stu-id="caa25-103">This example creates the string "abcd" from individual characters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="caa25-104">例</span><span class="sxs-lookup"><span data-stu-id="caa25-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#61](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-a-string-from-an-array-of-char-values_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="caa25-105">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="caa25-105">Compiling the Code</span></span>  
 <span data-ttu-id="caa25-106">このメソッドには、特別な要件はありません。</span><span class="sxs-lookup"><span data-stu-id="caa25-106">This method has no special requirements.</span></span>  
  
 <span data-ttu-id="caa25-107">構文`"a"c`, が、1 つ、`c`引用符で囲まれた 1 文字に依存して、文字リテラルを作成するために使用します。</span><span class="sxs-lookup"><span data-stu-id="caa25-107">The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="caa25-108">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="caa25-108">Robust Programming</span></span>  
 <span data-ttu-id="caa25-109">Null 文字 (に相当`Chr(0)`) 文字列が発生する予期しない結果文字列を使用する場合。</span><span class="sxs-lookup"><span data-stu-id="caa25-109">Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string.</span></span> <span data-ttu-id="caa25-110">Null 文字は、文字列に含まれますが、null 文字以降には、一部の状況では表示されません。</span><span class="sxs-lookup"><span data-stu-id="caa25-110">The null character will be included with the string, but characters following the null character will not be displayed in some situations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caa25-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="caa25-111">See Also</span></span>  
 <xref:System.String>  
 [<span data-ttu-id="caa25-112">Char データ型</span><span class="sxs-lookup"><span data-stu-id="caa25-112">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [<span data-ttu-id="caa25-113">データの種類</span><span class="sxs-lookup"><span data-stu-id="caa25-113">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
