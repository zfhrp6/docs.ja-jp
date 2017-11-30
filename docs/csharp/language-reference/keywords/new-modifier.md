---
title: "new 修飾子 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 28124c2f3ecef01fd4bc43fe7cfc975dd6466506
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="new-modifier-c-reference"></a><span data-ttu-id="91eaf-102">new 修飾子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="91eaf-102">new Modifier (C# Reference)</span></span>
<span data-ttu-id="91eaf-103">`new` キーワードを宣言の修飾子として使用すると、基底クラスから継承されたメンバーを明示的に隠ぺいできます。</span><span class="sxs-lookup"><span data-stu-id="91eaf-103">When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class.</span></span> <span data-ttu-id="91eaf-104">継承されたメンバーを隠ぺいすると、派生バージョンのメンバーで基底クラスのバージョンが置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="91eaf-104">When you hide an inherited member, the derived version of the member replaces the base class version.</span></span> <span data-ttu-id="91eaf-105">`new` 修飾子を使わずにメンバーを隠ぺいすることもできますが、コンパイラ警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="91eaf-105">Although you can hide members without using the `new` modifier, you get a compiler warning.</span></span> <span data-ttu-id="91eaf-106">メンバーを明示的に隠ぺいするために `new` を使用する場合は、この警告が抑制されます。</span><span class="sxs-lookup"><span data-stu-id="91eaf-106">If you use `new` to explicitly hide a member, it suppresses this warning.</span></span>  
  
 <span data-ttu-id="91eaf-107">継承されたメンバーを隠ぺいするには、派生クラスで同じメンバー名を使用してメンバーを宣言し、`new` キーワードで修飾します。</span><span class="sxs-lookup"><span data-stu-id="91eaf-107">To hide an inherited member, declare it in the derived class by using the same member name, and modify it with the `new` keyword.</span></span> <span data-ttu-id="91eaf-108">例:</span><span class="sxs-lookup"><span data-stu-id="91eaf-108">For example:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_1.cs)]  
  
 <span data-ttu-id="91eaf-109">この例では、`BaseC.Invoke` は `DerivedC.Invoke` で隠ぺいされます。</span><span class="sxs-lookup"><span data-stu-id="91eaf-109">In this example, `BaseC.Invoke` is hidden by `DerivedC.Invoke`.</span></span> <span data-ttu-id="91eaf-110">`x` フィールドは、似た名前によって隠ぺいされないため、影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="91eaf-110">The field `x` is not affected because it is not hidden by a similar name.</span></span>  
  
 <span data-ttu-id="91eaf-111">継承による名前の隠ぺいは、次のいずれかの形式で行われます。</span><span class="sxs-lookup"><span data-stu-id="91eaf-111">Name hiding through inheritance takes one of the following forms:</span></span>  
  
