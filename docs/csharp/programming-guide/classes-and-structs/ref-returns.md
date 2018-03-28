---
title: ref 戻り値と ref ローカル変数 (C# ガイド)
description: ref 戻り値と ref ローカル変数を定義して使用する方法について説明します。
author: rpetrusha
ms.author: ronpet
ms.date: 01/23/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: c37c6dd61ae02813bcc467982f3b175da9136e4a
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2018
---
# <a name="ref-returns-and-ref-locals"></a><span data-ttu-id="0491b-103">ref 戻り値と ref ローカル変数</span><span class="sxs-lookup"><span data-stu-id="0491b-103">Ref returns and ref locals</span></span>

<span data-ttu-id="0491b-104">C# 7 以降の C# は参照戻り値 (ref 戻り値) に対応しています。</span><span class="sxs-lookup"><span data-stu-id="0491b-104">Starting with C# 7, C# supports reference return values (ref returns).</span></span> <span data-ttu-id="0491b-105">参照戻り値を使用すると、メソッドから呼び出し元に、値ではなく、変数への参照を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="0491b-105">A reference return value allows a method to return a reference to a variable, rather than a value, back to a caller.</span></span> <span data-ttu-id="0491b-106">呼び出し元は、返された変数を値渡しとして処理するか、参照渡しとして処理するかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="0491b-106">The caller can then choose to treat the returned variable as if it were returned by value or by reference.</span></span> <span data-ttu-id="0491b-107">呼び出し元は、それ自体が、返された値の参照である新しい変数を作成できます。これは ref ローカルと呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="0491b-107">The caller can create a new variable that is itself a reference to the returned value, called a ref local.</span></span>

## <a name="what-is-a-reference-return-value"></a><span data-ttu-id="0491b-108">参照戻り値とは</span><span class="sxs-lookup"><span data-stu-id="0491b-108">What is a reference return value?</span></span>

<span data-ttu-id="0491b-109">呼び出されたメソッドに参照によって引数を渡す*参照渡し*は、ほとんどの開発者によく知られています。</span><span class="sxs-lookup"><span data-stu-id="0491b-109">Most developers are familiar with passing an argument to a called method *by reference*.</span></span> <span data-ttu-id="0491b-110">呼び出されたメソッドの引数リストに参照によって渡された変数が含まれており、呼び出されたメソッドが値に加えた変更は呼び出し元に認識されます。</span><span class="sxs-lookup"><span data-stu-id="0491b-110">A called method's argument list includes a variable passed by reference, and any changes made to its value by the called method are observed by the caller.</span></span> <span data-ttu-id="0491b-111">*参照戻り値*とは、ある変数の範囲にメソッドが含まれ、その変数の有効期間がメソッドの戻りより長いとき、その変数にメソッドが*参照* (エイリアス) を返すことを意味します。</span><span class="sxs-lookup"><span data-stu-id="0491b-111">A *reference return value* means that a method returns a *reference* (or an alias) to some variable whose scope includes the method and whose lifetime must extend beyond the return of the method.</span></span> <span data-ttu-id="0491b-112">呼び出し元によるメソッドの戻り値の変更は、メソッドによって返される変数に対して行われます。</span><span class="sxs-lookup"><span data-stu-id="0491b-112">Modifications to the method's return value by the caller are made to the variable that is returned by the method.</span></span>

<span data-ttu-id="0491b-113">メソッドが*参照戻り値*を返すという宣言があれば、それはそのメソッドが変数にエイリアスを返すことを示します。</span><span class="sxs-lookup"><span data-stu-id="0491b-113">Declaring that a method returns a *reference return value* indicates that the method returns an alias to a variable.</span></span> <span data-ttu-id="0491b-114">この設計の意図は、多くの場合、呼び出し元のコードが変数の変更などを行うとき、そのコードにはエイリアス経由でその変数にアクセスさせるというものです。</span><span class="sxs-lookup"><span data-stu-id="0491b-114">The design intent is often that the calling code should have access to that variable through the alias, including to modify it.</span></span> <span data-ttu-id="0491b-115">参照で返すメソッドには戻り値の型 `void` を与えることができません。</span><span class="sxs-lookup"><span data-stu-id="0491b-115">It follows that methods returning by reference cannot have the return type `void`.</span></span>

<span data-ttu-id="0491b-116">メソッドが参照戻り値として返すことができる式には、いくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="0491b-116">There are some restrictions on the expression that a method can return as a reference return value.</span></span> <span data-ttu-id="0491b-117">次の設定があります。</span><span class="sxs-lookup"><span data-stu-id="0491b-117">These include:</span></span>

- <span data-ttu-id="0491b-118">戻り値の有効期間は、メソッドの実行より長くならないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0491b-118">The return value must have a lifetime that extends beyond the execution of the method.</span></span> <span data-ttu-id="0491b-119">言い換えると、値を返すメソッドに含まれているローカル変数にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="0491b-119">In other words, it cannot be a local variable in the method that returns it.</span></span> <span data-ttu-id="0491b-120">クラスのインスタンスまたは静的フィールドを戻り値にすることができます。または、メソッドに渡される引数を戻り値にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="0491b-120">It can be an instance or static field of a class, or it can be an argument passed to the method.</span></span> <span data-ttu-id="0491b-121">ローカル変数を返そうとすると、コンパイラ エラー CS8168 "ローカル変数 'obj' は ref ローカル変数ではないため、参照渡しで返すことはできません" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="0491b-121">Attempting to return a local variable generates compiler error CS8168, "Cannot return local 'obj' by reference because it is not a ref local."</span></span>

- <span data-ttu-id="0491b-122">戻り値はリテラル `null` にすることができません。</span><span class="sxs-lookup"><span data-stu-id="0491b-122">The return value cannot be the literal `null`.</span></span> <span data-ttu-id="0491b-123">`null` を返そうとすると、コンパイラ エラー CS8156 "参照渡しで返すことができないため、このコンテキストで使用できない式があります" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="0491b-123">Attempting to return `null` generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

   <span data-ttu-id="0491b-124">ref 戻りを含むメソッドは、現在の値が null (インスタンス化されていない) 値か、値の型が [null 許容型](../nullable-types/index.md)の変数にエイリアスを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="0491b-124">A method with a ref return can return an alias to a variable whose value is currently the null (uninstantiated) value or a [nullable type](../nullable-types/index.md) for a value type.</span></span>
 
- <span data-ttu-id="0491b-125">戻り値は、定数、列挙型のメンバー、プロパティの値渡し戻り値、`class` または `struct` のメソッドにすることができません。</span><span class="sxs-lookup"><span data-stu-id="0491b-125">The return value cannot be a constant, an enumeration member, the by-value return value from a property, or a method of a `class` or `struct`.</span></span> <span data-ttu-id="0491b-126">それらのいずれかを返そうとすると、コンパイラ エラー CS8156 "参照渡しで返すことができないため、このコンテキストで使用できない式があります" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="0491b-126">Attempting to return these generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

<span data-ttu-id="0491b-127">さらに、非同期メソッドは、実行が完了する前にまだ戻り値が判明していないときに返される可能性があるため、非同期メソッドでは参照戻り値を使用できません。</span><span class="sxs-lookup"><span data-stu-id="0491b-127">In addition, because an asynchronous method may return before it has finished execution, while its return value is still unknown, reference return values are not allowed on async methods.</span></span>
 
## <a name="defining-a-ref-return-value"></a><span data-ttu-id="0491b-128">ref 戻り値の定義</span><span class="sxs-lookup"><span data-stu-id="0491b-128">Defining a ref return value</span></span>

<span data-ttu-id="0491b-129">戻り値を定義するには、メソッド シグネチャの戻り値の型に [ref](../../language-reference/keywords/ref.md) キーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="0491b-129">You define a ref return value by adding the [ref](../../language-reference/keywords/ref.md) keyword to the return type of the method signature.</span></span> <span data-ttu-id="0491b-130">たとえば、次のシグネチャは、`GetContactInformation` プロパティが `Person` オブジェクトへの参照を呼び出し元に返すことを示しています。</span><span class="sxs-lookup"><span data-stu-id="0491b-130">For example, the following signature indicates that the `GetContactInformation` property returns a reference to a `Person` object to the caller:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname);
```

<span data-ttu-id="0491b-131">さらに、メソッド本文の各 [return](../../language-reference/keywords/return.md) ステートメントによって返されるオブジェクトの名前の前に、[ref](../../language-reference/keywords/ref.md) キーワードが必要です。</span><span class="sxs-lookup"><span data-stu-id="0491b-131">In addition, the name of the object returned by each [return](../../language-reference/keywords/return.md) statement in the method body must be preceded by the [ref](../../language-reference/keywords/ref.md) keyword.</span></span> <span data-ttu-id="0491b-132">たとえば、次の `return` ステートメントは、`p` という名前の `Person` オブジェクトに参照を返します。</span><span class="sxs-lookup"><span data-stu-id="0491b-132">For example, the following `return` statement returns a reference to a `Person` object named `p`:</span></span>

```csharp
return ref p;
```

## <a name="consuming-a-ref-return-value"></a><span data-ttu-id="0491b-133">ref 戻り値の使用</span><span class="sxs-lookup"><span data-stu-id="0491b-133">Consuming a ref return value</span></span>

<span data-ttu-id="0491b-134">ref 戻り値は、呼び出されるメソッドの範囲で、別の変数のエイリアスになります。</span><span class="sxs-lookup"><span data-stu-id="0491b-134">The ref return value is an alias to another variable in the called method's scope.</span></span> <span data-ttu-id="0491b-135">ref 戻り値の使用は、それが別名を与える変数の使用として解釈できます。</span><span class="sxs-lookup"><span data-stu-id="0491b-135">You can interpret any use of the ref return as using the variable it aliases:</span></span>

- <span data-ttu-id="0491b-136">その値を割り当てるとき、それが別名を与える変数に値を割り当てることになります。</span><span class="sxs-lookup"><span data-stu-id="0491b-136">When you assign its value, you are assigning a value to the variable it aliases.</span></span>
- <span data-ttu-id="0491b-137">その値を読み取るとき、それが別名を与える変数の値を読み取ることになります。</span><span class="sxs-lookup"><span data-stu-id="0491b-137">When you read its value, you are reading the value of the variable it aliases.</span></span>
- <span data-ttu-id="0491b-138">*参照渡し*で値を返す場合、その同じ変数にエイリアスを返すことになります。</span><span class="sxs-lookup"><span data-stu-id="0491b-138">If you return it *by reference* you are returning an alias to that same variable.</span></span>
- <span data-ttu-id="0491b-139">*参照渡し*で別のメソッドに値を渡す場合、それが別名を与える変数に参照を渡すことになります。</span><span class="sxs-lookup"><span data-stu-id="0491b-139">If you pass it to another method *by reference* you are passing a reference to the variable it aliases.</span></span>
- <span data-ttu-id="0491b-140">[ref ローカル](#ref-local)をエイリアスにすると、同じ変数に新しいエイリアスが作られます。</span><span class="sxs-lookup"><span data-stu-id="0491b-140">When you make a [ref local](#ref-local) alias, you make a new alias to the same variable.</span></span>


## <a name="ref-locals"></a><span data-ttu-id="0491b-141">ref ローカル変数</span><span class="sxs-lookup"><span data-stu-id="0491b-141">Ref locals</span></span>

<span data-ttu-id="0491b-142">`GetContactInformation` メソッドが ref 戻り値として宣言されているとします。</span><span class="sxs-lookup"><span data-stu-id="0491b-142">Assume the `GetContactInformation` method is declared as a ref return:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

<span data-ttu-id="0491b-143">値渡し代入によって、変数の値が読み取られ、それが新しい変数に渡されます。</span><span class="sxs-lookup"><span data-stu-id="0491b-143">A by-value assignment reads the value of a variable and assigns it to a new variable:</span></span>

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="0491b-144">先の代入では、ローカル変数として `p` が宣言されています。</span><span class="sxs-lookup"><span data-stu-id="0491b-144">The preceding assignment declares `p` as a local variable.</span></span> <span data-ttu-id="0491b-145">その初期値は、`GetContactInformation` によって返された値の読み取りからコピーされます。</span><span class="sxs-lookup"><span data-stu-id="0491b-145">Its initial value is copied from reading the value returned by `GetContactInformation`.</span></span> <span data-ttu-id="0491b-146">今後、`p` に値が代入されることで、`GetContactInformation` によって返された変数の値が変わることはありません。</span><span class="sxs-lookup"><span data-stu-id="0491b-146">Any future assignments to `p` will not change the value of the variable returned by `GetContactInformation`.</span></span> <span data-ttu-id="0491b-147">変数 `p` は、返された変数のエイリアスではなくなります。</span><span class="sxs-lookup"><span data-stu-id="0491b-147">The variable `p` is no longer an alias to the variable returned.</span></span>

<span data-ttu-id="0491b-148">*ref ローカル*変数を宣言し、元の値にエイリアスをコピーします。</span><span class="sxs-lookup"><span data-stu-id="0491b-148">You declare a *ref local* variable to copy the alias to the original value.</span></span> <span data-ttu-id="0491b-149">次の代入では、`p` は、`GetContactInformation` から返された変数のエイリアスになります。</span><span class="sxs-lookup"><span data-stu-id="0491b-149">In the following assignment, `p` is an alias to the variable returned from `GetContactInformation`.</span></span>

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="0491b-150">この後 `p` を使用することは、`GetContactInformation` によって返された変数を使用することと同じです。`p` はその変数のエイリアスであるためです。</span><span class="sxs-lookup"><span data-stu-id="0491b-150">Subsequent usage of `p` is the same as using the variable returned by `GetContactInformation` because `p` is an alias for that variable.</span></span> <span data-ttu-id="0491b-151">`p` を変更すると、`GetContactInformation` から返される変数も変更されます。</span><span class="sxs-lookup"><span data-stu-id="0491b-151">Changes to `p` also change the variable returned from `GetContactInformation`.</span></span>

<span data-ttu-id="0491b-152">なお、`ref` キーワードは、ローカル変数宣言の前*および*メソッド呼び出しの前の両方で使用します。</span><span class="sxs-lookup"><span data-stu-id="0491b-152">Note that the `ref` keyword is used both before the local variable declaration *and* before the method call.</span></span> 

<span data-ttu-id="0491b-153">同じ方法で、参照渡しの値にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="0491b-153">You can access a value by reference in the same way.</span></span> <span data-ttu-id="0491b-154">場合によっては、参照渡しの値へのアクセスによって負荷がかかる可能性があるコピー操作が回避され、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="0491b-154">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="0491b-155">たとえば、次のステートメントは、値の参照に使用される ref ローカル値をどのように定義できるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="0491b-155">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="0491b-156">なお、`ref` キーワードは、ローカル変数宣言の前*および* 2 番目の例の値の前で使用します。</span><span class="sxs-lookup"><span data-stu-id="0491b-156">Note that the `ref` keyword is used both before the local variable declaration *and* before the value in the second example.</span></span> <span data-ttu-id="0491b-157">両方の例の、変数宣言と代入の両方の `ref` キーワードを含めないと、コンパイラ エラー CS8172 "値を使用して参照渡し変数を初期化することはできません" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="0491b-157">Failure to include both `ref` keywords in the variable declaration and assignment in both examples results in compiler error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 
 
## <a name="ref-returns-and-ref-locals-an-example"></a><span data-ttu-id="0491b-158">ref 戻り値と ref ローカル変数: 使用例</span><span class="sxs-lookup"><span data-stu-id="0491b-158">Ref returns and ref locals: an example</span></span>

<span data-ttu-id="0491b-159">次の例では、整数値の配列を格納する `NumberStore` クラスを定義しています。</span><span class="sxs-lookup"><span data-stu-id="0491b-159">The following example defines a `NumberStore` class that stores an array of integer values.</span></span> <span data-ttu-id="0491b-160">`FindNumber` メソッドは、引数として渡された数値に等しいかそれより大きい最初の数値を参照渡しで返します。</span><span class="sxs-lookup"><span data-stu-id="0491b-160">The `FindNumber` method returns by reference the first number that is greater than or equal to the number passed as an argument.</span></span> <span data-ttu-id="0491b-161">引数に等しいかそれより大きい数値がない場合、メソッドはインデックス 0 の数値を返します。</span><span class="sxs-lookup"><span data-stu-id="0491b-161">If no number is greater than or equal to the argument, the method returns the number in index 0.</span></span> 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#1)]

<span data-ttu-id="0491b-162">次の例では、`NumberStore.FindNumber` メソッドを呼び出して、16 に等しいかそれより大きい最初の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="0491b-162">The following example calls the `NumberStore.FindNumber` method to retrieve the first value that is greater than or equal to 16.</span></span> <span data-ttu-id="0491b-163">呼び出し元は、メソッドによって返された値を 2 倍にします。</span><span class="sxs-lookup"><span data-stu-id="0491b-163">The caller then doubles the value returned by the method.</span></span> <span data-ttu-id="0491b-164">この変更は、次の例の出力に示されているように、`NumberStore` インスタンスの配列要素の値に反映されます。</span><span class="sxs-lookup"><span data-stu-id="0491b-164">As the output from the example shows, this change is reflected in the value of the array elements of the `NumberStore` instance.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#2)]

<span data-ttu-id="0491b-165">参照戻り値がサポートされていない場合、このような操作は通常、配列要素のインデックスと値を返すことによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="0491b-165">Without support for reference return values, such an operation is usually performed by returning the index of the array element along with its value.</span></span> <span data-ttu-id="0491b-166">呼び出し元はこのインデックスを使用して、別のメソッド呼び出しで値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="0491b-166">The caller can then use this index to modify the value in a separate method call.</span></span> <span data-ttu-id="0491b-167">一方、インデックスを変更して配列の他の値にアクセスし、変更することも可能です。</span><span class="sxs-lookup"><span data-stu-id="0491b-167">However, the caller can also modify the index to access and possibly modify other array values.</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="0491b-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="0491b-168">See also</span></span>

[<span data-ttu-id="0491b-169">ref キーワード</span><span class="sxs-lookup"><span data-stu-id="0491b-169">ref keyword</span></span>](../../language-reference/keywords/ref.md)  
[<span data-ttu-id="0491b-170">値の型による参照セマンティクス</span><span class="sxs-lookup"><span data-stu-id="0491b-170">Reference Semantics with Value Types</span></span>](../../../csharp/reference-semantics-with-value-types.md)
