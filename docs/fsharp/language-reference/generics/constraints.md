---
title: "制約 (F#)"
description: "ジェネリック型または関数の型引数の要件を指定してジェネリック型パラメーターに適用される f# 制約について説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2f232a3a-9486-48fb-9759-f23404ed4b52
ms.openlocfilehash: 91854fd2f692688e0f1c27aba1422eff64156048
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="constraints"></a><span data-ttu-id="14afc-104">制約</span><span class="sxs-lookup"><span data-stu-id="14afc-104">Constraints</span></span>

<span data-ttu-id="14afc-105">このトピックには、ジェネリックに適用可能な制約がについて説明します、ジェネリック型または関数の型引数の要件を指定するパラメータを入力します。</span><span class="sxs-lookup"><span data-stu-id="14afc-105">This topic describes constraints that you can apply to generic type parameters to specify the requirements for a type argument in a generic type or function.</span></span>


## <a name="syntax"></a><span data-ttu-id="14afc-106">構文</span><span class="sxs-lookup"><span data-stu-id="14afc-106">Syntax</span></span>

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a><span data-ttu-id="14afc-107">コメント</span><span class="sxs-lookup"><span data-stu-id="14afc-107">Remarks</span></span>
<span data-ttu-id="14afc-108">これは、いくつかのさまざまな制約を適用すると、ジェネリック型に使用できる型を制限することができます。</span><span class="sxs-lookup"><span data-stu-id="14afc-108">There are several different constraints you can apply to limit the types that can be used in a generic type.</span></span> <span data-ttu-id="14afc-109">次の表は、これらの制約の一覧です。</span><span class="sxs-lookup"><span data-stu-id="14afc-109">The following table lists and describes these constraints.</span></span>

