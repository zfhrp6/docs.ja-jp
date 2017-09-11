---
title: "明示的なインターフェイスの実装 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6baf985e8031e1e859d20570168222ca8f368eff
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="d06ec-102">明示的なインターフェイスの実装 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="d06ec-102">Explicit Interface Implementation (C# Programming Guide)</span></span>
<span data-ttu-id="d06ec-103">シグネチャが同じメンバーが含まれる 2 つのインターフェイスをある[クラス](../../../csharp/language-reference/keywords/class.md)が実装する場合、そのクラスでそのメンバーを実装することで、実装としてそのメンバーが両方のインターフェイスで使用されます。</span><span class="sxs-lookup"><span data-stu-id="d06ec-103">If a [class](../../../csharp/language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="d06ec-104">次の例では、`Paint` のすべての呼び出しで同じメソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d06ec-104">In the following example, all the calls to `Paint` invoke the same method.</span></span>  
  
 <span data-ttu-id="d06ec-105">[!code-cs[csProgGuideInheritance#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d06ec-105">[!code-cs[csProgGuideInheritance#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_1.cs)]</span></span>  
  
 <span data-ttu-id="d06ec-106">ただし、2 つの[インターフェイス](../../../csharp/language-reference/keywords/interface.md) メンバーが同じ関数を実行しない場合、一方または両方のインターフェイスが間違って実装される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d06ec-106">If the two [interface](../../../csharp/language-reference/keywords/interface.md) members do not perform the same function, however, this can lead to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="d06ec-107">インターフェイス メンバーは明示的に実装できます。そのインターフェイス経由でのみ呼び出され、そのインターフェイスに固有となるクラス メンバーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d06ec-107">It is possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="d06ec-108">この実装は、インターフェイスの名前とピリオドを利用してクラス メンバーに名前を付けることで行われます。</span><span class="sxs-lookup"><span data-stu-id="d06ec-108">This is accomplished by naming the class member with the name of the interface and a period.</span></span> <span data-ttu-id="d06ec-109">例:</span><span class="sxs-lookup"><span data-stu-id="d06ec-109">For example:</span></span>  
  
 <span data-ttu-id="d06ec-110">[!code-cs[csProgGuideInheritance#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="d06ec-110">[!code-cs[csProgGuideInheritance#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_2.cs)]</span></span>  
  
 <span data-ttu-id="d06ec-111">クラス メンバー `IControl.Paint` は `IControl` インターフェイス経由でのみ利用できます。`ISurface.Paint` は `ISurface` 経由でのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="d06ec-111">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="d06ec-112">いずれのメソッド実装も個別であり、クラスで直接利用できません。</span><span class="sxs-lookup"><span data-stu-id="d06ec-112">Both method implementations are separate, and neither is available directly on the class.</span></span> <span data-ttu-id="d06ec-113">例:</span><span class="sxs-lookup"><span data-stu-id="d06ec-113">For example:</span></span>  
  
 <span data-ttu-id="d06ec-114">[!code-cs[csProgGuideInheritance#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="d06ec-114">[!code-cs[csProgGuideInheritance#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_3.cs)]</span></span>  
  
 <span data-ttu-id="d06ec-115">2 つのインターフェイスで、それぞれが同じ名前の別のメンバー (プロパティやメソッドなど) を宣言するような場合の解決には、明示的な実装も利用されます。</span><span class="sxs-lookup"><span data-stu-id="d06ec-115">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method:</span></span>  
  
 <span data-ttu-id="d06ec-116">[!code-cs[csProgGuideInheritance#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="d06ec-116">[!code-cs[csProgGuideInheritance#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_4.cs)]</span></span>  
  
 <span data-ttu-id="d06ec-117">両方のインターフェイスを実装するには、コンパイラ エラーを回避するために、クラスはプロパティ P、メソッド P、または両方に明示的な実装を利用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d06ec-117">To implement both interfaces, a class has to use explicit implementation either for the property P, or the method P, or both, to avoid a compiler error.</span></span> <span data-ttu-id="d06ec-118">例:</span><span class="sxs-lookup"><span data-stu-id="d06ec-118">For example:</span></span>  
  
 <span data-ttu-id="d06ec-119">[!code-cs[csProgGuideInheritance#43](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="d06ec-119">[!code-cs[csProgGuideInheritance#43](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_5.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d06ec-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="d06ec-120">See Also</span></span>  
 <span data-ttu-id="d06ec-121">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d06ec-121">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="d06ec-122">[クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="d06ec-122">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="d06ec-123">[インターフェイス](../../../csharp/programming-guide/interfaces/index.md) </span><span class="sxs-lookup"><span data-stu-id="d06ec-123">[Interfaces](../../../csharp/programming-guide/interfaces/index.md) </span></span>  
 [<span data-ttu-id="d06ec-124">継承</span><span class="sxs-lookup"><span data-stu-id="d06ec-124">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)

