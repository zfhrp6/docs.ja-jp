---
title: "sizeof (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0148ae8381804ca9286315251582c8ab40778369
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sizeof-c-reference"></a><span data-ttu-id="c7c5d-102">sizeof (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="c7c5d-102">sizeof (C# Reference)</span></span>
<span data-ttu-id="c7c5d-103">アンマネージ型のサイズ (バイト単位) を取得するときに使用します。</span><span class="sxs-lookup"><span data-stu-id="c7c5d-103">Used to obtain the size in bytes for an unmanaged type.</span></span> <span data-ttu-id="c7c5d-104">アンマネージ型には、以下の表に示す組み込み型のほか、次の型も含まれます。</span><span class="sxs-lookup"><span data-stu-id="c7c5d-104">Unmanaged types include the built-in types that are listed in the table that follows, and also the following:</span></span>  
  
-   <span data-ttu-id="c7c5d-105">列挙型</span><span class="sxs-lookup"><span data-stu-id="c7c5d-105">Enum types</span></span>  
  
-   <span data-ttu-id="c7c5d-106">ポインター型</span><span class="sxs-lookup"><span data-stu-id="c7c5d-106">Pointer types</span></span>  
  
-   <span data-ttu-id="c7c5d-107">参照型のフィールドやプロパティが含まれないユーザー定義の構造体</span><span class="sxs-lookup"><span data-stu-id="c7c5d-107">User-defined structs that do not contain any fields or properties that are reference types</span></span>  
  
 <span data-ttu-id="c7c5d-108">次の例は、`int` のサイズを取得する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c7c5d-108">The following example shows how to retrieve the size of an `int`:</span></span>  
  
