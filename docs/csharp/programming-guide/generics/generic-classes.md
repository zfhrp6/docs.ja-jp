---
title: "ジェネリック クラス (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
caps.latest.revision: 30
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
ms.openlocfilehash: 17ec9f5d26c01b7f7f7f95026bfdfaa88d709b60
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="generic-classes-c-programming-guide"></a><span data-ttu-id="6efee-102">ジェネリック クラス (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="6efee-102">Generic Classes (C# Programming Guide)</span></span>
<span data-ttu-id="6efee-103">ジェネリック クラスは、特定のデータ型に固有ではない操作をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="6efee-103">Generic classes encapsulate operations that are not specific to a particular data type.</span></span> <span data-ttu-id="6efee-104">ジェネリック クラスは最も一般的に、リンク リスト、ハッシュ テーブル、スタック、キュー、ツリーなどのコレクションと共に使用されます。</span><span class="sxs-lookup"><span data-stu-id="6efee-104">The most common use for generic classes is with collections like linked lists, hash tables, stacks, queues, trees, and so on.</span></span> <span data-ttu-id="6efee-105">コレクションの項目を追加または削除するなどの操作は、保存されているデータの型に関係なく、基本的に同じように実行されます。</span><span class="sxs-lookup"><span data-stu-id="6efee-105">Operations such as adding and removing items from the collection are performed in basically the same way regardless of the type of data being stored.</span></span>  
  
 <span data-ttu-id="6efee-106">コレクション クラスを必要とするほとんどのシナリオで、.NET Framework クラス ライブラリで提供されているものを使用するという方法が推奨されます。</span><span class="sxs-lookup"><span data-stu-id="6efee-106">For most scenarios that require collection classes, the recommended approach is to use the ones provided in the .NET Framework class library.</span></span> <span data-ttu-id="6efee-107">これらのクラスの詳細については、「[.NET Framework クラス ライブラリのジェネリック](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6efee-107">For more information about using these classes, see [Generics in the .NET Framework Class Library](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md).</span></span>  
  
 <span data-ttu-id="6efee-108">通常、ジェネリック クラスを作成するには、既存の具象クラスから始め、汎用性と使いやすさの間で最適なバランスが取れるまで、一度に 1 つずつ型を型パラメーターに変更します。</span><span class="sxs-lookup"><span data-stu-id="6efee-108">Typically, you create generic classes by starting with an existing concrete class, and changing types into type parameters one at a time until you reach the optimal balance of generalization and usability.</span></span> <span data-ttu-id="6efee-109">独自のジェネリック クラスを作成するときの重要な考慮事項は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6efee-109">When creating your own generic classes, important considerations include the following:</span></span>  
  
-   <span data-ttu-id="6efee-110">型パラメーターに汎用化する型。</span><span class="sxs-lookup"><span data-stu-id="6efee-110">Which types to generalize into type parameters.</span></span>  
  
     <span data-ttu-id="6efee-111">通例、パラメーター化できる型が多ければ多いほど、コードの柔軟性が上がり、再利用しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="6efee-111">As a rule, the more types you can parameterize, the more flexible and reusable your code becomes.</span></span> <span data-ttu-id="6efee-112">ただし、汎用化が多すぎると、他の開発者にとって読みにくい、理解しにくいコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="6efee-112">However, too much generalization can create code that is difficult for other developers to read or understand.</span></span>  
  
-   <span data-ttu-id="6efee-113">型パラメーターに適用する制約 (制約がある場合) (「[型パラメーターの制約](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="6efee-113">What constraints, if any, to apply to the type parameters (See [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)).</span></span>  
  
     <span data-ttu-id="6efee-114">処理しなければならない型を処理できる範囲で最大の制約を適用することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="6efee-114">A good rule is to apply the maximum constraints possible that will still let you handle the types you must handle.</span></span> <span data-ttu-id="6efee-115">たとえば、ジェネリック クラスが参照型でのみ使用される場合、クラス制約を適用します。</span><span class="sxs-lookup"><span data-stu-id="6efee-115">For example, if you know that your generic class is intended for use only with reference types, apply the class constraint.</span></span> <span data-ttu-id="6efee-116">それにより、意図しない、値型でのクラスの使用が回避され、`T` で `as` 演算子を使用したり、null 値を確認したりできます。</span><span class="sxs-lookup"><span data-stu-id="6efee-116">That will prevent unintended use of your class with value types, and will enable you to use the `as` operator on `T`, and check for null values.</span></span>  
  
-   <span data-ttu-id="6efee-117">基底クラスやサブクラスの要因としてジェネリック動作を考慮するかどうか。</span><span class="sxs-lookup"><span data-stu-id="6efee-117">Whether to factor generic behavior into base classes and subclasses.</span></span>  
  
     <span data-ttu-id="6efee-118">ジェネリック クラスは基底クラスとして機能できるので、非ジェネリック クラスと同様の設計考慮事項がここで適用されます。</span><span class="sxs-lookup"><span data-stu-id="6efee-118">Because generic classes can serve as base classes, the same design considerations apply here as with non-generic classes.</span></span> <span data-ttu-id="6efee-119">ジェネリック基底クラスからの継承ルールについて、このトピックの後半で確認してください。</span><span class="sxs-lookup"><span data-stu-id="6efee-119">See the rules about inheriting from generic base classes later in this topic.</span></span>  
  
-   <span data-ttu-id="6efee-120">1 つまたは複数のジェネリック インターフェイスを実装するかどうか。</span><span class="sxs-lookup"><span data-stu-id="6efee-120">Whether to implement one or more generic interfaces.</span></span>  
  
     <span data-ttu-id="6efee-121">たとえば、ジェネリック基盤のコレクションで項目を作成するために使用されるクラスを設計するとき、場合によっては、<xref:System.IComparable%601> のようなインターフェイスを実装する必要があります。ここで `T` はクラスの型です。</span><span class="sxs-lookup"><span data-stu-id="6efee-121">For example, if you are designing a class that will be used to create items in a generics-based collection, you may have to implement an interface such as <xref:System.IComparable%601> where `T` is the type of your class.</span></span>  
  
 <span data-ttu-id="6efee-122">単純なジェネリック クラスの例については、「[ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6efee-122">For an example of a simple generic class, see [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md).</span></span>  
  
 <span data-ttu-id="6efee-123">型パラメーターや制約のルールは、特に継承とメンバーのアクセシビリティに関して、ジェネリック クラスの動作と密接な関係があります。</span><span class="sxs-lookup"><span data-stu-id="6efee-123">The rules for type parameters and constraints have several implications for generic class behavior, especially regarding inheritance and member accessibility.</span></span> <span data-ttu-id="6efee-124">続行する前に、いくつかの用語を理解してください。</span><span class="sxs-lookup"><span data-stu-id="6efee-124">Before proceeding, you should understand some terms.</span></span> <span data-ttu-id="6efee-125">ジェネリック クラス `Node<T>,` の場合、型引数を指定することで、クライアント コードはクラスを参照し、構築されたクローズ型を作成できます (`Node<int>`)。</span><span class="sxs-lookup"><span data-stu-id="6efee-125">For a generic class `Node<T>,` client code can reference the class either by specifying a type argument, to create a closed constructed type (`Node<int>`).</span></span> <span data-ttu-id="6efee-126">あるいは、ジェネリック基底クラスを指定するときなど、型パラメーターを指定せず、構築されたオープン型を作成できます (`Node<T>`)。</span><span class="sxs-lookup"><span data-stu-id="6efee-126">Alternatively, it can leave the type parameter unspecified, for example when you specify a generic base class, to create an open constructed type (`Node<T>`).</span></span> <span data-ttu-id="6efee-127">ジェネリック クラスは、具象、構築されたクローズ型、または構築されたオープン型の基底クラスから継承できます。</span><span class="sxs-lookup"><span data-stu-id="6efee-127">Generic classes can inherit from concrete, closed constructed, or open constructed base classes:</span></span>  
  
 <span data-ttu-id="6efee-128">[!code-cs[csProgGuideGenerics#16](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="6efee-128">[!code-cs[csProgGuideGenerics#16](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_1.cs)]</span></span>  
  
 <span data-ttu-id="6efee-129">非ジェネリック クラス、言い換えれば、具象クラスは、構築されたクローズ型の基底クラスから継承できますが、構築されたオープン型のクラスや型パラメーターからは継承できません。ランタイム時、基底クラスのインスタンス化に必要な型引数をクライアント コードが提供できないためです。</span><span class="sxs-lookup"><span data-stu-id="6efee-129">Non-generic, in other words, concrete, classes can inherit from closed constructed base classes, but not from open constructed classes or from type parameters because there is no way at run time for client code to supply the type argument required to instantiate the base class.</span></span>  
  
 <span data-ttu-id="6efee-130">[!code-cs[csProgGuideGenerics#17](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="6efee-130">[!code-cs[csProgGuideGenerics#17](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_2.cs)]</span></span>  
  
 <span data-ttu-id="6efee-131">構築されたオープン型から継承するジェネリック クラスは、継承クラスで共有されない基底クラスの型パラメーターに対して型引数を提供する必要があります。次のコードをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6efee-131">Generic classes that inherit from open constructed types must supply type arguments for any base class type parameters that are not shared by the inheriting class, as demonstrated in the following code:</span></span>  
  
 <span data-ttu-id="6efee-132">[!code-cs[csProgGuideGenerics#18](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="6efee-132">[!code-cs[csProgGuideGenerics#18](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_3.cs)]</span></span>  
  
 <span data-ttu-id="6efee-133">構築されたオープン型から継承するジェネリック クラスは、基底クラスの制約のスーパーセットである (基底クラスの制約を暗黙に定義する) 制約を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6efee-133">Generic classes that inherit from open constructed types must specify constraints that are a superset of, or imply, the constraints on the base type:</span></span>  
  
 <span data-ttu-id="6efee-134">[!code-cs[csProgGuideGenerics#19](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="6efee-134">[!code-cs[csProgGuideGenerics#19](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_4.cs)]</span></span>  
  
 <span data-ttu-id="6efee-135">ジェネリック型では、次のように、複数の型パラメーターと制約を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6efee-135">Generic types can use multiple type parameters and constraints, as follows:</span></span>  
  
 <span data-ttu-id="6efee-136">[!code-cs[csProgGuideGenerics#20](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="6efee-136">[!code-cs[csProgGuideGenerics#20](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_5.cs)]</span></span>  
  
 <span data-ttu-id="6efee-137">構築されたオープン型と構築されたクローズ型をメソッド パラメーターとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="6efee-137">Open constructed and closed constructed types can be used as method parameters:</span></span>  
  
 <span data-ttu-id="6efee-138">[!code-cs[csProgGuideGenerics#21](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="6efee-138">[!code-cs[csProgGuideGenerics#21](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_6.cs)]</span></span>  
  
 <span data-ttu-id="6efee-139">ジェネリック クラスでインターフェイスを実装する場合、そのクラスのすべてのインスタンスをそのインターフェイスにキャストできます。</span><span class="sxs-lookup"><span data-stu-id="6efee-139">If a generic class implements an interface, all instances of that class can be cast to that interface.</span></span>  
  
 <span data-ttu-id="6efee-140">ジェネリック クラスは変化しません。</span><span class="sxs-lookup"><span data-stu-id="6efee-140">Generic classes are invariant.</span></span> <span data-ttu-id="6efee-141">言い換えると、入力パラメーターが `List<BaseClass>` を指定するとき、`List<DerivedClass>` を指定するとコンパイル時エラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6efee-141">In other words, if an input parameter specifies a `List<BaseClass>`, you will get a compile-time error if you try to provide a `List<DerivedClass>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6efee-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="6efee-142">See Also</span></span>  
 <span data-ttu-id="6efee-143"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="6efee-143"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="6efee-144">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="6efee-144">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="6efee-145">[ジェネリック](../../../csharp/programming-guide/generics/index.md) </span><span class="sxs-lookup"><span data-stu-id="6efee-145">[Generics](../../../csharp/programming-guide/generics/index.md) </span></span>  
 <span data-ttu-id="6efee-146">[列挙子の状態を保存する](http://go.microsoft.com/fwlink/?LinkId=112390) </span><span class="sxs-lookup"><span data-stu-id="6efee-146">[Saving the State of Enumerators](http://go.microsoft.com/fwlink/?LinkId=112390) </span></span>  
 [<span data-ttu-id="6efee-147">継承パズル、パート 1</span><span class="sxs-lookup"><span data-stu-id="6efee-147">An Inheritance Puzzle, Part One</span></span>](http://go.microsoft.com/fwlink/?LinkId=112380)

