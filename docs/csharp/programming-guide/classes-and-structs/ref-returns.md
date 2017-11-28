---
title: "ref 戻り値と ref ローカル変数 (C# ガイド)"
description: "ref 戻り値と ref ローカル変数を定義して使用する方法について説明します。"
author: rpetrusha
ms.author: ronpet
ms.date: 05/30/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 18cf7a4b-29f0-4b14-85b8-80af754aabd8
ms.openlocfilehash: 1d8fb092b578602b5d4f791a3fd14f47dfae1ba6
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="ref-returns-and-ref-locals"></a><span data-ttu-id="ea42e-103">ref 戻り値と ref ローカル変数</span><span class="sxs-lookup"><span data-stu-id="ea42e-103">Ref returns and ref locals</span></span>

<span data-ttu-id="ea42e-104">C# 7 以降の C# は参照戻り値 (ref 戻り値) に対応しています。</span><span class="sxs-lookup"><span data-stu-id="ea42e-104">Starting with C# 7, C# supports reference return values (ref returns).</span></span> <span data-ttu-id="ea42e-105">参照戻り値を使用すると、メソッドから呼び出し元に、値ではなく、オブジェクトへの参照を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="ea42e-105">A reference return value allows a method to return a reference to an object, rather than a value, back to a caller.</span></span> <span data-ttu-id="ea42e-106">呼び出し元は、返されたオブジェクトを値渡しとして処理するか、参照渡しとして処理するかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="ea42e-106">The caller can then choose to treat the returned object returned as if it were returned by value or by reference.</span></span> <span data-ttu-id="ea42e-107">呼び出し元が値ではなく参照として処理する、参照渡しで返された値が ref ローカル変数です。</span><span class="sxs-lookup"><span data-stu-id="ea42e-107">A value returned by reference that the caller handles as a reference rather than a value is a ref local.</span></span>

## <a name="what-is-a-reference-return-value"></a><span data-ttu-id="ea42e-108">参照戻り値とは</span><span class="sxs-lookup"><span data-stu-id="ea42e-108">What is a reference return value?</span></span>

<span data-ttu-id="ea42e-109">呼び出されたメソッドに参照によって引数を渡す*参照渡し*は、ほとんどの開発者によく知られています。</span><span class="sxs-lookup"><span data-stu-id="ea42e-109">Most developers are familiar with passing an argument to a called method *by reference*.</span></span> <span data-ttu-id="ea42e-110">呼び出されたメソッドの引数リストに参照によって渡された値が含まれており、呼び出されたメソッドが値に加えた変更が、呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="ea42e-110">A called method's argument list includes a value passed by reference, and any changes made to its value by the called method are returned to the caller.</span></span> <span data-ttu-id="ea42e-111">*参照戻り値*は、その逆です。</span><span class="sxs-lookup"><span data-stu-id="ea42e-111">A *reference return value* is the opposite:</span></span>

- <span data-ttu-id="ea42e-112">呼び出されたメソッドに渡された引数ではなく、メソッドの戻り値が参照です。</span><span class="sxs-lookup"><span data-stu-id="ea42e-112">The called method's return value, rather than an argument passed to it, is a reference.</span></span>

- <span data-ttu-id="ea42e-113">呼び出されたメソッドではなく呼び出し元が、メソッドによって返された値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="ea42e-113">The caller, rather than the called method, can modify the value returned by the method.</span></span>

- <span data-ttu-id="ea42e-114">引数への変更が呼び出し元のオブジェクトの状態に反映されるのはなく、呼び出し元がメソッドの戻り値に加えた変更が、メソッドが呼び出されたオブジェクトの状態に反映されます。</span><span class="sxs-lookup"><span data-stu-id="ea42e-114">Instead of modifications to the argument that are reflected in state of the object on the caller, modifications to the method's return value by the caller are reflected in the state of the object whose method was called.</span></span>

<span data-ttu-id="ea42e-115">参照戻り値を使用すると、コードがよりコンパクトになり、オブジェクトは、呼び出し元が関心のある配列要素のような個々のデータ項目のみを公開できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ea42e-115">Reference return values can produce more compact code, as well as allow an object to expose only the individual data items, such as an array element, that are of interest to the caller.</span></span> <span data-ttu-id="ea42e-116">これにより、呼び出し元が誤ってオブジェクトの状態を変更する可能性が低くなります。</span><span class="sxs-lookup"><span data-stu-id="ea42e-116">This reduces the likelihood that the caller will inadvertently modify the object's state.</span></span>

