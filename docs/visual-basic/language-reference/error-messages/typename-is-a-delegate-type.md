---
title: "&quot;&lt;typename&gt;&quot; はデリゲート型です |。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32008
- vbc32008
dev_langs:
- VB
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
caps.latest.revision: 11
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
ms.openlocfilehash: 55532e269a7d6756157d324a2db14320df5d3f55
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="39lttypenamegt39-is-a-delegate-type"></a><span data-ttu-id="da920-102">'&lt;typename&gt;' はデリゲート型です。</span><span class="sxs-lookup"><span data-stu-id="da920-102">&#39;&lt;typename&gt;&#39; is a delegate type</span></span>
<span data-ttu-id="da920-103">'\<typename >' はデリゲート型です。</span><span class="sxs-lookup"><span data-stu-id="da920-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="da920-104">デリゲートの構築では、引数リストとして単一の AddressOf 式のみを許可します。</span><span class="sxs-lookup"><span data-stu-id="da920-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="da920-105">多くの場合、デリゲートの構築ではなく、AddressOf 式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="da920-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="da920-106">A`New`デリゲート クラスのインスタンスを作成する句は、デリゲート コンス トラクターに無効な引数リストを提供します。</span><span class="sxs-lookup"><span data-stu-id="da920-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="da920-107">1 つだけを指定する`AddressOf`新しいデリゲート インスタンスを作成するときの式。</span><span class="sxs-lookup"><span data-stu-id="da920-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="da920-108">失敗した場合、引数デリゲート コンス トラクターに複数の引数を渡すことも、1 つの引数を渡した場合、無効である場合にこのエラーが発生`AddressOf`式です。</span><span class="sxs-lookup"><span data-stu-id="da920-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="da920-109">**エラー ID:** BC32008</span><span class="sxs-lookup"><span data-stu-id="da920-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="da920-110">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="da920-110">To correct this error</span></span>  
  
-   <span data-ttu-id="da920-111">1 つを使用して`AddressOf`にデリゲート クラスの引数リスト内の式、`New`句。</span><span class="sxs-lookup"><span data-stu-id="da920-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da920-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="da920-112">See Also</span></span>  
 <span data-ttu-id="da920-113">[New 演算子](../../../visual-basic/language-reference/operators/new-operator.md) </span><span class="sxs-lookup"><span data-stu-id="da920-113">[New Operator](../../../visual-basic/language-reference/operators/new-operator.md) </span></span>  
<span data-ttu-id="da920-114"> [AddressOf 演算子](../../../visual-basic/language-reference/operators/addressof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="da920-114"> [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md) </span></span>  
<span data-ttu-id="da920-115"> [デリゲート](../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="da920-115"> [Delegates](../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="da920-116"> [方法: デリゲート メソッドを呼び出す](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)</span><span class="sxs-lookup"><span data-stu-id="da920-116"> [How to: Invoke a Delegate Method](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)</span></span>
