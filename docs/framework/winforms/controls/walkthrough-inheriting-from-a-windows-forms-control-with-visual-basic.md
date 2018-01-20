---
title: "チュートリアル : Visual Basic による Windows フォーム コントロールからの継承"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: fb58d7c8-b702-4478-ad31-b00cae118882
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b165de0d18cede275dfe8405b0266c1a909ac570
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a><span data-ttu-id="2c0a8-102">チュートリアル : Visual Basic による Windows フォーム コントロールからの継承</span><span class="sxs-lookup"><span data-stu-id="2c0a8-102">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>
<span data-ttu-id="2c0a8-103">[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] では、*継承*によって強力なカスタム コントロールを作成できます。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-103">With [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="2c0a8-104">継承を使用すると、標準の Windows フォーム コントロールの固有の機能をすべて保持しながら、カスタム機能も組み込んだコントロールを作成できます。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="2c0a8-105">このチュートリアルでは、`ValueButton` という単純な継承されたコントロールを作成します。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="2c0a8-106">このボタンは、標準の Windows フォームの機能を継承<xref:System.Windows.Forms.Button>制御、およびと呼ばれるカスタム プロパティを公開`ButtonValue`です。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c0a8-107">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="2c0a8-108">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="2c0a8-109">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="2c0a8-110">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="2c0a8-110">Creating the Project</span></span>  
 <span data-ttu-id="2c0a8-111">新しいプロジェクトを作成するときは、ルート名前空間、アセンブリ名、プロジェクト名を設定し、既定のコンポーネントが適切な名前空間に含まれるようにするために、プロジェクトの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-111">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="2c0a8-112">ValueButtonLib コントロール ライブラリと ValueButton コントロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="2c0a8-112">To create the ValueButtonLib control library and the ValueButton control</span></span>  
  
