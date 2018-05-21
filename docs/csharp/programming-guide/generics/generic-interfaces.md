---
title: ジェネリック インターフェイス (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 72f48aa1d70e6cf81b20adc547e2d418c4497256
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="generic-interfaces-c-programming-guide"></a><span data-ttu-id="ec674-102">ジェネリック インターフェイス (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="ec674-102">Generic Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="ec674-103">ジェネリック コレクション クラスのインターフェイスか、コレクション内の項目を表すジェネリック クラスのインターフェイスを定義すると、多くの場合、便利です。</span><span class="sxs-lookup"><span data-stu-id="ec674-103">It is often useful to define interfaces either for generic collection classes, or for the generic classes that represent items in the collection.</span></span> <span data-ttu-id="ec674-104">ジェネリック クラスの優先設定の意図は、値型に対するボックス化とボックス化解除を回避する目的で、<xref:System.IComparable> ではなく <xref:System.IComparable%601> など、ジェネリック インターフェイスを利用することにあります。</span><span class="sxs-lookup"><span data-stu-id="ec674-104">The preference for generic classes is to use generic interfaces, such as <xref:System.IComparable%601> rather than <xref:System.IComparable>, in order to avoid boxing and unboxing operations on value types.</span></span> <span data-ttu-id="ec674-105">.NET Framework クラス ライブラリにより、<xref:System.Collections.Generic> 名前空間のコレクション クラスと共に利用するためのジェネリック インターフェイスがいくつか定義されます。</span><span class="sxs-lookup"><span data-stu-id="ec674-105">The .NET Framework class library defines several generic interfaces for use with the collection classes in the <xref:System.Collections.Generic> namespace.</span></span>  
  
 <span data-ttu-id="ec674-106">インターフェイスが型パラメーターの制約として指定される場合、インターフェイスを実装する型のみを利用できます。</span><span class="sxs-lookup"><span data-stu-id="ec674-106">When an interface is specified as a constraint on a type parameter, only types that implement the interface can be used.</span></span> <span data-ttu-id="ec674-107">`GenericList<T>` クラスから派生する `SortedList<T>` クラスを示したのが次のコード サンプルです。</span><span class="sxs-lookup"><span data-stu-id="ec674-107">The following code example shows a `SortedList<T>` class that derives from the `GenericList<T>` class.</span></span> <span data-ttu-id="ec674-108">詳細については、「[ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec674-108">For more information, see [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md).</span></span> <span data-ttu-id="ec674-109">`SortedList<T>` により制約 `where T : IComparable<T>` が追加されます。</span><span class="sxs-lookup"><span data-stu-id="ec674-109">`SortedList<T>` adds the constraint `where T : IComparable<T>`.</span></span> <span data-ttu-id="ec674-110">これにより、`SortedList<T>` の `BubbleSort` メソッドは、一覧要素でジェネリック <xref:System.IComparable%601.CompareTo%2A> メソッドを利用できます。</span><span class="sxs-lookup"><span data-stu-id="ec674-110">This enables the `BubbleSort` method in `SortedList<T>` to use the generic <xref:System.IComparable%601.CompareTo%2A> method on list elements.</span></span> <span data-ttu-id="ec674-111">この例では、一覧要素は単純なクラスである `Person` です。これは `IComparable<Person>` を実装します。</span><span class="sxs-lookup"><span data-stu-id="ec674-111">In this example, list elements are a simple class, `Person`, that implements `IComparable<Person>`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#29](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_1.cs)]  
  
 <span data-ttu-id="ec674-112">次のように、複数のインターフェイスを単一の型で制約として指定できます。</span><span class="sxs-lookup"><span data-stu-id="ec674-112">Multiple interfaces can be specified as constraints on a single type, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#30](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_2.cs)]  
  
 <span data-ttu-id="ec674-113">1 つのインターフェイスで、次のように、複数の型パラメーターを定義できます。</span><span class="sxs-lookup"><span data-stu-id="ec674-113">An interface can define more than one type parameter, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#31](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_3.cs)]  
  
 <span data-ttu-id="ec674-114">クラスに適用される継承規則は、インターフェイスにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="ec674-114">The rules of inheritance that apply to classes also apply to interfaces:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#32](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_4.cs)]  
  
 <span data-ttu-id="ec674-115">ジェネリック インターフェイスが反変の場合、つまり、その型パラメーターを戻り値としてのみ利用する場合、ジェネリック インターフェイスは非ジェネリック インターフェイスから継承できます。</span><span class="sxs-lookup"><span data-stu-id="ec674-115">Generic interfaces can inherit from non-generic interfaces if the generic interface is contra-variant, which means it only uses its type parameter as a return value.</span></span> <span data-ttu-id="ec674-116">.NET Framework クラス ライブラリでは、<xref:System.Collections.Generic.IEnumerable%601> は <xref:System.Collections.IEnumerable> から継承します。これは、<xref:System.Collections.Generic.IEnumerable%601> が <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> の戻り値と <xref:System.Collections.Generic.IEnumerator%601.Current%2A> プロパティ ゲッターの `T` のみを利用するためです。</span><span class="sxs-lookup"><span data-stu-id="ec674-116">In the .NET Framework class library, <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable> because <xref:System.Collections.Generic.IEnumerable%601> only uses `T` in the return value of <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> and in the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property getter.</span></span>  
  
 <span data-ttu-id="ec674-117">具象クラスは、次のように、構築されたクローズ型インターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="ec674-117">Concrete classes can implement closed constructed interfaces, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#33](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_5.cs)]  
  
 <span data-ttu-id="ec674-118">ジェネリック クラスは、クラス パラメーターの一覧からインターフェイスが必要とするすべての引数が提供される限り、ジェネリック インターフェイスや構築されたクローズ型インターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="ec674-118">Generic classes can implement generic interfaces or closed constructed interfaces as long as the class parameter list supplies all arguments required by the interface, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#34](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_6.cs)]  
  
 <span data-ttu-id="ec674-119">メソッドのオーバーロードを制御する規則は、ジェネリック クラス、ジェネリック構造体、ジェネリック インターフェイス内のメソッドの規則と同じです。</span><span class="sxs-lookup"><span data-stu-id="ec674-119">The rules that control method overloading are the same for methods within generic classes, generic structs, or generic interfaces.</span></span> <span data-ttu-id="ec674-120">詳細については、「[ジェネリック メソッド](../../../csharp/programming-guide/generics/generic-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec674-120">For more information, see [Generic Methods](../../../csharp/programming-guide/generics/generic-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec674-121">参照</span><span class="sxs-lookup"><span data-stu-id="ec674-121">See Also</span></span>  
 [<span data-ttu-id="ec674-122">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="ec674-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ec674-123">ジェネリックの概要</span><span class="sxs-lookup"><span data-stu-id="ec674-123">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="ec674-124">interface</span><span class="sxs-lookup"><span data-stu-id="ec674-124">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
 [<span data-ttu-id="ec674-125">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="ec674-125">Generics</span></span>](~/docs/standard/generics/index.md)
