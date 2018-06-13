---
title: 'オブジェクト初期化子: 名前付きの型と匿名型 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.ObjectInitializer
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
ms.openlocfilehash: 612b1dcea0f776dfd4580803e76f2785e7d28da6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655637"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a><span data-ttu-id="3c3c6-102">オブジェクト初期化子: 名前付きの型と匿名型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c3c6-102">Object Initializers: Named and Anonymous Types (Visual Basic)</span></span>
<span data-ttu-id="3c3c6-103">オブジェクト初期化子を使用すると、1 つの式を使用して、複雑なオブジェクトのプロパティを指定できます。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-103">Object initializers enable you to specify properties for a complex object by using a single expression.</span></span> <span data-ttu-id="3c3c6-104">名前付きの型と匿名型のインスタンスの作成に使用できます。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-104">They can be used to create instances of named types and of anonymous types.</span></span>  
  
## <a name="declarations"></a><span data-ttu-id="3c3c6-105">宣言</span><span class="sxs-lookup"><span data-stu-id="3c3c6-105">Declarations</span></span>  
 <span data-ttu-id="3c3c6-106">匿名の名前付きの型のインスタンスの宣言はほとんど同じように確認できますが、その効果が同じではありません。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-106">Declarations of instances of named and anonymous types can look almost identical, but their effects are not the same.</span></span> <span data-ttu-id="3c3c6-107">各カテゴリには、独自の機能と制限があります。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-107">Each category has abilities and restrictions of its own.</span></span> <span data-ttu-id="3c3c6-108">次の例は、宣言し、名前付きクラスのインスタンスを初期化するための便利な方法を示しています。 `Customer`、オブジェクト初期化子リストを使用しています。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-108">The following example shows a convenient way to declare and initialize an instance of a named class, `Customer`, by using an object initializer list.</span></span> <span data-ttu-id="3c3c6-109">キーワードの後に、クラスの名前が指定されていることを確認`New`です。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-109">Notice that the name of the class is specified after the keyword `New`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#1](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_1.vb)]  
  
 <span data-ttu-id="3c3c6-110">匿名型には、使用可能な名前がありません。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-110">An anonymous type has no usable name.</span></span> <span data-ttu-id="3c3c6-111">そのため、匿名型のインスタンス化では、クラス名を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-111">Therefore an instantiation of an anonymous type cannot include a class name.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
 <span data-ttu-id="3c3c6-112">要件および 2 つの宣言の結果は同じです。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-112">The requirements and results of the two declarations are not the same.</span></span> <span data-ttu-id="3c3c6-113">`namedCust`、`Customer`を持つクラス、`Name`プロパティが既に存在し、宣言は、そのクラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-113">For `namedCust`, a `Customer` class that has a `Name` property must already exist, and the declaration creates an instance of that class.</span></span> <span data-ttu-id="3c3c6-114">`anonymousCust`、コンパイラと呼ばれる文字列の 1 つのプロパティを持つ新しいクラスを定義する`Name`、し、そのクラスの新しいインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-114">For `anonymousCust`, the compiler defines a new class that has one property, a string called `Name`, and creates a new instance of that class.</span></span>  
  
