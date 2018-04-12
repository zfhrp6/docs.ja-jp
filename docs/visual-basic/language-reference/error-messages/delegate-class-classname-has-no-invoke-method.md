---
title: デリゲート クラス &#39;&lt;classname&gt;&#39; この型の式はメソッドの呼び出しのターゲットにすることはできませんので Invoke メソッドがありません
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 55d0e2442807e25737d90ac4b45a59b9d3e73037
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="delegate-class-39ltclassnamegt39-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="73494-102">デリゲート クラス &#39;&lt;classname&gt;&#39; この型の式はメソッドの呼び出しのターゲットにすることはできませんので Invoke メソッドがありません</span><span class="sxs-lookup"><span data-stu-id="73494-102">Delegate class &#39;&lt;classname&gt;&#39; has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>
<span data-ttu-id="73494-103">呼び出し`Invoke`がデリゲートから失敗しました。`Invoke`デリゲート クラスで実装されていません。</span><span class="sxs-lookup"><span data-stu-id="73494-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>  
  
 <span data-ttu-id="73494-104">**エラー ID:** BC30220</span><span class="sxs-lookup"><span data-stu-id="73494-104">**Error ID:** BC30220</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="73494-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="73494-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="73494-106">デリゲート クラスのインスタンスが作成されたことを確認してください、`Dim`ステートメントと、プロシージャがデリゲートのインスタンスに割り当てられている、`AddressOf`演算子。</span><span class="sxs-lookup"><span data-stu-id="73494-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>  
  
2.  <span data-ttu-id="73494-107">デリゲート クラスを実装するコードを検索しを実装するかどうかを確認、`Invoke`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="73494-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73494-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="73494-108">See Also</span></span>  
 [<span data-ttu-id="73494-109">デリゲート</span><span class="sxs-lookup"><span data-stu-id="73494-109">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="73494-110">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="73494-110">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="73494-111">AddressOf 演算子</span><span class="sxs-lookup"><span data-stu-id="73494-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="73494-112">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="73494-112">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
