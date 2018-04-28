---
title: let 束縛 (F#)
description: F# の 'let' 束縛で、値または関数関連付け識別子を使用する方法を説明します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 2abc4e05f9f2977501f01f745062e2e7cd611f68
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="let-bindings"></a><span data-ttu-id="face5-103">let 束縛</span><span class="sxs-lookup"><span data-stu-id="face5-103">let Bindings</span></span>

<span data-ttu-id="face5-104">A*バインディング*を値または関数識別子を関連付けます。</span><span class="sxs-lookup"><span data-stu-id="face5-104">A *binding* associates an identifier with a value or function.</span></span> <span data-ttu-id="face5-105">使用する、`let`値または関数に名前をバインドするキーワードです。</span><span class="sxs-lookup"><span data-stu-id="face5-105">You use the `let` keyword to bind a name to a value or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="face5-106">構文</span><span class="sxs-lookup"><span data-stu-id="face5-106">Syntax</span></span>

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a><span data-ttu-id="face5-107">コメント</span><span class="sxs-lookup"><span data-stu-id="face5-107">Remarks</span></span>

<span data-ttu-id="face5-108">`let`バインディング値または関数名の値を 1 つまたは複数定義する式でキーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="face5-108">The `let` keyword is used in binding expressions to define values or function values for one or more names.</span></span> <span data-ttu-id="face5-109">最も単純な形式、`let`式に名前をバインド単純な値では、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="face5-109">The simplest form of the `let` expression binds a name to a simple value, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

<span data-ttu-id="face5-110">新しい行を使用して、識別子から式を分離する場合は、次のコードのように、式の各行をインデントする必要があります。</span><span class="sxs-lookup"><span data-stu-id="face5-110">If you separate the expression from the identifier by using a new line, you must indent each line of the expression, as in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

<span data-ttu-id="face5-111">名前だけではなく名前を含むパターンを指定できますが、たとえば、組、次のコードに示すようにします。</span><span class="sxs-lookup"><span data-stu-id="face5-111">Instead of just a name, a pattern that contains names can be specified, for example, a tuple, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

<span data-ttu-id="face5-112">*式本体*名前を使用する式です。</span><span class="sxs-lookup"><span data-stu-id="face5-112">The *body-expression* is the expression in which the names are used.</span></span> <span data-ttu-id="face5-113">最初の文字と正確に一致を行にインデント、独自の行に式の本体が表示されます、`let`キーワード。</span><span class="sxs-lookup"><span data-stu-id="face5-113">The body expression appears on its own line, indented to line up exactly with the first character in the `let` keyword:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

<span data-ttu-id="face5-114">A`let`バインディング表示できる、クラス型の定義またはローカルのスコープで、モジュール レベルで関数定義のようです。</span><span class="sxs-lookup"><span data-stu-id="face5-114">A `let` binding can appear at the module level, in the definition of a class type, or in local scopes, such as in a function definition.</span></span> <span data-ttu-id="face5-115">A`let`最上位レベルのモジュール内、またはクラス型のバインディングは、式の本体がある必要はありませんが、他のスコープ レベルで式の本体が必要です。</span><span class="sxs-lookup"><span data-stu-id="face5-115">A `let` binding at the top level in a module or in a class type does not need to have a body expression, but at other scope levels, the body expression is required.</span></span> <span data-ttu-id="face5-116">バインドされる名前を使用する前に、任意の時点ではなくが、定義の時点より後、`let`バインディングが表示されたら、次のコードに示すようにします。</span><span class="sxs-lookup"><span data-stu-id="face5-116">The bound names are usable after the point of definition, but not at any point before the `let` binding appears, as is illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]
    
## <a name="function-bindings"></a><span data-ttu-id="face5-117">関数のバインディング</span><span class="sxs-lookup"><span data-stu-id="face5-117">Function Bindings</span></span>

<span data-ttu-id="face5-118">関数バインドは、次のコードに示すように関数名とパラメーターを関数バインドが含まれる点を除いて値のバインディングの規則を適用します。</span><span class="sxs-lookup"><span data-stu-id="face5-118">Function bindings follow the rules for value bindings, except that function bindings include the function name and the parameters, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

<span data-ttu-id="face5-119">一般に、パラメーターは、タプル パターンなどのパターンです。</span><span class="sxs-lookup"><span data-stu-id="face5-119">In general, parameters are patterns, such as a tuple pattern:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

<span data-ttu-id="face5-120">A`let`最後の式の値に評価される式をバインドします。</span><span class="sxs-lookup"><span data-stu-id="face5-120">A `let` binding expression evaluates to the value of the last expression.</span></span> <span data-ttu-id="face5-121">そのため、次のコード例の値では`result`から計算された`100 * function3 (1, 2)`に評価される`300`です。</span><span class="sxs-lookup"><span data-stu-id="face5-121">Therefore, in the following code example, the value of `result` is computed from `100 * function3 (1, 2)`, which evaluates to `300`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