|<span data-ttu-id="14afc-110">制約</span><span class="sxs-lookup"><span data-stu-id="14afc-110">Constraint</span></span>|<span data-ttu-id="14afc-111">構文</span><span class="sxs-lookup"><span data-stu-id="14afc-111">Syntax</span></span>|<span data-ttu-id="14afc-112">説明</span><span class="sxs-lookup"><span data-stu-id="14afc-112">Description</span></span>|
|----------|------|-----------|
|<span data-ttu-id="14afc-113">型の制約</span><span class="sxs-lookup"><span data-stu-id="14afc-113">Type Constraint</span></span>|<span data-ttu-id="14afc-114">*型パラメーター* :&gt; *型*</span><span class="sxs-lookup"><span data-stu-id="14afc-114">*type-parameter* :&gt; *type*</span></span>|<span data-ttu-id="14afc-115">指定された型は、指定した型から同じかまたは派生をする必要がありますか、型がインターフェイスの場合は、指定された型がインターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14afc-115">The provided type must be equal to or derived from the type specified, or, if the type is an interface, the provided type must implement the interface.</span></span>|
|<span data-ttu-id="14afc-116">Null の制約</span><span class="sxs-lookup"><span data-stu-id="14afc-116">Null Constraint</span></span>|<span data-ttu-id="14afc-117">*型パラメーター* : null</span><span class="sxs-lookup"><span data-stu-id="14afc-117">*type-parameter* : null</span></span>|<span data-ttu-id="14afc-118">指定された型は、null リテラルをサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="14afc-118">The provided type must support the null literal.</span></span> <span data-ttu-id="14afc-119">これには、すべて .NET オブジェクトの種類がない f# 一覧、タプル、関数、クラス、レコード、または共用体の型が含まれます。</span><span class="sxs-lookup"><span data-stu-id="14afc-119">This includes all .NET object types but not F# list, tuple, function, class, record, or union types.</span></span>|
|<span data-ttu-id="14afc-120">明示的なメンバーの制約</span><span class="sxs-lookup"><span data-stu-id="14afc-120">Explicit Member Constraint</span></span>|<span data-ttu-id="14afc-121">[(]*型パラメーター* [または... または*型パラメーター*)]: (* メンバー シグネチャ *)</span><span class="sxs-lookup"><span data-stu-id="14afc-121">[(]*type-parameter* [or ... or *type-parameter*)] : (*member-signature *)</span></span>|<span data-ttu-id="14afc-122">指定された型引数の少なくとも 1 つを指定の署名を持つメンバーがあります。一般的な用途のものでありません。</span><span class="sxs-lookup"><span data-stu-id="14afc-122">At least one of the type arguments provided must have a member that has the specified signature; not intended for common use.</span></span> <span data-ttu-id="14afc-123">メンバー必要がありますか、明示的に定義する、明示的なメンバーの制約の有効なターゲットにするには、型または暗黙的な型の拡張機能の一部にできます。</span><span class="sxs-lookup"><span data-stu-id="14afc-123">Members must be either explicitly defined on the type or part of an implicit type extension to be valid targets for an Explicit Member Constraint.</span></span>|
|<span data-ttu-id="14afc-124">コンス トラクターの制約</span><span class="sxs-lookup"><span data-stu-id="14afc-124">Constructor Constraint</span></span>|<span data-ttu-id="14afc-125">*型パラメーター* : (新しい: 単位 -&gt; ' を)</span><span class="sxs-lookup"><span data-stu-id="14afc-125">*type-parameter* : ( new : unit -&gt; 'a )</span></span>|<span data-ttu-id="14afc-126">指定された型は、既定のコンス トラクターをいる必要があります。</span><span class="sxs-lookup"><span data-stu-id="14afc-126">The provided type must have a default constructor.</span></span>|
|<span data-ttu-id="14afc-127">値型の制約</span><span class="sxs-lookup"><span data-stu-id="14afc-127">Value Type Constraint</span></span>|<span data-ttu-id="14afc-128">: 構造体</span><span class="sxs-lookup"><span data-stu-id="14afc-128">: struct</span></span>|<span data-ttu-id="14afc-129">指定された型は、.NET 値型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="14afc-129">The provided type must be a .NET value type.</span></span>|
|<span data-ttu-id="14afc-130">参照型の制約</span><span class="sxs-lookup"><span data-stu-id="14afc-130">Reference Type Constraint</span></span>|<span data-ttu-id="14afc-131">: 構造体ではありません</span><span class="sxs-lookup"><span data-stu-id="14afc-131">: not struct</span></span>|<span data-ttu-id="14afc-132">指定された型は、.NET 参照型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="14afc-132">The provided type must be a .NET reference type.</span></span>|
|<span data-ttu-id="14afc-133">列挙型の制約</span><span class="sxs-lookup"><span data-stu-id="14afc-133">Enumeration Type Constraint</span></span>|<span data-ttu-id="14afc-134">: enum&lt;*基になる型*&gt;</span><span class="sxs-lookup"><span data-stu-id="14afc-134">: enum&lt;*underlying-type*&gt;</span></span>|<span data-ttu-id="14afc-135">指定された型を指定した基になる型を持つ列挙型である必要があります。一般的な用途のものでありません。</span><span class="sxs-lookup"><span data-stu-id="14afc-135">The provided type must be an enumerated type that has the specified underlying type; not intended for common use.</span></span>|
|<span data-ttu-id="14afc-136">デリゲートの制約</span><span class="sxs-lookup"><span data-stu-id="14afc-136">Delegate Constraint</span></span>|<span data-ttu-id="14afc-137">: 委任&lt;*組パラメーター型*、*戻り値の型*&gt;</span><span class="sxs-lookup"><span data-stu-id="14afc-137">: delegate&lt;*tuple-parameter-type*, *return-type*&gt;</span></span>|<span data-ttu-id="14afc-138">指定された型必要がありますを指定した引数を持つデリゲート型であるし、戻り値一般的な用途のものでありません。</span><span class="sxs-lookup"><span data-stu-id="14afc-138">The provided type must be a delegate type that has the specified arguments and return value; not intended for common use.</span></span>|
|<span data-ttu-id="14afc-139">比較の制約</span><span class="sxs-lookup"><span data-stu-id="14afc-139">Comparison Constraint</span></span>|<span data-ttu-id="14afc-140">: 比較</span><span class="sxs-lookup"><span data-stu-id="14afc-140">: comparison</span></span>|<span data-ttu-id="14afc-141">指定された型は、比較をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="14afc-141">The provided type must support comparison.</span></span>|
|<span data-ttu-id="14afc-142">等しいかどうかの制約</span><span class="sxs-lookup"><span data-stu-id="14afc-142">Equality Constraint</span></span>|<span data-ttu-id="14afc-143">: 等しいかどうか</span><span class="sxs-lookup"><span data-stu-id="14afc-143">: equality</span></span>|<span data-ttu-id="14afc-144">指定された型は、等しいかどうかをサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="14afc-144">The provided type must support equality.</span></span>|
|<span data-ttu-id="14afc-145">アンマネージの制約</span><span class="sxs-lookup"><span data-stu-id="14afc-145">Unmanaged Constraint</span></span>|<span data-ttu-id="14afc-146">: 管理されていません。</span><span class="sxs-lookup"><span data-stu-id="14afc-146">: unmanaged</span></span>|<span data-ttu-id="14afc-147">指定された型は、アンマネージ型にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="14afc-147">The provided type must be an unmanaged type.</span></span> <span data-ttu-id="14afc-148">アンマネージ型は、プリミティブ型 (`sbyte`、 `byte`、 `char`、 `nativeint`、 `unativeint`、 `float32`、 `float`、 `int16`、 `uint16`、 `int32`、 `uint32`、 `int64`、 `uint64`、または`decimal`)、列挙型、 `nativeptr&lt;_&gt;`、またはその結果、フィールドはすべてのアンマネージ型の非ジェネリック構造体。</span><span class="sxs-lookup"><span data-stu-id="14afc-148">Unmanaged types are either certain primitive types (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, or `decimal`), enumeration types, `nativeptr&lt;_&gt;`, or a non-generic structure whose fields are all unmanaged types.</span></span>|
<span data-ttu-id="14afc-149">利用可能な制約の種類は型でない、一般に、機能を使用するコードがある場合は、制約を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14afc-149">You have to add a constraint when your code has to use a feature that is available on the constraint type but not on types in general.</span></span> <span data-ttu-id="14afc-150">たとえば、クラス型を指定する型の制約を使用する場合は、ジェネリック関数またはジェネリック型では、そのクラスのメソッドのいずれかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="14afc-150">For example, if you use the type constraint to specify a class type, you can use any one of the methods of that class in the generic function or type.</span></span>

