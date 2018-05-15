---
title: プロパティまたはメソッドの呼び出しには、引数または戻り値としてプライベート オブジェクトへの参照を含めることはできません。
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 1f36526eab1bc0964bf89398b6e0f3e74d09fdc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a><span data-ttu-id="64e55-102">プロパティまたはメソッドの呼び出しには、引数または戻り値としてプライベート オブジェクトへの参照を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="64e55-102">A property or method call cannot include a reference to a private object, either as an argument or as a return value</span></span>
<span data-ttu-id="64e55-103">このエラーでは以下の原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="64e55-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="64e55-104">クライアントが、アウトプロセス コンポーネントのプロパティまたはメソッドを呼び出し、引数の 1 つとしてプライベート オブジェクトへの参照を渡そうとしました。</span><span class="sxs-lookup"><span data-stu-id="64e55-104">A client invoked a property or method of an out-of-process component and attempted to pass a reference to a private object as one of the arguments.</span></span>  
  
-   <span data-ttu-id="64e55-105">アウトプロセス コンポーネントがクライアントに対してコールバック メソッドを呼び出し、プライベート オブジェクトへの参照を渡そうとしました。</span><span class="sxs-lookup"><span data-stu-id="64e55-105">An out-of-process component invoked a call-back method on its client and attempted to pass a reference to a private object.</span></span>  
  
-   <span data-ttu-id="64e55-106">アウトプロセス コンポーネントが、それ自身が発生させているイベントの引数として、プライベート オブジェクトへの参照を渡そうとしました。</span><span class="sxs-lookup"><span data-stu-id="64e55-106">An out-of-process component attempted to pass a reference to a private object as an argument of an event it was raising.</span></span>  
  
-   <span data-ttu-id="64e55-107">クライアントが、それ自身が処理しているイベントの `ByRef` 引数に、プライベート オブジェクト参照を代入しようとしました。</span><span class="sxs-lookup"><span data-stu-id="64e55-107">A client attempted to assign a private object reference to a `ByRef` argument of an event it was handling.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="64e55-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="64e55-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="64e55-109">参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="64e55-109">Remove the reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64e55-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="64e55-110">See Also</span></span>  
 [<span data-ttu-id="64e55-111">Private</span><span class="sxs-lookup"><span data-stu-id="64e55-111">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
