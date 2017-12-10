---
title: "方法: 複数のデータ型に同一の機能を提供できるクラスを定義する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data type arguments [Visual Basic], using
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- data type parameters [Visual Basic], using
- generics [Visual Basic], defining classes with type parameters
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- type arguments
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
- parameters [Visual Basic], data type
- generics [Visual Basic], defining generic types
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: a914adf8-e68f-4819-a6b1-200d1cf1c21c
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c81d1f795b0c27f2eaf07832f2c1276b626f5ce1
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a><span data-ttu-id="d89ac-102">方法: 複数のデータ型に同一の機能を提供できるクラスを定義する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d89ac-102">How to: Define a Class That Can Provide Identical Functionality on Different Data Types (Visual Basic)</span></span>
<span data-ttu-id="d89ac-103">複数の異なるデータ型に同一の機能を提供するオブジェクトを作成するために使用できるクラスを定義できます。</span><span class="sxs-lookup"><span data-stu-id="d89ac-103">You can define a class from which you can create objects that provide identical functionality on different data types.</span></span> <span data-ttu-id="d89ac-104">これを行うには、1 つ以上の *型パラメーター* を定義内で指定します。</span><span class="sxs-lookup"><span data-stu-id="d89ac-104">To do this, you specify one or more *type parameters* in the definition.</span></span> <span data-ttu-id="d89ac-105">このようなクラスは、さまざまなデータ型を使用するオブジェクトのテンプレートとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="d89ac-105">The class can then serve as a template for objects that use various data types.</span></span> <span data-ttu-id="d89ac-106">この方法で定義したクラスは、 *ジェネリック クラス*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="d89ac-106">A class defined in this way is called a *generic class*.</span></span>  
  
 <span data-ttu-id="d89ac-107">ジェネリック クラスを定義する利点は、クラスを一度だけ定義すれば、コードの中でそれを使って、さまざまなデータ型を使用する多くのオブジェクトを作成できることです。</span><span class="sxs-lookup"><span data-stu-id="d89ac-107">The advantage of defining a generic class is that you define it just once, and your code can use it to create many objects that use a wide variety of data types.</span></span> <span data-ttu-id="d89ac-108">これにより、クラスを `Object` 型で定義した場合よりパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="d89ac-108">This results in better performance than defining the class with the `Object` type.</span></span>  
  
 <span data-ttu-id="d89ac-109">クラスに加えて、ジェネリックの構造体、インターフェイス、プロシージャ、デリゲートを定義して利用することもできます。</span><span class="sxs-lookup"><span data-stu-id="d89ac-109">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
### <a name="to-define-a-class-with-a-type-parameter"></a><span data-ttu-id="d89ac-110">型パラメーターを持つクラスを定義するには</span><span class="sxs-lookup"><span data-stu-id="d89ac-110">To define a class with a type parameter</span></span>  
  
1.  <span data-ttu-id="d89ac-111">通常の方法でクラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="d89ac-111">Define the class in the normal way.</span></span>  
  
2.  <span data-ttu-id="d89ac-112">クラス名の直後に `(Of` *typeparameter*`)` を追加し、型パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="d89ac-112">Add `(Of` *typeparameter*`)` immediately after the class name to specify a type parameter.</span></span>  
  
3.  <span data-ttu-id="d89ac-113">複数の型パラメーターがある場合は、かっこ内にコンマ区切りのリストを指定します。</span><span class="sxs-lookup"><span data-stu-id="d89ac-113">If you have more than one type parameter, make a comma-separated list inside the parentheses.</span></span> <span data-ttu-id="d89ac-114">`Of` キーワードは繰り返さないでください。</span><span class="sxs-lookup"><span data-stu-id="d89ac-114">Do not repeat the `Of` keyword.</span></span>  
  
