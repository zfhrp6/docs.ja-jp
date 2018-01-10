---
title: "チュートリアル : ビジュアル継承のデモンストレーション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- form inheritance [Windows Forms], walkthroughs
- visual inheritance
- inheritance [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], visual inheritance
- Windows Forms, inheritance
ms.assetid: 01966086-3142-450e-8210-3fd4cb33f591
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54f521050025f2f9e55085ee2656a5874b62226d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a><span data-ttu-id="f646a-102">チュートリアル : ビジュアル継承のデモンストレーション</span><span class="sxs-lookup"><span data-stu-id="f646a-102">Walkthrough: Demonstrating Visual Inheritance</span></span>
<span data-ttu-id="f646a-103">ビジュアル継承により、基本フォームのコントロールを表示して、新しいコントロールを追加できます。</span><span class="sxs-lookup"><span data-stu-id="f646a-103">Visual inheritance enables you to see the controls on the base form and to add new controls.</span></span> <span data-ttu-id="f646a-104">このチュートリアルでは、基本フォームを作成してクラス ライブラリにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="f646a-104">In this walkthrough you will create a base form and compile it into a class library.</span></span> <span data-ttu-id="f646a-105">このクラス ライブラリを別のプロジェクトにインポートして、基本フォームから継承する新しいフォームを作成します。</span><span class="sxs-lookup"><span data-stu-id="f646a-105">You will import this class library into another project and create a new form that inherits from the base form.</span></span> <span data-ttu-id="f646a-106">このチュートリアルでは、次の作業を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f646a-106">During this walkthrough, you will learn how to:</span></span>  
  
-   <span data-ttu-id="f646a-107">基本フォームを含むクラス ライブラリ プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f646a-107">Create a class library project containing a base form.</span></span>  
  
-   <span data-ttu-id="f646a-108">基本フォームの派生クラスが変更できるプロパティを持つボタンを追加します。</span><span class="sxs-lookup"><span data-stu-id="f646a-108">Add a button with properties that derived classes of the base form can modify.</span></span>  
  
-   <span data-ttu-id="f646a-109">基本フォームの継承元により変更できないボタンを追加します。</span><span class="sxs-lookup"><span data-stu-id="f646a-109">Add a button that cannot be modified by inheritors of the base form.</span></span>  
  
-   <span data-ttu-id="f646a-110">`BaseForm` から継承したフォームを含むプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f646a-110">Create a project containing a form that inherits from `BaseForm`.</span></span>  
  
 <span data-ttu-id="f646a-111">最終的には、このチュートリアルでは、継承されたフォーム上のプライベート コントロールとプロテクト コントロールの違いを示します。</span><span class="sxs-lookup"><span data-stu-id="f646a-111">Ultimately, this walkthrough will demonstrate the difference between private and protected controls on an inherited form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f646a-112">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f646a-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f646a-113">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f646a-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f646a-114">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f646a-114">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="f646a-115">すべてのコントロールが基本フォームのビジュアル継承をサポートするわけではありません。</span><span class="sxs-lookup"><span data-stu-id="f646a-115">Not all controls support visual inheritance from a base form.</span></span> <span data-ttu-id="f646a-116">次のコントロールでは、このチュートリアルで説明するシナリオはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="f646a-116">The following controls do not support the scenario described in this walkthrough:</span></span>  
>   
>  <xref:System.Windows.Forms.WebBrowser>  
>   
>  <xref:System.Windows.Forms.ToolStrip>  
>   
>  <xref:System.Windows.Forms.ToolStripPanel>  
>   
>  <xref:System.Windows.Forms.TableLayoutPanel>  
>   
>  <xref:System.Windows.Forms.FlowLayoutPanel>  
>   
>  <xref:System.Windows.Forms.DataGridView>  
>   
>  <span data-ttu-id="f646a-117">継承されたフォームのこれらのコントロールは、使用する修飾子 (`private`、`protected`、または `public`) に関係なく、常に読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="f646a-117">These controls in the inherited form are always read-only regardless of the modifiers you use (`private`, `protected`, or `public`).</span></span>  
  
## <a name="scenario-steps"></a><span data-ttu-id="f646a-118">シナリオの手順</span><span class="sxs-lookup"><span data-stu-id="f646a-118">Scenario Steps</span></span>  
 <span data-ttu-id="f646a-119">最初の手順では、基本フォームを作成します。</span><span class="sxs-lookup"><span data-stu-id="f646a-119">The first step is to create the base form.</span></span>  
  
