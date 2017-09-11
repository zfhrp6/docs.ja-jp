---
title: "チュートリアル: COM オブジェクト (Visual Basic) での継承を実装する |Microsoft ドキュメント"
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
- inheritance, COM reusability
- base classes, COM reusability
- inheritance, walkthroughs
- derived classes, COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
caps.latest.revision: 16
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
ms.openlocfilehash: 0e816d1728678467d930de524b894d175f9b0c0a
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a><span data-ttu-id="b525c-102">チュートリアル: COM オブジェクトによる継承の実装 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b525c-102">Walkthrough: Implementing Inheritance with COM Objects (Visual Basic)</span></span>
<span data-ttu-id="b525c-103">Visual Basic クラスを派生する`Public`でもの以前のバージョンで作成された COM オブジェクトのクラス[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="b525c-103">You can derive Visual Basic classes from `Public` classes in COM objects, even those created in earlier versions of [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="b525c-104">プロパティと COM オブジェクトから継承されたクラスのメソッドをオーバーライドまたはプロパティと同じようにオーバー ロード、およびその他の基本クラスのメソッドをオーバーライドまたはオーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="b525c-104">The properties and methods of classes inherited from COM objects can be overridden or overloaded just as properties and methods of any other base class can be overridden or overloaded.</span></span> <span data-ttu-id="b525c-105">COM オブジェクトからの継承は、再コンパイルしない既存のクラス ライブラリがある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="b525c-105">Inheritance from COM objects is useful when you have an existing class library that you do not want to recompile.</span></span>  
  
 <span data-ttu-id="b525c-106">次の手順では、Visual Basic 6.0 を使用して、クラスが含まれている COM オブジェクトを作成し、基本クラスとして使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b525c-106">The following procedure shows how to use Visual Basic 6.0 to create a COM object that contains a class, and then use it as a base class.</span></span>  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a><span data-ttu-id="b525c-107">このチュートリアルで使用される COM オブジェクトを構築するには</span><span class="sxs-lookup"><span data-stu-id="b525c-107">To build the COM object that is used in this walkthrough</span></span>  
  
1.  <span data-ttu-id="b525c-108">Visual Basic 6.0 では、新しい ActiveX DLL プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="b525c-108">In Visual Basic 6.0, open a new ActiveX DLL project.</span></span> <span data-ttu-id="b525c-109">という名前のプロジェクト`Project1`が作成されます。</span><span class="sxs-lookup"><span data-stu-id="b525c-109">A project named `Project1` is created.</span></span> <span data-ttu-id="b525c-110">という名前のクラスがある`Class1`です。</span><span class="sxs-lookup"><span data-stu-id="b525c-110">It has a class named `Class1`.</span></span>  
  
2.  <span data-ttu-id="b525c-111">**プロジェクト エクスプ ローラー**を右クリックして**Project1**、クリックして**Project1 プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="b525c-111">In the **Project Explorer**, right-click **Project1**, and then click **Project1 Properties**.</span></span> <span data-ttu-id="b525c-112">**プロジェクトのプロパティ** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b525c-112">The **Project Properties** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="b525c-113">**全般**のタブ、**プロジェクトのプロパティ** ダイアログ ボックスで、」と入力して、プロジェクト名を変更`ComObject1`で、**プロジェクト名**フィールドです。</span><span class="sxs-lookup"><span data-stu-id="b525c-113">On the **General** tab of the **Project Properties** dialog box, change the project name by typing `ComObject1` in the **Project Name** field.</span></span>  
  
4.  <span data-ttu-id="b525c-114">**プロジェクト エクスプ ローラー**を右クリックして`Class1`、クリックして**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="b525c-114">In the **Project Explorer**, right-click `Class1`, and then click **Properties**.</span></span> <span data-ttu-id="b525c-115">**プロパティ**クラスのウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b525c-115">The **Properties** window for the class is displayed.</span></span>  
  
5.  <span data-ttu-id="b525c-116">変更、`Name`プロパティを`MathFunctions`します。</span><span class="sxs-lookup"><span data-stu-id="b525c-116">Change the `Name` property to `MathFunctions`.</span></span>  
  
6.  <span data-ttu-id="b525c-117">**プロジェクト エクスプ ローラー**を右クリックして`MathFunctions`、クリックして**コードの表示**します。</span><span class="sxs-lookup"><span data-stu-id="b525c-117">In the **Project Explorer**, right-click `MathFunctions`, and then click **View Code**.</span></span> <span data-ttu-id="b525c-118">**コード エディター**が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b525c-118">The **Code Editor** is displayed.</span></span>  
  
7.  <span data-ttu-id="b525c-119">プロパティ値を保持するローカル変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="b525c-119">Add a local variable to hold the property value:</span></span>  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  <span data-ttu-id="b525c-120">プロパティを追加`Let`とプロパティ`Get`プロパティ プロシージャ。</span><span class="sxs-lookup"><span data-stu-id="b525c-120">Add Property `Let` and Property `Get` property procedures:</span></span>  
  
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
  
9. <span data-ttu-id="b525c-121">関数を追加します。</span><span class="sxs-lookup"><span data-stu-id="b525c-121">Add a function:</span></span>  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. <span data-ttu-id="b525c-122">作成しをクリックして、COM オブジェクトを登録**、ComObject1.dll**上、**ファイル**メニュー。</span><span class="sxs-lookup"><span data-stu-id="b525c-122">Create and register the COM object by clicking **Make ComObject1.dll** on the **File** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b525c-123">作成したクラスを公開することもできます。 ただし[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]COM オブジェクトとして、真の COM オブジェクトではありませんし、このチュートリアルでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="b525c-123">Although you can also expose a class created with [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] as a COM object, it is not a true COM object and cannot be used in this walkthrough.</span></span> <span data-ttu-id="b525c-124">詳細については、「 [.NET Framework アプリケーションにおける COM 相互運用性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)します。</span><span class="sxs-lookup"><span data-stu-id="b525c-124">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="interop-assemblies"></a><span data-ttu-id="b525c-125">相互運用機能アセンブリ</span><span class="sxs-lookup"><span data-stu-id="b525c-125">Interop Assemblies</span></span>  
 <span data-ttu-id="b525c-126">次の手順では、COM オブジェクト) などのアンマネージ コードとマネージ コード間のブリッジとして機能する相互運用機能アセンブリを作成します[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]を使用します。</span><span class="sxs-lookup"><span data-stu-id="b525c-126">In the following procedure, you will create an interop assembly, which acts as a bridge between unmanaged code (such as a COM object) and the managed code [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] uses.</span></span> <span data-ttu-id="b525c-127">相互運用機能アセンブリを[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]などの COM の使用の詳細の多くのオブジェクトのハンドルが作成*相互運用マーシャ リング*、パッケージ パラメーターと戻り値を等価のデータの処理と COM オブジェクトの間で移動するための型します。</span><span class="sxs-lookup"><span data-stu-id="b525c-127">The interop assembly that [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] creates handles many of the details of working with COM objects, such as *interop marshaling*, the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="b525c-128">内の参照、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]実際の COM オブジェクトではなく、相互運用機能アセンブリをアプリケーションのポイント。</span><span class="sxs-lookup"><span data-stu-id="b525c-128">The reference in the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] application points to the interop assembly, not the actual COM object.</span></span>  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a><span data-ttu-id="b525c-129">Visual Basic 2005 およびそれ以降のバージョンで、COM オブジェクトを使用するには</span><span class="sxs-lookup"><span data-stu-id="b525c-129">To use a COM object with Visual Basic 2005 and later versions</span></span>  
  
