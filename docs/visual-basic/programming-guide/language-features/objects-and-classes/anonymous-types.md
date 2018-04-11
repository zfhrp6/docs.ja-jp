---
title: 匿名型 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AnonymousType
helpviewer_keywords:
- anonymous types [Visual Basic], about anonymous types
- anonymous types [Visual Basic]
- types [Visual Basic], anonymous
ms.assetid: 7b87532c-4b3e-4398-8503-6ea9d67574a4
caps.latest.revision: 46
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 530e21e1595f9bbc3436280418287413e2a48111
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-types-visual-basic"></a><span data-ttu-id="6fe4c-102">匿名型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fe4c-102">Anonymous Types (Visual Basic)</span></span>
<span data-ttu-id="6fe4c-103">Visual Basic では、匿名型は、使用すると、データ型のクラス定義を記述することがなくオブジェクトの作成をサポートします。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-103">Visual Basic supports anonymous types, which enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="6fe4c-104">クラスは、コンパイラによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-104">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="6fe4c-105">クラスの使用可能な名前を持たないから直接継承<xref:System.Object>オブジェクトの宣言で指定したプロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-105">The class has no usable name, inherits directly from <xref:System.Object>, and contains the properties you specify in declaring the object.</span></span> <span data-ttu-id="6fe4c-106">データ型の名前が指定されていないため、呼びます、*匿名型*です。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-106">Because the name of the data type is not specified, it is referred to as an *anonymous type*.</span></span>  
  
 <span data-ttu-id="6fe4c-107">次の例を宣言し、変数を作成`product`を 2 つのプロパティを持つ匿名型のインスタンスとして`Name`と`Price`です。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-107">The following example declares and creates variable `product` as an instance of an anonymous type that has two properties, `Name` and `Price`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#1](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_1.vb)]  
  
 <span data-ttu-id="6fe4c-108">A*クエリ式*匿名型を使用して、クエリによって選択されたデータの列を結合します。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-108">A *query expression* uses anonymous types to combine columns of data selected by a query.</span></span> <span data-ttu-id="6fe4c-109">特定のクエリで選択される列を予測できないために、結果の型を事前に定義できません。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-109">You cannot define the type of the result in advance, because you cannot predict the columns a particular query might select.</span></span> <span data-ttu-id="6fe4c-110">匿名型を使用すると、任意の順序で、列の任意の数を選択するクエリを記述できます。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-110">Anonymous types enable you to write a query that selects any number of columns, in any order.</span></span> <span data-ttu-id="6fe4c-111">コンパイラでは、指定されたプロパティおよび指定した順序と一致するデータ型を作成します。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-111">The compiler creates a data type that matches the specified properties and the specified order.</span></span>  
  
 <span data-ttu-id="6fe4c-112">次の例についてで`products`それぞれが多数のプロパティを持つ製品オブジェクトの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-112">In the following examples, `products` is a list of product objects, each of which has many properties.</span></span> <span data-ttu-id="6fe4c-113">変数`namePriceQuery`が実行されるときに、2 つのプロパティを持つ匿名型のインスタンスのコレクションを返すクエリの定義を保持`Name`と`Price`です。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-113">Variable `namePriceQuery` holds the definition of a query that, when it is executed, returns a collection of instances of an anonymous type that has two properties, `Name` and `Price`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#2](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_2.vb)]  
  
 <span data-ttu-id="6fe4c-114">変数`nameQuantityQuery`が実行されるときに、2 つのプロパティを持つ匿名型のインスタンスのコレクションを返すクエリの定義を保持`Name`と`OnHand`です。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-114">Variable `nameQuantityQuery` holds the definition of a query that, when it is executed, returns a collection of instances of an anonymous type that has two properties, `Name` and `OnHand`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#3](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_3.vb)]  
  
 <span data-ttu-id="6fe4c-115">匿名型のためにコンパイラによって作成されたコードの詳細については、次を参照してください。[匿名の型定義](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)です。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-115">For more information about the code created by the compiler for an anonymous type, see [Anonymous Type Definition](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="6fe4c-116">匿名型の名前は、コンパイラが生成され、コンパイルするたびに異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-116">The name of the anonymous type is compiler generated and may vary from compilation to compilation.</span></span> <span data-ttu-id="6fe4c-117">コード必要がありますいないを使用してに依存したり、匿名型の名前のプロジェクトが再コンパイルするとき、名前が変わる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-117">Your code should not use or rely on the name of an anonymous type because the name might change when a project is recompiled.</span></span>  
  
