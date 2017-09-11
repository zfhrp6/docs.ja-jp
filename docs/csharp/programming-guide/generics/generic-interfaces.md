---
title: "ジェネリック インターフェイス (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
caps.latest.revision: 28
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
ms.openlocfilehash: 2a9a994c339553b923b930660c0e129dd930de96
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="generic-interfaces-c-programming-guide"></a><span data-ttu-id="7f5de-102">ジェネリック インターフェイス (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="7f5de-102">Generic Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="7f5de-103">ジェネリック コレクション クラスのインターフェイスか、コレクション内の項目を表すジェネリック クラスのインターフェイスを定義すると、多くの場合、便利です。</span><span class="sxs-lookup"><span data-stu-id="7f5de-103">It is often useful to define interfaces either for generic collection classes, or for the generic classes that represent items in the collection.</span></span> <span data-ttu-id="7f5de-104">ジェネリック クラスの優先設定の意図は、値型に対するボックス化とボックス化解除を回避する目的で、<xref:System.IComparable> ではなく <xref:System.IComparable%601> など、ジェネリック インターフェイスを利用することにあります。</span><span class="sxs-lookup"><span data-stu-id="7f5de-104">The preference for generic classes is to use generic interfaces, such as <xref:System.IComparable%601> rather than <xref:System.IComparable>, in order to avoid boxing and unboxing operations on value types.</span></span> <span data-ttu-id="7f5de-105">.NET Framework クラス ライブラリにより、<xref:System.Collections.Generic> 名前空間のコレクション クラスと共に利用するためのジェネリック インターフェイスがいくつか定義されます。</span><span class="sxs-lookup"><span data-stu-id="7f5de-105">The .NET Framework class library defines several generic interfaces for use with the collection classes in the <xref:System.Collections.Generic> namespace.</span></span>  
  
 <span data-ttu-id="7f5de-106">インターフェイスが型パラメーターの制約として指定される場合、インターフェイスを実装する型のみを利用できます。</span><span class="sxs-lookup"><span data-stu-id="7f5de-106">When an interface is specified as a constraint on a type parameter, only types that implement the interface can be used.</span></span> <span data-ttu-id="7f5de-107">`GenericList<T>` クラスから派生する `SortedList<T>` クラスを示したのが次のコード サンプルです。</span><span class="sxs-lookup"><span data-stu-id="7f5de-107">The following code example shows a `SortedList<T>` class that derives from the `GenericList<T>` class.</span></span> <span data-ttu-id="7f5de-108">詳細については、「[ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f5de-108">For more information, see [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md).</span></span> <span data-ttu-id="7f5de-109">`SortedList<T>` により制約 `where T : IComparable<T>` が追加されます。</span><span class="sxs-lookup"><span data-stu-id="7f5de-109">`SortedList<T>` adds the constraint `where T : IComparable<T>`.</span></span> <span data-ttu-id="7f5de-110">これにより、`SortedList<T>` の `BubbleSort` メソッドは、一覧要素でジェネリック <xref:System.IComparable%601.CompareTo%2A> メソッドを利用できます。</span><span class="sxs-lookup"><span data-stu-id="7f5de-110">This enables the `BubbleSort` method in `SortedList<T>` to use the generic <xref:System.IComparable%601.CompareTo%2A> method on list elements.</span></span> <span data-ttu-id="7f5de-111">この例では、一覧要素は単純なクラスである `Person` です。これは `IComparable<Person>` を実装します。</span><span class="sxs-lookup"><span data-stu-id="7f5de-111">In this example, list elements are a simple class, `Person`, that implements `IComparable<Person>`.</span></span>  
  
 <span data-ttu-id="7f5de-112">[!code-cs[csProgGuideGenerics#29](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="7f5de-112">[!code-cs[csProgGuideGenerics#29](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_1.cs)]</span></span>  
  
 <span data-ttu-id="7f5de-113">次のように、複数のインターフェイスを単一の型で制約として指定できます。</span><span class="sxs-lookup"><span data-stu-id="7f5de-113">Multiple interfaces can be specified as constraints on a single type, as follows:</span></span>  
  
 <span data-ttu-id="7f5de-114">[!code-cs[csProgGuideGenerics#30](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="7f5de-114">[!code-cs[csProgGuideGenerics#30](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_2.cs)]</span></span>  
  
 <span data-ttu-id="7f5de-115">1 つのインターフェイスで、次のように、複数の型パラメーターを定義できます。</span><span class="sxs-lookup"><span data-stu-id="7f5de-115">An interface can define more than one type parameter, as follows:</span></span>  
  
 <span data-ttu-id="7f5de-116">[!code-cs[csProgGuideGenerics#31](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="7f5de-116">[!code-cs[csProgGuideGenerics#31](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_3.cs)]</span></span>  
  
 <span data-ttu-id="7f5de-117">クラスに適用される継承規則は、インターフェイスにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="7f5de-117">The rules of inheritance that apply to classes also apply to interfaces:</span></span>  
  
 <span data-ttu-id="7f5de-118">[!code-cs[csProgGuideGenerics#32](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="7f5de-118">[!code-cs[csProgGuideGenerics#32](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_4.cs)]</span></span>  
  
 <span data-ttu-id="7f5de-119">ジェネリック インターフェイスが反変の場合、つまり、その型パラメーターを戻り値としてのみ利用する場合、ジェネリック インターフェイスは非ジェネリック インターフェイスから継承できます。</span><span class="sxs-lookup"><span data-stu-id="7f5de-119">Generic interfaces can inherit from non-generic interfaces if the generic interface is contra-variant, which means it only uses its type parameter as a return value.</span></span> <span data-ttu-id="7f5de-120">.NET Framework クラス ライブラリでは、<xref:System.Collections.Generic.IEnumerable%601> は <xref:System.Collections.IEnumerable> から継承します。これは、<xref:System.Collections.Generic.IEnumerable%601> が <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> の戻り値と <xref:System.Collections.Generic.IEnumerator%601.Current%2A> プロパティ ゲッターの `T` のみを利用するためです。</span><span class="sxs-lookup"><span data-stu-id="7f5de-120">In the .NET Framework class library, <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable> because <xref:System.Collections.Generic.IEnumerable%601> only uses `T` in the return value of <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> and in the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property getter.</span></span>  
  
 <span data-ttu-id="7f5de-121">具象クラスは、次のように、構築されたクローズ型インターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="7f5de-121">Concrete classes can implement closed constructed interfaces, as follows:</span></span>  
  
 <span data-ttu-id="7f5de-122">[!code-cs[csProgGuideGenerics#33](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="7f5de-122">[!code-cs[csProgGuideGenerics#33](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_5.cs)]</span></span>  
  
 <span data-ttu-id="7f5de-123">ジェネリック クラスは、クラス パラメーターの一覧からインターフェイスが必要とするすべての引数が提供される限り、ジェネリック インターフェイスや構築されたクローズ型インターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="7f5de-123">Generic classes can implement generic interfaces or closed constructed interfaces as long as the class parameter list supplies all arguments required by the interface, as follows:</span></span>  
  
 <span data-ttu-id="7f5de-124">[!code-cs[csProgGuideGenerics#34](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="7f5de-124">[!code-cs[csProgGuideGenerics#34](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_6.cs)]</span></span>  
  
 <span data-ttu-id="7f5de-125">メソッドのオーバーロードを制御する規則は、ジェネリック クラス、ジェネリック構造体、ジェネリック インターフェイス内のメソッドの規則と同じです。</span><span class="sxs-lookup"><span data-stu-id="7f5de-125">The rules that control method overloading are the same for methods within generic classes, generic structs, or generic interfaces.</span></span> <span data-ttu-id="7f5de-126">詳細については、「[ジェネリック メソッド](../../../csharp/programming-guide/generics/generic-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f5de-126">For more information, see [Generic Methods](../../../csharp/programming-guide/generics/generic-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f5de-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f5de-127">See Also</span></span>  
 <span data-ttu-id="7f5de-128">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="7f5de-128">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="7f5de-129">[ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span><span class="sxs-lookup"><span data-stu-id="7f5de-129">[Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span></span>  
 <span data-ttu-id="7f5de-130">[インターフェイス](../../../csharp/language-reference/keywords/interface.md) </span><span class="sxs-lookup"><span data-stu-id="7f5de-130">[interface](../../../csharp/language-reference/keywords/interface.md) </span></span>  
 [<span data-ttu-id="7f5de-131">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="7f5de-131">Generics</span></span>](~/docs/standard/generics/index.md)

