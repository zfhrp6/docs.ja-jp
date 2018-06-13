---
title: '方法: ToString メソッドをオーバーライドする (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 86394f5fed55f57df8928648548fcfca117b00d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330708"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a><span data-ttu-id="c631c-102">方法: ToString メソッドをオーバーライドする (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="c631c-102">How to: Override the ToString Method (C# Programming Guide)</span></span>
<span data-ttu-id="c631c-103">C# では、すべてのクラスまたは構造体が、暗黙的に <xref:System.Object> クラスを継承します。</span><span class="sxs-lookup"><span data-stu-id="c631c-103">Every class or struct in C# implicitly inherits the <xref:System.Object> class.</span></span> <span data-ttu-id="c631c-104">そのため、C# のすべてのオブジェクトが <xref:System.Object.ToString%2A> メソッドを取得し、そのオブジェクトの文字列表現を返します。</span><span class="sxs-lookup"><span data-stu-id="c631c-104">Therefore, every object in C# gets the <xref:System.Object.ToString%2A> method, which returns a string representation of that object.</span></span> <span data-ttu-id="c631c-105">たとえば、`int` 型の変数はすべて `ToString` メソッドを持ち、次のようにその変数の内容を文字列として返すことができます。</span><span class="sxs-lookup"><span data-stu-id="c631c-105">For example, all variables of type `int` have a `ToString` method, which enables them to return their contents as a string:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_1.cs)]  
  
 <span data-ttu-id="c631c-106">カスタムのクラスまたは構造体を作成するときは、クライアント コードにカスタム型の情報を提供するため、<xref:System.Object.ToString%2A> メソッドをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c631c-106">When you create a custom class or struct, you should override the <xref:System.Object.ToString%2A> method in order to provide information about your type to client code.</span></span>  
  
 <span data-ttu-id="c631c-107">`ToString` メソッドで書式設定文字列やその他のカスタム形式を使用する方法については、「[型の書式設定](../../../standard/base-types/formatting-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c631c-107">For information about how to use format strings and other types of custom formatting with the `ToString` method, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c631c-108">このメソッドを使用して提供する情報を決定するときは、作成したクラスまたは構造体が信頼関係のないコードによって使用されるかどうかを考慮します。</span><span class="sxs-lookup"><span data-stu-id="c631c-108">When you decide what information to provide through this method, consider whether your class or struct will ever be used by untrusted code.</span></span> <span data-ttu-id="c631c-109">悪意があるコードで利用される可能性がある情報を提供しないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="c631c-109">Be careful to ensure that you do not provide any information that could be exploited by malicious code.</span></span>  
  
### <a name="to-override-the-tostring-method-in-your-class-or-struct"></a><span data-ttu-id="c631c-110">クラスまたは構造体内の ToString メソッドをオーバーライドするには</span><span class="sxs-lookup"><span data-stu-id="c631c-110">To override the ToString method in your class or struct</span></span>  
  
1.  <span data-ttu-id="c631c-111">次の修飾子および戻り値の値を指定して、`ToString` メソッドを宣言します。</span><span class="sxs-lookup"><span data-stu-id="c631c-111">Declare a `ToString` method with the following modifiers and return type:</span></span>  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2.  <span data-ttu-id="c631c-112">文字列を返すように、メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="c631c-112">Implement the method so that it returns a string.</span></span>  
  
     <span data-ttu-id="c631c-113">次の例では、特定のクラス インスタンスに固有のデータに加えて、クラス名も返されます。</span><span class="sxs-lookup"><span data-stu-id="c631c-113">The following example returns the name of the class in addition to the data specific to a particular instance of the class.</span></span>  
  
     [!code-csharp[csProgGuideInheritance#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_2.cs)]  
  
     <span data-ttu-id="c631c-114">`ToString` メソッドをテストする方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="c631c-114">You can test the `ToString` method as shown in the following code example:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c631c-115">参照</span><span class="sxs-lookup"><span data-stu-id="c631c-115">See Also</span></span>  
 <xref:System.IFormattable>  
 [<span data-ttu-id="c631c-116">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="c631c-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c631c-117">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="c631c-117">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="c631c-118">文字列</span><span class="sxs-lookup"><span data-stu-id="c631c-118">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="c631c-119">string</span><span class="sxs-lookup"><span data-stu-id="c631c-119">string</span></span>](../../../csharp/language-reference/keywords/string.md)  
 [<span data-ttu-id="c631c-120">new</span><span class="sxs-lookup"><span data-stu-id="c631c-120">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
 [<span data-ttu-id="c631c-121">override</span><span class="sxs-lookup"><span data-stu-id="c631c-121">override</span></span>](../../../csharp/language-reference/keywords/override.md)  
 [<span data-ttu-id="c631c-122">virtual</span><span class="sxs-lookup"><span data-stu-id="c631c-122">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)  
 [<span data-ttu-id="c631c-123">型の書式設定</span><span class="sxs-lookup"><span data-stu-id="c631c-123">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
