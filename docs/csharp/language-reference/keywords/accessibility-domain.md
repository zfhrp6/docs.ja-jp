---
title: "アクセシビリティ ドメイン (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
caps.latest.revision: 17
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
ms.openlocfilehash: 90faf22d8a7d515ae8bd062f0b95f4be5e051f79
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="accessibility-domain-c-reference"></a><span data-ttu-id="0021d-102">アクセシビリティ ドメイン (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="0021d-102">Accessibility Domain (C# Reference)</span></span>
<span data-ttu-id="0021d-103">メンバーのアクセシビリティ ドメインとは、どのプログラム セクションをメンバーから参照できるかを規定するものです。</span><span class="sxs-lookup"><span data-stu-id="0021d-103">The accessibility domain of a member specifies in which program sections a member can be referenced.</span></span> <span data-ttu-id="0021d-104">そのメンバーが他の型の入れ子になっている場合、そのアクセシビリティ ドメインは、そのメンバーの[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)と、その直接のコンテナーである型のアクセシビリティ ドメインとの両方によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="0021d-104">If the member is nested within another type, its accessibility domain is determined by both the [accessibility level](../../../csharp/language-reference/keywords/accessibility-levels.md) of the member and the accessibility domain of the immediately containing type.</span></span>  
  
 <span data-ttu-id="0021d-105">トップレベルの型のアクセシビリティ ドメインは、それが宣言されているプロジェクトのプログラム テキストと同じかそれ以上になります。</span><span class="sxs-lookup"><span data-stu-id="0021d-105">The accessibility domain of a top-level type is at least the program text of the project that it is declared in.</span></span> <span data-ttu-id="0021d-106">つまり、そのプロジェクトのすべてのソース ファイルがアクセシビリティ ドメインに含まれます。</span><span class="sxs-lookup"><span data-stu-id="0021d-106">That is, the domain includes all of the source files of this project.</span></span> <span data-ttu-id="0021d-107">入れ子にされた型のアクセシビリティ ドメインは、それが宣言されている型のプログラム テキストと同じかそれ以上になります。</span><span class="sxs-lookup"><span data-stu-id="0021d-107">The accessibility domain of a nested type is at least the program text of the type in which it is declared.</span></span> <span data-ttu-id="0021d-108">つまり、アクセシビリティ ドメインは型の本体 (入れ子にされたすべての型のコンテナー) です。</span><span class="sxs-lookup"><span data-stu-id="0021d-108">That is, the domain is the type body, which includes all nested types.</span></span> <span data-ttu-id="0021d-109">入れ子にされた型のアクセシビリティ ドメインが、その型を含んでいる型のアクセシビリティ ドメインを超えることはありません。</span><span class="sxs-lookup"><span data-stu-id="0021d-109">The accessibility domain of a nested type never exceeds that of the containing type.</span></span> <span data-ttu-id="0021d-110">次の例では、以上の概念を説明します。</span><span class="sxs-lookup"><span data-stu-id="0021d-110">These concepts are demonstrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0021d-111">例</span><span class="sxs-lookup"><span data-stu-id="0021d-111">Example</span></span>  
 <span data-ttu-id="0021d-112">この例には、トップレベルの型 `T1` があり、そこに `M1` と `M2` の 2 つのクラスが入れ子にされています。</span><span class="sxs-lookup"><span data-stu-id="0021d-112">This example contains a top-level type, `T1`, and two nested classes, `M1` and `M2`.</span></span> <span data-ttu-id="0021d-113">これらのクラスには、それぞれ異なるアクセシビリティが宣言されたいくつかのフィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="0021d-113">The classes contain fields that have different declared accessibilities.</span></span> <span data-ttu-id="0021d-114">`Main` メソッドの各ステートメントには、それぞれのメンバーのアクセシビリティ ドメインを示したコメントが記述されています。</span><span class="sxs-lookup"><span data-stu-id="0021d-114">In the `Main` method, a comment follows each statement to indicate the accessibility domain of each member.</span></span> <span data-ttu-id="0021d-115">アクセスできないメンバーを参照するステートメントがコメント アウトされていることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="0021d-115">Notice that the statements that try to reference the inaccessible members are commented out.</span></span> <span data-ttu-id="0021d-116">アクセスできないメンバーを参照したことが原因で発生するコンパイラ エラーを確認したい場合は、1 つずつコメントを解除してください。</span><span class="sxs-lookup"><span data-stu-id="0021d-116">If you want to see the compiler errors caused by referencing an inaccessible member, remove the comments one at a time.</span></span>  
  
 <span data-ttu-id="0021d-117">[!code-cs[csrefKeywordsModifiers#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/accessibility-domain_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="0021d-117">[!code-cs[csrefKeywordsModifiers#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/accessibility-domain_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="0021d-118">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="0021d-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0021d-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="0021d-119">See Also</span></span>  
 <span data-ttu-id="0021d-120">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="0021d-120">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="0021d-121">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="0021d-121">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="0021d-122">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="0021d-122">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="0021d-123">[アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="0021d-123">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="0021d-124">[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="0021d-124">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="0021d-125">[アクセシビリティ レベルの使用に関する制限事項](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="0021d-125">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md) </span></span>  
 <span data-ttu-id="0021d-126">[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="0021d-126">[Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span></span>  
 <span data-ttu-id="0021d-127">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="0021d-127">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="0021d-128">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="0021d-128">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="0021d-129">[protected](../../../csharp/language-reference/keywords/protected.md) </span><span class="sxs-lookup"><span data-stu-id="0021d-129">[protected](../../../csharp/language-reference/keywords/protected.md) </span></span>  
 [<span data-ttu-id="0021d-130">internal</span><span class="sxs-lookup"><span data-stu-id="0021d-130">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)