4.  <span data-ttu-id="d89ac-115">型パラメーターに対して単純な代入以外の操作を実行する場合は、その型パラメーターの後に `As` 句を付けて 1 つ以上の *制約*を追加します。</span><span class="sxs-lookup"><span data-stu-id="d89ac-115">If your code performs operations on a type parameter other than simple assignment, follow that type parameter with an `As` clause to add one or more *constraints*.</span></span> <span data-ttu-id="d89ac-116">制約は、その型パラメーターに渡される型が、たとえば以下のような要件を満たすことを保証します。</span><span class="sxs-lookup"><span data-stu-id="d89ac-116">A constraint guarantees that the type supplied for that type parameter satisfies a requirement such as the following:</span></span>  
  
    -   <span data-ttu-id="d89ac-117">コードで実行する `>`などの演算をサポートする</span><span class="sxs-lookup"><span data-stu-id="d89ac-117">Supports an operation, such as `>`, that your code performs</span></span>  
  
    -   <span data-ttu-id="d89ac-118">コードでアクセスするメソッドなどのメンバーをサポートする</span><span class="sxs-lookup"><span data-stu-id="d89ac-118">Supports a member, such as a method, that your code accesses</span></span>  
  
    -   <span data-ttu-id="d89ac-119">パラメーターなしのコンストラクターを公開する</span><span class="sxs-lookup"><span data-stu-id="d89ac-119">Exposes a parameterless constructor</span></span>  
  
     <span data-ttu-id="d89ac-120">制約を指定しない場合、コードで使用できる演算とメンバーは、 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)でサポートされるものだけになります。</span><span class="sxs-lookup"><span data-stu-id="d89ac-120">If you do not specify any constraints, the only operations and members your code can use are those supported by the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="d89ac-121">詳細については、「 [Type List](../../../../visual-basic/language-reference/statements/type-list.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d89ac-121">For more information, see [Type List](../../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
5.  <span data-ttu-id="d89ac-122">渡された型を使って宣言する必要のある各クラス メンバーを識別し、それを `As` `typeparameter`として宣言します。</span><span class="sxs-lookup"><span data-stu-id="d89ac-122">Identify every class member that is to be declared with a supplied type, and declare it `As` `typeparameter`.</span></span> <span data-ttu-id="d89ac-123">これは、内部ストレージ、プロシージャのパラメーター、戻り値に適用されます。</span><span class="sxs-lookup"><span data-stu-id="d89ac-123">This applies to internal storage, procedure parameters, and return values.</span></span>  
  
6.  <span data-ttu-id="d89ac-124">コードでは、 `itemType`に渡される可能性があるすべてのデータ型でサポートされる演算とメソッドだけを使用します。</span><span class="sxs-lookup"><span data-stu-id="d89ac-124">Be sure your code uses only operations and methods that are supported by any data type it can supply to `itemType`.</span></span>  
  
     <span data-ttu-id="d89ac-125">次のコード例は、ごく単純なリストを管理するクラスを定義しています。</span><span class="sxs-lookup"><span data-stu-id="d89ac-125">The following example defines a class that manages a very simple list.</span></span> <span data-ttu-id="d89ac-126">このクラスは、リストを内部配列 `items`に格納します。このクラスを使用するコードでは、このリストの要素のデータ型を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="d89ac-126">It holds the list in the internal array `items`, and the using code can declare the data type of the list elements.</span></span> <span data-ttu-id="d89ac-127">パラメーター化されたコンストラクターを使うと、コードで `items`の上限を設定できます。既定のコンストラクターでは、この上限は 9 (合計で 10 アイテム) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="d89ac-127">A parameterized constructor allows the using code to set the upper bound of `items`, and the default constructor sets this to 9 (for a total of 10 items).</span></span>  
  
     [!code-vb[VbVbalrDataTypes#7](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_1.vb)]  
  
     <span data-ttu-id="d89ac-128">`simpleList` からは、 `Integer` 値のリストを格納するクラス、 `String` 値のリストを格納するクラス、 `Date` 値のリストを格納するクラスなどを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="d89ac-128">You can declare a class from `simpleList` to hold a list of `Integer` values, another class to hold a list of `String` values, and another to hold `Date` values.</span></span> <span data-ttu-id="d89ac-129">リスト メンバーのデータ型が異なるだけで、これらすべてのクラスから作成されるオブジェクトの動作はまったく同じです。</span><span class="sxs-lookup"><span data-stu-id="d89ac-129">Except for the data type of the list members, objects created from all these classes behave identically.</span></span>  
  
     <span data-ttu-id="d89ac-130">使用するコードから `itemType` に渡す型引数としては、 `Boolean` や `Double`などの組み込みの型、構造体、列挙、任意の型のクラス (アプリケーションで独自に定義したクラスを含む) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d89ac-130">The type argument that the using code supplies to `itemType` can be an intrinsic type such as `Boolean` or `Double`, a structure, an enumeration, or any type of class, including one that your application defines.</span></span>  
  
     <span data-ttu-id="d89ac-131">`simpleList` クラスをテストするには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="d89ac-131">You can test the class `simpleList` with the following code.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#8](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d89ac-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="d89ac-132">See Also</span></span>  
 [<span data-ttu-id="d89ac-133">データの種類</span><span class="sxs-lookup"><span data-stu-id="d89ac-133">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="d89ac-134">Visual Basic におけるジェネリック型</span><span class="sxs-lookup"><span data-stu-id="d89ac-134">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="d89ac-135">言語への非依存性、および言語非依存コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d89ac-135">Language Independence and Language-Independent Components</span></span>](../../../../../docs/standard/language-independence-and-language-independent-components.md)  
 [<span data-ttu-id="d89ac-136">Of</span><span class="sxs-lookup"><span data-stu-id="d89ac-136">Of</span></span>](../../../../visual-basic/language-reference/statements/of-clause.md)  
 [<span data-ttu-id="d89ac-137">型リスト</span><span class="sxs-lookup"><span data-stu-id="d89ac-137">Type List</span></span>](../../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="d89ac-138">方法 : ジェネリック クラスを使用する</span><span class="sxs-lookup"><span data-stu-id="d89ac-138">How to: Use a Generic Class</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="d89ac-139">Object 型</span><span class="sxs-lookup"><span data-stu-id="d89ac-139">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
