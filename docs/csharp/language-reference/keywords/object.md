---
title: object (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- object_CSharpKeyword
- object
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
ms.openlocfilehash: 67eaf7f1fd2f01e433395ed21701c3b7fad7c7b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267923"
---
# <a name="object-c-reference"></a><span data-ttu-id="d23fb-102">object (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="d23fb-102">object (C# Reference)</span></span>
<span data-ttu-id="d23fb-103">`object` 型は、.NET Framework の <xref:System.Object> のエイリアスです。</span><span class="sxs-lookup"><span data-stu-id="d23fb-103">The `object` type is an alias for <xref:System.Object> in the .NET Framework.</span></span> <span data-ttu-id="d23fb-104">C# の統一型システムでは、すべての型 (定義済み、ユーザー定義、参照型、および値型) が、直接または間接的に <xref:System.Object> を継承します。</span><span class="sxs-lookup"><span data-stu-id="d23fb-104">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span> <span data-ttu-id="d23fb-105">`object` 型の変数には、任意の型の値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="d23fb-105">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="d23fb-106">値型の変数が object に変換されることを、*ボックス化*されると言います。</span><span class="sxs-lookup"><span data-stu-id="d23fb-106">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="d23fb-107">object 型の変数が値型に変換されることを、*ボックス化解除*されると言います。</span><span class="sxs-lookup"><span data-stu-id="d23fb-107">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="d23fb-108">詳細については、「[ボックス化とボックス化解除](../../../csharp/programming-guide/types/boxing-and-unboxing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d23fb-108">For more information, see [Boxing and Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d23fb-109">例</span><span class="sxs-lookup"><span data-stu-id="d23fb-109">Example</span></span>  
 <span data-ttu-id="d23fb-110">次の例は、`object` 型の変数で任意のデータ型の値を受け取る方法と、`object` 型の変数で .NET Framework の <xref:System.Object> に対するメソッドを使用する方法を示したものです。</span><span class="sxs-lookup"><span data-stu-id="d23fb-110">The following sample shows how variables of type `object` can accept values of any data type and how variables of type `object` can use methods on <xref:System.Object> from the .NET Framework.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="d23fb-111">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="d23fb-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d23fb-112">参照</span><span class="sxs-lookup"><span data-stu-id="d23fb-112">See Also</span></span>  
 [<span data-ttu-id="d23fb-113">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="d23fb-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d23fb-114">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="d23fb-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d23fb-115">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="d23fb-115">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d23fb-116">参照型</span><span class="sxs-lookup"><span data-stu-id="d23fb-116">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="d23fb-117">値型</span><span class="sxs-lookup"><span data-stu-id="d23fb-117">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)
