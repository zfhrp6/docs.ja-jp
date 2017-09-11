---
title: "コレクション初期化子 (Visual Basic)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.CollectionInitializer
dev_langs:
- VB
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: a9290329-77b0-4fdf-ae75-8fc17287f469
caps.latest.revision: 23
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 72ca6506d0bd867efa60ba73ecda72c32def129e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="collection-initializers-visual-basic"></a><span data-ttu-id="f2a92-102">コレクション初期化子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2a92-102">Collection Initializers (Visual Basic)</span></span>
<span data-ttu-id="f2a92-103">*コレクション初期化子*とは、コレクションを作成して一連の初期値を設定できる、短い構文です。</span><span class="sxs-lookup"><span data-stu-id="f2a92-103">*Collection initializers* provide a shortened syntax that enables you to create a collection and populate it with an initial set of values.</span></span> <span data-ttu-id="f2a92-104">コレクション初期化子は、コレクションを既知の値のセットから作成する場合に便利です。値のセットの例として、メニュー オプションやカテゴリのリスト、数値の初期セット、曜日や月の名前の静的文字列のリスト、検証に使用する州のリストなどの地理的な場所が挙げられます。</span><span class="sxs-lookup"><span data-stu-id="f2a92-104">Collection initializers are useful when you are creating a collection from a set of known values, for example, a list of menu options or categories, an initial set of numeric values, a static list of strings such as day or month names, or geographic locations such as a list of states that is used for validation.</span></span>  
  
 <span data-ttu-id="f2a92-105">コレクションの詳細については、「[コレクション](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2a92-105">For more information about collections, see [Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b).</span></span>  
  
 <span data-ttu-id="f2a92-106">コレクション初期化子は、`From` キーワードの後に中かっこ (`{}`) を使用して指定できます。</span><span class="sxs-lookup"><span data-stu-id="f2a92-106">You identify a collection initializer by using the `From` keyword followed by braces (`{}`).</span></span> <span data-ttu-id="f2a92-107">これは、「[配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)」で説明する配列リテラルの構文と似ています。</span><span class="sxs-lookup"><span data-stu-id="f2a92-107">This is similar to the array literal syntax that is described in [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span> <span data-ttu-id="f2a92-108">次の例では、コレクション初期化子を使用してコレクションを作成するさまざまな方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f2a92-108">The following examples show various ways to use collection initializers to create collections.</span></span>  
  
 <span data-ttu-id="f2a92-109">[!code-vb[VbVbalrCollectionInitializers#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#1)]</span><span class="sxs-lookup"><span data-stu-id="f2a92-109">[!code-vb[VbVbalrCollectionInitializers#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#1)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2a92-110">C# にもコレクション初期化子はあります。</span><span class="sxs-lookup"><span data-stu-id="f2a92-110">C# also provides collection initializers.</span></span> <span data-ttu-id="f2a92-111">C# のコレクション初期化子には、Visual Basic のコレクション初期化子と同じ機能があります。</span><span class="sxs-lookup"><span data-stu-id="f2a92-111">C# collection initializers provide the same functionality as Visual Basic collection initializers.</span></span> <span data-ttu-id="f2a92-112">C# のコレクション初期化子の詳細については、「[オブジェクト初期化子とコレクション初期化子](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2a92-112">For more information about C# collection initializers, see [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2a92-113">構文</span><span class="sxs-lookup"><span data-stu-id="f2a92-113">Syntax</span></span>  
 <span data-ttu-id="f2a92-114">コレクション初期化子は、次のコードのように、先頭に `From` キーワードが付いた、中かっこ (`{}`) で囲まれたコンマ区切りの値の一覧で構成されます。</span><span class="sxs-lookup"><span data-stu-id="f2a92-114">A collection initializer consists of a list of comma-separated values that are enclosed in braces (`{}`), preceded by the `From` keyword, as shown in the following code.</span></span>  
  
 <span data-ttu-id="f2a92-115">[!code-vb[VbVbalrCollectionInitializers#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#2)]</span><span class="sxs-lookup"><span data-stu-id="f2a92-115">[!code-vb[VbVbalrCollectionInitializers#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#2)]</span></span>  
  
 <span data-ttu-id="f2a92-116"><xref:System.Collections.Generic.List%601> や <xref:System.Collections.Generic.Dictionary%602> などのコレクションを作成する場合、次のコードに示すように、コレクション初期化子の前に、コレクションの種類を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2a92-116">When you create a collection, such as a <xref:System.Collections.Generic.List%601> or a <xref:System.Collections.Generic.Dictionary%602>, you must supply the collection type before the collection initializer, as shown in the following code.</span></span>  
  
 <span data-ttu-id="f2a92-117">[!code-vb[VbVbalrCollectionInitializers#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#13)]</span><span class="sxs-lookup"><span data-stu-id="f2a92-117">[!code-vb[VbVbalrCollectionInitializers#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#13)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2a92-118">コレクション初期化子とオブジェクト初期化子を組み合わせて、同じコレクション オブジェクトを初期化することはできません。</span><span class="sxs-lookup"><span data-stu-id="f2a92-118">You cannot combine both a collection initializer and an object initializer to initialize the same collection object.</span></span> <span data-ttu-id="f2a92-119">コレクション初期化子内のオブジェクトを初期化するには、オブジェクト初期化子を使用します。</span><span class="sxs-lookup"><span data-stu-id="f2a92-119">You can use object initializers to initialize objects in a collection initializer.</span></span>  
  
## <a name="creating-a-collection-by-using-a-collection-intializer"></a><span data-ttu-id="f2a92-120">コレクション初期化子を使用してコレクションを作成する</span><span class="sxs-lookup"><span data-stu-id="f2a92-120">Creating a Collection by Using a Collection Intializer</span></span>  
 <span data-ttu-id="f2a92-121">コレクション初期化子を使用してコレクションを作成する場合、コレクション初期化子内の各値は、コレクション内の適切な `Add` メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="f2a92-121">When you create a collection by using a collection initializer, each value that is supplied in the collection initializer is passed to the appropriate `Add` method of the collection.</span></span> <span data-ttu-id="f2a92-122">たとえば、コレクション初期化子を使用して <xref:System.Collections.Generic.List%601> 作成する場合、コレクション初期化子内の各文字列値は <xref:System.Collections.Generic.List%601.Add%2A> メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="f2a92-122">For example, if you create a <xref:System.Collections.Generic.List%601> by using a collection initializer, each string value in the collection initializer is passed to the <xref:System.Collections.Generic.List%601.Add%2A> method.</span></span> <span data-ttu-id="f2a92-123">コレクション初期化子を使用してコレクションを作成する場合は、指定した型は有効なコレクション型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2a92-123">If you want to create a collection by using a collection initializer, the specified type must be valid collection type.</span></span> <span data-ttu-id="f2a92-124">有効なコレクションの型には、<xref:System.Collections.Generic.IEnumerable%601> インターフェイスを実装するクラスや、<xref:System.Collections.CollectionBase> クラスを継承するクラスなどがあります。</span><span class="sxs-lookup"><span data-stu-id="f2a92-124">Examples of valid collection types include classes that implement the <xref:System.Collections.Generic.IEnumerable%601> interface or inherit the <xref:System.Collections.CollectionBase> class.</span></span> <span data-ttu-id="f2a92-125">指定した型には、次の条件を満たす `Add` メソッドも公開されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2a92-125">The specified type must also expose an `Add` method that meets the following criteria.</span></span>  
  
-   <span data-ttu-id="f2a92-126">`Add` メソッドは、コレクション初期化子の呼び出し元の範囲から使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2a92-126">The `Add` method must be available from the scope in which the collection initializer is being called.</span></span> <span data-ttu-id="f2a92-127">そのコレクションのパブリックでないメソッドにアクセスできるシナリオでコレクション初期化子を使用する場合は、`Add` メソッドは、パブリックである必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f2a92-127">The `Add` method does not have to be public if you are using the collection initializer in a scenario where non-public methods of the collection can be accessed.</span></span>  
  
-   <span data-ttu-id="f2a92-128">`Add` メソッドはインスタンス メンバー、またはコレクション クラスの `Shared` メンバーまたは拡張メソッドである必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2a92-128">The `Add` method must be an instance member or `Shared` member of the collection class, or an extension method.</span></span>  
  
-   <span data-ttu-id="f2a92-129">オーバーロード解決規則に基づいて、コレクション初期化子で提供される型に対応付けることができる `Add` メソッドが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2a92-129">An `Add` method must exist that can be matched, based on overload resolution rules, to the types that are supplied in the collection initializer.</span></span>  
  
 <span data-ttu-id="f2a92-130">たとえば、コレクション初期化子を使用して、`List(Of Customer)` コレクションを作成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f2a92-130">For example, the following code example shows how to create a `List(Of Customer)` collection by using a collection initializer.</span></span> <span data-ttu-id="f2a92-131">このコードを実行すると、`Customer` の各オブジェクトは汎用リストの `Add(Customer)` メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="f2a92-131">When the code is run, each `Customer` object is passed to the `Add(Customer)` method of the generic list.</span></span>  
  
 <span data-ttu-id="f2a92-132">[!code-vb[VbVbalrCollectionInitializers#9](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#9)]</span><span class="sxs-lookup"><span data-stu-id="f2a92-132">[!code-vb[VbVbalrCollectionInitializers#9](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#9)]</span></span>  
  
 <span data-ttu-id="f2a92-133">次では、コレクション初期化子を使用しない同等のコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="f2a92-133">The following code example shows equivalent code that does not use a collection initializer.</span></span>  
  
 <span data-ttu-id="f2a92-134">[!code-vb[VbVbalrCollectionInitializers#10](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#10)]</span><span class="sxs-lookup"><span data-stu-id="f2a92-134">[!code-vb[VbVbalrCollectionInitializers#10](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#10)]</span></span>  
  
 <span data-ttu-id="f2a92-135">`Customer` オブジェクトのコンストラクターと一致するパラメーターを持つ `Add` メソッドがコレクションにある場合、次のセクションで説明するように、コレクション初期化子内に `Add` メソッドのパラメーター値を入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="f2a92-135">If the collection has an `Add` method that has parameters that match the constructor for the `Customer` object, you could nest parameter values for the `Add` method within collection initializers, as discussed in the next section.</span></span> <span data-ttu-id="f2a92-136">コレクションにこのような `Add` メソッドがない場合、それを拡張メソッドとして作成できます。</span><span class="sxs-lookup"><span data-stu-id="f2a92-136">If the collection does not have such an `Add` method, you can create one as an extension method.</span></span> <span data-ttu-id="f2a92-137">コレクションの拡張メソッドとして `Add` メソッドを作成する方法の例については、「[方法: コレクション初期化子で使用される拡張メソッドを作成または追加する](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2a92-137">For an example of how to create an `Add` method as an extension method for a collection, see [How to: Create an Add Extension Method Used by a Collection Initializer](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md).</span></span> <span data-ttu-id="f2a92-138">コレクション初期化子で使用できるカスタム コレクションを作成する方法の例については、「[方法: コレクション初期化子を使用してコレクションを作成する](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2a92-138">For an example of how to create a custom collection that can be used with a collection initializer, see [How to: Create a Collection Used by a Collection Initializer](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md).</span></span>  
  
## <a name="nesting-collection-initializers"></a><span data-ttu-id="f2a92-139">コレクション初期化子を入れ子にする</span><span class="sxs-lookup"><span data-stu-id="f2a92-139">Nesting Collection Initializers</span></span>  
 <span data-ttu-id="f2a92-140">作成するコレクションの `Add` メソッドで固有のオーバーロードを指定するため、コレクション初期化子内の値を入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="f2a92-140">You can nest values within a collection initializer to identify a specific overload of an `Add` method for the collection that is being created.</span></span> <span data-ttu-id="f2a92-141">`Add` メソッドに渡す値は、配列リテラルまたはコレクション初期化子の場合と同じように、コンマで区切り、中かっこ (`{}`) で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2a92-141">The values passed to the `Add` method must be separated by commas and enclosed in braces (`{}`), like you would do in an array literal or collection initializer.</span></span>  
  
 <span data-ttu-id="f2a92-142">入れ子にした値でコレクションを作成する場合、入れ子になった値一覧の各要素は、要素の型に一致する `Add` メソッドに引数として渡されます。</span><span class="sxs-lookup"><span data-stu-id="f2a92-142">When you create a collection by using nested values, each element of the nested value list is passed as an argument to the `Add` method that matches the element types.</span></span> <span data-ttu-id="f2a92-143">たとえば、次のコード例では、キーは `Integer` 型で値は `String` 型の <xref:System.Collections.Generic.Dictionary%602> が作成されます。</span><span class="sxs-lookup"><span data-stu-id="f2a92-143">For example, the following code example creates a <xref:System.Collections.Generic.Dictionary%602> in which the keys are of type `Integer` and the values are of type `String`.</span></span> <span data-ttu-id="f2a92-144">一連の入れ子になった値は、それぞれ `Dictionary` の <xref:System.Collections.Generic.Dictionary%602.Add%2A> メソッドと照合されます。</span><span class="sxs-lookup"><span data-stu-id="f2a92-144">Each of the nested value lists is matched to the <xref:System.Collections.Generic.Dictionary%602.Add%2A> method for the `Dictionary`.</span></span>  
  
 <span data-ttu-id="f2a92-145">[!code-vb[VbVbalrCollectionInitializers#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#5)]</span><span class="sxs-lookup"><span data-stu-id="f2a92-145">[!code-vb[VbVbalrCollectionInitializers#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#5)]</span></span>  
  
 <span data-ttu-id="f2a92-146">前のコード例は、次のコードと同じです。</span><span class="sxs-lookup"><span data-stu-id="f2a92-146">The previous code example is equivalent to the following code.</span></span>  
  
 <span data-ttu-id="f2a92-147">[!code-vb[VbVbalrCollectionInitializers#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#6)]</span><span class="sxs-lookup"><span data-stu-id="f2a92-147">[!code-vb[VbVbalrCollectionInitializers#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#6)]</span></span>  
  
 <span data-ttu-id="f2a92-148">入れ子の最初のレベルの一連の入れ子になった値のみが、それぞれそのコレクション型の `Add` メソッドに送信されます。</span><span class="sxs-lookup"><span data-stu-id="f2a92-148">Only nested value lists from the first level of nesting are sent to the `Add` method for the collection type.</span></span> <span data-ttu-id="f2a92-149">より深いレベルの入れ子は配列リテラルとして扱われ、入れ子になった一連の値はどのコレクションの `Add` メソッドとも照合されません。</span><span class="sxs-lookup"><span data-stu-id="f2a92-149">Deeper levels of nesting are treated as array literals and the nested value lists are not matched to the `Add` method of any collection.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="f2a92-150">関連トピック</span><span class="sxs-lookup"><span data-stu-id="f2a92-150">Related Topics</span></span>  
  
|<span data-ttu-id="f2a92-151">タイトル</span><span class="sxs-lookup"><span data-stu-id="f2a92-151">Title</span></span>|<span data-ttu-id="f2a92-152">説明</span><span class="sxs-lookup"><span data-stu-id="f2a92-152">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="f2a92-153">方法: コレクション初期化子で使用される拡張メソッドを作成または追加する</span><span class="sxs-lookup"><span data-stu-id="f2a92-153">How to: Create an Add Extension Method Used by a Collection Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)|<span data-ttu-id="f2a92-154">コレクション初期化子の値をコレクションに入力するために使用できる `Add` と呼ばれる拡張メソッドを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f2a92-154">Shows how to create an extension method called `Add` that can be used to populate a collection with values from a collection initializer.</span></span>|  
|[<span data-ttu-id="f2a92-155">方法: コレクション初期化子を使用してコレクションを作成する</span><span class="sxs-lookup"><span data-stu-id="f2a92-155">How to: Create a Collection Used by a Collection Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)|<span data-ttu-id="f2a92-156">`IEnumerable` を実装するコレクション クラスに `Add` メソッドを含めてコレクション初期化子を使用できるようにする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="f2a92-156">Shows how to enable use of a collection initializer by including an `Add` method in a collection class that implements `IEnumerable`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2a92-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2a92-157">See Also</span></span>  
 <span data-ttu-id="f2a92-158">[コレクション](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) </span><span class="sxs-lookup"><span data-stu-id="f2a92-158">[Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) </span></span>  
 <span data-ttu-id="f2a92-159">[配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="f2a92-159">[Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md) </span></span>  
 <span data-ttu-id="f2a92-160">[オブジェクト初期化子 : 名前付きの型と匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="f2a92-160">[Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span></span>  
 <span data-ttu-id="f2a92-161">[New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md) </span><span class="sxs-lookup"><span data-stu-id="f2a92-161">[New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) </span></span>  
 <span data-ttu-id="f2a92-162">[自動実装プロパティ](../../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md) </span><span class="sxs-lookup"><span data-stu-id="f2a92-162">[Auto-Implemented Properties](../../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md) </span></span>  
 <span data-ttu-id="f2a92-163">[方法: Visual Basic で配列変数を初期化する](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md) </span><span class="sxs-lookup"><span data-stu-id="f2a92-163">[How to: Initialize an Array Variable in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md) </span></span>  
 <span data-ttu-id="f2a92-164">[ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="f2a92-164">[Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
 <span data-ttu-id="f2a92-165">[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="f2a92-165">[Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span></span>  
 <span data-ttu-id="f2a92-166">[Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="f2a92-166">[Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
 [<span data-ttu-id="f2a92-167">方法: 項目のリストを作成する</span><span class="sxs-lookup"><span data-stu-id="f2a92-167">How to: Create a List of Items</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)