<span data-ttu-id="ea42e-117">メソッドが参照戻り値として返すことができる値には、いくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="ea42e-117">There are some restrictions on the value that a method can return as a reference return value.</span></span> <span data-ttu-id="ea42e-118">以下に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ea42e-118">These include:</span></span>

- <span data-ttu-id="ea42e-119">戻り値は `void` にできません。</span><span class="sxs-lookup"><span data-stu-id="ea42e-119">The return value cannot be `void`.</span></span> <span data-ttu-id="ea42e-120">`void` 参照戻り値によるメソッドを定義しようとすると、コンパイラ エラー CS1547 "キーワード void はこのコンテキストで使用できません" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ea42e-120">Attempting to define a method with a `void` reference return value generates compiler error CS1547, "Keyword 'void' cannot be used in this context."</span></span>
 
- <span data-ttu-id="ea42e-121">戻り値は、その戻り値を返すメソッドのローカル変数にすることはできません。戻り値を返すメソッドの外部にスコープが必要です。</span><span class="sxs-lookup"><span data-stu-id="ea42e-121">The return value cannot be a local variable in the method that returns it; it must have a scope that is outside the method that returns it.</span></span> <span data-ttu-id="ea42e-122">クラスのインスタンスまたは静的フィールドを戻り値にすることができます。または、メソッドに渡される引数を戻り値にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ea42e-122">It can be an instance or static field of a class, or it can be an argument passed to the method.</span></span> <span data-ttu-id="ea42e-123">ローカル変数を返そうとすると、コンパイラ エラー CS8168 "ローカル変数 'obj' は ref ローカル変数ではないため、参照渡しで返すことはできません" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ea42e-123">Attempting to return a local variable generates compiler error CS8168, "Cannot return local 'obj' by reference because it is not a ref local."</span></span>

- <span data-ttu-id="ea42e-124">戻り値は `null` にできません。</span><span class="sxs-lookup"><span data-stu-id="ea42e-124">The return value cannot be a `null`.</span></span> <span data-ttu-id="ea42e-125">`null` を返そうとすると、コンパイラ エラー CS8156 "参照渡しで返すことができないため、このコンテキストで使用できない式があります" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ea42e-125">Attempting to return `null` generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

   <span data-ttu-id="ea42e-126">ref 戻り値を持つメソッドで null 値を返す必要がある場合は、参照型の null (インスタンス化されていない) 値を返すか、値型の [null 許容型](../nullable-types/index.md)を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="ea42e-126">If a method with a ref return needs to return a null value, you can either return a null (uninstantiated) value for a reference type or a [nullable type](../nullable-types/index.md) for a value type.</span></span>
 
- <span data-ttu-id="ea42e-127">戻り値は、定数または列挙型のメンバーにすることも、`class` または `struct` のプロパティにすることもできません。</span><span class="sxs-lookup"><span data-stu-id="ea42e-127">The return value cannot be a constant, an enumeration member, or a property of a `class` or `struct`.</span></span> <span data-ttu-id="ea42e-128">それらのいずれかを返そうとすると、コンパイラ エラー CS8156 "参照渡しで返すことができないため、このコンテキストで使用できない式があります" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ea42e-128">Attempting to return these generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

<span data-ttu-id="ea42e-129">さらに、非同期メソッドは、実行が完了する前にまだ戻り値が判明していないときに返される可能性があるため、非同期メソッドでは参照戻り値を使用できません。</span><span class="sxs-lookup"><span data-stu-id="ea42e-129">In addition, because an asynchronous method may return before it has finished execution, while its return value is still unknown, reference return values are not allowed on async methods.</span></span>
 
## <a name="defining-a-ref-return-value"></a><span data-ttu-id="ea42e-130">ref 戻り値の定義</span><span class="sxs-lookup"><span data-stu-id="ea42e-130">Defining a ref return value</span></span>

