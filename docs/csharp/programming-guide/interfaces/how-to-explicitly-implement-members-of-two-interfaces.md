---
title: "方法: 2 つのインターフェイスのメンバーを明示的に実装する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
caps.latest.revision: 15
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
ms.openlocfilehash: 1446233793e3fd61f09d7da99f4f68cb7b3eabb8
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="f98ae-102">方法: 2 つのインターフェイスのメンバーを明示的に実装する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="f98ae-102">How to: Explicitly Implement Members of Two Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="f98ae-103">明示的な[インターフェイス](../../../csharp/language-reference/keywords/interface.md)実装では、プログラマは、メンバー名が同じ 2 つのインターフェイスを実装し、各インターフェイス メンバーに別の実装を与えることもできます。</span><span class="sxs-lookup"><span data-stu-id="f98ae-103">Explicit [interface](../../../csharp/language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="f98ae-104">この例では、メートル法とヤード ポンド法の両方の単位で、ボックスのサイズを表示します。</span><span class="sxs-lookup"><span data-stu-id="f98ae-104">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="f98ae-105">Box [クラス](../../../csharp/language-reference/keywords/class.md)では、異なる測定システムを表す IEnglishDimensions および IMetricDimensions という 2 つのインターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="f98ae-105">The Box [class](../../../csharp/language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="f98ae-106">両方のインターフェイスは Length および Width という同じメンバー名を持ちます。</span><span class="sxs-lookup"><span data-stu-id="f98ae-106">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f98ae-107">例</span><span class="sxs-lookup"><span data-stu-id="f98ae-107">Example</span></span>  
 <span data-ttu-id="f98ae-108">[!code-cs[csProgGuideInheritance#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f98ae-108">[!code-cs[csProgGuideInheritance#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_1.cs)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f98ae-109">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="f98ae-109">Robust Programming</span></span>  
 <span data-ttu-id="f98ae-110">ヤード ポンド単位で既定の測定を行う場合は、通常どおり Length と Width のメソッドを実装し、IMetricDimensions インターフェイスから Length と Width のメソッドを明示的に実装します。</span><span class="sxs-lookup"><span data-stu-id="f98ae-110">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 <span data-ttu-id="f98ae-111">[!code-cs[csProgGuideInheritance#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="f98ae-111">[!code-cs[csProgGuideInheritance#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_2.cs)]</span></span>  
  
 <span data-ttu-id="f98ae-112">この場合、ヤード ポンド単位にはクラス インスタンスからアクセスでき、メートル単位にはインターフェイス インスタンスからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f98ae-112">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 <span data-ttu-id="f98ae-113">[!code-cs[csProgGuideInheritance#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="f98ae-113">[!code-cs[csProgGuideInheritance#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_3.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f98ae-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="f98ae-114">See Also</span></span>  
 <span data-ttu-id="f98ae-115">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f98ae-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f98ae-116">[クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="f98ae-116">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="f98ae-117">[インターフェイス](../../../csharp/programming-guide/interfaces/index.md) </span><span class="sxs-lookup"><span data-stu-id="f98ae-117">[Interfaces](../../../csharp/programming-guide/interfaces/index.md) </span></span>  
 [<span data-ttu-id="f98ae-118">方法: インターフェイス メンバーを明示的に実装する</span><span class="sxs-lookup"><span data-stu-id="f98ae-118">How to: Explicitly Implement Interface Members</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)

