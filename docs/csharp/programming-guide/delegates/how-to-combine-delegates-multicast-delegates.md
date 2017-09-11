---
title: "方法 : デリゲートを結合する (マルチキャスト デリゲート) (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
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
ms.openlocfilehash: 617af10d3fb5f9371d5893b87a91a48639d44a53
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="96da6-102">方法 : デリゲートを結合する (マルチキャスト デリゲート) (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="96da6-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="96da6-103">ここでは、マルチキャスト デリゲートを作成する例について説明します。</span><span class="sxs-lookup"><span data-stu-id="96da6-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="96da6-104">[デリゲート](../../../csharp/language-reference/keywords/delegate.md) オブジェクトの便利な性質の 1 つは、`+` 演算子を使用して、複数のオブジェクトを 1 つのデリゲート インスタンスに割り当てられることです。</span><span class="sxs-lookup"><span data-stu-id="96da6-104">A useful property of [delegate](../../../csharp/language-reference/keywords/delegate.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="96da6-105">マルチキャスト デリゲートには、割り当てられたデリゲートの一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="96da6-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="96da6-106">マルチキャスト デリゲートを呼び出すと、一覧内のデリゲートが順に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="96da6-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="96da6-107">結合できるのは、同じ型のデリゲートのみです。</span><span class="sxs-lookup"><span data-stu-id="96da6-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="96da6-108">`-` 演算子を使用して、マルチキャスト デリゲートからコンポーネント デリゲートを削除することができます。</span><span class="sxs-lookup"><span data-stu-id="96da6-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96da6-109">例</span><span class="sxs-lookup"><span data-stu-id="96da6-109">Example</span></span>  
 <span data-ttu-id="96da6-110">[!code-cs[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="96da6-110">[!code-cs[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96da6-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="96da6-111">See Also</span></span>  
 <span data-ttu-id="96da6-112"><xref:System.MulticastDelegate></span><span class="sxs-lookup"><span data-stu-id="96da6-112"><xref:System.MulticastDelegate></span></span>   
 <span data-ttu-id="96da6-113">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="96da6-113">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="96da6-114">イベント</span><span class="sxs-lookup"><span data-stu-id="96da6-114">Events</span></span>](../../../csharp/programming-guide/events/index.md)

