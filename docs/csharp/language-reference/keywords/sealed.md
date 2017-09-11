---
title: "sealed (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- sealed
- sealed_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
caps.latest.revision: 30
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
ms.openlocfilehash: a8d0fe959eac03aad4f1ae1fada61c0ad2fd65cd
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="sealed-c-reference"></a><span data-ttu-id="88add-102">sealed (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="88add-102">sealed (C# Reference)</span></span>
<span data-ttu-id="88add-103">`sealed` 修飾子をクラスに適用すると、それ以外のクラスが、そのクラスから継承できなくなります。</span><span class="sxs-lookup"><span data-stu-id="88add-103">When applied to a class, the `sealed` modifier prevents other classes from inheriting from it.</span></span> <span data-ttu-id="88add-104">次の例では、`B` クラスは `A` クラスを継承しますが、`B` クラスからはどのクラスも継承できなくなります。</span><span class="sxs-lookup"><span data-stu-id="88add-104">In the following example, class `B` inherits from class `A`, but no class can inherit from class `B`.</span></span>  
  
```  
class A {}      
sealed class B : A {}  
```  
  
 <span data-ttu-id="88add-105">`sealed` 修飾子は、基底クラスの仮想メソッドまたは仮想プロパティをオーバーライドするメソッドやプロパティで使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="88add-105">You can also use the `sealed` modifier on a method or property that overrides a virtual method or property in a base class.</span></span> <span data-ttu-id="88add-106">これにより、クラスの派生が行えるようになり、そのクラスが特定の仮想メソッドまたは仮想プロパティをオーバーライドできなくなります。</span><span class="sxs-lookup"><span data-stu-id="88add-106">This enables you to allow classes to derive from your class and prevent them from overriding specific virtual methods or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88add-107">例</span><span class="sxs-lookup"><span data-stu-id="88add-107">Example</span></span>  
 <span data-ttu-id="88add-108">次の例では、`Z` は `Y` から継承しますが、`Z` は仮想関数 `F` をオーバーライドできません。この仮想関数は `X` で宣言されており、`Y` でシールされています。</span><span class="sxs-lookup"><span data-stu-id="88add-108">In the following example, `Z` inherits from `Y` but `Z` cannot override the virtual function `F` that is declared in `X` and sealed in `Y`.</span></span>  
  
 <span data-ttu-id="88add-109">[!code-cs[csrefKeywordsModifiers#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="88add-109">[!code-cs[csrefKeywordsModifiers#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_1.cs)]</span></span>  
  
 <span data-ttu-id="88add-110">新しいメソッドまたはプロパティをクラスで定義するときに、派生クラスによるオーバーライドを防ぐには、その派生クラスを [virtual](../../../csharp/language-reference/keywords/virtual.md) として宣言しないようにします。</span><span class="sxs-lookup"><span data-stu-id="88add-110">When you define new methods or properties in a class, you can prevent deriving classes from overriding them by not declaring them as [virtual](../../../csharp/language-reference/keywords/virtual.md).</span></span>  
  
 <span data-ttu-id="88add-111">[abstract](../../../csharp/language-reference/keywords/abstract.md) 修飾子をシール クラスで使用するとエラーになります。抽象メソッドまたは抽象プロパティを実装するクラスでは、抽象クラスを継承する必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="88add-111">It is an error to use the [abstract](../../../csharp/language-reference/keywords/abstract.md) modifier with a sealed class, because an abstract class must be inherited by a class that provides an implementation of the abstract methods or properties.</span></span>  
  
 <span data-ttu-id="88add-112">`sealed` 修飾子は、メソッドまたはプロパティに適用するときは、常に [override](../../../csharp/language-reference/keywords/override.md) と一緒に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="88add-112">When applied to a method or property, the `sealed` modifier must always be used with [override](../../../csharp/language-reference/keywords/override.md).</span></span>  
  
 <span data-ttu-id="88add-113">構造体は暗黙的にシールされるため、継承できません。</span><span class="sxs-lookup"><span data-stu-id="88add-113">Because structs are implicitly sealed, they cannot be inherited.</span></span>  
  
 <span data-ttu-id="88add-114">詳細については、「[継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="88add-114">For more information, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span></span>  
  
 <span data-ttu-id="88add-115">上記以外の例については、「[抽象クラスとシール クラス、およびクラス メンバー](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="88add-115">For more examples, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="88add-116">例</span><span class="sxs-lookup"><span data-stu-id="88add-116">Example</span></span>  
 <span data-ttu-id="88add-117">[!code-cs[csrefKeywordsModifiers#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="88add-117">[!code-cs[csrefKeywordsModifiers#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_2.cs)]</span></span>  
  
 <span data-ttu-id="88add-118">前の例で、次のステートメントを使用して、シール クラスからの継承を試みたとします。</span><span class="sxs-lookup"><span data-stu-id="88add-118">In the previous example, you might try to inherit from the sealed class by using the following statement:</span></span>  
  
 `class MyDerivedC: SealedClass {}   // Error`  
  
 <span data-ttu-id="88add-119">この場合、次のエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="88add-119">The result is an error message:</span></span>  
  
 `'MyDerivedC' cannot inherit from sealed class 'SealedClass'.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="88add-120">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="88add-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="remarks"></a><span data-ttu-id="88add-121">コメント</span><span class="sxs-lookup"><span data-stu-id="88add-121">Remarks</span></span>  
 <span data-ttu-id="88add-122">クラス、メソッド、またはプロパティをシールするかどうかを判断するには、通常、次の 2 つの点を検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="88add-122">To determine whether to seal a class, method, or property, you should generally consider the following two points:</span></span>  
  
-   <span data-ttu-id="88add-123">クラスをカスタマイズすることで、派生クラスにもたらされる可能性があるメリット。</span><span class="sxs-lookup"><span data-stu-id="88add-123">The potential benefits that deriving classes might gain through the ability to customize your class.</span></span>  
  
-   <span data-ttu-id="88add-124">派生クラスがクラスを変更することで、そのクラスが正常に、または期待どおりに機能しなくなる可能性。</span><span class="sxs-lookup"><span data-stu-id="88add-124">The potential that deriving classes could modify your classes in such a way that they would no longer work correctly or as expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88add-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="88add-125">See Also</span></span>  
 <span data-ttu-id="88add-126">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="88add-126">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="88add-127">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="88add-127">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="88add-128">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="88add-128">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="88add-129">[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) </span><span class="sxs-lookup"><span data-stu-id="88add-129">[Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) </span></span>  
 <span data-ttu-id="88add-130">[抽象クラスとシール クラス、およびクラス メンバー](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md) </span><span class="sxs-lookup"><span data-stu-id="88add-130">[Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md) </span></span>  
 <span data-ttu-id="88add-131">[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="88add-131">[Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span></span>  
 <span data-ttu-id="88add-132">[修飾子](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="88add-132">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="88add-133">[override](../../../csharp/language-reference/keywords/override.md) </span><span class="sxs-lookup"><span data-stu-id="88add-133">[override](../../../csharp/language-reference/keywords/override.md) </span></span>  
 [<span data-ttu-id="88add-134">virtual</span><span class="sxs-lookup"><span data-stu-id="88add-134">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)