-   <span data-ttu-id="91eaf-112">一般的に、定数、フィールド、プロパティ、型をクラスまたは構造体で使用すると、同じ名前を共有するすべての基底クラス メンバーが隠ぺいされます。</span><span class="sxs-lookup"><span data-stu-id="91eaf-112">Generally, a constant, field, property, or type that is introduced in a class or struct hides all base class members that share its name.</span></span>  <span data-ttu-id="91eaf-113">次のような特殊な状況があります。</span><span class="sxs-lookup"><span data-stu-id="91eaf-113">There are special cases.</span></span>  <span data-ttu-id="91eaf-114">たとえば、呼び出し可能ではない型を持つ `N` という名前の新しいフィールドを宣言し、基本型が `N` をメソッドとして宣言する場合は、新しいフィールドが呼び出し構文内で基本型の宣言を隠ぺいすることはありません。</span><span class="sxs-lookup"><span data-stu-id="91eaf-114">For example, if you declare a new field with name `N` to have a type that is not invocable, and a base type declares `N` to be a method, the new field does not hide the base declaration in invocation syntax.</span></span>  <span data-ttu-id="91eaf-115">参照してください、 [5.0 c# 言語仕様](http://go.microsoft.com/fwlink/?LinkId=199552)詳細については (セクション"Expressions"の「メンバーの照合」セクションを参照してください)。</span><span class="sxs-lookup"><span data-stu-id="91eaf-115">See the [C# 5.0 language specification](http://go.microsoft.com/fwlink/?LinkId=199552) for details (see section "Member Lookup" in section "Expressions").</span></span>  
  
-   <span data-ttu-id="91eaf-116">メソッドをクラスまたは構造体で使用すると、基底クラスで同じ名前を共有するプロパティ、フィールド、型が隠ぺいされます。</span><span class="sxs-lookup"><span data-stu-id="91eaf-116">A method introduced in a class or struct hides properties, fields, and types that share that name in the base class.</span></span> <span data-ttu-id="91eaf-117">また、同じシグネチャを持つすべての基底クラス メソッドも隠ぺいされます。</span><span class="sxs-lookup"><span data-stu-id="91eaf-117">It also hides all base class methods that have the same signature.</span></span>  
  
-   <span data-ttu-id="91eaf-118">インデクサーをクラスまたは構造体で使用すると、同じシグネチャを持つすべての基底クラス インデクサーが隠ぺいされます。</span><span class="sxs-lookup"><span data-stu-id="91eaf-118">An indexer introduced in a class or struct hides all base class indexers that have the same signature.</span></span>  
  
 <span data-ttu-id="91eaf-119">`new` と [override](../../../csharp/language-reference/keywords/override.md) には相反する意味があるため、同じメンバーにこの 2 つの修飾子を使用するとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="91eaf-119">It is an error to use both `new` and [override](../../../csharp/language-reference/keywords/override.md) on the same member, because the two modifiers have mutually exclusive meanings.</span></span> <span data-ttu-id="91eaf-120">`new` 修飾子は、同じ名前で新しいメンバーを作成し、元のメンバーを隠ぺいします。</span><span class="sxs-lookup"><span data-stu-id="91eaf-120">The `new` modifier creates a new member with the same name and causes the original member to become hidden.</span></span> <span data-ttu-id="91eaf-121">`override` 修飾子は、継承されたメンバーの実装を拡張します。</span><span class="sxs-lookup"><span data-stu-id="91eaf-121">The `override` modifier extends the implementation for an inherited member.</span></span>  
  
 <span data-ttu-id="91eaf-122">宣言で、継承されたメンバーを隠ぺいしない `new` 修飾子を使用すると、警告が出力されます。</span><span class="sxs-lookup"><span data-stu-id="91eaf-122">Using the `new` modifier in a declaration that does not hide an inherited member generates a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91eaf-123">例</span><span class="sxs-lookup"><span data-stu-id="91eaf-123">Example</span></span>  
 <span data-ttu-id="91eaf-124">この例では、基底クラス `BaseC` と派生クラス `DerivedC` が同じフィールド名 `x` を使用するため、継承されるフィールドの値が隠ぺいされます。</span><span class="sxs-lookup"><span data-stu-id="91eaf-124">In this example, a base class, `BaseC`, and a derived class, `DerivedC`, use the same field name `x`, which hides the value of the inherited field.</span></span> <span data-ttu-id="91eaf-125">この例では、`new` 修飾子の使い方を示します。</span><span class="sxs-lookup"><span data-stu-id="91eaf-125">The example demonstrates the use of the `new` modifier.</span></span> <span data-ttu-id="91eaf-126">また、基底クラスの隠ぺいされたメンバーに完全修飾名を使ってアクセスする方法も示します。</span><span class="sxs-lookup"><span data-stu-id="91eaf-126">It also demonstrates how to access the hidden members of the base class by using their fully qualified names.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="91eaf-127">例</span><span class="sxs-lookup"><span data-stu-id="91eaf-127">Example</span></span>  
 <span data-ttu-id="91eaf-128">この例では、入れ子になったクラスが、基底クラスにある同名のクラスを隠ぺいします。</span><span class="sxs-lookup"><span data-stu-id="91eaf-128">In this example, a nested class hides a class that has the same name in the base class.</span></span> <span data-ttu-id="91eaf-129">この例では、`new` 修飾子を使って警告メッセージが表示されないようにする方法に加えて、完全修飾名を使用してクラスの隠ぺいされたメンバーにアクセスする方法も示します。</span><span class="sxs-lookup"><span data-stu-id="91eaf-129">The example demonstrates how to use the `new` modifier to eliminate the warning message and how to access the hidden class members by using their fully qualified names.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_3.cs)]  
  
 <span data-ttu-id="91eaf-130">`new` 修飾子を削除すると、プログラムのコンパイルおよび実行は行われますが、次の警告が出力されます。</span><span class="sxs-lookup"><span data-stu-id="91eaf-130">If you remove the `new` modifier, the program will still compile and run, but you will get the following warning:</span></span>  
  
```  
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="91eaf-131">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="91eaf-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="91eaf-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="91eaf-132">See Also</span></span>  
 [<span data-ttu-id="91eaf-133">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="91eaf-133">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="91eaf-134">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="91eaf-134">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="91eaf-135">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="91eaf-135">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="91eaf-136">演算子のキーワード</span><span class="sxs-lookup"><span data-stu-id="91eaf-136">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="91eaf-137">修飾子</span><span class="sxs-lookup"><span data-stu-id="91eaf-137">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="91eaf-138">Override キーワードと New キーワードによるバージョン管理</span><span class="sxs-lookup"><span data-stu-id="91eaf-138">Versioning with the Override and New Keywords</span></span>](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
 [<span data-ttu-id="91eaf-139">Override キーワードと New キーワードを使用する場合について</span><span class="sxs-lookup"><span data-stu-id="91eaf-139">Knowing When to Use Override and New Keywords</span></span>](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
