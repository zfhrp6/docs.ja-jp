---
title: "方法: インターフェイス メンバーを明示的に実装する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
caps.latest.revision: 16
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
ms.openlocfilehash: 88b96c15f724ee5961c72917308138a045988225
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="c59d2-102">方法: インターフェイス メンバーを明示的に実装する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="c59d2-102">How to: Explicitly Implement Interface Members (C# Programming Guide)</span></span>
<span data-ttu-id="c59d2-103">この例では[インターフェイス](../../../csharp/language-reference/keywords/interface.md)、`IDimensions`、およびクラス `Box` を宣言します。これは、インターフェイス メンバーの `getLength` と `getWidth` を明示的に実装します。</span><span class="sxs-lookup"><span data-stu-id="c59d2-103">This example declares an [interface](../../../csharp/language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `getLength` and `getWidth`.</span></span> <span data-ttu-id="c59d2-104">メンバーには、インターフェイス インスタンス `dimensions` を介してアクセスします。</span><span class="sxs-lookup"><span data-stu-id="c59d2-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c59d2-105">例</span><span class="sxs-lookup"><span data-stu-id="c59d2-105">Example</span></span>  
 <span data-ttu-id="c59d2-106">[!code-cs[csProgGuideInheritance#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c59d2-106">[!code-cs[csProgGuideInheritance#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_1.cs)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c59d2-107">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="c59d2-107">Robust Programming</span></span>  
  
-   <span data-ttu-id="c59d2-108">`Main` メソッドでは、次の行はコメントアウトされます。これらの行でコンパイル エラーが発生するためです。</span><span class="sxs-lookup"><span data-stu-id="c59d2-108">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="c59d2-109">明示的に実装されるインターフェイス メンバーに、[クラス](../../../csharp/language-reference/keywords/class.md) インスタンスからアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="c59d2-109">An interface member that is explicitly implemented cannot be accessed from a [class](../../../csharp/language-reference/keywords/class.md) instance:</span></span>  
  
     <span data-ttu-id="c59d2-110">[!code-cs[csProgGuideInheritance#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="c59d2-110">[!code-cs[csProgGuideInheritance#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_2.cs)]</span></span>  
  
-   <span data-ttu-id="c59d2-111">`Main` メソッドの以下の行では、メソッドがインターフェイスのインスタンスから呼び出されるため、ボックスのサイズを正常に出力できます。</span><span class="sxs-lookup"><span data-stu-id="c59d2-111">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     <span data-ttu-id="c59d2-112">[!code-cs[csProgGuideInheritance#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="c59d2-112">[!code-cs[csProgGuideInheritance#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_3.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c59d2-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="c59d2-113">See Also</span></span>  
 <span data-ttu-id="c59d2-114">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c59d2-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="c59d2-115">[クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="c59d2-115">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="c59d2-116">[インターフェイス](../../../csharp/programming-guide/interfaces/index.md) </span><span class="sxs-lookup"><span data-stu-id="c59d2-116">[Interfaces](../../../csharp/programming-guide/interfaces/index.md) </span></span>  
 [<span data-ttu-id="c59d2-117">方法: 2 つのインターフェイスのメンバーを明示的に実装する</span><span class="sxs-lookup"><span data-stu-id="c59d2-117">How to: Explicitly Implement Members of Two Interfaces</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)

