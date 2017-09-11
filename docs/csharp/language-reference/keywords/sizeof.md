---
title: "sizeof (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
dev_langs:
- CSharp
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 15d11071c369fad398d40cfef301e462c006d5e4
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="sizeof-c-reference"></a><span data-ttu-id="b21f2-102">sizeof (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="b21f2-102">sizeof (C# Reference)</span></span>
<span data-ttu-id="b21f2-103">アンマネージ型のサイズ (バイト単位) を取得するときに使用します。</span><span class="sxs-lookup"><span data-stu-id="b21f2-103">Used to obtain the size in bytes for an unmanaged type.</span></span> <span data-ttu-id="b21f2-104">アンマネージ型には、以下の表に示す組み込み型のほか、次の型も含まれます。</span><span class="sxs-lookup"><span data-stu-id="b21f2-104">Unmanaged types include the built-in types that are listed in the table that follows, and also the following:</span></span>  
  
-   <span data-ttu-id="b21f2-105">列挙型</span><span class="sxs-lookup"><span data-stu-id="b21f2-105">Enum types</span></span>  
  
-   <span data-ttu-id="b21f2-106">ポインター型</span><span class="sxs-lookup"><span data-stu-id="b21f2-106">Pointer types</span></span>  
  
-   <span data-ttu-id="b21f2-107">参照型のフィールドやプロパティが含まれないユーザー定義の構造体</span><span class="sxs-lookup"><span data-stu-id="b21f2-107">User-defined structs that do not contain any fields or properties that are reference types</span></span>  
  
 <span data-ttu-id="b21f2-108">次の例は、`int` のサイズを取得する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b21f2-108">The following example shows how to retrieve the size of an `int`:</span></span>  
  
```csharp  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## <a name="remarks"></a><span data-ttu-id="b21f2-109">コメント</span><span class="sxs-lookup"><span data-stu-id="b21f2-109">Remarks</span></span>  
 <span data-ttu-id="b21f2-110">C# バージョン 2.0 以降、組み込み型に `sizeof` を適用するときに、[unsafe](../../../csharp/language-reference/keywords/unsafe.md) モードを使用する必要がなくなりました。</span><span class="sxs-lookup"><span data-stu-id="b21f2-110">Starting with version 2.0 of C#, applying `sizeof` to built-in types no longer requires that [unsafe](../../../csharp/language-reference/keywords/unsafe.md) mode be used.</span></span>  
  
 <span data-ttu-id="b21f2-111">`sizeof` 演算子はオーバーロードできません。</span><span class="sxs-lookup"><span data-stu-id="b21f2-111">The `sizeof` operator cannot be overloaded.</span></span> <span data-ttu-id="b21f2-112">`sizeof` 演算子により返される値の型は `int` です。</span><span class="sxs-lookup"><span data-stu-id="b21f2-112">The values returned by the `sizeof` operator are of type `int`.</span></span> <span data-ttu-id="b21f2-113">次の表に、特定の組み込み型をオペランドとする `sizeof` 式と、代用される定数値を示します。</span><span class="sxs-lookup"><span data-stu-id="b21f2-113">The following table shows the constant values that are substituted for `sizeof` expressions that have certain built-in types as operands.</span></span>  
  
|<span data-ttu-id="b21f2-114">式</span><span class="sxs-lookup"><span data-stu-id="b21f2-114">Expression</span></span>|<span data-ttu-id="b21f2-115">定数値</span><span class="sxs-lookup"><span data-stu-id="b21f2-115">Constant value</span></span>|  
|----------------|--------------------|  
|`sizeof(sbyte)`|<span data-ttu-id="b21f2-116">1</span><span class="sxs-lookup"><span data-stu-id="b21f2-116">1</span></span>|  
|`sizeof(byte)`|<span data-ttu-id="b21f2-117">1</span><span class="sxs-lookup"><span data-stu-id="b21f2-117">1</span></span>|  
|`sizeof(short)`|<span data-ttu-id="b21f2-118">2</span><span class="sxs-lookup"><span data-stu-id="b21f2-118">2</span></span>|  
|`sizeof(ushort)`|<span data-ttu-id="b21f2-119">2</span><span class="sxs-lookup"><span data-stu-id="b21f2-119">2</span></span>|  
|`sizeof(int)`|<span data-ttu-id="b21f2-120">4</span><span class="sxs-lookup"><span data-stu-id="b21f2-120">4</span></span>|  
|`sizeof(uint)`|<span data-ttu-id="b21f2-121">4</span><span class="sxs-lookup"><span data-stu-id="b21f2-121">4</span></span>|  
|`sizeof(long)`|<span data-ttu-id="b21f2-122">9</span><span class="sxs-lookup"><span data-stu-id="b21f2-122">8</span></span>|  
|`sizeof(ulong)`|<span data-ttu-id="b21f2-123">8</span><span class="sxs-lookup"><span data-stu-id="b21f2-123">8</span></span>|  
|`sizeof(char)`|<span data-ttu-id="b21f2-124">2 (Unicode)</span><span class="sxs-lookup"><span data-stu-id="b21f2-124">2 (Unicode)</span></span>|  
|`sizeof(float)`|<span data-ttu-id="b21f2-125">4</span><span class="sxs-lookup"><span data-stu-id="b21f2-125">4</span></span>|  
|`sizeof(double)`|<span data-ttu-id="b21f2-126">9</span><span class="sxs-lookup"><span data-stu-id="b21f2-126">8</span></span>|  
|`sizeof(decimal)`|<span data-ttu-id="b21f2-127">16</span><span class="sxs-lookup"><span data-stu-id="b21f2-127">16</span></span>|  
|`sizeof(bool)`|<span data-ttu-id="b21f2-128">1</span><span class="sxs-lookup"><span data-stu-id="b21f2-128">1</span></span>|  
  
 <span data-ttu-id="b21f2-129">struct など、その他の型については、`sizeof` 演算子はアンセーフ コード ブロックでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="b21f2-129">For all other types, including structs, the `sizeof` operator can be used only in unsafe code blocks.</span></span> <span data-ttu-id="b21f2-130"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=fullName> メソッドを使用できますが、このメソッドによって返される値は常に `sizeof` によって返される値と同じとは限りません。</span><span class="sxs-lookup"><span data-stu-id="b21f2-130">Although you can use the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=fullName> method, the value returned by this method is not always the same as the value returned by `sizeof`.</span></span> <span data-ttu-id="b21f2-131"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=fullName> は、型のマーシャリング後にサイズを返します。一方、`sizeof` は、共通言語ランタイムによって割り当てられたサイズ (埋め込みを含む) を返します。</span><span class="sxs-lookup"><span data-stu-id="b21f2-131"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=fullName> returns the size after the type has been marshaled, whereas `sizeof` returns the size as it has been allocated by the common language runtime, including any padding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b21f2-132">例</span><span class="sxs-lookup"><span data-stu-id="b21f2-132">Example</span></span>  
 <span data-ttu-id="b21f2-133">[!code-cs[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b21f2-133">[!code-cs[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b21f2-134">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="b21f2-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b21f2-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="b21f2-135">See Also</span></span>  
 <span data-ttu-id="b21f2-136">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="b21f2-136">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="b21f2-137">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b21f2-137">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="b21f2-138">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="b21f2-138">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="b21f2-139">[演算子のキーワード](../../../csharp/language-reference/keywords/operator-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="b21f2-139">[Operator Keywords](../../../csharp/language-reference/keywords/operator-keywords.md) </span></span>  
 <span data-ttu-id="b21f2-140">[enum](../../../csharp/language-reference/keywords/enum.md) </span><span class="sxs-lookup"><span data-stu-id="b21f2-140">[enum](../../../csharp/language-reference/keywords/enum.md) </span></span>  
 <span data-ttu-id="b21f2-141">[アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span><span class="sxs-lookup"><span data-stu-id="b21f2-141">[Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span></span>  
 <span data-ttu-id="b21f2-142">[構造体](../../../csharp/programming-guide/classes-and-structs/structs.md) </span><span class="sxs-lookup"><span data-stu-id="b21f2-142">[Structs](../../../csharp/programming-guide/classes-and-structs/structs.md) </span></span>  
 [<span data-ttu-id="b21f2-143">定数</span><span class="sxs-lookup"><span data-stu-id="b21f2-143">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)

