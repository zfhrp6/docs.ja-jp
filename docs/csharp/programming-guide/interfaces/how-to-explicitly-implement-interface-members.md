---
title: '方法: インターフェイス メンバーを明示的に実装する (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 5f7ae6bae46cdf6596b206abbdeeb94b5c21a13f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332187"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="423e7-102">方法: インターフェイス メンバーを明示的に実装する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="423e7-102">How to: Explicitly Implement Interface Members (C# Programming Guide)</span></span>
<span data-ttu-id="423e7-103">この例では[インターフェイス](../../../csharp/language-reference/keywords/interface.md)、`IDimensions`、およびクラス `Box` を宣言します。これは、インターフェイス メンバーの `getLength` と `getWidth` を明示的に実装します。</span><span class="sxs-lookup"><span data-stu-id="423e7-103">This example declares an [interface](../../../csharp/language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `getLength` and `getWidth`.</span></span> <span data-ttu-id="423e7-104">メンバーには、インターフェイス インスタンス `dimensions` を介してアクセスします。</span><span class="sxs-lookup"><span data-stu-id="423e7-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="423e7-105">例</span><span class="sxs-lookup"><span data-stu-id="423e7-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="423e7-106">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="423e7-106">Robust Programming</span></span>  
  
-   <span data-ttu-id="423e7-107">`Main` メソッドでは、次の行はコメントアウトされます。これらの行でコンパイル エラーが発生するためです。</span><span class="sxs-lookup"><span data-stu-id="423e7-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="423e7-108">明示的に実装されるインターフェイス メンバーに、[クラス](../../../csharp/language-reference/keywords/class.md) インスタンスからアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="423e7-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../../csharp/language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_2.cs)]  
  
-   <span data-ttu-id="423e7-109">`Main` メソッドの以下の行では、メソッドがインターフェイスのインスタンスから呼び出されるため、ボックスのサイズを正常に出力できます。</span><span class="sxs-lookup"><span data-stu-id="423e7-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="423e7-110">参照</span><span class="sxs-lookup"><span data-stu-id="423e7-110">See Also</span></span>  
 [<span data-ttu-id="423e7-111">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="423e7-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="423e7-112">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="423e7-112">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="423e7-113">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="423e7-113">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="423e7-114">方法: 2 つのインターフェイスのメンバーを明示的に実装する</span><span class="sxs-lookup"><span data-stu-id="423e7-114">How to: Explicitly Implement Members of Two Interfaces</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)
