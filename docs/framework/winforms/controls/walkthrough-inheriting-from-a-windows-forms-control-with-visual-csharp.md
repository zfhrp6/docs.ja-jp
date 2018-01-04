---
title: "チュートリアル : Visual C# による Windows フォーム コントロールからの継承"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c28e41ad7c9e07dae150035e205e79b3d8cac84
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-c"></a><span data-ttu-id="98084-102">チュートリアル : Visual C# による Windows フォーム コントロールからの継承</span><span class="sxs-lookup"><span data-stu-id="98084-102">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span> #
<span data-ttu-id="98084-103">[!INCLUDE[csprcslong](../../../../includes/csprcslong-md.md)] では、*継承*によって強力なカスタム コントロールを作成できます。</span><span class="sxs-lookup"><span data-stu-id="98084-103">With [!INCLUDE[csprcslong](../../../../includes/csprcslong-md.md)], you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="98084-104">継承を使用すると、標準の Windows フォーム コントロールの固有の機能をすべて保持しながら、カスタム機能も組み込んだコントロールを作成できます。</span><span class="sxs-lookup"><span data-stu-id="98084-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="98084-105">このチュートリアルでは、`ValueButton` という単純な継承されたコントロールを作成します。</span><span class="sxs-lookup"><span data-stu-id="98084-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="98084-106">このボタンは、標準の Windows フォームの機能を継承<xref:System.Windows.Forms.Button>制御、およびと呼ばれるカスタム プロパティを公開`ButtonValue`です。</span><span class="sxs-lookup"><span data-stu-id="98084-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98084-107">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="98084-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="98084-108">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="98084-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="98084-109">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98084-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="98084-110">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="98084-110">Creating the Project</span></span>  
 <span data-ttu-id="98084-111">新しいプロジェクトを作成するときは、ルート名前空間、アセンブリ名、プロジェクト名を設定し、既定のコンポーネントが適切な名前空間に含まれるようにするために、プロジェクトの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="98084-111">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="98084-112">ValueButtonLib コントロール ライブラリと ValueButton コントロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="98084-112">To create the ValueButtonLib control library and the ValueButton control</span></span>  
  
