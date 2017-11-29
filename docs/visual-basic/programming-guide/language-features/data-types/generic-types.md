---
title: "Visual Basic におけるジェネリック型 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- generic interfaces
- data type arguments [Visual Basic], defining
- generic delegates
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- delegates, generic
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- procedures [Visual Basic], generic
- generic procedures
- data types [Visual Basic], generic
- data types [Visual Basic], as parameters
- generics [Visual Basic], generic types
- data types [Visual Basic], as arguments
- generic classes [Visual Basic], Visual Basic
- parameters [Visual Basic], type
- type arguments
- interfaces [Visual Basic], generic
- generics [Visual Basic]
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generic structures [Visual Basic]
- generic classes [Visual Basic]
- type parameters
- data type arguments
- structures [Visual Basic], generic
- parameters [Visual Basic], data type
- collections, generic
- classes [Visual Basic], generic
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 89f771d9-ecbb-4737-88b8-116b63c6cf4d
caps.latest.revision: "45"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 463391da61cbafe1f50a246307994cfa134dba38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="generic-types-in-visual-basic-visual-basic"></a><span data-ttu-id="2220e-102">Visual Basic におけるジェネリック型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2220e-102">Generic Types in Visual Basic (Visual Basic)</span></span>
<span data-ttu-id="2220e-103">*ジェネリック型* はさまざまなデータ型に対して同じ機能を実行するために必要な処理を行う、1 つのプログラミング要素です。</span><span class="sxs-lookup"><span data-stu-id="2220e-103">A *generic type* is a single programming element that adapts to perform the same functionality for a variety of data types.</span></span> <span data-ttu-id="2220e-104">ジェネリック クラスまたはジェネリック プロシージャを定義すると、同じ機能を実行させる各データ型に対して、その機能を別々に定義する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="2220e-104">When you define a generic class or procedure, you do not have to define a separate version for each data type for which you might want to perform that functionality.</span></span>  
  
 <span data-ttu-id="2220e-105">これは、ヘッドの部分が交換可能な、ねじ回しのセットにたとえることができます。</span><span class="sxs-lookup"><span data-stu-id="2220e-105">An analogy is a screwdriver set with removable heads.</span></span> <span data-ttu-id="2220e-106">回すねじを調べて、そのねじに合った正しいヘッド (マイナス、プラス、星型) を選択します。</span><span class="sxs-lookup"><span data-stu-id="2220e-106">You inspect the screw you need to turn and select the correct head for that screw (slotted, crossed, starred).</span></span> <span data-ttu-id="2220e-107">ねじ回しのハンドルに正しいヘッドを挿入したら、ねじ回しを使ってまったく同じ作業 (ねじを回すこと) を行います。</span><span class="sxs-lookup"><span data-stu-id="2220e-107">Once you insert the correct head in the screwdriver handle, you perform the exact same function with the screwdriver, namely turning the screw.</span></span>  
  
 <span data-ttu-id="2220e-108">![汎用ツールとして設定されたスクリュー ドライバーのダイアグラム](../../../../visual-basic/programming-guide/language-features/data-types/media/genericscrewdriver.gif "GenericScrewDriver")</span><span class="sxs-lookup"><span data-stu-id="2220e-108">![Diagram of a screwdriver set as a generic tool](../../../../visual-basic/programming-guide/language-features/data-types/media/genericscrewdriver.gif "GenericScrewDriver")</span></span>  