<span data-ttu-id="14afc-151">制約を指定する場合があります必要な型パラメーターを明示的に記述する場合、制約、コンパイラがあるないためを使用している機能が実行時の種類を指定する場合がある任意の型で使用できることを確認する方法パラメーター。</span><span class="sxs-lookup"><span data-stu-id="14afc-151">Specifying constraints is sometimes required when writing type parameters explicitly, because without a constraint, the compiler has no way of verifying that the features that you are using will be available on any type that might be supplied at run time for the type parameter.</span></span>

<span data-ttu-id="14afc-152">F# コードで使用する最も一般的な制約は、基底クラスまたはインターフェイスを指定する型の制約です。</span><span class="sxs-lookup"><span data-stu-id="14afc-152">The most common constraints you use in F# code are type constraints that specify base classes or interfaces.</span></span> <span data-ttu-id="14afc-153">その他の制約が f# ライブラリでの算術演算子のオーバー ロードする演算子を実装するために使用または主に f# をサポートするための完全な指定が明示的なメンバー制約などの特定の機能を実装するか、使用します。共通言語ランタイムでサポートされている制約のセット。</span><span class="sxs-lookup"><span data-stu-id="14afc-153">The other constraints are either used by the F# library to implement certain functionality, such as the explicit member constraint, which is used to implement operator overloading for arithmetic operators, or are provided mainly because F# supports the complete set of constraints that is supported by the common language runtime.</span></span>

<span data-ttu-id="14afc-154">型の推論プロセス中にいくつかの制約は、コンパイラによって自動的に推論されます。</span><span class="sxs-lookup"><span data-stu-id="14afc-154">During the type inference process, some constraints are inferred automatically by the compiler.</span></span> <span data-ttu-id="14afc-155">たとえば、使用する場合、`+`関数に演算子は、コンパイラは、明示的なメンバーの制約式で使用されている変数の型を推測します。</span><span class="sxs-lookup"><span data-stu-id="14afc-155">For example, if you use the `+` operator in a function, the compiler infers an explicit member constraint on variable types that are used in the expression.</span></span>

<span data-ttu-id="14afc-156">次のコードは、いくつか制約宣言を示しています。</span><span class="sxs-lookup"><span data-stu-id="14afc-156">The following code illustrates some constraint declarations.</span></span>

```fsharp
// Base Type Constraint
type Class1<'T when 'T :> System.Exception> =
class end

// Interface Type Constraint
type Class2<'T when 'T :> System.IComparable> = 
class end

// Null constraint
type Class3<'T when 'T : null> =
class end

// Member constraint with static member
type Class4<'T when 'T : (static member staticMethod1 : unit -> 'T) > =
class end

// Member constraint with instance member
type Class5<'T when 'T : (member Method1 : 'T -> int)> =
class end

// Member constraint with property
type Class6<'T when 'T : (member Property1 : int)> =
class end

// Constructor constraint
type Class7<'T when 'T : (new : unit -> 'T)>() =
member val Field = new 'T()

// Reference type constraint
type Class8<'T when 'T : not struct> =
class end

// Enumeration constraint with underlying value specified
type Class9<'T when 'T : enum<uint32>> =
class end

// 'T must implement IComparable, or be an array type with comparable
// elements, or be System.IntPtr or System.UIntPtr. Also, 'T must not have
// the NoComparison attribute.
type Class10<'T when 'T : comparison> =
class end

// 'T must support equality. This is true for any type that does not
// have the NoEquality attribute.
type Class11<'T when 'T : equality> =
class end

type Class12<'T when 'T : delegate<obj * System.EventArgs, unit>> =
class end

type Class13<'T when 'T : unmanaged> =
class end

// Member constraints with two type parameters
// Most often used with static type parameters in inline functions
let inline add(value1 : ^T when ^T : (static member (+) : ^T * ^T -> ^T), value2: ^T) =
value1 + value2

// ^T and ^U must support operator +
let inline heterogenousAdd(value1 : ^T when (^T or ^U) : (static member (+) : ^T * ^U -> ^T), value2 : ^U) =
value1 + value2

// If there are multiple constraints, use the and keyword to separate them.
type Class14<'T,'U when 'T : equality and 'U : equality> =
class end
```

## <a name="see-also"></a><span data-ttu-id="14afc-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="14afc-157">See Also</span></span>
[<span data-ttu-id="14afc-158">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="14afc-158">Generics</span></span>](index.md)

[<span data-ttu-id="14afc-159">制約</span><span class="sxs-lookup"><span data-stu-id="14afc-159">Constraints</span></span>](constraints.md)
