---
title: "入れ子になった関数にデリゲート & #39; と互換性のあるシグネチャがありません。&lt;delegatename&gt;& #39 です。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords: BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 60cf15343023110561da3e3fcf202bd00394127a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-39ltdelegatenamegt39"></a><span data-ttu-id="78770-102">入れ子になった関数にデリゲート & #39; と互換性のあるシグネチャがありません。&lt;delegatename&gt;& #39 です。</span><span class="sxs-lookup"><span data-stu-id="78770-102">Nested function does not have a signature that is compatible with delegate &#39;&lt;delegatename&gt;&#39;</span></span>
<span data-ttu-id="78770-103">ラムダ式は、互換性のないシグネチャを持つデリゲートに割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="78770-103">A lambda expression has been assigned to a delegate that has an incompatible signature.</span></span> <span data-ttu-id="78770-104">たとえば、次のコードでは、委任`Del`2 つの整数パラメーターします。</span><span class="sxs-lookup"><span data-stu-id="78770-104">For example, in the following code, delegate `Del` has two integer parameters.</span></span>  
  
```vb  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 <span data-ttu-id="78770-105">1 つの引数があるラムダ式は型として宣言されている場合、エラーが発生`Del`:</span><span class="sxs-lookup"><span data-stu-id="78770-105">The error is raised if a lambda expression with one argument is declared as type `Del`:</span></span>  
  
```vb  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 <span data-ttu-id="78770-106">**エラー ID:** BC36532</span><span class="sxs-lookup"><span data-stu-id="78770-106">**Error ID:** BC36532</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="78770-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="78770-107">To correct this error</span></span>  
  
-   <span data-ttu-id="78770-108">シグネチャに互換性があるようには、デリゲートの定義または割り当てられているラムダ式のいずれかを調整します。</span><span class="sxs-lookup"><span data-stu-id="78770-108">Adjust either the delegate definition or the assigned lambda expression so that the signatures are compatible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78770-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="78770-109">See Also</span></span>  
 [<span data-ttu-id="78770-110">厳密でないデリゲート変換</span><span class="sxs-lookup"><span data-stu-id="78770-110">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [<span data-ttu-id="78770-111">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="78770-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
