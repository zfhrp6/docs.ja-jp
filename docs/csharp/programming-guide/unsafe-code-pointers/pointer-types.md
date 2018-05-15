---
title: ポインター型 (C# プログラミング ガイド)
ms.date: 04/20/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1dce99af2f0f5fdab28058c7f56e79625af84500
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="4f0f2-102">ポインター型 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="4f0f2-102">Pointer types (C# Programming Guide)</span></span>

<span data-ttu-id="4f0f2-103">unsafe コンテキストの型には、ポインター型、値型、または参照型を設定できます。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-103">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="4f0f2-104">ポインター型の宣言は、次のいずれかの形式になります。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-104">A pointer type declaration takes one of the following forms:</span></span>

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

<span data-ttu-id="4f0f2-105">ポインター型の `*` の前に指定された型は、**参照型**と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-105">The type specified before the `*` in a pointer type is called the **referrent type**.</span></span> <span data-ttu-id="4f0f2-106">次の型はいずれも参照型になります。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-106">Any of the following types may be a referrent type:</span></span>

- <span data-ttu-id="4f0f2-107">任意の整数型: [sbyte](../../language-reference/keywords/sbyte.md)、[byte](../../language-reference/keywords/byte.md)、[short](../../language-reference/keywords/short.md)、[ushort](../../language-reference/keywords/ushort.md)、[int](../../language-reference/keywords/int.md)、[uint](../../language-reference/keywords/uint.md)、[long](../../language-reference/keywords/long.md)、[ulong](../../language-reference/keywords/ulong.md)。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-107">Any integral type: [sbyte](../../language-reference/keywords/sbyte.md), [byte](../../language-reference/keywords/byte.md), [short](../../language-reference/keywords/short.md), [ushort](../../language-reference/keywords/ushort.md), [int](../../language-reference/keywords/int.md), [uint](../../language-reference/keywords/uint.md), [long](../../language-reference/keywords/long.md), [ulong](../../language-reference/keywords/ulong.md).</span></span>
- <span data-ttu-id="4f0f2-108">任意の浮動小数点型: [float](../../language-reference/keywords/float.md)、[double](../../language-reference/keywords/double.md)。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-108">Any floating point type: [float](../../language-reference/keywords/float.md), [double](../../language-reference/keywords/double.md).</span></span>
- <span data-ttu-id="4f0f2-109">[char](../../language-reference/keywords/char.md)。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-109">[char](../../language-reference/keywords/char.md).</span></span>
- <span data-ttu-id="4f0f2-110">[bool](../../language-reference/keywords/bool.md)。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-110">[bool](../../language-reference/keywords/bool.md).</span></span>
- <span data-ttu-id="4f0f2-111">[decimal](../../language-reference/keywords/decimal.md)。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-111">[decimal](../../language-reference/keywords/decimal.md).</span></span>
- <span data-ttu-id="4f0f2-112">任意の[列挙](../../language-reference/keywords/enum.md)型。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-112">Any [enum](../../language-reference/keywords/enum.md) type.</span></span>
- <span data-ttu-id="4f0f2-113">任意のポインター型。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-113">Any pointer type.</span></span> <span data-ttu-id="4f0f2-114">`void**` などの式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-114">This allows expressions such as `void**`.</span></span>
- <span data-ttu-id="4f0f2-115">アンマネージ型のフィールドのみを含むユーザー定義の struct 型。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-115">Any user-defined struct type that contains fields of unmanaged types only.</span></span>

<span data-ttu-id="4f0f2-116">ポインター型は [object](../../language-reference/keywords/object.md) を継承せず、ポインター型と `object` の間で変換を行う方法はありません。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-116">Pointer types do not inherit from [object](../../language-reference/keywords/object.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="4f0f2-117">また、ボックス化とボックス化解除もポインターをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-117">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="4f0f2-118">ただし、異なるポインター型の間で変換したり、ポインター型と整数型の間で変換したりすることはできます。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-118">However, you can convert between different pointer types and between pointer types and integral types.</span></span>

<span data-ttu-id="4f0f2-119">同じ 1 つの宣言で複数のポインターを宣言する場合、アスタリスク (\*) は基底の型だけに記述します。各ポインター名のプレフィックスとしては使用しません。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-119">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="4f0f2-120">例:</span><span class="sxs-lookup"><span data-stu-id="4f0f2-120">For example:</span></span>

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

<span data-ttu-id="4f0f2-121">オブジェクト参照は、それを指すポインターがあってもガベージ コレクションされる可能性があるため、ポインターによって参照や参照を含む[構造体](../../language-reference/keywords/struct.md)を指すことはできません。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-121">A pointer cannot point to a reference or to a [struct](../../language-reference/keywords/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="4f0f2-122">ガベージ コレクターは、オブジェクトを指すポインター型があるかどうかを追跡しません。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-122">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>

<span data-ttu-id="4f0f2-123">`myType*` 型のポインター変数の値は、`myType` 型の変数のアドレスです。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-123">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="4f0f2-124">ポインター型の宣言の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-124">The following are examples of pointer type declarations:</span></span>

|<span data-ttu-id="4f0f2-125">例</span><span class="sxs-lookup"><span data-stu-id="4f0f2-125">Example</span></span>|<span data-ttu-id="4f0f2-126">説明</span><span class="sxs-lookup"><span data-stu-id="4f0f2-126">Description</span></span>|
|-------------|-----------------|
|`int* p`|<span data-ttu-id="4f0f2-127">`p` は、整数へのポインターです。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-127">`p` is a pointer to an integer.</span></span>|
|`int** p`|<span data-ttu-id="4f0f2-128">`p` は、整数へのポインターのポインターです。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-128">`p` is a pointer to a pointer to an integer.</span></span>|
|`int*[] p`|<span data-ttu-id="4f0f2-129">`p` は、整数へのポインターの 1 次元配列です。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-129">`p` is a single-dimensional array of pointers to integers.</span></span>|
|`char* p`|<span data-ttu-id="4f0f2-130">`p` は、char へのポインターです。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-130">`p` is a pointer to a char.</span></span>|
|`void* p`|<span data-ttu-id="4f0f2-131">`p` は、未知の型へのポインターです。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-131">`p` is a pointer to an unknown type.</span></span>|

<span data-ttu-id="4f0f2-132">ポインター間接演算子 \* を使用すると、ポインター変数が指す位置にあるコンテンツにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-132">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="4f0f2-133">たとえば、次のような宣言があるとします。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-133">For example, consider the following declaration:</span></span>

```csharp
int* myVariable;
```

<span data-ttu-id="4f0f2-134">この例の式 `*myVariable` は、`int` に含まれているアドレスの位置にある `myVariable` 変数を示しています。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-134">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>

<span data-ttu-id="4f0f2-135">トピック「[fixed ステートメント](../../language-reference/keywords/fixed-statement.md)」および「[ポインター変換](../../programming-guide/unsafe-code-pointers/pointer-conversions.md)」に、ポインターの例がいくつか記載されています。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-135">There are several examples of pointers in the topics [fixed Statement](../../language-reference/keywords/fixed-statement.md) and [Pointer Conversions](../../programming-guide/unsafe-code-pointers/pointer-conversions.md).</span></span> <span data-ttu-id="4f0f2-136">次の例は、`unsafe` キーワードと `fixed` ステートメントの使用例と、内部ポインターのインクリメント方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-136">The following example uses the `unsafe` keyword and the `fixed` statement, and shows how to increment an interior pointer.</span></span>  <span data-ttu-id="4f0f2-137">このコードは、コンソール アプリケーションの Main 関数に貼り付けて実行することができます </span><span class="sxs-lookup"><span data-stu-id="4f0f2-137">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="4f0f2-138">これらの例は、[-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) コンパイラ オプションを設定してコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-138">These examples must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option set.</span></span>

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

<span data-ttu-id="4f0f2-139">間接演算子は、`void*` 型のポインターに適用できません。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-139">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="4f0f2-140">ただし、void ポインターと他のポインター型はキャストを使用して相互に変換できます。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-140">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>

<span data-ttu-id="4f0f2-141">ポインターは、`null` にできます。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-141">A pointer can be `null`.</span></span> <span data-ttu-id="4f0f2-142">null ポインターに間接演算子を適用すると、実装で定義されている動作が発生します。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-142">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>

<span data-ttu-id="4f0f2-143">ポインターをメソッド間で引き渡すと、未定義の動作が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-143">Passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="4f0f2-144">たとえば、`in`、`out` または `ref` パラメーターを介してポインターをローカル変数に返したり、関数の結果として返したりするメソッドがあるとします。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-144">Consider a method that returns a pointer to a local variable through an `in`, `out`, or `ref` parameter or as the function result.</span></span> <span data-ttu-id="4f0f2-145">ポインターが固定ブロックに設定されていた場合は、そのポインターが指す変数が既に固定されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-145">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>

<span data-ttu-id="4f0f2-146">次の表は、unsafe コンテキストでポインターに使用できる演算子とステートメントの一覧を示しています。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-146">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>

|<span data-ttu-id="4f0f2-147">演算子/ステートメント</span><span class="sxs-lookup"><span data-stu-id="4f0f2-147">Operator/Statement</span></span>|<span data-ttu-id="4f0f2-148">使用</span><span class="sxs-lookup"><span data-stu-id="4f0f2-148">Use</span></span>|
|-------------------------|---------|
|*|<span data-ttu-id="4f0f2-149">ポインターの間接参照を実行します。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-149">Performs pointer indirection.</span></span>|
|->|<span data-ttu-id="4f0f2-150">ポインター経由で構造体のメンバーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-150">Accesses a member of a struct through a pointer.</span></span>|
|<span data-ttu-id="4f0f2-151">[]</span><span class="sxs-lookup"><span data-stu-id="4f0f2-151">[]</span></span>|<span data-ttu-id="4f0f2-152">ポインターにインデックスを付けます。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-152">Indexes a pointer.</span></span>|
|`&`|<span data-ttu-id="4f0f2-153">変数のアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-153">Obtains the address of a variable.</span></span>|
|<span data-ttu-id="4f0f2-154">++ および --</span><span class="sxs-lookup"><span data-stu-id="4f0f2-154">++ and --</span></span>|<span data-ttu-id="4f0f2-155">ポインターをインクリメントおよびデクリメントします。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-155">Increments and decrements pointers.</span></span>|
|<span data-ttu-id="4f0f2-156">+ および -</span><span class="sxs-lookup"><span data-stu-id="4f0f2-156">+ and -</span></span>|<span data-ttu-id="4f0f2-157">ポインター演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-157">Performs pointer arithmetic.</span></span>|
|<span data-ttu-id="4f0f2-158">==、!=、\<、>、\<=、>=</span><span class="sxs-lookup"><span data-stu-id="4f0f2-158">==, !=, \<, >, \<=, and >=</span></span>|<span data-ttu-id="4f0f2-159">ポインターを比較します。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-159">Compares pointers.</span></span>|
|`stackalloc`|<span data-ttu-id="4f0f2-160">スタックにメモリを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-160">Allocates memory on the stack.</span></span>|
|<span data-ttu-id="4f0f2-161">`fixed` ステートメント</span><span class="sxs-lookup"><span data-stu-id="4f0f2-161">`fixed` statement</span></span>|<span data-ttu-id="4f0f2-162">変数を一時的に固定して、そのアドレスを取得できるようにします。</span><span class="sxs-lookup"><span data-stu-id="4f0f2-162">Temporarily fixes a variable so that its address may be found.</span></span>|

## <a name="c-language-specification"></a><span data-ttu-id="4f0f2-163">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="4f0f2-163">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="4f0f2-164">参照</span><span class="sxs-lookup"><span data-stu-id="4f0f2-164">See Also</span></span>
 [<span data-ttu-id="4f0f2-165">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="4f0f2-165">C# Programming Guide</span></span>](../index.md)  
 [<span data-ttu-id="4f0f2-166">アンセーフ コードとポインター</span><span class="sxs-lookup"><span data-stu-id="4f0f2-166">Unsafe Code and Pointers</span></span>](index.md)  
 [<span data-ttu-id="4f0f2-167">ポインター変換</span><span class="sxs-lookup"><span data-stu-id="4f0f2-167">Pointer Conversions</span></span>](pointer-conversions.md)  
 [<span data-ttu-id="4f0f2-168">ポインター式</span><span class="sxs-lookup"><span data-stu-id="4f0f2-168">Pointer Expressions</span></span>](pointer-expressions.md)  
 [<span data-ttu-id="4f0f2-169">型</span><span class="sxs-lookup"><span data-stu-id="4f0f2-169">Types</span></span>](../../language-reference/keywords/types.md)  
 [<span data-ttu-id="4f0f2-170">unsafe</span><span class="sxs-lookup"><span data-stu-id="4f0f2-170">unsafe</span></span>](../../language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="4f0f2-171">fixed ステートメント</span><span class="sxs-lookup"><span data-stu-id="4f0f2-171">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="4f0f2-172">stackalloc</span><span class="sxs-lookup"><span data-stu-id="4f0f2-172">stackalloc</span></span>](../../language-reference/keywords/stackalloc.md)  
 [<span data-ttu-id="4f0f2-173">ボックス化とボックス化解除</span><span class="sxs-lookup"><span data-stu-id="4f0f2-173">Boxing and Unboxing</span></span>](../types/boxing-and-unboxing.md)