#### <a name="to-create-a-class-library-project-containing-a-base-form"></a><span data-ttu-id="f646a-120">基本フォームを含むクラス ライブラリ プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="f646a-120">To create a class library project containing a base form</span></span>  
  
1.  <span data-ttu-id="f646a-121">**ファイル** メニューの 選択**新規**、し**プロジェクト**を開くには、**新しいプロジェクト** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="f646a-121">From the **File** menu, choose **New**, and then **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="f646a-122">という名前の Windows フォーム アプリケーションを作成する`BaseFormLibrary`です。</span><span class="sxs-lookup"><span data-stu-id="f646a-122">Create a Windows Forms application named `BaseFormLibrary`.</span></span>  
  
3.  <span data-ttu-id="f646a-123">標準の Windows フォーム アプリケーションではなく、クラス ライブラリを作成する**ソリューション エクスプ ローラー**を右クリックし、 **BaseFormLibrary**プロジェクト ノードを選択し、 **のプロパティ**.</span><span class="sxs-lookup"><span data-stu-id="f646a-123">To create a class library instead of a standard Windows Forms application, in **Solution Explorer**, right-click the **BaseFormLibrary** project node and then select **Properties**.</span></span>  
  
4.  <span data-ttu-id="f646a-124">プロジェクトのプロパティで、変更、**出力の種類**から**Windows アプリケーション**に**クラス ライブラリ**です。</span><span class="sxs-lookup"><span data-stu-id="f646a-124">In the properties for the project, change the **Output type** from **Windows Application** to **Class Library**.</span></span>  
  