## <a name="named-types"></a><span data-ttu-id="3c3c6-115">名前付きの型</span><span class="sxs-lookup"><span data-stu-id="3c3c6-115">Named Types</span></span>  
 <span data-ttu-id="3c3c6-116">オブジェクト初期化子は、型のコンス トラクターを呼び出すし、単一のステートメントでの一部またはすべてのプロパティの値を設定する簡単な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-116">Object initializers provide a simple way to call the constructor of a type and then set the values of some or all properties in a single statement.</span></span> <span data-ttu-id="3c3c6-117">コンパイラは、ステートメントの適切なコンス トラクターを呼び出します: 引数が何も表示されない場合、既定のコンス トラクターまたは 1 つまたは複数の引数が送信される場合にパラメーター化されたコンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-117">The compiler invokes the appropriate constructor for the statement: the default constructor if no arguments are presented, or a parameterized constructor if one or more arguments are sent.</span></span> <span data-ttu-id="3c3c6-118">その後、指定したプロパティは初期化子リストに示されている順序で初期化されます。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-118">After that, the specified properties are initialized in the order in which they are presented in the initializer list.</span></span>  
  
 <span data-ttu-id="3c3c6-119">初期化子リストで各初期化は、クラスのメンバーに初期値の割り当てで構成されます。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-119">Each initialization in the initializer list consists of the assignment of an initial value to a member of the class.</span></span> <span data-ttu-id="3c3c6-120">名前と、メンバーのデータ型は、クラスが定義されているときに決定されます。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-120">The names and data types of the members are determined when the class is defined.</span></span> <span data-ttu-id="3c3c6-121">次の例で、`Customer`クラスが存在し、必要がありますにはメンバー名前付け`Name`と`City`文字列値を受け入れることができます。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-121">In the following examples, the `Customer` class must exist, and must have members named `Name` and `City` that can accept string values.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#3](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_3.vb)]  
  
 <span data-ttu-id="3c3c6-122">また、次のコードを使用して、同じ結果を取得できます。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-122">Alternatively, you can obtain the same result by using the following code:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#4](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_4.vb)]  
  
 <span data-ttu-id="3c3c6-123">これらの各宣言は次の例は、作成、`Customer`既定のコンス トラクターを使用して、オブジェクトし、の初期値を指定し、`Name`と`City`プロパティを使用して、 `With`ステートメント。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-123">Each of these declarations is equivalent to the following example, which creates a `Customer` object by using the default constructor, and then specifies initial values for the `Name` and `City` properties by using a `With` statement.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#5](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_5.vb)]  
  
 <span data-ttu-id="3c3c6-124">場合、`Customer`クラスには、の値を送信することができますをパラメーター化されたコンス トラクターが含まれています。 `Name`、たとえば、もを宣言して初期化、`Customer`次の方法でオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-124">If the `Customer` class contains a parameterized constructor that enables you to send in a value for `Name`, for example, you can also declare and initialize a `Customer` object in the following ways:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#6](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_6.vb)]  
  
 <span data-ttu-id="3c3c6-125">次のコードに示すように、すべてのプロパティを初期化する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-125">You do not have to initialize all properties, as the following code shows.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#7](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_7.vb)]  
  
 <span data-ttu-id="3c3c6-126">ただし、初期化リストを空にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-126">However, the initialization list cannot be empty.</span></span> <span data-ttu-id="3c3c6-127">初期化されていないプロパティは、既定値を保持します。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-127">Uninitialized properties retain their default values.</span></span>  
  
### <a name="type-inference-with-named-types"></a><span data-ttu-id="3c3c6-128">名前付きの型と型の推論</span><span class="sxs-lookup"><span data-stu-id="3c3c6-128">Type Inference with Named Types</span></span>  
 <span data-ttu-id="3c3c6-129">宣言のコードを短縮する`cust1`オブジェクト初期化子とローカル型推論を結合します。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-129">You can shorten the code for the declaration of `cust1` by combining object initializers and local type inference.</span></span> <span data-ttu-id="3c3c6-130">これにより、省略すること、`As`変数の宣言内の句。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-130">This enables you to omit the `As` clause in the variable declaration.</span></span> <span data-ttu-id="3c3c6-131">変数のデータ型は、割り当てによって作成されるオブジェクトの型から推論されます。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-131">The data type of the variable is inferred from the type of the object that is created by the assignment.</span></span> <span data-ttu-id="3c3c6-132">次の例では、型で`cust6`は`Customer`します。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-132">In the following example, the type of `cust6` is `Customer`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#8](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_8.vb)]  
  
### <a name="remarks-about-named-types"></a><span data-ttu-id="3c3c6-133">名前付きの型についての解説</span><span class="sxs-lookup"><span data-stu-id="3c3c6-133">Remarks About Named Types</span></span>  
  
-   <span data-ttu-id="3c3c6-134">クラスのメンバーは、オブジェクト初期化子リストで複数回初期化できません。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-134">A class member cannot be initialized more than one time in the object initializer list.</span></span> <span data-ttu-id="3c3c6-135">宣言`cust7`エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-135">The declaration of `cust7` causes an error.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#9](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_9.vb)]  
  
-   <span data-ttu-id="3c3c6-136">メンバーは、そのリング自体または別のフィールドを初期化するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-136">A member can be used to initialize itself or another field.</span></span> <span data-ttu-id="3c3c6-137">メンバーにアクセスしてそれが初期化される前に、次の宣言と同様に場合`cust8`既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-137">If a member is accessed before it has been initialized, as in the following declaration for `cust8`, the default value will be used.</span></span> <span data-ttu-id="3c3c6-138">オブジェクト初期化子を使用する宣言が処理されるときに発生する最初の手順がある適切なコンス トラクターが呼び出されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-138">Remember that when a declaration that uses an object initializer is processed, the first thing that happens is that the appropriate constructor is invoked.</span></span> <span data-ttu-id="3c3c6-139">その後、初期化子リスト内の各フィールドが初期化されます。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-139">After that, the individual fields in the initializer list are initialized.</span></span> <span data-ttu-id="3c3c6-140">既定値を次の例で`Name`に割り当てられた`cust8`で初期化される値が割り当てられていると`cust9`です。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-140">In the following examples, the default value for `Name` is assigned for `cust8`, and an initialized value is assigned in `cust9`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#10](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_10.vb)]  
  
     <span data-ttu-id="3c3c6-141">次の例は、パラメーター化されたコンス トラクターから`cust3`と`cust4`を宣言および初期化する`cust10`と`cust11`です。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-141">The following example uses the parameterized constructor from `cust3` and `cust4` to declare and initialize `cust10` and `cust11`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#11](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_11.vb)]  
  
