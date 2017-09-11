---
title: "ポインター変換 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
caps.latest.revision: 17
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
ms.openlocfilehash: e415d892d979e2bdcd648256150e2a96b1772ce4
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="f7c9b-102">ポインター変換 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="f7c9b-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="f7c9b-103">定義済みの暗黙的なポインター変換を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="f7c9b-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="f7c9b-104">暗黙的な変換は、メソッドの呼び出しや代入ステートメントなど、多くの状況で発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="f7c9b-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="f7c9b-105">暗黙的なポインター変換</span><span class="sxs-lookup"><span data-stu-id="f7c9b-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="f7c9b-106">変換前</span><span class="sxs-lookup"><span data-stu-id="f7c9b-106">From</span></span>|<span data-ttu-id="f7c9b-107">目的</span><span class="sxs-lookup"><span data-stu-id="f7c9b-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="f7c9b-108">任意のポインター型</span><span class="sxs-lookup"><span data-stu-id="f7c9b-108">Any pointer type</span></span>|<span data-ttu-id="f7c9b-109">void*</span><span class="sxs-lookup"><span data-stu-id="f7c9b-109">void*</span></span>|  
|<span data-ttu-id="f7c9b-110">null</span><span class="sxs-lookup"><span data-stu-id="f7c9b-110">null</span></span>|<span data-ttu-id="f7c9b-111">任意のポインター型</span><span class="sxs-lookup"><span data-stu-id="f7c9b-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="f7c9b-112">明示的なポインター変換は、暗黙的な変換がない場合に、キャスト式を使用して、変換を実行するために使用します。</span><span class="sxs-lookup"><span data-stu-id="f7c9b-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="f7c9b-113">次の表はこの変換についてまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="f7c9b-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="f7c9b-114">明示的なポインター変換</span><span class="sxs-lookup"><span data-stu-id="f7c9b-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="f7c9b-115">変換前</span><span class="sxs-lookup"><span data-stu-id="f7c9b-115">From</span></span>|<span data-ttu-id="f7c9b-116">目的</span><span class="sxs-lookup"><span data-stu-id="f7c9b-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="f7c9b-117">任意のポインター型</span><span class="sxs-lookup"><span data-stu-id="f7c9b-117">Any pointer type</span></span>|<span data-ttu-id="f7c9b-118">その他のポインター型</span><span class="sxs-lookup"><span data-stu-id="f7c9b-118">Any other pointer type</span></span>|  
|<span data-ttu-id="f7c9b-119">sbyte、byte、short、ushort、int、uint、long または ulong</span><span class="sxs-lookup"><span data-stu-id="f7c9b-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="f7c9b-120">任意のポインター型</span><span class="sxs-lookup"><span data-stu-id="f7c9b-120">Any pointer type</span></span>|  
|<span data-ttu-id="f7c9b-121">任意のポインター型</span><span class="sxs-lookup"><span data-stu-id="f7c9b-121">Any pointer type</span></span>|<span data-ttu-id="f7c9b-122">sbyte、byte、short、ushort、int、uint、long または ulong</span><span class="sxs-lookup"><span data-stu-id="f7c9b-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f7c9b-123">例</span><span class="sxs-lookup"><span data-stu-id="f7c9b-123">Example</span></span>  
 <span data-ttu-id="f7c9b-124">次の例では、`int` へのポインターは `byte` へのポインターに変換されます。</span><span class="sxs-lookup"><span data-stu-id="f7c9b-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="f7c9b-125">ポインターは、変数の最下位バイト アドレスを指すことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f7c9b-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="f7c9b-126">`int` のサイズ (4 バイト) まで結果を連続してインクリメントする場合、変数の残りのバイトを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="f7c9b-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 <span data-ttu-id="f7c9b-127">[!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f7c9b-127">[!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]</span></span>  
  
 <span data-ttu-id="f7c9b-128">[!code-cs[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="f7c9b-128">[!code-cs[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7c9b-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7c9b-129">See Also</span></span>  
 <span data-ttu-id="f7c9b-130">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f7c9b-130">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f7c9b-131">[ポインター式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="f7c9b-131">[Pointer Expressions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span></span>  
 <span data-ttu-id="f7c9b-132">[ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span><span class="sxs-lookup"><span data-stu-id="f7c9b-132">[Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span></span>  
 <span data-ttu-id="f7c9b-133">[型](../../../csharp/language-reference/keywords/types.md) </span><span class="sxs-lookup"><span data-stu-id="f7c9b-133">[Types](../../../csharp/language-reference/keywords/types.md) </span></span>  
 <span data-ttu-id="f7c9b-134">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span><span class="sxs-lookup"><span data-stu-id="f7c9b-134">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span></span>  
 <span data-ttu-id="f7c9b-135">[fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="f7c9b-135">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 [<span data-ttu-id="f7c9b-136">stackalloc</span><span class="sxs-lookup"><span data-stu-id="f7c9b-136">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)

