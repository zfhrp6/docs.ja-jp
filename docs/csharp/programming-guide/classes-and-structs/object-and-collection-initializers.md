---
title: "オブジェクト初期化子とコレクション初期化子 (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 628f08aaebfa209fc9cb7cfb2b506fc67d5424f9
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="object-and-collection-initializers-c-programming-guide"></a><span data-ttu-id="5b736-102">オブジェクト初期化子とコレクション初期化子 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="5b736-102">Object and Collection Initializers (C# Programming Guide)</span></span>
<span data-ttu-id="5b736-103">オブジェクト初期化子を使用すると、オブジェクトの作成時にアクセスできるフィールドまたはプロパティに、コンストラクターを呼び出して代入ステートメントを使用しなくても、値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="5b736-103">Object initializers let you assign values to any accessible fields or properties of an object at creation time without having to invoke a constructor followed by lines of assignment statements.</span></span> <span data-ttu-id="5b736-104">オブジェクト初期化子の構文では、コンストラクターの引数を指定することも、引数 (およびかっこ構文) を省略することもできます。</span><span class="sxs-lookup"><span data-stu-id="5b736-104">The object initializer syntax enables you to specify arguments for a constructor or omit the arguments (and parentheses syntax).</span></span>  <span data-ttu-id="5b736-105">以下の例では、名前付きの型である `Cat` でオブジェクト初期化子を使用する方法と、既定のコンストラクターを呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5b736-105">The following example shows how to use an object initializer with a named type, `Cat` and how to invoke the default constructor.</span></span> <span data-ttu-id="5b736-106">`Cat` クラス内で自動実装プロパティが使用されています。</span><span class="sxs-lookup"><span data-stu-id="5b736-106">Note the use of auto-implemented properties in the `Cat` class.</span></span> <span data-ttu-id="5b736-107">詳細については、「[自動実装プロパティ](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b736-107">For more information, see [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>  
  
 [!code-csharp[csProgGuideLINQ#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_1.cs)]  
  
 [!code-csharp[csProgGuideLINQ#45](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_2.cs)] 
 
<span data-ttu-id="5b736-108">オブジェクト初期化子の構文では、インスタンスを作成できます。その後、新規作成されたオブジェクトは、割り当てられたプロパティと共に、割り当ての変数に代入されます。</span><span class="sxs-lookup"><span data-stu-id="5b736-108">The object initializers syntax allows you to create an instance, and after that it assigns the newly created object, with its assigned properties, to the variable in the assignment.</span></span>
  
## <a name="object-initializers-with-anonymous-types"></a><span data-ttu-id="5b736-109">オブジェクト初期化子と匿名型</span><span class="sxs-lookup"><span data-stu-id="5b736-109">Object Initializers with anonymous types</span></span>  
 <span data-ttu-id="5b736-110">オブジェクト初期化子は、どのような場合にも使うことができますが、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリ式で使うと特に有用です。</span><span class="sxs-lookup"><span data-stu-id="5b736-110">Although object initializers can be used in any context, they are especially useful in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="5b736-111">クエリ式では、次の宣言に示すように、オブジェクト初期化子を使うことによってのみ初期化できる[匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)が頻繁に使われます。</span><span class="sxs-lookup"><span data-stu-id="5b736-111">Query expressions make frequent use of [anonymous types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), which can only be initialized by using an object initializer, as shown in the following declaration.</span></span>  
  
```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```  
  
 <span data-ttu-id="5b736-112">匿名型を使うと、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリ式の `select` 句によって元のシーケンスのオブジェクトを値と形状が元とは異なるオブジェクトに変換できます。</span><span class="sxs-lookup"><span data-stu-id="5b736-112">Anonymous types enable the `select` clause in a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression to transform objects of the original sequence into objects whose value and shape may differ from the original.</span></span> <span data-ttu-id="5b736-113">この方法は、シーケンス内の各オブジェクトの情報の一部のみを保存する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="5b736-113">This is useful if you want to store only a part of the information from each object in a sequence.</span></span> <span data-ttu-id="5b736-114">次の例は、製品オブジェクト (`p`) に多くのフィールドおよびメソッドが含まれており、製品名および単価を含むオブジェクトのシーケンスを作成することにのみ関心があることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="5b736-114">In the following example, assume that a product object (`p`) contains many fields and methods, and that you are only interested in creating a sequence of objects that contain the product name and the unit price.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_3.cs)]  
  
 <span data-ttu-id="5b736-115">このクエリが実行されると、`productInfos` 変数には、次の例に示す `foreach` ステートメントでアクセスできるオブジェクトのシーケンスが格納されます。</span><span class="sxs-lookup"><span data-stu-id="5b736-115">When this query is executed, the `productInfos` variable will contain a sequence of objects that can be accessed in a `foreach` statement as shown in this example:</span></span>  
  
```csharp
foreach(var p in productInfos){...}  
```  
  
 <span data-ttu-id="5b736-116">作成される匿名型内の各オブジェクトには、2 つのパブリック プロパティがあります。これらのプロパティには、元のオブジェクトのプロパティまたはフィールドと同じ名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="5b736-116">Each object in the new anonymous type has two public properties which receive the same names as the properties or fields in the original object.</span></span> <span data-ttu-id="5b736-117">匿名型を作成するときにフィールドの名前を変更することもできます。次の例では、フィールド `UnitPrice` の名前が `Price` に変更されます。</span><span class="sxs-lookup"><span data-stu-id="5b736-117">You can also rename a field when you are creating an anonymous type; the following example renames the `UnitPrice` field to `Price`.</span></span>  
  
```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```  
  
## <a name="object-initializers-with-nullable-types"></a><span data-ttu-id="5b736-118">オブジェクト初期化子と Null 許容型</span><span class="sxs-lookup"><span data-stu-id="5b736-118">Object initializers with nullable types</span></span>  
 <span data-ttu-id="5b736-119">オブジェクト初期化子を null 許容構造体と共に使用すると、コンパイル時にエラーになります。</span><span class="sxs-lookup"><span data-stu-id="5b736-119">It is a compile-time error to use an object initializer with a nullable struct.</span></span>  
  
## <a name="collection-initializers"></a><span data-ttu-id="5b736-120">コレクション初期化子</span><span class="sxs-lookup"><span data-stu-id="5b736-120">Collection initializers</span></span>  
 <span data-ttu-id="5b736-121">コレクション初期化子を使うと、<xref:System.Collections.IEnumerable> を実装するコレクション型を初期化するときに 1 つ以上の要素の初期化子を指定でき、適切なシグネチャの `Add` をインスタンス メソッドまたは拡張メソッドとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="5b736-121">Collection initializers let you specify one or more element initializers when you initialize a collection type that implements <xref:System.Collections.IEnumerable> and has `Add` with the appropriate signature as an instance method or an extension method.</span></span> <span data-ttu-id="5b736-122">要素の初期化子は、単純な値、式またはオブジェクト初期化子です。</span><span class="sxs-lookup"><span data-stu-id="5b736-122">The element initializers can be a simple value, an expression or an object initializer.</span></span> <span data-ttu-id="5b736-123">コレクション初期化子を使用すると、ソース コード内でクラスの `Add` メソッドの呼び出しを複数回指定する必要がなくなります。コンパイラによって呼び出しが追加されるためです。</span><span class="sxs-lookup"><span data-stu-id="5b736-123">By using a collection initializer you do not have to specify multiple calls to the `Add` method of the class in your source code; the compiler adds the calls.</span></span>  
  
 <span data-ttu-id="5b736-124">2 つの単純なコレクション初期化子を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="5b736-124">The following examples shows two simple collection initializers:</span></span>  
  
```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```  
  
 <span data-ttu-id="5b736-125">次のコレクション初期化子は、前の例で定義されている `Cat` クラスのオブジェクトをオブジェクト初期化子を使用して初期化します。</span><span class="sxs-lookup"><span data-stu-id="5b736-125">The following collection initializer uses object initializers to initialize objects of the `Cat` class defined in a previous example.</span></span> <span data-ttu-id="5b736-126">個々のオブジェクト初期化子は、かっこで囲まれ、コンマで区切られています。</span><span class="sxs-lookup"><span data-stu-id="5b736-126">Note that the individual object initializers are enclosed in braces and separated by commas.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_4.cs)]  
  
 <span data-ttu-id="5b736-127">コレクションの `Add` メソッドで許容されている場合、コレクション初期化子の要素として [null](../../../csharp/language-reference/keywords/null.md) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5b736-127">You can specify [null](../../../csharp/language-reference/keywords/null.md) as an element in a collection initializer if the collection's `Add` method allows it.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_5.cs)]  
  
 <span data-ttu-id="5b736-128">コレクションがインデックス作成をサポートしている場合は、インデックス付きの要素を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="5b736-128">You can specify indexed elements if the collection supports indexing.</span></span>  
  
```csharp
var numbers = new Dictionary<int, string> {   
    [7] = "seven",   
    [9] = "nine",   
    [13] = "thirteen"   
};  
```  
  
## <a name="examples"></a><span data-ttu-id="5b736-129">使用例</span><span class="sxs-lookup"><span data-stu-id="5b736-129">Examples</span></span>

 <span data-ttu-id="5b736-130">次の例では、オブジェクトの概念とコレクション初期化子の概念が組み合わさっています。</span><span class="sxs-lookup"><span data-stu-id="5b736-130">The following example combines the concepts of object and collection initializers.</span></span>

 [!code-csharp[csProgGuideLINQ#46](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_6.cs)]  
 
 <span data-ttu-id="5b736-131">次の例では、複数のパラメーターを持つ `Add` メソッドが含まれる <xref:System.Collections.IEnumerable> を実装するオブジェクトが、`Add` メソッドのシグネチャに対応するリストの項目ごとの複数の要素を持つコレクション初期化子を可能にしています。</span><span class="sxs-lookup"><span data-stu-id="5b736-131">Shown in the following example, an object which implements <xref:System.Collections.IEnumerable> containing an `Add` method with multiple parameters allows for collection initializers with multiple elements per item in the list corresponding to the signature of the `Add` method.</span></span> 
 
 [!code-csharp[csProgGuideLINQ#84](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_7.cs)]
 
 <span data-ttu-id="5b736-132">`Add` メソッドでは、次の例で示すように、`params` キーワードを使用して可変数個の引数を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="5b736-132">`Add` methods can use the `params` keyword to take a variable number of arguments as shown in the following example.</span></span> <span data-ttu-id="5b736-133">この例では、インデクサーのカスタム実装と、インデクサーを使用したコレクションの初期化を示しています。</span><span class="sxs-lookup"><span data-stu-id="5b736-133">This example demonstrates the custom implementation of an indexer as well to initialize a collection using indexes.</span></span>
 
 [!code-csharp[csProgGuideLINQ#85](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_8.cs)]
 
## <a name="see-also"></a><span data-ttu-id="5b736-134">参照</span><span class="sxs-lookup"><span data-stu-id="5b736-134">See Also</span></span>  
 [<span data-ttu-id="5b736-135">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="5b736-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5b736-136">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="5b736-136">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="5b736-137">匿名型</span><span class="sxs-lookup"><span data-stu-id="5b736-137">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
