---
title: '方法: 日付または時刻を表す文字列を検証する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 411c8517783421b2472c3e4aa77287f8252f179b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647863"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="41234-102">方法: 日付または時刻を表す文字列を検証する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41234-102">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>
<span data-ttu-id="41234-103">次のコード例のセット、`Boolean`文字列が有効な日付または時刻を表しているかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="41234-103">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41234-104">例</span><span class="sxs-lookup"><span data-stu-id="41234-104">Example</span></span>  
 [!code-vb[VbVbcnRegEx#2](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-strings-that-represent-dates-or-times_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="41234-105">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="41234-105">Compiling the Code</span></span>  
 <span data-ttu-id="41234-106">置き換える`("01/01/03")`と`"9:30 PM"`日付と時刻を検証するとします。</span><span class="sxs-lookup"><span data-stu-id="41234-106">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="41234-107">ハード コードされた別の文字列、文字列を置き換えることができます、`String`など、文字列を返す変数、またはメソッドで`InputBox`です。</span><span class="sxs-lookup"><span data-stu-id="41234-107">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="41234-108">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="41234-108">Robust Programming</span></span>  
 <span data-ttu-id="41234-109">変換する前に、文字列を検証するには、このメソッドを使用して、`String`を`DateTime`変数。</span><span class="sxs-lookup"><span data-stu-id="41234-109">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="41234-110">最初の日付または時刻をチェックする場合は、実行時に例外を生成を回避できます。</span><span class="sxs-lookup"><span data-stu-id="41234-110">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41234-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="41234-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Information.IsDate%2A>  
 <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>  
 [<span data-ttu-id="41234-112">Visual Basic における文字列の検証</span><span class="sxs-lookup"><span data-stu-id="41234-112">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
