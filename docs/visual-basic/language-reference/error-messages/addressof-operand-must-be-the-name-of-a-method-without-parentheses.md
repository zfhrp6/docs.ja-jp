---
title: '&#39;AddressOf&#39;オペランドはかっこは不要メソッドの名前である必要があります'
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: 701d86e03d9b14236eec8436d99ec40cebbbcd44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583813"
---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="9c6b5-102">&#39;AddressOf&#39;オペランドはかっこは不要メソッドの名前である必要があります</span><span class="sxs-lookup"><span data-stu-id="9c6b5-102">&#39;AddressOf&#39; operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="9c6b5-103">`AddressOf` 演算子は、特定のプロシージャを参照するプロシージャ デリゲート インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="9c6b5-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="9c6b5-104">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9c6b5-104">The syntax is as follows.</span></span>  
  
 <span data-ttu-id="9c6b5-105">`AddressOf` `procedurename`</span><span class="sxs-lookup"><span data-stu-id="9c6b5-105">`AddressOf` `procedurename`</span></span>  
  
 <span data-ttu-id="9c6b5-106">引数以下を囲むかっこを挿入した`AddressOf`[なし] が必要なします。</span><span class="sxs-lookup"><span data-stu-id="9c6b5-106">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="9c6b5-107">**エラー ID:** BC30577</span><span class="sxs-lookup"><span data-stu-id="9c6b5-107">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9c6b5-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="9c6b5-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="9c6b5-109">引数以下、かっこを削除する`AddressOf`です。</span><span class="sxs-lookup"><span data-stu-id="9c6b5-109">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2.  <span data-ttu-id="9c6b5-110">引数がメソッド名を確認します。</span><span class="sxs-lookup"><span data-stu-id="9c6b5-110">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c6b5-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c6b5-111">See Also</span></span>  
 [<span data-ttu-id="9c6b5-112">AddressOf 演算子</span><span class="sxs-lookup"><span data-stu-id="9c6b5-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="9c6b5-113">デリゲート</span><span class="sxs-lookup"><span data-stu-id="9c6b5-113">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