5.  <span data-ttu-id="f646a-125">**ファイル**] メニューの [選択**すべて保存**を既定の場所に、プロジェクト ファイルとファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="f646a-125">From the **File** menu, choose **Save All** to save the project and files to the default location.</span></span>  
  
 <span data-ttu-id="f646a-126">次の 2 つの手順では、基本フォームにボタンを追加します。</span><span class="sxs-lookup"><span data-stu-id="f646a-126">The next two procedures add buttons to the base form.</span></span> <span data-ttu-id="f646a-127">ビジュアル継承を示すには、`Modifiers` プロパティを設定して、ボタンに異なるアクセス レベルを付与します。</span><span class="sxs-lookup"><span data-stu-id="f646a-127">To demonstrate visual inheritance, you will give the buttons different access levels by setting their `Modifiers` properties.</span></span>  
  
#### <a name="to-add-a-button-that-inheritors-of-the-base-form-can-modify"></a><span data-ttu-id="f646a-128">基本フォームの継承クラスから変更が可能なボタンを追加するには</span><span class="sxs-lookup"><span data-stu-id="f646a-128">To add a button that inheritors of the base form can modify</span></span>  
  
1.  <span data-ttu-id="f646a-129">開いている**Form1**デザイナーでします。</span><span class="sxs-lookup"><span data-stu-id="f646a-129">Open **Form1** in the designer.</span></span>  
  
2.  <span data-ttu-id="f646a-130">**すべての Windows フォーム**のタブ、**ツールボックス**をダブルクリックして**ボタン**をフォームにボタンを追加します。</span><span class="sxs-lookup"><span data-stu-id="f646a-130">On the **All Windows Forms** tab of the **Toolbox**, double-click **Button** to add a button to the form.</span></span> <span data-ttu-id="f646a-131">マウスを使用し、ボタンを配置してサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="f646a-131">Use the mouse to position and resize the button.</span></span>  
  
3.  <span data-ttu-id="f646a-132">[プロパティ] ウィンドウで、ボタンの次のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="f646a-132">In the Properties window, set the following properties of the button:</span></span>  
  
    -   <span data-ttu-id="f646a-133">設定、**テキスト**プロパティを**Say こんにちは**です。</span><span class="sxs-lookup"><span data-stu-id="f646a-133">Set the **Text** property to **Say Hello**.</span></span>  
  
    -   <span data-ttu-id="f646a-134">設定、 **(名)**プロパティを**btnProtected**です。</span><span class="sxs-lookup"><span data-stu-id="f646a-134">Set the **(Name)** property to **btnProtected**.</span></span>  
  
    -   <span data-ttu-id="f646a-135">設定、**修飾子**プロパティを**Protected**です。</span><span class="sxs-lookup"><span data-stu-id="f646a-135">Set the**Modifiers** property to **Protected**.</span></span> <span data-ttu-id="f646a-136">継承するフォームができるようになります**Form1**のプロパティを変更する**btnProtected**です。</span><span class="sxs-lookup"><span data-stu-id="f646a-136">This makes it possible for forms that inherit from **Form1** to modify the properties of **btnProtected**.</span></span>  
  
4.  <span data-ttu-id="f646a-137">ダブルクリックして、 **Say こんにちは**のイベント ハンドラーを追加するボタン、  **をクリックして**イベント。</span><span class="sxs-lookup"><span data-stu-id="f646a-137">Double-click the **Say Hello** button to add an event handler for the **Click** event.</span></span>  
  
5.  <span data-ttu-id="f646a-138">イベント ハンドラーに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="f646a-138">Add the following line of code to the event handler:</span></span>  
  
    ```vb  
    MessageBox.Show("Hello, World!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Hello, World!");  
    ```  
  
#### <a name="to-add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a><span data-ttu-id="f646a-139">基本フォームの継承元により変更できないボタンを追加するには</span><span class="sxs-lookup"><span data-stu-id="f646a-139">To add a button that cannot be modified by inheritors of the base form</span></span>  
  
1.  <span data-ttu-id="f646a-140">クリックしてデザイン ビューに切り替え、 **Form1.vb [デザイン]、Form1.cs [デザイン]、または Form1.jsl の [デザイン]**コード エディターの上または F7 キーを押してタブです。</span><span class="sxs-lookup"><span data-stu-id="f646a-140">Switch to design view by clicking the **Form1.vb [Design], Form1.cs [Design], or Form1.jsl [Design]** tab above the code editor, or by pressing F7.</span></span>  
  
2.  <span data-ttu-id="f646a-141">2 番目のボタンを追加し、そのプロパティを次のように設定します。</span><span class="sxs-lookup"><span data-stu-id="f646a-141">Add a second button and set its properties as follows:</span></span>  
  
    -   <span data-ttu-id="f646a-142">設定、**テキスト**プロパティを**Say Goodbye**です。</span><span class="sxs-lookup"><span data-stu-id="f646a-142">Set the **Text** property to **Say Goodbye**.</span></span>  
  
    -   <span data-ttu-id="f646a-143">設定、 **(名)**プロパティを**btnPrivate**です。</span><span class="sxs-lookup"><span data-stu-id="f646a-143">Set the **(Name)** property to **btnPrivate**.</span></span>  
  
    -   <span data-ttu-id="f646a-144">設定、**修飾子**プロパティを**プライベート**です。</span><span class="sxs-lookup"><span data-stu-id="f646a-144">Set the **Modifiers** property to **Private**.</span></span> <span data-ttu-id="f646a-145">継承するフォームが不可能になります。 **Form1**のプロパティを変更する**btnPrivate**です。</span><span class="sxs-lookup"><span data-stu-id="f646a-145">This makes it impossible for forms that inherit from **Form1** to modify the properties of **btnPrivate**.</span></span>  
  
3.  <span data-ttu-id="f646a-146">ダブルクリックして、 **Say Goodbye**のイベント ハンドラーを追加するボタン、  **をクリックして**イベント。</span><span class="sxs-lookup"><span data-stu-id="f646a-146">Double-click the **Say Goodbye** button to add an event handler for the **Click** event.</span></span> <span data-ttu-id="f646a-147">イベントの手順で、次のコード行を配置します。</span><span class="sxs-lookup"><span data-stu-id="f646a-147">Place the following line of code in the event procedure:</span></span>  
  
    ```vb  
    MessageBox.Show("Goodbye!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Goodbye!");  
    ```  
  
4.  <span data-ttu-id="f646a-148">**ビルド**] メニューの [選択**BaseForm ライブラリのビルド**クラス ライブラリをビルドします。</span><span class="sxs-lookup"><span data-stu-id="f646a-148">From the **Build** menu, choose **Build BaseForm Library** to build the class library.</span></span>  
  
     <span data-ttu-id="f646a-149">ライブラリがビルドされたら、作成したフォームから継承する新しいプロジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="f646a-149">Once the library is built, you can create a new project that inherits from the form you just created.</span></span>  
  
#### <a name="to-create-a-project-containing-a-form-that-inherits-from-the-base-form"></a><span data-ttu-id="f646a-150">基本フォームから継承したフォームを含むプロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="f646a-150">To create a project containing a form that inherits from the base form</span></span>  
  
1.  <span data-ttu-id="f646a-151">**ファイル** メニューの 選択**追加**し**新しいプロジェクト**を開くには、**新しいプロジェクトの追加** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="f646a-151">From the **File** menu, choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="f646a-152">という名前の Windows フォーム アプリケーションを作成する`InheritanceTest`です。</span><span class="sxs-lookup"><span data-stu-id="f646a-152">Create a Windows Forms application named `InheritanceTest`.</span></span>  
  
#### <a name="to-add-an-inherited-form"></a><span data-ttu-id="f646a-153">継承されたフォームを追加するには</span><span class="sxs-lookup"><span data-stu-id="f646a-153">To add an inherited form</span></span>  
  
1.  <span data-ttu-id="f646a-154">**ソリューション エクスプ ローラー**を右クリックし、 **InheritanceTest**プロジェクトで、**追加**、し、**新しい項目の**します。</span><span class="sxs-lookup"><span data-stu-id="f646a-154">In **Solution Explorer**, right-click the **InheritanceTest** project, select **Add**, and then select**New Item**.</span></span>  
  
2.  <span data-ttu-id="f646a-155">**新しい項目の追加**ダイアログ ボックスで、 **Windows フォーム**カテゴリ (カテゴリの一覧の場合) クリックし、**継承されたフォーム**テンプレート。</span><span class="sxs-lookup"><span data-stu-id="f646a-155">In the **Add New Item** dialog box, select the **Windows Forms** category (if you have a list of categories) and then select the **Inherited Form** template.</span></span>  
  
3.  <span data-ttu-id="f646a-156">既定の名前のままにして`Form2` をクリックし、**追加**です。</span><span class="sxs-lookup"><span data-stu-id="f646a-156">Leave the default name of `Form2` and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="f646a-157">**継承ピッカー**ダイアログ ボックスで、 **Form1**から、 **BaseFormLibrary**フォームから継承し、をクリックするとプロジェクト**OK**.</span><span class="sxs-lookup"><span data-stu-id="f646a-157">In the **Inheritance Picker** dialog box, select **Form1** from the **BaseFormLibrary** project as the form to inherit from and click **OK**.</span></span>  
  
     <span data-ttu-id="f646a-158">これでフォームを作成、 **InheritanceTest**プロジェクトのフォームから派生した**BaseFormLibrary**です。</span><span class="sxs-lookup"><span data-stu-id="f646a-158">This creates a form in the **InheritanceTest** project that derives from the form in **BaseFormLibrary**.</span></span>  
  
5.  <span data-ttu-id="f646a-159">継承されたフォームを開きます (**Form2**) がまだ開いていない場合をダブルクリックしてデザイナーでします。</span><span class="sxs-lookup"><span data-stu-id="f646a-159">Open the inherited form (**Form2**) in the designer by double-clicking it, if it is not already open.</span></span>  
  
     <span data-ttu-id="f646a-160">デザイナーで、継承されたボタンにシンボルがある (![VisualBasicInheritanceSymbol スクリーン ショット](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.gif "vbInheritanceGlyph")) を示す継承され、上の隅にします。</span><span class="sxs-lookup"><span data-stu-id="f646a-160">In the designer, the inherited buttons have a symbol (![VisualBasicInheritanceSymbol screenshot](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.gif "vbInheritanceGlyph")) in their upper corner, indicating they are inherited.</span></span>  
  
6.  <span data-ttu-id="f646a-161">選択、 **Say こんにちは**ボタンをクリックし、サイズ変更ハンドルを観察します。</span><span class="sxs-lookup"><span data-stu-id="f646a-161">Select the **Say Hello** button and observe the resize handles.</span></span> <span data-ttu-id="f646a-162">このボタンは保護されているため、継承元が、移動、サイズ変更、キャプションの変更、およびその他の変更を実行できます。</span><span class="sxs-lookup"><span data-stu-id="f646a-162">Because this button is protected, the inheritors can move it, resize it, change its caption, and make other modifications.</span></span>  
  
7.  <span data-ttu-id="f646a-163">プライベート**Say Goodbye**  ボタン、およびサイズ変更ハンドルがないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f646a-163">Select the private **Say Goodbye** button, and notice that it does not have resize handles.</span></span> <span data-ttu-id="f646a-164">また、、**プロパティ**ウィンドウで、このボタンのプロパティは変更できないことを示すためにグレー表示にします。</span><span class="sxs-lookup"><span data-stu-id="f646a-164">Additionally, in the **Properties** window, the properties of this button are grayed to indicate they cannot be modified.</span></span>  
  
8.  <span data-ttu-id="f646a-165">[!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] を使用している場合:</span><span class="sxs-lookup"><span data-stu-id="f646a-165">If you are using [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]:</span></span>  
  
    1.  <span data-ttu-id="f646a-166">**ソリューション エクスプ ローラー**を右クリックして**Form1**で、 **InheritanceTest**プロジェクトし、**削除**です。</span><span class="sxs-lookup"><span data-stu-id="f646a-166">In **Solution Explorer**, right-click **Form1** in the **InheritanceTest** project and then choose **Delete**.</span></span> <span data-ttu-id="f646a-167">表示されるメッセージ ボックスで、をクリックして**OK**削除を確認します。</span><span class="sxs-lookup"><span data-stu-id="f646a-167">In the message box that appears, click **OK** to confirm the deletion.</span></span>  
  
    2.  <span data-ttu-id="f646a-168">Program.cs ファイルを開き、行 `Application.Run(new Form1());` を `Application.Run(new Form2());` に変更します。</span><span class="sxs-lookup"><span data-stu-id="f646a-168">Open the Program.cs file and change the line `Application.Run(new Form1());` to `Application.Run(new Form2());`.</span></span>  
  
9. <span data-ttu-id="f646a-169">**ソリューション エクスプ ローラー**を右クリックし、 **InheritanceTest**プロジェクトし、選択**スタートアップ プロジェクトとして設定**です。</span><span class="sxs-lookup"><span data-stu-id="f646a-169">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Set As Startup Project**.</span></span>  
  
10. <span data-ttu-id="f646a-170">**ソリューション エクスプ ローラー**を右クリックし、 **InheritanceTest**プロジェクトし、選択**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="f646a-170">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Properties**.</span></span>  
  
11. <span data-ttu-id="f646a-171">**InheritanceTest**プロパティ ページ、設定、**スタートアップ オブジェクト**継承されたフォーム (**Form2**)。</span><span class="sxs-lookup"><span data-stu-id="f646a-171">In the **InheritanceTest** property pages, set the **Startup object** to be the inherited form (**Form2**).</span></span>  
  
12. <span data-ttu-id="f646a-172">F5 を押してアプリケーションを実行し、継承されたフォームの動作を確認します。</span><span class="sxs-lookup"><span data-stu-id="f646a-172">Press F5 to run the application, and observe the behavior of the inherited form.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f646a-173">次の手順</span><span class="sxs-lookup"><span data-stu-id="f646a-173">Next Steps</span></span>  
 <span data-ttu-id="f646a-174">ユーザー コントロールの継承はほぼ同じ方法で機能します。</span><span class="sxs-lookup"><span data-stu-id="f646a-174">Inheritance for user controls works in much the same way.</span></span> <span data-ttu-id="f646a-175">新しいクラス ライブラリ プロジェクトを開き、ユーザー コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="f646a-175">Open a new class library project and add a user control.</span></span> <span data-ttu-id="f646a-176">内在コントロールを配置し、プロジェクトをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="f646a-176">Place constituent controls on it and compile the project.</span></span> <span data-ttu-id="f646a-177">別の新しいクラス ライブラリ プロジェクトを開き、コンパイル済みのクラス ライブラリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="f646a-177">Open another new class library project and add a reference to the compiled class library.</span></span> <span data-ttu-id="f646a-178">また、[継承されたコントロールを追加してみてください (を通じて、**新しい項目の追加**] ダイアログ ボックス) をプロジェクトを使用して、**継承ピッカー**です。</span><span class="sxs-lookup"><span data-stu-id="f646a-178">Also, try adding an inherited control (through the **Add New Items** dialog box) to the project and using the **Inheritance Picker**.</span></span> <span data-ttu-id="f646a-179">ユーザー コントロールを追加し、`Inherits` ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] の`:`) ステートメントを変更します。</span><span class="sxs-lookup"><span data-stu-id="f646a-179">Add a user control, and change the `Inherits` (`:` in [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) statement.</span></span> <span data-ttu-id="f646a-180">詳細については、次を参照してください。[する方法: Windows フォームの継承](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="f646a-180">For more information, see [How to: Inherit Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f646a-181">参照</span><span class="sxs-lookup"><span data-stu-id="f646a-181">See Also</span></span>  
 [<span data-ttu-id="f646a-182">方法: Windows フォームを継承する</span><span class="sxs-lookup"><span data-stu-id="f646a-182">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 [<span data-ttu-id="f646a-183">Windows フォームのビジュアルの継承</span><span class="sxs-lookup"><span data-stu-id="f646a-183">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [<span data-ttu-id="f646a-184">Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="f646a-184">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