## <a name="declaring-an-anonymous-type"></a><span data-ttu-id="6fe4c-118">匿名型の宣言</span><span class="sxs-lookup"><span data-stu-id="6fe4c-118">Declaring an Anonymous Type</span></span>  
 <span data-ttu-id="6fe4c-119">匿名型のインスタンスの宣言は、型のプロパティを指定するのに、初期化子リストを使用します。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-119">The declaration of an instance of an anonymous type uses an initializer list to specify the properties of the type.</span></span> <span data-ttu-id="6fe4c-120">匿名型、いないその他のクラスなどの要素メソッドまたはイベントを宣言する場合は、プロパティのみを指定できます。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-120">You can specify only properties when you declare an anonymous type, not other class elements such as methods or events.</span></span> <span data-ttu-id="6fe4c-121">次の例では、`product1`を 2 つのプロパティを持つ匿名型のインスタンス:`Name`と`Price`です。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-121">In the following example, `product1` is an instance of an anonymous type that has two properties: `Name` and `Price`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#4](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_4.vb)]  
  
 <span data-ttu-id="6fe4c-122">プロパティをキー プロパティとして指定する場合は、2 つの匿名型のインスタンスの等価性を比較に使用できます。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-122">If you designate properties as key properties, you can use them to compare two anonymous type instances for equality.</span></span> <span data-ttu-id="6fe4c-123">ただし、キー プロパティの値を変更できません。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-123">However, the values of key properties cannot be changed.</span></span> <span data-ttu-id="6fe4c-124">詳細については、このトピックの後半のキーのプロパティ セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-124">See the Key Properties section later in this topic for more information.</span></span>  
  
 <span data-ttu-id="6fe4c-125">オブジェクト初期化子を使用して名前付きの型のインスタンスを宣言するようが匿名型のインスタンスを宣言することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-125">Notice that declaring an instance of an anonymous type is like declaring an instance of a named type by using an object initializer:</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#5](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_5.vb)]  
  
 <span data-ttu-id="6fe4c-126">匿名型プロパティを指定するには、その他の方法の詳細については、次を参照してください。[する方法: 匿名型の宣言におけるプロパティ名の推論と型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)です。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-126">For more information about other ways to specify anonymous type properties, see [How to: Infer Property Names and Types in Anonymous Type Declarations](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="6fe4c-127">キー プロパティ</span><span class="sxs-lookup"><span data-stu-id="6fe4c-127">Key Properties</span></span>  
 <span data-ttu-id="6fe4c-128">キー プロパティは、いくつかの基本的な方法でキー以外のプロパティと異なります。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-128">Key properties differ from non-key properties in several fundamental ways:</span></span>  
  
-   <span data-ttu-id="6fe4c-129">2 つのインスタンスが等しいかどうかを判断するためには、キー プロパティの値のみが比較されます。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-129">Only the values of key properties are compared in order to determine whether two instances are equal.</span></span>  
  
-   <span data-ttu-id="6fe4c-130">キー プロパティの値は、読み取り専用し、変更できません。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-130">The values of key properties are read-only and cannot be changed.</span></span>  
  
-   <span data-ttu-id="6fe4c-131">のみ、コンパイラによって生成されたコードに対してハッシュ アルゴリズム、匿名型のキー プロパティの値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-131">Only key property values are included in the compiler-generated hash code algorithm for an anonymous type.</span></span>  
  
