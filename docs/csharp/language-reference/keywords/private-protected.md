---
title: "private protected (c# リファレンス)"
ms.date: 11/15/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
author: sputier
ms.author: wiwagn
ms.openlocfilehash: 5f7abd2569d5bad5af64161042e4e5d21e741c8c
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="914f2-102">private protected (c# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="914f2-102">private protected (C# Reference)</span></span>
<span data-ttu-id="914f2-103">`private protected`キーワードの組み合わせは、メンバー アクセス修飾子。</span><span class="sxs-lookup"><span data-stu-id="914f2-103">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="914f2-104">プライベート、プロテクト メンバーは、含んでいるアセンブリ内でのみが、外側のクラスから派生した型からアクセス可能です。</span><span class="sxs-lookup"><span data-stu-id="914f2-104">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="914f2-105">`private protected` と他のアクセス修飾子の比較については、「[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="914f2-105">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 
   
## <a name="example"></a><span data-ttu-id="914f2-106">例</span><span class="sxs-lookup"><span data-stu-id="914f2-106">Example</span></span>  
 <span data-ttu-id="914f2-107">変数の静的な型が派生クラス型である場合にのみ、基底クラスのプライベート、プロテクト メンバーは、含んでいるアセンブリでの派生型からアクセス可能です。</span><span class="sxs-lookup"><span data-stu-id="914f2-107">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="914f2-108">たとえば、次のコード セグメントを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="914f2-108">For example, consider the following code segment:</span></span>  
  
 ```
 // Assembly1.cs  
 // Compile with: /target:library  
 public class BaseClass
 {
     private protected int myValue = 0;
 }
 
 public class DerivedClass1 : BaseClass
 {
     void Access()
     {
         BaseClass baseObject = new BaseClass();
 
         // Error CS1540, because myValue can only be accessed by
         // classes derived from BaseClass.
         // baseObject.myValue = 5;  
 
         // OK, accessed through the current derived class instance
         myValue = 5;
     }
 }
```  
  
```  
 // Assembly2.cs  
 // Compile with: /reference:Assembly1.dll  
 class DerivedClass2 : BaseClass
 {
     void Access()
     {
         // Error CS0122, because myValue can only be
         // accessed by types in Assembly1
         // myValue = 10;
     }
 }
```  
 <span data-ttu-id="914f2-109">この例には、2 つのファイル (`Assembly1.cs` と `Assembly2.cs`) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="914f2-109">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span> <span data-ttu-id="914f2-110">最初のファイルにはパブリック基底クラスが含まれています`BaseClass`、および、その派生型`DerivedClass1`です。</span><span class="sxs-lookup"><span data-stu-id="914f2-110">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="914f2-111">`BaseClass`プライベートのプロテクト メンバーを所有している`myValue`、どの`DerivedClass1`に 2 つの方法でアクセスしようとしています。</span><span class="sxs-lookup"><span data-stu-id="914f2-111">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="914f2-112">最初の試行にアクセスする`myValue`のインスタンスを通じて`BaseClass`でエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="914f2-112">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="914f2-113">ただし、継承されたメンバーとして使用しようとすると、`DerivedClass1`は成功します。</span><span class="sxs-lookup"><span data-stu-id="914f2-113">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>
<span data-ttu-id="914f2-114">2 番目のファイルへのアクセスに`myValue`の継承されたメンバーと`DerivedClass2`Assembly1 での派生型からアクセス可能なだけ、エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="914f2-114">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span> 

 <span data-ttu-id="914f2-115">構造体のメンバーにすることはできません`private protected`のため、構造体は継承できません。</span><span class="sxs-lookup"><span data-stu-id="914f2-115">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="914f2-116">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="914f2-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="914f2-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="914f2-117">See Also</span></span>  
 <span data-ttu-id="914f2-118">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="914f2-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="914f2-119">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="914f2-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="914f2-120">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="914f2-120">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="914f2-121">[アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="914f2-121">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="914f2-122">[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="914f2-122">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="914f2-123">[修飾子](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="914f2-123">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="914f2-124">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="914f2-124">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="914f2-125">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="914f2-125">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="914f2-126">[internal](../../../csharp/language-reference/keywords/internal.md) </span><span class="sxs-lookup"><span data-stu-id="914f2-126">[internal](../../../csharp/language-reference/keywords/internal.md) </span></span>  
 <span data-ttu-id="914f2-127">[Internal virtual キーワードのセキュリティに関する注意事項](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="914f2-127">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>
