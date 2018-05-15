---
title: スタック領域が不足しています。(Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: e39be5913fe877cf7b3396e4f13f4440288cb8f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="02084-102">スタック領域が不足しています。(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02084-102">Out of stack space (Visual Basic)</span></span>
<span data-ttu-id="02084-103">スタックは、実行しているプログラムの要求で動的に拡大および縮小するメモリの作業領域です。</span><span class="sxs-lookup"><span data-stu-id="02084-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="02084-104">上限を超えました。</span><span class="sxs-lookup"><span data-stu-id="02084-104">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="02084-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="02084-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="02084-106">プロシージャが深すぎます。 入れ子にできないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="02084-106">Check that procedures are not nested too deeply.</span></span>  
  
2.  <span data-ttu-id="02084-107">再帰プロシージャが正常に終了することを確認します。</span><span class="sxs-lookup"><span data-stu-id="02084-107">Make sure recursive procedures terminate properly.</span></span>  
  
3.  <span data-ttu-id="02084-108">ローカル変数では、ローカル変数領域を超える領域がある必要がある場合は、モジュール レベルでのいくつかの変数を宣言してみてください。</span><span class="sxs-lookup"><span data-stu-id="02084-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="02084-109">宣言することも、プロシージャのすべての変数静的前に追加して、 `Property`、 `Sub`、または`Function`キーワード`Static`です。</span><span class="sxs-lookup"><span data-stu-id="02084-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="02084-110">使用することができます、`Static`ステートメントをプロシージャ内で個別に静的変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="02084-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4.  <span data-ttu-id="02084-111">固定長文字列可変長文字列よりも多くのスタック領域を使用すると、可変長文字列として、固定長文字列の一部を再定義します。</span><span class="sxs-lookup"><span data-stu-id="02084-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="02084-112">ここでは必要ありませんスタック領域モジュール レベルで文字列を定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="02084-112">You can also define the string at module level where it requires no stack space.</span></span>  
  
5.  <span data-ttu-id="02084-113">数を確認して入れ子になった`DoEvents`関数を使用して呼び出し、`Calls`ダイアログ ボックスで、スタック上でアクティブなプロシージャ ビューをします。</span><span class="sxs-lookup"><span data-stu-id="02084-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6.  <span data-ttu-id="02084-114">スタックで既にイベント プロシージャを呼び出すイベントをトリガーすることによって、「イベントの連鎖」を発生しないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="02084-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="02084-115">イベント cascade は、未終了の再帰的なプロシージャの呼び出しに似ていますのコード内の明示的な呼び出しではなく、Visual Basic での呼び出しが行われるために、わかりにくいがします。</span><span class="sxs-lookup"><span data-stu-id="02084-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by Visual Basic rather than an explicit call in the code.</span></span> <span data-ttu-id="02084-116">使用して、`Calls`ダイアログ ボックスで、スタック上でアクティブなプロシージャ ビューをします。</span><span class="sxs-lookup"><span data-stu-id="02084-116">Use the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02084-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="02084-117">See Also</span></span>  
 <span data-ttu-id="02084-118">[[メモリ] ウィンドウ](/visualstudio/debugger/memory-windows)</span><span class="sxs-lookup"><span data-stu-id="02084-118">[Memory Windows](/visualstudio/debugger/memory-windows)</span></span>
