---
title: "public (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords: public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 197ef4a2a8544d439b0c34ec14bb7752b760ea06
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="public-c-reference"></a><span data-ttu-id="f18b6-102">public (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f18b6-102">public (C# Reference)</span></span>
<span data-ttu-id="f18b6-103">`public` キーワードは、型と型のメンバーを示すアクセス修飾子です。</span><span class="sxs-lookup"><span data-stu-id="f18b6-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="f18b6-104">パブリック アクセスは、最も制限の少ないアクセス レベルです。</span><span class="sxs-lookup"><span data-stu-id="f18b6-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="f18b6-105">次の例のように、パブリック メンバーへのアクセスには制限がありません。</span><span class="sxs-lookup"><span data-stu-id="f18b6-105">There are no restrictions on accessing public members, as in this example:</span></span>  
  
```  
class SampleClass  
{  
    public int x; // No access restrictions.  
}  
```  
  
 <span data-ttu-id="f18b6-106">詳しくは、「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」および「[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f18b6-106">See [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f18b6-107">例</span><span class="sxs-lookup"><span data-stu-id="f18b6-107">Example</span></span>  
 <span data-ttu-id="f18b6-108">次の例では、2 つのクラス (`PointTest` と `MainClass`) が宣言されています。</span><span class="sxs-lookup"><span data-stu-id="f18b6-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="f18b6-109">`PointTest` のパブリック メンバー `x` および `y` は、`MainClass` から直接アクセスされます。</span><span class="sxs-lookup"><span data-stu-id="f18b6-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/public_1.cs)]  
  
 <span data-ttu-id="f18b6-110">`public` アクセス レベルを [private](../../../csharp/language-reference/keywords/private.md) または [protected](../../../csharp/language-reference/keywords/protected.md) に変更すると、次のエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f18b6-110">If you change the `public` access level to [private](../../../csharp/language-reference/keywords/private.md) or [protected](../../../csharp/language-reference/keywords/protected.md), you will get the error message:</span></span>  
  
 <span data-ttu-id="f18b6-111">'PointTest.y' はアクセスできない保護レベルになっています。</span><span class="sxs-lookup"><span data-stu-id="f18b6-111">'PointTest.y' is inaccessible due to its protection level.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="f18b6-112">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="f18b6-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f18b6-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f18b6-113">See Also</span></span>  
 [<span data-ttu-id="f18b6-114">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="f18b6-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f18b6-115">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="f18b6-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f18b6-116">アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="f18b6-116">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="f18b6-117">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="f18b6-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="f18b6-118">アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="f18b6-118">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="f18b6-119">アクセシビリティ レベル</span><span class="sxs-lookup"><span data-stu-id="f18b6-119">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="f18b6-120">修飾子</span><span class="sxs-lookup"><span data-stu-id="f18b6-120">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="f18b6-121">private</span><span class="sxs-lookup"><span data-stu-id="f18b6-121">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="f18b6-122">protected</span><span class="sxs-lookup"><span data-stu-id="f18b6-122">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="f18b6-123">internal</span><span class="sxs-lookup"><span data-stu-id="f18b6-123">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
