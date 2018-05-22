---
title: C# の構造体 - C# 言語のツアー
description: 構造体と呼ばれる C# の値型の基本を学ぶ
ms.date: 08/10/2016
ms.assetid: 88a74571-f741-4a31-a2b5-1ccf165535b8
ms.openlocfilehash: dac0952e6a55a16ecefec79f9789f9e2d44aada1
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/11/2018
---
# <a name="structs"></a><span data-ttu-id="087f2-103">構造体</span><span class="sxs-lookup"><span data-stu-id="087f2-103">Structs</span></span>

<span data-ttu-id="087f2-104">***構造体***は、クラスと同様に、データ メンバーおよび関数メンバーを含むことができるデータ構造ですが、値型でありヒープ割り当てを必要としない点でクラスと異なります。</span><span class="sxs-lookup"><span data-stu-id="087f2-104">Like classes, ***structs*** are data structures that can contain data members and function members, but unlike classes, structs are value types and do not require heap allocation.</span></span> <span data-ttu-id="087f2-105">構造体型の変数は、構造体のデータを直接格納しますが、クラス型の変数は、動的に割り当てられたオブジェクトへの参照を格納します。</span><span class="sxs-lookup"><span data-stu-id="087f2-105">A variable of a struct type directly stores the data of the struct, whereas a variable of a class type stores a reference to a dynamically allocated object.</span></span> <span data-ttu-id="087f2-106">構造体型はユーザー指定の継承をサポートせず、すべての構造体型は暗黙的に <xref:System.ValueType> 型を継承し、この型はさらに `object` を暗黙的に継承します。</span><span class="sxs-lookup"><span data-stu-id="087f2-106">Struct types do not support user-specified inheritance, and all struct types implicitly inherit from type <xref:System.ValueType>, which in turn implicitly inherits from `object`.</span></span>

<span data-ttu-id="087f2-107">構造体は、値セマンティクスを持つ小規模なデータ構造に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="087f2-107">Structs are particularly useful for small data structures that have value semantics.</span></span> <span data-ttu-id="087f2-108">構造体の主な例としては、複素数、座標系のポイント、ディクショナリのキーと値のペアなどがあります。</span><span class="sxs-lookup"><span data-stu-id="087f2-108">Complex numbers, points in a coordinate system, or key-value pairs in a dictionary are all good examples of structs.</span></span> <span data-ttu-id="087f2-109">小規模なデータ構造には、クラスよりむしろ構造体を使用するほうが、アプリケーションが実行するメモリ割り当ての数を大幅に減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="087f2-109">The use of structs rather than classes for small data structures can make a large difference in the number of memory allocations an application performs.</span></span> <span data-ttu-id="087f2-110">たとえば、次のプログラムでは、100 個のポイントの配列を作成し初期化します。</span><span class="sxs-lookup"><span data-stu-id="087f2-110">For example, the following program creates and initializes an array of 100 points.</span></span> <span data-ttu-id="087f2-111">`Point` をクラスとして実装すると、101 個の別々のオブジェクトがインスタンス化されます。配列に1 個、残りは 100 個の要素に 1 個ずつです。</span><span class="sxs-lookup"><span data-stu-id="087f2-111">With `Point` implemented as a class, 101 separate objects are instantiated—one for the array and one each for the 100 elements.</span></span>

[!code-csharp[PointClassUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L5-L13)]

<span data-ttu-id="087f2-112">これに代わる方法が、ポイントを構造体にすることです。</span><span class="sxs-lookup"><span data-stu-id="087f2-112">An alternative is to make Point a struct.</span></span>

