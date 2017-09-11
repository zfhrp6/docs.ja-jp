---
title: "構造体 - C# ガイド"
description: "構造体型と、構造体を作成する方法について説明します"
keywords: .NET, .NET Core, C#
author: BillWagner
ms.author: wiwagn
ms.date: 10/12/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e2a4bfdb46a69113d5eb8949df4ccf902acf9dee
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="structs"></a><span data-ttu-id="9936e-104">構造体</span><span class="sxs-lookup"><span data-stu-id="9936e-104">Structs</span></span>
<span data-ttu-id="9936e-105">"*構造体*" は値の型です。</span><span class="sxs-lookup"><span data-stu-id="9936e-105">A *struct* is a value type.</span></span> <span data-ttu-id="9936e-106">構造体が作成されると、構造体が割り当てられている変数にはその構造体の実際のデータが設定されます。</span><span class="sxs-lookup"><span data-stu-id="9936e-106">When a struct is created, the variable to which the struct is assigned holds the struct's actual data.</span></span> <span data-ttu-id="9936e-107">構造体が新しい変数に割り当てられると、そのデータがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="9936e-107">When the struct is assigned to a new variable, it is copied.</span></span> <span data-ttu-id="9936e-108">したがって、新しい変数と元の変数には、同じデータのコピーが別個に含まれることになります。</span><span class="sxs-lookup"><span data-stu-id="9936e-108">The new variable and the original variable therefore contain two separate copies of the same data.</span></span> <span data-ttu-id="9936e-109">一方のコピーに対して行われた変更は、もう一方のコピーには影響しません。</span><span class="sxs-lookup"><span data-stu-id="9936e-109">Changes made to one copy do not affect the other copy.</span></span>

<span data-ttu-id="9936e-110">値型の変数は、その値を直接含みます。つまり、変数がどのようなコンテキストで宣言されたとしても、必ずメモリがインラインで割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="9936e-110">Value type variables directly contain their values, which means that the memory is allocated inline in whatever context the variable is declared.</span></span> <span data-ttu-id="9936e-111">値型の変数には、独立したヒープ割り当てやガベージ コレクションのオーバーヘッドはありません。</span><span class="sxs-lookup"><span data-stu-id="9936e-111">There is no separate heap allocation or garbage collection overhead for value-type variables.</span></span>  
  
<span data-ttu-id="9936e-112">値型には、[構造体](./language-reference/keywords/struct.md)と[列挙体](./language-reference/keywords/enum.md)の 2 つのカテゴリがあります。</span><span class="sxs-lookup"><span data-stu-id="9936e-112">There are two categories of value types: [struct](./language-reference/keywords/struct.md) and [enum](./language-reference/keywords/enum.md).</span></span>  
  
<span data-ttu-id="9936e-113">組み込みの数値型は構造体であり、次のようにしてアクセスできるプロパティとメソッドを持ちます。</span><span class="sxs-lookup"><span data-stu-id="9936e-113">The built-in numeric types are structs, and they have properties and methods that you can access:</span></span>  
  
<span data-ttu-id="9936e-114">[!code-csharp[静的メソッド](../../samples/snippets/csharp/concepts/structs/static-method.cs)]</span><span class="sxs-lookup"><span data-stu-id="9936e-114">[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]</span></span>
  
<span data-ttu-id="9936e-115">ただし、宣言とそこへの値の代入は、あたかも単純な非集約型であるかのように行うことができます。</span><span class="sxs-lookup"><span data-stu-id="9936e-115">But you declare and assign values to them as if they were simple non-aggregate types:</span></span>  
  
<span data-ttu-id="9936e-116">[!code-csharp[値の割り当て](../../samples/snippets/csharp/concepts/structs/assign-value.cs)]</span><span class="sxs-lookup"><span data-stu-id="9936e-116">[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)]</span></span> 
  
<span data-ttu-id="9936e-117">値型は、"*シール*" されています。たとえば @System.Int32 から値型を派生させることはできません。構造体は @System.ValueType からしか継承できないため、任意のユーザー定義型または構造体を継承する構造体を定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="9936e-117">Value types are *sealed*, which means, for example, that you cannot derive a type from @System.Int32, and you cannot define a struct to inherit from any user-defined class or struct because a struct can only inherit from @System.ValueType.</span></span> <span data-ttu-id="9936e-118">ただし、構造体は 1 つ以上のインターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="9936e-118">However, a struct can implement one or more interfaces.</span></span> <span data-ttu-id="9936e-119">構造体型は、インターフェイス型にキャストできます。これを行うと、"*ボックス化*" 操作によって、構造体がマネージ ヒープ上の参照型オブジェクト内にラップされます。</span><span class="sxs-lookup"><span data-stu-id="9936e-119">You can cast a struct type to an interface type; this causes a *boxing* operation to wrap the struct inside a reference type object on the managed heap.</span></span> <span data-ttu-id="9936e-120">ボックス化操作が発生するのは、入力パラメーターとして @System.Object を受け取るメソッドに値型を渡した場合です。</span><span class="sxs-lookup"><span data-stu-id="9936e-120">Boxing operations occur when you pass a value type to a method that takes an @System.Object as an input parameter.</span></span> <span data-ttu-id="9936e-121">詳細については、「[ボックス化とボックス化解除](./programming-guide/types/boxing-and-unboxing.md )」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9936e-121">For more information, see [Boxing and Unboxing](./programming-guide/types/boxing-and-unboxing.md ).</span></span>  
  