### <a name="equality"></a><span data-ttu-id="6fe4c-132">等価比較</span><span class="sxs-lookup"><span data-stu-id="6fe4c-132">Equality</span></span>  
 <span data-ttu-id="6fe4c-133">匿名型のインスタンスは、同じ匿名型のインスタンスの場合のみ等しいと指定できます。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-133">Instances of anonymous types can be equal only if they are instances of the same anonymous type.</span></span> <span data-ttu-id="6fe4c-134">コンパイラは、次の条件を満たしている場合、同じ型のインスタンスとして 2 つのインスタンスを処理します。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-134">The compiler treats two instances as instances of the same type if they meet the following conditions:</span></span>  
  
-   <span data-ttu-id="6fe4c-135">同じアセンブリ内で宣言されています。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-135">They are declared in the same assembly.</span></span>  
  
-   <span data-ttu-id="6fe4c-136">そのプロパティは、同じ名前では、同じ推定された型、および同じ順序で宣言されます。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-136">Their properties have the same names, the same inferred types, and are declared in the same order.</span></span> <span data-ttu-id="6fe4c-137">名前の比較は区別されません。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-137">Name comparisons are not case-sensitive.</span></span>  
  
-   <span data-ttu-id="6fe4c-138">それぞれの同じプロパティがキー プロパティとしてマークされます。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-138">The same properties in each are marked as key properties.</span></span>  
  
-   <span data-ttu-id="6fe4c-139">各宣言内の少なくとも 1 つのプロパティは、キー プロパティです。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-139">At least one property in each declaration is a key property.</span></span>  
  
 <span data-ttu-id="6fe4c-140">キー プロパティを持たない匿名型のインスタンスが自身に対してのみです。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-140">An instance of an anonymous types that has no key properties is equal only to itself.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#6](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_6.vb)]  
  
 <span data-ttu-id="6fe4c-141">同じ匿名型の 2 つのインスタンスは、主要なプロパティの値が等しい場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-141">Two instances of the same anonymous type are equal if the values of their key properties are equal.</span></span> <span data-ttu-id="6fe4c-142">次の例では、等しいかどうかをテストする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-142">The following examples illustrate how equality is tested.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#7](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_7.vb)]  
  
### <a name="read-only-values"></a><span data-ttu-id="6fe4c-143">読み取り専用の値</span><span class="sxs-lookup"><span data-stu-id="6fe4c-143">Read-Only Values</span></span>  
 <span data-ttu-id="6fe4c-144">キー プロパティの値を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-144">The values of key properties cannot be changed.</span></span> <span data-ttu-id="6fe4c-145">たとえば、`prod8`前の例で、`Name`と`Price`フィールドは`read-only`が`OnHand`変更できます。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-145">For example, in `prod8` in the previous example, the `Name` and `Price` fields are `read-only`, but `OnHand` can be changed.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#8](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_8.vb)]  
  
## <a name="anonymous-types-from-query-expressions"></a><span data-ttu-id="6fe4c-146">クエリ式からの匿名型</span><span class="sxs-lookup"><span data-stu-id="6fe4c-146">Anonymous Types from Query Expressions</span></span>  
 <span data-ttu-id="6fe4c-147">常に、クエリ式では、匿名型の作成を必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-147">Query expressions do not always require the creation of anonymous types.</span></span> <span data-ttu-id="6fe4c-148">可能な場合は、列のデータを保持するために既存の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-148">When possible, they use an existing type to hold the column data.</span></span> <span data-ttu-id="6fe4c-149">これは、クエリ、データ ソースまたは各レコードから 1 つだけのフィールドからレコード全体が返されるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-149">This occurs when the query returns either whole records from the data source, or only one field from each record.</span></span> <span data-ttu-id="6fe4c-150">次のコード例で`customers`のオブジェクトのコレクションには、`Customer`クラスです。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-150">In the following code examples, `customers` is a collection of objects of a `Customer` class.</span></span> <span data-ttu-id="6fe4c-151">クラスには、多数のプロパティと任意の順序で、クエリ結果のうちの 1 つ以上を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-151">The class has many properties, and you can include one or more of them in the query result, in any order.</span></span> <span data-ttu-id="6fe4c-152">最初の 2 つの例については、匿名型はありません必要なため、クエリは、名前付きの型の要素を選択です。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-152">In the first two examples, no anonymous types are required because the queries select elements of named types:</span></span>  
  