-   <span data-ttu-id="3c3c6-142">オブジェクト初期化子が入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-142">Object initializers can be nested.</span></span> <span data-ttu-id="3c3c6-143">次の例では、`AddressClass`は 2 つのプロパティを持つクラスである`City`と`State`、および`Customer`クラスには、`Address`のインスタンスであるプロパティ`AddressClass`です。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-143">In the following example, `AddressClass` is a class that has two properties, `City` and `State`, and the `Customer` class has an `Address` property that is an instance of `AddressClass`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#12](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_12.vb)]  
  
-   <span data-ttu-id="3c3c6-144">初期化リストを空にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-144">The initialization list cannot be empty.</span></span>  
  
-   <span data-ttu-id="3c3c6-145">初期化されているインスタンスは、Object 型のすることはできません。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-145">The instance being initialized cannot be of type Object.</span></span>  
  
-   <span data-ttu-id="3c3c6-146">クラスのメンバーの初期化中には、共有メンバー、読み取り専用のメンバー、定数、またはメソッドの呼び出しをすることはできません。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-146">Class members being initialized cannot be shared members, read-only members, constants, or method calls.</span></span>  
  
-   <span data-ttu-id="3c3c6-147">クラスのメンバーの初期化中は、インデックス付きまたは修飾ことはできません。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-147">Class members being initialized cannot be indexed or qualified.</span></span> <span data-ttu-id="3c3c6-148">次の例では、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-148">The following examples raise compiler errors:</span></span>  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a><span data-ttu-id="3c3c6-149">匿名型</span><span class="sxs-lookup"><span data-stu-id="3c3c6-149">Anonymous Types</span></span>  
 <span data-ttu-id="3c3c6-150">匿名型では、オブジェクト初期化子を使用して、明示的に定義していない新しい型と名前のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-150">Anonymous types use object initializers to create instances of new types that you do not explicitly define and name.</span></span> <span data-ttu-id="3c3c6-151">代わりに、コンパイラは、オブジェクト初期化子リストで指定されているプロパティに従って型を生成します。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-151">Instead, the compiler generates a type according to the properties you designate in the object initializer list.</span></span> <span data-ttu-id="3c3c6-152">型の名前が指定されていないため、呼びます、*匿名型*です。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-152">Because the name of the type is not specified, it is referred to as an *anonymous type*.</span></span> <span data-ttu-id="3c3c6-153">たとえば、前に、次の宣言を比較`cust6`です。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-153">For example, compare the following declaration to the earlier one for `cust6`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#13](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_13.vb)]  
  
 <span data-ttu-id="3c3c6-154">唯一の違いが構文的に後の名前が指定されていないことは`New`データ型。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-154">The only difference syntactically is that no name is specified after `New` for the data type.</span></span> <span data-ttu-id="3c3c6-155">ただし、動作は大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-155">However, what happens is quite different.</span></span> <span data-ttu-id="3c3c6-156">コンパイラは 2 つのプロパティを持つ新しい匿名型を定義`Name`と`City`、し、値を指定して、そのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-156">The compiler defines a new anonymous type that has two properties, `Name` and `City`, and creates an instance of it with the specified values.</span></span> <span data-ttu-id="3c3c6-157">型の推論の種類を決定する`Name`と`City`文字列である例です。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-157">Type inference determines the types of `Name` and `City` in the example to be strings.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="3c3c6-158">匿名型の名前は、コンパイラによって生成され、コンパイルするたびに異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-158">The name of the anonymous type is generated by the compiler, and may vary from compilation to compilation.</span></span> <span data-ttu-id="3c3c6-159">コードがや使用しない匿名型の名前に依存します。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-159">Your code should not use or rely on the name of an anonymous type.</span></span>  
  
 <span data-ttu-id="3c3c6-160">使用することはできません型の名前が使用できないため、`As`を宣言する句`cust13`です。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-160">Because the name of the type is not available, you cannot use an `As` clause to declare `cust13`.</span></span> <span data-ttu-id="3c3c6-161">その型を推論する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-161">Its type must be inferred.</span></span> <span data-ttu-id="3c3c6-162">遅延バインディングを使用しない場合は、ローカル変数に匿名型の使用を制限します。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-162">Without using late binding, this limits the use of anonymous types to local variables.</span></span>  
  
 <span data-ttu-id="3c3c6-163">匿名型には、重要なサポートが提供されます。[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリ。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-163">Anonymous types provide critical support for [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="3c3c6-164">クエリ内で匿名型の使用に関する詳細については、次を参照してください。[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)と[Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)です。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-164">For more information about the use of anonymous types in queries, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) and [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).</span></span>  
  