[!code-csharp[PointStruct](../../../samples/snippets/csharp/tour/structs/Point.cs#L3-L11)]

<span data-ttu-id="087f2-113">ここでは 1 つのオブジェクトのみがインスタンス化されます。すなわち、配列に 1 個です。そして、`Point` インスタンスがその配列内にインラインで格納されます。</span><span class="sxs-lookup"><span data-stu-id="087f2-113">Now, only one object is instantiated—the one for the array—and the `Point` instances are stored in-line in the array.</span></span>

<span data-ttu-id="087f2-114">構造体コンストラクターは `new` 演算子を使って呼び出されますが、メモリが割り当てられていることを意味するものではありません。</span><span class="sxs-lookup"><span data-stu-id="087f2-114">Struct constructors are invoked with the `new` operator, but that does not imply that memory is being allocated.</span></span> <span data-ttu-id="087f2-115">オブジェクトを動的に割り当てそこへの参照を返す代わりに、構造体コンストラクターは単に構造体の値自体 (通常、スタック上の一時的な場所) を返し、この値は必要に応じてコピーされます。</span><span class="sxs-lookup"><span data-stu-id="087f2-115">Instead of dynamically allocating an object and returning a reference to it, a struct constructor simply returns the struct value itself (typically in a temporary location on the stack), and this value is then copied as necessary.</span></span>

<span data-ttu-id="087f2-116">クラスを使用すると、2 つの変数が同じオブジェクトを参照できるため、1 つの変数に対する操作によって、もう一方の変数によって参照されるオブジェクトに影響を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="087f2-116">With classes, it is possible for two variables to reference the same object and thus possible for operations on one variable to affect the object referenced by the other variable.</span></span> <span data-ttu-id="087f2-117">構造体を使用すると、各々の変数がデータのコピーを各々で持ち、1 つに対する操作がもう一方に影響を与えることはできません。</span><span class="sxs-lookup"><span data-stu-id="087f2-117">With structs, the variables each have their own copy of the data, and it is not possible for operations on one to affect the other.</span></span> <span data-ttu-id="087f2-118">たとえば、次のコードによって生成される出力は、ポイントがクラスであるか構造体であるかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="087f2-118">For example, the output produced by the following code fragment depends on whether Point is a class or a struct.</span></span>

[!code-csharp[PointUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L19-L22)]

<span data-ttu-id="087f2-119">`Point` がクラスである場合、a と b は同じオブジェクトを参照しているので、出力は 20 です。</span><span class="sxs-lookup"><span data-stu-id="087f2-119">If `Point` is a class, the output is 20 because a and b reference the same object.</span></span> <span data-ttu-id="087f2-120">ポイントが構造体である場合、出力は 10 です。`a` の `b` への割り当ては値のコピーを作成し、このコピーは後続の `a.x` への割り当てには影響されないからです。</span><span class="sxs-lookup"><span data-stu-id="087f2-120">If Point is a struct, the output is 10 because the assignment of `a` to `b` creates a copy of the value, and this copy is unaffected by the subsequent assignment to `a.x`.</span></span>

<span data-ttu-id="087f2-121">前述の例では、構造体の 2 つの制限事項が強調されています。</span><span class="sxs-lookup"><span data-stu-id="087f2-121">The previous example highlights two of the limitations of structs.</span></span> <span data-ttu-id="087f2-122">1 つめは、構造体全体をコピーすることは通常、オブジェクト参照をコピーするよりも非効率であり、割り当てと値パラメーターの引き渡しは参照型よりも構造体のほうが手がかかるということです。</span><span class="sxs-lookup"><span data-stu-id="087f2-122">First, copying an entire struct is typically less efficient than copying an object reference, so assignment and value parameter passing can be more expensive with structs than with reference types.</span></span> <span data-ttu-id="087f2-123">2 つめは、`in`、`ref`、`out` パラメーターを除いて、構造体への参照を作成することはできず、そのために構造体を使用できない状況が数多くあるということです。</span><span class="sxs-lookup"><span data-stu-id="087f2-123">Second, except for `in`, `ref`, and `out` parameters, it is not possible to create references to structs, which rules out their usage in a number of situations.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="087f2-124">[前へ](classes-and-objects.md)
[次へ](arrays.md)</span><span class="sxs-lookup"><span data-stu-id="087f2-124">[Previous](classes-and-objects.md)
[Next](arrays.md)</span></span>
