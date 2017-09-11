---
title: "void (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- void_CSharpKeyword
- void
dev_langs:
- CSharp
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
caps.latest.revision: 15
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
ms.openlocfilehash: d1bd7ece5ce3b558c616a4eb3a4668c3c13eb1cb
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="void-c-reference"></a><span data-ttu-id="0ac0f-102">void (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="0ac0f-102">void (C# Reference)</span></span>
<span data-ttu-id="0ac0f-103">メソッドの戻り値の型として使用した場合、`void` はメソッドが値を返さないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="0ac0f-103">When used as the return type for a method, `void` specifies that the method doesn't return a value.</span></span>

<span data-ttu-id="0ac0f-104">`void` は、メソッドのパラメーター リストに含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="0ac0f-104">`void` isn't allowed in the parameter list of a method.</span></span> <span data-ttu-id="0ac0f-105">パラメーターを取らず、値を返さないメソッドは、次のように宣言されます。</span><span class="sxs-lookup"><span data-stu-id="0ac0f-105">A method that takes no parameters and returns no value is declared as follows:</span></span>

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

<span data-ttu-id="0ac0f-106">`void` は、不明な型へのポインターを宣言するために、unsafe コンテキストでも使用されます。</span><span class="sxs-lookup"><span data-stu-id="0ac0f-106">`void` is also used in an unsafe context to declare a pointer to an unknown type.</span></span> <span data-ttu-id="0ac0f-107">詳しくは、「[ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0ac0f-107">For more information, see [Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="0ac0f-108">`void` は、.NET Framework の <xref:System.Void?displayProperty=fullName> 型のエイリアスです。</span><span class="sxs-lookup"><span data-stu-id="0ac0f-108">`void` is an alias for the .NET Framework <xref:System.Void?displayProperty=fullName> type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0ac0f-109">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="0ac0f-109">C# Language Specification</span></span>
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="0ac0f-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ac0f-110">See also</span></span>
 <span data-ttu-id="0ac0f-111">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="0ac0f-111">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="0ac0f-112">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="0ac0f-112">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="0ac0f-113">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="0ac0f-113">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="0ac0f-114">[参照型](../../../csharp/language-reference/keywords/reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="0ac0f-114">[Reference Types](../../../csharp/language-reference/keywords/reference-types.md) </span></span>  
 <span data-ttu-id="0ac0f-115">[値型](../../../csharp/language-reference/keywords/value-types.md) </span><span class="sxs-lookup"><span data-stu-id="0ac0f-115">[Value Types](../../../csharp/language-reference/keywords/value-types.md) </span></span>  
 <span data-ttu-id="0ac0f-116">[メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md) </span><span class="sxs-lookup"><span data-stu-id="0ac0f-116">[Methods](../../../csharp/programming-guide/classes-and-structs/methods.md) </span></span>  
 [<span data-ttu-id="0ac0f-117">アンセーフ コードとポインター</span><span class="sxs-lookup"><span data-stu-id="0ac0f-117">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)

