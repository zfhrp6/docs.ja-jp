---
title: 'チュートリアル: COM オブジェクトによる継承の実装 (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 10c6bdf46e351b23705107da3b693531718cfd37
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a><span data-ttu-id="04dca-102">チュートリアル: COM オブジェクトによる継承の実装 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04dca-102">Walkthrough: Implementing Inheritance with COM Objects (Visual Basic)</span></span>
<span data-ttu-id="04dca-103">Visual Basic クラスを派生させることができます`Public`も以前のバージョンの Visual Basic で作成された COM オブジェクトのクラスです。</span><span class="sxs-lookup"><span data-stu-id="04dca-103">You can derive Visual Basic classes from `Public` classes in COM objects, even those created in earlier versions of Visual Basic.</span></span> <span data-ttu-id="04dca-104">プロパティと COM オブジェクトから継承されたクラスのメソッドをオーバーライドまたはプロパティと同様にオーバー ロード、およびその他の任意の基本クラスのメソッドをオーバーライドまたはオーバー ロードできます。</span><span class="sxs-lookup"><span data-stu-id="04dca-104">The properties and methods of classes inherited from COM objects can be overridden or overloaded just as properties and methods of any other base class can be overridden or overloaded.</span></span> <span data-ttu-id="04dca-105">COM オブジェクトからの継承は、再コンパイルしたくない既存のクラス ライブラリがある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="04dca-105">Inheritance from COM objects is useful when you have an existing class library that you do not want to recompile.</span></span>  
  
 <span data-ttu-id="04dca-106">次の手順では、Visual Basic 6.0 を使用して、クラスが含まれている COM オブジェクトを作成し、基底クラスとして使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="04dca-106">The following procedure shows how to use Visual Basic 6.0 to create a COM object that contains a class, and then use it as a base class.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a><span data-ttu-id="04dca-107">このチュートリアルで使用されている COM オブジェクトを構築するには</span><span class="sxs-lookup"><span data-stu-id="04dca-107">To build the COM object that is used in this walkthrough</span></span>  
  
1.  <span data-ttu-id="04dca-108">Visual Basic 6.0 では、新しい ActiveX DLL プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="04dca-108">In Visual Basic 6.0, open a new ActiveX DLL project.</span></span> <span data-ttu-id="04dca-109">という名前のプロジェクト`Project1`を作成します。</span><span class="sxs-lookup"><span data-stu-id="04dca-109">A project named `Project1` is created.</span></span> <span data-ttu-id="04dca-110">という名前のクラスがある`Class1`です。</span><span class="sxs-lookup"><span data-stu-id="04dca-110">It has a class named `Class1`.</span></span>  
  
2.  <span data-ttu-id="04dca-111">**プロジェクト エクスプ ローラー**を右クリックして**Project1**、クリックして**Project1 プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="04dca-111">In the **Project Explorer**, right-click **Project1**, and then click **Project1 Properties**.</span></span> <span data-ttu-id="04dca-112">**プロジェクト プロパティ** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="04dca-112">The **Project Properties** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="04dca-113">**全般**のタブ、**プロジェクトのプロパティ** ダイアログ ボックスで、プロジェクトの名前を入力して変更`ComObject1`で、**プロジェクト名**フィールドです。</span><span class="sxs-lookup"><span data-stu-id="04dca-113">On the **General** tab of the **Project Properties** dialog box, change the project name by typing `ComObject1` in the **Project Name** field.</span></span>  
  
4.  <span data-ttu-id="04dca-114">**プロジェクト エクスプ ローラー**を右クリックして`Class1`、クリックして**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="04dca-114">In the **Project Explorer**, right-click `Class1`, and then click **Properties**.</span></span> <span data-ttu-id="04dca-115">**プロパティ**クラスのウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="04dca-115">The **Properties** window for the class is displayed.</span></span>  
  
5.  <span data-ttu-id="04dca-116">変更、`Name`プロパティを`MathFunctions`です。</span><span class="sxs-lookup"><span data-stu-id="04dca-116">Change the `Name` property to `MathFunctions`.</span></span>  
  
