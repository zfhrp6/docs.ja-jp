---
title: "方法: ToString メソッドをオーバーライドする (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5b0f7bf35e5bd565e0bfa46fe91cf86aedcd2d8e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a><span data-ttu-id="3d0a8-102">方法: ToString メソッドをオーバーライドする (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="3d0a8-102">How to: Override the ToString Method (C# Programming Guide)</span></span>
<span data-ttu-id="3d0a8-103">C# では、すべてのクラスまたは構造体が、暗黙的に <xref:System.Object> クラスを継承します。</span><span class="sxs-lookup"><span data-stu-id="3d0a8-103">Every class or struct in C# implicitly inherits the <xref:System.Object> class.</span></span> <span data-ttu-id="3d0a8-104">そのため、C# のすべてのオブジェクトが <xref:System.Object.ToString%2A> メソッドを取得し、そのオブジェクトの文字列表現を返します。</span><span class="sxs-lookup"><span data-stu-id="3d0a8-104">Therefore, every object in C# gets the <xref:System.Object.ToString%2A> method, which returns a string representation of that object.</span></span> <span data-ttu-id="3d0a8-105">たとえば、`int` 型の変数はすべて `ToString` メソッドを持ち、次のようにその変数の内容を文字列として返すことができます。</span><span class="sxs-lookup"><span data-stu-id="3d0a8-105">For example, all variables of type `int` have a `ToString` method, which enables them to return their contents as a string:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_1.cs)]  
  
 <span data-ttu-id="3d0a8-106">カスタムのクラスまたは構造体を作成するときは、クライアント コードにカスタム型の情報を提供するため、<xref:System.Object.ToString%2A> メソッドをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d0a8-106">When you create a custom class or struct, you should override the <xref:System.Object.ToString%2A> method in order to provide information about your type to client code.</span></span>  
  
 <span data-ttu-id="3d0a8-107">`ToString` メソッドで書式設定文字列やその他のカスタム形式を使用する方法については、「[型の書式設定](../../../standard/base-types/formatting-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d0a8-107">For information about how to use format strings and other types of custom formatting with the `ToString` method, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3d0a8-108">このメソッドを使用して提供する情報を決定するときは、作成したクラスまたは構造体が信頼関係のないコードによって使用されるかどうかを考慮します。</span><span class="sxs-lookup"><span data-stu-id="3d0a8-108">When you decide what information to provide through this method, consider whether your class or struct will ever be used by untrusted code.</span></span> <span data-ttu-id="3d0a8-109">悪意があるコードで利用される可能性がある情報を提供しないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="3d0a8-109">Be careful to ensure that you do not provide any information that could be exploited by malicious code.</span></span>  
  
### <a name="to-override-the-tostring-method-in-your-class-or-struct"></a><span data-ttu-id="3d0a8-110">クラスまたは構造体内の ToString メソッドをオーバーライドするには</span><span class="sxs-lookup"><span data-stu-id="3d0a8-110">To override the ToString method in your class or struct</span></span>  
  
1.  <span data-ttu-id="3d0a8-111">次の修飾子および戻り値の値を指定して、`ToString` メソッドを宣言します。</span><span class="sxs-lookup"><span data-stu-id="3d0a8-111">Declare a `ToString` method with the following modifiers and return type:</span></span>  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2.  <span data-ttu-id="3d0a8-112">文字列を返すように、メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="3d0a8-112">Implement the method so that it returns a string.</span></span>  
  
     <span data-ttu-id="3d0a8-113">次の例では、特定のクラス インスタンスに固有のデータに加えて、クラス名も返されます。</span><span class="sxs-lookup"><span data-stu-id="3d0a8-113">The following example returns the name of the class in addition to the data specific to a particular instance of the class.</span></span>  
  
     [!code-csharp[csProgGuideInheritance#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_2.cs)]  
  
     <span data-ttu-id="3d0a8-114">`ToString` メソッドをテストする方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="3d0a8-114">You can test the `ToString` method as shown in the following code example:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="3d0a8-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d0a8-115">See Also</span></span>  
 <xref:System.IFormattable>  
 [<span data-ttu-id="3d0a8-116">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="3d0a8-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3d0a8-117">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="3d0a8-117">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="3d0a8-118">文字列</span><span class="sxs-lookup"><span data-stu-id="3d0a8-118">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="3d0a8-119">string</span><span class="sxs-lookup"><span data-stu-id="3d0a8-119">string</span></span>](../../../csharp/language-reference/keywords/string.md)  
 [<span data-ttu-id="3d0a8-120">new</span><span class="sxs-lookup"><span data-stu-id="3d0a8-120">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
 [<span data-ttu-id="3d0a8-121">override</span><span class="sxs-lookup"><span data-stu-id="3d0a8-121">override</span></span>](../../../csharp/language-reference/keywords/override.md)  
 [<span data-ttu-id="3d0a8-122">virtual</span><span class="sxs-lookup"><span data-stu-id="3d0a8-122">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)  
 [<span data-ttu-id="3d0a8-123">型の書式設定</span><span class="sxs-lookup"><span data-stu-id="3d0a8-123">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
