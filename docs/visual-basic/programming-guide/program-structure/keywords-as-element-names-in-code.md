---
title: "コード内の要素名としてのキーワード (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f410a0eaac0dcc034d406a89ed1d01a8f228a583
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a><span data-ttu-id="d5b96-102">コード内の要素名としてのキーワード (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5b96-102">Keywords as Element Names in Code (Visual Basic)</span></span>
<span data-ttu-id="d5b96-103">すべてのプログラム要素 — 変数、クラス、またはメンバーなど、予約されたキーワードと同じ名前を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="d5b96-103">Any program element — such as a variable, class, or member — can have the same name as a restricted keyword.</span></span> <span data-ttu-id="d5b96-104">たとえば、という名前の変数を作成することができます`Loop`です。</span><span class="sxs-lookup"><span data-stu-id="d5b96-104">For example, you can create a variable named `Loop`.</span></span> <span data-ttu-id="d5b96-105">ただし、そのバージョンを参照する —、制限と同じ名前を持つ`Loop`キーワード — 完全修飾文字列を付けますか、角かっこで囲んでする必要があります (`[ ]`) 次の例に示すように、します。</span><span class="sxs-lookup"><span data-stu-id="d5b96-105">However, to refer to your version of it — which has the same name as the restricted `Loop` keyword — you must either precede it with a full qualification string or enclose it in square brackets (`[ ]`), as the following example shows.</span></span>  
  
 [!code-vb[VbVbcnConventions#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/keywords-as-element-names-in-code_1.vb)]  
  
 <span data-ttu-id="d5b96-106">これらのうち、どちらも行わないかどうかは、Visual Basic は、組み込みの使用を想定しています`Loop`キーワードと、次の例のように、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="d5b96-106">If you do not do either of these, then Visual Basic assumes use of the intrinsic `Loop` keyword and produces an error, as in the following example:</span></span>  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 <span data-ttu-id="d5b96-107">角かっこを使用するには、フォームとコントロールを参照するとき、および変数を宣言するか、予約されたキーワードとして同じ名前のプロシージャを定義します。</span><span class="sxs-lookup"><span data-stu-id="d5b96-107">You can use square brackets when referring to forms and controls, and when declaring a variable or defining a procedure with the same name as a restricted keyword.</span></span> <span data-ttu-id="d5b96-108">忘れがち名を修飾するまたは角かっこを含めるため、コードにエラーが発生し読み取るが難しくなります。</span><span class="sxs-lookup"><span data-stu-id="d5b96-108">It can be easy to forget to qualify names or include square brackets, and thus introduce errors into your code and make it harder to read.</span></span> <span data-ttu-id="d5b96-109">このため、プログラム要素の名前として予約キーワードを使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d5b96-109">For this reason, we recommend that you not use restricted keywords as the names of program elements.</span></span> <span data-ttu-id="d5b96-110">ただし、将来のバージョンの Visual Basic では、既存のフォームまたはコントロールの名前と競合している新しいキーワードを定義する場合、できる方法を使用するこのコードを更新するときに、新しいバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="d5b96-110">However, if a future version of Visual Basic defines a new keyword that conflicts with an existing form or control name, then you can use this technique when updating your code to work with the new version.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5b96-111">また、プログラムは、他の参照先アセンブリによって提供される要素名をなどがあります。</span><span class="sxs-lookup"><span data-stu-id="d5b96-111">Your program also might include element names provided by other referenced assemblies.</span></span> <span data-ttu-id="d5b96-112">これらの名前は、制限付きのキーワードと競合している場合、角かっこで囲むことにすると Visual Basic では定義された要素として解釈します。</span><span class="sxs-lookup"><span data-stu-id="d5b96-112">If these names conflict with restricted keywords, then placing square brackets around them causes Visual Basic to interpret them as your defined elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5b96-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5b96-113">See Also</span></span>  
 [<span data-ttu-id="d5b96-114">Visual Basic の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="d5b96-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [<span data-ttu-id="d5b96-115">プログラム構造とコード規則</span><span class="sxs-lookup"><span data-stu-id="d5b96-115">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="d5b96-116">キーワード</span><span class="sxs-lookup"><span data-stu-id="d5b96-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