6.  <span data-ttu-id="04dca-117">**プロジェクト エクスプ ローラー**を右クリックして`MathFunctions`、クリックして**コードの表示**です。</span><span class="sxs-lookup"><span data-stu-id="04dca-117">In the **Project Explorer**, right-click `MathFunctions`, and then click **View Code**.</span></span> <span data-ttu-id="04dca-118">**コード エディター**が表示されます。</span><span class="sxs-lookup"><span data-stu-id="04dca-118">The **Code Editor** is displayed.</span></span>  
  
7.  <span data-ttu-id="04dca-119">プロパティの値を保持するローカル変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="04dca-119">Add a local variable to hold the property value:</span></span>  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  <span data-ttu-id="04dca-120">プロパティを追加`Let`およびプロパティ`Get`プロパティ プロシージャ。</span><span class="sxs-lookup"><span data-stu-id="04dca-120">Add Property `Let` and Property `Get` property procedures:</span></span>  
  
    ```  
    Public Property Let Prop1(ByVal vData As Integer)  
       'Used when assigning a value to the property.  
       mvarProp1 = vData  
    End Property  
    Public Property Get Prop1() As Integer  
       'Used when retrieving a property's value.  
       Prop1 = mvarProp1  
    End Property  
    ```  
  
9. <span data-ttu-id="04dca-121">関数を追加するには。</span><span class="sxs-lookup"><span data-stu-id="04dca-121">Add a function:</span></span>  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. <span data-ttu-id="04dca-122">作成しをクリックして、COM オブジェクトを登録**ように ComObject1.dll**上、**ファイル**メニュー。</span><span class="sxs-lookup"><span data-stu-id="04dca-122">Create and register the COM object by clicking **Make ComObject1.dll** on the **File** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="04dca-123">COM オブジェクトとして Visual Basic で作成したクラスを公開することが true COM オブジェクトではないと、このチュートリアルでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="04dca-123">Although you can also expose a class created with Visual Basic as a COM object, it is not a true COM object and cannot be used in this walkthrough.</span></span> <span data-ttu-id="04dca-124">詳細については、「 [.NET Framework アプリケーションにおける COM 相互運用性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)です。</span><span class="sxs-lookup"><span data-stu-id="04dca-124">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="interop-assemblies"></a><span data-ttu-id="04dca-125">相互運用機能アセンブリ</span><span class="sxs-lookup"><span data-stu-id="04dca-125">Interop Assemblies</span></span>  
 <span data-ttu-id="04dca-126">次の手順では、(COM オブジェクトなど) のアンマネージ コードとマネージ コード間の仲介役として機能する、相互運用機能アセンブリを作成します[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]を使用します。</span><span class="sxs-lookup"><span data-stu-id="04dca-126">In the following procedure, you will create an interop assembly, which acts as a bridge between unmanaged code (such as a COM object) and the managed code [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] uses.</span></span> <span data-ttu-id="04dca-127">Visual Basic によって作成される相互運用機能アセンブリでは、ように、COM オブジェクトの操作の詳細を処理*相互運用マーシャ リング*、パッケージ パラメーターと戻り値を等価のデータの処理の種類に移動してCOM オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="04dca-127">The interop assembly that Visual Basic creates handles many of the details of working with COM objects, such as *interop marshaling*, the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="04dca-128">Visual Basic アプリケーション内の参照は、実際の COM オブジェクトではなく、相互運用機能アセンブリを指します。</span><span class="sxs-lookup"><span data-stu-id="04dca-128">The reference in the Visual Basic application points to the interop assembly, not the actual COM object.</span></span>  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a><span data-ttu-id="04dca-129">Visual Basic 2005 およびそれ以降のバージョンで COM オブジェクトを使用するには</span><span class="sxs-lookup"><span data-stu-id="04dca-129">To use a COM object with Visual Basic 2005 and later versions</span></span>  
  
1.  <span data-ttu-id="04dca-130">新しい Visual Basic Windows アプリケーション プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="04dca-130">Open a new Visual Basic Windows Application project.</span></span>  
  
