---
title: "Visual Basic (Visual Basic) におけるジェネリック型 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- generic interfaces
- data type arguments, defining
- generic delegates
- arguments [Visual Basic], data types
- Of keyword, using
- delegates, generic
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- procedures, generic
- generic procedures
- data types [Visual Basic], generic
- data types [Visual Basic], as parameters
- generics [Visual Basic], generic types
- data types [Visual Basic], as arguments
- generic classes, Visual Basic
- parameters, type
- type arguments
- interfaces, generic
- generics [Visual Basic]
- types [Visual Basic], generic
- parameters, generic
- generic structures
- generic classes
- type parameters
- data type arguments
- structures, generic
- parameters, data type
- collections, generic
- classes [Visual Basic], generic
- data type parameters, defining
- type arguments, defining
- arguments [Visual Basic], type
ms.assetid: 89f771d9-ecbb-4737-88b8-116b63c6cf4d
caps.latest.revision: 45
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 40b175655b2b2341fd15e763058a3dae1291f2c4
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="generic-types-in-visual-basic-visual-basic"></a><span data-ttu-id="d363b-102">Visual Basic におけるジェネリック型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d363b-102">Generic Types in Visual Basic (Visual Basic)</span></span>
<span data-ttu-id="d363b-103">*ジェネリック型* はさまざまなデータ型に対して同じ機能を実行するために必要な処理を行う、1 つのプログラミング要素です。</span><span class="sxs-lookup"><span data-stu-id="d363b-103">A *generic type* is a single programming element that adapts to perform the same functionality for a variety of data types.</span></span> <span data-ttu-id="d363b-104">ジェネリック クラスまたはジェネリック プロシージャを定義すると、同じ機能を実行させる各データ型に対して、その機能を別々に定義する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="d363b-104">When you define a generic class or procedure, you do not have to define a separate version for each data type for which you might want to perform that functionality.</span></span>  
  
 <span data-ttu-id="d363b-105">これは、ヘッドの部分が交換可能な、ねじ回しのセットにたとえることができます。</span><span class="sxs-lookup"><span data-stu-id="d363b-105">An analogy is a screwdriver set with removable heads.</span></span> <span data-ttu-id="d363b-106">回すねじを調べて、そのねじに合った正しいヘッド (マイナス、プラス、星型) を選択します。</span><span class="sxs-lookup"><span data-stu-id="d363b-106">You inspect the screw you need to turn and select the correct head for that screw (slotted, crossed, starred).</span></span> <span data-ttu-id="d363b-107">ねじ回しのハンドルに正しいヘッドを挿入したら、ねじ回しを使ってまったく同じ作業 (ねじを回すこと) を行います。</span><span class="sxs-lookup"><span data-stu-id="d363b-107">Once you insert the correct head in the screwdriver handle, you perform the exact same function with the screwdriver, namely turning the screw.</span></span>  
  
 <span data-ttu-id="d363b-108">![汎用ツールとして設定されたスクリュー ドライバーのダイアグラム](../../../../visual-basic/programming-guide/language-features/data-types/media/genericscrewdriver.gif "GenericScrewDriver")</span><span class="sxs-lookup"><span data-stu-id="d363b-108">![Diagram of a screwdriver set as a generic tool](../../../../visual-basic/programming-guide/language-features/data-types/media/genericscrewdriver.gif "GenericScrewDriver")</span></span>  
