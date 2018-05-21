---
title: である必要があります。 演算子 (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: 088f1991cafa92a69e11ca14bd2d983b36c0e3ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="083f2-103">である必要があります。</span><span class="sxs-lookup"><span data-stu-id="083f2-103">.</span></span> <span data-ttu-id="083f2-104">演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="083f2-104">Operator (C# Reference)</span></span>
<span data-ttu-id="083f2-105">ドット演算子 (`.`) は、メンバー アクセスに使用されます。</span><span class="sxs-lookup"><span data-stu-id="083f2-105">The dot operator (`.`) is used for member access.</span></span> <span data-ttu-id="083f2-106">ドット演算子は、型または名前空間のメンバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="083f2-106">The dot operator specifies a member of a type or namespace.</span></span> <span data-ttu-id="083f2-107">たとえば、ドット演算子は、.NET Framework クラス ライブラリ内の特定のメソッドにアクセスするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="083f2-107">For example, the dot operator is used to access specific methods within the .NET Framework class libraries:</span></span>  
  
 [!code-csharp[csRefOperators#16](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_1.cs)]  
  
 <span data-ttu-id="083f2-108">たとえば、次のクラスを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="083f2-108">For example, consider the following class:</span></span>  
  
 [!code-csharp[csRefOperators#17](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_2.cs)]  
  
 [!code-csharp[csRefOperators#18](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_3.cs)]  
  
 <span data-ttu-id="083f2-109">`s` 変数には 2 つのメンバー (`a` と `b`) があり、それらにアクセスするために、ドット演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="083f2-109">The variable `s` has two members, `a` and `b`; to access them, use the dot operator:</span></span>  
  
 [!code-csharp[csRefOperators#19](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_4.cs)]  
  
 <span data-ttu-id="083f2-110">ドットは、修飾名を形成するためにも使用されます。この修飾名は、たとえば、属している名前空間やインターフェイスを指定する名前です。</span><span class="sxs-lookup"><span data-stu-id="083f2-110">The dot is also used to form qualified names, which are names that specify the namespace or interface, for example, to which they belong.</span></span>  
  
 [!code-csharp[csRefOperators#20](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_5.cs)]  
  
 <span data-ttu-id="083f2-111">using ディレクティブを使用すると、名前の修飾をオプションにすることができます。</span><span class="sxs-lookup"><span data-stu-id="083f2-111">The using directive makes some name qualification optional:</span></span>  
  
 [!code-csharp[csRefOperators#21](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_6.cs)]  
  
 <span data-ttu-id="083f2-112">ただし、識別子があいまいな場合は、修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="083f2-112">But when an identifier is ambiguous, it must be qualified:</span></span>  
  
 [!code-csharp[csRefOperators#22](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_7.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="083f2-113">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="083f2-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="083f2-114">参照</span><span class="sxs-lookup"><span data-stu-id="083f2-114">See Also</span></span>  
 [<span data-ttu-id="083f2-115">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="083f2-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="083f2-116">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="083f2-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="083f2-117">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="083f2-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
