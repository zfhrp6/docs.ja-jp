---
title: "-&gt; 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ->_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f42135e43bdfc58ee64fd3465074b3f8791f8ada
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-gt-operator-c-reference"></a><span data-ttu-id="d8456-102">-&gt; 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="d8456-102">-&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="d8456-103">`->` 演算子は、ポインターの逆参照とメンバー アクセスを組み合わせます。</span><span class="sxs-lookup"><span data-stu-id="d8456-103">The `->` operator combines pointer dereferencing and member access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8456-104">コメント</span><span class="sxs-lookup"><span data-stu-id="d8456-104">Remarks</span></span>  
 <span data-ttu-id="d8456-105">次のような形式の式があるとします。</span><span class="sxs-lookup"><span data-stu-id="d8456-105">An expression of the form,</span></span>  
  
```  
x->y  
```  
  
 <span data-ttu-id="d8456-106">ここで、`x` は `T*` 型のポインター、`y` は `T` のメンバーです。この式は次の式と同じです。</span><span class="sxs-lookup"><span data-stu-id="d8456-106">(where `x` is a pointer of type `T*` and `y` is a member of `T`) is equivalent to,</span></span>  
  
```  
(*x).y  
```  
  
 <span data-ttu-id="d8456-107">`->` 演算子は、[unsafe](../../../csharp/language-reference/keywords/unsafe.md) とマークされているコードでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d8456-107">The `->` operator can be used only in code that is marked as [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span></span>  
  
 <span data-ttu-id="d8456-108">`->` 演算子はオーバーロードできません。</span><span class="sxs-lookup"><span data-stu-id="d8456-108">The `->` operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8456-109">例</span><span class="sxs-lookup"><span data-stu-id="d8456-109">Example</span></span>  
 <span data-ttu-id="d8456-110">[!code-cs[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d8456-110">[!code-cs[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8456-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="d8456-111">See Also</span></span>  
 <span data-ttu-id="d8456-112">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="d8456-112">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="d8456-113">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d8456-113">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="d8456-114">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="d8456-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