-   <span data-ttu-id="6fe4c-153">`custs1`に、文字列のコレクションを含む`cust.Name`文字列です。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-153">`custs1` contains a collection of strings, because `cust.Name` is a string.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#30](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_9.vb)]  
  
-   <span data-ttu-id="6fe4c-154">`custs2`コレクションを格納`Customer`ため、オブジェクトの各要素`customers`は、`Customer`オブジェクト、および全体の要素は、クエリで選択します。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-154">`custs2` contains a collection of `Customer` objects, because each element of `customers` is a `Customer` object, and the whole element is selected by the query.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#31](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_10.vb)]  
  
 <span data-ttu-id="6fe4c-155">ただし、適切な名前付きの型は常に使用できません。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-155">However, appropriate named types are not always available.</span></span> <span data-ttu-id="6fe4c-156">顧客名と 1 つの目的、顧客 ID 番号および別の場所のアドレスと顧客の名前、アドレス、および 3 つ目の注文履歴を選択する場合があります。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-156">You might want to select customer names and addresses for one purpose, customer ID numbers and locations for another, and customer names, addresses, and order histories for a third.</span></span> <span data-ttu-id="6fe4c-157">匿名型を使用すると、最初に結果を保持する新しい名前付きの型を宣言しなくても、任意の順序で、プロパティの任意の組み合わせを選択できます。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-157">Anonymous types enable you to select any combination of properties, in any order, without first declaring a new named type to hold the result.</span></span> <span data-ttu-id="6fe4c-158">代わりに、コンパイラは、プロパティのコンパイルごとの匿名型を作成します。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-158">Instead, the compiler creates an anonymous type for each compilation of properties.</span></span> <span data-ttu-id="6fe4c-159">次のクエリでは各からのみ、顧客の名前と ID 番号が選択`Customer`オブジェクトに`customers`です。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-159">The following query selects only the customer's name and ID number from each `Customer` object in `customers`.</span></span> <span data-ttu-id="6fe4c-160">そのため、コンパイラは、これら 2 つのプロパティのみを含んでいる匿名型を作成します。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-160">Therefore, the compiler creates an anonymous type that contains only those two properties.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTYpes#32](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_11.vb)]  
  
 <span data-ttu-id="6fe4c-161">名前と匿名型のプロパティのデータ型の両方が引数から取得した`Select`、`cust.Name`と`cust.ID`です。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-161">Both the names and the data types of the properties in the anonymous type are taken from the arguments to `Select`, `cust.Name` and `cust.ID`.</span></span> <span data-ttu-id="6fe4c-162">クエリによって作成される匿名型のプロパティは、常にキー プロパティです。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-162">The properties in an anonymous type that is created by a query are always key properties.</span></span> <span data-ttu-id="6fe4c-163">ときに`custs3`が、次に実行される`For Each`ループ、結果は、2 つのキー プロパティを持つ匿名型のインスタンスのコレクション`Name`と`ID`です。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-163">When `custs3` is executed in the following `For Each` loop, the result is a collection of instances of an anonymous type with two key properties, `Name` and `ID`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#33](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_12.vb)]  
  
 <span data-ttu-id="6fe4c-164">によって表されるコレクション内の要素`custs3`厳密に型指定し、使用可能なプロパティ内を移動し、それらの種類を確認するのには、IntelliSense を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-164">The elements in the collection represented by `custs3` are strongly typed, and you can use IntelliSense to navigate through the available properties and to verify their types.</span></span>  
  
 <span data-ttu-id="6fe4c-165">詳細については、次を参照してください。 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)です。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-165">For more information, see [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).</span></span>  
  
