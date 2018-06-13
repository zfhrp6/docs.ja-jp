---
title: コンス トラクター &#39;&lt;名前&gt;&#39;自体を呼び出すことはできません
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 069de813a0426230e19cddf14c3b83d40a602a41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588997"
---
# <a name="constructor-39ltnamegt39-cannot-call-itself"></a><span data-ttu-id="a8a22-102">コンス トラクター &#39;&lt;名前&gt;&#39;自体を呼び出すことはできません</span><span class="sxs-lookup"><span data-stu-id="a8a22-102">Constructor &#39;&lt;name&gt;&#39; cannot call itself</span></span>
<span data-ttu-id="a8a22-103">A`Sub New`クラスまたは構造体でプロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a8a22-103">A `Sub New` procedure in a class or structure calls itself.</span></span>  
  
 <span data-ttu-id="a8a22-104">クラスのインスタンスを初期化するコンス トラクターの目的は、またはそのが最初に構造を作成します。</span><span class="sxs-lookup"><span data-stu-id="a8a22-104">The purpose of a constructor is to initialize an instance of a class or structure when it is first created.</span></span> <span data-ttu-id="a8a22-105">異なるパラメーター リストを持っている、それらはすべて、クラスまたは構造体によって複数のコンス トラクター、することができます。</span><span class="sxs-lookup"><span data-stu-id="a8a22-105">A class or structure can have several constructors, provided they all have different parameter lists.</span></span> <span data-ttu-id="a8a22-106">それ自体に加え、その機能を実行する別のコンス トラクターを呼び出し、コンス トラクターを許可します。</span><span class="sxs-lookup"><span data-stu-id="a8a22-106">A constructor is permitted to call another constructor to perform its functionality in addition to its own.</span></span> <span data-ttu-id="a8a22-107">コンス トラクターをそれ自体を呼び出すの意味がなく、実際に結果は無限再帰の許可されている場合。</span><span class="sxs-lookup"><span data-stu-id="a8a22-107">But it is meaningless for a constructor to call itself, and in fact it would result in infinite recursion if permitted.</span></span>  
  
 <span data-ttu-id="a8a22-108">**エラー ID:** BC30298</span><span class="sxs-lookup"><span data-stu-id="a8a22-108">**Error ID:** BC30298</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a8a22-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="a8a22-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="a8a22-110">呼び出されるコンス トラクターのパラメーター リストを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a8a22-110">Check the parameter list of the constructor being called.</span></span> <span data-ttu-id="a8a22-111">呼び出すコンス トラクターの場合と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a8a22-111">It should be different from that of the constructor making the call.</span></span>  
  
2.  <span data-ttu-id="a8a22-112">別のコンス トラクターを呼び出す予定がない場合は、削除、`Sub New`完全呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a8a22-112">If you do not intend to call a different constructor, remove the `Sub New` call entirely.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8a22-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8a22-113">See Also</span></span>  
 [<span data-ttu-id="a8a22-114">オブジェクトの有効期間 : オブジェクトの作成と破棄</span><span class="sxs-lookup"><span data-stu-id="a8a22-114">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
