---
title: ステートメントの終わりを指定してください。
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 7b91d13cbcb9d211d4ca18c8e48c7494bf6eccc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588081"
---
# <a name="end-of-statement-expected"></a><span data-ttu-id="f9275-102">ステートメントの終わりを指定してください。</span><span class="sxs-lookup"><span data-stu-id="f9275-102">End of statement expected</span></span>
<span data-ttu-id="f9275-103">ステートメントが構文的に完了するが、その他のプログラミング要素に依存してステートメントを終了する要素。</span><span class="sxs-lookup"><span data-stu-id="f9275-103">The statement is syntactically complete, but an additional programming element follows the element that completes the statement.</span></span> <span data-ttu-id="f9275-104">行終端記号が、すべてのステートメントの末尾に必要です。</span><span class="sxs-lookup"><span data-stu-id="f9275-104">A line terminator is required at the end of every statement.</span></span>
  
 <span data-ttu-id="f9275-105">行終端記号は、Visual Basic のソース ファイルの文字を行に分割します。</span><span class="sxs-lookup"><span data-stu-id="f9275-105">A line terminator divides the characters of a Visual Basic source file into lines.</span></span> <span data-ttu-id="f9275-106">行の終端記号の例としては、Unicode キャリッジ リターン文字 (& HD) を Unicode とライン フィード文字 (& HA)、Unicode キャリッジ リターン Unicode 改行文字が続く文字とします。</span><span class="sxs-lookup"><span data-stu-id="f9275-106">Examples of line terminators are the Unicode carriage return character (&HD), the Unicode linefeed character (&HA), and the Unicode carriage return character followed by the Unicode linefeed character.</span></span> <span data-ttu-id="f9275-107">行の終端記号の詳細については、次を参照してください。、 [Visual Basic 言語仕様](../../../visual-basic/reference/language-specification/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="f9275-107">For more information about line terminators, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>
  
 <span data-ttu-id="f9275-108">**エラー ID:** BC30205</span><span class="sxs-lookup"><span data-stu-id="f9275-108">**Error ID:** BC30205</span></span>
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f9275-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="f9275-109">To correct this error</span></span>
  
1.  <span data-ttu-id="f9275-110">2 つの異なるステートメントが同じ行に格納された誤ってかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="f9275-110">Check to see if two different statements have inadvertently been put on the same line.</span></span>
  
2.  <span data-ttu-id="f9275-111">ステートメントを終了する要素の後に、行終端記号を挿入します。</span><span class="sxs-lookup"><span data-stu-id="f9275-111">Insert a line terminator after the element that completes the statement.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f9275-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9275-112">See Also</span></span>  
 [<span data-ttu-id="f9275-113">方法 : コード内でステートメントを分割および連結する</span><span class="sxs-lookup"><span data-stu-id="f9275-113">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 [<span data-ttu-id="f9275-114">ステートメント</span><span class="sxs-lookup"><span data-stu-id="f9275-114">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