2.  <span data-ttu-id="04dca-131">**[プロジェクト]** メニューの **[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="04dca-131">On the **Project** menu, click **Add Reference**.</span></span>  
  
     <span data-ttu-id="04dca-132">**[参照の追加]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="04dca-132">The **Add Reference** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="04dca-133">**COM**  タブをダブルクリックして`ComObject1`で、**コンポーネント名**を一覧表示し、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="04dca-133">On the **COM** tab, double-click `ComObject1` in the **Component Name** list and click **OK**.</span></span>  
  
4.  <span data-ttu-id="04dca-134">**[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="04dca-134">On the **Project** menu, click **Add New Item**.</span></span>  
  
     <span data-ttu-id="04dca-135">**[新しい項目の追加]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="04dca-135">The **Add New Item** dialog box is displayed.</span></span>  
  
5.  <span data-ttu-id="04dca-136">**テンプレート** ウィンドウで、をクリックして**クラス**です。</span><span class="sxs-lookup"><span data-stu-id="04dca-136">In the **Templates** pane, click **Class**.</span></span>  
  
     <span data-ttu-id="04dca-137">既定のファイル名、`Class1.vb`に表示されます、**名前**フィールドです。</span><span class="sxs-lookup"><span data-stu-id="04dca-137">The default file name, `Class1.vb`, appears in the **Name** field.</span></span> <span data-ttu-id="04dca-138">このフィールドは MathClass.vb をクリックして変更**追加**です。</span><span class="sxs-lookup"><span data-stu-id="04dca-138">Change this field to MathClass.vb and click **Add**.</span></span> <span data-ttu-id="04dca-139">これがという名前のクラスを作成`MathClass`、し、そのコードを表示します。</span><span class="sxs-lookup"><span data-stu-id="04dca-139">This creates a class named `MathClass`, and displays its code.</span></span>  
  
6.  <span data-ttu-id="04dca-140">先頭に次のコードを追加`MathClass`COM クラスから継承します。</span><span class="sxs-lookup"><span data-stu-id="04dca-140">Add the following code to the top of `MathClass` to inherit from the COM class.</span></span>  
  
     [!code-vb[VbVbalrInterop#31](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]  
  
7.  <span data-ttu-id="04dca-141">次のコードを追加することで、基本クラスのパブリック メソッドをオーバー ロード`MathClass`:</span><span class="sxs-lookup"><span data-stu-id="04dca-141">Overload the public method of the base class by adding the following code to `MathClass`:</span></span>  
  
     [!code-vb[VbVbalrInterop#32](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]  
  
8.  <span data-ttu-id="04dca-142">次のコードを追加することで、継承されたクラスを拡張`MathClass`:</span><span class="sxs-lookup"><span data-stu-id="04dca-142">Extend the inherited class by adding the following code to `MathClass`:</span></span>  
  
     [!code-vb[VbVbalrInterop#33](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]  
  
 <span data-ttu-id="04dca-143">新しいクラス、COM オブジェクトの基本クラスのプロパティを継承するには、メソッドをオーバー ロードおよびクラスを拡張する新しいメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="04dca-143">The new class inherits the properties of the base class in the COM object, overloads a method, and defines a new method to extend the class.</span></span>  
  
#### <a name="to-test-the-inherited-class"></a><span data-ttu-id="04dca-144">継承されたクラスをテストするには</span><span class="sxs-lookup"><span data-stu-id="04dca-144">To test the inherited class</span></span>  
  
1.  <span data-ttu-id="04dca-145">スタートアップ フォームにボタンを追加しをダブルクリックすると、そのコードを表示します。</span><span class="sxs-lookup"><span data-stu-id="04dca-145">Add a button to your startup form, and then double-click it to view its code.</span></span>  
  
2.  <span data-ttu-id="04dca-146">ボタンの`Click`イベント ハンドラーのプロシージャのインスタンスを作成する次のコードを追加`MathClass`オーバー ロードされたメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="04dca-146">In the button's `Click` event handler procedure, add the following code to create an instance of `MathClass` and call the overloaded methods:</span></span>  
  
     [!code-vb[VbVbalrInterop#34](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]  
  
3.  <span data-ttu-id="04dca-147">F5 キーを押してプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="04dca-147">Run the project by pressing F5.</span></span>  
  
 <span data-ttu-id="04dca-148">フォーム上のボタンをクリックすると、`AddNumbers`メソッドが呼び出された最初`Short`データ型の数値、Visual Basic は、基本クラスから、適切なメソッドを選択します。</span><span class="sxs-lookup"><span data-stu-id="04dca-148">When you click the button on the form, the `AddNumbers` method is first called with `Short` data type numbers, and Visual Basic chooses the appropriate method from the base class.</span></span> <span data-ttu-id="04dca-149">2 番目の呼び出し`AddNumbers`からは、オーバー ロード メソッドに送られます`MathClass`です。</span><span class="sxs-lookup"><span data-stu-id="04dca-149">The second call to `AddNumbers` is directed to the overload method from `MathClass`.</span></span> <span data-ttu-id="04dca-150">3 番目の呼び出しの呼び出し、`SubtractNumbers`メソッドで、クラスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="04dca-150">The third call calls the `SubtractNumbers` method, which extends the class.</span></span> <span data-ttu-id="04dca-151">基本クラスのプロパティが設定され、値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="04dca-151">The property in the base class is set, and the value is displayed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="04dca-152">次の手順</span><span class="sxs-lookup"><span data-stu-id="04dca-152">Next Steps</span></span>  
 <span data-ttu-id="04dca-153">お気付きをオーバー ロードされた`AddNumbers`と同じデータ型、COM オブジェクトの基本クラスから継承されたメソッドに関数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="04dca-153">You may have noticed that the overloaded `AddNumbers` function appears to have the same data type as the method inherited from the base class of the COM object.</span></span> <span data-ttu-id="04dca-154">これは、引数と、基底クラス メソッドのパラメーターは、Visual Basic 6.0 の 16 ビット整数値として定義されますが、型の 16 ビット整数として公開されるため`Short`Visual Basic のそれ以降のバージョン。</span><span class="sxs-lookup"><span data-stu-id="04dca-154">This is because the arguments and parameters of the base class method are defined as 16-bit integers in Visual Basic 6.0, but they are exposed as 16-bit integers of type `Short` in later versions of Visual Basic.</span></span> <span data-ttu-id="04dca-155">新しい関数では、32 ビット整数値を受け入れるし、基本クラスの関数をオーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="04dca-155">The new function accepts 32-bit integers, and overloads the base class function.</span></span>  
  
 <span data-ttu-id="04dca-156">COM オブジェクトを使用する場合は、パラメーターのサイズとデータ型を確認することを確認します。</span><span class="sxs-lookup"><span data-stu-id="04dca-156">When working with COM objects, make sure that you verify the size and data types of parameters.</span></span> <span data-ttu-id="04dca-157">たとえば、Visual Basic 6.0 コレクション オブジェクトを引数として受け取りを COM オブジェクトを使用しているときに、以降のバージョンの Visual Basic からコレクションを提供できません。</span><span class="sxs-lookup"><span data-stu-id="04dca-157">For example, when you are using a COM object that accepts a Visual Basic 6.0 collection object as an argument, you cannot provide a collection from a later version of Visual Basic.</span></span>  
  
 <span data-ttu-id="04dca-158">プロパティとメソッドが COM クラスから継承したオーバーライドできます、つまり、ローカル プロパティまたはプロパティを置換するメソッドまたは COM の基本クラスから継承されたメソッドを宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="04dca-158">Properties and methods inherited from COM classes can be overridden, meaning that you can declare a local property or method that replaces a property or method inherited from a base COM class.</span></span> <span data-ttu-id="04dca-159">継承された COM プロパティをオーバーライドするため規則は、他のプロパティと、次の例外を持つメソッドをオーバーライドするための規則に似ています。</span><span class="sxs-lookup"><span data-stu-id="04dca-159">The rules for overriding inherited COM properties are similar to the rules for overriding other properties and methods with the following exceptions:</span></span>  
  
-   <span data-ttu-id="04dca-160">任意のプロパティや、COM クラスから継承されたメソッドをオーバーライドする場合は、その他のすべての継承されたプロパティとメソッドをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="04dca-160">If you override any property or method inherited from a COM class, you must override all the other inherited properties and methods.</span></span>  
  
-   <span data-ttu-id="04dca-161">使用するプロパティ`ByRef`パラメーターをオーバーライドすることはできません。</span><span class="sxs-lookup"><span data-stu-id="04dca-161">Properties that use `ByRef` parameters cannot be overridden.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04dca-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="04dca-162">See Also</span></span>  
 [<span data-ttu-id="04dca-163">.NET Framework アプリケーションにおける COM 相互運用性</span><span class="sxs-lookup"><span data-stu-id="04dca-163">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [<span data-ttu-id="04dca-164">Inherits ステートメント</span><span class="sxs-lookup"><span data-stu-id="04dca-164">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="04dca-165">Short データ型</span><span class="sxs-lookup"><span data-stu-id="04dca-165">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
