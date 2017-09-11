---
title: "変換演算子 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c12fd13d6526d79363f973ce2a944c4823bf4104
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="conversion-operators-c-programming-guide"></a><span data-ttu-id="a4018-102">変換演算子 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="a4018-102">Conversion Operators (C# Programming Guide)</span></span>
<span data-ttu-id="a4018-103">C# を使用すると、クラスまたは構造体に関する変換を宣言し、クラスまたは構造体を別のクラスまたは構造体に、または基本型に変換することができます。</span><span class="sxs-lookup"><span data-stu-id="a4018-103">C# enables programmers to declare conversions on classes or structs so that classes or structs can be converted to and/or from other classes or structs, or basic types.</span></span> <span data-ttu-id="a4018-104">変換は演算子と同様の方法で定義され、変換先の型に由来する名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="a4018-104">Conversions are defined like operators and are named for the type to which they convert.</span></span> <span data-ttu-id="a4018-105">変換する引数の型と変換結果の型の両方ではなく一方を、含んでいる型にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4018-105">Either the type of the argument to be converted, or the type of the result of the conversion, but not both, must be the containing type.</span></span>  
  
 <span data-ttu-id="a4018-106">[!code-cs[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/conversion-operators_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="a4018-106">[!code-cs[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/conversion-operators_1.cs)]</span></span>  
  
## <a name="conversion-operators-overview"></a><span data-ttu-id="a4018-107">変換演算子の概要</span><span class="sxs-lookup"><span data-stu-id="a4018-107">Conversion Operators Overview</span></span>  
 <span data-ttu-id="a4018-108">変換演算子には、次の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="a4018-108">Conversion operators have the following properties:</span></span>  
  
-   <span data-ttu-id="a4018-109">`implicit` として宣言される変換は、必要なときに自動的に発生します。</span><span class="sxs-lookup"><span data-stu-id="a4018-109">Conversions declared as `implicit` occur automatically when it is required.</span></span>  
  
-   <span data-ttu-id="a4018-110">`explicit` として宣言される変換には、キャストの呼び出しが必要です。</span><span class="sxs-lookup"><span data-stu-id="a4018-110">Conversions declared as `explicit` require a cast to be called.</span></span>  
  
-   <span data-ttu-id="a4018-111">すべての変換は、`static` として宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4018-111">All conversions must be declared as `static`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a4018-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="a4018-112">Related Sections</span></span>  
 <span data-ttu-id="a4018-113">詳細情報</span><span class="sxs-lookup"><span data-stu-id="a4018-113">For more information:</span></span>  
  
-   [<span data-ttu-id="a4018-114">変換演算子の使用</span><span class="sxs-lookup"><span data-stu-id="a4018-114">Using Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [<span data-ttu-id="a4018-115">キャストと型変換</span><span class="sxs-lookup"><span data-stu-id="a4018-115">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [<span data-ttu-id="a4018-116">方法: 構造体間にユーザー定義の変換を実装する</span><span class="sxs-lookup"><span data-stu-id="a4018-116">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [<span data-ttu-id="a4018-117">explicit</span><span class="sxs-lookup"><span data-stu-id="a4018-117">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [<span data-ttu-id="a4018-118">implicit</span><span class="sxs-lookup"><span data-stu-id="a4018-118">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [<span data-ttu-id="a4018-119">static</span><span class="sxs-lookup"><span data-stu-id="a4018-119">static</span></span>](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a><span data-ttu-id="a4018-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="a4018-120">See Also</span></span>  
 <span data-ttu-id="a4018-121"><xref:System.Convert></span><span class="sxs-lookup"><span data-stu-id="a4018-121"><xref:System.Convert></span></span>   
 <span data-ttu-id="a4018-122">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="a4018-122">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="a4018-123">[Chained user-defined explicit conversions in C#](http://go.microsoft.com/fwlink/?LinkId=112384) (C# でのユーザー定義の明示的変換の連結)</span><span class="sxs-lookup"><span data-stu-id="a4018-123">[Chained user-defined explicit conversions in C#](http://go.microsoft.com/fwlink/?LinkId=112384)</span></span>

