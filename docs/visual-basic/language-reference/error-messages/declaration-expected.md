---
title: 宣言が必要です。
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 97bd1701a8a07c39d08a9276cdb929bc9425c1f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="declaration-expected"></a><span data-ttu-id="ed819-102">宣言が必要です。</span><span class="sxs-lookup"><span data-stu-id="ed819-102">Declaration expected</span></span>
<span data-ttu-id="ed819-103">Loop ステートメント、または割り当てなどの代入ステートメントは、プロシージャの外に発生します。</span><span class="sxs-lookup"><span data-stu-id="ed819-103">A nondeclarative statement, such as an assignment or loop statement, occurs outside any procedure.</span></span> <span data-ttu-id="ed819-104">外部のプロシージャ宣言のみが許可されます。</span><span class="sxs-lookup"><span data-stu-id="ed819-104">Only declarations are allowed outside procedures.</span></span>  
  
 <span data-ttu-id="ed819-105">または、プログラミング要素が宣言されている宣言キーワードを使用せずなど`Dim`または`Const`です。</span><span class="sxs-lookup"><span data-stu-id="ed819-105">Alternatively, a programming element is declared without a declaration keyword such as `Dim` or `Const`.</span></span>  
  
 <span data-ttu-id="ed819-106">**エラー ID:** BC30188</span><span class="sxs-lookup"><span data-stu-id="ed819-106">**Error ID:** BC30188</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ed819-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="ed819-107">To correct this error</span></span>  
  
-   <span data-ttu-id="ed819-108">代入ステートメントをプロシージャの本体に移動します。</span><span class="sxs-lookup"><span data-stu-id="ed819-108">Move the nondeclarative statement to the body of a procedure.</span></span>  
  
-   <span data-ttu-id="ed819-109">適切な宣言キーワードで宣言を開始します。</span><span class="sxs-lookup"><span data-stu-id="ed819-109">Begin the declaration with an appropriate declaration keyword.</span></span>  
  
-   <span data-ttu-id="ed819-110">宣言キーワードのスペルが間違っていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ed819-110">Ensure that a declaration keyword is not misspelled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed819-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="ed819-111">See Also</span></span>  
 [<span data-ttu-id="ed819-112">手順</span><span class="sxs-lookup"><span data-stu-id="ed819-112">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="ed819-113">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="ed819-113">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
