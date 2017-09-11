---
title: "」を参照してください。 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ._CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
caps.latest.revision: 21
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
ms.openlocfilehash: fdc7c1821548509f3a3750aef2836c034f7aa53b
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="47680-103">」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47680-103">.</span></span> <span data-ttu-id="47680-104">演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="47680-104">Operator (C# Reference)</span></span>
<span data-ttu-id="47680-105">ドット演算子 (`.`) は、メンバー アクセスに使用されます。</span><span class="sxs-lookup"><span data-stu-id="47680-105">The dot operator (`.`) is used for member access.</span></span> <span data-ttu-id="47680-106">ドット演算子は、型または名前空間のメンバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="47680-106">The dot operator specifies a member of a type or namespace.</span></span> <span data-ttu-id="47680-107">たとえば、ドット演算子は、.NET Framework クラス ライブラリ内の特定のメソッドにアクセスするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="47680-107">For example, the dot operator is used to access specific methods within the .NET Framework class libraries:</span></span>  
  
 <span data-ttu-id="47680-108">[!code-cs[csRefOperators#16](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="47680-108">[!code-cs[csRefOperators#16](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_1.cs)]</span></span>  
  
 <span data-ttu-id="47680-109">たとえば、次のクラスを考えます。</span><span class="sxs-lookup"><span data-stu-id="47680-109">For example, consider the following class:</span></span>  
  
 <span data-ttu-id="47680-110">[!code-cs[csRefOperators#17](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="47680-110">[!code-cs[csRefOperators#17](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_2.cs)]</span></span>  
  
 <span data-ttu-id="47680-111">[!code-cs[csRefOperators#18](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="47680-111">[!code-cs[csRefOperators#18](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_3.cs)]</span></span>  
  
 <span data-ttu-id="47680-112">`s` 変数には 2 つのメンバー (`a` と `b`) があり、それらのメンバーにアクセスするために、ドット演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="47680-112">The variable `s` has two members, `a` and `b`; to access them, use the dot operator:</span></span>  
  
 <span data-ttu-id="47680-113">[!code-cs[csRefOperators#19](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="47680-113">[!code-cs[csRefOperators#19](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_4.cs)]</span></span>  
  
 <span data-ttu-id="47680-114">ドットは、修飾名を形成するためにも使用されます。この修飾名は、たとえば、属している名前空間やインターフェイスを指定する名前です。</span><span class="sxs-lookup"><span data-stu-id="47680-114">The dot is also used to form qualified names, which are names that specify the namespace or interface, for example, to which they belong.</span></span>  
  
 <span data-ttu-id="47680-115">[!code-cs[csRefOperators#20](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="47680-115">[!code-cs[csRefOperators#20](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_5.cs)]</span></span>  
  
 <span data-ttu-id="47680-116">ディレクティブを使用すると、オプションで名前を限定することができます。</span><span class="sxs-lookup"><span data-stu-id="47680-116">The using directive makes some name qualification optional:</span></span>  
  
 <span data-ttu-id="47680-117">[!code-cs[csRefOperators#21](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="47680-117">[!code-cs[csRefOperators#21](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_6.cs)]</span></span>  
  
 <span data-ttu-id="47680-118">ただし、識別子があいまいな場合は、修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47680-118">But when an identifier is ambiguous, it must be qualified:</span></span>  
  
 <span data-ttu-id="47680-119">[!code-cs[csRefOperators#22](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="47680-119">[!code-cs[csRefOperators#22](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_7.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="47680-120">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="47680-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="47680-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="47680-121">See Also</span></span>  
 <span data-ttu-id="47680-122">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="47680-122">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="47680-123">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="47680-123">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="47680-124">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="47680-124">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