## <a name="deciding-whether-to-use-anonymous-types"></a><span data-ttu-id="6fe4c-166">匿名型を使用するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-166">Deciding Whether to Use Anonymous Types</span></span>  
 <span data-ttu-id="6fe4c-167">匿名クラスのインスタンスとしてオブジェクトを作成する前に、最適なオプションであるかどうかを検討してください。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-167">Before you create an object as an instance of an anonymous class, consider whether that is the best option.</span></span> <span data-ttu-id="6fe4c-168">たとえば、関連データを格納する一時オブジェクトを作成する、完全なクラスを含めることができるメソッドとフィールド、その他の必要があるない場合は、匿名型は良いソリューションです。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-168">For example, if you want to create a temporary object to contain related data, and you have no need for other fields and methods that a complete class might contain, an anonymous type is a good solution.</span></span> <span data-ttu-id="6fe4c-169">匿名型は、宣言ごとに異なるプロパティを選択をする場合、またはプロパティの順序を変更する場合にも便利です。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-169">Anonymous types are also convenient if you want a different selection of properties for each declaration, or if you want to change the order of the properties.</span></span> <span data-ttu-id="6fe4c-170">ただし、プロジェクトには、同じプロパティを持つ、一定の順序で複数のオブジェクトが含まれている場合でも宣言できますより簡単にクラス コンス トラクターを持つ名前付きの型を使用しています。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-170">However, if your project includes several objects that have the same properties, in a fixed order, you can declare them more easily by using a named type with a class constructor.</span></span> <span data-ttu-id="6fe4c-171">たとえば、適切なコンス トラクターがのいくつかのインスタンスを宣言しやすく、`Product`匿名型の複数のインスタンスを宣言するよりものクラスです。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-171">For example, with an appropriate constructor, it is easier to declare several instances of a `Product` class than it is to declare several instances of an anonymous type.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#9](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_13.vb)]  
  
 <span data-ttu-id="6fe4c-172">名前付きの型のもう 1 つの利点は、コンパイラがプロパティ名のタイプミスをキャッチできることです。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-172">Another advantage of named types is that the compiler can catch an accidental mistyping of a property name.</span></span> <span data-ttu-id="6fe4c-173">前の例で`firstProd2`、 `secondProd2`、および`thirdProd2`同じ匿名型のインスタンスにする対象としています。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-173">In the previous examples, `firstProd2`, `secondProd2`, and `thirdProd2` are intended to be instances of the same anonymous type.</span></span> <span data-ttu-id="6fe4c-174">ただし、する場合は誤って宣言`thirdProd2`、次の方法の 1 つは、その型とは異なるの`firstProd2`と`secondProd2`です。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-174">However, if you were to accidentally declare `thirdProd2` in one of the following ways, its type would be different from that of `firstProd2` and `secondProd2`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#10](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_14.vb)]  
  
 <span data-ttu-id="6fe4c-175">さらに、名前付きの型のインスタンスに適用されない匿名型の使用に関する制限事項があります。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-175">More importantly, there are limitations on the use of anonymous types that do not apply to instances of named types.</span></span> <span data-ttu-id="6fe4c-176">`firstProd2`、 `secondProd2`、および`thirdProd2`、同じ匿名型のインスタンスであります。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-176">`firstProd2`, `secondProd2`, and `thirdProd2` are instances of the same anonymous type.</span></span> <span data-ttu-id="6fe4c-177">ただし、共有の匿名型の名前を使用できないが、型名は、コードで、必要なことはできません。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-177">However, the name for the shared anonymous type is not available and cannot appear where a type name is expected in your code.</span></span> <span data-ttu-id="6fe4c-178">たとえば、匿名型を使用して、別の変数またはフィールド、または任意の型宣言で宣言するメソッドのシグネチャを定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-178">For example, an anonymous type cannot be used to define a method signature, to declare another variable or field, or in any type declaration.</span></span> <span data-ttu-id="6fe4c-179">その結果、メソッドの間で情報を共有する必要があるとき匿名型は適していません。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-179">As a result, anonymous types are not appropriate when you have to share information across methods.</span></span>  
  
