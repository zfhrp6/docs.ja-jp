---
title: ref 戻り値と ref ローカル変数 (C# ガイド)
description: ref 戻り値と ref ローカル変数を定義して使用する方法について説明します。
author: rpetrusha
ms.author: ronpet
ms.date: 04/04/2018
ms.openlocfilehash: e749b9c9309a4b1a737a0c1d0b5e1cfe5748114a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339619"
---
# <a name="ref-returns-and-ref-locals"></a><span data-ttu-id="87673-103">ref 戻り値と ref ローカル変数</span><span class="sxs-lookup"><span data-stu-id="87673-103">Ref returns and ref locals</span></span>

<span data-ttu-id="87673-104">C# 7.0 以降の C# は参照戻り値 (ref 戻り値) に対応しています。</span><span class="sxs-lookup"><span data-stu-id="87673-104">Starting with C# 7.0, C# supports reference return values (ref returns).</span></span> <span data-ttu-id="87673-105">参照戻り値を使用すると、メソッドから呼び出し元に、値ではなく、変数への参照を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="87673-105">A reference return value allows a method to return a reference to a variable, rather than a value, back to a caller.</span></span> <span data-ttu-id="87673-106">呼び出し元は、返された変数を値渡しとして処理するか、参照渡しとして処理するかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="87673-106">The caller can then choose to treat the returned variable as if it were returned by value or by reference.</span></span> <span data-ttu-id="87673-107">呼び出し元は、それ自体が、返された値の参照である新しい変数を作成できます。これは ref ローカルと呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="87673-107">The caller can create a new variable that is itself a reference to the returned value, called a ref local.</span></span>

## <a name="what-is-a-reference-return-value"></a><span data-ttu-id="87673-108">参照戻り値とは</span><span class="sxs-lookup"><span data-stu-id="87673-108">What is a reference return value?</span></span>

<span data-ttu-id="87673-109">呼び出されたメソッドに参照によって引数を渡す*参照渡し*は、ほとんどの開発者によく知られています。</span><span class="sxs-lookup"><span data-stu-id="87673-109">Most developers are familiar with passing an argument to a called method *by reference*.</span></span> <span data-ttu-id="87673-110">呼び出されたメソッドの引数リストには、参照によって渡された変数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="87673-110">A called method's argument list includes a variable passed by reference.</span></span> <span data-ttu-id="87673-111">呼び出されたメソッドがその値に対して行った変更は、呼び出し元によって観察されます。</span><span class="sxs-lookup"><span data-stu-id="87673-111">Any changes made to its value by the called method are observed by the caller.</span></span> <span data-ttu-id="87673-112">"*参照戻り値*" とは、メソッドが何らかの変数への "*参照*" (または別名) を返すことを意味します。</span><span class="sxs-lookup"><span data-stu-id="87673-112">A *reference return value* means that a method returns a *reference* (or an alias) to some variable.</span></span> <span data-ttu-id="87673-113">その変数のスコープには、メソッドが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="87673-113">That variable's scope must include the method.</span></span> <span data-ttu-id="87673-114">その変数の有効期間は、メソッドから戻った後まで継続している必要があります。</span><span class="sxs-lookup"><span data-stu-id="87673-114">That variable's lifetime must extend beyond the return of the method.</span></span> <span data-ttu-id="87673-115">呼び出し元によるメソッドの戻り値の変更は、メソッドによって返される変数に対して行われます。</span><span class="sxs-lookup"><span data-stu-id="87673-115">Modifications to the method's return value by the caller are made to the variable that is returned by the method.</span></span>

<span data-ttu-id="87673-116">メソッドが*参照戻り値*を返すという宣言があれば、それはそのメソッドが変数にエイリアスを返すことを示します。</span><span class="sxs-lookup"><span data-stu-id="87673-116">Declaring that a method returns a *reference return value* indicates that the method returns an alias to a variable.</span></span> <span data-ttu-id="87673-117">この設計の意図は、多くの場合、呼び出し元のコードが変数の変更などを行うとき、そのコードにはエイリアス経由でその変数にアクセスさせるというものです。</span><span class="sxs-lookup"><span data-stu-id="87673-117">The design intent is often that the calling code should have access to that variable through the alias, including to modify it.</span></span> <span data-ttu-id="87673-118">参照で返すメソッドには戻り値の型 `void` を与えることができません。</span><span class="sxs-lookup"><span data-stu-id="87673-118">It follows that methods returning by reference can't have the return type `void`.</span></span>

<span data-ttu-id="87673-119">メソッドが参照戻り値として返すことができる式には、いくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="87673-119">There are some restrictions on the expression that a method can return as a reference return value.</span></span> <span data-ttu-id="87673-120">次のような制約があります。</span><span class="sxs-lookup"><span data-stu-id="87673-120">Restrictions include:</span></span>

- <span data-ttu-id="87673-121">戻り値の有効期間は、メソッドの実行より長くならないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="87673-121">The return value must have a lifetime that extends beyond the execution of the method.</span></span> <span data-ttu-id="87673-122">言い換えると、値を返すメソッドに含まれているローカル変数にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="87673-122">In other words, it cannot be a local variable in the method that returns it.</span></span> <span data-ttu-id="87673-123">クラスのインスタンスまたは静的フィールドを戻り値にすることができます。または、メソッドに渡される引数を戻り値にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="87673-123">It can be an instance or static field of a class, or it can be an argument passed to the method.</span></span> <span data-ttu-id="87673-124">ローカル変数を返そうとすると、コンパイラ エラー CS8168 "ローカル変数 'obj' は ref ローカル変数ではないため、参照渡しで返すことはできません" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="87673-124">Attempting to return a local variable generates compiler error CS8168, "Cannot return local 'obj' by reference because it is not a ref local."</span></span>

- <span data-ttu-id="87673-125">戻り値はリテラル `null` にすることができません。</span><span class="sxs-lookup"><span data-stu-id="87673-125">The return value cannot be the literal `null`.</span></span> <span data-ttu-id="87673-126">`null` を返すと、コンパイラ エラー CS8156 "参照渡しで返すことができないため、このコンテキストで使用できない式があります" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="87673-126">Returning `null` generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

   <span data-ttu-id="87673-127">ref 戻りを含むメソッドは、現在の値が null (インスタンス化されていない) 値か、値の型が [null 許容型](../nullable-types/index.md)の変数にエイリアスを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="87673-127">A method with a ref return can return an alias to a variable whose value is currently the null (uninstantiated) value or a [nullable type](../nullable-types/index.md) for a value type.</span></span>
 
- <span data-ttu-id="87673-128">戻り値は、定数、列挙型のメンバー、プロパティの値渡し戻り値、`class` または `struct` のメソッドにすることができません。</span><span class="sxs-lookup"><span data-stu-id="87673-128">The return value cannot be a constant, an enumeration member, the by-value return value from a property, or a method of a `class` or `struct`.</span></span> <span data-ttu-id="87673-129">この規則に違反すると、コンパイラ エラー CS8156 "参照渡しで返すことができないため、このコンテキストで使用できない式があります" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="87673-129">Violating this rule generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

<span data-ttu-id="87673-130">さらに、参照戻り値は非同期メソッドでは許可されません。</span><span class="sxs-lookup"><span data-stu-id="87673-130">In addition, reference return values are not allowed on async methods.</span></span> <span data-ttu-id="87673-131">非同期メソッドは実行が終了する前に戻る可能性があり、戻り値はまだ不明です。</span><span class="sxs-lookup"><span data-stu-id="87673-131">An asynchronous method may return before it has finished execution, while its return value is still unknown.</span></span>
 
## <a name="defining-a-ref-return-value"></a><span data-ttu-id="87673-132">ref 戻り値の定義</span><span class="sxs-lookup"><span data-stu-id="87673-132">Defining a ref return value</span></span>

<span data-ttu-id="87673-133">戻り値を定義するには、メソッド シグネチャの戻り値の型に [ref](../../language-reference/keywords/ref.md) キーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="87673-133">You define a ref return value by adding the [ref](../../language-reference/keywords/ref.md) keyword to the return type of the method signature.</span></span> <span data-ttu-id="87673-134">たとえば、次のシグネチャは、`GetContactInformation` プロパティが `Person` オブジェクトへの参照を呼び出し元に返すことを示しています。</span><span class="sxs-lookup"><span data-stu-id="87673-134">For example, the following signature indicates that the `GetContactInformation` property returns a reference to a `Person` object to the caller:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname);
```

<span data-ttu-id="87673-135">さらに、メソッド本文の各 [return](../../language-reference/keywords/return.md) ステートメントによって返されるオブジェクトの名前の前に、[ref](../../language-reference/keywords/ref.md) キーワードが必要です。</span><span class="sxs-lookup"><span data-stu-id="87673-135">In addition, the name of the object returned by each [return](../../language-reference/keywords/return.md) statement in the method body must be preceded by the [ref](../../language-reference/keywords/ref.md) keyword.</span></span> <span data-ttu-id="87673-136">たとえば、次の `return` ステートメントは、`p` という名前の `Person` オブジェクトに参照を返します。</span><span class="sxs-lookup"><span data-stu-id="87673-136">For example, the following `return` statement returns a reference to a `Person` object named `p`:</span></span>

```csharp
return ref p;
```

## <a name="consuming-a-ref-return-value"></a><span data-ttu-id="87673-137">ref 戻り値の使用</span><span class="sxs-lookup"><span data-stu-id="87673-137">Consuming a ref return value</span></span>

<span data-ttu-id="87673-138">ref 戻り値は、呼び出されるメソッドの範囲で、別の変数のエイリアスになります。</span><span class="sxs-lookup"><span data-stu-id="87673-138">The ref return value is an alias to another variable in the called method's scope.</span></span> <span data-ttu-id="87673-139">ref 戻り値の使用は、それが別名を与える変数の使用として解釈できます。</span><span class="sxs-lookup"><span data-stu-id="87673-139">You can interpret any use of the ref return as using the variable it aliases:</span></span>

- <span data-ttu-id="87673-140">その値を割り当てるとき、それが別名を与える変数に値を割り当てることになります。</span><span class="sxs-lookup"><span data-stu-id="87673-140">When you assign its value, you are assigning a value to the variable it aliases.</span></span>
- <span data-ttu-id="87673-141">その値を読み取るとき、それが別名を与える変数の値を読み取ることになります。</span><span class="sxs-lookup"><span data-stu-id="87673-141">When you read its value, you are reading the value of the variable it aliases.</span></span>
- <span data-ttu-id="87673-142">"*参照渡し*" で値を返す場合、その同じ変数の別名を返すことになります。</span><span class="sxs-lookup"><span data-stu-id="87673-142">If you return it *by reference*, you are returning an alias to that same variable.</span></span>
- <span data-ttu-id="87673-143">"*参照渡し*" で別のメソッドに値を渡す場合、それが別名を与える変数への参照を渡すことになります。</span><span class="sxs-lookup"><span data-stu-id="87673-143">If you pass it to another method *by reference*, you are passing a reference to the variable it aliases.</span></span>
- <span data-ttu-id="87673-144">[ref ローカル](#ref-local)をエイリアスにすると、同じ変数に新しいエイリアスが作られます。</span><span class="sxs-lookup"><span data-stu-id="87673-144">When you make a [ref local](#ref-local) alias, you make a new alias to the same variable.</span></span>


## <a name="ref-locals"></a><span data-ttu-id="87673-145">ref ローカル変数</span><span class="sxs-lookup"><span data-stu-id="87673-145">Ref locals</span></span>

<span data-ttu-id="87673-146">`GetContactInformation` メソッドが ref 戻り値として宣言されているとします。</span><span class="sxs-lookup"><span data-stu-id="87673-146">Assume the `GetContactInformation` method is declared as a ref return:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

<span data-ttu-id="87673-147">値渡し代入によって、変数の値が読み取られ、それが新しい変数に渡されます。</span><span class="sxs-lookup"><span data-stu-id="87673-147">A by-value assignment reads the value of a variable and assigns it to a new variable:</span></span>

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="87673-148">先の代入では、ローカル変数として `p` が宣言されています。</span><span class="sxs-lookup"><span data-stu-id="87673-148">The preceding assignment declares `p` as a local variable.</span></span> <span data-ttu-id="87673-149">その初期値は、`GetContactInformation` によって返された値の読み取りからコピーされます。</span><span class="sxs-lookup"><span data-stu-id="87673-149">Its initial value is copied from reading the value returned by `GetContactInformation`.</span></span> <span data-ttu-id="87673-150">今後、`p` に値が代入されることで、`GetContactInformation` によって返された変数の値が変わることはありません。</span><span class="sxs-lookup"><span data-stu-id="87673-150">Any future assignments to `p` will not change the value of the variable returned by `GetContactInformation`.</span></span> <span data-ttu-id="87673-151">変数 `p` は、返された変数のエイリアスではなくなります。</span><span class="sxs-lookup"><span data-stu-id="87673-151">The variable `p` is no longer an alias to the variable returned.</span></span>

<span data-ttu-id="87673-152">*ref ローカル*変数を宣言し、元の値にエイリアスをコピーします。</span><span class="sxs-lookup"><span data-stu-id="87673-152">You declare a *ref local* variable to copy the alias to the original value.</span></span> <span data-ttu-id="87673-153">次の代入では、`p` は、`GetContactInformation` から返された変数のエイリアスになります。</span><span class="sxs-lookup"><span data-stu-id="87673-153">In the following assignment, `p` is an alias to the variable returned from `GetContactInformation`.</span></span>

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="87673-154">この後 `p` を使用することは、`GetContactInformation` によって返された変数を使用することと同じです。`p` はその変数のエイリアスであるためです。</span><span class="sxs-lookup"><span data-stu-id="87673-154">Subsequent usage of `p` is the same as using the variable returned by `GetContactInformation` because `p` is an alias for that variable.</span></span> <span data-ttu-id="87673-155">`p` を変更すると、`GetContactInformation` から返される変数も変更されます。</span><span class="sxs-lookup"><span data-stu-id="87673-155">Changes to `p` also change the variable returned from `GetContactInformation`.</span></span>

<span data-ttu-id="87673-156">`ref` キーワードは、ローカル変数宣言の前 "*および*" メソッド呼び出しの前の両方で使用します。</span><span class="sxs-lookup"><span data-stu-id="87673-156">The `ref` keyword is used both before the local variable declaration *and* before the method call.</span></span> 

<span data-ttu-id="87673-157">同じ方法で、参照渡しの値にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="87673-157">You can access a value by reference in the same way.</span></span> <span data-ttu-id="87673-158">場合によっては、参照渡しの値へのアクセスによって負荷がかかる可能性があるコピー操作が回避され、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="87673-158">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="87673-159">たとえば、次のステートメントは、値の参照に使用される ref ローカル値をどのように定義できるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="87673-159">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="87673-160">`ref` キーワードは、ローカル変数宣言の前 "*および*" 2 番目の例の値の前で使用します。</span><span class="sxs-lookup"><span data-stu-id="87673-160">The `ref` keyword is used both before the local variable declaration *and* before the value in the second example.</span></span> <span data-ttu-id="87673-161">両方の例の、変数宣言と代入の両方の `ref` キーワードを含めないと、コンパイラ エラー CS8172 "値を使用して参照渡し変数を初期化することはできません" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="87673-161">Failure to include both `ref` keywords in the variable declaration and assignment in both examples results in compiler error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 

<span data-ttu-id="87673-162">C# 7.3 より前は、初期化後に別の記憶域を参照するように ref ローカル変数を割り当て直すことはできませんでした。</span><span class="sxs-lookup"><span data-stu-id="87673-162">Prior to C# 7.3, ref local variables couldn't be reassigned to refer to different storage after being initialized.</span></span> <span data-ttu-id="87673-163">この制限はなくなりました。</span><span class="sxs-lookup"><span data-stu-id="87673-163">That restriction has been removed.</span></span> <span data-ttu-id="87673-164">再割り当ての例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="87673-164">The following example shows a reassignment:</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 <span data-ttu-id="87673-165">ref ローカル変数は、宣言時にやはり初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="87673-165">Ref local variables must still be initialized when they are declared.</span></span>

## <a name="ref-returns-and-ref-locals-an-example"></a><span data-ttu-id="87673-166">ref 戻り値と ref ローカル変数: 使用例</span><span class="sxs-lookup"><span data-stu-id="87673-166">Ref returns and ref locals: an example</span></span>

<span data-ttu-id="87673-167">次の例では、整数値の配列を格納する `NumberStore` クラスを定義しています。</span><span class="sxs-lookup"><span data-stu-id="87673-167">The following example defines a `NumberStore` class that stores an array of integer values.</span></span> <span data-ttu-id="87673-168">`FindNumber` メソッドは、引数として渡された数値に等しいかそれより大きい最初の数値を参照渡しで返します。</span><span class="sxs-lookup"><span data-stu-id="87673-168">The `FindNumber` method returns by reference the first number that is greater than or equal to the number passed as an argument.</span></span> <span data-ttu-id="87673-169">引数に等しいかそれより大きい数値がない場合、メソッドはインデックス 0 の数値を返します。</span><span class="sxs-lookup"><span data-stu-id="87673-169">If no number is greater than or equal to the argument, the method returns the number in index 0.</span></span> 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

<span data-ttu-id="87673-170">次の例では、`NumberStore.FindNumber` メソッドを呼び出して、16 に等しいかそれより大きい最初の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="87673-170">The following example calls the `NumberStore.FindNumber` method to retrieve the first value that is greater than or equal to 16.</span></span> <span data-ttu-id="87673-171">呼び出し元は、メソッドによって返された値を 2 倍にします。</span><span class="sxs-lookup"><span data-stu-id="87673-171">The caller then doubles the value returned by the method.</span></span> <span data-ttu-id="87673-172">次の例の出力では、`NumberStore` インスタンスの配列要素の値に変更が反映されたことが示されています。</span><span class="sxs-lookup"><span data-stu-id="87673-172">The output from the example shows the change reflected in the value of the array elements of the `NumberStore` instance.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

<span data-ttu-id="87673-173">参照戻り値がサポートされていない場合、このような操作は、配列要素のインデックスと値を返すことによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="87673-173">Without support for reference return values, such an operation is performed by returning the index of the array element along with its value.</span></span> <span data-ttu-id="87673-174">呼び出し元はこのインデックスを使用して、別のメソッド呼び出しで値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="87673-174">The caller can then use this index to modify the value in a separate method call.</span></span> <span data-ttu-id="87673-175">一方、インデックスを変更して配列の他の値にアクセスし、変更することも可能です。</span><span class="sxs-lookup"><span data-stu-id="87673-175">However, the caller can also modify the index to access and possibly modify other array values.</span></span>  

<span data-ttu-id="87673-176">次の例では、C# 7.3 以降で ref ローカル変数の再割り当てを使用するように `FindNumber` メソッドを書き直す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="87673-176">The following example shows how the `FindNumber` method could be rewritten after C# 7.3 to use ref local reassignment:</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

<span data-ttu-id="87673-177">この 2 番目のバージョンは、シークされる値が配列の末尾近くにあるようなシナリオのシーケンスが長い場合に、より効率的です。</span><span class="sxs-lookup"><span data-stu-id="87673-177">This second version is more efficient with longer sequences in scenarios where the number sought is closer to the end of the array.</span></span>

## <a name="see-also"></a><span data-ttu-id="87673-178">関連項目</span><span class="sxs-lookup"><span data-stu-id="87673-178">See also</span></span>

[<span data-ttu-id="87673-179">ref キーワード</span><span class="sxs-lookup"><span data-stu-id="87673-179">ref keyword</span></span>](../../language-reference/keywords/ref.md)  
[<span data-ttu-id="87673-180">値の型による参照セマンティクス</span><span class="sxs-lookup"><span data-stu-id="87673-180">Reference Semantics with Value Types</span></span>](../../../csharp/reference-semantics-with-value-types.md)