<span data-ttu-id="d363b-109">汎用的な道具であるねじ回しのセット</span><span class="sxs-lookup"><span data-stu-id="d363b-109">Screwdriver set as a generic tool</span></span>  
  
 <span data-ttu-id="d363b-110">ジェネリック型を定義する場合は、1 つ以上のデータ型でジェネリック型をパラメーター化します。</span><span class="sxs-lookup"><span data-stu-id="d363b-110">When you define a generic type, you parameterize it with one or more data types.</span></span> <span data-ttu-id="d363b-111">これにより、ジェネリック型を使用するコードで、データ型をコードの要件に合わせて変更できるようになります。</span><span class="sxs-lookup"><span data-stu-id="d363b-111">This allows the using code to tailor the data types to its requirements.</span></span> <span data-ttu-id="d363b-112">コードでは、1 つのジェネリックな要素から複数のプログラミング要素を宣言し、それぞれを異なるデータ型のセットに使用できます。</span><span class="sxs-lookup"><span data-stu-id="d363b-112">Your code can declare several different programming elements from the generic element, each one acting on a different set of data types.</span></span> <span data-ttu-id="d363b-113">ただし、使用するデータ型が異なっていても、宣言した要素はどれも同じロジックを実行します。</span><span class="sxs-lookup"><span data-stu-id="d363b-113">But the declared elements all perform the identical logic, no matter what data types they are using.</span></span>  
  
 <span data-ttu-id="d363b-114">たとえば、 `String`などの特定のデータ型を操作するキュー クラスを作成し、使用する必要があるとします。</span><span class="sxs-lookup"><span data-stu-id="d363b-114">For example, you might want to create and use a queue class that operates on a specific data type such as `String`.</span></span> <span data-ttu-id="d363b-115">クラスを宣言する<xref:System.Collections.Generic.Queue%601?displayProperty=fullName>次の例を示します</xref:System.Collections.Generic.Queue%601?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="d363b-115">You can declare such a class from <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>, as the following example shows.</span></span>  
  
 <span data-ttu-id="d363b-116">[!code-vb[VbVbalrDataTypes&#1;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d363b-116">[!code-vb[VbVbalrDataTypes#1](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_1.vb)]</span></span>  
  
 <span data-ttu-id="d363b-117">このときに、 `stringQ` を使って、 `String` 値だけを扱うように指定できます。</span><span class="sxs-lookup"><span data-stu-id="d363b-117">You can now use `stringQ` to work exclusively with `String` values.</span></span> <span data-ttu-id="d363b-118">`stringQ` は、 `String` 値を汎用的に扱うのではなく `Object` だけを扱うことを意味するので、遅延バインディングまたは型変換は行いません。</span><span class="sxs-lookup"><span data-stu-id="d363b-118">Because `stringQ` is specific for `String` instead of being generalized for `Object` values, you do not have late binding or type conversion.</span></span> <span data-ttu-id="d363b-119">その結果、実行時間が短縮され、ランタイム エラーが減少します。</span><span class="sxs-lookup"><span data-stu-id="d363b-119">This saves execution time and reduces run-time errors.</span></span>  
  
 <span data-ttu-id="d363b-120">ジェネリック型の使用に関する詳細については、次を参照してください。[方法: ジェネリック クラスを使用して](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)します。</span><span class="sxs-lookup"><span data-stu-id="d363b-120">For more information on using a generic type, see [How to: Use a Generic Class](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md).</span></span>  
  
## <a name="example-of-a-generic-class"></a><span data-ttu-id="d363b-121">ジェネリック クラスの例</span><span class="sxs-lookup"><span data-stu-id="d363b-121">Example of a Generic Class</span></span>  
 <span data-ttu-id="d363b-122">次の例は、ジェネリック クラスのスケルトン定義を示しています。</span><span class="sxs-lookup"><span data-stu-id="d363b-122">The following example shows a skeleton definition of a generic class.</span></span>  
  
 <span data-ttu-id="d363b-123">[!code-vb[VbVbalrDataTypes&#2;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="d363b-123">[!code-vb[VbVbalrDataTypes#2](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_2.vb)]</span></span>  
  
 <span data-ttu-id="d363b-124">このスケルトンでは、 `t` は *型パラメーター*です。これはプレースホルダーなので、このクラスを宣言するときにはデータ型で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="d363b-124">In the preceding skeleton, `t` is a *type parameter*, that is, a placeholder for a data type that you supply when you declare the class.</span></span> <span data-ttu-id="d363b-125">コードの他の部分では、 `classHolder` をさまざまなデータ型で置き換えることにより、 `t`のさまざまなバージョンを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="d363b-125">Elsewhere in your code, you can declare various versions of `classHolder` by supplying various data types for `t`.</span></span> <span data-ttu-id="d363b-126">このようにして宣言した&2; つのクラスを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="d363b-126">The following example shows two such declarations.</span></span>  
  
 <span data-ttu-id="d363b-127">[!code-vb[VbVbalrDataTypes&#3;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="d363b-127">[!code-vb[VbVbalrDataTypes#3](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_3.vb)]</span></span>  
  
 <span data-ttu-id="d363b-128">このステートメントでは、 *構成されるクラス*を宣言し、その中で型パラメーターを特定の型に置き換えています。</span><span class="sxs-lookup"><span data-stu-id="d363b-128">The preceding statements declare *constructed classes*, in which a specific type replaces the type parameter.</span></span> <span data-ttu-id="d363b-129">この置き換えは、構成されるクラスのコード全体に反映されます。</span><span class="sxs-lookup"><span data-stu-id="d363b-129">This replacement is propagated throughout the code within the constructed class.</span></span> <span data-ttu-id="d363b-130">次の例は、 `processNewItem` の `integerClass`プロシージャがどのようなコードになるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="d363b-130">The following example shows what the `processNewItem` procedure looks like in `integerClass`.</span></span>  
  
 <span data-ttu-id="d363b-131">[!code-vb[VbVbalrDataTypes&4;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="d363b-131">[!code-vb[VbVbalrDataTypes#4](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_4.vb)]</span></span>  
  
 <span data-ttu-id="d363b-132">完全な例では、次を参照してください。[方法: 機能を定義する、クラス、ことができます提供と同じ別のデータ型に](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)します。</span><span class="sxs-lookup"><span data-stu-id="d363b-132">For a more complete example, see [How to: Define a Class That Can Provide Identical Functionality on Different Data Types](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md).</span></span>  
  
## <a name="eligible-programming-elements"></a><span data-ttu-id="d363b-133">使用できるプログラミング要素</span><span class="sxs-lookup"><span data-stu-id="d363b-133">Eligible Programming Elements</span></span>  
 <span data-ttu-id="d363b-134">ジェネリック クラス、構造体、インターフェイス、プロシージャ、およびデリゲートを定義して使用することができます。</span><span class="sxs-lookup"><span data-stu-id="d363b-134">You can define and use generic classes, structures, interfaces, procedures, and delegates.</span></span> <span data-ttu-id="d363b-135">なお、[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]いくつかのジェネリック クラス、構造、およびよく使用される一般的な要素を表すインターフェイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="d363b-135">Note that the [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] defines several generic classes, structures, and interfaces that represent commonly used generic elements.</span></span> <span data-ttu-id="d363b-136"><xref:System.Collections.Generic?displayProperty=fullName>名前空間は、ディクショナリ、リスト、キュー、およびスタックを提供します</xref:System.Collections.Generic?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="d363b-136">The <xref:System.Collections.Generic?displayProperty=fullName> namespace provides dictionaries, lists, queues, and stacks.</span></span> <span data-ttu-id="d363b-137">独自のジェネリックな要素を定義する前に既に<xref:System.Collections.Generic?displayProperty=fullName>。</xref:System.Collections.Generic?displayProperty=fullName>で利用可能なかどうかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d363b-137">Before defining your own generic element, see if it is already available in <xref:System.Collections.Generic?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="d363b-138">プロシージャは型ではありませんが、ジェネリック プロシージャを定義し、使用できます。</span><span class="sxs-lookup"><span data-stu-id="d363b-138">Procedures are not types, but you can define and use generic procedures.</span></span> <span data-ttu-id="d363b-139">参照してください[Visual Basic におけるジェネリック プロシージャ](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)します。</span><span class="sxs-lookup"><span data-stu-id="d363b-139">See [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span></span>  
  
## <a name="advantages-of-generic-types"></a><span data-ttu-id="d363b-140">ジェネリック型の利点</span><span class="sxs-lookup"><span data-stu-id="d363b-140">Advantages of Generic Types</span></span>  
 <span data-ttu-id="d363b-141">ジェネリック型は、それぞれが特定のデータ型を操作する複数のプログラミング要素を宣言するための基礎となります。</span><span class="sxs-lookup"><span data-stu-id="d363b-141">A generic type serves as a basis for declaring several different programming elements, each of which operates on a specific data type.</span></span> <span data-ttu-id="d363b-142">ジェネリック型の代わりになるものを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="d363b-142">The alternatives to a generic type are:</span></span>  
  
1.  <span data-ttu-id="d363b-143">`Object` データ型を操作する単一の型。</span><span class="sxs-lookup"><span data-stu-id="d363b-143">A single type operating on the `Object` data type.</span></span>  
  
2.  <span data-ttu-id="d363b-144">型の *型固有* バージョンのセット。それぞれのバージョンは、個別にコーディングされ、 `String`、 `Integer`、または `customer`などのユーザー定義型などの特定のデータ型を操作します。</span><span class="sxs-lookup"><span data-stu-id="d363b-144">A set of *type-specific* versions of the type, each version individually coded and operating on one specific data type such as `String`, `Integer`, or a user-defined type such as `customer`.</span></span>  
  
 <span data-ttu-id="d363b-145">ジェネリック型には、これらの代替手段にはない次の利点があります。</span><span class="sxs-lookup"><span data-stu-id="d363b-145">A generic type has the following advantages over these alternatives:</span></span>  
  
-   <span data-ttu-id="d363b-146">**タイプ セーフです。**</span><span class="sxs-lookup"><span data-stu-id="d363b-146">**Type Safety.**</span></span> <span data-ttu-id="d363b-147">ジェネリック型では、コンパイル時に型がチェックされます。</span><span class="sxs-lookup"><span data-stu-id="d363b-147">Generic types enforce compile-time type checking.</span></span> <span data-ttu-id="d363b-148">一方、 `Object` に基づく型はすべてのデータ型を受け入れるので、入力したデータ型が受け入れられる型かどうかをチェックするコードを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d363b-148">Types based on `Object` accept any data type, and you must write code to check whether an input data type is acceptable.</span></span> <span data-ttu-id="d363b-149">ジェネリック型を使うと、型の不一致は実行する前にコンパイラで検出できます。</span><span class="sxs-lookup"><span data-stu-id="d363b-149">With generic types, the compiler can catch type mismatches before run time.</span></span>  
  
-   <span data-ttu-id="d363b-150">**パフォーマンスを改善。**</span><span class="sxs-lookup"><span data-stu-id="d363b-150">**Performance.**</span></span> <span data-ttu-id="d363b-151">それぞれが特定の&1; つのデータ型に特化されるので、データを *ボックス化* したり、 *unボックス化* したりする必要がありません。</span><span class="sxs-lookup"><span data-stu-id="d363b-151">Generic types do not have to *box* and *unbox* data, because each one is specialized for one data type.</span></span> <span data-ttu-id="d363b-152">`Object` に基づいて操作を実行する場合、入力したデータ型をボックス化して `Object` に変換したり、出力時にデータのボックス化を解除したりする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d363b-152">Operations based on `Object` must box input data types to convert them to `Object` and unbox data destined for output.</span></span> <span data-ttu-id="d363b-153">ボックス化とボックス化解除は、パフォーマンスを低下させます。</span><span class="sxs-lookup"><span data-stu-id="d363b-153">Boxing and unboxing reduce performance.</span></span>  
  
     <span data-ttu-id="d363b-154">また、 `Object` に基づく型は遅延バインディングでもあります。つまり、この型のメンバーにアクセスするには、実行時に余分なコードが必要になります。</span><span class="sxs-lookup"><span data-stu-id="d363b-154">Types based on `Object` are also late-bound, which means that accessing their members requires extra code at run time.</span></span> <span data-ttu-id="d363b-155">これも、パフォーマンスを低下させます。</span><span class="sxs-lookup"><span data-stu-id="d363b-155">This also reduces performance.</span></span>  
  
-   <span data-ttu-id="d363b-156">**コードの統合。**</span><span class="sxs-lookup"><span data-stu-id="d363b-156">**Code Consolidation.**</span></span> <span data-ttu-id="d363b-157">ジェネリック型のコードの定義は、一度だけ行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="d363b-157">The code in a generic type has to be defined only once.</span></span> <span data-ttu-id="d363b-158">1 つの型の一連の型固有バージョンでは、同じコードが各バージョンに複製されます。バージョンによって異なるのは、扱うデータ型だけです。</span><span class="sxs-lookup"><span data-stu-id="d363b-158">A set of type-specific versions of a type must replicate the same code in each version, with the only difference being the specific data type for that version.</span></span> <span data-ttu-id="d363b-159">ジェネリック型では、すべての型固有バージョンが元のジェネリック型から生成されます。</span><span class="sxs-lookup"><span data-stu-id="d363b-159">With generic types, the type-specific versions are all generated from the original generic type.</span></span>  
  
-   <span data-ttu-id="d363b-160">**コードの再利用をします。**</span><span class="sxs-lookup"><span data-stu-id="d363b-160">**Code Reuse.**</span></span> <span data-ttu-id="d363b-161">特定のデータ型に依存しないコードは、ジェネリックである場合に、さまざまなデータ型で再利用できます。</span><span class="sxs-lookup"><span data-stu-id="d363b-161">Code that does not depend on a particular data type can be reused with various data types if it is generic.</span></span> <span data-ttu-id="d363b-162">予期しなかったデータ型に再利用できることもあります。</span><span class="sxs-lookup"><span data-stu-id="d363b-162">You can often reuse it even with a data type that you did not originally predict.</span></span>  
  
-   <span data-ttu-id="d363b-163">**IDE のサポート。**</span><span class="sxs-lookup"><span data-stu-id="d363b-163">**IDE Support.**</span></span> <span data-ttu-id="d363b-164">ジェネリック型から宣言した構成型を使用すると、コードの開発中に統合開発環境 (IDE) から提供されるサポートが増えます。</span><span class="sxs-lookup"><span data-stu-id="d363b-164">When you use a constructed type declared from a generic type, the integrated development environment (IDE) can give you more support while you are developing your code.</span></span> <span data-ttu-id="d363b-165">たとえば、IntelliSense は、コンストラクターまたはメソッドに対して引数の型固有のオプションを示します。</span><span class="sxs-lookup"><span data-stu-id="d363b-165">For example, IntelliSense can show you the type-specific options for an argument to a constructor or method.</span></span>  
  
-   <span data-ttu-id="d363b-166">**ジェネリックなアルゴリズム。**</span><span class="sxs-lookup"><span data-stu-id="d363b-166">**Generic Algorithms.**</span></span> <span data-ttu-id="d363b-167">型に依存しない抽象アルゴリズムは、ジェネリック型にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d363b-167">Abstract algorithms that are type-independent are good candidates for generic types.</span></span> <span data-ttu-id="d363b-168"><xref:System.IComparable>インターフェイスを使用すると、 <xref:System.IComparable>。</xref:System.IComparable>を実装する任意のデータ型を</xref:System.IComparable>使用して項目を並べ替えてジェネリック プロシージャなど、</span><span class="sxs-lookup"><span data-stu-id="d363b-168">For example, a generic procedure that sorts items using the <xref:System.IComparable> interface can be used with any data type that implements <xref:System.IComparable>.</span></span>  
  
## <a name="constraints"></a><span data-ttu-id="d363b-169">制約</span><span class="sxs-lookup"><span data-stu-id="d363b-169">Constraints</span></span>  
 <span data-ttu-id="d363b-170">ジェネリック型定義のコードはできる限り型に依存しない必要がありますが、なんらかのデータ型の機能がジェネリック型に必要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="d363b-170">Although the code in a generic type definition should be as type-independent as possible, you might need to require a certain capability of any data type supplied to your generic type.</span></span> <span data-ttu-id="d363b-171">たとえば、並べ替えまたは照合するために&2; つの項目を比較する場合は、そのデータ型必要があります実装、<xref:System.IComparable>インターフェイス</xref:System.IComparable>。</span><span class="sxs-lookup"><span data-stu-id="d363b-171">For example, if you want to compare two items for the purpose of sorting or collating, their data type must implement the <xref:System.IComparable> interface.</span></span> <span data-ttu-id="d363b-172">この要件を強制するには、 *制約* を型パラメーターに追加します。</span><span class="sxs-lookup"><span data-stu-id="d363b-172">You can enforce this requirement by adding a *constraint* to the type parameter.</span></span>  
  
### <a name="example-of-a-constraint"></a><span data-ttu-id="d363b-173">制約の例</span><span class="sxs-lookup"><span data-stu-id="d363b-173">Example of a Constraint</span></span>  
 <span data-ttu-id="d363b-174">次の例は、 <xref:System.IComparable>。</xref:System.IComparable>を実装する型引数が必要な制約が設定されたクラスのスケルトンの定義を示しています。</span><span class="sxs-lookup"><span data-stu-id="d363b-174">The following example shows a skeleton definition of a class with a constraint that requires the type argument to implement <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="d363b-175">[!code-vb[VbVbalrDataTypes&#5;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="d363b-175">[!code-vb[VbVbalrDataTypes#5](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_5.vb)]</span></span>  
  
 <span data-ttu-id="d363b-176">後続のコードからクラスを作成しようとしました場合`itemManager`を実装しない型を指定して<xref:System.IComparable>、コンパイラはエラーです。</xref:System.IComparable> 。</span><span class="sxs-lookup"><span data-stu-id="d363b-176">If subsequent code attempts to construct a class from `itemManager` supplying a type that does not implement <xref:System.IComparable>, the compiler signals an error.</span></span>  
  
### <a name="types-of-constraints"></a><span data-ttu-id="d363b-177">制約の種類</span><span class="sxs-lookup"><span data-stu-id="d363b-177">Types of Constraints</span></span>  
 <span data-ttu-id="d363b-178">次の要件を任意に組み合わせて制約を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d363b-178">Your constraint can specify the following requirements in any combination:</span></span>  
  
-   <span data-ttu-id="d363b-179">型引数は、1 つまたは複数のインターフェイスを実装する必要があります</span><span class="sxs-lookup"><span data-stu-id="d363b-179">The type argument must implement one or more interfaces</span></span>  
  
-   <span data-ttu-id="d363b-180">型引数は、クラスの型そのものであるか、最大&1; つのクラスを継承する必要があります</span><span class="sxs-lookup"><span data-stu-id="d363b-180">The type argument must be of the type of, or inherit from, at most one class</span></span>  
  
-   <span data-ttu-id="d363b-181">型引数はパラメーターなしのコンストラクターを公開し、そのコンストラクターからオブジェクトを作成するコードで使用できる必要があります</span><span class="sxs-lookup"><span data-stu-id="d363b-181">The type argument must expose a parameterless constructor accessible to the code that creates objects from it</span></span>  
  
-   <span data-ttu-id="d363b-182">型引数は、 *参照型*である、または *値型*である必要があります</span><span class="sxs-lookup"><span data-stu-id="d363b-182">The type argument must be a *reference type*, or it must be a *value type*</span></span>  
  
 <span data-ttu-id="d363b-183">複数の要件を指定する場合は、コンマで区切られた *制約リスト* を中かっこ (`{ }`) で囲みます。</span><span class="sxs-lookup"><span data-stu-id="d363b-183">If you need to impose more than one requirement, you use a comma-separated *constraint list* inside braces (`{ }`).</span></span> <span data-ttu-id="d363b-184">含めるをアクセス可能なコンス トラクターを必要とする、 [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)一覧のキーワードです。</span><span class="sxs-lookup"><span data-stu-id="d363b-184">To require an accessible constructor, you include the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword in the list.</span></span> <span data-ttu-id="d363b-185">参照型であることを必須とするには、 `Class` キーワードを追加し、値型であることを必須とするには、 `Structure` キーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="d363b-185">To require a reference type, you include the `Class` keyword; to require a value type, you include the `Structure` keyword.</span></span>  
  
 <span data-ttu-id="d363b-186">制約の詳細については、次を参照してください。[型リスト](../../../../visual-basic/language-reference/statements/type-list.md)します。</span><span class="sxs-lookup"><span data-stu-id="d363b-186">For more information on constraints, see [Type List](../../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
### <a name="example-of-multiple-constraints"></a><span data-ttu-id="d363b-187">複数の制約の例</span><span class="sxs-lookup"><span data-stu-id="d363b-187">Example of Multiple Constraints</span></span>  
 <span data-ttu-id="d363b-188">次の例は、型パラメーターに制約リストがあるジェネリック クラスのスケルトン定義を示しています。</span><span class="sxs-lookup"><span data-stu-id="d363b-188">The following example shows a skeleton definition of a generic class with a constraint list on the type parameter.</span></span> <span data-ttu-id="d363b-189">をこのクラスのインスタンスを作成したコードで型引数必要があります両方を実装、<xref:System.IComparable>と<xref:System.IDisposable>インターフェイスの参照型であるし、アクセス可能なパラメーターなしコンス トラクターを公開します。</xref:System.IDisposable> </xref:System.IComparable></span><span class="sxs-lookup"><span data-stu-id="d363b-189">In the code that creates an instance of this class, the type argument must implement both the <xref:System.IComparable> and <xref:System.IDisposable> interfaces, be a reference type, and expose an accessible parameterless constructor.</span></span>  
  
 <span data-ttu-id="d363b-190">[!code-vb[VbVbalrDataTypes&6;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="d363b-190">[!code-vb[VbVbalrDataTypes#6](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_6.vb)]</span></span>  
  
## <a name="important-terms"></a><span data-ttu-id="d363b-191">重要な用語</span><span class="sxs-lookup"><span data-stu-id="d363b-191">Important Terms</span></span>  
 <span data-ttu-id="d363b-192">ジェネリック型に関連して、以下の新しい用語が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d363b-192">Generic types introduce and use the following terms:</span></span>  
  
-   <span data-ttu-id="d363b-193">*ジェネリック型*。</span><span class="sxs-lookup"><span data-stu-id="d363b-193">*Generic Type*.</span></span> <span data-ttu-id="d363b-194">宣言時に少なくとも&1; つのデータ型を指定するクラス、構造体、インターフェイス、プロシージャ、またはデリゲートの定義です。</span><span class="sxs-lookup"><span data-stu-id="d363b-194">A definition of a class, structure, interface, procedure, or delegate for which you supply at least one data type when you declare it.</span></span>  
  
-   <span data-ttu-id="d363b-195">*型パラメーター*。</span><span class="sxs-lookup"><span data-stu-id="d363b-195">*Type Parameter*.</span></span> <span data-ttu-id="d363b-196">ジェネリック型定義で、型を宣言するときにデータ型の代わりに指定するプレースホルダーです。</span><span class="sxs-lookup"><span data-stu-id="d363b-196">In a generic type definition, a placeholder for a data type you supply when you declare the type.</span></span>  
  
-   <span data-ttu-id="d363b-197">*型引数*。</span><span class="sxs-lookup"><span data-stu-id="d363b-197">*Type Argument*.</span></span> <span data-ttu-id="d363b-198">構成型をジェネリック型から宣言するときに、型パラメーターを置き換える特定のデータ型です。</span><span class="sxs-lookup"><span data-stu-id="d363b-198">A specific data type that replaces a type parameter when you declare a constructed type from a generic type.</span></span>  
  
-   <span data-ttu-id="d363b-199">*制約*。</span><span class="sxs-lookup"><span data-stu-id="d363b-199">*Constraint*.</span></span> <span data-ttu-id="d363b-200">型パラメーターに指定できる型引数を制限する条件です。</span><span class="sxs-lookup"><span data-stu-id="d363b-200">A condition on a type parameter that restricts the type argument you can supply for it.</span></span> <span data-ttu-id="d363b-201">型引数が特定のインターフェイスを実装すること、特定のクラスであるか特定のクラスを継承すること、アクセス可能なパラメーターなしのコンストラクターを持つこと、または参照型または値型であることを強制できます。</span><span class="sxs-lookup"><span data-stu-id="d363b-201">A constraint can require that the type argument must implement a particular interface, be or inherit from a particular class, have an accessible parameterless constructor, or be a reference type or a value type.</span></span> <span data-ttu-id="d363b-202">このような制約は組み合わせて指定できますが、指定できるのは&1; つのクラスだけです。</span><span class="sxs-lookup"><span data-stu-id="d363b-202">You can combine these constraints, but you can specify at most one class.</span></span>  
  
-   <span data-ttu-id="d363b-203">*構成型*。</span><span class="sxs-lookup"><span data-stu-id="d363b-203">*Constructed Type*.</span></span> <span data-ttu-id="d363b-204">型パラメーターに型引数を指定してジェネリック型から宣言されるクラス、構造体、インターフェイス、プロシージャ、またはデリゲートです。</span><span class="sxs-lookup"><span data-stu-id="d363b-204">A class, structure, interface, procedure, or delegate declared from a generic type by supplying type arguments for its type parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d363b-205">関連項目</span><span class="sxs-lookup"><span data-stu-id="d363b-205">See Also</span></span>  
 <span data-ttu-id="d363b-206">[データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="d363b-206">[Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="d363b-207"> [型文字](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md) </span><span class="sxs-lookup"><span data-stu-id="d363b-207"> [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md) </span></span>  
<span data-ttu-id="d363b-208"> [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="d363b-208"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="d363b-209"> [Visual Basic における型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="d363b-209"> [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="d363b-210"> [データ型のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="d363b-210"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="d363b-211"> [データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="d363b-211"> [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="d363b-212"> [Of](../../../../visual-basic/language-reference/statements/of-clause.md) </span><span class="sxs-lookup"><span data-stu-id="d363b-212"> [Of](../../../../visual-basic/language-reference/statements/of-clause.md) </span></span>  
<span data-ttu-id="d363b-213"> [として](../../../../visual-basic/language-reference/statements/as-clause.md) </span><span class="sxs-lookup"><span data-stu-id="d363b-213"> [As](../../../../visual-basic/language-reference/statements/as-clause.md) </span></span>  
<span data-ttu-id="d363b-214"> [オブジェクトのデータ型](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="d363b-214"> [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span></span>  
<span data-ttu-id="d363b-215"> [ジェネリックの共変性と反変性](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8) </span><span class="sxs-lookup"><span data-stu-id="d363b-215"> [Covariance and Contravariance](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8) </span></span>  
<span data-ttu-id="d363b-216"> [反復子](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)</span><span class="sxs-lookup"><span data-stu-id="d363b-216"> [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)</span></span>