1.  <span data-ttu-id="2c0a8-113">**[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** をクリックして **[新しいプロジェクト]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-113">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="2c0a8-114">[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] プロジェクトの一覧で **[Windows フォーム コントロール ライブラリ]** プロジェクト テンプレートを選択し、**[名前]** ボックスに「`ValueButtonLib`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-114">Select the **Windows Forms Control Library** project template from the list of [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] projects, and type `ValueButtonLib` in the **Name** box.</span></span>  
  
     <span data-ttu-id="2c0a8-115">プロジェクト名 `ValueButtonLib` は、既定でルート名前空間にも割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-115">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="2c0a8-116">ルート名前空間は、アセンブリ内のコンポーネント名の修飾に使用されます。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-116">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="2c0a8-117">たとえば、`ValueButton` という名前のコンポーネントが 2 つのアセンブリに含まれている場合、`ValueButtonLib.ValueButton` を使用して目的の `ValueButton` コンポーネントを指定できます。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-117">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="2c0a8-118">詳細については、「[Visual Basic における名前空間](~/docs/visual-basic/programming-guide/program-structure/namespaces.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-118">For more information, see [Namespaces in Visual Basic](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
3.  <span data-ttu-id="2c0a8-119">**ソリューション エクスプローラー**で、**[UserControl1.vb]** を右クリックし、ショートカット メニューの **[名前の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-119">In **Solution Explorer**, right-click **UserControl1.vb**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="2c0a8-120">ファイル名を `ValueButton.vb` に変更します。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-120">Change the file name to `ValueButton.vb`.</span></span> <span data-ttu-id="2c0a8-121">コード要素 "UserControl1" へのすべての参照の名前を変更するかどうかをたずねられたら、**[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-121">Click the **Yes** button when you are asked if you want to rename all references to the code element 'UserControl1'.</span></span>  
  
4.  <span data-ttu-id="2c0a8-122">**ソリューション エクスプローラー**で、**[すべてのファイルを表示]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-122">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
5.  <span data-ttu-id="2c0a8-123">**[ValueButton.vb]** ノードを開いて、デザイナーによって生成されたコード ファイル (**ValueButton.Designer.vb**) を表示します。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-123">Open the **ValueButton.vb** node to display the designer-generated code file, **ValueButton.Designer.vb**.</span></span> <span data-ttu-id="2c0a8-124">このファイルを**コード エディター**で開きます。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-124">Open this file in the **Code Editor**.</span></span>  
  
6.  <span data-ttu-id="2c0a8-125">検索、`Class`ステートメントでは、 `Partial Public Class ValueButton`、このコントロールから継承する型を変更および<xref:System.Windows.Forms.UserControl>に<xref:System.Windows.Forms.Button>です。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-125">Locate the `Class` statement, `Partial Public Class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="2c0a8-126">これにより、継承されたコントロールのすべての機能を継承する、<xref:System.Windows.Forms.Button>コントロール。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-126">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>  
  
7.  <span data-ttu-id="2c0a8-127">検索、`InitializeComponent`メソッドおよび削除を代入する行、<xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-127">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="2c0a8-128">このプロパティに存在しません、<xref:System.Windows.Forms.Button>コントロール。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-128">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>  
  
8.  <span data-ttu-id="2c0a8-129">**[ファイル]** メニューの **[すべて保存]** をクリックして、プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-129">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
     <span data-ttu-id="2c0a8-130">ビジュアル デザイナーは使用できなくなっていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-130">Note that a visual designer is no longer available.</span></span> <span data-ttu-id="2c0a8-131"><xref:System.Windows.Forms.Button>コントロールは独自の描画、デザイナーでその外観を変更することができません。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-131">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="2c0a8-132">ビジュアル表現は同じでなければから継承するクラスと (つまり、 <xref:System.Windows.Forms.Button>) コードで変更しない限り、します。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-132">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c0a8-133">UI 要素のないコンポーネントをデザイン サーフェイスに追加することは可能です。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-133">You can still add components, which have no UI elements, to the design surface.</span></span>  
  
## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="2c0a8-134">継承されたコントロールへのプロパティの追加</span><span class="sxs-lookup"><span data-stu-id="2c0a8-134">Adding a Property to Your Inherited Control</span></span>  
 <span data-ttu-id="2c0a8-135">継承された Windows フォーム コントロールの考えられる用途の 1 つとして、外観と動作 (ルック アンド フィール) は標準の Windows フォーム コントロールと同じでありながら、カスタム プロパティを公開するコントロールの作成があります。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-135">One possible use of inherited Windows Forms controls is the creation of controls that are identical in appearance and behavior (look and feel) to standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="2c0a8-136">このセクションでは、`ButtonValue` というプロパティをコントロールに追加します。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-136">In this section, you will add a property called `ButtonValue` to your control.</span></span>  
  
#### <a name="to-add-the-value-property"></a><span data-ttu-id="2c0a8-137">Value プロパティを追加するには</span><span class="sxs-lookup"><span data-stu-id="2c0a8-137">To add the Value property</span></span>  
  
1.  <span data-ttu-id="2c0a8-138">**ソリューション エクスプローラー**で、**[ValueButton.vb]** を右クリックし、ショートカット メニューの **[コードの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-138">In **Solution Explorer**, right-click **ValueButton.vb**, and then click **View Code** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="2c0a8-139">`Public Class ValueButton` ステートメントを探します。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-139">Locate the `Public Class ValueButton` statement.</span></span> <span data-ttu-id="2c0a8-140">このステートメントの直後に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-140">Immediately beneath this statement, type the following code:</span></span>  
  
    ```vb  
    ' Creates the private variable that will store the value of your   
    ' property.  
    Private varValue as integer  
    ' Declares the property.  
    Property ButtonValue() as Integer  
    ' Sets the method for retrieving the value of your property.  
       Get  
          Return varValue  
       End Get  
    ' Sets the method for setting the value of your property.  
       Set(ByVal Value as Integer)  
          varValue = Value  
       End Set  
    End Property  
    ```  
  
     <span data-ttu-id="2c0a8-141">このコードでは、`ButtonValue` プロパティを格納し、取得するメソッドを設定しています。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-141">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="2c0a8-142">`Get` ステートメントは、返された値を `varValue` プライベート変数に格納されている値に設定します。`Set` ステートメントは、`Value` キーワードを使用してプライベート変数の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-142">The `Get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `Set` statement sets the value of the private variable by use of the `Value` keyword.</span></span>  
  
3.  <span data-ttu-id="2c0a8-143">**[ファイル]** メニューの **[すべて保存]** をクリックして、プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-143">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
## <a name="testing-your-control"></a><span data-ttu-id="2c0a8-144">コントロールのテスト</span><span class="sxs-lookup"><span data-stu-id="2c0a8-144">Testing Your Control</span></span>  
 <span data-ttu-id="2c0a8-145">コントロールはスタンドアロン プロジェクトではないため、コンテナー内でホストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-145">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="2c0a8-146">コントロールをテストするには、コントロールを実行するテスト プロジェクトを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-146">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="2c0a8-147">また、コントロールをビルド (コンパイル) して、テスト プロジェクトからアクセスできるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-147">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="2c0a8-148">このセクションでは、コントロールをビルドし、Windows フォームでテストします。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-148">In this section, you will build your control and test it in a Windows Form.</span></span>  
  
#### <a name="to-build-your-control"></a><span data-ttu-id="2c0a8-149">コントロールをビルドするには</span><span class="sxs-lookup"><span data-stu-id="2c0a8-149">To build your control</span></span>  
  
1.  <span data-ttu-id="2c0a8-150">**[ビルド]** メニューの **[ソリューションのビルド]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-150">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="2c0a8-151">コンパイル エラーも警告も発生せずに、ビルドが正常に完了します。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-151">The build should be successful with no compiler errors or warnings.</span></span>  
  
#### <a name="to-create-a-test-project"></a><span data-ttu-id="2c0a8-152">テスト プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="2c0a8-152">To create a test project</span></span>  
  
1.  <span data-ttu-id="2c0a8-153">**[ファイル]** メニューの **[追加]** をポイントし、**[新しいプロジェクト]** をクリックして **[新しいプロジェクトの追加]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-153">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="2c0a8-154">[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] プロジェクト ノードを選択し、**[Windows フォーム アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-154">Select the [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] projects node, and click **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="2c0a8-155">**[名前]** ボックスに「`Test`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-155">In the **Name** box, type `Test`.</span></span>  
  
4.  <span data-ttu-id="2c0a8-156">**ソリューション エクスプローラー**で、**[すべてのファイルを表示]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-156">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
5.  <span data-ttu-id="2c0a8-157">**ソリューション エクスプローラー**で、テスト プロジェクトの **[参照設定]** ノードを右クリックし、ショートカット メニューの **[参照の追加]** をクリックして **[参照の追加]** ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-157">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>  
  
6.  <span data-ttu-id="2c0a8-158">**[プロジェクト]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-158">Click the **Projects** tab.</span></span>  
  
7.  <span data-ttu-id="2c0a8-159">**[プロジェクト]** というラベルのタブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-159">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="2c0a8-160">**[プロジェクト名]** に `ValueButtonLib` プロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-160">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="2c0a8-161">プロジェクトをダブルクリックして、テスト プロジェクトへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-161">Double-click the project to add the reference to the test project.</span></span>  
  
8.  <span data-ttu-id="2c0a8-162">**ソリューション エクスプローラー**で、**[Test]** を右クリックし、**[ビルド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-162">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>  
  
#### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="2c0a8-163">コントロールをフォームに追加するには</span><span class="sxs-lookup"><span data-stu-id="2c0a8-163">To add your control to the form</span></span>  
  
1.  <span data-ttu-id="2c0a8-164">**ソリューション エクスプローラー**で、**[Form1.vb]** を右クリックし、ショートカット メニューの **[デザイナーの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-164">In **Solution Explorer**, right-click **Form1.vb** and choose **View Designer** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="2c0a8-165">**ツールボックス**の **[ValueButtonLib コンポーネント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-165">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="2c0a8-166">**[ValueButton]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-166">Double-click **ValueButton**.</span></span>  
  
     <span data-ttu-id="2c0a8-167">**ValueButton** がフォームに表示されます。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-167">A **ValueButton** appears on the form.</span></span>  
  
3.  <span data-ttu-id="2c0a8-168">**[ValueButton]** を右クリックし、ショートカット メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-168">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="2c0a8-169">**[プロパティ]** ウィンドウで、このコントロールのプロパティを調べます。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-169">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="2c0a8-170">プロパティは、追加のプロパティである `ButtonValue` がある点を除き、標準ボタンで公開されるプロパティと同じです。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-170">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>  
  
5.  <span data-ttu-id="2c0a8-171">`ButtonValue` プロパティを `5` に設定します。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-171">Set the `ButtonValue` property to `5`.</span></span>  
  
6.  <span data-ttu-id="2c0a8-172">**すべての Windows フォーム**のタブ、**ツールボックス**をダブルクリックして**ラベル**を追加する、<xref:System.Windows.Forms.Label>をフォームにコントロールです。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-172">On the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>  
  
7.  <span data-ttu-id="2c0a8-173">ラベルをフォームの中央に配置し直します。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-173">Relocate the label to the center of the form.</span></span>  
  
8.  <span data-ttu-id="2c0a8-174">`ValueButton1` をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-174">Double-click `ValueButton1`.</span></span>  
  
     <span data-ttu-id="2c0a8-175">**コード エディター**が開き、`ValueButton1_Click` イベントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-175">The **Code Editor** opens to the `ValueButton1_Click` event.</span></span>  
  
9. <span data-ttu-id="2c0a8-176">次のコード行を入力します。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-176">Type the following line of code.</span></span>  
  
    ```vb  
    Label1.Text = CStr(ValueButton1.ButtonValue)  
    ```  
  
10. <span data-ttu-id="2c0a8-177">**ソリューション エクスプローラー**で、**[Test]** を右クリックし、ショートカット メニューの **[スタートアップ プロジェクトに設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-177">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>  
  
11. <span data-ttu-id="2c0a8-178">**[デバッグ]** メニューの **[デバッグの開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-178">From the **Debug** menu, select **Start Debugging**.</span></span>  
  
     <span data-ttu-id="2c0a8-179">`Form1` が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-179">`Form1` appears.</span></span>  
  
12. <span data-ttu-id="2c0a8-180">[`Valuebutton1`] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-180">Click `Valuebutton1`.</span></span>  
  
     <span data-ttu-id="2c0a8-181">`Label1` に数字の "5" が表示されます。これは、継承されたコントロールの `ButtonValue` プロパティが、`ValueButton1_Click` メソッドによって `Label1` に渡されたことを示しています。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-181">The numeral '5' is displayed in `Label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `Label1` through the `ValueButton1_Click` method.</span></span> <span data-ttu-id="2c0a8-182">このようにして、`ValueButton` コントロールは標準の Windows フォーム ボタンの機能をすべて継承しながら、追加のカスタム プロパティを公開します。</span><span class="sxs-lookup"><span data-stu-id="2c0a8-182">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c0a8-183">参照</span><span class="sxs-lookup"><span data-stu-id="2c0a8-183">See Also</span></span>  
 [<span data-ttu-id="2c0a8-184">チュートリアル: Visual Basic による複合コントロールの作成</span><span class="sxs-lookup"><span data-stu-id="2c0a8-184">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 <span data-ttu-id="2c0a8-185">[方法: [ツールボックス アイテムの選択] ダイアログ ボックスにコントロールを表示する](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="2c0a8-185">[How to: Display a Control in the Choose Toolbox Items Dialog Box](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span></span>  
 [<span data-ttu-id="2c0a8-186">.NET Framework を使用したカスタム Windows フォーム コントロールの開発</span><span class="sxs-lookup"><span data-stu-id="2c0a8-186">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="2c0a8-187">継承の基礎 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c0a8-187">Inheritance basics (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="2c0a8-188">コンポーネント作成のチュートリアル</span><span class="sxs-lookup"><span data-stu-id="2c0a8-188">Component Authoring Walkthroughs</span></span>](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)
