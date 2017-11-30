---
title: "チュートリアル: 動的オブジェクトの作成と使用 (C# および Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dynamic objects [Visual Basic]
- dynamic objects
- dynamic objects [C#]
ms.assetid: 568f1645-1305-4906-8625-5d77af81e04f
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ab1e245ed806cf0ea6346c76c6ade83273eed7be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-and-using-dynamic-objects-c-and-visual-basic"></a><span data-ttu-id="1194c-102">チュートリアル: 動的オブジェクトの作成と使用 (C# および Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1194c-102">Walkthrough: Creating and Using Dynamic Objects (C# and Visual Basic)</span></span>

<span data-ttu-id="1194c-103">動的オブジェクトは、プロパティやメソッドなどのメンバーを、コンパイル時ではなく実行時に公開します。</span><span class="sxs-lookup"><span data-stu-id="1194c-103">Dynamic objects expose members such as properties and methods at run time, instead of in at compile time.</span></span> <span data-ttu-id="1194c-104">これにより、静的な型や書式に一致しない構造体と連携するオブジェクトを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="1194c-104">This enables you to create objects to work with structures that do not match a static type or format.</span></span> <span data-ttu-id="1194c-105">たとえば、動的オブジェクトを使用して HTML ドキュメント オブジェクト モデル (DOM) を参照することもできます。HTML DOM には、有効な HTML マークアップ要素と属性の任意の組み合わせを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="1194c-105">For example, you can use a dynamic object to reference the HTML Document Object Model (DOM), which can contain any combination of valid HTML markup elements and attributes.</span></span> <span data-ttu-id="1194c-106">各 HTML ドキュメントは一意であるため、特定の HTML ドキュメントのメンバーは実行時に決定されます。</span><span class="sxs-lookup"><span data-stu-id="1194c-106">Because each HTML document is unique, the members for a particular HTML document are determined at run time.</span></span> <span data-ttu-id="1194c-107">HTML 要素の属性を参照するための一般的な方法は、属性の名前を要素の `GetProperty` メソッドに渡す方法です。</span><span class="sxs-lookup"><span data-stu-id="1194c-107">A common method to reference an attribute of an HTML element is to pass the name of the attribute to the `GetProperty` method of the element.</span></span> <span data-ttu-id="1194c-108">HTML 要素 `<div id="Div1">` の `id` 属性を参照するには、まず `<div>` 要素への参照を取得し、その後 `divElement.GetProperty("id")` を使用します。</span><span class="sxs-lookup"><span data-stu-id="1194c-108">To reference the `id` attribute of the HTML element `<div id="Div1">`, you first obtain a reference to the `<div>` element, and then use `divElement.GetProperty("id")`.</span></span> <span data-ttu-id="1194c-109">動的オブジェクトを使用する場合は、`id` 属性を `divElement.id` として参照できます。</span><span class="sxs-lookup"><span data-stu-id="1194c-109">If you use a dynamic object, you can reference the `id` attribute as `divElement.id`.</span></span>  
  
 <span data-ttu-id="1194c-110">動的オブジェクトを使用すると、IronPython や IronRuby などの動的言語にも簡単にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1194c-110">Dynamic objects also provide convenient access to dynamic languages such as IronPython and IronRuby.</span></span> <span data-ttu-id="1194c-111">動的オブジェクトを使用して、実行時に解釈される動的スクリプトを参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="1194c-111">You can use a dynamic object to refer to a dynamic script that is interpreted at run time.</span></span>  
  
 <span data-ttu-id="1194c-112">動的オブジェクトを参照するには、遅延バインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="1194c-112">You reference a dynamic object by using late binding.</span></span> <span data-ttu-id="1194c-113">C# では、遅延バインディング オブジェクトの型は `dynamic` として指定します。</span><span class="sxs-lookup"><span data-stu-id="1194c-113">In C#, you specify the type of a late-bound object as `dynamic`.</span></span> <span data-ttu-id="1194c-114">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] では、遅延バインディング オブジェクトの型は `Object` として指定します。</span><span class="sxs-lookup"><span data-stu-id="1194c-114">In [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], you specify the type of a late-bound object as `Object`.</span></span> <span data-ttu-id="1194c-115">詳しくは、「[dynamic](../../../csharp/language-reference/keywords/dynamic.md)」および「[事前バインディングと遅延バインディング](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1194c-115">For more information, see [dynamic](../../../csharp/language-reference/keywords/dynamic.md) and [Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).</span></span>  
  
 <span data-ttu-id="1194c-116">カスタムの動的オブジェクトは、<xref:System.Dynamic?displayProperty=nameWithType> 名前空間内のクラスを使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="1194c-116">You can create custom dynamic objects by using the classes in the <xref:System.Dynamic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="1194c-117">たとえば、<xref:System.Dynamic.ExpandoObject> を作成し、実行時にそのオブジェクトのメンバーを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="1194c-117">For example, you can create an <xref:System.Dynamic.ExpandoObject> and specify the members of that object at run time.</span></span> <span data-ttu-id="1194c-118">また、<xref:System.Dynamic.DynamicObject> クラスを継承する、独自の型を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="1194c-118">You can also create your own type that inherits the <xref:System.Dynamic.DynamicObject> class.</span></span> <span data-ttu-id="1194c-119">その後、<xref:System.Dynamic.DynamicObject> クラスのメンバーをオーバーライドして、実行時の動的機能を提供することができます。</span><span class="sxs-lookup"><span data-stu-id="1194c-119">You can then override the members of the <xref:System.Dynamic.DynamicObject> class to provide run-time dynamic functionality.</span></span>  
  
 <span data-ttu-id="1194c-120">このチュートリアルでは、次のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="1194c-120">In this walkthrough you will perform the following tasks:</span></span>  
  
-   <span data-ttu-id="1194c-121">テキスト ファイルの内容をオブジェクトのプロパティとして動的に公開する、カスタム オブジェクトを作成する。</span><span class="sxs-lookup"><span data-stu-id="1194c-121">Create a custom object that dynamically exposes the contents of a text file as properties of an object.</span></span>  
  
-   <span data-ttu-id="1194c-122">`IronPython` ライブラリを使用するプロジェクトを作成する。</span><span class="sxs-lookup"><span data-stu-id="1194c-122">Create a project that uses an `IronPython` library.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1194c-123">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="1194c-123">Prerequisites</span></span>  
<span data-ttu-id="1194c-124">必要がある[IronPython](http://ironpython.net/)このチュートリアルを完了する、.NET 用です。</span><span class="sxs-lookup"><span data-stu-id="1194c-124">You need [IronPython](http://ironpython.net/) for .NET to complete this walkthrough.</span></span> <span data-ttu-id="1194c-125">移動してその[ダウンロード ページ](http://ironpython.net/download/)を最新バージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="1194c-125">Go to their [Download page](http://ironpython.net/download/) to obtain the latest version.</span></span>
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-custom-dynamic-object"></a><span data-ttu-id="1194c-126">カスタム動的オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="1194c-126">Creating a Custom Dynamic Object</span></span>  
 <span data-ttu-id="1194c-127">このチュートリアルで作成する最初のプロジェクトでは、テキスト ファイルの内容を検索するカスタムの動的オブジェクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="1194c-127">The first project that you create in this walkthrough defines a custom dynamic object that searches the contents of a text file.</span></span> <span data-ttu-id="1194c-128">検索するテキストは、動的プロパティの名前によって指定されます。</span><span class="sxs-lookup"><span data-stu-id="1194c-128">Text to search for is specified by the name of a dynamic property.</span></span> <span data-ttu-id="1194c-129">たとえば、呼び出しコードで `dynamicFile.Sample` が指定された場合、動的クラスは "Sample" で始まるすべての行をファイルから取得し、それらを含んだ文字列のジェネリック リストを返します。</span><span class="sxs-lookup"><span data-stu-id="1194c-129">For example, if calling code specifies `dynamicFile.Sample`, the dynamic class returns a generic list of strings that contains all of the lines from the file that begin with "Sample".</span></span> <span data-ttu-id="1194c-130">検索では、大文字と小文字を区別しません。</span><span class="sxs-lookup"><span data-stu-id="1194c-130">The search is case-insensitive.</span></span> <span data-ttu-id="1194c-131">動的クラスでは、2 つの省略可能な引数もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1194c-131">The dynamic class also supports two optional arguments.</span></span> <span data-ttu-id="1194c-132">最初の引数は、検索オプションの列挙値です。この引数では、動的クラスが行の先頭、行の末尾、または行内の任意の場所から一致を検索することを指定します。</span><span class="sxs-lookup"><span data-stu-id="1194c-132">The first argument is a search option enum value that specifies that the dynamic class should search for matches at the start of the line, the end of the line, or anywhere in the line.</span></span> <span data-ttu-id="1194c-133">2 番目の引数は、動的クラスが検索の前に各行から先頭と末尾の空白をトリミングすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="1194c-133">The second argument specifies that the dynamic class should trim leading and trailing spaces from each line before searching.</span></span> <span data-ttu-id="1194c-134">たとえば、呼び出しコードで `dynamicFile.Sample(StringSearchOption.Contains)` と指定された場合、動的クラスは行内の任意の場所にある "Sample" を検索します。</span><span class="sxs-lookup"><span data-stu-id="1194c-134">For example, if calling code specifies `dynamicFile.Sample(StringSearchOption.Contains)`, the dynamic class searches for "Sample" anywhere in a line.</span></span> <span data-ttu-id="1194c-135">呼び出しコードで `dynamicFile.Sample(StringSearchOption.StartsWith, false)` と指定された場合、動的クラスは、各行の先頭にある "Sample" を検索し、先頭と末尾のスペースは削除しません。</span><span class="sxs-lookup"><span data-stu-id="1194c-135">If calling code specifies `dynamicFile.Sample(StringSearchOption.StartsWith, false)`, the dynamic class searches for "Sample" at the start of each line, and does not remove leading and trailing spaces.</span></span> <span data-ttu-id="1194c-136">既定では、動的クラスは各行の先頭で一致を検索し、先頭と末尾のスペースを削除します。</span><span class="sxs-lookup"><span data-stu-id="1194c-136">The default behavior of the dynamic class is to search for a match at the start of each line and to remove leading and trailing spaces.</span></span>  
  
#### <a name="to-create-a-custom-dynamic-class"></a><span data-ttu-id="1194c-137">カスタムの動的クラスを作成するには</span><span class="sxs-lookup"><span data-stu-id="1194c-137">To create a custom dynamic class</span></span>  
  
1.  <span data-ttu-id="1194c-138">[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] を起動します。</span><span class="sxs-lookup"><span data-stu-id="1194c-138">Start [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span></span>  
  
2.  <span data-ttu-id="1194c-139">**[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1194c-139">On the **File** menu, point to **New** and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="1194c-140">**[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、**[Windows]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1194c-140">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="1194c-141">**[テンプレート]** ペインの **[コンソール アプリケーション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1194c-141">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="1194c-142">**[名前]** ボックスに `DynamicSample` と入力して、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1194c-142">In the **Name** box, type `DynamicSample`, and then click **OK**.</span></span> <span data-ttu-id="1194c-143">新しいプロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1194c-143">The new project is created.</span></span>  
  
4.  <span data-ttu-id="1194c-144">DynamicSample プロジェクトを右クリックし、**[追加]** をポイントした後、**[クラス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1194c-144">Right-click the DynamicSample project and point to **Add**, and then click **Class**.</span></span> <span data-ttu-id="1194c-145">**[名前]** ボックスに `ReadOnlyFile` と入力して、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1194c-145">In the **Name** box, type `ReadOnlyFile`, and then click **OK**.</span></span> <span data-ttu-id="1194c-146">ReadOnlyFile クラスを含んだ新しいファイルが追加されます。</span><span class="sxs-lookup"><span data-stu-id="1194c-146">A new file is added that contains the ReadOnlyFile class.</span></span>  
  
5.  <span data-ttu-id="1194c-147">ReadOnlyFile.cs ファイルまたは ReadOnlyFile.vb ファイルの先頭に、次のコードを追加して <xref:System.IO?displayProperty=nameWithType> および <xref:System.Dynamic?displayProperty=nameWithType> 名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="1194c-147">At the top of the ReadOnlyFile.cs or ReadOnlyFile.vb file, add the following code to import the <xref:System.IO?displayProperty=nameWithType> and <xref:System.Dynamic?displayProperty=nameWithType> namespaces.</span></span>  
  
     [!code-csharp[VbDynamicWalkthrough#1](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_1.cs)]

     [!code-vb[VbDynamicWalkthrough#1](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_1.vb)]  
  
6.  <span data-ttu-id="1194c-148">カスタム動的オブジェクトでは、列挙型を使用して検索条件を決定します。</span><span class="sxs-lookup"><span data-stu-id="1194c-148">The custom dynamic object uses an enum to determine the search criteria.</span></span> <span data-ttu-id="1194c-149">クラス ステートメントの前に、次の列挙定義を追加します。</span><span class="sxs-lookup"><span data-stu-id="1194c-149">Before the class statement, add the following enum definition.</span></span>  
  
     [!code-csharp[VbDynamicWalkthrough#2](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_2.cs)]

     [!code-vb[VbDynamicWalkthrough#2](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_2.vb)]  
  
7.  <span data-ttu-id="1194c-150">次のコード例に示すように、クラス ステートメントを更新して `DynamicObject` クラスを継承します。</span><span class="sxs-lookup"><span data-stu-id="1194c-150">Update the class statement to inherit the `DynamicObject` class, as shown in the following code example.</span></span>  
  
     [!code-csharp[VbDynamicWalkthrough#3](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_3.cs)]

     [!code-vb[VbDynamicWalkthrough#3](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_3.vb)]  
  
8.  <span data-ttu-id="1194c-151">`ReadOnlyFile` クラスに次のコードを追加して、 ファイル パスのプライベート フィールドと、`ReadOnlyFile` クラスのコンス トラクターを定義します。</span><span class="sxs-lookup"><span data-stu-id="1194c-151">Add the following code to the `ReadOnlyFile` class to define a private field for the file path and a constructor for the `ReadOnlyFile` class.</span></span>  
  
     [!code-csharp[VbDynamicWalkthrough#4](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_4.cs)]
     
     [!code-vb[VbDynamicWalkthrough#4](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_4.vb)]  
  
9. <span data-ttu-id="1194c-152">次の `GetPropertyValue` メソッドを `ReadOnlyFile` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="1194c-152">Add the following `GetPropertyValue` method to the `ReadOnlyFile` class.</span></span> <span data-ttu-id="1194c-153">`GetPropertyValue` メソッドは検索条件を (入力として) 受け取り、テキスト ファイルから検索条件に一致する行を返します。</span><span class="sxs-lookup"><span data-stu-id="1194c-153">The `GetPropertyValue` method takes, as input, search criteria and returns the lines from a text file that match that search criteria.</span></span> <span data-ttu-id="1194c-154">`ReadOnlyFile` クラスによって提供される動的メソッドは、`GetPropertyValue` メソッドを呼び出して、それぞれの結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="1194c-154">The dynamic methods provided by the `ReadOnlyFile` class call the `GetPropertyValue` method to retrieve their respective results.</span></span>  
  
     [!code-csharp[VbDynamicWalkthrough#5](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_5.cs)]
     
     [!code-vb[VbDynamicWalkthrough#5](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_5.vb)]  
  
10. <span data-ttu-id="1194c-155">`GetPropertyValue` メソッドの後に、<xref:System.Dynamic.DynamicObject> クラスの <xref:System.Dynamic.DynamicObject.TryGetMember%2A> メソッドをオーバーライドする次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1194c-155">After the `GetPropertyValue` method, add the following code to override the <xref:System.Dynamic.DynamicObject.TryGetMember%2A> method of the <xref:System.Dynamic.DynamicObject> class.</span></span> <span data-ttu-id="1194c-156"><xref:System.Dynamic.DynamicObject.TryGetMember%2A> メソッドは、動的クラスのメンバーが要求され、引数が指定されていない場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="1194c-156">The <xref:System.Dynamic.DynamicObject.TryGetMember%2A> method is called when a member of a dynamic class is requested and no arguments are specified.</span></span> <span data-ttu-id="1194c-157">`binder` 引数には、参照されているメンバーに関する情報が含まれます。`result` 引数は、指定したメンバーに対して返された結果を参照します。</span><span class="sxs-lookup"><span data-stu-id="1194c-157">The `binder` argument contains information about the referenced member, and the `result` argument references the result returned for the specified member.</span></span> <span data-ttu-id="1194c-158"><xref:System.Dynamic.DynamicObject.TryGetMember%2A> メソッドはブール値を返します。要求されたメンバーが存在する場合には `true` を返し、その他の場合には `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="1194c-158">The <xref:System.Dynamic.DynamicObject.TryGetMember%2A> method returns a Boolean value that returns `true` if the requested member exists; otherwise it returns `false`.</span></span>  
  
     [!code-csharp[VbDynamicWalkthrough#6](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_6.cs)]
     
     [!code-vb[VbDynamicWalkthrough#6](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_6.vb)]  
  
11. <span data-ttu-id="1194c-159">`TryGetMember` メソッドの後に、<xref:System.Dynamic.DynamicObject> クラスの <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> メソッドをオーバーライドする次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1194c-159">After the `TryGetMember` method, add the following code to override the <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> method of the <xref:System.Dynamic.DynamicObject> class.</span></span> <span data-ttu-id="1194c-160"><xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> メソッドは、動的クラスのメンバーが引数を使用して要求された場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="1194c-160">The <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> method is called when a member of a dynamic class is requested with arguments.</span></span> <span data-ttu-id="1194c-161">`binder` 引数には、参照されているメンバーに関する情報が含まれます。`result` 引数は、指定したメンバーに対して返された結果を参照します。</span><span class="sxs-lookup"><span data-stu-id="1194c-161">The `binder` argument contains information about the referenced member, and the `result` argument references the result returned for the specified member.</span></span> <span data-ttu-id="1194c-162">`args` 引数には、メンバーに渡される引数の配列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1194c-162">The `args` argument contains an array of the arguments that are passed to the member.</span></span> <span data-ttu-id="1194c-163"><xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> メソッドはブール値を返します。要求されたメンバーが存在する場合には `true` を返し、その他の場合には `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="1194c-163">The <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> method returns a Boolean value that returns `true` if the requested member exists; otherwise it returns `false`.</span></span>  
  
     <span data-ttu-id="1194c-164">`TryInvokeMember` メソッドのカスタム バージョンは、1 つ目の引数として、前の手順で定義した `StringSearchOption` 列挙からの値を受け付けます。</span><span class="sxs-lookup"><span data-stu-id="1194c-164">The custom version of the `TryInvokeMember` method expects the first argument to be a value from the `StringSearchOption` enum that you defined in a previous step.</span></span> <span data-ttu-id="1194c-165">`TryInvokeMember` メソッドは、2 つ目の引数としてブール値を受け付けます。</span><span class="sxs-lookup"><span data-stu-id="1194c-165">The `TryInvokeMember` method expects the second argument to be a Boolean value.</span></span> <span data-ttu-id="1194c-166">引数の一方または両方が有効な値であれば、それらが `GetPropertyValue` メソッドに渡され、結果が取得されます。</span><span class="sxs-lookup"><span data-stu-id="1194c-166">If one or both arguments are valid values, they are passed to the `GetPropertyValue` method to retrieve the results.</span></span>  
  
     [!code-csharp[VbDynamicWalkthrough#7](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_7.cs)]
     
     [!code-vb[VbDynamicWalkthrough#7](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_7.vb)]  
  
12. <span data-ttu-id="1194c-167">ファイルを保存して閉じます。</span><span class="sxs-lookup"><span data-stu-id="1194c-167">Save and close the file.</span></span>  
  
#### <a name="to-create-a-sample-text-file"></a><span data-ttu-id="1194c-168">サンプルのテキスト ファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="1194c-168">To create a sample text file</span></span>  
  
1.  <span data-ttu-id="1194c-169">DynamicSample プロジェクトを右クリックし、**[追加]** をポイントした後、**[新しい項目]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1194c-169">Right-click the DynamicSample project and point to **Add**, and then click **New Item**.</span></span> <span data-ttu-id="1194c-170">**[インストールされたテンプレート]** ペインで **[全般]** をクリックし、**[テキスト ファイル]** テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="1194c-170">In the **Installed Templates** pane, select **General**, and then select the **Text File** template.</span></span> <span data-ttu-id="1194c-171">**[名前]** ボックスで、既定の名前である TextFile1.txt をそのままにし、**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1194c-171">Leave the default name of TextFile1.txt in the **Name** box, and then click **Add**.</span></span> <span data-ttu-id="1194c-172">新しいテキスト ファイルがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="1194c-172">A new text file is added to the project.</span></span>  
  
2.  <span data-ttu-id="1194c-173">TextFile1.txt ファイルに次のテキストをコピーします。</span><span class="sxs-lookup"><span data-stu-id="1194c-173">Copy the following text to the TextFile1.txt file.</span></span>  
  
    ```  
    List of customers and suppliers  
  
    Supplier: Lucerne Publishing (http://www.lucernepublishing.com/)  
    Customer: Preston, Chris  
    Customer: Hines, Patrick  
    Customer: Cameron, Maria  
    Supplier: Graphic Design Institute (http://www.graphicdesigninstitute.com/)   
    Supplier: Fabrikam, Inc. (http://www.fabrikam.com/)   
    Customer: Seubert, Roxanne  
    Supplier: Proseware, Inc. (http://www.proseware.com/)   
    Customer: Adolphi, Stephan  
    Customer: Koch, Paul  
    ```  
  
3.  <span data-ttu-id="1194c-174">ファイルを保存して閉じます。</span><span class="sxs-lookup"><span data-stu-id="1194c-174">Save and close the file.</span></span>  
  
#### <a name="to-create-a-sample-application-that-uses-the-custom-dynamic-object"></a><span data-ttu-id="1194c-175">カスタム動的オブジェクトを使用するサンプル アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="1194c-175">To create a sample application that uses the custom dynamic object</span></span>  
  
1.  <span data-ttu-id="1194c-176">**ソリューション エクスプ ローラー**で、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] を使用している場合は Module1.vb ファイルを、Visual C# を使用している場合は Program.cs ファイルをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="1194c-176">In **Solution Explorer**, double-click the Module1.vb file if you are using [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] or the Program.cs file if you are using Visual C#.</span></span>  
  
2.  <span data-ttu-id="1194c-177">Main プロシージャに次のコードを追加して、TextFile1.txt ファイルの `ReadOnlyFile` クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1194c-177">Add the following code to the Main procedure to create an instance of the `ReadOnlyFile` class for the TextFile1.txt file.</span></span> <span data-ttu-id="1194c-178">このコードは、遅延バインディングを使用して動的メンバーを呼び出し、"Customer" という文字列を含んだテキスト行を取得します。</span><span class="sxs-lookup"><span data-stu-id="1194c-178">The code uses late binding to call dynamic members and retrieve lines of text that contain the string "Customer".</span></span>  
  
     [!code-csharp[VbDynamicWalkthrough#8](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_8.cs)]
     
     [!code-vb[VbDynamicWalkthrough#8](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_8.vb)]  
  
3.  <span data-ttu-id="1194c-179">ファイルを保存し、Ctrl キーを押しながら F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="1194c-179">Save the file and press CTRL+F5 to build and run the application.</span></span>  
  
## <a name="calling-a-dynamic-language-library"></a><span data-ttu-id="1194c-180">動的言語ライブラリの呼び出し</span><span class="sxs-lookup"><span data-stu-id="1194c-180">Calling a Dynamic Language Library</span></span>  

<span data-ttu-id="1194c-181">このチュートリアルで作成する次のプロジェクトでは、動的言語 IronPython で記述されたライブラリにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="1194c-181">The next project that you create in this walkthrough accesses a library that is written in the dynamic language IronPython.</span></span>
  
#### <a name="to-create-a-custom-dynamic-class"></a><span data-ttu-id="1194c-182">カスタムの動的クラスを作成するには</span><span class="sxs-lookup"><span data-stu-id="1194c-182">To create a custom dynamic class</span></span>  
  
1.  <span data-ttu-id="1194c-183">[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] で、**[ファイル]** メニューの **[新規作成]**をポイントし、 **[プロジェクト]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1194c-183">In [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="1194c-184">**[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、**[Windows]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1194c-184">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="1194c-185">**[テンプレート]** ペインの **[コンソール アプリケーション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1194c-185">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="1194c-186">**[名前]** ボックスに `DynamicIronPythonSample` と入力して、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1194c-186">In the **Name** box, type `DynamicIronPythonSample`, and then click **OK**.</span></span> <span data-ttu-id="1194c-187">新しいプロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1194c-187">The new project is created.</span></span>  
  
3.  <span data-ttu-id="1194c-188">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] を使用している場合は、 DynamicIronPythonSample プロジェクトを右クリックし、**[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1194c-188">If you are using [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], right-click the DynamicIronPythonSample project and then click **Properties**.</span></span> <span data-ttu-id="1194c-189">**[参照]** タブをクリックします。**[追加]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1194c-189">Click the **References** tab. Click the **Add** button.</span></span> <span data-ttu-id="1194c-190">Visual C# を使用している場合は、**ソリューション エクスプローラー**で **[参照]** フォルダーを右クリックし、**[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1194c-190">If you are using Visual C#, in **Solution Explorer**, right-click the **References** folder and then click **Add Reference**.</span></span>  
  
4.  <span data-ttu-id="1194c-191">**[参照]** タブで、IronPython ライブラリがインストールされているフォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="1194c-191">On the **Browse** tab, browse to the folder where the IronPython libraries are installed.</span></span> <span data-ttu-id="1194c-192">たとえば、 C:\Program Files\IronPython 2.6 for .NET 4.0 です。</span><span class="sxs-lookup"><span data-stu-id="1194c-192">For example, C:\Program Files\IronPython 2.6 for .NET 4.0.</span></span> <span data-ttu-id="1194c-193">**IronPython.dll**、**IronPython.Modules.dll**、**Microsoft.Scripting.dll**、および **Microsoft.Dynamic.dll** ライブラリを選択します。</span><span class="sxs-lookup"><span data-stu-id="1194c-193">Select the **IronPython.dll**, **IronPython.Modules.dll**, **Microsoft.Scripting.dll**, and **Microsoft.Dynamic.dll** libraries.</span></span> <span data-ttu-id="1194c-194">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1194c-194">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="1194c-195">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] を使用している場合は、Module1.vb ファイルを編集します。</span><span class="sxs-lookup"><span data-stu-id="1194c-195">If you are using [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], edit the Module1.vb file.</span></span> <span data-ttu-id="1194c-196">Visual C# を使用している場合は、Program.cs ファイルを編集します。</span><span class="sxs-lookup"><span data-stu-id="1194c-196">If you are using Visual C#, edit the Program.cs file.</span></span>  
  
6.  <span data-ttu-id="1194c-197">ファイルの先頭に、IronPython ライブラリから `Microsoft.Scripting.Hosting` および `IronPython.Hosting` 名前空間をインポートするための次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1194c-197">At the top of the file, add the following code to import the `Microsoft.Scripting.Hosting` and `IronPython.Hosting` namespaces from the IronPython libraries.</span></span>  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#1](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_9.cs)]
     
     [!code-vb[VbDynamicWalkthroughIronPython#1](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_9.vb)]  
  
7.  <span data-ttu-id="1194c-198">Main メソッドで、IronPython ライブラリをホストする新しい `Microsoft.Scripting.Hosting.ScriptRuntime` オブジェクトを作成するための次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1194c-198">In the Main method, add the following code to create a new `Microsoft.Scripting.Hosting.ScriptRuntime` object to host the IronPython libraries.</span></span> <span data-ttu-id="1194c-199">`ScriptRuntime` オブジェクトは、IronPython ライブラリ モジュール random.py を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="1194c-199">The `ScriptRuntime` object loads the IronPython library module random.py.</span></span>  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#2](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_10.cs)]
     
     [!code-vb[VbDynamicWalkthroughIronPython#2](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_10.vb)]  
  
8.  <span data-ttu-id="1194c-200">Random.py モジュールを読み込むコードの後に、整数の配列を作成する次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1194c-200">After the code to load the random.py module, add the following code to create an array of integers.</span></span> <span data-ttu-id="1194c-201">配列は random.py モジュールの `shuffle` メソッドに渡されます。このメソッドは、配列内の値をランダムに並べ替えします。</span><span class="sxs-lookup"><span data-stu-id="1194c-201">The array is passed to the `shuffle` method of the random.py module, which randomly sorts the values in the array.</span></span>  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#3](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_11.cs)]
     
     [!code-vb[VbDynamicWalkthroughIronPython#3](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_11.vb)]  
  
9. <span data-ttu-id="1194c-202">ファイルを保存し、Ctrl キーを押しながら F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="1194c-202">Save the file and press CTRL+F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1194c-203">関連項目</span><span class="sxs-lookup"><span data-stu-id="1194c-203">See Also</span></span>  
 <xref:System.Dynamic?displayProperty=nameWithType>  
 <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>  
 [<span data-ttu-id="1194c-204">dynamic 型の使用</span><span class="sxs-lookup"><span data-stu-id="1194c-204">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [<span data-ttu-id="1194c-205">事前バインディングと遅延バインディング</span><span class="sxs-lookup"><span data-stu-id="1194c-205">Early and Late Binding</span></span>](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [<span data-ttu-id="1194c-206">dynamic</span><span class="sxs-lookup"><span data-stu-id="1194c-206">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)  
 [<span data-ttu-id="1194c-207">動的インターフェイスを実装する (外部ブログ)</span><span class="sxs-lookup"><span data-stu-id="1194c-207">Implementing Dynamic Interfaces (external blog)</span></span>](http://go.microsoft.com/fwlink/?LinkId=230895)
