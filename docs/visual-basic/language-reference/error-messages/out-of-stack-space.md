---
title: "スタック領域が不足 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID28
dev_langs:
- VB
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
caps.latest.revision: 8
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
ms.openlocfilehash: 256ef0c7fcb3632e0c13d12737d438225343884f
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="fd373-102">スタック領域が不足しています。(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fd373-102">Out of stack space (Visual Basic)</span></span>
<span data-ttu-id="fd373-103">スタックは、実行しているプログラムの要求で動的に拡大または縮小するメモリの作業領域です。</span><span class="sxs-lookup"><span data-stu-id="fd373-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="fd373-104">限界を超えました。</span><span class="sxs-lookup"><span data-stu-id="fd373-104">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fd373-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="fd373-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="fd373-106">プロシージャが深すぎます。 入れ子にしないように確認してください。</span><span class="sxs-lookup"><span data-stu-id="fd373-106">Check that procedures are not nested too deeply.</span></span>  
  
2.  <span data-ttu-id="fd373-107">再帰プロシージャが正常に終了することを確認します。</span><span class="sxs-lookup"><span data-stu-id="fd373-107">Make sure recursive procedures terminate properly.</span></span>  
  
3.  <span data-ttu-id="fd373-108">ローカル変数では、複数領域がある必要がある場合は、モジュール レベルでいくつかの変数を宣言してください。</span><span class="sxs-lookup"><span data-stu-id="fd373-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="fd373-109">宣言することも、手順のすべての変数静的より前で、 `Property`、 `Sub`、または`Function`キーワード`Static`します。</span><span class="sxs-lookup"><span data-stu-id="fd373-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="fd373-110">使用することも、`Static`プロシージャ内で個別に静的変数を宣言するステートメントです。</span><span class="sxs-lookup"><span data-stu-id="fd373-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4.  <span data-ttu-id="fd373-111">固定長文字列可変長文字列よりも多いスタック領域を使用すると、可変長の文字列として、固定長文字列の一部を再定義します。</span><span class="sxs-lookup"><span data-stu-id="fd373-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="fd373-112">スタック領域必要ありません、モジュール レベルで文字列を定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="fd373-112">You can also define the string at module level where it requires no stack space.</span></span>  
  
5.  <span data-ttu-id="fd373-113">数を確認して入れ子になった`DoEvents`関数を使用して呼び出し、`Calls`ダイアログ ボックスで、スタック上でアクティブなプロシージャ ビューをします。</span><span class="sxs-lookup"><span data-stu-id="fd373-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6.  <span data-ttu-id="fd373-114">スタックに既にイベント プロシージャを呼び出すイベントをトリガーすることによって、「イベントの連鎖」を発生しないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="fd373-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="fd373-115">イベント cascade は、終端文字なし再帰プロシージャの呼び出しに似ていますが、によって呼び出されるためにわかりにくく、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]のコード内の明示的な呼び出しではなく。</span><span class="sxs-lookup"><span data-stu-id="fd373-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] rather than an explicit call in the code.</span></span> <span data-ttu-id="fd373-116">使用して、 `Calls` ダイアログ ボックス プロシージャが、スタック上でアクティブなビューにします。</span><span class="sxs-lookup"><span data-stu-id="fd373-116">Use the `Calls`dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd373-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd373-117">See Also</span></span>  
 <span data-ttu-id="fd373-118">[[メモリ] ウィンドウ](https://docs.microsoft.com/visualstudio/debugger/memory-windows)</span><span class="sxs-lookup"><span data-stu-id="fd373-118">[Memory Windows](https://docs.microsoft.com/visualstudio/debugger/memory-windows)</span></span>