```csharp  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## <a name="remarks"></a><span data-ttu-id="c7c5d-109">コメント</span><span class="sxs-lookup"><span data-stu-id="c7c5d-109">Remarks</span></span>  
 <span data-ttu-id="c7c5d-110">C# バージョン 2.0 以降、組み込み型に `sizeof` を適用するときに、[unsafe](../../../csharp/language-reference/keywords/unsafe.md) モードを使用する必要がなくなりました。</span><span class="sxs-lookup"><span data-stu-id="c7c5d-110">Starting with version 2.0 of C#, applying `sizeof` to built-in types no longer requires that [unsafe](../../../csharp/language-reference/keywords/unsafe.md) mode be used.</span></span>  
  
 <span data-ttu-id="c7c5d-111">`sizeof` 演算子はオーバーロードできません。</span><span class="sxs-lookup"><span data-stu-id="c7c5d-111">The `sizeof` operator cannot be overloaded.</span></span> <span data-ttu-id="c7c5d-112">`sizeof` 演算子により返される値の型は `int` です。</span><span class="sxs-lookup"><span data-stu-id="c7c5d-112">The values returned by the `sizeof` operator are of type `int`.</span></span> <span data-ttu-id="c7c5d-113">次の表に、特定の組み込み型をオペランドとする `sizeof` 式と、代用される定数値を示します。</span><span class="sxs-lookup"><span data-stu-id="c7c5d-113">The following table shows the constant values that are substituted for `sizeof` expressions that have certain built-in types as operands.</span></span>  
  
|<span data-ttu-id="c7c5d-114">式</span><span class="sxs-lookup"><span data-stu-id="c7c5d-114">Expression</span></span>|<span data-ttu-id="c7c5d-115">定数値</span><span class="sxs-lookup"><span data-stu-id="c7c5d-115">Constant value</span></span>|  
|----------------|--------------------|  
|`sizeof(sbyte)`|<span data-ttu-id="c7c5d-116">1</span><span class="sxs-lookup"><span data-stu-id="c7c5d-116">1</span></span>|  
|`sizeof(byte)`|<span data-ttu-id="c7c5d-117">1</span><span class="sxs-lookup"><span data-stu-id="c7c5d-117">1</span></span>|  
|`sizeof(short)`|<span data-ttu-id="c7c5d-118">2</span><span class="sxs-lookup"><span data-stu-id="c7c5d-118">2</span></span>|  
|`sizeof(ushort)`|<span data-ttu-id="c7c5d-119">2</span><span class="sxs-lookup"><span data-stu-id="c7c5d-119">2</span></span>|  
|`sizeof(int)`|<span data-ttu-id="c7c5d-120">4</span><span class="sxs-lookup"><span data-stu-id="c7c5d-120">4</span></span>|  
|`sizeof(uint)`|<span data-ttu-id="c7c5d-121">4</span><span class="sxs-lookup"><span data-stu-id="c7c5d-121">4</span></span>|  
|`sizeof(long)`|<span data-ttu-id="c7c5d-122">8</span><span class="sxs-lookup"><span data-stu-id="c7c5d-122">8</span></span>|  
|`sizeof(ulong)`|<span data-ttu-id="c7c5d-123">8</span><span class="sxs-lookup"><span data-stu-id="c7c5d-123">8</span></span>|  
|`sizeof(char)`|<span data-ttu-id="c7c5d-124">2 (Unicode)</span><span class="sxs-lookup"><span data-stu-id="c7c5d-124">2 (Unicode)</span></span>|  
|`sizeof(float)`|<span data-ttu-id="c7c5d-125">4</span><span class="sxs-lookup"><span data-stu-id="c7c5d-125">4</span></span>|  
|`sizeof(double)`|<span data-ttu-id="c7c5d-126">8</span><span class="sxs-lookup"><span data-stu-id="c7c5d-126">8</span></span>|  
|`sizeof(decimal)`|<span data-ttu-id="c7c5d-127">16</span><span class="sxs-lookup"><span data-stu-id="c7c5d-127">16</span></span>|  
|`sizeof(bool)`|<span data-ttu-id="c7c5d-128">1</span><span class="sxs-lookup"><span data-stu-id="c7c5d-128">1</span></span>|  
  
 <span data-ttu-id="c7c5d-129">struct など、その他の型については、`sizeof` 演算子はアンセーフ コード ブロックでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="c7c5d-129">For all other types, including structs, the `sizeof` operator can be used only in unsafe code blocks.</span></span> <span data-ttu-id="c7c5d-130"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> メソッドを使用できますが、このメソッドによって返される値は常に `sizeof` によって返される値と同じとは限りません。</span><span class="sxs-lookup"><span data-stu-id="c7c5d-130">Although you can use the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, the value returned by this method is not always the same as the value returned by `sizeof`.</span></span> <span data-ttu-id="c7c5d-131"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> は、型のマーシャリング後にサイズを返します。一方、`sizeof` は、共通言語ランタイムによって割り当てられたサイズ (埋め込みを含む) を返します。</span><span class="sxs-lookup"><span data-stu-id="c7c5d-131"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> returns the size after the type has been marshaled, whereas `sizeof` returns the size as it has been allocated by the common language runtime, including any padding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7c5d-132">例</span><span class="sxs-lookup"><span data-stu-id="c7c5d-132">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="c7c5d-133">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="c7c5d-133">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c7c5d-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7c5d-134">See Also</span></span>  
 [<span data-ttu-id="c7c5d-135">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="c7c5d-135">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c7c5d-136">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="c7c5d-136">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c7c5d-137">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="c7c5d-137">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="c7c5d-138">演算子のキーワード</span><span class="sxs-lookup"><span data-stu-id="c7c5d-138">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="c7c5d-139">enum</span><span class="sxs-lookup"><span data-stu-id="c7c5d-139">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
 [<span data-ttu-id="c7c5d-140">アンセーフ コードとポインター</span><span class="sxs-lookup"><span data-stu-id="c7c5d-140">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="c7c5d-141">構造体</span><span class="sxs-lookup"><span data-stu-id="c7c5d-141">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [<span data-ttu-id="c7c5d-142">定数</span><span class="sxs-lookup"><span data-stu-id="c7c5d-142">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)
