---
title: "デリゲート クラス&lt;classname&gt;&quot; この型の式がメソッド呼び出しの対象にすることはできませんので Invoke メソッドを持たない |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30220
- bc30220
dev_langs:
- VB
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
caps.latest.revision: 10
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
ms.openlocfilehash: 54cd62bc2b4cafa89873728ba4e5b31c46f1aab1
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="delegate-class-39ltclassnamegt39-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="5bb42-102">デリゲート クラス&lt;classname&gt;' れていない Invoke メソッドのため、この型の式がメソッド呼び出しの対象にすることはできません</span><span class="sxs-lookup"><span data-stu-id="5bb42-102">Delegate class &#39;&lt;classname&gt;&#39; has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>
<span data-ttu-id="5bb42-103">呼び出し`Invoke`がデリゲートからが失敗したため`Invoke`デリゲート クラスで実装されていません。</span><span class="sxs-lookup"><span data-stu-id="5bb42-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>  
  
 <span data-ttu-id="5bb42-104">**エラー ID:** BC30220</span><span class="sxs-lookup"><span data-stu-id="5bb42-104">**Error ID:** BC30220</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5bb42-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="5bb42-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="5bb42-106">デリゲート クラスのインスタンスが作成されたことを確認、`Dim`ステートメントと、プロシージャがデリゲートのインスタンスに割り当てられたこと、`AddressOf`演算子。</span><span class="sxs-lookup"><span data-stu-id="5bb42-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>  
  
2.  <span data-ttu-id="5bb42-107">デリゲート クラスを実装するコードを見つけてを実装しているかどうかを確認、`Invoke`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="5bb42-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bb42-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="5bb42-108">See Also</span></span>  
 <span data-ttu-id="5bb42-109">[デリゲート](../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="5bb42-109">[Delegates](../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="5bb42-110"> [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md) </span><span class="sxs-lookup"><span data-stu-id="5bb42-110"> [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) </span></span>  
<span data-ttu-id="5bb42-111"> [AddressOf 演算子](../../../visual-basic/language-reference/operators/addressof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="5bb42-111"> [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md) </span></span>  
<span data-ttu-id="5bb42-112"> [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="5bb42-112"> [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>
