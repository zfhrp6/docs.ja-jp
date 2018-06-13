---
title: ポインター変換 (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: e0c3a409d76468a6e214a96e8bb326a9d906fe18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322693"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="fdb16-102">ポインター変換 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="fdb16-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="fdb16-103">定義済みの暗黙的なポインター変換を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="fdb16-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="fdb16-104">暗黙的な変換は、メソッドの呼び出しや代入ステートメントなど、多くの状況で発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="fdb16-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="fdb16-105">暗黙的なポインター変換</span><span class="sxs-lookup"><span data-stu-id="fdb16-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="fdb16-106">From</span><span class="sxs-lookup"><span data-stu-id="fdb16-106">From</span></span>|<span data-ttu-id="fdb16-107">終了</span><span class="sxs-lookup"><span data-stu-id="fdb16-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="fdb16-108">任意のポインター型</span><span class="sxs-lookup"><span data-stu-id="fdb16-108">Any pointer type</span></span>|<span data-ttu-id="fdb16-109">void\*</span><span class="sxs-lookup"><span data-stu-id="fdb16-109">void\*</span></span>|  
|<span data-ttu-id="fdb16-110">null</span><span class="sxs-lookup"><span data-stu-id="fdb16-110">null</span></span>|<span data-ttu-id="fdb16-111">任意のポインター型</span><span class="sxs-lookup"><span data-stu-id="fdb16-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="fdb16-112">明示的なポインター変換は、暗黙的な変換がない場合に、キャスト式を使用して、変換を実行するために使用します。</span><span class="sxs-lookup"><span data-stu-id="fdb16-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="fdb16-113">次の表はこの変換についてまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="fdb16-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="fdb16-114">明示的なポインター変換</span><span class="sxs-lookup"><span data-stu-id="fdb16-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="fdb16-115">From</span><span class="sxs-lookup"><span data-stu-id="fdb16-115">From</span></span>|<span data-ttu-id="fdb16-116">終了</span><span class="sxs-lookup"><span data-stu-id="fdb16-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="fdb16-117">任意のポインター型</span><span class="sxs-lookup"><span data-stu-id="fdb16-117">Any pointer type</span></span>|<span data-ttu-id="fdb16-118">その他のポインター型</span><span class="sxs-lookup"><span data-stu-id="fdb16-118">Any other pointer type</span></span>|  
|<span data-ttu-id="fdb16-119">sbyte、byte、short、ushort、int、uint、long または ulong</span><span class="sxs-lookup"><span data-stu-id="fdb16-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="fdb16-120">任意のポインター型</span><span class="sxs-lookup"><span data-stu-id="fdb16-120">Any pointer type</span></span>|  
|<span data-ttu-id="fdb16-121">任意のポインター型</span><span class="sxs-lookup"><span data-stu-id="fdb16-121">Any pointer type</span></span>|<span data-ttu-id="fdb16-122">sbyte、byte、short、ushort、int、uint、long または ulong</span><span class="sxs-lookup"><span data-stu-id="fdb16-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fdb16-123">例</span><span class="sxs-lookup"><span data-stu-id="fdb16-123">Example</span></span>  
 <span data-ttu-id="fdb16-124">次の例では、`int` へのポインターは `byte` へのポインターに変換されます。</span><span class="sxs-lookup"><span data-stu-id="fdb16-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="fdb16-125">ポインターは、変数の最下位バイト アドレスを指すことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="fdb16-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="fdb16-126">`int` のサイズ (4 バイト) まで結果を連続してインクリメントする場合、変数の残りのバイトを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="fdb16-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="fdb16-127">参照</span><span class="sxs-lookup"><span data-stu-id="fdb16-127">See Also</span></span>  
 [<span data-ttu-id="fdb16-128">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="fdb16-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fdb16-129">ポインター式</span><span class="sxs-lookup"><span data-stu-id="fdb16-129">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="fdb16-130">ポインター型</span><span class="sxs-lookup"><span data-stu-id="fdb16-130">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="fdb16-131">型</span><span class="sxs-lookup"><span data-stu-id="fdb16-131">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="fdb16-132">unsafe</span><span class="sxs-lookup"><span data-stu-id="fdb16-132">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="fdb16-133">fixed ステートメント</span><span class="sxs-lookup"><span data-stu-id="fdb16-133">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="fdb16-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="fdb16-134">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
