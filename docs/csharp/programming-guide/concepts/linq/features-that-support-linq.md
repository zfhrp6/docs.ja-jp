---
title: "LINQ をサポートする C# の機能"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2f5accb188e54e0d3e2b941832637ec33afc26b2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="c-features-that-support-linq"></a><span data-ttu-id="0b28b-102">LINQ をサポートする C# の機能</span><span class="sxs-lookup"><span data-stu-id="0b28b-102">C# Features That Support LINQ</span></span>
<span data-ttu-id="0b28b-103">このセクションでは、C# 3.0 で導入された新しい言語構成要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0b28b-103">The following section introduces new language constructs introduced in C# 3.0.</span></span> <span data-ttu-id="0b28b-104">これらの新機能はすべてある程度まで [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリで使用されていますが、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] だけでなく、これらの機能が役立つと思われるあらゆる状況で使用できます。</span><span class="sxs-lookup"><span data-stu-id="0b28b-104">Although these new features are all used to a degree with [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, they are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] and can be used in any context where you find them useful.</span></span>  
  
## <a name="query-expressions"></a><span data-ttu-id="0b28b-105">クエリ式</span><span class="sxs-lookup"><span data-stu-id="0b28b-105">Query Expressions</span></span>  
 <span data-ttu-id="0b28b-106">クエリ式は、SQL や XQuery に似た宣言型構文を使用して、IEnumerable コレクションを照会します。</span><span class="sxs-lookup"><span data-stu-id="0b28b-106">Queries expressions use a declarative syntax similar to SQL or XQuery to query over IEnumerable collections.</span></span> <span data-ttu-id="0b28b-107">クエリ構文は、コンパイル時に、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] プロバイダーの標準クエリ演算子拡張メソッドの実装に対するメソッド呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="0b28b-107">At compile time query syntax is converted to method calls to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="0b28b-108">アプリケーションは、`using` ディレクティブを使用して適切な名前空間を指定することにより、スコープ内の標準クエリ演算子を制御します。</span><span class="sxs-lookup"><span data-stu-id="0b28b-108">Applications control the standard query operators that are in scope by specifying the appropriate namespace with a `using` directive.</span></span> <span data-ttu-id="0b28b-109">次のクエリ式では、文字列の配列を受け取り、文字列の最初の文字を基に文字列をグループ化し、グループを並び替えています。</span><span class="sxs-lookup"><span data-stu-id="0b28b-109">The following query expression takes an array of strings, groups them according to the first character in the string, and orders the groups.</span></span>  
  
