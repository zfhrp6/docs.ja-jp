---
title: ジェネリック (F#)
description: F# の汎用的な機能とコードを繰り返すことがなく、さまざまな種類で動作するコードを記述する型を使用する方法を説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 332e42dd53689440757da04727b69eb3d85ca0fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="generics"></a><span data-ttu-id="8148f-103">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="8148f-103">Generics</span></span>

<span data-ttu-id="8148f-104">F# の関数値、メソッド、プロパティ、および集約型 (クラス、レコード、判別共用体など) は、*ジェネリック*にすることができます。</span><span class="sxs-lookup"><span data-stu-id="8148f-104">F# function values, methods, properties, and aggregate types such as classes, records, and discriminated unions can be *generic*.</span></span> <span data-ttu-id="8148f-105">ジェネリック コンストラクトには、少なくとも 1 つの型パラメーターが含まれます。この型は、通常、ジェネリック コンストラクトのユーザーによって指定されます。</span><span class="sxs-lookup"><span data-stu-id="8148f-105">Generic constructs contain at least one type parameter, which is usually supplied by the user of the generic construct.</span></span> <span data-ttu-id="8148f-106">ジェネリック関数とジェネリック型を使用すると、型ごとにコードを繰り返し記述しなくても、さまざまな型で動作するコードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="8148f-106">Generic functions and types enable you to write code that works with a variety of types without repeating the code for each type.</span></span> <span data-ttu-id="8148f-107">多くの場合、F# のコードは、コンパイラの型推論と自動ジェネリック化メカニズムによって、暗黙的にジェネリックとして推論されるため、F# では、コードを簡単にジェネリックにできる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8148f-107">Making your code generic can be simple in F#, because often your code is implicitly inferred to be generic by the compiler's type inference and automatic generalization mechanisms.</span></span>


## <a name="syntax"></a><span data-ttu-id="8148f-108">構文</span><span class="sxs-lookup"><span data-stu-id="8148f-108">Syntax</span></span>

```fsharp
// Explicitly generic function.
let function-name<type-parameters> parameter-list =
function-body

// Explicitly generic method.
[ static ] member object-identifer.method-name<type-parameters> parameter-list [ return-type ] =
method-body

// Explicitly generic class, record, interface, structure,
// or discriminated union.
type type-name<type-parameters> type-definition
```

## <a name="remarks"></a><span data-ttu-id="8148f-109">コメント</span><span class="sxs-lookup"><span data-stu-id="8148f-109">Remarks</span></span>
<span data-ttu-id="8148f-110">明示的なジェネリック関数やジェネリック型の宣言は、非ジェネリックの関数や型の宣言によく似ていますが、型パラメーターの指定 (および使用) 方法が異なり、型パラメーターは、関数名または型名の後ろに山かっこで囲んで指定します。</span><span class="sxs-lookup"><span data-stu-id="8148f-110">The declaration of an explicitly generic function or type is much like that of a non-generic function or type, except for the specification (and use) of the type parameters, in angle brackets after the function or type name.</span></span>

<span data-ttu-id="8148f-111">宣言は、多くの場合、暗黙的にジェネリックになります。</span><span class="sxs-lookup"><span data-stu-id="8148f-111">Declarations are often implicitly generic.</span></span> <span data-ttu-id="8148f-112">関数または型の作成に使用されるすべてのパラメーターの型が完全に指定されていない場合、コンパイラは、記述されたコードから、それぞれのパラメーター、値、および変数の型を推論しようと試みます。</span><span class="sxs-lookup"><span data-stu-id="8148f-112">If you do not fully specify the type of every parameter that is used to compose a function or type, the compiler attempts to infer the type of each parameter, value, and variable from the code you write.</span></span> <span data-ttu-id="8148f-113">詳細については、「[Type Inference](../type-inference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8148f-113">For more information, see [Type Inference](../type-inference.md).</span></span> <span data-ttu-id="8148f-114">型や関数のコードによってパラメーターの型が特に制約されない場合、その関数または型は暗黙的にジェネリックとなります。</span><span class="sxs-lookup"><span data-stu-id="8148f-114">If the code for your type or function does not otherwise constrain the types of parameters, the function or type is implicitly generic.</span></span> <span data-ttu-id="8148f-115">このプロセスは、*自動ジェネリック化*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="8148f-115">This process is named *automatic generalization*.</span></span> <span data-ttu-id="8148f-116">自動ジェネリック化にいくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="8148f-116">There are some limits on automatic generalization.</span></span> <span data-ttu-id="8148f-117">たとえば、F# コンパイラがジェネリック コンストラクトの型を推論できない場合、コンパイラは、*値の制限*と呼ばれる制約を示すエラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="8148f-117">For example, if the F# compiler is unable to infer the types for a generic construct, the compiler reports an error that refers to a restriction called the *value restriction*.</span></span> <span data-ttu-id="8148f-118">この場合、型の注釈の追加が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="8148f-118">In that case, you may have to add some type annotations.</span></span> <span data-ttu-id="8148f-119">自動ジェネリック化と値の制限の詳細、およびコードを変更して問題に対処する方法については、「[自動ジェネリック化](automatic-generalization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8148f-119">For more information about automatic generalization and the value restriction, and how to change your code to address the problem, see [Automatic Generalization](automatic-generalization.md).</span></span>

<span data-ttu-id="8148f-120">前の構文の *type-parameters* は、未知の型を表すパラメーターのコンマ区切りのリストです。それぞれは単一引用符から開始し、必要に応じて、その型パラメーターで使用できる型をさらに制限する制約句を指定します。</span><span class="sxs-lookup"><span data-stu-id="8148f-120">In the previous syntax, *type-parameters* is a comma-separated list of parameters that represent unknown types, each of which starts with a single quotation mark, optionally with a constraint clause that further limits what types may be used for that type parameter.</span></span> <span data-ttu-id="8148f-121">制約句の構文および制約に関するその他の情報については、「[制約](constraints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8148f-121">For the syntax for constraint clauses of various kinds and other information about constraints, see [Constraints](constraints.md).</span></span>

<span data-ttu-id="8148f-122">構文の *type-definition* は、非ジェネリック型の型定義と同じです。</span><span class="sxs-lookup"><span data-stu-id="8148f-122">The *type-definition* in the syntax is the same as the type definition for a non-generic type.</span></span> <span data-ttu-id="8148f-123">これには、クラス型のコンストラクター パラメーター、オプションの `as` 句、等号、レコード フィールド、`inherit` 句、判別共用体の選択、`let` バインドと `do` バインド、メンバー定義、および非ジェネリック型定義で許可されている他の任意の記述が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8148f-123">It includes the constructor parameters for a class type, an optional `as` clause, the equal symbol, the record fields, the `inherit` clause, the choices for a discriminated union, `let` and `do` bindings, member definitions, and anything else permitted in a non-generic type definition.</span></span>

<span data-ttu-id="8148f-124">その他の構文要素は、非ジェネリック関数および非ジェネリック型と同じです。</span><span class="sxs-lookup"><span data-stu-id="8148f-124">The other syntax elements are the same as those for non-generic functions and types.</span></span> <span data-ttu-id="8148f-125">たとえば、*object-identifier* は、それを含むオブジェクト自体を表す識別子です。</span><span class="sxs-lookup"><span data-stu-id="8148f-125">For example, *object-identifier* is an identifier that represents the containing object itself.</span></span>

<span data-ttu-id="8148f-126">プロパティ、フィールド、およびコンストラクターは、それを囲む型よりもジェネリックにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="8148f-126">Properties, fields, and constructors cannot be more generic than the enclosing type.</span></span> <span data-ttu-id="8148f-127">また、モジュール内の値をジェネリックにすることもできません。</span><span class="sxs-lookup"><span data-stu-id="8148f-127">Also, values in a module cannot be generic.</span></span>


## <a name="implicitly-generic-constructs"></a><span data-ttu-id="8148f-128">暗黙的なジェネリック コンストラクト</span><span class="sxs-lookup"><span data-stu-id="8148f-128">Implicitly Generic Constructs</span></span>
<span data-ttu-id="8148f-129">F# コンパイラがコード内の型を推論するとき、ジェネリックにできる関数はすべて自動的にジェネリックとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="8148f-129">When the F# compiler infers the types in your code, it automatically treats any function that can be generic as generic.</span></span> <span data-ttu-id="8148f-130">パラメーター型など、型を明示的に指定すると、自動ジェネリック化を回避できます。</span><span class="sxs-lookup"><span data-stu-id="8148f-130">If you specify a type explicitly, such as a parameter type, you prevent automatic generalization.</span></span>

<span data-ttu-id="8148f-131">次のコード例では、`makeList` とそのパラメーターはいずれもジェネリックとして明示的に宣言されていませんが、makeList はジェネリックになります。</span><span class="sxs-lookup"><span data-stu-id="8148f-131">In the following code example, `makeList` is generic, even though neither it nor its parameters are explicitly declared as generic.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1700.fs)]

<span data-ttu-id="8148f-132">関数のシグネチャは、`'a -> 'a -> 'a list` と推論されます。</span><span class="sxs-lookup"><span data-stu-id="8148f-132">The signature of the function is inferred to be `'a -> 'a -> 'a list`.</span></span> <span data-ttu-id="8148f-133">この例で、`a` と `b` は同じ型と推論されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8148f-133">Note that `a` and `b` in this example are inferred to have the same type.</span></span> <span data-ttu-id="8148f-134">これは、いずれも同じリストに含まれており、1 つのリスト内の要素はすべて同じ型でなければならないためです。</span><span class="sxs-lookup"><span data-stu-id="8148f-134">This is because they are included in a list together, and all elements of a list must be of the same type.</span></span>

<span data-ttu-id="8148f-135">関数をジェネリックにするには、型の注釈で単一引用符の構文を使用して、パラメーター型がジェネリック型パラメーターであることを示す方法もあります。</span><span class="sxs-lookup"><span data-stu-id="8148f-135">You can also make a function generic by using the single quotation mark syntax in a type annotation to indicate that a parameter type is a generic type parameter.</span></span> <span data-ttu-id="8148f-136">次のコードでは、この方法でパラメーターが型パラメーターとして宣言されているため、`function1` はジェネリックになります。</span><span class="sxs-lookup"><span data-stu-id="8148f-136">In the following code, `function1` is generic because its parameters are declared in this manner, as type parameters.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1701.fs)]
    