## <a name="an-anonymous-type-definition"></a><span data-ttu-id="6fe4c-180">匿名型の定義</span><span class="sxs-lookup"><span data-stu-id="6fe4c-180">An Anonymous Type Definition</span></span>  
 <span data-ttu-id="6fe4c-181">匿名型のインスタンスの宣言に応答してでは、コンパイラは、指定したプロパティを格納する新しいクラス定義を作成します。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-181">In response to the declaration of an instance of an anonymous type, the compiler creates a new class definition that contains the specified properties.</span></span>  
  
 <span data-ttu-id="6fe4c-182">匿名型には、少なくとも 1 つのキー プロパティが含まれている場合、定義によって上書きから継承した 3 つのメンバー <xref:System.Object>: <xref:System.Object.Equals%2A>、 <xref:System.Object.GetHashCode%2A>、および<xref:System.Object.ToString%2A>です。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-182">If the anonymous type contains at least one key property, the definition overrides three members inherited from <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="6fe4c-183">等価性をテストし、ハッシュ コード値がキー プロパティだけを考慮を決定するために生成されるコード。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-183">The code produced for testing equality and determining the hash code value considers only the key properties.</span></span> <span data-ttu-id="6fe4c-184">匿名型が含まれていないキーのプロパティでのみ<xref:System.Object.ToString%2A>はオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-184">If the anonymous type contains no key properties, only <xref:System.Object.ToString%2A> is overridden.</span></span> <span data-ttu-id="6fe4c-185">匿名型のプロパティを明示的に指定されたこれらの生成されたメソッドと競合することはできません。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-185">Explicitly named properties of an anonymous type cannot conflict with these generated methods.</span></span> <span data-ttu-id="6fe4c-186">つまり、使用することはできません`.Equals`、 `.GetHashCode`、または`.ToString`プロパティの名前を付ける。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-186">That is, you cannot use `.Equals`, `.GetHashCode`, or `.ToString` to name a property.</span></span>  
  
 <span data-ttu-id="6fe4c-187">匿名型の定義には、少なくとも 1 つを持つキー プロパティも実装して、<xref:System.IEquatable%601?displayProperty=nameWithType>インターフェイス、場所`T`匿名型の型です。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-187">Anonymous type definitions that have at least one key property also implement the <xref:System.IEquatable%601?displayProperty=nameWithType> interface, where `T` is the type of the anonymous type.</span></span>  
  
 <span data-ttu-id="6fe4c-188">詳細について、コンパイラとのオーバーライドされたメソッドの機能で作成したコードは、次を参照してください。[匿名の型定義](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)です。</span><span class="sxs-lookup"><span data-stu-id="6fe4c-188">For more information about the code created by the compiler and the functionality of the overridden methods, see [Anonymous Type Definition](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fe4c-189">関連項目</span><span class="sxs-lookup"><span data-stu-id="6fe4c-189">See Also</span></span>  
 [<span data-ttu-id="6fe4c-190">オブジェクト初期化子 : 名前付きの型と匿名型</span><span class="sxs-lookup"><span data-stu-id="6fe4c-190">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="6fe4c-191">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="6fe4c-191">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="6fe4c-192">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="6fe4c-192">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="6fe4c-193">方法 : 匿名型の宣言におけるプロパティ名と型を推論する</span><span class="sxs-lookup"><span data-stu-id="6fe4c-193">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [<span data-ttu-id="6fe4c-194">匿名型の定義</span><span class="sxs-lookup"><span data-stu-id="6fe4c-194">Anonymous Type Definition</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)  
 [<span data-ttu-id="6fe4c-195">Key</span><span class="sxs-lookup"><span data-stu-id="6fe4c-195">Key</span></span>](../../../../visual-basic/language-reference/modifiers/key.md)
