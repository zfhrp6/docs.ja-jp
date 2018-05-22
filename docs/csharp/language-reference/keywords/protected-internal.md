---
title: protected internal (C# リファレンス)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 5ba2c811a1a4f095bcee65ed6678a7dc50fe94db
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="c1caf-102">protected internal (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="c1caf-102">protected internal (C# Reference)</span></span>
<span data-ttu-id="c1caf-103">キーワード組み合わせ `protected internal` はメンバー アクセス修飾子です。</span><span class="sxs-lookup"><span data-stu-id="c1caf-103">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="c1caf-104">protected internal メンバーには、現在のアセンブリから、または包含クラスから派生した型からアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c1caf-104">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="c1caf-105">`protected internal` と他のアクセス修飾子の比較については、「[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1caf-105">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 
   
## <a name="example"></a><span data-ttu-id="c1caf-106">例</span><span class="sxs-lookup"><span data-stu-id="c1caf-106">Example</span></span>  
 <span data-ttu-id="c1caf-107">基底クラスのプロテクト内部メンバーは、包含アセンブリ内の任意の型からアクセスします。</span><span class="sxs-lookup"><span data-stu-id="c1caf-107">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="c1caf-108">派生クラス型の変数経由でアクセスする場合にのみ、別のアセンブリにある派生クラスでもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c1caf-108">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="c1caf-109">たとえば、次のコード セグメントを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="c1caf-109">For example, consider the following code segment:</span></span>  

```csharp
// Assembly1.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   protected internal int myValue = 0;  
}

class TestAccess 
{
    void Access()
    {
        BaseClass baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}  
```  
  
```csharp  
// Assembly2.cs  
// Compile with: /reference:Assembly1.dll  
class DerivedClass : BaseClass   
{  
    static void Main()
    {
        BaseClass baseObject = new BaseClass();
        DerivedClass derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10; 

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
} 
```  
 <span data-ttu-id="c1caf-110">この例には、2 つのファイル (`Assembly1.cs` と `Assembly2.cs`) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c1caf-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span> <span data-ttu-id="c1caf-111">最初のファイルには public 基底クラスである `BaseClass` ともう 1 つのクラスである `TestAccess` が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c1caf-111">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="c1caf-112">`BaseClass` は protected internal メンバーの `myValue` を持っています。これは `TestAccess` 型にアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="c1caf-112">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span> <span data-ttu-id="c1caf-113">2 番目のファイルでは、`BaseClass` のインスタンス経由で `myValue` にアクセスしようとするとエラーが発生します。一方で、派生クラス `DerivedClass` のインスタンスからこのメンバーにアクセスすると成功します。</span><span class="sxs-lookup"><span data-stu-id="c1caf-113">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span> 

 <span data-ttu-id="c1caf-114">構造体は継承できないため、構造体メンバーは `protected internal` になりません。</span><span class="sxs-lookup"><span data-stu-id="c1caf-114">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c1caf-115">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="c1caf-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c1caf-116">参照</span><span class="sxs-lookup"><span data-stu-id="c1caf-116">See Also</span></span>  
 <span data-ttu-id="c1caf-117">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="c1caf-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="c1caf-118">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c1caf-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="c1caf-119">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="c1caf-119">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="c1caf-120">[アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="c1caf-120">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="c1caf-121">[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="c1caf-121">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="c1caf-122">[修飾子](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="c1caf-122">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="c1caf-123">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="c1caf-123">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="c1caf-124">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="c1caf-124">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="c1caf-125">[internal](../../../csharp/language-reference/keywords/internal.md) </span><span class="sxs-lookup"><span data-stu-id="c1caf-125">[internal](../../../csharp/language-reference/keywords/internal.md) </span></span>  
 <span data-ttu-id="c1caf-126">[Internal Virtual キーワードのセキュリティ関連事項](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="c1caf-126">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>
