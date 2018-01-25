---
title: "定数 (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 86c9371a6a82c4034b7bdf279e7b205cfcc84bea
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="constants-c-programming-guide"></a><span data-ttu-id="4b04e-102">定数 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="4b04e-102">Constants (C# Programming Guide)</span></span>
<span data-ttu-id="4b04e-103">定数とは、コンパイル時に既知であり、プログラムの実行期間を通じて変更されない値です。</span><span class="sxs-lookup"><span data-stu-id="4b04e-103">Constants are immutable values which are known at compile time and do not change for the life of the program.</span></span> <span data-ttu-id="4b04e-104">定数を宣言するには、[const](../../../csharp/language-reference/keywords/const.md) 修飾子を使用します。</span><span class="sxs-lookup"><span data-stu-id="4b04e-104">Constants are declared with the [const](../../../csharp/language-reference/keywords/const.md) modifier.</span></span> <span data-ttu-id="4b04e-105">`const` として宣言できるのは、C# 組み込み型 (<xref:System.Object?displayProperty=nameWithType> を除く) のみです。</span><span class="sxs-lookup"><span data-stu-id="4b04e-105">Only the C# built-in types (excluding <xref:System.Object?displayProperty=nameWithType>) may be declared as `const`.</span></span> <span data-ttu-id="4b04e-106">組み込み型の一覧については、「[組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b04e-106">For a list of the built-in types, see [Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md).</span></span> <span data-ttu-id="4b04e-107">クラス、構造体、配列などのユーザー定義型を `const` にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="4b04e-107">User-defined types, including classes, structs, and arrays, cannot be `const`.</span></span> <span data-ttu-id="4b04e-108">実行時に (コンストラクターなどで) 一度だけ初期化され、その後は変更できないクラス、構造体、または配列を作成するには、[readonly](../../../csharp/language-reference/keywords/readonly.md) 修飾子を使用します。</span><span class="sxs-lookup"><span data-stu-id="4b04e-108">Use the [readonly](../../../csharp/language-reference/keywords/readonly.md) modifier to create a class, struct, or array that is initialized one time at runtime (for example in a constructor) and thereafter cannot be changed.</span></span>  
  
 <span data-ttu-id="4b04e-109">C# では、`const` のメソッド、プロパティ、またはイベントはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="4b04e-109">C# does not support `const` methods, properties, or events.</span></span>  
  
 <span data-ttu-id="4b04e-110">enum 型を使用すると、組み込みの整数型 (`int`、`uint`、`long` など) の名前付き定数を定義できます。</span><span class="sxs-lookup"><span data-stu-id="4b04e-110">The enum type enables you to define named constants for integral built-in types (for example `int`, `uint`, `long`, and so on).</span></span> <span data-ttu-id="4b04e-111">詳細については、「[enum](../../../csharp/language-reference/keywords/enum.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b04e-111">For more information, see [enum](../../../csharp/language-reference/keywords/enum.md).</span></span>  
  
 <span data-ttu-id="4b04e-112">定数は、宣言するときに初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b04e-112">Constants must be initialized as they are declared.</span></span> <span data-ttu-id="4b04e-113">例:</span><span class="sxs-lookup"><span data-stu-id="4b04e-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#64](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_1.cs)]  
  
 <span data-ttu-id="4b04e-114">この例では、定数 `months` は常に 12 になり、クラス自体によっても変更できません。</span><span class="sxs-lookup"><span data-stu-id="4b04e-114">In this example, the constant `months` is always 12, and it cannot be changed even by the class itself.</span></span> <span data-ttu-id="4b04e-115">実際、コンパイラが C# ソース コードで定数の識別子 (この場合は `months`) を検出すると、コンパイラが生成する中間言語 (IL) コードには、識別子の代わりにリテラル値が直接出力されます。</span><span class="sxs-lookup"><span data-stu-id="4b04e-115">In fact, when the compiler encounters a constant identifier in C# source code (for example, `months`), it substitutes the literal value directly into the intermediate language (IL) code that it produces.</span></span> <span data-ttu-id="4b04e-116">実行時に定数に関連付けられる変数アドレスが存在しないため、`const` フィールドは、参照渡しすることも、式の左辺値として指定することもできません。</span><span class="sxs-lookup"><span data-stu-id="4b04e-116">Because there is no variable address associated with a constant at run time, `const` fields cannot be passed by reference and cannot appear as an l-value in an expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b04e-117">DLL などの他のコードに定義されている定数値を参照するときは、注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="4b04e-117">Use caution when you refer to constant values defined in other code such as DLLs.</span></span> <span data-ttu-id="4b04e-118">新しいバージョンの DLL で定数の新しい値を定義しても、その新バージョンを対象にプログラムを再コンパイルするまで、プログラムには古いリテラル値が保持されたままになります。</span><span class="sxs-lookup"><span data-stu-id="4b04e-118">If a new version of the DLL defines a new value for the constant, your program will still hold the old literal value until it is recompiled against the new version.</span></span>  
  
 <span data-ttu-id="4b04e-119">同じ型の複数の定数を、次のように同時に宣言できます。</span><span class="sxs-lookup"><span data-stu-id="4b04e-119">Multiple constants of the same type can be declared at the same time, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#65](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_2.cs)]  
  
 <span data-ttu-id="4b04e-120">定数の初期化に使用する式は、循環参照を形成しない限り別の定数を参照できます。</span><span class="sxs-lookup"><span data-stu-id="4b04e-120">The expression that is used to initialize a constant can refer to another constant if it does not create a circular reference.</span></span> <span data-ttu-id="4b04e-121">例:</span><span class="sxs-lookup"><span data-stu-id="4b04e-121">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#66](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_3.cs)]  
  
 <span data-ttu-id="4b04e-122">定数は、[public](../../../csharp/language-reference/keywords/public.md)、[private](../../../csharp/language-reference/keywords/private.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、[protected internal](../../../csharp/language-reference/keywords/protected-internal.md) または [private protected](../../../csharp/language-reference/keywords/private-protected.md) としてマークできます。</span><span class="sxs-lookup"><span data-stu-id="4b04e-122">Constants can be marked as [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [protected internal](../../../csharp/language-reference/keywords/protected-internal.md) or [private protected](../../../csharp/language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="4b04e-123">これらのアクセス修飾子により、クラスのユーザーが定数にアクセスする方法が定義されます。</span><span class="sxs-lookup"><span data-stu-id="4b04e-123">These access modifiers define how users of the class can access the constant.</span></span> <span data-ttu-id="4b04e-124">詳細については、「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b04e-124">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="4b04e-125">定数の値は型のすべてのインスタンスで同じであるため、定数は[静的](../../../csharp/language-reference/keywords/static.md)フィールドのようにアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="4b04e-125">Constants are accessed as if they were [static](../../../csharp/language-reference/keywords/static.md) fields because the value of the constant is the same for all instances of the type.</span></span> <span data-ttu-id="4b04e-126">定数の宣言に `static` キーワードは使用しません。</span><span class="sxs-lookup"><span data-stu-id="4b04e-126">You do not use the `static` keyword to declare them.</span></span> <span data-ttu-id="4b04e-127">定数を定義しているクラスに含まれていない式で定数を使用する場合は、クラス名、ピリオド、定数の名前を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b04e-127">Expressions that are not in the class that defines the constant must use the class name, a period, and the name of the constant to access the constant.</span></span> <span data-ttu-id="4b04e-128">例:</span><span class="sxs-lookup"><span data-stu-id="4b04e-128">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#67](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="4b04e-129">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="4b04e-129">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4b04e-130">参照</span><span class="sxs-lookup"><span data-stu-id="4b04e-130">See Also</span></span>  
 [<span data-ttu-id="4b04e-131">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="4b04e-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4b04e-132">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="4b04e-132">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="4b04e-133">プロパティ</span><span class="sxs-lookup"><span data-stu-id="4b04e-133">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="4b04e-134">型</span><span class="sxs-lookup"><span data-stu-id="4b04e-134">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="4b04e-135">readonly</span><span class="sxs-lookup"><span data-stu-id="4b04e-135">readonly</span></span>](../../../csharp/language-reference/keywords/readonly.md)  
 [<span data-ttu-id="4b04e-136">C# の不変性パート 1: 不変性の種類</span><span class="sxs-lookup"><span data-stu-id="4b04e-136">Immutability in C# Part One: Kinds of Immutability</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/11/13/immutability-in-c-part-one-kinds-of-immutability)
