---
title: static (C# リファレンス)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
caps.latest.revision: 26
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c47f4a19843039c27ef9f1602581d1004fb8fd76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="static-c-reference"></a><span data-ttu-id="42061-102">static (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="42061-102">static (C# Reference)</span></span>
<span data-ttu-id="42061-103">`static` 修飾子は、静的メンバーの宣言に使用します。静的メンバーは、特定のオブジェクトではなく、型自体に属するメンバーです。</span><span class="sxs-lookup"><span data-stu-id="42061-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="42061-104">`static` 修飾子は、クラス、フィールド、メソッド、プロパティ、演算子、イベント、コンストラクターと組み合わせて使用できますが、クラス以外のインデクサー、ファイナライザー、型で使うことはできません。</span><span class="sxs-lookup"><span data-stu-id="42061-104">The `static` modifier can be used with classes, fields, methods, properties, operators, events, and constructors, but it cannot be used with indexers, finalizers, or types other than classes.</span></span> <span data-ttu-id="42061-105">詳細については、「[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42061-105">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="42061-106">例</span><span class="sxs-lookup"><span data-stu-id="42061-106">Example</span></span>  
 <span data-ttu-id="42061-107">次のクラスは `static` として宣言され、`static` メソッドのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="42061-107">The following class is declared as `static` and contains only `static` methods:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_1.cs)]  
  
 <span data-ttu-id="42061-108">定数宣言や型宣言は、暗黙的な静的メンバーです。</span><span class="sxs-lookup"><span data-stu-id="42061-108">A constant or type declaration is implicitly a static member.</span></span>  
  
 <span data-ttu-id="42061-109">静的メンバーは、インスタンスを使って参照できません。</span><span class="sxs-lookup"><span data-stu-id="42061-109">A static member cannot be referenced through an instance.</span></span> <span data-ttu-id="42061-110">代わりに、型の名前を使って参照します。</span><span class="sxs-lookup"><span data-stu-id="42061-110">Instead, it is referenced through the type name.</span></span> <span data-ttu-id="42061-111">たとえば、次のクラスを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="42061-111">For example, consider the following class:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_2.cs)]  
  
 <span data-ttu-id="42061-112">静的メンバー `x` を参照するには、同じスコープからその静的メンバーにアクセス可能でない限り、完全修飾名 (`MyBaseC.MyStruct.x`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="42061-112">To refer to the static member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>  
  
```csharp  
Console.WriteLine(MyBaseC.MyStruct.x);  
```  
  
 <span data-ttu-id="42061-113">クラスのインスタンスには、そのクラスのインスタンス フィールドすべてにそれぞれのコピーが含まれていますが、各静的フィールドのコピーは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="42061-113">While an instance of a class contains a separate copy of all instance fields of the class, there is only one copy of each static field.</span></span>  
  
 <span data-ttu-id="42061-114">静的メソッドまたはプロパティ アクセサーへの参照には、[this](../../../csharp/language-reference/keywords/this.md) は使用できません。</span><span class="sxs-lookup"><span data-stu-id="42061-114">It is not possible to use [this](../../../csharp/language-reference/keywords/this.md) to reference static methods or property accessors.</span></span>  
  
 <span data-ttu-id="42061-115">`static` キーワードをクラスに適用する場合、そのクラスのすべてのメンバーが静的でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="42061-115">If the `static` keyword is applied to a class, all the members of the class must be static.</span></span>  
  
 <span data-ttu-id="42061-116">クラスおよび静的クラスには、静的コンストラクターを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="42061-116">Classes and static classes may have static constructors.</span></span> <span data-ttu-id="42061-117">静的コンストラクターは、プログラムが開始されてからクラスがインスタンス化されるまでの間に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="42061-117">Static constructors are called at some point between when the program starts and the class is instantiated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42061-118">`static` キーワードの用法は、C++ の場合よりも制限されています。</span><span class="sxs-lookup"><span data-stu-id="42061-118">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="42061-119">C++ キーワードと比較するには、「[ストレージ クラス (C++)](/cpp/cpp/storage-classes-cpp#static)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="42061-119">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>
  
 <span data-ttu-id="42061-120">静的メンバーの例を示すために、ある企業の従業員を表すクラスを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="42061-120">To demonstrate static members, consider a class that represents a company employee.</span></span> <span data-ttu-id="42061-121">このクラスには、従業員数を数えるメソッドと、従業員数を格納するフィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="42061-121">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="42061-122">メソッドとフィールドはどちらも、従業員のインスタンスに属しておらず、</span><span class="sxs-lookup"><span data-stu-id="42061-122">Both the method and the field do not belong to any instance employee.</span></span> <span data-ttu-id="42061-123">企業クラスに属しています。</span><span class="sxs-lookup"><span data-stu-id="42061-123">Instead they belong to the company class.</span></span> <span data-ttu-id="42061-124">そのため、クラスの静的メンバーとして宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="42061-124">Therefore, they should be declared as static members of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42061-125">例</span><span class="sxs-lookup"><span data-stu-id="42061-125">Example</span></span>  
 <span data-ttu-id="42061-126">この例では、新しい従業員の名前と ID を読み取り、従業員数のカウンターを 1 つインクリメントして、新しい従業員の情報と従業員数を表示します。</span><span class="sxs-lookup"><span data-stu-id="42061-126">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="42061-127">説明を簡単にするために、この例では、現在の従業員数をキーボード入力から読み取っていますが、</span><span class="sxs-lookup"><span data-stu-id="42061-127">For simplicity, this program reads the current number of employees from the keyboard.</span></span> <span data-ttu-id="42061-128">実際のアプリケーションでは、ファイルから情報を読み取るようにしてください。</span><span class="sxs-lookup"><span data-stu-id="42061-128">In a real application, this information should be read from a file.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="42061-129">例</span><span class="sxs-lookup"><span data-stu-id="42061-129">Example</span></span>  
 <span data-ttu-id="42061-130">この例では、宣言されていない別の静的フィールドを使用して静的フィールドを初期化できても、静的フィールドに値を明示的に割り当てない限り、結果は未定義になることを示します。</span><span class="sxs-lookup"><span data-stu-id="42061-130">This example shows that although you can initialize a static field by using another static field not yet declared, the results will be undefined until you explicitly assign a value to the static field.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="42061-131">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="42061-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="42061-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="42061-132">See Also</span></span>  
 [<span data-ttu-id="42061-133">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="42061-133">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="42061-134">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="42061-134">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="42061-135">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="42061-135">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="42061-136">修飾子</span><span class="sxs-lookup"><span data-stu-id="42061-136">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="42061-137">静的クラスと静的クラス メンバー</span><span class="sxs-lookup"><span data-stu-id="42061-137">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
