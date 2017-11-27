---
title: "Alias 句 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Alias
helpviewer_keywords: Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f61e738434ea616d751576ef21669545afc41397
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="f77d2-102">Alias 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f77d2-102">Alias Clause (Visual Basic)</span></span>
<span data-ttu-id="f77d2-103">外部プロシージャが DLL の中で別の名前を持つことを示します。</span><span class="sxs-lookup"><span data-stu-id="f77d2-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f77d2-104">コメント</span><span class="sxs-lookup"><span data-stu-id="f77d2-104">Remarks</span></span>  
 <span data-ttu-id="f77d2-105">`Alias`キーワードは、このコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="f77d2-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="f77d2-106">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="f77d2-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="f77d2-107">次の例で、 `Alias` advapi32.dll、内の関数の名前を指定するキーワードを使用`GetUserNameA`、その`getUserName`の代わりにこの例では使用できます。</span><span class="sxs-lookup"><span data-stu-id="f77d2-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="f77d2-108">関数`getUserName`sub で呼び出される`getUser`、現在のユーザーの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f77d2-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/alias-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f77d2-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="f77d2-109">See Also</span></span>  
 [<span data-ttu-id="f77d2-110">キーワード</span><span class="sxs-lookup"><span data-stu-id="f77d2-110">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
