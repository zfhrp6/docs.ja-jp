---
title: 構造体 - C# ガイド
description: 構造体型と、構造体を作成する方法について説明します
ms.date: 10/12/2016
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.openlocfilehash: 9fe4e0278ecf46f762a93aa489030c0a9e5563b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349770"
---
# <a name="structs"></a><span data-ttu-id="f21db-103">構造体</span><span class="sxs-lookup"><span data-stu-id="f21db-103">Structs</span></span>
<span data-ttu-id="f21db-104">"*構造体*" は値の型です。</span><span class="sxs-lookup"><span data-stu-id="f21db-104">A *struct* is a value type.</span></span> <span data-ttu-id="f21db-105">構造体が作成されると、構造体が割り当てられている変数にはその構造体の実際のデータが設定されます。</span><span class="sxs-lookup"><span data-stu-id="f21db-105">When a struct is created, the variable to which the struct is assigned holds the struct's actual data.</span></span> <span data-ttu-id="f21db-106">構造体が新しい変数に割り当てられると、そのデータがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="f21db-106">When the struct is assigned to a new variable, it is copied.</span></span> <span data-ttu-id="f21db-107">したがって、新しい変数と元の変数には、同じデータのコピーが別個に含まれることになります。</span><span class="sxs-lookup"><span data-stu-id="f21db-107">The new variable and the original variable therefore contain two separate copies of the same data.</span></span> <span data-ttu-id="f21db-108">一方のコピーに対して行われた変更は、もう一方のコピーには影響しません。</span><span class="sxs-lookup"><span data-stu-id="f21db-108">Changes made to one copy do not affect the other copy.</span></span>

<span data-ttu-id="f21db-109">値型の変数は、その値を直接含みます。つまり、変数がどのようなコンテキストで宣言されたとしても、必ずメモリがインラインで割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="f21db-109">Value type variables directly contain their values, which means that the memory is allocated inline in whatever context the variable is declared.</span></span> <span data-ttu-id="f21db-110">値型の変数には、独立したヒープ割り当てやガベージ コレクションのオーバーヘッドはありません。</span><span class="sxs-lookup"><span data-stu-id="f21db-110">There is no separate heap allocation or garbage collection overhead for value-type variables.</span></span>  
  
<span data-ttu-id="f21db-111">値型には、[構造体](./language-reference/keywords/struct.md)と[列挙体](./language-reference/keywords/enum.md)の 2 つのカテゴリがあります。</span><span class="sxs-lookup"><span data-stu-id="f21db-111">There are two categories of value types: [struct](./language-reference/keywords/struct.md) and [enum](./language-reference/keywords/enum.md).</span></span>  
  
<span data-ttu-id="f21db-112">組み込みの数値型は構造体であり、次のようにしてアクセスできるプロパティとメソッドを持ちます。</span><span class="sxs-lookup"><span data-stu-id="f21db-112">The built-in numeric types are structs, and they have properties and methods that you can access:</span></span>  
  
[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]
  
<span data-ttu-id="f21db-113">ただし、宣言とそこへの値の代入は、あたかも単純な非集約型であるかのように行うことができます。</span><span class="sxs-lookup"><span data-stu-id="f21db-113">But you declare and assign values to them as if they were simple non-aggregate types:</span></span>  
  
[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)] 
  
<span data-ttu-id="f21db-114">値型は、"*シール*" されています。たとえば <xref:System.Int32> から値型を派生させることはできません。構造体は <xref:System.ValueType> からしか継承できないため、任意のユーザー定義型または構造体を継承する構造体を定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="f21db-114">Value types are *sealed*, which means, for example, that you cannot derive a type from <xref:System.Int32>, and you cannot define a struct to inherit from any user-defined class or struct because a struct can only inherit from <xref:System.ValueType>.</span></span> <span data-ttu-id="f21db-115">ただし、構造体は 1 つ以上のインターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="f21db-115">However, a struct can implement one or more interfaces.</span></span> <span data-ttu-id="f21db-116">構造体型は、インターフェイス型にキャストできます。これを行うと、"*ボックス化*" 操作によって、構造体がマネージ ヒープ上の参照型オブジェクト内にラップされます。</span><span class="sxs-lookup"><span data-stu-id="f21db-116">You can cast a struct type to an interface type; this causes a *boxing* operation to wrap the struct inside a reference type object on the managed heap.</span></span> <span data-ttu-id="f21db-117">ボックス化操作が発生するのは、入力パラメーターとして <xref:System.Object> を受け取るメソッドに値型を渡した場合です。</span><span class="sxs-lookup"><span data-stu-id="f21db-117">Boxing operations occur when you pass a value type to a method that takes an <xref:System.Object> as an input parameter.</span></span> <span data-ttu-id="f21db-118">詳細については、「[ボックス化とボックス化解除](./programming-guide/types/boxing-and-unboxing.md )」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f21db-118">For more information, see [Boxing and Unboxing](./programming-guide/types/boxing-and-unboxing.md ).</span></span>  
  
