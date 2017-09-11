---
title: "Visual Basic の LINQ をサポートする機能 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
caps.latest.revision: 51
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
ms.openlocfilehash: 728018de7e38374875b15a809e5659003519d60f
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="visual-basic-features-that-support-linq"></a><span data-ttu-id="f4e37-102">LINQ をサポートする Visual Basic の機能</span><span class="sxs-lookup"><span data-stu-id="f4e37-102">Visual Basic Features That Support LINQ</span></span>
<span data-ttu-id="f4e37-103">名前[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]サポートしているクエリの構文を言語内で直接その他の言語構造は、Visual Basic での技術を参照します。</span><span class="sxs-lookup"><span data-stu-id="f4e37-103">The name [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] refers to technology in Visual Basic that supports query syntax and other language constructs directly in the language.</span></span> <span data-ttu-id="f4e37-104">[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]、外部データ ソースに対してクエリを新しい言語を習得する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f4e37-104">With [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], you do not have to learn a new language to query against an external data source.</span></span> <span data-ttu-id="f4e37-105">リレーショナル データベース、XML ストア、またはオブジェクトのデータを照会するには、Visual Basic を使用します。</span><span class="sxs-lookup"><span data-stu-id="f4e37-105">You can query against data in relational databases, XML stores, or objects by using Visual Basic.</span></span> <span data-ttu-id="f4e37-106">この統合言語クエリ機能のにより、コンパイル時の構文エラーと型の安全性をチェックします。</span><span class="sxs-lookup"><span data-stu-id="f4e37-106">This integration of query capabilities into the language enables compile-time checking for syntax errors and type safety.</span></span> <span data-ttu-id="f4e37-107">この統合は、Visual Basic で豊富なさまざまなクエリを記述しておく必要があるのほとんどを既に理解しているようにもなります。</span><span class="sxs-lookup"><span data-stu-id="f4e37-107">This integration also ensures that you already know most of what you have to know to write rich, varied queries in Visual Basic.</span></span>  
  
 <span data-ttu-id="f4e37-108">次のセクションでは、概要ドキュメント、コード例については、およびサンプル アプリケーションの読み取りを開始するために十分な詳細情報で LINQ をサポートする言語構成要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f4e37-108">The following sections describe the language constructs that support LINQ in enough detail to enable you to get started in reading the introductory documentation, code examples, and sample applications.</span></span> <span data-ttu-id="f4e37-109">また、どの言語機能が連携する統合言語クエリを有効にするのより詳細な説明を検索するリンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f4e37-109">You can also click the links to find more detailed explanations of how the language features come together to enable language-integrated query.</span></span> <span data-ttu-id="f4e37-110">開始するが最適[チュートリアル: Visual Basic でクエリを記述](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)します。</span><span class="sxs-lookup"><span data-stu-id="f4e37-110">A good place to start is [Walkthrough: Writing Queries in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md).</span></span>  
  
