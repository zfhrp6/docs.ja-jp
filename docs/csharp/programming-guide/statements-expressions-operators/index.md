---
title: "ステートメント、式、および演算子 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- expressions [C#]
- operators [C#]
- C# language, statements
- C# language, operators
- C# language, expressions
- statements [C#]
ms.assetid: 20f8469d-5a6a-4084-ad90-0856b7e97e45
caps.latest.revision: 22
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
ms.openlocfilehash: 71988a5b9aa59b2655b4fd7b91522fe69c8064b6
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="statements-expressions-and-operators-c-programming-guide"></a><span data-ttu-id="a1f51-102">ステートメント、式、および演算子 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="a1f51-102">Statements, Expressions, and Operators (C# Programming Guide)</span></span>
<span data-ttu-id="a1f51-103">アプリケーションを構成する C# コードは、キーワード、式、演算子から成るステートメントで構成されます。</span><span class="sxs-lookup"><span data-stu-id="a1f51-103">The C# code that comprises an application consists of statements made up of keywords, expressions and operators.</span></span> <span data-ttu-id="a1f51-104">このセクションには、C# プログラムのこのような基本要素に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a1f51-104">This section contains information regarding these fundamental elements of a C# program.</span></span>  
  
 <span data-ttu-id="a1f51-105">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="a1f51-105">For more information, see:</span></span>  
  
-   [<span data-ttu-id="a1f51-106">ステートメント</span><span class="sxs-lookup"><span data-stu-id="a1f51-106">Statements</span></span>](../../../csharp/programming-guide/statements-expressions-operators/statements.md)  
  
-   [<span data-ttu-id="a1f51-107">式</span><span class="sxs-lookup"><span data-stu-id="a1f51-107">Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/expressions.md)  
  
    -   [<span data-ttu-id="a1f51-108">式形式のメンバー</span><span class="sxs-lookup"><span data-stu-id="a1f51-108">Expression-bodied members</span></span>](expression-bodied-members.md)
 
-   [<span data-ttu-id="a1f51-109">演算子</span><span class="sxs-lookup"><span data-stu-id="a1f51-109">Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
-   [<span data-ttu-id="a1f51-110">匿名関数</span><span class="sxs-lookup"><span data-stu-id="a1f51-110">Anonymous Functions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [<span data-ttu-id="a1f51-111">オーバーロードされた演算子</span><span class="sxs-lookup"><span data-stu-id="a1f51-111">Overloadable Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)  
  
-   [<span data-ttu-id="a1f51-112">変換演算子</span><span class="sxs-lookup"><span data-stu-id="a1f51-112">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
  
    -   [<span data-ttu-id="a1f51-113">変換演算子の使用</span><span class="sxs-lookup"><span data-stu-id="a1f51-113">Using Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
    -   [<span data-ttu-id="a1f51-114">方法: 構造体間にユーザー定義の変換を実装する</span><span class="sxs-lookup"><span data-stu-id="a1f51-114">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [<span data-ttu-id="a1f51-115">方法: 演算子のオーバーロードを使用して複素数クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="a1f51-115">How to: Use Operator Overloading to Create a Complex Number Class</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-operator-overloading-to-create-a-complex-number-class.md)  
  
-   [<span data-ttu-id="a1f51-116">等価比較</span><span class="sxs-lookup"><span data-stu-id="a1f51-116">Equality Comparisons</span></span>](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="a1f51-117">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="a1f51-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a1f51-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1f51-118">See Also</span></span>  
 <span data-ttu-id="a1f51-119">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="a1f51-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="a1f51-120">キャストと型変換</span><span class="sxs-lookup"><span data-stu-id="a1f51-120">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)

