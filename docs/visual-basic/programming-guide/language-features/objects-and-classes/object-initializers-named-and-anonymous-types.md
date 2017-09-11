---
title: "オブジェクト初期化子: 名前付きで匿名型 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ObjectInitializer
dev_langs:
- VB
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d3c89fb0a7b7c535f1b46c208ac47f58513208ba
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a><span data-ttu-id="654df-102">オブジェクト初期化子: 名前付きの型と匿名型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="654df-102">Object Initializers: Named and Anonymous Types (Visual Basic)</span></span>
<span data-ttu-id="654df-103">オブジェクト初期化子を使用すると、1 つの式を使用して、複雑なオブジェクトのプロパティを指定できます。</span><span class="sxs-lookup"><span data-stu-id="654df-103">Object initializers enable you to specify properties for a complex object by using a single expression.</span></span> <span data-ttu-id="654df-104">名前付きの型と匿名型のインスタンスを作成して、使用できます。</span><span class="sxs-lookup"><span data-stu-id="654df-104">They can be used to create instances of named types and of anonymous types.</span></span>  
  
## <a name="declarations"></a><span data-ttu-id="654df-105">宣言</span><span class="sxs-lookup"><span data-stu-id="654df-105">Declarations</span></span>  
 <span data-ttu-id="654df-106">名前付きで匿名型のインスタンスの宣言はほとんど同じように確認できますが、その効果が同じではありません。</span><span class="sxs-lookup"><span data-stu-id="654df-106">Declarations of instances of named and anonymous types can look almost identical, but their effects are not the same.</span></span> <span data-ttu-id="654df-107">各カテゴリには、独自の機能と制限があります。</span><span class="sxs-lookup"><span data-stu-id="654df-107">Each category has abilities and restrictions of its own.</span></span> <span data-ttu-id="654df-108">次の例を宣言し、名前付きクラスのインスタンスを初期化するための便利な方法を示しています。 `Customer`、オブジェクト初期化子リストを使用しています。</span><span class="sxs-lookup"><span data-stu-id="654df-108">The following example shows a convenient way to declare and initialize an instance of a named class, `Customer`, by using an object initializer list.</span></span> <span data-ttu-id="654df-109">キーワードの後に、クラスの名前が指定されていることに注意してください。`New`します。</span><span class="sxs-lookup"><span data-stu-id="654df-109">Notice that the name of the class is specified after the keyword `New`.</span></span>  
  
 <span data-ttu-id="654df-110">[!code-vb[VbVbalrObjectInit&#1;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="654df-110">[!code-vb[VbVbalrObjectInit#1](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_1.vb)]</span></span>  
  
 <span data-ttu-id="654df-111">匿名型には、使用可能な名前がありません。</span><span class="sxs-lookup"><span data-stu-id="654df-111">An anonymous type has no usable name.</span></span> <span data-ttu-id="654df-112">そのため、匿名型のインスタンス化では、クラス名を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="654df-112">Therefore an instantiation of an anonymous type cannot include a class name.</span></span>  
  
 <span data-ttu-id="654df-113">[!code-vb[VbVbalrObjectInit&#2;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="654df-113">[!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]</span></span>  
  
 <span data-ttu-id="654df-114">要件と&2; つの宣言の結果は同じです。</span><span class="sxs-lookup"><span data-stu-id="654df-114">The requirements and results of the two declarations are not the same.</span></span> <span data-ttu-id="654df-115">`namedCust`、`Customer`を持つクラス、`Name`プロパティが既に存在し、宣言は、そのクラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="654df-115">For `namedCust`, a `Customer` class that has a `Name` property must already exist, and the declaration creates an instance of that class.</span></span> <span data-ttu-id="654df-116">`anonymousCust`、コンパイラと呼ばれる文字列の&1; つのプロパティを使用する新しいクラスを定義`Name`、し、そのクラスの新しいインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="654df-116">For `anonymousCust`, the compiler defines a new class that has one property, a string called `Name`, and creates a new instance of that class.</span></span>  
  
## <a name="named-types"></a><span data-ttu-id="654df-117">名前付きの型</span><span class="sxs-lookup"><span data-stu-id="654df-117">Named Types</span></span>  
 <span data-ttu-id="654df-118">オブジェクト初期化子は、型のコンス トラクターを呼び出すし、単一のステートメントでの一部またはすべてのプロパティの値を設定する簡単な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="654df-118">Object initializers provide a simple way to call the constructor of a type and then set the values of some or all properties in a single statement.</span></span> <span data-ttu-id="654df-119">コンパイラは、ステートメントの適切なコンス トラクターを呼び出します。 既定のコンス トラクターの引数が何も表示されない場合、または&1; つまたは複数の引数を渡す場合にパラメーター化されたコンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="654df-119">The compiler invokes the appropriate constructor for the statement: the default constructor if no arguments are presented, or a parameterized constructor if one or more arguments are sent.</span></span> <span data-ttu-id="654df-120">その後、指定したプロパティは、初期化子リストに示されている順序で初期化されます。</span><span class="sxs-lookup"><span data-stu-id="654df-120">After that, the specified properties are initialized in the order in which they are presented in the initializer list.</span></span>  
  
 <span data-ttu-id="654df-121">初期化子リスト内の各初期化は、クラスのメンバーへの初期値の割り当てで構成されます。</span><span class="sxs-lookup"><span data-stu-id="654df-121">Each initialization in the initializer list consists of the assignment of an initial value to a member of the class.</span></span> <span data-ttu-id="654df-122">クラスが定義されている場合、名前と、メンバーのデータ型が決まります。</span><span class="sxs-lookup"><span data-stu-id="654df-122">The names and data types of the members are determined when the class is defined.</span></span> <span data-ttu-id="654df-123">次の例で、`Customer`クラスが存在し、あるメンバーという名前の必要があります`Name`と`City`文字列の値を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="654df-123">In the following examples, the `Customer` class must exist, and must have members named `Name` and `City` that can accept string values.</span></span>  
  
 <span data-ttu-id="654df-124">[!code-vb[VbVbalrObjectInit&#3;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="654df-124">[!code-vb[VbVbalrObjectInit#3](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_3.vb)]</span></span>  
  
 <span data-ttu-id="654df-125">または、次のコードを使用して、同じ結果を取得できます。</span><span class="sxs-lookup"><span data-stu-id="654df-125">Alternatively, you can obtain the same result by using the following code:</span></span>  
  
 <span data-ttu-id="654df-126">[!code-vb[VbVbalrObjectInit&4;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="654df-126">[!code-vb[VbVbalrObjectInit#4](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_4.vb)]</span></span>  
  
 <span data-ttu-id="654df-127">これらの宣言は次の例は、作成に相当する`Customer`既定のコンス トラクターを使用して、オブジェクトし、の初期値を指定、`Name`と`City`プロパティを使用して、`With`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="654df-127">Each of these declarations is equivalent to the following example, which creates a `Customer` object by using the default constructor, and then specifies initial values for the `Name` and `City` properties by using a `With` statement.</span></span>  
  
 <span data-ttu-id="654df-128">[!code-vb[VbVbalrObjectInit&#5;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="654df-128">[!code-vb[VbVbalrObjectInit#5](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_5.vb)]</span></span>  
  
 <span data-ttu-id="654df-129">場合、`Customer`クラスには、パラメーター化されたコンス トラクター値を送信することができますにはが含まれています。 `Name`、なども宣言して初期化、`Customer`次の方法でオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="654df-129">If the `Customer` class contains a parameterized constructor that enables you to send in a value for `Name`, for example, you can also declare and initialize a `Customer` object in the following ways:</span></span>  
  
 <span data-ttu-id="654df-130">[!code-vb[VbVbalrObjectInit&6;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="654df-130">[!code-vb[VbVbalrObjectInit#6](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_6.vb)]</span></span>  
  
 <span data-ttu-id="654df-131">次のコードに示すように、すべてのプロパティを初期化する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="654df-131">You do not have to initialize all properties, as the following code shows.</span></span>  
  
 <span data-ttu-id="654df-132">[!code-vb[VbVbalrObjectInit&#7;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="654df-132">[!code-vb[VbVbalrObjectInit#7](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_7.vb)]</span></span>  
  
 <span data-ttu-id="654df-133">ただし、初期化リストを空にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="654df-133">However, the initialization list cannot be empty.</span></span> <span data-ttu-id="654df-134">初期化されていないプロパティは、既定値を保持します。</span><span class="sxs-lookup"><span data-stu-id="654df-134">Uninitialized properties retain their default values.</span></span>  
  
### <a name="type-inference-with-named-types"></a><span data-ttu-id="654df-135">名前付きの型と型の推論</span><span class="sxs-lookup"><span data-stu-id="654df-135">Type Inference with Named Types</span></span>  
 <span data-ttu-id="654df-136">宣言のコードを短く`cust1`オブジェクト初期化子とローカル型推論を結合します。</span><span class="sxs-lookup"><span data-stu-id="654df-136">You can shorten the code for the declaration of `cust1` by combining object initializers and local type inference.</span></span> <span data-ttu-id="654df-137">これは、省略することにより、`As`変数の宣言内の句。</span><span class="sxs-lookup"><span data-stu-id="654df-137">This enables you to omit the `As` clause in the variable declaration.</span></span> <span data-ttu-id="654df-138">変数のデータ型は、代入によって作成されるオブジェクトの型から推論されます。</span><span class="sxs-lookup"><span data-stu-id="654df-138">The data type of the variable is inferred from the type of the object that is created by the assignment.</span></span> <span data-ttu-id="654df-139">次の例の種類で`cust6`は`Customer`です。</span><span class="sxs-lookup"><span data-stu-id="654df-139">In the following example, the type of `cust6` is `Customer`.</span></span>  
  
 <span data-ttu-id="654df-140">[!code-vb[VbVbalrObjectInit&#8;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="654df-140">[!code-vb[VbVbalrObjectInit#8](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_8.vb)]</span></span>  
  
### <a name="remarks-about-named-types"></a><span data-ttu-id="654df-141">名前付きの型についての解説</span><span class="sxs-lookup"><span data-stu-id="654df-141">Remarks About Named Types</span></span>  
  
-   <span data-ttu-id="654df-142">クラスのメンバーには、オブジェクト初期化子リストに&1; つ以上の時間を初期化できません。</span><span class="sxs-lookup"><span data-stu-id="654df-142">A class member cannot be initialized more than one time in the object initializer list.</span></span> <span data-ttu-id="654df-143">宣言`cust7`エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="654df-143">The declaration of `cust7` causes an error.</span></span>  
  
     <span data-ttu-id="654df-144">[!code-vb[VbVbalrObjectInit&#9;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="654df-144">[!code-vb[VbVbalrObjectInit#9](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_9.vb)]</span></span>  
  
-   <span data-ttu-id="654df-145">メンバーは、そのリング自体または別のフィールドを初期化するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="654df-145">A member can be used to initialize itself or another field.</span></span> <span data-ttu-id="654df-146">初期化された、次の宣言と同様にする前に、メンバーがアクセスされる場合`cust8`既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="654df-146">If a member is accessed before it has been initialized, as in the following declaration for `cust8`, the default value will be used.</span></span> <span data-ttu-id="654df-147">オブジェクト初期化子を使用する宣言が処理されるときに最初に行われるが適切なコンス トラクターが呼び出されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="654df-147">Remember that when a declaration that uses an object initializer is processed, the first thing that happens is that the appropriate constructor is invoked.</span></span> <span data-ttu-id="654df-148">その後は、初期化子リスト内の各フィールドが初期化されます。</span><span class="sxs-lookup"><span data-stu-id="654df-148">After that, the individual fields in the initializer list are initialized.</span></span> <span data-ttu-id="654df-149">既定値を次の例で`Name`が割り当てられている`cust8`、しで初期化された値を割り当てる`cust9`します。</span><span class="sxs-lookup"><span data-stu-id="654df-149">In the following examples, the default value for `Name` is assigned for `cust8`, and an initialized value is assigned in `cust9`.</span></span>  
  
     <span data-ttu-id="654df-150">[!code-vb[VbVbalrObjectInit&#10;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="654df-150">[!code-vb[VbVbalrObjectInit#10](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_10.vb)]</span></span>  
  
     <span data-ttu-id="654df-151">次の例は、パラメーター化されたコンス トラクターから`cust3`と`cust4`を宣言して初期化`cust10`と`cust11`です。</span><span class="sxs-lookup"><span data-stu-id="654df-151">The following example uses the parameterized constructor from `cust3` and `cust4` to declare and initialize `cust10` and `cust11`.</span></span>  
  
     <span data-ttu-id="654df-152">[!code-vb[VbVbalrObjectInit&#11;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_11.vb)]</span><span class="sxs-lookup"><span data-stu-id="654df-152">[!code-vb[VbVbalrObjectInit#11](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_11.vb)]</span></span>  
  
-   <span data-ttu-id="654df-153">オブジェクト初期化子が入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="654df-153">Object initializers can be nested.</span></span> <span data-ttu-id="654df-154">次の例で`AddressClass`を&2; つのプロパティを持つクラスは、`City`と`State`、および`Customer`クラスには、`Address`のインスタンスであるプロパティ`AddressClass`します。</span><span class="sxs-lookup"><span data-stu-id="654df-154">In the following example, `AddressClass` is a class that has two properties, `City` and `State`, and the `Customer` class has an `Address` property that is an instance of `AddressClass`.</span></span>  
  
     <span data-ttu-id="654df-155">[!code-vb[VbVbalrObjectInit&#12;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_12.vb)]</span><span class="sxs-lookup"><span data-stu-id="654df-155">[!code-vb[VbVbalrObjectInit#12](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_12.vb)]</span></span>  
  
-   <span data-ttu-id="654df-156">初期化リストを空にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="654df-156">The initialization list cannot be empty.</span></span>  
  
-   <span data-ttu-id="654df-157">初期化中のインスタンスは、Object 型のすることはできません。</span><span class="sxs-lookup"><span data-stu-id="654df-157">The instance being initialized cannot be of type Object.</span></span>  
  
-   <span data-ttu-id="654df-158">クラスのメンバーの初期化中には、共有メンバー、読み取り専用のメンバー、定数、またはメソッドの呼び出しをすることはできません。</span><span class="sxs-lookup"><span data-stu-id="654df-158">Class members being initialized cannot be shared members, read-only members, constants, or method calls.</span></span>  
  
-   <span data-ttu-id="654df-159">クラスのメンバーの初期化中は、インデックス付きまたは修飾ことはできません。</span><span class="sxs-lookup"><span data-stu-id="654df-159">Class members being initialized cannot be indexed or qualified.</span></span> <span data-ttu-id="654df-160">次の例では、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="654df-160">The following examples raise compiler errors:</span></span>  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a><span data-ttu-id="654df-161">匿名型</span><span class="sxs-lookup"><span data-stu-id="654df-161">Anonymous Types</span></span>  
 <span data-ttu-id="654df-162">匿名型では、オブジェクト初期化子を使用して、明示的に定義していない新しい型と名前のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="654df-162">Anonymous types use object initializers to create instances of new types that you do not explicitly define and name.</span></span> <span data-ttu-id="654df-163">代わりに、コンパイラは、オブジェクト初期化子リストに指定されているプロパティに従って型を生成します。</span><span class="sxs-lookup"><span data-stu-id="654df-163">Instead, the compiler generates a type according to the properties you designate in the object initializer list.</span></span> <span data-ttu-id="654df-164">型の名前が指定されていないためと呼びます、*匿名型*します。</span><span class="sxs-lookup"><span data-stu-id="654df-164">Because the name of the type is not specified, it is referred to as an *anonymous type*.</span></span> <span data-ttu-id="654df-165">たとえば、前に、次の宣言を比較`cust6`します。</span><span class="sxs-lookup"><span data-stu-id="654df-165">For example, compare the following declaration to the earlier one for `cust6`.</span></span>  
  
 <span data-ttu-id="654df-166">[!code-vb[VbVbalrObjectInit&#13;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_13.vb)]</span><span class="sxs-lookup"><span data-stu-id="654df-166">[!code-vb[VbVbalrObjectInit#13](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_13.vb)]</span></span>  
  
 <span data-ttu-id="654df-167">唯一の違いが構文的に後に名前が指定されていないことは`New`データ型にします。</span><span class="sxs-lookup"><span data-stu-id="654df-167">The only difference syntactically is that no name is specified after `New` for the data type.</span></span> <span data-ttu-id="654df-168">ただし、動作は大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="654df-168">However, what happens is quite different.</span></span> <span data-ttu-id="654df-169">コンパイラは次の&2; つのプロパティを持つ新しい匿名型を定義`Name`と`City`、し、値を指定して、そのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="654df-169">The compiler defines a new anonymous type that has two properties, `Name` and `City`, and creates an instance of it with the specified values.</span></span> <span data-ttu-id="654df-170">型の推定の種類を決定する`Name`と`City`文字列の例です。</span><span class="sxs-lookup"><span data-stu-id="654df-170">Type inference determines the types of `Name` and `City` in the example to be strings.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="654df-171">匿名型の名前は、コンパイラによって生成され、コンパイルするたびに異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="654df-171">The name of the anonymous type is generated by the compiler, and may vary from compilation to compilation.</span></span> <span data-ttu-id="654df-172">コード使用したり、避けて、匿名型の名前に依存します。</span><span class="sxs-lookup"><span data-stu-id="654df-172">Your code should not use or rely on the name of an anonymous type.</span></span>  
  
 <span data-ttu-id="654df-173">型の名前を使用できないために使用できません、`As`を宣言する句`cust13`します。</span><span class="sxs-lookup"><span data-stu-id="654df-173">Because the name of the type is not available, you cannot use an `As` clause to declare `cust13`.</span></span> <span data-ttu-id="654df-174">その型を推論する必要があります。</span><span class="sxs-lookup"><span data-stu-id="654df-174">Its type must be inferred.</span></span> <span data-ttu-id="654df-175">遅延バインディングを使用しない場合は、ローカル変数に匿名型の使用を制限します。</span><span class="sxs-lookup"><span data-stu-id="654df-175">Without using late binding, this limits the use of anonymous types to local variables.</span></span>  
  
 <span data-ttu-id="654df-176">匿名型の重要なサポートは提供[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]クエリ。</span><span class="sxs-lookup"><span data-stu-id="654df-176">Anonymous types provide critical support for [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] queries.</span></span> <span data-ttu-id="654df-177">クエリ内で匿名型の使用に関する詳細については、次を参照してください。[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)と[Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)します。</span><span class="sxs-lookup"><span data-stu-id="654df-177">For more information about the use of anonymous types in queries, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) and [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).</span></span>  
  
### <a name="remarks-about-anonymous-types"></a><span data-ttu-id="654df-178">匿名型についての解説</span><span class="sxs-lookup"><span data-stu-id="654df-178">Remarks About Anonymous Types</span></span>  
  
-   <span data-ttu-id="654df-179">通常、匿名型の宣言におけるプロパティのほとんどまたはすべてでは、キーワードを入力して示されるキー プロパティ`Key`プロパティ名の前にします。</span><span class="sxs-lookup"><span data-stu-id="654df-179">Typically, all or most of the properties in an anonymous type declaration will be key properties, which are indicated by typing the keyword `Key` in front of the property name.</span></span>  
  
     <span data-ttu-id="654df-180">[!code-vb[VbVbalrObjectInit&#14;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_14.vb)]</span><span class="sxs-lookup"><span data-stu-id="654df-180">[!code-vb[VbVbalrObjectInit#14](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_14.vb)]</span></span>  
  
     <span data-ttu-id="654df-181">キー プロパティの詳細については、次を参照してください。[キー](../../../../visual-basic/language-reference/modifiers/key.md)します。</span><span class="sxs-lookup"><span data-stu-id="654df-181">For more information about key properties, see [Key](../../../../visual-basic/language-reference/modifiers/key.md).</span></span>  
  
-   <span data-ttu-id="654df-182">このような名前付きの型、初期化子リスト匿名型の定義は、少なくとも&1; つのプロパティを宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="654df-182">Like named types, initializer lists for anonymous type definitions must declare at least one property.</span></span>  
  
     <span data-ttu-id="654df-183">[!code-vb[VbVbalrObjectInit&#2;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="654df-183">[!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]</span></span>  
  
-   <span data-ttu-id="654df-184">匿名型のインスタンスを宣言すると、コンパイラは、一致する匿名型の定義を生成します。</span><span class="sxs-lookup"><span data-stu-id="654df-184">When an instance of an anonymous type is declared, the compiler generates a matching anonymous type definition.</span></span> <span data-ttu-id="654df-185">名前とプロパティのデータ型インスタンスの宣言から取得され、定義のコンパイラでは追加します。</span><span class="sxs-lookup"><span data-stu-id="654df-185">The names and data types of the properties are taken from the instance declaration, and are included by the compiler in the definition.</span></span> <span data-ttu-id="654df-186">プロパティがないという名前し、名前付きの型とは異なり、事前に定義されています。</span><span class="sxs-lookup"><span data-stu-id="654df-186">The properties are not named and defined in advance, as they would be for a named type.</span></span> <span data-ttu-id="654df-187">その型が推論されます。</span><span class="sxs-lookup"><span data-stu-id="654df-187">Their types are inferred.</span></span> <span data-ttu-id="654df-188">使用して、プロパティのデータ型を指定することはできません、`As`句。</span><span class="sxs-lookup"><span data-stu-id="654df-188">You cannot specify the data types of the properties by using an `As` clause.</span></span>  
  
-   <span data-ttu-id="654df-189">匿名型は、その他のいくつかの方法で、名前とそのプロパティの値を確立できますもします。</span><span class="sxs-lookup"><span data-stu-id="654df-189">Anonymous types can also establish the names and values of their properties in several other ways.</span></span> <span data-ttu-id="654df-190">たとえば、匿名型のプロパティには、名前と、変数、または名前の値と別のオブジェクトのプロパティの値の両方がかかります。</span><span class="sxs-lookup"><span data-stu-id="654df-190">For example, an anonymous type property can take both the name and the value of a variable, or the name and value of a property of another object.</span></span>  
  
     <span data-ttu-id="654df-191">[!code-vb[VbVbalrObjectInit&#15;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_15.vb)]</span><span class="sxs-lookup"><span data-stu-id="654df-191">[!code-vb[VbVbalrObjectInit#15](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_15.vb)]</span></span>  
  
     <span data-ttu-id="654df-192">匿名型のプロパティを定義するためのオプションの詳細については、次を参照してください。[方法: 匿名型の宣言におけるプロパティ名の推論と型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)します。</span><span class="sxs-lookup"><span data-stu-id="654df-192">For more information about the options for defining properties in anonymous types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="654df-193">関連項目</span><span class="sxs-lookup"><span data-stu-id="654df-193">See Also</span></span>  
 <span data-ttu-id="654df-194">[ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="654df-194">[Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="654df-195"> [匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="654df-195"> [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span></span>  
<span data-ttu-id="654df-196"> [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="654df-196"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="654df-197"> [方法: 匿名型の宣言におけるプロパティ名と型の推論](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md) </span><span class="sxs-lookup"><span data-stu-id="654df-197"> [How to: Infer Property Names and Types in Anonymous Type Declarations](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md) </span></span>  
<span data-ttu-id="654df-198"> [キー](../../../../visual-basic/language-reference/modifiers/key.md) </span><span class="sxs-lookup"><span data-stu-id="654df-198"> [Key](../../../../visual-basic/language-reference/modifiers/key.md) </span></span>  
<span data-ttu-id="654df-199"> [方法 : オブジェクト初期化子を使用してオブジェクトを宣言する](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)</span><span class="sxs-lookup"><span data-stu-id="654df-199"> [How to: Declare an Object by Using an Object Initializer](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)</span></span>