```  
var query = from str in stringArray  
            group str by str[0] into stringGroup  
            orderby stringGroup.Key  
            select stringGroup;  
```  
  
 <span data-ttu-id="0b28b-110">詳細については、「[LINQ クエリ式](../../../../csharp/programming-guide/linq-query-expressions/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0b28b-110">For more information, see [LINQ Query Expressions](../../../../csharp/programming-guide/linq-query-expressions/index.md).</span></span>  
  
## <a name="implicitly-typed-variables-var"></a><span data-ttu-id="0b28b-111">暗黙的に型指定された変数 (var)</span><span class="sxs-lookup"><span data-stu-id="0b28b-111">Implicitly Typed Variables (var)</span></span>  
 <span data-ttu-id="0b28b-112">変数を宣言して初期化するときに、型を明示的に指定する代わりに、次に示すように [var](../../../../csharp/language-reference/keywords/var.md) 修飾子を使用すると、コンパイラが型を推論して代入するように指示できます。</span><span class="sxs-lookup"><span data-stu-id="0b28b-112">Instead of explicitly specifying a type when you declare and initialize a variable, you can use the [var](../../../../csharp/language-reference/keywords/var.md) modifier to instruct the compiler to infer and assign the type, as shown here:</span></span>  
  
```  
var number = 5;  
var name = "Virginia";  
var query = from str in stringArray  
            where str[0] == 'm'  
            select str;  
```  
  
 <span data-ttu-id="0b28b-113">`var` として宣言された変数は、明示的に型を指定した変数とまったく同じように厳密に型指定されます。</span><span class="sxs-lookup"><span data-stu-id="0b28b-113">Variables declared as `var` are just as strongly-typed as variables whose type you specify explicitly.</span></span> <span data-ttu-id="0b28b-114">`var` を使用すると匿名型を作成できますが、任意のローカル変数にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="0b28b-114">The use of `var` makes it possible to create anonymous types, but it can be used for any local variable.</span></span> <span data-ttu-id="0b28b-115">また、暗黙的な型指定を使用して、配列を宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="0b28b-115">Arrays can also be declared with implicit typing.</span></span>  
  
 <span data-ttu-id="0b28b-116">詳細については、「[暗黙的に型指定されたローカル変数](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0b28b-116">For more information, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
## <a name="object-and-collection-initializers"></a><span data-ttu-id="0b28b-117">オブジェクト初期化子とコレクション初期化子</span><span class="sxs-lookup"><span data-stu-id="0b28b-117">Object and Collection Initializers</span></span>  
 <span data-ttu-id="0b28b-118">オブジェクト初期化子とコレクション初期化子を使用すると、オブジェクトのコンストラクターを明示的に呼び出さなくても、オブジェクトを初期化できます。</span><span class="sxs-lookup"><span data-stu-id="0b28b-118">Object and collection initializers make it possible to initialize objects without explicitly calling a constructor for the object.</span></span> <span data-ttu-id="0b28b-119">通常、初期化子は、ソース データを新しいデータ型に投影するクエリ式で使用されます。</span><span class="sxs-lookup"><span data-stu-id="0b28b-119">Initializers are typically used in query expressions when they project the source data into a new data type.</span></span> <span data-ttu-id="0b28b-120">パブリックな `Name` プロパティと `Phone` プロパティを持つ `Customer` という名前のクラスがある場合、オブジェクト初期化子は次のコードのように使用できます。</span><span class="sxs-lookup"><span data-stu-id="0b28b-120">Assuming a class named `Customer` with public `Name` and `Phone` properties, the object initializer can be used as in the following code:</span></span>  
  
```  
Customer cust = new Customer { Name = "Mike", Phone = "555-1212" };  
```  
  
 <span data-ttu-id="0b28b-121">詳細については、「[オブジェクト初期化子とコレクション初期化子](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0b28b-121">For more information, see [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
## <a name="anonymous-types"></a><span data-ttu-id="0b28b-122">匿名型</span><span class="sxs-lookup"><span data-stu-id="0b28b-122">Anonymous Types</span></span>  
 <span data-ttu-id="0b28b-123">匿名型はコンパイラによって作成され、型名はコンパイラにしかわかりません。</span><span class="sxs-lookup"><span data-stu-id="0b28b-123">An anonymous type is constructed by the compiler and the type name is only available to the compiler.</span></span> <span data-ttu-id="0b28b-124">匿名型を使用すると、個別に名前付き型を定義しなくても、クエリ結果内のプロパティのセットを一時的にグループ化できるため便利です。</span><span class="sxs-lookup"><span data-stu-id="0b28b-124">Anonymous types provide a convenient way to group a set of properties temporarily in a query result without having to define a separate named type.</span></span> <span data-ttu-id="0b28b-125">次に示すように、匿名型は new 式とオブジェクト初期化子を使用して初期化されます。</span><span class="sxs-lookup"><span data-stu-id="0b28b-125">Anonymous types are initialized with a new expression and an object initializer, as shown here:</span></span>  
  
```  
select new {name = cust.Name, phone = cust.Phone};  
```  
  
 <span data-ttu-id="0b28b-126">詳細については、「[匿名型](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0b28b-126">For more information, see [Anonymous Types](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="extension-methods"></a><span data-ttu-id="0b28b-127">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="0b28b-127">Extension Methods</span></span>  
 <span data-ttu-id="0b28b-128">拡張メソッドは型に関連付けることができる静的メソッドであるため、その型のインスタンス メソッドと同じように呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="0b28b-128">An extension method is a static method that can be associated with a type, so that it can be called as if it were an instance method on the type.</span></span> <span data-ttu-id="0b28b-129">この機能を使用すると、既存の型を実際に変更しなくても、その型に新しいメソッドを実質的に "追加" できます。</span><span class="sxs-lookup"><span data-stu-id="0b28b-129">This feature enables you to, in effect, "add" new methods to existing types without actually modifying them.</span></span> <span data-ttu-id="0b28b-130">標準クエリ演算子は、<xref:System.Collections.Generic.IEnumerable%601> を実装する任意の型で [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリ機能を実現する拡張メソッドのセットです。</span><span class="sxs-lookup"><span data-stu-id="0b28b-130">The standard query operators are a set of extension methods that provide [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="0b28b-131">詳細については、「[拡張メソッド](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0b28b-131">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
## <a name="lambda-expressions"></a><span data-ttu-id="0b28b-132">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="0b28b-132">Lambda Expressions</span></span>  
 <span data-ttu-id="0b28b-133">ラムダ式は、=> 演算子を使用して関数本体からパラメーター入力を分離するインライン関数で、コンパイル時にデリゲートまたは式ツリーに変換されます。</span><span class="sxs-lookup"><span data-stu-id="0b28b-133">A lambda expression is an inline function that uses the => operator to separate input parameters from the function body and can be converted at compile time to a delegate or an expression tree.</span></span> <span data-ttu-id="0b28b-134">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] プログラミングでは、標準クエリ演算子に対する直接メソッド呼び出しを行う場合にラムダ式を使用します。</span><span class="sxs-lookup"><span data-stu-id="0b28b-134">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programming, you will encounter lambda expressions when you make direct method calls to the standard query operators.</span></span>  
  
 <span data-ttu-id="0b28b-135">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="0b28b-135">For more information, see:</span></span>  
  
-   [<span data-ttu-id="0b28b-136">匿名関数</span><span class="sxs-lookup"><span data-stu-id="0b28b-136">Anonymous Functions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [<span data-ttu-id="0b28b-137">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="0b28b-137">Lambda Expressions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
-   [<span data-ttu-id="0b28b-138">式ツリー (C#)</span><span class="sxs-lookup"><span data-stu-id="0b28b-138">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
  
## <a name="auto-implemented-properties"></a><span data-ttu-id="0b28b-139">自動実装プロパティ</span><span class="sxs-lookup"><span data-stu-id="0b28b-139">Auto-Implemented Properties</span></span>  
 <span data-ttu-id="0b28b-140">自動実装プロパティによって、プロパティの宣言が簡略化されます。</span><span class="sxs-lookup"><span data-stu-id="0b28b-140">Auto-implemented properties make property-declaration more concise.</span></span> <span data-ttu-id="0b28b-141">次の例に示すようなプロパティを宣言すると、コンパイラによってプライベートの匿名バッキング フィールドが作成されます。このフィールドには、プロパティ getter およびプロパティ setter でしかアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="0b28b-141">When you declare a property as shown in the following example, the compiler will create a private, anonymous backing field that is not accessible except through the property getter and setter.</span></span>  
  
```  
public string Name {get; set;}  
```  
  
 <span data-ttu-id="0b28b-142">詳細については、「[自動実装プロパティ](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0b28b-142">For more information, see [Auto-Implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b28b-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b28b-143">See Also</span></span>  
 [<span data-ttu-id="0b28b-144">統合言語クエリ (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="0b28b-144">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