<span data-ttu-id="f21db-119">独自のカスタム値型を作成するには、[struct](./language-reference/keywords/struct.md) キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="f21db-119">You use the [struct](./language-reference/keywords/struct.md) keyword to create your own custom value types.</span></span> <span data-ttu-id="f21db-120">通常、構造体は、次の例に示すように、少数の関連する変数のコンテナーとして使用します。</span><span class="sxs-lookup"><span data-stu-id="f21db-120">Typically, a struct is used as a container for a small set of related variables, as shown in the following example:</span></span>  
  
[!code-csharp[Struct Keyword](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]  
  
<span data-ttu-id="f21db-121">.NET Framework における値の型の詳細については、「[共通型システム](../standard/common-type-system.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f21db-121">For more information about value types in the .NET Framework, see [Common Type System](../standard/common-type-system.md).</span></span>  
    
<span data-ttu-id="f21db-122">構造体は、構文上はクラスとほとんど変わりませんが、次のようにクラスよりも制限されます。</span><span class="sxs-lookup"><span data-stu-id="f21db-122">Structs share most of the same syntax as classes, although structs are more limited than classes:</span></span>  
  
-   <span data-ttu-id="f21db-123">構造体宣言内では、`const` または `static` と宣言されているフィールド以外は初期化できません。</span><span class="sxs-lookup"><span data-stu-id="f21db-123">Within a struct declaration, fields cannot be initialized unless they are declared as `const` or `static`.</span></span>  
  
-   <span data-ttu-id="f21db-124">構造体では、既定のコンストラクター (パラメーターなしのコンストラクター) やファイナライザーを宣言できません。</span><span class="sxs-lookup"><span data-stu-id="f21db-124">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
  
-   <span data-ttu-id="f21db-125">構造体は、割り当て時にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="f21db-125">Structs are copied on assignment.</span></span> <span data-ttu-id="f21db-126">構造体を新しい変数に割り当てると、すべてのデータがコピーされ、新しいコピーを変更しても、元のコピーのデータは変更されません。</span><span class="sxs-lookup"><span data-stu-id="f21db-126">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="f21db-127">これは、Dictionary<string, myStruct> などの値の型のコレクションを使用する際に重要です。</span><span class="sxs-lookup"><span data-stu-id="f21db-127">This is important to remember when working with collections of value types such as Dictionary<string, myStruct>.</span></span>  
  
-   <span data-ttu-id="f21db-128">構造体は値型ですが、クラスは参照型です。</span><span class="sxs-lookup"><span data-stu-id="f21db-128">Structs are value types and classes are reference types.</span></span>  
  
-   <span data-ttu-id="f21db-129">クラスとは異なり、構造体は `new` 演算子を使用せずにインスタンス化できます。</span><span class="sxs-lookup"><span data-stu-id="f21db-129">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
  
-   <span data-ttu-id="f21db-130">構造体は、パラメーターのあるコンストラクターを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="f21db-130">Structs can declare constructors that have parameters.</span></span>  
  
-   <span data-ttu-id="f21db-131">構造体は、他の構造体やクラスから継承できず、基本クラスになることはできません。</span><span class="sxs-lookup"><span data-stu-id="f21db-131">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="f21db-132">すべての構造体が <xref:System.ValueType> を直接継承し、System.ValueType は <xref:System.Object> を継承します。</span><span class="sxs-lookup"><span data-stu-id="f21db-132">All structs inherit directly from <xref:System.ValueType>, which inherits from <xref:System.Object>.</span></span>  
  
-   <span data-ttu-id="f21db-133">構造体は、インターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="f21db-133">A struct can implement interfaces.</span></span>

## <a name="literal-values"></a><span data-ttu-id="f21db-134">リテラル値</span><span class="sxs-lookup"><span data-stu-id="f21db-134">Literal values</span></span>  
<span data-ttu-id="f21db-135">C# では、リテラル値の型がコンパイラによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="f21db-135">In C#, literal values receive a type from the compiler.</span></span> <span data-ttu-id="f21db-136">数値リテラルの型指定の方法を指定するには、その数値の末尾に文字を付加します。</span><span class="sxs-lookup"><span data-stu-id="f21db-136">You can specify how a numeric literal should be typed by appending a letter to the end of the number.</span></span> <span data-ttu-id="f21db-137">たとえば、値 4.56 を float 型として扱うには、数値の後に "f" または "F" を付加して、`4.56f` のように指定します。</span><span class="sxs-lookup"><span data-stu-id="f21db-137">For example, to specify that the value 4.56 should be treated as a float, append an "f" or "F" after the number: `4.56f`.</span></span> <span data-ttu-id="f21db-138">文字を付加しない場合、リテラルの `double` 型はコンパイラによって推論されます。</span><span class="sxs-lookup"><span data-stu-id="f21db-138">If no letter is appended, the compiler will infer the `double` type for the literal.</span></span> <span data-ttu-id="f21db-139">文字サフィックスによって指定できる型の詳細については、「[値型](./language-reference/keywords/value-types.md)」の各型のリファレンス ページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f21db-139">For more information about which types can be specified with letter suffixes, see the reference pages for individual types in [Value Types](./language-reference/keywords/value-types.md).</span></span>  
  
<span data-ttu-id="f21db-140">リテラルは型指定され、すべての型は最終的に <xref:System.Object> から派生するため、次のようなコードを記述してコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="f21db-140">Because literals are typed, and all types derive ultimately from <xref:System.Object>, you can write and compile code such as the following:</span></span>  
  
[!code-csharp[Literal Values](../../samples/snippets/csharp/concepts/structs/literals.cs)]

<span data-ttu-id="f21db-141">最後の 2 つの例では、C# 7.0 で導入された言語機能を紹介します。</span><span class="sxs-lookup"><span data-stu-id="f21db-141">The last two examples demonstrate language features introduced in C# 7.0.</span></span> <span data-ttu-id="f21db-142">最初の機能を使用すると、アンダースコア文字を、数値リテラルの "*桁区切り記号*" として使用できます。</span><span class="sxs-lookup"><span data-stu-id="f21db-142">The first allows you to use an underscore character as a *digit separator* inside numeric literals.</span></span> <span data-ttu-id="f21db-143">このアンダースコア文字を数字の任意の場所に配置して、読みやすくすることができます。</span><span class="sxs-lookup"><span data-stu-id="f21db-143">You can put them wherever you want between digits to improve readability.</span></span> <span data-ttu-id="f21db-144">値には影響はありません。</span><span class="sxs-lookup"><span data-stu-id="f21db-144">They have no effect on the value.</span></span>

<span data-ttu-id="f21db-145">もう 1 つの機能は "*バイナリ リテラル*" で、これにより 16 進数表記ではなく、ビット パターンを直接指定できます。</span><span class="sxs-lookup"><span data-stu-id="f21db-145">The second demonstrates *binary literals*, which allow you to specify bit patterns directly instead of using hexadecimal notation.</span></span>

## <a name="nullable-types"></a><span data-ttu-id="f21db-146">Null 許容型</span><span class="sxs-lookup"><span data-stu-id="f21db-146">Nullable types</span></span>  
<span data-ttu-id="f21db-147">値型には、通常、[null](./language-reference/keywords/null.md) 値を割り当てることができません。</span><span class="sxs-lookup"><span data-stu-id="f21db-147">Ordinary value types cannot have a value of [null](./language-reference/keywords/null.md).</span></span> <span data-ttu-id="f21db-148">しかし、型の後ろに **?** </span><span class="sxs-lookup"><span data-stu-id="f21db-148">However, you can create nullable value types by affixing a **?**</span></span> <span data-ttu-id="f21db-149">を付けることによって、null 値を設定できる値型を作成できます。</span><span class="sxs-lookup"><span data-stu-id="f21db-149">after the type.</span></span> <span data-ttu-id="f21db-150">たとえば、**int?** は、[null](./language-reference/keywords/null.md) も設定できる **int** 型です。</span><span class="sxs-lookup"><span data-stu-id="f21db-150">For example, **int?** is an **int** type that can also have the value [null](./language-reference/keywords/null.md).</span></span> <span data-ttu-id="f21db-151">CTS では、null 許容型は一般的な構造体型 <xref:System.Nullable%601> のインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="f21db-151">In the CTS, nullable types are instances of the generic struct type <xref:System.Nullable%601>.</span></span> <span data-ttu-id="f21db-152">Null 許容型は、数値が null になる可能性のあるデータベースとの間でデータを受け渡しする場合に、特に便利です。</span><span class="sxs-lookup"><span data-stu-id="f21db-152">Nullable types are especially useful when you are passing data to and from databases in which numeric values might be null.</span></span> <span data-ttu-id="f21db-153">詳細については、「[null 許容型 (C# プログラミング ガイド)](./programming-guide/nullable-types/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f21db-153">For more information, see [Nullable Types (C# Programming Guide)](./programming-guide/nullable-types/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f21db-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="f21db-154">See also</span></span>
[<span data-ttu-id="f21db-155">クラス</span><span class="sxs-lookup"><span data-stu-id="f21db-155">Classes</span></span>](classes.md)

[<span data-ttu-id="f21db-156">基本型</span><span class="sxs-lookup"><span data-stu-id="f21db-156">Basic Types</span></span>](basic-types.md)
