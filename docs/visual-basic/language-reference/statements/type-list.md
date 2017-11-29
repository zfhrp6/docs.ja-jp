---
title: "型リスト (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- StructureConstraint
- vb.StructureConstraint
- ClassConstraint
- vb.ClassConstraint
helpviewer_keywords:
- class constraint
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- generics [Visual Basic], type list
- structure constraint
- constraints, in type parameters
- generics [Visual Basic], generic types
- parameters [Visual Basic], type
- constraints, Structure keyword
- type parameters [Visual Basic], constraints
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], type parameters
- type parameters
- constraints, Class keyword
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 35e72414b236615dc230b654ccfeed290841fb31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="type-list-visual-basic"></a><span data-ttu-id="233b8-102">型リスト (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="233b8-102">Type List (Visual Basic)</span></span>
<span data-ttu-id="233b8-103">指定します、*パラメーター入力*の*ジェネリック*プログラミング要素です。</span><span class="sxs-lookup"><span data-stu-id="233b8-103">Specifies the *type parameters* for a *generic* programming element.</span></span> <span data-ttu-id="233b8-104">複数のパラメーターは、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="233b8-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="233b8-105">1 つの型パラメーターの構文を次に示します。</span><span class="sxs-lookup"><span data-stu-id="233b8-105">Following is the syntax for one type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="233b8-106">構文</span><span class="sxs-lookup"><span data-stu-id="233b8-106">Syntax</span></span>  
  
```  
[genericmodifier] typename [ As constraintlist ]  
```  
  
## <a name="parts"></a><span data-ttu-id="233b8-107">指定項目</span><span class="sxs-lookup"><span data-stu-id="233b8-107">Parts</span></span>  
  
|<span data-ttu-id="233b8-108">用語</span><span class="sxs-lookup"><span data-stu-id="233b8-108">Term</span></span>|<span data-ttu-id="233b8-109">定義</span><span class="sxs-lookup"><span data-stu-id="233b8-109">Definition</span></span>|  
|---|---|  
|`genericmodifier`|<span data-ttu-id="233b8-110">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="233b8-110">Optional.</span></span> <span data-ttu-id="233b8-111">ジェネリック インターフェイスとバリアント汎用デリゲートでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="233b8-111">Can be used only in generic interfaces and delegates.</span></span> <span data-ttu-id="233b8-112">型を宣言する共変を使用して、[アウト](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)キーワードまたは反変を使用して、[で](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)キーワード。</span><span class="sxs-lookup"><span data-stu-id="233b8-112">You can declare a type covariant by using the [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) keyword or contravariant by using the [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) keyword.</span></span> <span data-ttu-id="233b8-113">「 [共変性と反変性](../../programming-guide/concepts/covariance-contravariance/index.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="233b8-113">See [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>|  
|`typename`|<span data-ttu-id="233b8-114">必須です。</span><span class="sxs-lookup"><span data-stu-id="233b8-114">Required.</span></span> <span data-ttu-id="233b8-115">型パラメーターの名前です。</span><span class="sxs-lookup"><span data-stu-id="233b8-115">Name of the type parameter.</span></span> <span data-ttu-id="233b8-116">これは、対応する型引数で指定した定義済みの型によって置き換えられるプレース ホルダーです。</span><span class="sxs-lookup"><span data-stu-id="233b8-116">This is a placeholder, to be replaced by a defined type supplied by the corresponding type argument.</span></span>|  
|`constraintlist`|<span data-ttu-id="233b8-117">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="233b8-117">Optional.</span></span> <span data-ttu-id="233b8-118">指定できるデータ型を制約するための要件の一覧`typename`です。</span><span class="sxs-lookup"><span data-stu-id="233b8-118">List of requirements that constrain the data type that can be supplied for `typename`.</span></span> <span data-ttu-id="233b8-119">複数の制約があれば、中かっこで囲む (`{ }`) をコンマで区切って指定します。</span><span class="sxs-lookup"><span data-stu-id="233b8-119">If you have multiple constraints, enclose them in curly braces (`{ }`) and separate them with commas.</span></span> <span data-ttu-id="233b8-120">使用して、制約リストを導入する必要があります、[として](../../../visual-basic/language-reference/statements/as-clause.md)キーワード。</span><span class="sxs-lookup"><span data-stu-id="233b8-120">You must introduce the constraint list with the [As](../../../visual-basic/language-reference/statements/as-clause.md) keyword.</span></span> <span data-ttu-id="233b8-121">使用する`As`リストの先頭に一度だけです。</span><span class="sxs-lookup"><span data-stu-id="233b8-121">You use `As` only once, at the beginning of the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="233b8-122">コメント</span><span class="sxs-lookup"><span data-stu-id="233b8-122">Remarks</span></span>  
 <span data-ttu-id="233b8-123">すべて汎用のプログラミング要素には、少なくとも 1 つの型パラメーターを受け取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="233b8-123">Every generic programming element must take at least one type parameter.</span></span> <span data-ttu-id="233b8-124">型パラメーターは、特定の種類を表すプレース ホルダー (、*構築される要素*) クライアント コードは、ジェネリック型のインスタンスを作成するタイミングを指定します。</span><span class="sxs-lookup"><span data-stu-id="233b8-124">A type parameter is a placeholder for a specific type (a *constructed element*) that client code specifies when it creates an instance of the generic type.</span></span> <span data-ttu-id="233b8-125">ジェネリック クラスを定義、構造体、インターフェイス、プロシージャ、したり、委任できます。</span><span class="sxs-lookup"><span data-stu-id="233b8-125">You can define a generic class, structure, interface, procedure, or delegate.</span></span>  
  
 <span data-ttu-id="233b8-126">ジェネリック型を定義する場合の詳細については、次を参照してください。 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="233b8-126">For more information on when to define a generic type, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span> <span data-ttu-id="233b8-127">型パラメーター名の詳細については、次を参照してください。[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。</span><span class="sxs-lookup"><span data-stu-id="233b8-127">For more information on type parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="233b8-128">ルール</span><span class="sxs-lookup"><span data-stu-id="233b8-128">Rules</span></span>  
  
-   <span data-ttu-id="233b8-129">**かっこです。**</span><span class="sxs-lookup"><span data-stu-id="233b8-129">**Parentheses.**</span></span> <span data-ttu-id="233b8-130">型パラメーター リストを指定する場合は、かっこで囲む必要がありますを使用してリストを導入する必要があります、[の](../../../visual-basic/language-reference/statements/of-clause.md)キーワード。</span><span class="sxs-lookup"><span data-stu-id="233b8-130">If you supply a type parameter list, you must enclose it in parentheses, and you must introduce the list with the [Of](../../../visual-basic/language-reference/statements/of-clause.md) keyword.</span></span> <span data-ttu-id="233b8-131">使用する`Of`リストの先頭に一度だけです。</span><span class="sxs-lookup"><span data-stu-id="233b8-131">You use `Of` only once, at the beginning of the list.</span></span>  
  
-   <span data-ttu-id="233b8-132">**制約。**</span><span class="sxs-lookup"><span data-stu-id="233b8-132">**Constraints.**</span></span> <span data-ttu-id="233b8-133">一連の*制約*型のパラメーターは、任意の組み合わせで、次の項目を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="233b8-133">A list of *constraints* on a type parameter can include the following items in any combination:</span></span>  
  
    -   <span data-ttu-id="233b8-134">インターフェイスの数。</span><span class="sxs-lookup"><span data-stu-id="233b8-134">Any number of interfaces.</span></span> <span data-ttu-id="233b8-135">指定された型は、この一覧にすべてのインターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="233b8-135">The supplied type must implement every interface in this list.</span></span>  
  
    -   <span data-ttu-id="233b8-136">1 つのクラスです。</span><span class="sxs-lookup"><span data-stu-id="233b8-136">At most one class.</span></span> <span data-ttu-id="233b8-137">指定された型は、そのクラスから継承する必要があります。</span><span class="sxs-lookup"><span data-stu-id="233b8-137">The supplied type must inherit from that class.</span></span>  
  
    -   <span data-ttu-id="233b8-138">`New` キーワード。</span><span class="sxs-lookup"><span data-stu-id="233b8-138">The `New` keyword.</span></span> <span data-ttu-id="233b8-139">指定された型は、ジェネリック型にアクセスできるパラメーターなしのコンス トラクターを公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="233b8-139">The supplied type must expose a parameterless constructor that your generic type can access.</span></span> <span data-ttu-id="233b8-140">これは、1 つまたは複数のインターフェイスによって型パラメーターを制約する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="233b8-140">This is useful if you constrain a type parameter by one or more interfaces.</span></span> <span data-ttu-id="233b8-141">インターフェイスを実装する型は必ずしもは、コンス トラクターを公開しませんし、コンス トラクターのアクセス レベルに応じて、ジェネリック型内のコードできないことがありますへのアクセスします。</span><span class="sxs-lookup"><span data-stu-id="233b8-141">A type that implements interfaces does not necessarily expose a constructor, and depending on the access level of a constructor, the code within the generic type might not be able to access it.</span></span>  
  
    -   <span data-ttu-id="233b8-142">いずれか、`Class`キーワードまたは`Structure`キーワード。</span><span class="sxs-lookup"><span data-stu-id="233b8-142">Either the `Class` keyword or the `Structure` keyword.</span></span> <span data-ttu-id="233b8-143">`Class`キーワードは、すべての型引数が渡された文字列、配列、またはデリゲート、たとえば、参照型であること、またはクラスから作成されたオブジェクトを必要とするジェネリック型パラメーターを制約します。</span><span class="sxs-lookup"><span data-stu-id="233b8-143">The `Class` keyword constrains a generic type parameter to require that any type argument passed to it be a reference type, for example a string, array, or delegate, or an object created from a class.</span></span> <span data-ttu-id="233b8-144">`Structure`キーワードは、たとえば構造体、列挙型、または基本データ型をすべての型引数が渡された値型であることを必要とするジェネリック型パラメーターに制約します。</span><span class="sxs-lookup"><span data-stu-id="233b8-144">The `Structure` keyword constrains a generic type parameter to require that any type argument passed to it be a value type, for example a structure, enumeration, or elementary data type.</span></span> <span data-ttu-id="233b8-145">両方を含めることはできません`Class`と`Structure`同じ`constraintlist`です。</span><span class="sxs-lookup"><span data-stu-id="233b8-145">You cannot include both `Class` and `Structure` in the same `constraintlist`.</span></span>  
  
     <span data-ttu-id="233b8-146">指定された型に含めるすべての要件を満たす必要があります`constraintlist`です。</span><span class="sxs-lookup"><span data-stu-id="233b8-146">The supplied type must satisfy every requirement you include in `constraintlist`.</span></span>  
  
     <span data-ttu-id="233b8-147">それぞれの型パラメーターに対する制約は、その他の型パラメーターの制約の依存しません。</span><span class="sxs-lookup"><span data-stu-id="233b8-147">Constraints on each type parameter are independent of constraints on other type parameters.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="233b8-148">動作</span><span class="sxs-lookup"><span data-stu-id="233b8-148">Behavior</span></span>  
  
-   <span data-ttu-id="233b8-149">**コンパイル時の代入。**</span><span class="sxs-lookup"><span data-stu-id="233b8-149">**Compile-Time Substitution.**</span></span> <span data-ttu-id="233b8-150">汎用のプログラミング要素から構築された型を作成する場合は、それぞれの型パラメーターの定義済みの型を指定します。</span><span class="sxs-lookup"><span data-stu-id="233b8-150">When you create a constructed type from a generic programming element, you supply a defined type for each type parameter.</span></span> <span data-ttu-id="233b8-151">Visual Basic コンパイラごとに出現する位置を指定する型で置き換え`typename`内のジェネリックな要素です。</span><span class="sxs-lookup"><span data-stu-id="233b8-151">The Visual Basic compiler substitutes that supplied type for every occurrence of `typename` within the generic element.</span></span>  
  
-   <span data-ttu-id="233b8-152">**制約が存在しない場合。**</span><span class="sxs-lookup"><span data-stu-id="233b8-152">**Absence of Constraints.**</span></span> <span data-ttu-id="233b8-153">コードは操作およびでサポートされているメンバーに限定型パラメーターに対する制約を指定しない場合、[オブジェクト データ型](../../../visual-basic/language-reference/data-types/object-data-type.md)その型パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="233b8-153">If you do not specify any constraints on a type parameter, your code is limited to the operations and members supported by the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md) for that type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="233b8-154">例</span><span class="sxs-lookup"><span data-stu-id="233b8-154">Example</span></span>  
 <span data-ttu-id="233b8-155">次の例では、ディクショナリに新しいエントリを追加する関数の骨組みをなどのジェネリック ディクショナリ クラスのスケルトン定義を示します。</span><span class="sxs-lookup"><span data-stu-id="233b8-155">The following example shows a skeleton definition of a generic dictionary class, including a skeleton function to add a new entry to the dictionary.</span></span>  
  
 [!code-vb[VbVbalrStatements#3](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="233b8-156">例</span><span class="sxs-lookup"><span data-stu-id="233b8-156">Example</span></span>  
 <span data-ttu-id="233b8-157">`dictionary`はジェネリックでそれを使用するコードから作成できますのさまざまなオブジェクト、同じ機能を持つが、別のデータ型で動作している各します。</span><span class="sxs-lookup"><span data-stu-id="233b8-157">Because `dictionary` is generic, the code that uses it can create a variety of objects from it, each having the same functionality but acting on a different data type.</span></span> <span data-ttu-id="233b8-158">次の例は、行のコードを作成する、`dictionary`オブジェクト`String`エントリと`Integer`キー。</span><span class="sxs-lookup"><span data-stu-id="233b8-158">The following example shows a line of code that creates a `dictionary` object with `String` entries and `Integer` keys.</span></span>  
  
 [!code-vb[VbVbalrStatements#4](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="233b8-159">例</span><span class="sxs-lookup"><span data-stu-id="233b8-159">Example</span></span>  
 <span data-ttu-id="233b8-160">次の例では、前の例によって生成された同等のスケルトン定義を示します。</span><span class="sxs-lookup"><span data-stu-id="233b8-160">The following example shows the equivalent skeleton definition generated by the preceding example.</span></span>  
  
 [!code-vb[VbVbalrStatements#5](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="233b8-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="233b8-161">See Also</span></span>  
 [<span data-ttu-id="233b8-162">Of</span><span class="sxs-lookup"><span data-stu-id="233b8-162">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)  
 [<span data-ttu-id="233b8-163">New 演算子</span><span class="sxs-lookup"><span data-stu-id="233b8-163">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)  
 [<span data-ttu-id="233b8-164">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="233b8-164">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="233b8-165">Object 型</span><span class="sxs-lookup"><span data-stu-id="233b8-165">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="233b8-166">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="233b8-166">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="233b8-167">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="233b8-167">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="233b8-168">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="233b8-168">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="233b8-169">方法 : ジェネリック クラスを使用する</span><span class="sxs-lookup"><span data-stu-id="233b8-169">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="233b8-170">共変性と反変性</span><span class="sxs-lookup"><span data-stu-id="233b8-170">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [<span data-ttu-id="233b8-171">In</span><span class="sxs-lookup"><span data-stu-id="233b8-171">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [<span data-ttu-id="233b8-172">Out</span><span class="sxs-lookup"><span data-stu-id="233b8-172">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
