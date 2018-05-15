---
title: '方法 : ディクショナリを使用してイベント インスタンスを格納する (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: 97a7b0f168e4a1c81ec396f42b731dabb45b3516
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a><span data-ttu-id="51300-102">方法 : ディクショナリを使用してイベント インスタンスを格納する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="51300-102">How to: Use a Dictionary to Store Event Instances (C# Programming Guide)</span></span>
<span data-ttu-id="51300-103">多数のイベントを公開する場合に `accessor-declarations` を使用すると、各イベントにフィールドを割り当てる代わりにディクショナリを使用してイベント インスタンスを格納できます。</span><span class="sxs-lookup"><span data-stu-id="51300-103">One use for `accessor-declarations` is to expose many events without allocating a field for each event, but instead using a Dictionary to store the event instances.</span></span> <span data-ttu-id="51300-104">これが便利なのは、多数のイベントがあるものの、それらのほとんどが実装されそうもない場合だけです。</span><span class="sxs-lookup"><span data-stu-id="51300-104">This is only useful if you have many events, but you expect most of the events will not be implemented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51300-105">例</span><span class="sxs-lookup"><span data-stu-id="51300-105">Example</span></span>  
 [!code-csharp[csProgGuideEvents#9](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-use-a-dictionary-to-store-event-instances_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="51300-106">参照</span><span class="sxs-lookup"><span data-stu-id="51300-106">See Also</span></span>  
 [<span data-ttu-id="51300-107">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="51300-107">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="51300-108">イベント</span><span class="sxs-lookup"><span data-stu-id="51300-108">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="51300-109">デリゲート</span><span class="sxs-lookup"><span data-stu-id="51300-109">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
