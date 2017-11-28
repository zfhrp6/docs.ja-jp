---
title: "方法 : デリゲートを結合する (マルチキャスト デリゲート) (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ddb4ecbbf456179e91aa0003c2dc5653f153411f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="c1a91-102">方法 : デリゲートを結合する (マルチキャスト デリゲート) (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="c1a91-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="c1a91-103">ここでは、マルチキャスト デリゲートを作成する例について説明します。</span><span class="sxs-lookup"><span data-stu-id="c1a91-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="c1a91-104">[デリゲート](../../../csharp/language-reference/keywords/delegate.md) オブジェクトの便利な性質の 1 つは、`+` 演算子を使用して、複数のオブジェクトを 1 つのデリゲート インスタンスに割り当てられることです。</span><span class="sxs-lookup"><span data-stu-id="c1a91-104">A useful property of [delegate](../../../csharp/language-reference/keywords/delegate.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="c1a91-105">マルチキャスト デリゲートには、割り当てられたデリゲートの一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c1a91-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="c1a91-106">マルチキャスト デリゲートを呼び出すと、一覧内のデリゲートが順に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c1a91-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="c1a91-107">結合できるのは、同じ型のデリゲートのみです。</span><span class="sxs-lookup"><span data-stu-id="c1a91-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="c1a91-108">`-` 演算子を使用して、マルチキャスト デリゲートからコンポーネント デリゲートを削除することができます。</span><span class="sxs-lookup"><span data-stu-id="c1a91-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1a91-109">例</span><span class="sxs-lookup"><span data-stu-id="c1a91-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c1a91-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1a91-110">See Also</span></span>  
 <xref:System.MulticastDelegate>  
 [<span data-ttu-id="c1a91-111">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="c1a91-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c1a91-112">イベント</span><span class="sxs-lookup"><span data-stu-id="c1a91-112">Events</span></span>](../../../csharp/programming-guide/events/index.md)