<span data-ttu-id="2220e-109">汎用的な道具であるねじ回しのセット</span><span class="sxs-lookup"><span data-stu-id="2220e-109">Screwdriver set as a generic tool</span></span>  
  
 <span data-ttu-id="2220e-110">ジェネリック型を定義する場合は、1 つ以上のデータ型でジェネリック型をパラメーター化します。</span><span class="sxs-lookup"><span data-stu-id="2220e-110">When you define a generic type, you parameterize it with one or more data types.</span></span> <span data-ttu-id="2220e-111">これにより、ジェネリック型を使用するコードで、データ型をコードの要件に合わせて変更できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2220e-111">This allows the using code to tailor the data types to its requirements.</span></span> <span data-ttu-id="2220e-112">コードでは、1 つのジェネリックな要素から複数のプログラミング要素を宣言し、それぞれを異なるデータ型のセットに使用できます。</span><span class="sxs-lookup"><span data-stu-id="2220e-112">Your code can declare several different programming elements from the generic element, each one acting on a different set of data types.</span></span> <span data-ttu-id="2220e-113">ただし、使用するデータ型が異なっていても、宣言した要素はどれも同じロジックを実行します。</span><span class="sxs-lookup"><span data-stu-id="2220e-113">But the declared elements all perform the identical logic, no matter what data types they are using.</span></span>  
  
 <span data-ttu-id="2220e-114">たとえば、 `String`などの特定のデータ型を操作するキュー クラスを作成し、使用する必要があるとします。</span><span class="sxs-lookup"><span data-stu-id="2220e-114">For example, you might want to create and use a queue class that operates on a specific data type such as `String`.</span></span> <span data-ttu-id="2220e-115">クラスを宣言する<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>次の例を示します。</span><span class="sxs-lookup"><span data-stu-id="2220e-115">You can declare such a class from <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#1](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_1.vb)]  
  
 <span data-ttu-id="2220e-116">このときに、 `stringQ` を使って、 `String` 値だけを扱うように指定できます。</span><span class="sxs-lookup"><span data-stu-id="2220e-116">You can now use `stringQ` to work exclusively with `String` values.</span></span> <span data-ttu-id="2220e-117">`stringQ` は、 `String` 値を汎用的に扱うのではなく `Object` だけを扱うことを意味するので、遅延バインディングまたは型変換は行いません。</span><span class="sxs-lookup"><span data-stu-id="2220e-117">Because `stringQ` is specific for `String` instead of being generalized for `Object` values, you do not have late binding or type conversion.</span></span> <span data-ttu-id="2220e-118">その結果、実行時間が短縮され、ランタイム エラーが減少します。</span><span class="sxs-lookup"><span data-stu-id="2220e-118">This saves execution time and reduces run-time errors.</span></span>  
  
 <span data-ttu-id="2220e-119">ジェネリック型の使い方の詳細については、「 [How to: Use a Generic Class](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2220e-119">For more information on using a generic type, see [How to: Use a Generic Class](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md).</span></span>  
  
## <a name="example-of-a-generic-class"></a><span data-ttu-id="2220e-120">ジェネリック クラスの例</span><span class="sxs-lookup"><span data-stu-id="2220e-120">Example of a Generic Class</span></span>  
 <span data-ttu-id="2220e-121">次の例は、ジェネリック クラスのスケルトン定義を示しています。</span><span class="sxs-lookup"><span data-stu-id="2220e-121">The following example shows a skeleton definition of a generic class.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#2](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_2.vb)]  
  
 <span data-ttu-id="2220e-122">このスケルトンでは、 `t` は *型パラメーター*です。これはプレースホルダーなので、このクラスを宣言するときにはデータ型で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="2220e-122">In the preceding skeleton, `t` is a *type parameter*, that is, a placeholder for a data type that you supply when you declare the class.</span></span> <span data-ttu-id="2220e-123">コードの他の部分では、 `classHolder` をさまざまなデータ型で置き換えることにより、 `t`のさまざまなバージョンを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="2220e-123">Elsewhere in your code, you can declare various versions of `classHolder` by supplying various data types for `t`.</span></span> <span data-ttu-id="2220e-124">このようにして宣言した 2 つのクラスを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="2220e-124">The following example shows two such declarations.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#3](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_3.vb)]  
  
 <span data-ttu-id="2220e-125">このステートメントでは、 *構成されるクラス*を宣言し、その中で型パラメーターを特定の型に置き換えています。</span><span class="sxs-lookup"><span data-stu-id="2220e-125">The preceding statements declare *constructed classes*, in which a specific type replaces the type parameter.</span></span> <span data-ttu-id="2220e-126">この置き換えは、構成されるクラスのコード全体に反映されます。</span><span class="sxs-lookup"><span data-stu-id="2220e-126">This replacement is propagated throughout the code within the constructed class.</span></span> <span data-ttu-id="2220e-127">次の例は、 `processNewItem` の `integerClass`プロシージャがどのようなコードになるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="2220e-127">The following example shows what the `processNewItem` procedure looks like in `integerClass`.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#4](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_4.vb)]  
  
 <span data-ttu-id="2220e-128">完全な例では、次を参照してください。[する方法: 機能を定義する、クラス、ことができます提供と同じ別のデータ型に](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)です。</span><span class="sxs-lookup"><span data-stu-id="2220e-128">For a more complete example, see [How to: Define a Class That Can Provide Identical Functionality on Different Data Types](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md).</span></span>  
  
## <a name="eligible-programming-elements"></a><span data-ttu-id="2220e-129">使用できるプログラミング要素</span><span class="sxs-lookup"><span data-stu-id="2220e-129">Eligible Programming Elements</span></span>  
 <span data-ttu-id="2220e-130">ジェネリック クラス、構造体、インターフェイス、プロシージャ、およびデリゲートを定義して使用することができます。</span><span class="sxs-lookup"><span data-stu-id="2220e-130">You can define and use generic classes, structures, interfaces, procedures, and delegates.</span></span> <span data-ttu-id="2220e-131">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] では、よく使われるジェネリックな要素を表すジェネリックのクラス、構造体、インターフェイスが定義されています。</span><span class="sxs-lookup"><span data-stu-id="2220e-131">Note that the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] defines several generic classes, structures, and interfaces that represent commonly used generic elements.</span></span> <span data-ttu-id="2220e-132"><xref:System.Collections.Generic?displayProperty=nameWithType>名前空間は、ディクショナリ、リスト、キュー、およびスタックを提供します。</span><span class="sxs-lookup"><span data-stu-id="2220e-132">The <xref:System.Collections.Generic?displayProperty=nameWithType> namespace provides dictionaries, lists, queues, and stacks.</span></span> <span data-ttu-id="2220e-133">独自のジェネリックな要素を定義するには、前に参照で使用可能なかどうかには既に<xref:System.Collections.Generic?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="2220e-133">Before defining your own generic element, see if it is already available in <xref:System.Collections.Generic?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="2220e-134">プロシージャは型ではありませんが、ジェネリック プロシージャを定義し、使用できます。</span><span class="sxs-lookup"><span data-stu-id="2220e-134">Procedures are not types, but you can define and use generic procedures.</span></span> <span data-ttu-id="2220e-135">「 [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2220e-135">See [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span></span>  
  
## <a name="advantages-of-generic-types"></a><span data-ttu-id="2220e-136">ジェネリック型の利点</span><span class="sxs-lookup"><span data-stu-id="2220e-136">Advantages of Generic Types</span></span>  
 <span data-ttu-id="2220e-137">ジェネリック型は、それぞれが特定のデータ型を操作する複数のプログラミング要素を宣言するための基礎となります。</span><span class="sxs-lookup"><span data-stu-id="2220e-137">A generic type serves as a basis for declaring several different programming elements, each of which operates on a specific data type.</span></span> <span data-ttu-id="2220e-138">ジェネリック型の代わりになるものを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="2220e-138">The alternatives to a generic type are:</span></span>  
  
1.  <span data-ttu-id="2220e-139">`Object` データ型を操作する単一の型。</span><span class="sxs-lookup"><span data-stu-id="2220e-139">A single type operating on the `Object` data type.</span></span>  
  
2.  <span data-ttu-id="2220e-140">型の *型固有* バージョンのセット。それぞれのバージョンは、個別にコーディングされ、 `String`、 `Integer`、または `customer`などのユーザー定義型などの特定のデータ型を操作します。</span><span class="sxs-lookup"><span data-stu-id="2220e-140">A set of *type-specific* versions of the type, each version individually coded and operating on one specific data type such as `String`, `Integer`, or a user-defined type such as `customer`.</span></span>  
  
 <span data-ttu-id="2220e-141">ジェネリック型には、これらの代替手段にはない次の利点があります。</span><span class="sxs-lookup"><span data-stu-id="2220e-141">A generic type has the following advantages over these alternatives:</span></span>  
  
-   <span data-ttu-id="2220e-142">**タイプ セーフ。**</span><span class="sxs-lookup"><span data-stu-id="2220e-142">**Type Safety.**</span></span> <span data-ttu-id="2220e-143">ジェネリック型では、コンパイル時に型がチェックされます。</span><span class="sxs-lookup"><span data-stu-id="2220e-143">Generic types enforce compile-time type checking.</span></span> <span data-ttu-id="2220e-144">一方、 `Object` に基づく型はすべてのデータ型を受け入れるので、入力したデータ型が受け入れられる型かどうかをチェックするコードを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2220e-144">Types based on `Object` accept any data type, and you must write code to check whether an input data type is acceptable.</span></span> <span data-ttu-id="2220e-145">ジェネリック型を使うと、型の不一致は実行する前にコンパイラで検出できます。</span><span class="sxs-lookup"><span data-stu-id="2220e-145">With generic types, the compiler can catch type mismatches before run time.</span></span>  
  
-   <span data-ttu-id="2220e-146">**パフォーマンス。**</span><span class="sxs-lookup"><span data-stu-id="2220e-146">**Performance.**</span></span> <span data-ttu-id="2220e-147">それぞれが特定の 1 つのデータ型に特化されるので、データを *ボックス化* したり、 *ボックス化を解除* したりする必要がありません。</span><span class="sxs-lookup"><span data-stu-id="2220e-147">Generic types do not have to *box* and *unbox* data, because each one is specialized for one data type.</span></span> <span data-ttu-id="2220e-148">`Object` に基づいて操作を実行する場合、入力したデータ型をボックス化して `Object` に変換したり、出力時にデータのボックス化を解除したりする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2220e-148">Operations based on `Object` must box input data types to convert them to `Object` and unbox data destined for output.</span></span> <span data-ttu-id="2220e-149">ボックス化とボックス化解除は、パフォーマンスを低下させます。</span><span class="sxs-lookup"><span data-stu-id="2220e-149">Boxing and unboxing reduce performance.</span></span>  
  
     <span data-ttu-id="2220e-150">また、 `Object` に基づく型は遅延バインディングでもあります。つまり、この型のメンバーにアクセスするには、実行時に余分なコードが必要になります。</span><span class="sxs-lookup"><span data-stu-id="2220e-150">Types based on `Object` are also late-bound, which means that accessing their members requires extra code at run time.</span></span> <span data-ttu-id="2220e-151">これも、パフォーマンスを低下させます。</span><span class="sxs-lookup"><span data-stu-id="2220e-151">This also reduces performance.</span></span>  
  
-   <span data-ttu-id="2220e-152">**コードの統合。**</span><span class="sxs-lookup"><span data-stu-id="2220e-152">**Code Consolidation.**</span></span> <span data-ttu-id="2220e-153">ジェネリック型のコードの定義は、一度だけ行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="2220e-153">The code in a generic type has to be defined only once.</span></span> <span data-ttu-id="2220e-154">1 つの型の一連の型固有バージョンでは、同じコードが各バージョンに複製されます。バージョンによって異なるのは、扱うデータ型だけです。</span><span class="sxs-lookup"><span data-stu-id="2220e-154">A set of type-specific versions of a type must replicate the same code in each version, with the only difference being the specific data type for that version.</span></span> <span data-ttu-id="2220e-155">ジェネリック型では、すべての型固有バージョンが元のジェネリック型から生成されます。</span><span class="sxs-lookup"><span data-stu-id="2220e-155">With generic types, the type-specific versions are all generated from the original generic type.</span></span>  
  
-   <span data-ttu-id="2220e-156">**コードの再利用。**</span><span class="sxs-lookup"><span data-stu-id="2220e-156">**Code Reuse.**</span></span> <span data-ttu-id="2220e-157">特定のデータ型に依存しないコードは、ジェネリックである場合に、さまざまなデータ型で再利用できます。</span><span class="sxs-lookup"><span data-stu-id="2220e-157">Code that does not depend on a particular data type can be reused with various data types if it is generic.</span></span> <span data-ttu-id="2220e-158">予期しなかったデータ型に再利用できることもあります。</span><span class="sxs-lookup"><span data-stu-id="2220e-158">You can often reuse it even with a data type that you did not originally predict.</span></span>  
  
-   <span data-ttu-id="2220e-159">**IDE サポート。**</span><span class="sxs-lookup"><span data-stu-id="2220e-159">**IDE Support.**</span></span> <span data-ttu-id="2220e-160">ジェネリック型から宣言した構成型を使用すると、コードの開発中に統合開発環境 (IDE) から提供されるサポートが増えます。</span><span class="sxs-lookup"><span data-stu-id="2220e-160">When you use a constructed type declared from a generic type, the integrated development environment (IDE) can give you more support while you are developing your code.</span></span> <span data-ttu-id="2220e-161">たとえば、IntelliSense は、コンストラクターまたはメソッドに対して引数の型固有のオプションを示します。</span><span class="sxs-lookup"><span data-stu-id="2220e-161">For example, IntelliSense can show you the type-specific options for an argument to a constructor or method.</span></span>  
  
-   <span data-ttu-id="2220e-162">**ジェネリックなアルゴリズム。**</span><span class="sxs-lookup"><span data-stu-id="2220e-162">**Generic Algorithms.**</span></span> <span data-ttu-id="2220e-163">型に依存しない抽象アルゴリズムは、ジェネリック型にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2220e-163">Abstract algorithms that are type-independent are good candidates for generic types.</span></span> <span data-ttu-id="2220e-164">たとえば、 <xref:System.IComparable> インターフェイスを使って項目を並べ替えるジェネリック プロシージャは、 <xref:System.IComparable>を実装する任意のデータ型に使用できます。</span><span class="sxs-lookup"><span data-stu-id="2220e-164">For example, a generic procedure that sorts items using the <xref:System.IComparable> interface can be used with any data type that implements <xref:System.IComparable>.</span></span>  
  
## <a name="constraints"></a><span data-ttu-id="2220e-165">制約</span><span class="sxs-lookup"><span data-stu-id="2220e-165">Constraints</span></span>  
 <span data-ttu-id="2220e-166">ジェネリック型定義のコードはできる限り型に依存しない必要がありますが、なんらかのデータ型の機能がジェネリック型に必要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="2220e-166">Although the code in a generic type definition should be as type-independent as possible, you might need to require a certain capability of any data type supplied to your generic type.</span></span> <span data-ttu-id="2220e-167">たとえば、並べ替えや照合順序のために 2 つの項目を比較する必要がある場合、それらのデータ型は <xref:System.IComparable> インターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2220e-167">For example, if you want to compare two items for the purpose of sorting or collating, their data type must implement the <xref:System.IComparable> interface.</span></span> <span data-ttu-id="2220e-168">この要件を強制するには、 *制約* を型パラメーターに追加します。</span><span class="sxs-lookup"><span data-stu-id="2220e-168">You can enforce this requirement by adding a *constraint* to the type parameter.</span></span>  
  
### <a name="example-of-a-constraint"></a><span data-ttu-id="2220e-169">制約の例</span><span class="sxs-lookup"><span data-stu-id="2220e-169">Example of a Constraint</span></span>  
 <span data-ttu-id="2220e-170">次の例は、 <xref:System.IComparable>の実装を型引数に強制する制約があるクラスのスケルトン定義を示しています。</span><span class="sxs-lookup"><span data-stu-id="2220e-170">The following example shows a skeleton definition of a class with a constraint that requires the type argument to implement <xref:System.IComparable>.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#5](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_5.vb)]  
  
 <span data-ttu-id="2220e-171">後続のコードで、 `itemManager` を実装しない型を渡して <xref:System.IComparable>からクラスを作成しようとすると、コンパイラがエラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="2220e-171">If subsequent code attempts to construct a class from `itemManager` supplying a type that does not implement <xref:System.IComparable>, the compiler signals an error.</span></span>  
  
### <a name="types-of-constraints"></a><span data-ttu-id="2220e-172">制約の種類</span><span class="sxs-lookup"><span data-stu-id="2220e-172">Types of Constraints</span></span>  
 <span data-ttu-id="2220e-173">次の要件を任意に組み合わせて制約を指定できます。</span><span class="sxs-lookup"><span data-stu-id="2220e-173">Your constraint can specify the following requirements in any combination:</span></span>  
  
-   <span data-ttu-id="2220e-174">型引数は、1 つまたは複数のインターフェイスを実装する必要があります</span><span class="sxs-lookup"><span data-stu-id="2220e-174">The type argument must implement one or more interfaces</span></span>  
  
-   <span data-ttu-id="2220e-175">型引数は、クラスの型そのものであるか、最大 1 つのクラスを継承する必要があります</span><span class="sxs-lookup"><span data-stu-id="2220e-175">The type argument must be of the type of, or inherit from, at most one class</span></span>  
  
-   <span data-ttu-id="2220e-176">型引数はパラメーターなしのコンストラクターを公開し、そのコンストラクターからオブジェクトを作成するコードで使用できる必要があります</span><span class="sxs-lookup"><span data-stu-id="2220e-176">The type argument must expose a parameterless constructor accessible to the code that creates objects from it</span></span>  
  
-   <span data-ttu-id="2220e-177">型引数は、 *参照型*である、または *値型*である必要があります</span><span class="sxs-lookup"><span data-stu-id="2220e-177">The type argument must be a *reference type*, or it must be a *value type*</span></span>  
  
 <span data-ttu-id="2220e-178">複数の要件を指定する場合は、コンマで区切られた *制約リスト* を中かっこ (`{ }`) で囲みます。</span><span class="sxs-lookup"><span data-stu-id="2220e-178">If you need to impose more than one requirement, you use a comma-separated *constraint list* inside braces (`{ }`).</span></span> <span data-ttu-id="2220e-179">アクセス可能なコンス トラクターを必要とする追加の[New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)リスト内のキーワードです。</span><span class="sxs-lookup"><span data-stu-id="2220e-179">To require an accessible constructor, you include the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword in the list.</span></span> <span data-ttu-id="2220e-180">参照型であることを必須とするには、 `Class` キーワードを追加し、値型であることを必須とするには、 `Structure` キーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="2220e-180">To require a reference type, you include the `Class` keyword; to require a value type, you include the `Structure` keyword.</span></span>  
  
 <span data-ttu-id="2220e-181">制約の詳細については、「 [Type List](../../../../visual-basic/language-reference/statements/type-list.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2220e-181">For more information on constraints, see [Type List](../../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
### <a name="example-of-multiple-constraints"></a><span data-ttu-id="2220e-182">複数の制約の例</span><span class="sxs-lookup"><span data-stu-id="2220e-182">Example of Multiple Constraints</span></span>  
 <span data-ttu-id="2220e-183">次の例は、型パラメーターに制約リストがあるジェネリック クラスのスケルトン定義を示しています。</span><span class="sxs-lookup"><span data-stu-id="2220e-183">The following example shows a skeleton definition of a generic class with a constraint list on the type parameter.</span></span> <span data-ttu-id="2220e-184">このクラスのインスタンスを作成するコードでは、型引数が <xref:System.IComparable> インターフェイスと <xref:System.IDisposable> インターフェイスの両方を実装し、参照型であり、アクセス可能なパラメーターなしのコンストラクターを公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2220e-184">In the code that creates an instance of this class, the type argument must implement both the <xref:System.IComparable> and <xref:System.IDisposable> interfaces, be a reference type, and expose an accessible parameterless constructor.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#6](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_6.vb)]  
  
## <a name="important-terms"></a><span data-ttu-id="2220e-185">重要な用語</span><span class="sxs-lookup"><span data-stu-id="2220e-185">Important Terms</span></span>  
 <span data-ttu-id="2220e-186">ジェネリック型に関連して、以下の新しい用語が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2220e-186">Generic types introduce and use the following terms:</span></span>  
  
-   <span data-ttu-id="2220e-187">*ジェネリック型*。</span><span class="sxs-lookup"><span data-stu-id="2220e-187">*Generic Type*.</span></span> <span data-ttu-id="2220e-188">宣言時に少なくとも 1 つのデータ型を指定するクラス、構造体、インターフェイス、プロシージャ、またはデリゲートの定義です。</span><span class="sxs-lookup"><span data-stu-id="2220e-188">A definition of a class, structure, interface, procedure, or delegate for which you supply at least one data type when you declare it.</span></span>  
  
-   <span data-ttu-id="2220e-189">*型パラメーター*。</span><span class="sxs-lookup"><span data-stu-id="2220e-189">*Type Parameter*.</span></span> <span data-ttu-id="2220e-190">ジェネリック型定義で、型を宣言するときにデータ型の代わりに指定するプレースホルダーです。</span><span class="sxs-lookup"><span data-stu-id="2220e-190">In a generic type definition, a placeholder for a data type you supply when you declare the type.</span></span>  
  
-   <span data-ttu-id="2220e-191">*型引数*。</span><span class="sxs-lookup"><span data-stu-id="2220e-191">*Type Argument*.</span></span> <span data-ttu-id="2220e-192">構成型をジェネリック型から宣言するときに、型パラメーターを置き換える特定のデータ型です。</span><span class="sxs-lookup"><span data-stu-id="2220e-192">A specific data type that replaces a type parameter when you declare a constructed type from a generic type.</span></span>  
  
-   <span data-ttu-id="2220e-193">*制約*。</span><span class="sxs-lookup"><span data-stu-id="2220e-193">*Constraint*.</span></span> <span data-ttu-id="2220e-194">型パラメーターに指定できる型引数を制限する条件です。</span><span class="sxs-lookup"><span data-stu-id="2220e-194">A condition on a type parameter that restricts the type argument you can supply for it.</span></span> <span data-ttu-id="2220e-195">型引数が特定のインターフェイスを実装すること、特定のクラスであるか特定のクラスを継承すること、アクセス可能なパラメーターなしのコンストラクターを持つこと、または参照型または値型であることを強制できます。</span><span class="sxs-lookup"><span data-stu-id="2220e-195">A constraint can require that the type argument must implement a particular interface, be or inherit from a particular class, have an accessible parameterless constructor, or be a reference type or a value type.</span></span> <span data-ttu-id="2220e-196">このような制約は組み合わせて指定できますが、指定できるのは 1 つのクラスだけです。</span><span class="sxs-lookup"><span data-stu-id="2220e-196">You can combine these constraints, but you can specify at most one class.</span></span>  
  
-   <span data-ttu-id="2220e-197">*構成型*。</span><span class="sxs-lookup"><span data-stu-id="2220e-197">*Constructed Type*.</span></span> <span data-ttu-id="2220e-198">型パラメーターに型引数を指定してジェネリック型から宣言されるクラス、構造体、インターフェイス、プロシージャ、またはデリゲートです。</span><span class="sxs-lookup"><span data-stu-id="2220e-198">A class, structure, interface, procedure, or delegate declared from a generic type by supplying type arguments for its type parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2220e-199">関連項目</span><span class="sxs-lookup"><span data-stu-id="2220e-199">See Also</span></span>  
 [<span data-ttu-id="2220e-200">データの種類</span><span class="sxs-lookup"><span data-stu-id="2220e-200">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="2220e-201">型文字</span><span class="sxs-lookup"><span data-stu-id="2220e-201">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [<span data-ttu-id="2220e-202">値型と参照型</span><span class="sxs-lookup"><span data-stu-id="2220e-202">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="2220e-203">Visual Basic での型変換</span><span class="sxs-lookup"><span data-stu-id="2220e-203">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="2220e-204">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="2220e-204">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="2220e-205">データの種類</span><span class="sxs-lookup"><span data-stu-id="2220e-205">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="2220e-206">Of</span><span class="sxs-lookup"><span data-stu-id="2220e-206">Of</span></span>](../../../../visual-basic/language-reference/statements/of-clause.md)  
 [<span data-ttu-id="2220e-207">As</span><span class="sxs-lookup"><span data-stu-id="2220e-207">As</span></span>](../../../../visual-basic/language-reference/statements/as-clause.md)  
 [<span data-ttu-id="2220e-208">Object 型</span><span class="sxs-lookup"><span data-stu-id="2220e-208">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="2220e-209">共変性と反変性</span><span class="sxs-lookup"><span data-stu-id="2220e-209">Covariance and Contravariance</span></span>](../../concepts/covariance-contravariance/index.md)  
 [<span data-ttu-id="2220e-210">反復子</span><span class="sxs-lookup"><span data-stu-id="2220e-210">Iterators</span></span>](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)