## <a name="explicitly-generic-constructs"></a><span data-ttu-id="8148f-137">明示的なジェネリック コンストラクト</span><span class="sxs-lookup"><span data-stu-id="8148f-137">Explicitly Generic Constructs</span></span>
<span data-ttu-id="8148f-138">山かっこ (`<type-parameter>`) 内で型パラメーターを明示的に宣言することで、関数をジェネリックにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="8148f-138">You can also make a function generic by explicitly declaring its type parameters in angle brackets (`<type-parameter>`).</span></span> <span data-ttu-id="8148f-139">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="8148f-139">The following code illustrates this.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1703.fs)]
    
## <a name="using-generic-constructs"></a><span data-ttu-id="8148f-140">ジェネリック コンストラクトの使用</span><span class="sxs-lookup"><span data-stu-id="8148f-140">Using Generic Constructs</span></span>
<span data-ttu-id="8148f-141">ジェネリック関数またはジェネリック メソッドを使用する場合、型引数を指定しなくてもよいことがあります。</span><span class="sxs-lookup"><span data-stu-id="8148f-141">When you use generic functions or methods, you might not have to specify the type arguments.</span></span> <span data-ttu-id="8148f-142">コンパイラは、型推論を使用して適切な型引数を推論します。</span><span class="sxs-lookup"><span data-stu-id="8148f-142">The compiler uses type inference to infer the appropriate type arguments.</span></span> <span data-ttu-id="8148f-143">あいまいさが残っている場合は、山かっこ内に型引数を指定できます。複数の型引数を指定する場合はコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="8148f-143">If there is still an ambiguity, you can supply type arguments in angle brackets, separating multiple type arguments with commas.</span></span>

