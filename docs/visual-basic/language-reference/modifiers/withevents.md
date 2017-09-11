---
title: "WithEvents (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.WithEvents
- WithEvents
dev_langs:
- VB
helpviewer_keywords:
- WithEvents keyword
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
caps.latest.revision: 17
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
ms.openlocfilehash: b956f8f0d6f0a2fd9f41c5df6d6c82b43fa09018
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="withevents-visual-basic"></a><span data-ttu-id="f84cb-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f84cb-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="f84cb-103">1 つまたは複数の宣言されたメンバー変数がイベントを発生させるクラスのインスタンスを参照しているかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f84cb-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f84cb-104">コメント</span><span class="sxs-lookup"><span data-stu-id="f84cb-104">Remarks</span></span>  
 <span data-ttu-id="f84cb-105">使用して変数を定義すると`WithEvents`、メソッドを使用して、変数のイベントを処理する宣言によって指定できます、`Handles`キーワードです。</span><span class="sxs-lookup"><span data-stu-id="f84cb-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>  
  
 <span data-ttu-id="f84cb-106">使用する`WithEvents`クラスまたはモジュール レベルでのみです。</span><span class="sxs-lookup"><span data-stu-id="f84cb-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="f84cb-107">つまりの宣言コンテキスト、`WithEvents`変数がクラスまたはモジュールにする必要があり、ソース ファイル、名前空間、構造体、またはプロシージャにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="f84cb-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>  
  
 <span data-ttu-id="f84cb-108">使用することはできません`WithEvents`構造体のメンバーにします。</span><span class="sxs-lookup"><span data-stu-id="f84cb-108">You cannot use `WithEvents` on a structure member.</span></span>  
  
 <span data-ttu-id="f84cb-109">それぞれの変数を宣言することができます-配列ではない — と`WithEvents`です。</span><span class="sxs-lookup"><span data-stu-id="f84cb-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="f84cb-110">ルール</span><span class="sxs-lookup"><span data-stu-id="f84cb-110">Rules</span></span>  
  
-   <span data-ttu-id="f84cb-111">**要素の型。**</span><span class="sxs-lookup"><span data-stu-id="f84cb-111">**Element Types.**</span></span> <span data-ttu-id="f84cb-112">宣言する必要があります`WithEvents`変数受け付けることができるため、オブジェクト変数をクラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="f84cb-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="f84cb-113">ただし、そのままは宣言できません`Object`します。</span><span class="sxs-lookup"><span data-stu-id="f84cb-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="f84cb-114">それをイベントを発生させる特定のクラスとして宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f84cb-114">You must declare them as the specific class that can raise the events.</span></span>  
  
 <span data-ttu-id="f84cb-115">`WithEvents`修飾子は、このコンテキストで使用できます: [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="f84cb-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f84cb-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f84cb-116">See Also</span></span>  
 <span data-ttu-id="f84cb-117">[ハンドル](../../../visual-basic/language-reference/statements/handles-clause.md) </span><span class="sxs-lookup"><span data-stu-id="f84cb-117">[Handles](../../../visual-basic/language-reference/statements/handles-clause.md) </span></span>  
<span data-ttu-id="f84cb-118"> [キーワード](../../../visual-basic/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="f84cb-118"> [Keywords](../../../visual-basic/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="f84cb-119"> [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="f84cb-119"> [Events](../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>
