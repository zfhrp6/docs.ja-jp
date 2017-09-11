---
title: "abstract (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- abstract
- abstract_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
caps.latest.revision: 24
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
ms.openlocfilehash: a109a8e37f84a2e91229bfce789a69cdc26adba9
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="abstract-c-reference"></a><span data-ttu-id="fb515-102">abstract (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="fb515-102">abstract (C# Reference)</span></span>
<span data-ttu-id="fb515-103">`abstract` 修飾子は、その修飾対象の実装が不足しているか、不完全であることを示します。</span><span class="sxs-lookup"><span data-stu-id="fb515-103">The `abstract` modifier indicates that the thing being modified has a missing or incomplete implementation.</span></span> <span data-ttu-id="fb515-104">クラスやメソッド、プロパティ、インデクサー、イベントと組み合わせて abstract 修飾子を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="fb515-104">The abstract modifier can be used with classes, methods, properties, indexers, and events.</span></span> <span data-ttu-id="fb515-105">クラスの宣言では、他のクラスの基底クラスとしての使用のみを意図したクラスであることを示すために `abstract` 修飾子を使います。</span><span class="sxs-lookup"><span data-stu-id="fb515-105">Use the `abstract` modifier in a class declaration to indicate that a class is intended only to be a base class of other classes.</span></span> <span data-ttu-id="fb515-106">abstract としてマークされた (つまり抽象クラスに含まれている) メンバーは、その抽象クラスから派生したクラスで実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb515-106">Members marked as abstract, or included in an abstract class, must be implemented by classes that derive from the abstract class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb515-107">例</span><span class="sxs-lookup"><span data-stu-id="fb515-107">Example</span></span>  
 <span data-ttu-id="fb515-108">この例で、`Area` の機能は、`ShapesClass` から派生している `Square` クラスで実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb515-108">In this example, the class `Square` must provide an implementation of `Area` because it derives from `ShapesClass`:</span></span>  
  
 <span data-ttu-id="fb515-109">[!code-cs[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="fb515-109">[!code-cs[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_1.cs)]</span></span>  
  
 <span data-ttu-id="fb515-110">抽象クラスには次の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="fb515-110">Abstract classes have the following features:</span></span>  
  
-   <span data-ttu-id="fb515-111">抽象クラスはインスタンス化できません。</span><span class="sxs-lookup"><span data-stu-id="fb515-111">An abstract class cannot be instantiated.</span></span>  
  
-   <span data-ttu-id="fb515-112">抽象クラスには抽象メソッドとアクセサーを記述することができます。</span><span class="sxs-lookup"><span data-stu-id="fb515-112">An abstract class may contain abstract methods and accessors.</span></span>  
  
-   <span data-ttu-id="fb515-113">抽象クラスに [sealed](../../../csharp/language-reference/keywords/sealed.md) 修飾子を使った変更を加えることはできません。これは、その 2 つの修飾子がまったく逆の意味を持つためです。</span><span class="sxs-lookup"><span data-stu-id="fb515-113">It is not possible to modify an abstract class with the [sealed](../../../csharp/language-reference/keywords/sealed.md) modifier because the two modifers have opposite meanings.</span></span> <span data-ttu-id="fb515-114">`sealed` 修飾子を指定したクラスは継承が禁止されるのに対し、`abstract` 修飾子を指定したクラスは継承による使用が強制されます。</span><span class="sxs-lookup"><span data-stu-id="fb515-114">The `sealed` modifier prevents a class from being inherited and the `abstract` modifier requires a class to be inherited.</span></span>  
  
-   <span data-ttu-id="fb515-115">抽象クラスから派生した具象クラスには、継承されたすべての抽象メソッドとアクセサーの実際の機能を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb515-115">A non-abstract class derived from an abstract class must include actual implementations of all inherited abstract methods and accessors.</span></span>  
  
 <span data-ttu-id="fb515-116">メソッドまたはプロパティに機能が実装されていないことを示すには、そのメソッドまたはプロパティの宣言で `abstract` 修飾子を使います。</span><span class="sxs-lookup"><span data-stu-id="fb515-116">Use the `abstract` modifier in a method or property declaration to indicate that the method or property does not contain implementation.</span></span>  
  
 <span data-ttu-id="fb515-117">抽象メソッドには次の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="fb515-117">Abstract methods have the following features:</span></span>  
  
-   <span data-ttu-id="fb515-118">抽象メソッドは、仮想メソッドの性質を暗に含んでいます。</span><span class="sxs-lookup"><span data-stu-id="fb515-118">An abstract method is implicitly a virtual method.</span></span>  
  
-   <span data-ttu-id="fb515-119">抽象メソッドの宣言は、抽象クラスでしか認められません。</span><span class="sxs-lookup"><span data-stu-id="fb515-119">Abstract method declarations are only permitted in abstract classes.</span></span>  
  
-   <span data-ttu-id="fb515-120">抽象メソッドの宣言には実際の機能が実装されないため、メソッドの本体はありません。つまり、メソッドの宣言は、末尾のセミコロンがあるだけで、シグネチャの後ろに中かっこ ({ }) は存在しません。</span><span class="sxs-lookup"><span data-stu-id="fb515-120">Because an abstract method declaration provides no actual implementation, there is no method body; the method declaration simply ends with a semicolon and there are no curly braces ({ }) following the signature.</span></span> <span data-ttu-id="fb515-121">例:</span><span class="sxs-lookup"><span data-stu-id="fb515-121">For example:</span></span>  
  
    ```  
    public abstract void MyMethod();  
    ```  
  
     <span data-ttu-id="fb515-122">実際の機能は、オーバーライドする側のメソッド (具象クラスのメンバー) に [override](../../../csharp/language-reference/keywords/override.md) を指定して実装します。</span><span class="sxs-lookup"><span data-stu-id="fb515-122">The implementation is provided by an overriding method[override](../../../csharp/language-reference/keywords/override.md), which is a member of a non-abstract class.</span></span>  
  
-   <span data-ttu-id="fb515-123">抽象メソッドの宣言に [static](../../../csharp/language-reference/keywords/static.md) 修飾子や [virtual](../../../csharp/language-reference/keywords/virtual.md) 修飾子を使うのは誤りです。</span><span class="sxs-lookup"><span data-stu-id="fb515-123">It is an error to use the [static](../../../csharp/language-reference/keywords/static.md) or [virtual](../../../csharp/language-reference/keywords/virtual.md) modifiers in an abstract method declaration.</span></span>  
  
 <span data-ttu-id="fb515-124">抽象プロパティは、宣言と呼び出しの構文の違いを除けば、抽象メソッドと似た働きを持ちます。</span><span class="sxs-lookup"><span data-stu-id="fb515-124">Abstract properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
-   <span data-ttu-id="fb515-125">`abstract` 修飾子を静的プロパティに対して使うのは誤りです。</span><span class="sxs-lookup"><span data-stu-id="fb515-125">It is an error to use the `abstract` modifier on a static property.</span></span>  
  
-   <span data-ttu-id="fb515-126">継承する抽象プロパティは、派生クラス内で [override](../../../csharp/language-reference/keywords/override.md) 修飾子を使ったプロパティ宣言を記述することでオーバーライドすることができます。</span><span class="sxs-lookup"><span data-stu-id="fb515-126">An abstract inherited property can be overridden in a derived class by including a property declaration that uses the [override](../../../csharp/language-reference/keywords/override.md) modifier.</span></span>  
  
 <span data-ttu-id="fb515-127">抽象クラスの詳細については、「[抽象クラスとシール クラス、およびクラス メンバー](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb515-127">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="fb515-128">すべてのインターフェイス メンバーの機能は、抽象クラスで実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb515-128">An abstract class must provide implementation for all interface members.</span></span>  
  
 <span data-ttu-id="fb515-129">インターフェイスを実装する抽象クラスで、インターフェイス メソッドを抽象メソッドにマップすることもできます。</span><span class="sxs-lookup"><span data-stu-id="fb515-129">An abstract class that implements an interface might map the interface methods onto abstract methods.</span></span> <span data-ttu-id="fb515-130">例:</span><span class="sxs-lookup"><span data-stu-id="fb515-130">For example:</span></span>  
  
 <span data-ttu-id="fb515-131">[!code-cs[csrefKeywordsModifiers#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="fb515-131">[!code-cs[csrefKeywordsModifiers#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb515-132">例</span><span class="sxs-lookup"><span data-stu-id="fb515-132">Example</span></span>  
 <span data-ttu-id="fb515-133">この例の `DerivedClass` クラスは、抽象クラス `BaseClass` から派生しています。</span><span class="sxs-lookup"><span data-stu-id="fb515-133">In this example, the class `DerivedClass` is derived from an abstract class `BaseClass`.</span></span> <span data-ttu-id="fb515-134">この抽象クラスには、`AbstractMethod` という抽象メソッドのほか、`X` と `Y` の 2 つの抽象プロパティが存在します。</span><span class="sxs-lookup"><span data-stu-id="fb515-134">The abstract class contains an abstract method, `AbstractMethod`, and two abstract properties, `X` and `Y`.</span></span>  
  
 <span data-ttu-id="fb515-135">[!code-cs[csrefKeywordsModifiers#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="fb515-135">[!code-cs[csrefKeywordsModifiers#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_3.cs)]</span></span>  
  
 <span data-ttu-id="fb515-136">この例の抽象クラスを次のようなステートメントでインスタンス化しようとするとどうなるかを次に示します。</span><span class="sxs-lookup"><span data-stu-id="fb515-136">In the preceding example, if you attempt to instantiate the abstract class by using a statement like this:</span></span>  
  
```  
BaseClass bc = new BaseClass();   // Error  
```  
  
 <span data-ttu-id="fb515-137">このように、抽象クラス 'BaseClass' のインスタンスをコンパイラが作成できないことを伝えるエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="fb515-137">you will get an error saying that the compiler cannot create an instance of the abstract class 'BaseClass'.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="fb515-138">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="fb515-138">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fb515-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="fb515-139">See Also</span></span>  
 <span data-ttu-id="fb515-140">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="fb515-140">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="fb515-141">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="fb515-141">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="fb515-142">[修飾子](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="fb515-142">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="fb515-143">[virtual](../../../csharp/language-reference/keywords/virtual.md) </span><span class="sxs-lookup"><span data-stu-id="fb515-143">[virtual](../../../csharp/language-reference/keywords/virtual.md) </span></span>  
 <span data-ttu-id="fb515-144">[override](../../../csharp/language-reference/keywords/override.md) </span><span class="sxs-lookup"><span data-stu-id="fb515-144">[override](../../../csharp/language-reference/keywords/override.md) </span></span>  
 [<span data-ttu-id="fb515-145">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="fb515-145">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)

