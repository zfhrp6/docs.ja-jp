---
title: Stop ステートメント (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d4b7f04214234837a86bf0c77c0d7b6934e2babd
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="a1b2c-102">Stop ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1b2c-102">Stop Statement (Visual Basic)</span></span>
<span data-ttu-id="a1b2c-103">実行を中断します。</span><span class="sxs-lookup"><span data-stu-id="a1b2c-103">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1b2c-104">構文</span><span class="sxs-lookup"><span data-stu-id="a1b2c-104">Syntax</span></span>  
  
```  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="a1b2c-105">コメント</span><span class="sxs-lookup"><span data-stu-id="a1b2c-105">Remarks</span></span>  
 <span data-ttu-id="a1b2c-106">配置できる`Stop`ステートメントの実行を中断するプロシージャに任意の場所。</span><span class="sxs-lookup"><span data-stu-id="a1b2c-106">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="a1b2c-107">使用して、`Stop`ステートメントは、コードでブレークポイントの設定に似ています。</span><span class="sxs-lookup"><span data-stu-id="a1b2c-107">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="a1b2c-108">`Stop`ステートメントのとは異なりの実行が中断`End`、任意のファイルを閉じておよびコンパイル済み実行可能 (.exe) ファイルで検出された場合を除き、任意の変数をクリアされません。</span><span class="sxs-lookup"><span data-stu-id="a1b2c-108">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1b2c-109">場合、`Stop`ステートメントが、統合開発環境 (IDE) の外部で実行されているコードで発生した場合、デバッガーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a1b2c-109">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="a1b2c-110">これは、コードをデバッグまたはリテールのモードでコンパイルされたかどうかに関係なく当てはまります。</span><span class="sxs-lookup"><span data-stu-id="a1b2c-110">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1b2c-111">例</span><span class="sxs-lookup"><span data-stu-id="a1b2c-111">Example</span></span>  
 <span data-ttu-id="a1b2c-112">この例では、`Stop`ステートメントの各繰り返しの実行を中断、`For...Next`ループします。</span><span class="sxs-lookup"><span data-stu-id="a1b2c-112">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#56](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/stop-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a1b2c-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1b2c-113">See Also</span></span>  
 [<span data-ttu-id="a1b2c-114">End ステートメント</span><span class="sxs-lookup"><span data-stu-id="a1b2c-114">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
