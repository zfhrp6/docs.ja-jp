---
title: Null 許容型の推論はこのコンテキストではサポートされていません
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: ea531c7be676e940a263b019a66cc80cf280a772
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="252d2-102">Null 許容型の推論はこのコンテキストではサポートされていません</span><span class="sxs-lookup"><span data-stu-id="252d2-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="252d2-103">値の型と構造体宣言できます null 値を許容します。</span><span class="sxs-lookup"><span data-stu-id="252d2-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="252d2-104">ただし、型の推定と組み合わせて、null 許容型の宣言を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="252d2-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="252d2-105">次の例では、このエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="252d2-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="252d2-106">**エラー ID:** BC36629</span><span class="sxs-lookup"><span data-stu-id="252d2-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="252d2-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="252d2-107">To correct this error</span></span>  
  
-   <span data-ttu-id="252d2-108">使用して、`As`句を null 値許容と変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="252d2-108">Use an `As` clause to declare the variable as nullable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="252d2-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="252d2-109">See Also</span></span>  
 [<span data-ttu-id="252d2-110">null 許容値型</span><span class="sxs-lookup"><span data-stu-id="252d2-110">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [<span data-ttu-id="252d2-111">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="252d2-111">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
