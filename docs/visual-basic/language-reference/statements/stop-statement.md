---
title: Stop ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Stop
helpviewer_keywords:
- breakpoints, Stop statements
- Stop statements [Visual Basic], syntax
- Stop statements [Visual Basic]
- execution [Visual Basic], suspending
- processing, interrupting
- processes, interrupting
- execution [Visual Basic], stopping
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
ms.openlocfilehash: 955a3b6a2f7dc1d0e9823ed6d500ab7f7f9fe5b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599136"
---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="2c17f-102">Stop ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c17f-102">Stop Statement (Visual Basic)</span></span>
<span data-ttu-id="2c17f-103">実行を中断します。</span><span class="sxs-lookup"><span data-stu-id="2c17f-103">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c17f-104">構文</span><span class="sxs-lookup"><span data-stu-id="2c17f-104">Syntax</span></span>  
  
```  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="2c17f-105">コメント</span><span class="sxs-lookup"><span data-stu-id="2c17f-105">Remarks</span></span>  
 <span data-ttu-id="2c17f-106">配置できる`Stop`ステートメントの実行を中断するプロシージャに任意の場所。</span><span class="sxs-lookup"><span data-stu-id="2c17f-106">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="2c17f-107">使用して、`Stop`ステートメントは、コードでブレークポイントの設定に似ています。</span><span class="sxs-lookup"><span data-stu-id="2c17f-107">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="2c17f-108">`Stop`ステートメントのとは異なりの実行が中断`End`、任意のファイルを閉じておよびコンパイル済み実行可能 (.exe) ファイルで検出された場合を除き、任意の変数をクリアされません。</span><span class="sxs-lookup"><span data-stu-id="2c17f-108">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c17f-109">場合、`Stop`ステートメントが、統合開発環境 (IDE) の外部で実行されているコードで発生した場合、デバッガーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2c17f-109">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="2c17f-110">これは、コードをデバッグまたはリテールのモードでコンパイルされたかどうかに関係なく当てはまります。</span><span class="sxs-lookup"><span data-stu-id="2c17f-110">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c17f-111">例</span><span class="sxs-lookup"><span data-stu-id="2c17f-111">Example</span></span>  
 <span data-ttu-id="2c17f-112">この例では、`Stop`ステートメントの各繰り返しの実行を中断、`For...Next`ループします。</span><span class="sxs-lookup"><span data-stu-id="2c17f-112">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#56](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/stop-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2c17f-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c17f-113">See Also</span></span>  
 [<span data-ttu-id="2c17f-114">End ステートメント</span><span class="sxs-lookup"><span data-stu-id="2c17f-114">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
