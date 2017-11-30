---
title: "class (C# リファレンス)"
ms.date: 07/18/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords: class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ae4b019ee88b6f331a76c750ab94fc76a3343adb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="class-c-reference"></a><span data-ttu-id="888c2-102">class (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="888c2-102">class (C# Reference)</span></span>

<span data-ttu-id="888c2-103">クラスは、次の例に示すように、キーワード `class` を使用して宣言します。</span><span class="sxs-lookup"><span data-stu-id="888c2-103">Classes are declared using the keyword `class`, as shown in the following example:</span></span>

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates 
    // and nested classes go here.
}
```

## <a name="remarks"></a><span data-ttu-id="888c2-104">コメント</span><span class="sxs-lookup"><span data-stu-id="888c2-104">Remarks</span></span>
<span data-ttu-id="888c2-105">C# では、単一継承のみを使用できます。</span><span class="sxs-lookup"><span data-stu-id="888c2-105">Only single inheritance is allowed in C#.</span></span> <span data-ttu-id="888c2-106">つまり、クラスは 1 つの基底クラスの実装だけを継承できます。</span><span class="sxs-lookup"><span data-stu-id="888c2-106">In other words, a class can inherit implementation from one base class only.</span></span> <span data-ttu-id="888c2-107">ただし、クラスは複数のインターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="888c2-107">However, a class can implement more than one interface.</span></span> <span data-ttu-id="888c2-108">クラスの継承とインターフェイスの実装の例を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="888c2-108">The following table shows examples of class inheritance and interface implementation:</span></span>

|<span data-ttu-id="888c2-109">継承</span><span class="sxs-lookup"><span data-stu-id="888c2-109">Inheritance</span></span>|<span data-ttu-id="888c2-110">例</span><span class="sxs-lookup"><span data-stu-id="888c2-110">Example</span></span>|
|-----------------|-------------|
|<span data-ttu-id="888c2-111">なし</span><span class="sxs-lookup"><span data-stu-id="888c2-111">None</span></span>|`class ClassA { }`|
|<span data-ttu-id="888c2-112">Single</span><span class="sxs-lookup"><span data-stu-id="888c2-112">Single</span></span>|`class DerivedClass: BaseClass { }`|
|<span data-ttu-id="888c2-113">なし。2 つのインターフェイスを実装</span><span class="sxs-lookup"><span data-stu-id="888c2-113">None, implements two interfaces</span></span>|`class ImplClass: IFace1, IFace2 { }`|
|<span data-ttu-id="888c2-114">1 つ。1 つのインターフェイスを実装</span><span class="sxs-lookup"><span data-stu-id="888c2-114">Single, implements one interface</span></span>|`class ImplDerivedClass: BaseClass, IFace1 { }`|

<span data-ttu-id="888c2-115">名前空間内で直接宣言され、他のクラスに入れ子にされていないクラスは、[public](../../../csharp/language-reference/keywords/public.md) または [internal](../../../csharp/language-reference/keywords/internal.md) のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="888c2-115">Classes that you declare directly within a namespace, not nested within other classes, can be either [public](../../../csharp/language-reference/keywords/public.md) or [internal](../../../csharp/language-reference/keywords/internal.md).</span></span> <span data-ttu-id="888c2-116">クラスは既定で `internal` です。</span><span class="sxs-lookup"><span data-stu-id="888c2-116">Classes are `internal` by default.</span></span>

<span data-ttu-id="888c2-117">入れ子になったクラスを含め、クラス メンバーは、[パブリック](../../../csharp/language-reference/keywords/public.md)、 `protected internal`、[保護](../../../csharp/language-reference/keywords/protected.md)、[内部](../../../csharp/language-reference/keywords/internal.md)、[プライベート](../../../csharp/language-reference/keywords/private.md)、または`private protected`.</span><span class="sxs-lookup"><span data-stu-id="888c2-117">Class members, including nested classes, can be [public](../../../csharp/language-reference/keywords/public.md), `protected internal`, [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [private](../../../csharp/language-reference/keywords/private.md), or `private protected`.</span></span> <span data-ttu-id="888c2-118">メンバーは既定で [private](../../../csharp/language-reference/keywords/private.md) です。</span><span class="sxs-lookup"><span data-stu-id="888c2-118">Members are [private](../../../csharp/language-reference/keywords/private.md) by default.</span></span>

<span data-ttu-id="888c2-119">詳細については、「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="888c2-119">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>

<span data-ttu-id="888c2-120">型パラメーターを持つジェネリック クラスを宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="888c2-120">You can declare generic classes that have type parameters.</span></span> <span data-ttu-id="888c2-121">詳細については、「[ジェネリック クラス](../../../csharp/programming-guide/generics/generic-classes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="888c2-121">For more information, see [Generic Classes](../../../csharp/programming-guide/generics/generic-classes.md).</span></span>

<span data-ttu-id="888c2-122">クラスには、次のメンバーの宣言を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="888c2-122">A class can contain declarations of the following members:</span></span>

- [<span data-ttu-id="888c2-123">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="888c2-123">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)

- [<span data-ttu-id="888c2-124">定数</span><span class="sxs-lookup"><span data-stu-id="888c2-124">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)

- [<span data-ttu-id="888c2-125">フィールド</span><span class="sxs-lookup"><span data-stu-id="888c2-125">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)

- [<span data-ttu-id="888c2-126">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="888c2-126">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)

- [<span data-ttu-id="888c2-127">メソッド</span><span class="sxs-lookup"><span data-stu-id="888c2-127">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="888c2-128">プロパティ</span><span class="sxs-lookup"><span data-stu-id="888c2-128">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)

- [<span data-ttu-id="888c2-129">インデクサー</span><span class="sxs-lookup"><span data-stu-id="888c2-129">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)

- [<span data-ttu-id="888c2-130">演算子</span><span class="sxs-lookup"><span data-stu-id="888c2-130">Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/operators.md)

- [<span data-ttu-id="888c2-131">イベント</span><span class="sxs-lookup"><span data-stu-id="888c2-131">Events</span></span>](../../../csharp/programming-guide/events/index.md)

- [<span data-ttu-id="888c2-132">デリゲート</span><span class="sxs-lookup"><span data-stu-id="888c2-132">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)

- [<span data-ttu-id="888c2-133">クラス</span><span class="sxs-lookup"><span data-stu-id="888c2-133">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)

- [<span data-ttu-id="888c2-134">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="888c2-134">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)

- [<span data-ttu-id="888c2-135">構造体</span><span class="sxs-lookup"><span data-stu-id="888c2-135">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)

## <a name="example"></a><span data-ttu-id="888c2-136">例</span><span class="sxs-lookup"><span data-stu-id="888c2-136">Example</span></span>
<span data-ttu-id="888c2-137">ここでは、クラスのフィールド、コンストラクター、メソッドの宣言例を示します。</span><span class="sxs-lookup"><span data-stu-id="888c2-137">The following example demonstrates declaring class fields, constructors, and methods.</span></span> <span data-ttu-id="888c2-138">また、オブジェクト インスタンスの作成とインスタンス データの出力の例も示します。</span><span class="sxs-lookup"><span data-stu-id="888c2-138">It also demonstrates object instantiation and printing instance data.</span></span> <span data-ttu-id="888c2-139">次の例では、2 つのクラスが宣言されています。</span><span class="sxs-lookup"><span data-stu-id="888c2-139">In this example, two classes are declared.</span></span> <span data-ttu-id="888c2-140">最初の `Child` クラスには、2 つのプライベート フィールド (`name` と `age`)、2 つのパブリック コンストラクター、および 1 つのパブリック メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="888c2-140">The first class, `Child`, contains two private fields (`name` and `age`), two public constructors and one public method.</span></span> <span data-ttu-id="888c2-141">2 番目のクラスである `StringTest` は、`Main`の格納に使用されます。</span><span class="sxs-lookup"><span data-stu-id="888c2-141">The second class, `StringTest`, is used to contain `Main`.</span></span>

[!code-csharp[csrefKeywordsTypes#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/class_1.cs)]

## <a name="comments"></a><span data-ttu-id="888c2-142">コメント</span><span class="sxs-lookup"><span data-stu-id="888c2-142">Comments</span></span>
<span data-ttu-id="888c2-143">前の例で、プライベート フィールド (`name` および `age`) にアクセスできるのは、`Child` クラスのパブリック メソッドだけであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="888c2-143">Notice that in the previous example the private fields (`name` and `age`) can only be accessed through the public method of the `Child` class.</span></span> <span data-ttu-id="888c2-144">たとえば、次のステートメントを使用して `Main` メソッドから子の名前を印刷することはできません。</span><span class="sxs-lookup"><span data-stu-id="888c2-144">For example, you cannot print the child's name, from the `Main` method, using a statement like this:</span></span>

```csharp
Console.Write(child1.name);   // Error
```

<span data-ttu-id="888c2-145">`Main` から `Child`のプライベート メンバーへのアクセスは、`Main` がそのクラスのメンバーである場合にのみ可能です。</span><span class="sxs-lookup"><span data-stu-id="888c2-145">Accessing private members of `Child` from `Main` would only be possible if `Main` were a member of the class.</span></span>

<span data-ttu-id="888c2-146">アクセス修飾子を指定せずにクラス内で宣言された型は既定で `private` になります。そのため、キーワードが削除されてもこの例のデータ メンバーは `private` です。</span><span class="sxs-lookup"><span data-stu-id="888c2-146">Types declared inside a class without an access modifier default to `private`, so the data members in this example would still be `private` if the keyword were removed.</span></span>

<span data-ttu-id="888c2-147">最後に、既定のコンストラクターを使用して作成されたオブジェクト (`child3`) は、既定で年齢フィールドが 0 に初期化されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="888c2-147">Finally, notice that for the object created using the default constructor (`child3`), the age field was initialized to zero by default.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="888c2-148">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="888c2-148">C# Language Specification</span></span>
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="888c2-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="888c2-149">See Also</span></span>
 [<span data-ttu-id="888c2-150">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="888c2-150">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="888c2-151">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="888c2-151">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="888c2-152">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="888c2-152">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="888c2-153">参照型</span><span class="sxs-lookup"><span data-stu-id="888c2-153">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)
