---
title: '方法: 2 つのインターフェイスのメンバーを明示的に実装する (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: c73089fdbf1350c1aff68ac3e8e78be00e21b931
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339041"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="575d2-102">方法: 2 つのインターフェイスのメンバーを明示的に実装する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="575d2-102">How to: Explicitly Implement Members of Two Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="575d2-103">明示的な[インターフェイス](../../../csharp/language-reference/keywords/interface.md)実装では、プログラマは、メンバー名が同じ 2 つのインターフェイスを実装し、各インターフェイス メンバーに別の実装を与えることもできます。</span><span class="sxs-lookup"><span data-stu-id="575d2-103">Explicit [interface](../../../csharp/language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="575d2-104">この例では、メートル法とヤード ポンド法の両方の単位で、ボックスのサイズを表示します。</span><span class="sxs-lookup"><span data-stu-id="575d2-104">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="575d2-105">Box [クラス](../../../csharp/language-reference/keywords/class.md)では、異なる測定システムを表す IEnglishDimensions および IMetricDimensions という 2 つのインターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="575d2-105">The Box [class](../../../csharp/language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="575d2-106">両方のインターフェイスは Length および Width という同じメンバー名を持ちます。</span><span class="sxs-lookup"><span data-stu-id="575d2-106">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="575d2-107">例</span><span class="sxs-lookup"><span data-stu-id="575d2-107">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="575d2-108">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="575d2-108">Robust Programming</span></span>  
 <span data-ttu-id="575d2-109">ヤード ポンド単位で既定の測定を行う場合は、通常どおり Length と Width のメソッドを実装し、IMetricDimensions インターフェイスから Length と Width のメソッドを明示的に実装します。</span><span class="sxs-lookup"><span data-stu-id="575d2-109">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_2.cs)]  
  
 <span data-ttu-id="575d2-110">この場合、ヤード ポンド単位にはクラス インスタンスからアクセスでき、メートル単位にはインターフェイス インスタンスからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="575d2-110">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="575d2-111">参照</span><span class="sxs-lookup"><span data-stu-id="575d2-111">See Also</span></span>  
 [<span data-ttu-id="575d2-112">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="575d2-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="575d2-113">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="575d2-113">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="575d2-114">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="575d2-114">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="575d2-115">方法: インターフェイス メンバーを明示的に実装する</span><span class="sxs-lookup"><span data-stu-id="575d2-115">How to: Explicitly Implement Interface Members</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)
