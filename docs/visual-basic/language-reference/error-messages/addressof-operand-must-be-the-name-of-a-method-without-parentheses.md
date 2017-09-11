---
title: "&quot;AddressOf&quot; オペランドは、(かっこは不要) メソッドの名前を指定する必要があります。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30577
- bc30577
dev_langs:
- VB
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
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
ms.openlocfilehash: c4ee57896b70d8af1a7bc245bdb45521c2442fea
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="8f6a2-102">'AddressOf' オペランドは、(かっこは不要) メソッドの名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8f6a2-102">&#39;AddressOf&#39; operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="8f6a2-103">`AddressOf` 演算子は、特定のプロシージャを参照するプロシージャ デリゲート インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="8f6a2-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="8f6a2-104">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8f6a2-104">The syntax is as follows.</span></span>  
  
 <span data-ttu-id="8f6a2-105">`AddressOf` `procedurename`</span><span class="sxs-lookup"><span data-stu-id="8f6a2-105">`AddressOf` `procedurename`</span></span>  
  
 <span data-ttu-id="8f6a2-106">引数以下を囲むかっこを挿入した`AddressOf`[なし] が必要とされる、します。</span><span class="sxs-lookup"><span data-stu-id="8f6a2-106">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="8f6a2-107">**エラー ID:** BC30577</span><span class="sxs-lookup"><span data-stu-id="8f6a2-107">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8f6a2-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="8f6a2-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="8f6a2-109">引数以下を囲むかっこは削除`AddressOf`します。</span><span class="sxs-lookup"><span data-stu-id="8f6a2-109">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2.  <span data-ttu-id="8f6a2-110">引数がメソッド名を確認します。</span><span class="sxs-lookup"><span data-stu-id="8f6a2-110">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f6a2-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="8f6a2-111">See Also</span></span>  
 <span data-ttu-id="8f6a2-112">[AddressOf 演算子](../../../visual-basic/language-reference/operators/addressof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="8f6a2-112">[AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md) </span></span>  
<span data-ttu-id="8f6a2-113"> [デリゲート](../../../visual-basic/programming-guide/language-features/delegates/index.md)</span><span class="sxs-lookup"><span data-stu-id="8f6a2-113"> [Delegates](../../../visual-basic/programming-guide/language-features/delegates/index.md)</span></span>
