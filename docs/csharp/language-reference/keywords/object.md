---
title: "object (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- object_CSharpKeyword
- object
dev_langs:
- CSharp
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
caps.latest.revision: 16
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
ms.openlocfilehash: 744debc51f68cc52f03bce09c9f276a66ae085e1
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="object-c-reference"></a><span data-ttu-id="1bc63-102">object (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="1bc63-102">object (C# Reference)</span></span>
<span data-ttu-id="1bc63-103">`object` 型は、.NET Framework の <xref:System.Object> のエイリアスです。</span><span class="sxs-lookup"><span data-stu-id="1bc63-103">The `object` type is an alias for <xref:System.Object> in the .NET Framework.</span></span> <span data-ttu-id="1bc63-104">C# の統一型システムでは、すべての型 (定義済み、ユーザー定義、参照型、および値型) が、直接または間接的に <xref:System.Object> を継承します。</span><span class="sxs-lookup"><span data-stu-id="1bc63-104">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span> <span data-ttu-id="1bc63-105">`object` 型の変数には、任意の型の値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="1bc63-105">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="1bc63-106">値型の変数が object に変換されることを、*ボックス化*されると言います。</span><span class="sxs-lookup"><span data-stu-id="1bc63-106">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="1bc63-107">object 型の変数が値型に変換されることを、*ボックス化解除*されると言います。</span><span class="sxs-lookup"><span data-stu-id="1bc63-107">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="1bc63-108">詳しくは、「[ボックス化とボックス化解除](../../../csharp/programming-guide/types/boxing-and-unboxing.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1bc63-108">For more information, see [Boxing and Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bc63-109">例</span><span class="sxs-lookup"><span data-stu-id="1bc63-109">Example</span></span>  
 <span data-ttu-id="1bc63-110">次の例は、`object` 型の変数で任意のデータ型の値を受け取る方法と、`object` 型の変数で .NET Framework の <xref:System.Object> に対するメソッドを使用する方法を示したものです。</span><span class="sxs-lookup"><span data-stu-id="1bc63-110">The following sample shows how variables of type `object` can accept values of any data type and how variables of type `object` can use methods on <xref:System.Object> from the .NET Framework.</span></span>  
  
 <span data-ttu-id="1bc63-111">[!code-cs[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="1bc63-111">[!code-cs[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="1bc63-112">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="1bc63-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1bc63-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="1bc63-113">See Also</span></span>  
 <span data-ttu-id="1bc63-114">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="1bc63-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="1bc63-115">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="1bc63-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="1bc63-116">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="1bc63-116">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="1bc63-117">[参照型](../../../csharp/language-reference/keywords/reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="1bc63-117">[Reference Types](../../../csharp/language-reference/keywords/reference-types.md) </span></span>  
 [<span data-ttu-id="1bc63-118">値型</span><span class="sxs-lookup"><span data-stu-id="1bc63-118">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)

