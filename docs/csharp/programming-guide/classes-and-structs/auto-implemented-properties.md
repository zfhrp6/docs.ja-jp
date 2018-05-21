---
title: 自動実装するプロパティ (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 756e235dacc3fcb2bf741d1d426e8dfcb53bf19b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="35ea2-102">自動実装するプロパティ (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="35ea2-102">Auto-Implemented Properties (C# Programming Guide)</span></span>
<span data-ttu-id="35ea2-103">C# 3.0 以降では、自動実装プロパティを使用することで、プロパティ アクセサーに追加のロジックが必要ない場合は、プロパティをより簡潔に宣言できます。</span><span class="sxs-lookup"><span data-stu-id="35ea2-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="35ea2-104">これにより、クライアント コードでオブジェクトを作成することも可能になります。</span><span class="sxs-lookup"><span data-stu-id="35ea2-104">They also enable client code to create objects.</span></span> <span data-ttu-id="35ea2-105">次の例に示すようにプロパティを宣言する場合、コンパイラによって、プロパティの `get` および `set` アクセサーを介してのみアクセスできる、プライベートの匿名バッキング フィールドが作成されます。</span><span class="sxs-lookup"><span data-stu-id="35ea2-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35ea2-106">例</span><span class="sxs-lookup"><span data-stu-id="35ea2-106">Example</span></span>  
 <span data-ttu-id="35ea2-107">次の例に、自動実装プロパティを持つ簡単なクラスを示します。</span><span class="sxs-lookup"><span data-stu-id="35ea2-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/auto-implemented-properties_1.cs)]  
  
 <span data-ttu-id="35ea2-108">C# 6 以降では、フィールドと同様に自動実装プロパティを初期化することができます。</span><span class="sxs-lookup"><span data-stu-id="35ea2-108">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 <span data-ttu-id="35ea2-109">前の例に示したクラスは、変更可能です。</span><span class="sxs-lookup"><span data-stu-id="35ea2-109">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="35ea2-110">クライアント コードは、オブジェクト内の値を作成後に変更できます。</span><span class="sxs-lookup"><span data-stu-id="35ea2-110">Client code can change the values in objects after they are created.</span></span> <span data-ttu-id="35ea2-111">データだけでなく、重要な動作 (メソッド) も含まれる複雑なクラスでは、多くの場合、パブリック プロパティが必要です。</span><span class="sxs-lookup"><span data-stu-id="35ea2-111">In complex classes that contain significant behavior (methods) as well as data, it is often necessary to have public properties.</span></span> <span data-ttu-id="35ea2-112">ただし、値 (データ) のセットをカプセル化しているだけで、動作をほとんど、またはまったく含まない小さなクラスや構造体の場合は、set アクセサーを [private](../../../csharp/language-reference/keywords/private.md) (コンシューマーからは変更できない) として宣言するか、または get アクセサー (コンストラクターを除くすべての場所で変更できない) のみを宣言することで、オブジェクトを変更不可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="35ea2-112">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../../csharp/language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="35ea2-113">詳細については、「[方法: 自動実装するプロパティを使用して簡易クラスを実装する](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35ea2-113">For more information, see [How to: Implement a Lightweight Class with Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="35ea2-114">属性は、自動実装プロパティでは使用できますが、ソース コードからアクセスできないバッキング フィールドでは、当然使用できません。</span><span class="sxs-lookup"><span data-stu-id="35ea2-114">Attributes are permitted on auto-implemented properties but obviously not on the backing fields since those are not accessible from your source code.</span></span> <span data-ttu-id="35ea2-115">プロパティのバッキング フィールドで属性を使用する必要がある場合は、標準プロパティを作成してください。</span><span class="sxs-lookup"><span data-stu-id="35ea2-115">If you must use an attribute on the backing field of a property, just create a regular property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35ea2-116">参照</span><span class="sxs-lookup"><span data-stu-id="35ea2-116">See Also</span></span>  
 [<span data-ttu-id="35ea2-117">プロパティ</span><span class="sxs-lookup"><span data-stu-id="35ea2-117">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="35ea2-118">修飾子</span><span class="sxs-lookup"><span data-stu-id="35ea2-118">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
