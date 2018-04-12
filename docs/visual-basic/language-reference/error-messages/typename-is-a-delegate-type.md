---
title: '&#39;です。&lt;typename&gt;&#39; はデリゲート型です。'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9428f0ac321b90e36d4d987381ed69b6c968894c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="39lttypenamegt39-is-a-delegate-type"></a><span data-ttu-id="5860c-102">&#39;です。&lt;typename&gt;&#39; はデリゲート型です。</span><span class="sxs-lookup"><span data-stu-id="5860c-102">&#39;&lt;typename&gt;&#39; is a delegate type</span></span>
<span data-ttu-id="5860c-103">'\<typename >' はデリゲート型です。</span><span class="sxs-lookup"><span data-stu-id="5860c-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="5860c-104">デリゲート構築では、引数リストとして 1 つの AddressOf 式のみを許可します。</span><span class="sxs-lookup"><span data-stu-id="5860c-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="5860c-105">多くの場合、デリゲート構築ではなく、AddressOf 式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="5860c-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="5860c-106">A`New`デリゲート クラスのインスタンスを作成する句は、デリゲート コンス トラクターに無効な引数リストを提供します。</span><span class="sxs-lookup"><span data-stu-id="5860c-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="5860c-107">1 つだけを指定することができます`AddressOf`式の新しいインスタンスを作成するときにします。</span><span class="sxs-lookup"><span data-stu-id="5860c-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="5860c-108">このエラーは発生したに失敗した場合、引数デリゲート コンス トラクターに 1 つ以上の引数を渡すか、有効なではない 1 つの引数を渡した場合`AddressOf`式。</span><span class="sxs-lookup"><span data-stu-id="5860c-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="5860c-109">**エラー ID:** BC32008</span><span class="sxs-lookup"><span data-stu-id="5860c-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5860c-110">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="5860c-110">To correct this error</span></span>  
  
-   <span data-ttu-id="5860c-111">1 つを使用して`AddressOf`にデリゲート クラスの引数リスト内の式、`New`句。</span><span class="sxs-lookup"><span data-stu-id="5860c-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5860c-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="5860c-112">See Also</span></span>  
 [<span data-ttu-id="5860c-113">New 演算子</span><span class="sxs-lookup"><span data-stu-id="5860c-113">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)  
 [<span data-ttu-id="5860c-114">AddressOf 演算子</span><span class="sxs-lookup"><span data-stu-id="5860c-114">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="5860c-115">デリゲート</span><span class="sxs-lookup"><span data-stu-id="5860c-115">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="5860c-116">方法: デリゲート メソッドを呼び出す</span><span class="sxs-lookup"><span data-stu-id="5860c-116">How to: Invoke a Delegate Method</span></span>](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