## <a name="query-expressions"></a><span data-ttu-id="f4e37-111">クエリ式</span><span class="sxs-lookup"><span data-stu-id="f4e37-111">Query Expressions</span></span>  
 <span data-ttu-id="f4e37-112">Visual Basic のクエリ式は、SQL や XQuery などのような宣言型の構文で表現できます。</span><span class="sxs-lookup"><span data-stu-id="f4e37-112">Query expressions in Visual Basic can be expressed in a declarative syntax similar to that of SQL or XQuery.</span></span> <span data-ttu-id="f4e37-113">コンパイル時に、クエリの構文は、標準クエリ演算子の拡張メソッドの LINQ プロバイダーの実装に対するメソッド呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="f4e37-113">At compile time, query syntax is converted into method calls to a LINQ provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="f4e37-114">標準クエリ演算子がスコープ内で適切な名前空間を指定することによって、アプリケーションを制御、`Imports`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="f4e37-114">Applications control which standard query operators are in scope by specifying the appropriate namespace with an `Imports` statement.</span></span> <span data-ttu-id="f4e37-115">Visual Basic のクエリ式の構文は、次のようにはなります。</span><span class="sxs-lookup"><span data-stu-id="f4e37-115">Syntax for a Visual Basic query expression looks like this:</span></span>  
  
 <span data-ttu-id="f4e37-116">[!code-vb[VbLINQVbFeatures&#1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f4e37-116">[!code-vb[VbLINQVbFeatures#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_1.vb)]</span></span>  
  
 <span data-ttu-id="f4e37-117">詳細については、次を参照してください。 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)します。</span><span class="sxs-lookup"><span data-stu-id="f4e37-117">For more information, see [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).</span></span>  
  
## <a name="implicitly-typed-variables"></a><span data-ttu-id="f4e37-118">暗黙的に型指定された変数</span><span class="sxs-lookup"><span data-stu-id="f4e37-118">Implicitly Typed Variables</span></span>  
 <span data-ttu-id="f4e37-119">明示的に宣言して、変数を初期化するときに、型を指定する、代わりに、型をコンパイラが有効にできます。</span><span class="sxs-lookup"><span data-stu-id="f4e37-119">Instead of explicitly specifying a type when you declare and initialize a variable, you can enable the compiler to infer and assign the type.</span></span> <span data-ttu-id="f4e37-120">これとして参照は*ローカル型推論*します。</span><span class="sxs-lookup"><span data-stu-id="f4e37-120">This is referred to as *local type inference*.</span></span>  
  
 <span data-ttu-id="f4e37-121">変数の型は推論される厳密に型指定、型を明示的に指定した変数と同じようにします。</span><span class="sxs-lookup"><span data-stu-id="f4e37-121">Variables whose types are inferred are strongly typed, just like variables whose type you specify explicitly.</span></span> <span data-ttu-id="f4e37-122">ローカル型推論は、メソッドの本文内のローカル変数を定義するときにのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="f4e37-122">Local type inference works only when you are defining a local variable inside a method body.</span></span> <span data-ttu-id="f4e37-123">詳細については、次を参照してください。 [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)と[ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)します。</span><span class="sxs-lookup"><span data-stu-id="f4e37-123">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
 <span data-ttu-id="f4e37-124">次の例では、ローカル型推論を示しています。</span><span class="sxs-lookup"><span data-stu-id="f4e37-124">The following example illustrates local type inference.</span></span> <span data-ttu-id="f4e37-125">この例を使用するに設定する必要があります`Option Infer`に`On`します。</span><span class="sxs-lookup"><span data-stu-id="f4e37-125">To use this example, you must set `Option Infer` to `On`.</span></span>  
  
 <span data-ttu-id="f4e37-126">[!code-vb[VbLINQVbFeatures&#2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="f4e37-126">[!code-vb[VbLINQVbFeatures#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_2.vb)]</span></span>  
  
 <span data-ttu-id="f4e37-127">ローカル型推論では、このセクションで後で説明し、LINQ クエリに必要な匿名型を作成することです。</span><span class="sxs-lookup"><span data-stu-id="f4e37-127">Local type inference also makes it possible to create anonymous types, which are described later in this section and are necessary for LINQ queries.</span></span>  
  
 <span data-ttu-id="f4e37-128">場合は次の LINQ の例では型の推定が発生した`Option Infer`か`On`または`Off`です。</span><span class="sxs-lookup"><span data-stu-id="f4e37-128">In the following LINQ example, type inference occurs if `Option Infer` is either `On` or `Off`.</span></span> <span data-ttu-id="f4e37-129">コンパイル時エラーが発生`Option Infer`は`Off`と`Option Strict`は`On`です。</span><span class="sxs-lookup"><span data-stu-id="f4e37-129">A compile-time error occurs if `Option Infer` is `Off` and `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="f4e37-130">[!code-vb[VbLINQVbFeatures&#3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="f4e37-130">[!code-vb[VbLINQVbFeatures#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_3.vb)]</span></span>  
  
## <a name="object-initializers"></a><span data-ttu-id="f4e37-131">オブジェクト初期化子</span><span class="sxs-lookup"><span data-stu-id="f4e37-131">Object Initializers</span></span>  
 <span data-ttu-id="f4e37-132">オブジェクト初期化子は、クエリの結果を保持するために匿名型を作成するときに、クエリ式で使用されます。</span><span class="sxs-lookup"><span data-stu-id="f4e37-132">Object initializers are used in query expressions when you have to create an anonymous type to hold the results of a query.</span></span> <span data-ttu-id="f4e37-133">これらも使用できますクエリの外部で名前付きの型のオブジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="f4e37-133">They also can be used to initialize objects of named types outside of queries.</span></span> <span data-ttu-id="f4e37-134">オブジェクト初期化子を使用するは、明示的にコンス トラクターを呼び出さずに、1 行でオブジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="f4e37-134">By using an object initializer, you can initialize an object in a single line without explicitly calling a constructor.</span></span> <span data-ttu-id="f4e37-135">という名前のクラスがある場合`Customer`を持つパブリック`Name`と`Phone`プロパティとその他のプロパティでは、この方法でオブジェクト初期化子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f4e37-135">Assuming that you have a class named `Customer` that has public `Name` and `Phone` properties, along with other properties, an object initializer can be used in this manner:</span></span>  
  
 <span data-ttu-id="f4e37-136">[!code-vb[VbLINQVbFeatures&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="f4e37-136">[!code-vb[VbLINQVbFeatures#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_4.vb)]</span></span>  
  
 <span data-ttu-id="f4e37-137">詳細については、次を参照してください。[オブジェクト初期化子: 名前付きおよび匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)します。</span><span class="sxs-lookup"><span data-stu-id="f4e37-137">For more information, see [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>  
  
## <a name="anonymous-types"></a><span data-ttu-id="f4e37-138">匿名型</span><span class="sxs-lookup"><span data-stu-id="f4e37-138">Anonymous Types</span></span>  
 <span data-ttu-id="f4e37-139">匿名型は、クエリ結果に追加する要素にプロパティのセットを一時的にグループ化する便利な手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="f4e37-139">Anonymous types provide a convenient way to temporarily group a set of properties into an element that you want to include in a query result.</span></span> <span data-ttu-id="f4e37-140">これにより、要素の名前付きのデータ型を定義することがなく任意の順序で、クエリで使用できるフィールドの任意の組み合わせを選択できます。</span><span class="sxs-lookup"><span data-stu-id="f4e37-140">This enables you to choose any combination of available fields in the query, in any order, without defining a named data type for the element.</span></span>  
  
 <span data-ttu-id="f4e37-141">*匿名型*はコンパイラによって動的に構築します。</span><span class="sxs-lookup"><span data-stu-id="f4e37-141">An *anonymous type* is constructed dynamically by the compiler.</span></span> <span data-ttu-id="f4e37-142">型の名前は、コンパイラによって割り当てられ、新しいコンパイルのたびに変更があります。</span><span class="sxs-lookup"><span data-stu-id="f4e37-142">The name of the type is assigned by the compiler, and it might change with each new compilation.</span></span> <span data-ttu-id="f4e37-143">そのため、名前は直接使用できません。</span><span class="sxs-lookup"><span data-stu-id="f4e37-143">Therefore, the name cannot be used directly.</span></span> <span data-ttu-id="f4e37-144">匿名型は、次のように初期化されます。</span><span class="sxs-lookup"><span data-stu-id="f4e37-144">Anonymous types are initialized in the following way:</span></span>  
  
 <span data-ttu-id="f4e37-145">[!code-vb[VbLINQVbFeatures&#5;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="f4e37-145">[!code-vb[VbLINQVbFeatures#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_5.vb)]</span></span>  
  
 <span data-ttu-id="f4e37-146">詳細については、次を参照してください。[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)します。</span><span class="sxs-lookup"><span data-stu-id="f4e37-146">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="extension-methods"></a><span data-ttu-id="f4e37-147">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="f4e37-147">Extension Methods</span></span>  
 <span data-ttu-id="f4e37-148">拡張メソッドを使用すると、データ型またはインターフェイスの元の定義の外部にメソッドを追加できます。</span><span class="sxs-lookup"><span data-stu-id="f4e37-148">Extension methods enable you to add methods to a data type or interface from outside the definition.</span></span> <span data-ttu-id="f4e37-149">この機能では、実際には、新しいメソッドを実際には、型を変更しなくても既存の型に追加することができます。</span><span class="sxs-lookup"><span data-stu-id="f4e37-149">This feature enables you to, in effect, add new methods to an existing type without actually modifying the type.</span></span> <span data-ttu-id="f4e37-150">標準クエリ演算子自体が提供する拡張メソッドのセット[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] <xref:System.Collections.Generic.IEnumerable%601>.</xref:System.Collections.Generic.IEnumerable%601>を実装する任意の型のクエリ機能</span><span class="sxs-lookup"><span data-stu-id="f4e37-150">The standard query operators are themselves a set of extension methods that provide [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="f4e37-151">他の拡張機能に<xref:System.Collections.Generic.IEnumerable%601>含める<xref:System.Linq.Enumerable.Count%2A>、 <xref:System.Linq.Enumerable.Union%2A>、 <xref:System.Linq.Enumerable.Intersect%2A>.</xref:System.Linq.Enumerable.Intersect%2A> </xref:System.Linq.Enumerable.Union%2A> </xref:System.Linq.Enumerable.Count%2A> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="f4e37-151">Other extensions to <xref:System.Collections.Generic.IEnumerable%601> include <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Intersect%2A>.</span></span>  
  
 <span data-ttu-id="f4e37-152">次の拡張メソッドでは、印刷メソッドを<xref:System.String>クラス</xref:System.String>に追加します。</span><span class="sxs-lookup"><span data-stu-id="f4e37-152">The following extension method adds a print method to the <xref:System.String> class.</span></span>  
  
 <span data-ttu-id="f4e37-153">[!code-vb[VbLINQVbFeatures&6;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="f4e37-153">[!code-vb[VbLINQVbFeatures#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_6.vb)]</span></span>  
  
 <span data-ttu-id="f4e37-154"><xref:System.String>::</xref:System.String>の通常のインスタンス メソッドのように、メソッドが呼び出されます</span><span class="sxs-lookup"><span data-stu-id="f4e37-154">The method is called like an ordinary instance method of <xref:System.String>:</span></span>  
  
 <span data-ttu-id="f4e37-155">[!code-vb[VbLINQVbFeatures&#7;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="f4e37-155">[!code-vb[VbLINQVbFeatures#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_7.vb)]</span></span>  
  
 <span data-ttu-id="f4e37-156">詳細については、次を参照してください。[拡張メソッド](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)します。</span><span class="sxs-lookup"><span data-stu-id="f4e37-156">For more information, see [Extension Methods](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
## <a name="lambda-expressions"></a><span data-ttu-id="f4e37-157">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="f4e37-157">Lambda Expressions</span></span>  
 <span data-ttu-id="f4e37-158">ラムダ式は、計算して、単一の値を返す名前のない関数です。</span><span class="sxs-lookup"><span data-stu-id="f4e37-158">A lambda expression is a function without a name that calculates and returns a single value.</span></span> <span data-ttu-id="f4e37-159">名前付きの関数とは異なり、ラムダ式の定義し、同時に実行します。</span><span class="sxs-lookup"><span data-stu-id="f4e37-159">Unlike named functions, a lambda expression can be defined and executed at the same time.</span></span> <span data-ttu-id="f4e37-160">次の例では、4 を表示します。</span><span class="sxs-lookup"><span data-stu-id="f4e37-160">The following example displays 4.</span></span>  
  
 <span data-ttu-id="f4e37-161">[!code-vb[VbLINQVbFeatures&#8;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="f4e37-161">[!code-vb[VbLINQVbFeatures#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_8.vb)]</span></span>  
  
 <span data-ttu-id="f4e37-162">変数名にラムダ式の定義を割り当てるでき、名前を使用して、関数を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f4e37-162">You can assign the lambda expression definition to a variable name and then use the name to call the function.</span></span> <span data-ttu-id="f4e37-163">次の例では、4 も表示されます。</span><span class="sxs-lookup"><span data-stu-id="f4e37-163">The following example also displays 4.</span></span>  
  
 <span data-ttu-id="f4e37-164">[!code-vb[VbLINQVbFeatures&#12;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="f4e37-164">[!code-vb[VbLINQVbFeatures#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_9.vb)]</span></span>  
  
 <span data-ttu-id="f4e37-165">[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]ラムダ式には、標準クエリ演算子の多くが基本となります。</span><span class="sxs-lookup"><span data-stu-id="f4e37-165">In [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], lambda expressions underlie many of the standard query operators.</span></span> <span data-ttu-id="f4e37-166">コンパイラなど、基本的なクエリ メソッドで定義されている計算をキャプチャするラムダ式を作成する`Where`、 `Select`、 `Order By`、 `Take While`、およびその他。</span><span class="sxs-lookup"><span data-stu-id="f4e37-166">The compiler creates lambda expressions to capture the calculations that are defined in fundamental query methods such as `Where`, `Select`, `Order By`, `Take While`, and others.</span></span>  
  
 <span data-ttu-id="f4e37-167">たとえば、次のコードでは、学生の一覧から上級生を返すクエリを定義します。</span><span class="sxs-lookup"><span data-stu-id="f4e37-167">For example, the following code defines a query that returns all senior students from a list of students.</span></span>  
  
 <span data-ttu-id="f4e37-168">[!code-vb[VbLINQVbFeatures&#9;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="f4e37-168">[!code-vb[VbLINQVbFeatures#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_10.vb)]</span></span>  
  
 <span data-ttu-id="f4e37-169">クエリ定義は次の例は、2 つのラムダ式を使用して引数を指定する次のようなコードにコンパイル`Where`と`Select`です。</span><span class="sxs-lookup"><span data-stu-id="f4e37-169">The query definition is compiled into code that is similar to the following example, which uses two lambda expressions to specify the arguments for `Where` and `Select`.</span></span>  
  
 <span data-ttu-id="f4e37-170">[!code-vb[VbLINQVbFeatures&#10;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_11.vb)]</span><span class="sxs-lookup"><span data-stu-id="f4e37-170">[!code-vb[VbLINQVbFeatures#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_11.vb)]</span></span>  
  
 <span data-ttu-id="f4e37-171">いずれかのバージョンを使用して実行できる、`For Each`ループします。</span><span class="sxs-lookup"><span data-stu-id="f4e37-171">Either version can be run by using a `For Each` loop:</span></span>  
  
 <span data-ttu-id="f4e37-172">[!code-vb[VbLINQVbFeatures&#11;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_12.vb)]</span><span class="sxs-lookup"><span data-stu-id="f4e37-172">[!code-vb[VbLINQVbFeatures#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_12.vb)]</span></span>  
  
 <span data-ttu-id="f4e37-173">詳細については、次を参照してください。[ラムダ式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)します。</span><span class="sxs-lookup"><span data-stu-id="f4e37-173">For more information, see [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4e37-174">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4e37-174">See Also</span></span>  
 <span data-ttu-id="f4e37-175">[統合言語クエリ (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="f4e37-175">[Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md) </span></span>  
<span data-ttu-id="f4e37-176"> [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md) </span><span class="sxs-lookup"><span data-stu-id="f4e37-176"> [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md) </span></span>  
<span data-ttu-id="f4e37-177"> [LINQ と文字列 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md) </span><span class="sxs-lookup"><span data-stu-id="f4e37-177"> [LINQ and Strings (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md) </span></span>  
<span data-ttu-id="f4e37-178"> [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md) </span><span class="sxs-lookup"><span data-stu-id="f4e37-178"> [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) </span></span>  
<span data-ttu-id="f4e37-179"> [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)</span><span class="sxs-lookup"><span data-stu-id="f4e37-179"> [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)</span></span>