<span data-ttu-id="face5-122">詳細については、「[関数](index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="face5-122">For more information, see [Functions](index.md).</span></span>

## <a name="type-annotations"></a><span data-ttu-id="face5-123">型の注釈</span><span class="sxs-lookup"><span data-stu-id="face5-123">Type Annotations</span></span>

<span data-ttu-id="face5-124">続けてかっこで囲まれたすべての種類名、コロン (:) を含めることによって、型パラメーターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="face5-124">You can specify types for parameters by including a colon (:) followed by a type name, all enclosed in parentheses.</span></span> <span data-ttu-id="face5-125">最後のパラメーターの後にコロンと型を追加することによって、戻り値の型を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="face5-125">You can also specify the type of the return value by appending the colon and type after the last parameter.</span></span> <span data-ttu-id="face5-126">完全な型の注釈に`function1`パラメーター型として整数となる次のようにします。</span><span class="sxs-lookup"><span data-stu-id="face5-126">The full type annotations for `function1`, with integers as the parameter types, would be as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

<span data-ttu-id="face5-127">明示的な型パラメーターがない場合は、型の推論は関数のパラメーターの種類の決定に使用されます。</span><span class="sxs-lookup"><span data-stu-id="face5-127">When there are no explicit type parameters, type inference is used to determine the types of parameters of functions.</span></span> <span data-ttu-id="face5-128">これは、ジェネリックにするパラメーターの型を自動的に一般化するとを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="face5-128">This can include automatically generalizing the type of a parameter to be generic.</span></span>

<span data-ttu-id="face5-129">詳細については、次を参照してください。[自動ジェネリック化](../generics/automatic-generalization.md)と[型の推論](../type-inference.md)です。</span><span class="sxs-lookup"><span data-stu-id="face5-129">For more information, see [Automatic Generalization](../generics/automatic-generalization.md) and [Type Inference](../type-inference.md).</span></span>

## <a name="let-bindings-in-classes"></a><span data-ttu-id="face5-130">クラス内の let 束縛</span><span class="sxs-lookup"><span data-stu-id="face5-130">let Bindings in Classes</span></span>

<span data-ttu-id="face5-131">A`let`バインディングは、構造体またはレコードの種類ではなく、クラス型でに表示されることができます。</span><span class="sxs-lookup"><span data-stu-id="face5-131">A `let` binding can appear in a class type but not in a structure or record type.</span></span> <span data-ttu-id="face5-132">Let クラス型のバインディングを使用するのには、プライマリ コンス トラクターがクラスにあります。</span><span class="sxs-lookup"><span data-stu-id="face5-132">To use a let binding in a class type, the class must have a primary constructor.</span></span> <span data-ttu-id="face5-133">コンス トラクターのパラメーターは、クラス定義の型名の後に必要です。</span><span class="sxs-lookup"><span data-stu-id="face5-133">Constructor parameters must appear after the type name in the class definition.</span></span> <span data-ttu-id="face5-134">A`let`クラス型でのバインディングは、プライベート フィールドとそのクラスの種類と、と共にメンバーを定義します。`do`型、バインド フォームのコードの種類のプライマリ コンス トラクターをします。</span><span class="sxs-lookup"><span data-stu-id="face5-134">A `let` binding in a class type defines private fields and members for that class type and, together with `do` bindings in the type, forms the code for the primary constructor for the type.</span></span> <span data-ttu-id="face5-135">次のコード例は、クラスを表示する`MyClass`プライベート フィールドを持つ`field1`と`field2`です。</span><span class="sxs-lookup"><span data-stu-id="face5-135">The following code examples show a class `MyClass` with private fields `field1` and `field2`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

<span data-ttu-id="face5-136">スコープ`field1`と`field2`は宣言されている型に制限されます。</span><span class="sxs-lookup"><span data-stu-id="face5-136">The scopes of `field1` and `field2` are limited to the type in which they are declared.</span></span> <span data-ttu-id="face5-137">詳細については、次を参照してください。 [ `let`クラス内のバインディング](../members/let-bindings-in-classes.md)と[クラス](../classes.md)です。</span><span class="sxs-lookup"><span data-stu-id="face5-137">For more information, see [`let` Bindings in Classes](../members/let-bindings-in-classes.md) and [Classes](../classes.md).</span></span>

## <a name="type-parameters-in-let-bindings"></a><span data-ttu-id="face5-138">型パラメーターの let 束縛</span><span class="sxs-lookup"><span data-stu-id="face5-138">Type Parameters in let Bindings</span></span>

<span data-ttu-id="face5-139">A`let`型、またはコンピュテーション式で、モジュール レベルでのバインディングは、明示的な型パラメーターを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="face5-139">A `let` binding at the module level, in a type, or in a computation expression can have explicit type parameters.</span></span> <span data-ttu-id="face5-140">Let 関数定義内でようにバインディングを式では、型パラメーターを持つことはできません。</span><span class="sxs-lookup"><span data-stu-id="face5-140">A let binding in an expression, such as within a function definition, cannot have type parameters.</span></span> <span data-ttu-id="face5-141">詳細については、「[ジェネリック](../generics/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="face5-141">For more information, see [Generics](../generics/index.md).</span></span>

## <a name="attributes-on-let-bindings"></a><span data-ttu-id="face5-142">属性の let 束縛</span><span class="sxs-lookup"><span data-stu-id="face5-142">Attributes on let Bindings</span></span>

<span data-ttu-id="face5-143">属性は、最上位レベルに適用できる`let`モジュールの場合、次のコードに示すようにバインドします。</span><span class="sxs-lookup"><span data-stu-id="face5-143">Attributes can be applied to top-level `let` bindings in a module, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]
    
## <a name="scope-and-accessibility-of-let-bindings"></a><span data-ttu-id="face5-144">スコープと使用すると、バインドのユーザー補助機能</span><span class="sxs-lookup"><span data-stu-id="face5-144">Scope and Accessibility of Let Bindings</span></span>

<span data-ttu-id="face5-145">使用すると、バインドで宣言されたエンティティのスコープを含むの部分に制限されます (など、関数、モジュール、ファイルまたはクラス) スコープの後、バインドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="face5-145">The scope of an entity declared with a let binding is limited to the portion of the containing scope (such as a function, module, file or class) after the binding appears.</span></span> <span data-ttu-id="face5-146">そのため、そのことが言えますを使用すると、バインドで名前をスコープ。</span><span class="sxs-lookup"><span data-stu-id="face5-146">Therefore, it can be said that a let binding introduces a name into a scope.</span></span> <span data-ttu-id="face5-147">モジュールでの let-bound 値または関数は、モジュールのクライアントからアクセス モジュールで使用すると、バインディングは、モジュールのパブリックの関数にコンパイルされるため、モジュールにアクセスできる限りです。</span><span class="sxs-lookup"><span data-stu-id="face5-147">In a module, a let-bound value or function is accessible to clients of a module as long as the module is accessible, since the let bindings in a module are compiled into public functions of the module.</span></span> <span data-ttu-id="face5-148">これに対し、クラスで使用すると、バインディングは、クラスにプライベートです。</span><span class="sxs-lookup"><span data-stu-id="face5-148">By contrast, let bindings in a class are private to the class.</span></span>

<span data-ttu-id="face5-149">通常、モジュール内の関数は、クライアント コードで使用する場合、モジュールの名前で修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="face5-149">Normally, functions in modules must be qualified by the name of the module when used by client code.</span></span> <span data-ttu-id="face5-150">たとえば、モジュール`Module1`関数`function1`、ユーザーは指定`Module1.function1`関数を参照します。</span><span class="sxs-lookup"><span data-stu-id="face5-150">For example, if a module `Module1` has a function `function1`, users would specify `Module1.function1` to refer to the function.</span></span>

<span data-ttu-id="face5-151">モジュールのユーザーは、インポート宣言を使用して、モジュール名によって修飾されることがなくそのモジュール内の関数を使用できるようにすることがあります。</span><span class="sxs-lookup"><span data-stu-id="face5-151">Users of a module may use an import declaration to make the functions within that module available for use without being qualified by the module name.</span></span> <span data-ttu-id="face5-152">説明した例では、モジュールのユーザー開くことができる場合は、モジュールのインポート宣言開くを使用して、`Module1`し、その後を参照してください`function1`直接です。</span><span class="sxs-lookup"><span data-stu-id="face5-152">In the example just mentioned, users of the module can in that case open the module by using the import declaration open `Module1` and thereafter refer to `function1` directly.</span></span>

```fsharp
module Module1 =
    let function1 x = x + 1.0

module Module2 =
    let function2 x =
        Module1.function1 x

open Module1

let function3 x =
    function1 x
```

<span data-ttu-id="face5-153">モジュールの一部が属性を持つ[RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15)、つまり、モジュールの名前、公開された関数を修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="face5-153">Some modules have the attribute [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), which means that the functions that they expose must be qualified with the name of the module.</span></span> <span data-ttu-id="face5-154">たとえば、f# List モジュールには、この属性があります。</span><span class="sxs-lookup"><span data-stu-id="face5-154">For example, the F# List module has this attribute.</span></span>

<span data-ttu-id="face5-155">モジュールとアクセス制御の詳細については、次を参照してください。[モジュール](../modules.md)と[アクセス制御](../access-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="face5-155">For more information on modules and access control, see [Modules](../modules.md) and [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="face5-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="face5-156">See Also</span></span>

[<span data-ttu-id="face5-157">関数</span><span class="sxs-lookup"><span data-stu-id="face5-157">Functions</span></span>](index.md)

[<span data-ttu-id="face5-158">クラス内の `let` バインド</span><span class="sxs-lookup"><span data-stu-id="face5-158">`let` Bindings in Classes</span></span>](../members/let-bindings-in-classes.md)
