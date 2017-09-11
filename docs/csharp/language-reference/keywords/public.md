---
title: "public (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- public
- public_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
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
ms.openlocfilehash: ae19bf9a33a9860a8960cde5dd4402e10418a094
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="public-c-reference"></a><span data-ttu-id="1b2a3-102">public (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="1b2a3-102">public (C# Reference)</span></span>
<span data-ttu-id="1b2a3-103">`public` キーワードは、型と型のメンバーを示すアクセス修飾子です。</span><span class="sxs-lookup"><span data-stu-id="1b2a3-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="1b2a3-104">パブリック アクセスは、最も制限の少ないアクセス レベルです。</span><span class="sxs-lookup"><span data-stu-id="1b2a3-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="1b2a3-105">次の例のように、パブリック メンバーへのアクセスには制限がありません。</span><span class="sxs-lookup"><span data-stu-id="1b2a3-105">There are no restrictions on accessing public members, as in this example:</span></span>  
  
```  
class SampleClass  
{  
    public int x; // No access restrictions.  
}  
```  
  
 <span data-ttu-id="1b2a3-106">詳しくは、「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」および「[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1b2a3-106">See [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b2a3-107">例</span><span class="sxs-lookup"><span data-stu-id="1b2a3-107">Example</span></span>  
 <span data-ttu-id="1b2a3-108">次の例では、2 つのクラス (`PointTest` と `MainClass`) が宣言されています。</span><span class="sxs-lookup"><span data-stu-id="1b2a3-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="1b2a3-109">`PointTest` のパブリック メンバー `x` および `y` は、`MainClass` から直接アクセスされます。</span><span class="sxs-lookup"><span data-stu-id="1b2a3-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>  
  
 <span data-ttu-id="1b2a3-110">[!code-cs[csrefKeywordsModifiers#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/public_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="1b2a3-110">[!code-cs[csrefKeywordsModifiers#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/public_1.cs)]</span></span>  
  
 <span data-ttu-id="1b2a3-111">`public` アクセス レベルを [private](../../../csharp/language-reference/keywords/private.md) または [protected](../../../csharp/language-reference/keywords/protected.md) に変更すると、次のエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1b2a3-111">If you change the `public` access level to [private](../../../csharp/language-reference/keywords/private.md) or [protected](../../../csharp/language-reference/keywords/protected.md), you will get the error message:</span></span>  
  
 <span data-ttu-id="1b2a3-112">'PointTest.y' はアクセスできない保護レベルになっています。</span><span class="sxs-lookup"><span data-stu-id="1b2a3-112">'PointTest.y' is inaccessible due to its protection level.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="1b2a3-113">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="1b2a3-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1b2a3-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b2a3-114">See Also</span></span>  
 <span data-ttu-id="1b2a3-115">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="1b2a3-115">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="1b2a3-116">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="1b2a3-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="1b2a3-117">[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="1b2a3-117">[Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span></span>  
 <span data-ttu-id="1b2a3-118">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="1b2a3-118">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="1b2a3-119">[アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="1b2a3-119">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="1b2a3-120">[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="1b2a3-120">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="1b2a3-121">[修飾子](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="1b2a3-121">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="1b2a3-122">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="1b2a3-122">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="1b2a3-123">[protected](../../../csharp/language-reference/keywords/protected.md) </span><span class="sxs-lookup"><span data-stu-id="1b2a3-123">[protected](../../../csharp/language-reference/keywords/protected.md) </span></span>  
 [<span data-ttu-id="1b2a3-124">internal</span><span class="sxs-lookup"><span data-stu-id="1b2a3-124">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)

