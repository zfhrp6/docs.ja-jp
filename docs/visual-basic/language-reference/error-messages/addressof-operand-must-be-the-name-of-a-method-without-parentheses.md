---
title: "& #39 です。AddressOf & #39;オペランドはかっこは不要メソッドの名前である必要があります。"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords: BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 02c996f1c94250526982e35395288b07db619db7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="46236-102">& #39 です。AddressOf & #39;オペランドはかっこは不要メソッドの名前である必要があります。</span><span class="sxs-lookup"><span data-stu-id="46236-102">&#39;AddressOf&#39; operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="46236-103">`AddressOf` 演算子は、特定のプロシージャを参照するプロシージャ デリゲート インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="46236-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="46236-104">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="46236-104">The syntax is as follows.</span></span>  
  
 <span data-ttu-id="46236-105">`AddressOf``procedurename`</span><span class="sxs-lookup"><span data-stu-id="46236-105">`AddressOf` `procedurename`</span></span>  
  
 <span data-ttu-id="46236-106">引数以下を囲むかっこを挿入した`AddressOf`[なし] が必要なします。</span><span class="sxs-lookup"><span data-stu-id="46236-106">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="46236-107">**エラー ID:** BC30577</span><span class="sxs-lookup"><span data-stu-id="46236-107">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="46236-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="46236-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="46236-109">引数以下、かっこを削除する`AddressOf`です。</span><span class="sxs-lookup"><span data-stu-id="46236-109">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2.  <span data-ttu-id="46236-110">引数がメソッド名を確認します。</span><span class="sxs-lookup"><span data-stu-id="46236-110">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46236-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="46236-111">See Also</span></span>  
 [<span data-ttu-id="46236-112">AddressOf 演算子</span><span class="sxs-lookup"><span data-stu-id="46236-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="46236-113">デリゲート</span><span class="sxs-lookup"><span data-stu-id="46236-113">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