1.  <span data-ttu-id="b525c-130">新しい[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Windows アプリケーション プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="b525c-130">Open a new [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] Windows Application project.</span></span>  
  
2.  <span data-ttu-id="b525c-131">**プロジェクト** メニューのをクリックして**参照の追加**します。</span><span class="sxs-lookup"><span data-stu-id="b525c-131">On the **Project** menu, click **Add Reference**.</span></span>  
  
     <span data-ttu-id="b525c-132">**参照の追加** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b525c-132">The **Add Reference** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="b525c-133">**COM**  タブをダブルクリックして`ComObject1`で、**コンポーネント名**を一覧表示し、クリックして**ok**します。</span><span class="sxs-lookup"><span data-stu-id="b525c-133">On the **COM** tab, double-click `ComObject1` in the **Component Name** list and click **OK**.</span></span>  
  
4.  <span data-ttu-id="b525c-134">**[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b525c-134">On the **Project** menu, click **Add New Item**.</span></span>  
  
     <span data-ttu-id="b525c-135">**新しい項目の追加** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b525c-135">The **Add New Item** dialog box is displayed.</span></span>  
  
5.  <span data-ttu-id="b525c-136">**テンプレート** ウィンドウで、をクリックして**クラス**します。</span><span class="sxs-lookup"><span data-stu-id="b525c-136">In the **Templates** pane, click **Class**.</span></span>  
  
     <span data-ttu-id="b525c-137">既定のファイル名`Class1.vb`に表示されます、**名前**フィールドです。</span><span class="sxs-lookup"><span data-stu-id="b525c-137">The default file name, `Class1.vb`, appears in the **Name** field.</span></span> <span data-ttu-id="b525c-138">このフィールドは変更をクリックして MathClass.vb**追加**します。</span><span class="sxs-lookup"><span data-stu-id="b525c-138">Change this field to MathClass.vb and click **Add**.</span></span> <span data-ttu-id="b525c-139">という名前のクラスを作成この`MathClass`、し、そのコードを表示します。</span><span class="sxs-lookup"><span data-stu-id="b525c-139">This creates a class named `MathClass`, and displays its code.</span></span>  
  
6.  <span data-ttu-id="b525c-140">先頭に次のコードを追加`MathClass`COM クラスから継承します。</span><span class="sxs-lookup"><span data-stu-id="b525c-140">Add the following code to the top of `MathClass` to inherit from the COM class.</span></span>  
  
     <span data-ttu-id="b525c-141">[!code-vb[VbVbalrInterop #&31;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b525c-141">[!code-vb[VbVbalrInterop#31](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]</span></span>  
  
7.  <span data-ttu-id="b525c-142">次のコードを追加することで、基本クラスのパブリック メソッドをオーバー ロード`MathClass`:</span><span class="sxs-lookup"><span data-stu-id="b525c-142">Overload the public method of the base class by adding the following code to `MathClass`:</span></span>  
  
     <span data-ttu-id="b525c-143">[!code-vb[VbVbalrInterop&#32;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="b525c-143">[!code-vb[VbVbalrInterop#32](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]</span></span>  
  
8.  <span data-ttu-id="b525c-144">次のコードを追加することで、継承されたクラスを拡張`MathClass`:</span><span class="sxs-lookup"><span data-stu-id="b525c-144">Extend the inherited class by adding the following code to `MathClass`:</span></span>  
  
     <span data-ttu-id="b525c-145">[!code-vb[VbVbalrInterop #&33;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="b525c-145">[!code-vb[VbVbalrInterop#33](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]</span></span>  
  
 <span data-ttu-id="b525c-146">新しいクラスは、COM オブジェクトの基本クラスのプロパティを継承し、メソッドをオーバー ロード、クラスを拡張する新しいメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="b525c-146">The new class inherits the properties of the base class in the COM object, overloads a method, and defines a new method to extend the class.</span></span>  
  
#### <a name="to-test-the-inherited-class"></a><span data-ttu-id="b525c-147">継承されたクラスをテストするには</span><span class="sxs-lookup"><span data-stu-id="b525c-147">To test the inherited class</span></span>  
  
1.  <span data-ttu-id="b525c-148">スタートアップ フォームにボタンを追加し、そのコードを表示することをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="b525c-148">Add a button to your startup form, and then double-click it to view its code.</span></span>  
  
2.  <span data-ttu-id="b525c-149">ボタンの`Click`イベント ハンドラーのプロシージャのインスタンスを作成するには、次のコードを追加`MathClass`オーバー ロードされたメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b525c-149">In the button's `Click` event handler procedure, add the following code to create an instance of `MathClass` and call the overloaded methods:</span></span>  
  
     <span data-ttu-id="b525c-150">[!code-vb[VbVbalrInterop #&34;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="b525c-150">[!code-vb[VbVbalrInterop#34](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]</span></span>  
  
3.  <span data-ttu-id="b525c-151">F5 キーを押して、プロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="b525c-151">Run the project by pressing F5.</span></span>  
  
 <span data-ttu-id="b525c-152">フォーム上のボタンをクリックすると、`AddNumbers`メソッドが呼び出された最初`Short`データ型の数字、および[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]基本クラスから適切な方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="b525c-152">When you click the button on the form, the `AddNumbers` method is first called with `Short` data type numbers, and [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] chooses the appropriate method from the base class.</span></span> <span data-ttu-id="b525c-153">2 番目の呼び出し`AddNumbers`からメソッドをオーバー ロードに転送`MathClass`します。</span><span class="sxs-lookup"><span data-stu-id="b525c-153">The second call to `AddNumbers` is directed to the overload method from `MathClass`.</span></span> <span data-ttu-id="b525c-154">3 番目の呼び出しを呼び出して、`SubtractNumbers`メソッドで、クラスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="b525c-154">The third call calls the `SubtractNumbers` method, which extends the class.</span></span> <span data-ttu-id="b525c-155">基本クラスのプロパティを設定すると、され、値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b525c-155">The property in the base class is set, and the value is displayed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b525c-156">次の手順</span><span class="sxs-lookup"><span data-stu-id="b525c-156">Next Steps</span></span>  
 <span data-ttu-id="b525c-157">気付いたかもしれませんが、オーバー ロードされた`AddNumbers`して、データ型、COM オブジェクトの基本クラスから継承されたメソッドと同じ関数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b525c-157">You may have noticed that the overloaded `AddNumbers` function appears to have the same data type as the method inherited from the base class of the COM object.</span></span> <span data-ttu-id="b525c-158">これは、引数および基本クラスのメソッドのパラメーターが Visual Basic 6.0 での 16 ビット整数値として定義されている型の 16 ビット整数として公開されるため`Short`Visual Basic のそれ以降のバージョン。</span><span class="sxs-lookup"><span data-stu-id="b525c-158">This is because the arguments and parameters of the base class method are defined as 16-bit integers in Visual Basic 6.0, but they are exposed as 16-bit integers of type `Short` in later versions of Visual Basic.</span></span> <span data-ttu-id="b525c-159">新しい関数は、32 ビットの整数入力し、基本クラスの関数をオーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="b525c-159">The new function accepts 32-bit integers, and overloads the base class function.</span></span>  
  
 <span data-ttu-id="b525c-160">COM オブジェクトを使用する場合は、パラメーターのサイズとデータ型を確認することを確認します。</span><span class="sxs-lookup"><span data-stu-id="b525c-160">When working with COM objects, make sure that you verify the size and data types of parameters.</span></span> <span data-ttu-id="b525c-161">たとえば、Visual Basic 6.0 コレクション オブジェクトを引数として受け取り、COM オブジェクトを使用しているときに、それ以降のバージョンの Visual Basic からコレクションを提供できません。</span><span class="sxs-lookup"><span data-stu-id="b525c-161">For example, when you are using a COM object that accepts a Visual Basic 6.0 collection object as an argument, you cannot provide a collection from a later version of Visual Basic.</span></span>  
  
 <span data-ttu-id="b525c-162">プロパティとメソッドが COM クラスから継承されたオーバーライドできます、つまり、ローカルのプロパティまたはプロパティを置換するメソッドまたは COM の基本クラスから継承されたメソッドを宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="b525c-162">Properties and methods inherited from COM classes can be overridden, meaning that you can declare a local property or method that replaces a property or method inherited from a base COM class.</span></span> <span data-ttu-id="b525c-163">COM の継承されたプロパティをオーバーライドするためのルールは、その他のプロパティと、次の例外のメソッドをオーバーライドするための規則に似ています。</span><span class="sxs-lookup"><span data-stu-id="b525c-163">The rules for overriding inherited COM properties are similar to the rules for overriding other properties and methods with the following exceptions:</span></span>  
  
-   <span data-ttu-id="b525c-164">任意のプロパティまたは COM クラスから継承されたメソッドをオーバーライドする場合は、その他のすべての継承されたプロパティとメソッドをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b525c-164">If you override any property or method inherited from a COM class, you must override all the other inherited properties and methods.</span></span>  
  
-   <span data-ttu-id="b525c-165">使用するプロパティ`ByRef`パラメーターはオーバーライドできません。</span><span class="sxs-lookup"><span data-stu-id="b525c-165">Properties that use `ByRef` parameters cannot be overridden.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b525c-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="b525c-166">See Also</span></span>  
 <span data-ttu-id="b525c-167">[.NET Framework アプリケーションにおける COM 相互運用性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md) </span><span class="sxs-lookup"><span data-stu-id="b525c-167">[COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md) </span></span>  
<span data-ttu-id="b525c-168"> [Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b525c-168"> [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) </span></span>  
<span data-ttu-id="b525c-169"> [Short データ型](../../../visual-basic/language-reference/data-types/short-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="b525c-169"> [Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md)</span></span>