1.  <span data-ttu-id="98084-113">**[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** をクリックして **[新しいプロジェクト]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="98084-113">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="98084-114">[!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] プロジェクトの一覧で **[Windows フォーム コントロール ライブラリ]** プロジェクト テンプレートを選択し、**[名前]** ボックスに「`ValueButtonLib`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="98084-114">Select the **Windows Forms Control Library** project template from the list of [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] Projects, and type `ValueButtonLib` in the **Name** box.</span></span>  
  
     <span data-ttu-id="98084-115">プロジェクト名 `ValueButtonLib` は、既定でルート名前空間にも割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="98084-115">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="98084-116">ルート名前空間は、アセンブリ内のコンポーネント名の修飾に使用されます。</span><span class="sxs-lookup"><span data-stu-id="98084-116">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="98084-117">たとえば、`ValueButton` という名前のコンポーネントが 2 つのアセンブリに含まれている場合、`ValueButtonLib.ValueButton` を使用して目的の `ValueButton` コンポーネントを指定できます。</span><span class="sxs-lookup"><span data-stu-id="98084-117">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="98084-118">詳細については、「[名前空間](../../../csharp/programming-guide/namespaces/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98084-118">For more information, see [Namespaces](../../../csharp/programming-guide/namespaces/index.md).</span></span>  
  
3.  <span data-ttu-id="98084-119">**ソリューション エクスプローラー**で、**[UserControl1.cs]** を右クリックし、ショートカット メニューの **[名前の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="98084-119">In **Solution Explorer**, right-click **UserControl1.cs**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="98084-120">ファイル名を `ValueButton.cs` に変更します。</span><span class="sxs-lookup"><span data-stu-id="98084-120">Change the file name to `ValueButton.cs`.</span></span> <span data-ttu-id="98084-121">コード要素 "`UserControl1`" へのすべての参照の名前を変更するかどうかをたずねられたら、**[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="98084-121">Click the **Yes** button when you are asked if you want to rename all references to the code element '`UserControl1`'.</span></span>  
  
4.  <span data-ttu-id="98084-122">**ソリューション エクスプローラー**で、**[ValueButton.cs]** を右クリックし、**[コードの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="98084-122">In **Solution Explorer**, right-click **ValueButton.cs** and select **View Code**.</span></span>  
  
5.  <span data-ttu-id="98084-123">検索、`class`明細行`public partial class ValueButton`、このコントロールから継承する型を変更および<xref:System.Windows.Forms.UserControl>に<xref:System.Windows.Forms.Button>です。</span><span class="sxs-lookup"><span data-stu-id="98084-123">Locate the `class` statement line, `public partial class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="98084-124">これにより、継承されたコントロールのすべての機能を継承する、<xref:System.Windows.Forms.Button>コントロール。</span><span class="sxs-lookup"><span data-stu-id="98084-124">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>  
  
6.  <span data-ttu-id="98084-125">**ソリューション エクスプローラー**で、**[ValueButton.cs]** ノードを開いて、デザイナーによって生成されたコード ファイル (**ValueButton.Designer.cs**) を表示します。</span><span class="sxs-lookup"><span data-stu-id="98084-125">In **Solution Explorer**, open the **ValueButton.cs** node to display the designer-generated code file, **ValueButton.Designer.cs**.</span></span> <span data-ttu-id="98084-126">このファイルを**コード エディター**で開きます。</span><span class="sxs-lookup"><span data-stu-id="98084-126">Open this file in the **Code Editor**.</span></span>  
  
7.  <span data-ttu-id="98084-127">検索、`InitializeComponent`メソッドおよび削除を代入する行、<xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="98084-127">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="98084-128">このプロパティに存在しません、<xref:System.Windows.Forms.Button>コントロール。</span><span class="sxs-lookup"><span data-stu-id="98084-128">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>  
  
8.  <span data-ttu-id="98084-129">**[ファイル]** メニューの **[すべて保存]** をクリックして、プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="98084-129">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="98084-130">ビジュアル デザイナーは使用できなくなっています。</span><span class="sxs-lookup"><span data-stu-id="98084-130">A visual designer is no longer available.</span></span> <span data-ttu-id="98084-131"><xref:System.Windows.Forms.Button>コントロールは独自の描画、デザイナーでその外観を変更することができません。</span><span class="sxs-lookup"><span data-stu-id="98084-131">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="98084-132">ビジュアル表現は同じでなければから継承するクラスと (つまり、 <xref:System.Windows.Forms.Button>) コードで変更しない限り、します。</span><span class="sxs-lookup"><span data-stu-id="98084-132">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span> <span data-ttu-id="98084-133">UI 要素のないコンポーネントをデザイン サーフェイスに追加することは可能です。</span><span class="sxs-lookup"><span data-stu-id="98084-133">You can still add components, which have no UI elements, to the design surface.</span></span>  
  
## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="98084-134">継承されたコントロールへのプロパティの追加</span><span class="sxs-lookup"><span data-stu-id="98084-134">Adding a Property to Your Inherited Control</span></span>  
 <span data-ttu-id="98084-135">継承された Windows フォーム コントロールの考えられる用途の 1 つとして、外観は標準の Windows フォーム コントロールと同じでありながら、カスタム プロパティを公開するコントロールの作成があります。</span><span class="sxs-lookup"><span data-stu-id="98084-135">One possible use of inherited Windows Forms controls is the creation of controls that are identical in look and feel of standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="98084-136">このセクションでは、`ButtonValue` というプロパティをコントロールに追加します。</span><span class="sxs-lookup"><span data-stu-id="98084-136">In this section, you will add a property called `ButtonValue` to your control.</span></span>  
  
#### <a name="to-add-the-value-property"></a><span data-ttu-id="98084-137">Value プロパティを追加するには</span><span class="sxs-lookup"><span data-stu-id="98084-137">To add the Value property</span></span>  
  
1.  <span data-ttu-id="98084-138">**ソリューション エクスプローラー**で、**[ValueButton.cs]** を右クリックし、ショートカット メニューの **[コードの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="98084-138">In **Solution Explorer**, right-click **ValueButton.cs**, and then click **View Code** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="98084-139">`class` ステートメントを見つけます。</span><span class="sxs-lookup"><span data-stu-id="98084-139">Locate the `class` statement.</span></span> <span data-ttu-id="98084-140">`{` の直後に次のコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="98084-140">Immediately after the `{`, type the following code:</span></span>  
  
    ```csharp  
    // Creates the private variable that will store the value of your   
    // property.  
    private int varValue;  
    // Declares the property.  
    public int ButtonValue  
    {  
       // Sets the method for retrieving the value of your property.  
       get  
       {  
          return varValue;  
       }  
       // Sets the method for setting the value of your property.  
       set  
       {  
          varValue = value;  
       }  
    }  
    ```  
  
     <span data-ttu-id="98084-141">このコードでは、`ButtonValue` プロパティを格納し、取得するメソッドを設定しています。</span><span class="sxs-lookup"><span data-stu-id="98084-141">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="98084-142">`get` ステートメントは、返された値を `varValue` プライベート変数に格納されている値に設定します。`set` ステートメントは、`value` キーワードを使用してプライベート変数の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="98084-142">The `get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `set` statement sets the value of the private variable by use of the `value` keyword.</span></span>  
  
3.  <span data-ttu-id="98084-143">**[ファイル]** メニューの **[すべて保存]** をクリックして、プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="98084-143">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
## <a name="testing-your-control"></a><span data-ttu-id="98084-144">コントロールのテスト</span><span class="sxs-lookup"><span data-stu-id="98084-144">Testing Your Control</span></span>  
 <span data-ttu-id="98084-145">コントロールはスタンドアロン プロジェクトではないため、コンテナー内でホストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="98084-145">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="98084-146">コントロールをテストするには、コントロールを実行するテスト プロジェクトを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98084-146">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="98084-147">また、コントロールをビルド (コンパイル) して、テスト プロジェクトからアクセスできるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="98084-147">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="98084-148">このセクションでは、コントロールをビルドし、Windows フォームでテストします。</span><span class="sxs-lookup"><span data-stu-id="98084-148">In this section, you will build your control and test it in a Windows Form.</span></span>  
  
#### <a name="to-build-your-control"></a><span data-ttu-id="98084-149">コントロールをビルドするには</span><span class="sxs-lookup"><span data-stu-id="98084-149">To build your control</span></span>  
  
1.  <span data-ttu-id="98084-150">**[ビルド]** メニューの **[ソリューションのビルド]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="98084-150">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="98084-151">コンパイル エラーも警告も発生せずに、ビルドが正常に完了します。</span><span class="sxs-lookup"><span data-stu-id="98084-151">The build should be successful with no compiler errors or warnings.</span></span>  
  
#### <a name="to-create-a-test-project"></a><span data-ttu-id="98084-152">テスト プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="98084-152">To create a test project</span></span>  
  
1.  <span data-ttu-id="98084-153">**[ファイル]** メニューの **[追加]** をポイントし、**[新しいプロジェクト]** をクリックして **[新しいプロジェクトの追加]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="98084-153">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="98084-154">**[Visual C#]** ノードの下の **[Windows]** ノードを選択し、**[Windows フォーム アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="98084-154">Select the **Windows** node, beneath the **Visual C#** node, and click **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="98084-155">**[名前]** ボックスに「`Test`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="98084-155">In the **Name** box, type `Test`.</span></span>  
  
4.  <span data-ttu-id="98084-156">**ソリューション エクスプローラー**で、テスト プロジェクトの **[参照設定]** ノードを右クリックし、ショートカット メニューの **[参照の追加]** をクリックして **[参照の追加]** ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="98084-156">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>  
  
5.  <span data-ttu-id="98084-157">**[プロジェクト]** というラベルのタブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="98084-157">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="98084-158">**[プロジェクト名]** に `ValueButtonLib` プロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="98084-158">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="98084-159">プロジェクトをダブルクリックして、テスト プロジェクトへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="98084-159">Double-click the project to add the reference to the test project.</span></span>  
  
6.  <span data-ttu-id="98084-160">**ソリューション エクスプローラー**で、**[Test]** を右クリックし、**[ビルド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="98084-160">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>  
  
#### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="98084-161">コントロールをフォームに追加するには</span><span class="sxs-lookup"><span data-stu-id="98084-161">To add your control to the form</span></span>  
  
1.  <span data-ttu-id="98084-162">**ソリューション エクスプローラー**で、**[Form1.cs]** を右クリックし、ショートカット メニューの **[デザイナーの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="98084-162">In **Solution Explorer**, right-click **Form1.cs** and choose **View Designer** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="98084-163">**ツールボックス**の **[ValueButtonLib コンポーネント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="98084-163">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="98084-164">**[ValueButton]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="98084-164">Double-click **ValueButton**.</span></span>  
  
     <span data-ttu-id="98084-165">**ValueButton** がフォームに表示されます。</span><span class="sxs-lookup"><span data-stu-id="98084-165">A **ValueButton** appears on the form.</span></span>  
  
3.  <span data-ttu-id="98084-166">**[ValueButton]** を右クリックし、ショートカット メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="98084-166">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="98084-167">**[プロパティ]** ウィンドウで、このコントロールのプロパティを調べます。</span><span class="sxs-lookup"><span data-stu-id="98084-167">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="98084-168">プロパティは、追加のプロパティである `ButtonValue` がある点を除き、標準ボタンで公開されるプロパティと同じです。</span><span class="sxs-lookup"><span data-stu-id="98084-168">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>  
  
5.  <span data-ttu-id="98084-169">`ButtonValue` プロパティを `5` に設定します。</span><span class="sxs-lookup"><span data-stu-id="98084-169">Set the `ButtonValue` property to `5`.</span></span>  
  
6.  <span data-ttu-id="98084-170">**すべての Windows フォーム**のタブ、**ツールボックス**をダブルクリックして**ラベル**を追加する、<xref:System.Windows.Forms.Label>をフォームにコントロールです。</span><span class="sxs-lookup"><span data-stu-id="98084-170">In the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>  
  
7.  <span data-ttu-id="98084-171">ラベルをフォームの中央に配置し直します。</span><span class="sxs-lookup"><span data-stu-id="98084-171">Relocate the label to the center of the form.</span></span>  
  
8.  <span data-ttu-id="98084-172">`valueButton1` をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="98084-172">Double-click `valueButton1`.</span></span>  
  
     <span data-ttu-id="98084-173">**コード エディター**が開き、`valueButton1_Click` イベントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="98084-173">The **Code Editor** opens to the `valueButton1_Click` event.</span></span>  
  
9. <span data-ttu-id="98084-174">次のコード行を挿入します。</span><span class="sxs-lookup"><span data-stu-id="98084-174">Insert the following line of code.</span></span>  
  
    ```csharp  
    label1.Text = valueButton1.ButtonValue.ToString();  
    ```  
  
10. <span data-ttu-id="98084-175">**ソリューション エクスプローラー**で、**[Test]** を右クリックし、ショートカット メニューの **[スタートアップ プロジェクトに設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="98084-175">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>  
  
11. <span data-ttu-id="98084-176">**[デバッグ]** メニューの **[デバッグの開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="98084-176">From the **Debug** menu, select **Start Debugging**.</span></span>  
  
     <span data-ttu-id="98084-177">`Form1` が表示されます。</span><span class="sxs-lookup"><span data-stu-id="98084-177">`Form1` appears.</span></span>  
  
12. <span data-ttu-id="98084-178">[`valueButton1`] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="98084-178">Click `valueButton1`.</span></span>  
  
     <span data-ttu-id="98084-179">`label1` に数字の "5" が表示されます。これは、継承されたコントロールの `ButtonValue` プロパティが、`valueButton1_Click` メソッドによって `label1` に渡されたことを示しています。</span><span class="sxs-lookup"><span data-stu-id="98084-179">The numeral '5' is displayed in `label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `label1` through the `valueButton1_Click` method.</span></span> <span data-ttu-id="98084-180">このようにして、`ValueButton` コントロールは標準の Windows フォーム ボタンの機能をすべて継承しながら、追加のカスタム プロパティを公開します。</span><span class="sxs-lookup"><span data-stu-id="98084-180">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98084-181">参照</span><span class="sxs-lookup"><span data-stu-id="98084-181">See Also</span></span>  
 [<span data-ttu-id="98084-182">コンポーネントによるプログラミング</span><span class="sxs-lookup"><span data-stu-id="98084-182">Programming with Components</span></span>](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
 [<span data-ttu-id="98084-183">コンポーネント作成のチュートリアル</span><span class="sxs-lookup"><span data-stu-id="98084-183">Component Authoring Walkthroughs</span></span>](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 <span data-ttu-id="98084-184">[方法: [ツールボックス アイテムの選択] ダイアログ ボックスにコントロールを表示する](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="98084-184">[How to: Display a Control in the Choose Toolbox Items Dialog Box](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span></span>  
 [<span data-ttu-id="98084-185">チュートリアル: Visual C# による複合コントロールの作成</span><span class="sxs-lookup"><span data-stu-id="98084-185">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)