<span data-ttu-id="8148f-144">次のコードでは、前のセクションで説明した関数の使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8148f-144">The following code shows the use of the functions that are defined in the previous sections.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1702.fs)]
    
>[!NOTE]
<span data-ttu-id="8148f-145">名前でジェネリック型を参照するには、2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="8148f-145">There are two ways to refer to a generic type by name.</span></span> <span data-ttu-id="8148f-146">たとえば、1 つの型引数 `list` を持つジェネリック型 `int` を参照する方法として、`list<int>` と `int list` の 2 つがあります</span><span class="sxs-lookup"><span data-stu-id="8148f-146">For example, `list<int>` and `int list` are two ways to refer to a generic type `list` that has a single type argument `int`.</span></span> <span data-ttu-id="8148f-147">後者の形式は、通常、`list` や `option` などの F# の組み込み型でのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="8148f-147">The latter form is conventionally used only with built-in F# types such as `list` and `option`.</span></span> <span data-ttu-id="8148f-148">複数の型引数がある場合、通常は `Dictionary<int, string>` 構文を使用しますが、`(int, string) Dictionary` 構文を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="8148f-148">If there are multiple type arguments, you normally use the syntax `Dictionary<int, string>` but you can also use the syntax `(int, string) Dictionary`.</span></span>

## <a name="wildcards-as-type-arguments"></a><span data-ttu-id="8148f-149">型引数としてのワイルドカード</span><span class="sxs-lookup"><span data-stu-id="8148f-149">Wildcards as Type Arguments</span></span>
<span data-ttu-id="8148f-150">引数がコンパイラによって推論される必要があることを指定するには、名前付き型引数の代わりに、アンダースコアまたはワイルドカード記号 (`_`) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="8148f-150">To specify that a type argument should be inferred by the compiler, you can use the underscore, or wildcard symbol (`_`), instead of a named type argument.</span></span> <span data-ttu-id="8148f-151">これを次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="8148f-151">This is shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1704.fs)]
    