### <a name="remarks-about-anonymous-types"></a><span data-ttu-id="3c3c6-165">匿名型についての解説</span><span class="sxs-lookup"><span data-stu-id="3c3c6-165">Remarks About Anonymous Types</span></span>  
  
-   <span data-ttu-id="3c3c6-166">通常、匿名型の宣言でのプロパティのほとんどまたはすべてにキーのプロパティがあり、キーワードを入力して示される`Key`プロパティ名の前にします。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-166">Typically, all or most of the properties in an anonymous type declaration will be key properties, which are indicated by typing the keyword `Key` in front of the property name.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#14](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_14.vb)]  
  
     <span data-ttu-id="3c3c6-167">キー プロパティの詳細については、次を参照してください。[キー](../../../../visual-basic/language-reference/modifiers/key.md)です。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-167">For more information about key properties, see [Key](../../../../visual-basic/language-reference/modifiers/key.md).</span></span>  
  
-   <span data-ttu-id="3c3c6-168">ような名前付きの型、初期化子リスト匿名型の定義は、少なくとも 1 つのプロパティを宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-168">Like named types, initializer lists for anonymous type definitions must declare at least one property.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
-   <span data-ttu-id="3c3c6-169">匿名型のインスタンスが宣言されると、コンパイラは、一致する匿名型の定義を生成します。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-169">When an instance of an anonymous type is declared, the compiler generates a matching anonymous type definition.</span></span> <span data-ttu-id="3c3c6-170">名前とプロパティのデータ型は、インスタンスの宣言からが取得され、定義に、コンパイラによって含まれています。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-170">The names and data types of the properties are taken from the instance declaration, and are included by the compiler in the definition.</span></span> <span data-ttu-id="3c3c6-171">プロパティがないという名前し、名前付きの型とは異なり、事前に定義されています。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-171">The properties are not named and defined in advance, as they would be for a named type.</span></span> <span data-ttu-id="3c3c6-172">その型が推論されます。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-172">Their types are inferred.</span></span> <span data-ttu-id="3c3c6-173">使用して、プロパティのデータ型を指定することはできません、`As`句。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-173">You cannot specify the data types of the properties by using an `As` clause.</span></span>  
  
-   <span data-ttu-id="3c3c6-174">匿名型は、その他のいくつかの方法で、名前とそのプロパティの値を確立できますも。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-174">Anonymous types can also establish the names and values of their properties in several other ways.</span></span> <span data-ttu-id="3c3c6-175">たとえば、匿名型のプロパティには、名前と、変数、または名前の値と別のオブジェクトのプロパティの値の両方がかかります。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-175">For example, an anonymous type property can take both the name and the value of a variable, or the name and value of a property of another object.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#15](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_15.vb)]  
  
     <span data-ttu-id="3c3c6-176">匿名型のプロパティを定義するためのオプションの詳細については、次を参照してください。[する方法: 匿名型の宣言におけるプロパティ名の推論と型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)です。</span><span class="sxs-lookup"><span data-stu-id="3c3c6-176">For more information about the options for defining properties in anonymous types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c3c6-177">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c3c6-177">See Also</span></span>  
 [<span data-ttu-id="3c3c6-178">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="3c3c6-178">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="3c3c6-179">匿名型</span><span class="sxs-lookup"><span data-stu-id="3c3c6-179">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="3c3c6-180">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="3c3c6-180">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="3c3c6-181">方法 : 匿名型の宣言におけるプロパティ名と型を推論する</span><span class="sxs-lookup"><span data-stu-id="3c3c6-181">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [<span data-ttu-id="3c3c6-182">Key</span><span class="sxs-lookup"><span data-stu-id="3c3c6-182">Key</span></span>](../../../../visual-basic/language-reference/modifiers/key.md)  
 [<span data-ttu-id="3c3c6-183">方法 : オブジェクト初期化子を使用してオブジェクトを宣言する</span><span class="sxs-lookup"><span data-stu-id="3c3c6-183">How to: Declare an Object by Using an Object Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
