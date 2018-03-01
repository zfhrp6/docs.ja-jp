---
title: "参照型 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c4f87363246deccf282b499aa2afee2a14d41593
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="eedd9-102">参照型 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="eedd9-102">Reference Types (C# Reference)</span></span>
<span data-ttu-id="eedd9-103">C# では、参照型と値型という 2 種類の型をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="eedd9-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="eedd9-104">参照型の変数はデータ (オブジェクト) への参照を格納するのに対して、値型の変数はデータを直接格納します。</span><span class="sxs-lookup"><span data-stu-id="eedd9-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="eedd9-105">参照型の場合、2 つの変数が同じオブジェクトを参照できるため、ある変数に対する演算によって、他の変数が参照しているオブジェクトが影響を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="eedd9-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="eedd9-106">値型の場合、各変数が独自のデータ コピーを保持し、ある変数に対する操作が別の変数に影響を与えることはありません (ref パラメーターと out パラメーターの変数を除きます。「[ref](../../../csharp/language-reference/keywords/ref.md)」と「[out パラメーター修飾子](../../../csharp/language-reference/keywords/out-parameter-modifier.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="eedd9-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of ref and out parameter variables, see [ref](../../../csharp/language-reference/keywords/ref.md) and [out parameter modifier](../../../csharp/language-reference/keywords/out-parameter-modifier.md)).</span></span>  
  
 <span data-ttu-id="eedd9-107">次のキーワードは、参照型を宣言するときに使用します。</span><span class="sxs-lookup"><span data-stu-id="eedd9-107">The following keywords are used to declare reference types:</span></span>  
  
-   [<span data-ttu-id="eedd9-108">class</span><span class="sxs-lookup"><span data-stu-id="eedd9-108">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="eedd9-109">interface</span><span class="sxs-lookup"><span data-stu-id="eedd9-109">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
-   [<span data-ttu-id="eedd9-110">delegate</span><span class="sxs-lookup"><span data-stu-id="eedd9-110">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
 <span data-ttu-id="eedd9-111">C# では次の組み込みの参照型も使用できます。</span><span class="sxs-lookup"><span data-stu-id="eedd9-111">C# also provides the following built-in reference types:</span></span>  
  
-   [<span data-ttu-id="eedd9-112">dynamic</span><span class="sxs-lookup"><span data-stu-id="eedd9-112">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)  
  
-   [<span data-ttu-id="eedd9-113">object</span><span class="sxs-lookup"><span data-stu-id="eedd9-113">object</span></span>](../../../csharp/language-reference/keywords/object.md)  
  
-   [<span data-ttu-id="eedd9-114">string</span><span class="sxs-lookup"><span data-stu-id="eedd9-114">string</span></span>](../../../csharp/language-reference/keywords/string.md)  
  
## <a name="see-also"></a><span data-ttu-id="eedd9-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="eedd9-115">See Also</span></span>  
 [<span data-ttu-id="eedd9-116">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="eedd9-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="eedd9-117">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="eedd9-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="eedd9-118">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="eedd9-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="eedd9-119">型</span><span class="sxs-lookup"><span data-stu-id="eedd9-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="eedd9-120">値型</span><span class="sxs-lookup"><span data-stu-id="eedd9-120">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)
