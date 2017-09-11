---
title: "internal (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- internal_CSharpKeyword
- internal
dev_langs:
- CSharp
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
caps.latest.revision: 23
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
ms.openlocfilehash: 5674a78e2c317357c31d9e2661a25ce86cbf4f6a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="internal-c-reference"></a><span data-ttu-id="db02e-102">internal (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="db02e-102">internal (C# Reference)</span></span>
<span data-ttu-id="db02e-103">`internal` キーワードは、型と型のメンバーを示す[アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md)です。</span><span class="sxs-lookup"><span data-stu-id="db02e-103">The `internal` keyword is an [access modifier](../../../csharp/language-reference/keywords/access-modifiers.md) for types and type members.</span></span> <span data-ttu-id="db02e-104">internal 型またはメンバーは、次の例のように、同じアセンブリ内のファイルでのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="db02e-104">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  
  
 <span data-ttu-id="db02e-105">`protected internal` アクセス修飾子を持つ型またはメンバーには、現在のアセンブリから、または外側のクラスから派生した型からアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="db02e-105">Types or members that have access modifier `protected internal` can be accessed from the current assembly or from types that are derived from the containing class.</span></span>  
  
 <span data-ttu-id="db02e-106">`internal` とその他のアクセス修飾子の比較については、「[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)」と「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db02e-106">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) and [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="db02e-107">アセンブリの詳細については、「[アセンブリとグローバル アセンブリ キャッシュ](../../../csharp/programming-guide/concepts/assemblies-gac/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db02e-107">For more information about assemblies, see [Assemblies and the Global Assembly Cache](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).</span></span>  
  
 <span data-ttu-id="db02e-108">一般的に、内部アクセスはコンポーネント ベースの開発で使用されます。これは、コンポーネントのグループを、アプリケーション コードの他の部分に公開することなくプライベートに連携させることができるためです。</span><span class="sxs-lookup"><span data-stu-id="db02e-108">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="db02e-109">たとえば、グラフィカル ユーザー インターフェイスを構築するためのフレームワークでは、内部アクセスによってメンバーを使用することで連携する `Control` クラスと `Form` クラスを提供できます。</span><span class="sxs-lookup"><span data-stu-id="db02e-109">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="db02e-110">これらは内部のメンバーなので、フレームワークを使用しているコードには公開されません。</span><span class="sxs-lookup"><span data-stu-id="db02e-110">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="db02e-111">型またはメンバーが定義されているアセンブリの外側で、型またはメンバーを内部アクセスで参照するとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="db02e-111">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db02e-112">例</span><span class="sxs-lookup"><span data-stu-id="db02e-112">Example</span></span>  
 <span data-ttu-id="db02e-113">この例には、2 つのファイル (`Assembly1.cs` と `Assembly1_a.cs`) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="db02e-113">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="db02e-114">最初のファイルには、内部の基底クラス `BaseClass` が含まれています。</span><span class="sxs-lookup"><span data-stu-id="db02e-114">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="db02e-115">2 番目のファイルでは、`BaseClass` のインスタンス化を試行するとエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="db02e-115">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
```  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass   
{  
   public static int intM = 0;  
}  
```  
  
```  
// Assembly1_a.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="db02e-116">例</span><span class="sxs-lookup"><span data-stu-id="db02e-116">Example</span></span>  
 <span data-ttu-id="db02e-117">この例では、例 1 で使用したのと同じファイルを使用し、`BaseClass` のアクセシビリティ レベルを `public` に変更します。</span><span class="sxs-lookup"><span data-stu-id="db02e-117">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="db02e-118">また、メンバー `IntM` のアクセシビリティ レベルを `internal` に変更します。</span><span class="sxs-lookup"><span data-stu-id="db02e-118">Also change the accessibility level of the member `IntM` to `internal`.</span></span> <span data-ttu-id="db02e-119">この場合、クラスのインスタンス化は可能ですが、内部メンバーへのアクセスはできません。</span><span class="sxs-lookup"><span data-stu-id="db02e-119">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
```  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   internal static int intM = 0;  
}  
```  
  
```  
// Assembly2_a.cs  
// Compile with: /reference:Assembly1.dll  
public class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="db02e-120">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="db02e-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="db02e-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="db02e-121">See Also</span></span>  
 <span data-ttu-id="db02e-122">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="db02e-122">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="db02e-123">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="db02e-123">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="db02e-124">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="db02e-124">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="db02e-125">[アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="db02e-125">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="db02e-126">[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="db02e-126">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="db02e-127">[修飾子](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="db02e-127">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="db02e-128">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="db02e-128">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="db02e-129">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="db02e-129">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 [<span data-ttu-id="db02e-130">protected</span><span class="sxs-lookup"><span data-stu-id="db02e-130">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)