## <a name="constraints-in-generic-types-and-functions"></a><span data-ttu-id="8148f-152">ジェネリック型とジェネリック関数の制約</span><span class="sxs-lookup"><span data-stu-id="8148f-152">Constraints in Generic Types and Functions</span></span>
<span data-ttu-id="8148f-153">ジェネリック型またはジェネリック関数の定義では、ジェネリック型パラメーターで使用できることがわかっているコンストラクトのみを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8148f-153">In a generic type or function definition, you can use only those constructs that are known to be available on the generic type parameter.</span></span> <span data-ttu-id="8148f-154">この制限は、コンパイル時に関数呼び出しやメソッド呼び出しを検証できるようにするために必要です。</span><span class="sxs-lookup"><span data-stu-id="8148f-154">This is required to enable the verification of function and method calls at compile time.</span></span> <span data-ttu-id="8148f-155">型パラメーターを明示的に宣言する場合は、ジェネリック型パラメーターに明示的な制約を適用して、特定のメソッドおよび関数を使用できることをコンパイラに通知できます。</span><span class="sxs-lookup"><span data-stu-id="8148f-155">If you declare your type parameters explicitly, you can apply an explicit constraint to a generic type parameter to notify the compiler that certain methods and functions are available.</span></span> <span data-ttu-id="8148f-156">ただし、F# コンパイラがジェネリック パラメーターの型を推論できるようにすると、コンパイラが自動的に適切な制約を決定します。</span><span class="sxs-lookup"><span data-stu-id="8148f-156">However, if you allow the F# compiler to infer your generic parameter types, it will determine the appropriate constraints for you.</span></span> <span data-ttu-id="8148f-157">詳細については、「[制約](constraints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8148f-157">For more information, see [Constraints](constraints.md).</span></span>


## <a name="statically-resolved-type-parameters"></a><span data-ttu-id="8148f-158">静的に解決される型パラメーター</span><span class="sxs-lookup"><span data-stu-id="8148f-158">Statically Resolved Type Parameters</span></span>
<span data-ttu-id="8148f-159">F# プログラムで使用できる型パラメーターには、2 つの種類があります。</span><span class="sxs-lookup"><span data-stu-id="8148f-159">There are two kinds of type parameters that can be used in F# programs.</span></span> <span data-ttu-id="8148f-160">1 つ目は、前のセクションで説明した種類のジェネリック型パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="8148f-160">The first are generic type parameters of the kind described in the previous sections.</span></span> <span data-ttu-id="8148f-161">1 つ目の種類の型パラメーターは、Visual Basic や C# などの言語で使用されるジェネリック型パラメーターと同等です。</span><span class="sxs-lookup"><span data-stu-id="8148f-161">This first kind of type parameter is equivalent to the generic type parameters that are used in languages such as Visual Basic and C#.</span></span> <span data-ttu-id="8148f-162">もう 1 つの種類の型パラメーターは F# に固有のもので、*静的に解決される型パラメーター*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="8148f-162">Another kind of type parameter is specific to F# and is referred to as a *statically resolved type parameter*.</span></span> <span data-ttu-id="8148f-163">これらのコンストラクトの詳細については、「[Statically Resolved Type Parameters](statically-resolved-type-parameters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8148f-163">For information about these constructs, see [Statically Resolved Type Parameters](statically-resolved-type-parameters.md).</span></span>


## <a name="examples"></a><span data-ttu-id="8148f-164">使用例</span><span class="sxs-lookup"><span data-stu-id="8148f-164">Examples</span></span>
[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1705.fs)]
    
## <a name="see-also"></a><span data-ttu-id="8148f-165">関連項目</span><span class="sxs-lookup"><span data-stu-id="8148f-165">See Also</span></span>
[<span data-ttu-id="8148f-166">言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="8148f-166">Language Reference</span></span>](../index.md)

[<span data-ttu-id="8148f-167">型</span><span class="sxs-lookup"><span data-stu-id="8148f-167">Types</span></span>](../fsharp-types.md)

[<span data-ttu-id="8148f-168">静的に解決される型パラメーター</span><span class="sxs-lookup"><span data-stu-id="8148f-168">Statically Resolved Type Parameters</span></span>](statically-resolved-type-parameters.md)

[<span data-ttu-id="8148f-169">.NET Framework におけるジェネリック</span><span class="sxs-lookup"><span data-stu-id="8148f-169">Generics in the .NET Framework</span></span>](~/docs/standard/generics/index.md)

[<span data-ttu-id="8148f-170">自動ジェネリック化</span><span class="sxs-lookup"><span data-stu-id="8148f-170">Automatic Generalization</span></span>](automatic-generalization.md)

[<span data-ttu-id="8148f-171">制約</span><span class="sxs-lookup"><span data-stu-id="8148f-171">Constraints</span></span>](constraints.md)