<span data-ttu-id="9936e-122">独自のカスタム値型を作成するには、[struct](./language-reference/keywords/struct.md) キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="9936e-122">You use the [struct](./language-reference/keywords/struct.md) keyword to create your own custom value types.</span></span> <span data-ttu-id="9936e-123">通常、構造体は、次の例に示すように、少数の関連する変数のコンテナーとして使用します。</span><span class="sxs-lookup"><span data-stu-id="9936e-123">Typically, a struct is used as a container for a small set of related variables, as shown in the following example:</span></span>  
  
<span data-ttu-id="9936e-124">[!code-csharp[struct キーワード](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]</span><span class="sxs-lookup"><span data-stu-id="9936e-124">[!code-csharp[Struct Keyword](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]</span></span>  
  
<span data-ttu-id="9936e-125">.NET Framework における値の型の詳細については、「[共通型システム](../standard/common-type-system.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9936e-125">For more information about value types in the .NET Framework, see [Common Type System](../standard/common-type-system.md).</span></span>  
    
<span data-ttu-id="9936e-126">構造体は、構文上はクラスとほとんど変わりませんが、次のようにクラスよりも制限されます。</span><span class="sxs-lookup"><span data-stu-id="9936e-126">Structs share most of the same syntax as classes, although structs are more limited than classes:</span></span>  
  
-   <span data-ttu-id="9936e-127">構造体宣言内では、`const` または `static` と宣言されているフィールド以外は初期化できません。</span><span class="sxs-lookup"><span data-stu-id="9936e-127">Within a struct declaration, fields cannot be initialized unless they are declared as `const` or `static`.</span></span>  
  
-   <span data-ttu-id="9936e-128">構造体では、既定のコンストラクター (パラメーターなしのコンストラクター) やファイナライザーを宣言できません。</span><span class="sxs-lookup"><span data-stu-id="9936e-128">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
  
-   <span data-ttu-id="9936e-129">構造体は、割り当て時にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="9936e-129">Structs are copied on assignment.</span></span> <span data-ttu-id="9936e-130">構造体を新しい変数に割り当てると、すべてのデータがコピーされ、新しいコピーを変更しても、元のコピーのデータは変更されません。</span><span class="sxs-lookup"><span data-stu-id="9936e-130">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="9936e-131">これは、Dictionary<string, myStruct> などの値の型のコレクションを使用する際に重要です。</span><span class="sxs-lookup"><span data-stu-id="9936e-131">This is important to remember when working with collections of value types such as Dictionary<string, myStruct>.</span></span>  
  
-   <span data-ttu-id="9936e-132">構造体は値型ですが、クラスは参照型です。</span><span class="sxs-lookup"><span data-stu-id="9936e-132">Structs are value types and classes are reference types.</span></span>  
  
-   <span data-ttu-id="9936e-133">クラスとは異なり、構造体は `new` 演算子を使用せずにインスタンス化できます。</span><span class="sxs-lookup"><span data-stu-id="9936e-133">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
  
-   <span data-ttu-id="9936e-134">構造体は、パラメーターのあるコンストラクターを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="9936e-134">Structs can declare constructors that have parameters.</span></span>  
  
-   <span data-ttu-id="9936e-135">構造体は、他の構造体やクラスから継承できず、基本クラスになることはできません。</span><span class="sxs-lookup"><span data-stu-id="9936e-135">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="9936e-136">すべての構造体が @System.ValueType を直接継承し、System.ValueType は @System.Object を継承します。</span><span class="sxs-lookup"><span data-stu-id="9936e-136">All structs inherit directly from @System.ValueType, which inherits from @System.Object.</span></span>  
  
-   <span data-ttu-id="9936e-137">構造体は、インターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="9936e-137">A struct can implement interfaces.</span></span>

## <a name="literal-values"></a><span data-ttu-id="9936e-138">リテラル値</span><span class="sxs-lookup"><span data-stu-id="9936e-138">Literal values</span></span>  
<span data-ttu-id="9936e-139">C# では、リテラル値の型がコンパイラによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="9936e-139">In C#, literal values receive a type from the compiler.</span></span> <span data-ttu-id="9936e-140">数値リテラルの型指定の方法を指定するには、その数値の末尾に文字を付加します。</span><span class="sxs-lookup"><span data-stu-id="9936e-140">You can specify how a numeric literal should be typed by appending a letter to the end of the number.</span></span> <span data-ttu-id="9936e-141">たとえば、値 4.56 を float 型として扱うには、数値の後に "f" または "F" を付加して、`4.56f` のように指定します。</span><span class="sxs-lookup"><span data-stu-id="9936e-141">For example, to specify that the value 4.56 should be treated as a float, append an "f" or "F" after the number: `4.56f`.</span></span> <span data-ttu-id="9936e-142">文字を付加しない場合、リテラルの `double` 型はコンパイラによって推論されます。</span><span class="sxs-lookup"><span data-stu-id="9936e-142">If no letter is appended, the compiler will infer the `double` type for the literal.</span></span> <span data-ttu-id="9936e-143">文字サフィックスによって指定できる型の詳細については、「[値型](./language-reference/keywords/value-types.md)」の各型のリファレンス ページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9936e-143">For more information about which types can be specified with letter suffixes, see the reference pages for individual types in [Value Types](./language-reference/keywords/value-types.md).</span></span>  
  
<span data-ttu-id="9936e-144">リテラルは型指定され、すべての型は最終的に @System.Object から派生するため、次のようなコードを記述してコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="9936e-144">Because literals are typed, and all types derive ultimately from @System.Object, you can write and compile code such as the following:</span></span>  
  
<span data-ttu-id="9936e-145">[!code-csharp[リテラル値](../../samples/snippets/csharp/concepts/structs/literals.cs)]</span><span class="sxs-lookup"><span data-stu-id="9936e-145">[!code-csharp[Literal Values](../../samples/snippets/csharp/concepts/structs/literals.cs)]</span></span>

<span data-ttu-id="9936e-146">最後の 2 つの例では、C# 7.0 で導入された言語機能を紹介します。</span><span class="sxs-lookup"><span data-stu-id="9936e-146">The last two examples demonstrate language features introduced in C# 7.0.</span></span> <span data-ttu-id="9936e-147">最初の機能を使用すると、アンダースコア文字を、数値リテラルの "*桁区切り記号*" として使用できます。</span><span class="sxs-lookup"><span data-stu-id="9936e-147">The first allows you to use an underscore character as a *digit separator* inside numeric literals.</span></span> <span data-ttu-id="9936e-148">このアンダースコア文字を数字の任意の場所に配置して、読みやすくすることができます。</span><span class="sxs-lookup"><span data-stu-id="9936e-148">You can put them wherever you want between digits to improve readability.</span></span> <span data-ttu-id="9936e-149">値には影響はありません。</span><span class="sxs-lookup"><span data-stu-id="9936e-149">They have no effect on the value.</span></span>

<span data-ttu-id="9936e-150">もう 1 つの機能は "*バイナリ リテラル*" で、これにより 16 進数表記ではなく、ビット パターンを直接指定できます。</span><span class="sxs-lookup"><span data-stu-id="9936e-150">The second demonstrates *binary literals*, which allow you to specify bit patterns directly instead of using hexadecimal notation.</span></span>

## <a name="nullable-types"></a><span data-ttu-id="9936e-151">Null 許容型</span><span class="sxs-lookup"><span data-stu-id="9936e-151">Nullable types</span></span>  
<span data-ttu-id="9936e-152">値型には、通常、[null](./language-reference/keywords/null.md) 値を割り当てることができません。</span><span class="sxs-lookup"><span data-stu-id="9936e-152">Ordinary value types cannot have a value of [null](./language-reference/keywords/null.md).</span></span> <span data-ttu-id="9936e-153">しかし、型の後ろに **?** </span><span class="sxs-lookup"><span data-stu-id="9936e-153">However, you can create nullable value types by affixing a **?**</span></span> <span data-ttu-id="9936e-154">を付けることによって、null 値を設定できる値型を作成できます。</span><span class="sxs-lookup"><span data-stu-id="9936e-154">after the type.</span></span> <span data-ttu-id="9936e-155">たとえば、**int?** は、[null](./language-reference/keywords/null.md) も設定できる **int** 型です。</span><span class="sxs-lookup"><span data-stu-id="9936e-155">For example, **int?** is an **int** type that can also have the value [null](./language-reference/keywords/null.md).</span></span> <span data-ttu-id="9936e-156">CTS では、null 許容型は一般的な構造体型 @System.Nullable%601 のインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="9936e-156">In the CTS, nullable types are instances of the generic struct type @System.Nullable%601.</span></span> <span data-ttu-id="9936e-157">Null 許容型は、数値が null になる可能性のあるデータベースとの間でデータを受け渡しする場合に、特に便利です。</span><span class="sxs-lookup"><span data-stu-id="9936e-157">Nullable types are especially useful when you are passing data to and from databases in which numeric values might be null.</span></span> <span data-ttu-id="9936e-158">詳細については、「[null 許容型 (C# プログラミング ガイド)](./programming-guide/nullable-types/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9936e-158">For more information, see [Nullable Types (C# Programming Guide)](./programming-guide/nullable-types/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9936e-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="9936e-159">See also</span></span>
[<span data-ttu-id="9936e-160">クラス</span><span class="sxs-lookup"><span data-stu-id="9936e-160">Classes</span></span>](classes.md)

[<span data-ttu-id="9936e-161">基本型</span><span class="sxs-lookup"><span data-stu-id="9936e-161">Basic Types</span></span>](basic-types.md)

