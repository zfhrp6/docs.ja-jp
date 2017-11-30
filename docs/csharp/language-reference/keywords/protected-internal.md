---
title: "保護された内部 (c# リファレンス)"
ms.date: 11/15/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
author: sputier
ms.author: wiwagn
ms.openlocfilehash: f9004a5e8d65179c9ff2e30688e63c14c95ab431
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="16d23-102">保護された内部 (c# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="16d23-102">protected internal (C# Reference)</span></span>
<span data-ttu-id="16d23-103">`protected internal`キーワードの組み合わせは、メンバー アクセス修飾子。</span><span class="sxs-lookup"><span data-stu-id="16d23-103">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="16d23-104">プロテクト内部メンバーは、現在のアセンブリとは、含んでいるクラスから派生した型からアクセス可能です。</span><span class="sxs-lookup"><span data-stu-id="16d23-104">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="16d23-105">`protected internal` と他のアクセス修飾子の比較については、「[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16d23-105">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 
   
## <a name="example"></a><span data-ttu-id="16d23-106">例</span><span class="sxs-lookup"><span data-stu-id="16d23-106">Example</span></span>  
 <span data-ttu-id="16d23-107">基底クラスのプロテクト内部メンバーは、含んでいるアセンブリ内の任意の型からアクセスします。</span><span class="sxs-lookup"><span data-stu-id="16d23-107">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="16d23-108">派生クラス型の変数を使用して、アクセスが行われる場合にのみ、別のアセンブリ内にある派生クラスではアクセスもできます。</span><span class="sxs-lookup"><span data-stu-id="16d23-108">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="16d23-109">たとえば、次のコード セグメントを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="16d23-109">For example, consider the following code segment:</span></span>  

```
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
  
```  
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
 <span data-ttu-id="16d23-110">この例には、2 つのファイル (`Assembly1.cs` と `Assembly2.cs`) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="16d23-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span> <span data-ttu-id="16d23-111">最初のファイルにはパブリック基底クラスが含まれています`BaseClass`、および別のクラス、`TestAccess`です。</span><span class="sxs-lookup"><span data-stu-id="16d23-111">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="16d23-112">`BaseClass`プロテクトの内部メンバーを所有している`myValue`、によってアクセスされる、`TestAccess`型です。</span><span class="sxs-lookup"><span data-stu-id="16d23-112">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span> <span data-ttu-id="16d23-113">2 番目のファイルへのアクセスに`myValue`のインスタンスを通じて`BaseClass`、派生クラスのインスタンスを使用してこのメンバーへのアクセス中にエラーが生成されます`DerivedClass`は成功します。</span><span class="sxs-lookup"><span data-stu-id="16d23-113">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span> 

 <span data-ttu-id="16d23-114">構造体のメンバーにすることはできません`protected internal`のため、構造体は継承できません。</span><span class="sxs-lookup"><span data-stu-id="16d23-114">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="16d23-115">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="16d23-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="16d23-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="16d23-116">See Also</span></span>  
 <span data-ttu-id="16d23-117">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="16d23-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="16d23-118">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="16d23-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="16d23-119">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="16d23-119">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="16d23-120">[アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="16d23-120">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="16d23-121">[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="16d23-121">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="16d23-122">[修飾子](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="16d23-122">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="16d23-123">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="16d23-123">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="16d23-124">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="16d23-124">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="16d23-125">[internal](../../../csharp/language-reference/keywords/internal.md) </span><span class="sxs-lookup"><span data-stu-id="16d23-125">[internal](../../../csharp/language-reference/keywords/internal.md) </span></span>  
 <span data-ttu-id="16d23-126">[Internal virtual キーワードのセキュリティに関する注意事項](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="16d23-126">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>
