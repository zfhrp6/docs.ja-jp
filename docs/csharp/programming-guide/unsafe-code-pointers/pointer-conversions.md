---
title: "ポインター変換 (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 36589d139c91e04d9e3d8b31281a91c26b85a5d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="a717e-102">ポインター変換 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="a717e-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="a717e-103">定義済みの暗黙的なポインター変換を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="a717e-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="a717e-104">暗黙的な変換は、メソッドの呼び出しや代入ステートメントなど、多くの状況で発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="a717e-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="a717e-105">暗黙的なポインター変換</span><span class="sxs-lookup"><span data-stu-id="a717e-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="a717e-106">変換前</span><span class="sxs-lookup"><span data-stu-id="a717e-106">From</span></span>|<span data-ttu-id="a717e-107">目的</span><span class="sxs-lookup"><span data-stu-id="a717e-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="a717e-108">任意のポインター型</span><span class="sxs-lookup"><span data-stu-id="a717e-108">Any pointer type</span></span>|<span data-ttu-id="a717e-109">void*</span><span class="sxs-lookup"><span data-stu-id="a717e-109">void*</span></span>|  
|<span data-ttu-id="a717e-110">null</span><span class="sxs-lookup"><span data-stu-id="a717e-110">null</span></span>|<span data-ttu-id="a717e-111">任意のポインター型</span><span class="sxs-lookup"><span data-stu-id="a717e-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="a717e-112">明示的なポインター変換は、暗黙的な変換がない場合に、キャスト式を使用して、変換を実行するために使用します。</span><span class="sxs-lookup"><span data-stu-id="a717e-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="a717e-113">次の表はこの変換についてまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="a717e-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="a717e-114">明示的なポインター変換</span><span class="sxs-lookup"><span data-stu-id="a717e-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="a717e-115">変換前</span><span class="sxs-lookup"><span data-stu-id="a717e-115">From</span></span>|<span data-ttu-id="a717e-116">目的</span><span class="sxs-lookup"><span data-stu-id="a717e-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="a717e-117">任意のポインター型</span><span class="sxs-lookup"><span data-stu-id="a717e-117">Any pointer type</span></span>|<span data-ttu-id="a717e-118">その他のポインター型</span><span class="sxs-lookup"><span data-stu-id="a717e-118">Any other pointer type</span></span>|  
|<span data-ttu-id="a717e-119">sbyte、byte、short、ushort、int、uint、long または ulong</span><span class="sxs-lookup"><span data-stu-id="a717e-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="a717e-120">任意のポインター型</span><span class="sxs-lookup"><span data-stu-id="a717e-120">Any pointer type</span></span>|  
|<span data-ttu-id="a717e-121">任意のポインター型</span><span class="sxs-lookup"><span data-stu-id="a717e-121">Any pointer type</span></span>|<span data-ttu-id="a717e-122">sbyte、byte、short、ushort、int、uint、long または ulong</span><span class="sxs-lookup"><span data-stu-id="a717e-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a717e-123">例</span><span class="sxs-lookup"><span data-stu-id="a717e-123">Example</span></span>  
 <span data-ttu-id="a717e-124">次の例では、`int` へのポインターは `byte` へのポインターに変換されます。</span><span class="sxs-lookup"><span data-stu-id="a717e-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="a717e-125">ポインターは、変数の最下位バイト アドレスを指すことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a717e-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="a717e-126">`int` のサイズ (4 バイト) まで結果を連続してインクリメントする場合、変数の残りのバイトを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="a717e-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a717e-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="a717e-127">See Also</span></span>  
 [<span data-ttu-id="a717e-128">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="a717e-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a717e-129">ポインター式</span><span class="sxs-lookup"><span data-stu-id="a717e-129">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="a717e-130">ポインター型</span><span class="sxs-lookup"><span data-stu-id="a717e-130">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="a717e-131">型</span><span class="sxs-lookup"><span data-stu-id="a717e-131">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="a717e-132">unsafe</span><span class="sxs-lookup"><span data-stu-id="a717e-132">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="a717e-133">fixed ステートメント</span><span class="sxs-lookup"><span data-stu-id="a717e-133">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="a717e-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="a717e-134">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
