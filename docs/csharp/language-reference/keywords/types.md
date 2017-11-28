---
title: "型 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- types [C#]
- data types [C#], type system
ms.assetid: 16b984df-f417-4e02-b1e6-4589d4a614ea
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2c7285e237b04c1290391c4bba3e62886dceb83c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="types-c-reference"></a><span data-ttu-id="d299b-102">型 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="d299b-102">Types (C# Reference)</span></span>
<span data-ttu-id="d299b-103">C# の型指定システムには次のカテゴリがあります。</span><span class="sxs-lookup"><span data-stu-id="d299b-103">The C# typing system contains the following categories:</span></span>  
  
-   [<span data-ttu-id="d299b-104">値型</span><span class="sxs-lookup"><span data-stu-id="d299b-104">Value types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
  
-   [<span data-ttu-id="d299b-105">参照型</span><span class="sxs-lookup"><span data-stu-id="d299b-105">Reference types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [<span data-ttu-id="d299b-106">ポインター型</span><span class="sxs-lookup"><span data-stu-id="d299b-106">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
 <span data-ttu-id="d299b-107">値型の変数はデータを格納し、参照型の変数は実データへの参照を格納します。</span><span class="sxs-lookup"><span data-stu-id="d299b-107">Variables that are value types store data, and those that are reference types store references to the actual data.</span></span> <span data-ttu-id="d299b-108">参照型はオブジェクトとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="d299b-108">Reference types are also referred to as objects.</span></span> <span data-ttu-id="d299b-109">ポインター型は [unsafe](../../../csharp/language-reference/keywords/unsafe.md) モードでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d299b-109">Pointer types can be used only in [unsafe](../../../csharp/language-reference/keywords/unsafe.md) mode.</span></span>  
  
 <span data-ttu-id="d299b-110">[ボックス化とボックス化解除](../../../csharp/programming-guide/types/boxing-and-unboxing.md)を使用して、値型を参照型に変換でき、参照型から値型に変換して戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="d299b-110">It is possible to convert a value type to a reference type, and back again to a value type, by using [boxing and unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span> <span data-ttu-id="d299b-111">ボックス化された値型の場合を除き、参照型を値型に変換することはできません。</span><span class="sxs-lookup"><span data-stu-id="d299b-111">With the exception of a boxed value type, you cannot convert a reference type to a value type.</span></span>  
  
 <span data-ttu-id="d299b-112">このセクションでは [void](../../../csharp/language-reference/keywords/void.md) についても説明します。</span><span class="sxs-lookup"><span data-stu-id="d299b-112">This section also introduces [void](../../../csharp/language-reference/keywords/void.md).</span></span>  
  
 <span data-ttu-id="d299b-113">値型は null 許容型でもあります。つまり、値がない状態を追加で格納することができます。</span><span class="sxs-lookup"><span data-stu-id="d299b-113">Value types are also nullable, which means they can store an additional non-value state.</span></span> <span data-ttu-id="d299b-114">詳細については、「[ull 許容型](../../../csharp/programming-guide/nullable-types/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d299b-114">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d299b-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="d299b-115">See Also</span></span>  
 [<span data-ttu-id="d299b-116">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="d299b-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d299b-117">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="d299b-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d299b-118">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="d299b-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d299b-119">型のリファレンス表</span><span class="sxs-lookup"><span data-stu-id="d299b-119">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
 [<span data-ttu-id="d299b-120">キャストと型変換</span><span class="sxs-lookup"><span data-stu-id="d299b-120">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [<span data-ttu-id="d299b-121">型</span><span class="sxs-lookup"><span data-stu-id="d299b-121">Types</span></span>](../../../csharp/programming-guide/types/index.md)