<span data-ttu-id="ea42e-131">戻り値を定義するには、メソッド シグネチャの戻り値の型に [ref](../../language-reference/keywords/ref.md) キーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="ea42e-131">You define a ref return value by adding the [ref](../../language-reference/keywords/ref.md) keyword to the return type of the method signature.</span></span> <span data-ttu-id="ea42e-132">たとえば、次のシグネチャは、`GetContactInformation` プロパティが `Person` オブジェクトへの参照を呼び出し元に返すことを示しています。</span><span class="sxs-lookup"><span data-stu-id="ea42e-132">For example, the following signature indicates that the `GetContactInformation` property returns a reference to a `Person` object to the caller:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname);
```

<span data-ttu-id="ea42e-133">さらに、メソッド本文の各 [return](../../language-reference/keywords/return.md) ステートメントによって返されるオブジェクトの名前の前に、[ref](../../language-reference/keywords/ref.md) キーワードが必要です。</span><span class="sxs-lookup"><span data-stu-id="ea42e-133">In addition, the name of the object returned by each [return](../../language-reference/keywords/return.md) statement in the method body must be preceded by the [ref](../../language-reference/keywords/ref.md) keyword.</span></span> <span data-ttu-id="ea42e-134">たとえば、次の `return` ステートメントは、`p` という名前の `Person` オブジェクトを参照渡しで返します。</span><span class="sxs-lookup"><span data-stu-id="ea42e-134">For example, the following `return` statement returns a `Person` object named `p` by reference:</span></span>

```csharp
return ref p;
```

## <a name="consuming-a-ref-return-value"></a><span data-ttu-id="ea42e-135">ref 戻り値の使用</span><span class="sxs-lookup"><span data-stu-id="ea42e-135">Consuming a ref return value</span></span>

<span data-ttu-id="ea42e-136">呼び出し元は、2 つの方法のいずれかで ref 戻り値を処理できます。</span><span class="sxs-lookup"><span data-stu-id="ea42e-136">A caller can handle a ref return value in either of two ways:</span></span>

- <span data-ttu-id="ea42e-137">メソッドから値渡しで返される通常の値として処理します。</span><span class="sxs-lookup"><span data-stu-id="ea42e-137">As an ordinary value returned by value from a method.</span></span> <span data-ttu-id="ea42e-138">呼び出し元は、戻り値が参照の戻り値であることを無視する選択ができます。</span><span class="sxs-lookup"><span data-stu-id="ea42e-138">The caller can choose to ignore that the return value is a reference return value.</span></span> <span data-ttu-id="ea42e-139">この場合、メソッドの呼び出しによって返される値に加えられた変更は、呼び出された型の状態に反映されません。</span><span class="sxs-lookup"><span data-stu-id="ea42e-139">In this case, any changes made to the value returned by the method call are not reflected in the state of the called type.</span></span> <span data-ttu-id="ea42e-140">戻り値が値型の場合、メソッドの呼び出しによって返される値に加えられた変更は、呼び出された型の状態に反映されません。</span><span class="sxs-lookup"><span data-stu-id="ea42e-140">If the returned value is a value type, any changes made to the value returned by the method call are not reflected in the state of the called type.</span></span>

- <span data-ttu-id="ea42e-141">参照戻り値として処理します。</span><span class="sxs-lookup"><span data-stu-id="ea42e-141">As a reference return value.</span></span> <span data-ttu-id="ea42e-142">呼び出し元は、参照戻り値が代入される変数を [ref ローカル変数](#ref-local)として定義する必要があります。それにより、メソッドの呼び出しによって返される値への変更が、呼び出された型の状態に反映されます。</span><span class="sxs-lookup"><span data-stu-id="ea42e-142">The caller must define the variable to which the reference return value is assigned as a [ref local](#ref-local), and any changes to the value returned by the method call are reflected in the state of the called type.</span></span> 

## <a name="ref-locals"></a><span data-ttu-id="ea42e-143">ref ローカル変数</span><span class="sxs-lookup"><span data-stu-id="ea42e-143">Ref locals</span></span>

<span data-ttu-id="ea42e-144">参照戻り値を参照として処理するには、呼び出し元は `ref` キーワードを使用して値を *ref ローカル変数*として宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea42e-144">To handle the reference return value as a reference, the caller must declare the value to be a *ref local* by using the `ref` keyword.</span></span> <span data-ttu-id="ea42e-145">たとえば、`Person.GetContactInfomation` メソッドによって返される値を値ではなく参照として使用する場合、メソッドの呼び出しは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ea42e-145">For example, if the value returned by the `Person.GetContactInfomation` method is to be consumed as a reference rather than a value, the method call appears as:</span></span>

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="ea42e-146">なお、`ref` キーワードは、ローカル変数宣言の前*および*メソッド呼び出しの前の両方で使用します。</span><span class="sxs-lookup"><span data-stu-id="ea42e-146">Note that the `ref` keyword is used both before the local variable declaration *and* before the method call.</span></span> <span data-ttu-id="ea42e-147">変数宣言と代入の両方の `ref` キーワードを含めないと、コンパイラ エラー CS8172 "値を使用して参照渡し変数を初期化することはできません" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ea42e-147">Failure to include both `ref` keywords in the variable declaration and assignment results in compiler error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 
 
<span data-ttu-id="ea42e-148">メソッドによって返される `Person` オブジェクトに対する以降の変更は、`contacts` オブジェクトに反映されます。</span><span class="sxs-lookup"><span data-stu-id="ea42e-148">Subsequent changes to the `Person` object returned by the method are reflected in the `contacts` object.</span></span>

<span data-ttu-id="ea42e-149">`p` が `ref` キーワードを使用して ref ローカル変数として定義されていない場合、呼び出し元によって `p` に加えられた変更は、`contacts` オブジェクトに反映されません。</span><span class="sxs-lookup"><span data-stu-id="ea42e-149">If `p` is not defined as a ref local by using the `ref` keyword, any changes made to `p` by the caller are not reflected in the `contacts` object.</span></span>
 
## <a name="ref-returns-and-ref-locals-an-example"></a><span data-ttu-id="ea42e-150">ref 戻り値と ref ローカル変数: 使用例</span><span class="sxs-lookup"><span data-stu-id="ea42e-150">Ref returns and ref locals: an example</span></span>

<span data-ttu-id="ea42e-151">次の例では、整数値の配列を格納する `NumberStore` クラスを定義しています。</span><span class="sxs-lookup"><span data-stu-id="ea42e-151">The following example defines a `NumberStore` class that stores an array of integer values.</span></span> <span data-ttu-id="ea42e-152">`FindNumber` メソッドは、引数として渡された数値に等しいかそれより大きい最初の数値を参照渡しで返します。</span><span class="sxs-lookup"><span data-stu-id="ea42e-152">The `FindNumber` method returns by reference the first number that is greater than or equal to the number passed as an argument.</span></span> <span data-ttu-id="ea42e-153">引数に等しいかそれより大きい数値がない場合、メソッドはインデックス 0 の数値を返します。</span><span class="sxs-lookup"><span data-stu-id="ea42e-153">If no number is greater than or equal to the argument, the method returns the number in index 0.</span></span> 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#1)]

<span data-ttu-id="ea42e-154">次の例では、`NumberStore.FindNumber` メソッドを呼び出して、16 に等しいかそれより大きい最初の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="ea42e-154">The following example calls the `NumberStore.FindNumber` method to retrieve the first value that is greater than or equal to 16.</span></span> <span data-ttu-id="ea42e-155">呼び出し元は、メソッドによって返された値を 2 倍にします。</span><span class="sxs-lookup"><span data-stu-id="ea42e-155">The caller then doubles the value returned by the method.</span></span> <span data-ttu-id="ea42e-156">この変更は、次の例の出力に示されているように、`NumberStore` インスタンスの配列要素の値に反映されます。</span><span class="sxs-lookup"><span data-stu-id="ea42e-156">As the output from the example shows, this change is reflected in the value of the array elements of the `NumberStore` instance.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#2)]

<span data-ttu-id="ea42e-157">参照戻り値がサポートされていない場合、このような操作は通常、配列要素のインデックスと値を返すことによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="ea42e-157">Without support for reference return values, such an operation is usually performed by returning the index of the array element along with its value.</span></span> <span data-ttu-id="ea42e-158">呼び出し元はこのインデックスを使用して、別のメソッド呼び出しで値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="ea42e-158">The caller can then use this index to modify the value in a separate method call.</span></span> <span data-ttu-id="ea42e-159">一方、インデックスを変更して配列の他の値にアクセスし、変更することも可能です。</span><span class="sxs-lookup"><span data-stu-id="ea42e-159">However, the caller can also modify the index to access and possibly modify other array values.</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="ea42e-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea42e-160">See also</span></span>

[<span data-ttu-id="ea42e-161">ref キーワード</span><span class="sxs-lookup"><span data-stu-id="ea42e-161">ref keyword</span></span>](../../language-reference/keywords/ref.md)
