---
title: プロパティ グリッドの拡張
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3530c3a3-756d-4712-9f10-fb2897414d3a
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9356e30a8b2d53a149e58f52f21fa6626dff0a75
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="property-grid-extensibliity"></a><span data-ttu-id="bd16a-102">プロパティ グリッドの拡張</span><span class="sxs-lookup"><span data-stu-id="bd16a-102">Property Grid Extensibliity</span></span>
<span data-ttu-id="bd16a-103">開発者は、デザイナー内で特定のアクティビティを選択したときに表示されるプロパティ グリッドをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="bd16a-103">A developer can customize the property grid that is displayed when a given activity is selected within the designer.</span></span> <span data-ttu-id="bd16a-104">これにより、高度な編集操作の作成が可能になります。</span><span class="sxs-lookup"><span data-stu-id="bd16a-104">This can be done to create a rich editing experience.</span></span> <span data-ttu-id="bd16a-105">このサンプルでは、その方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bd16a-105">This sample shows how this can be done.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="bd16a-106">使用例</span><span class="sxs-lookup"><span data-stu-id="bd16a-106">Demonstrates</span></span>  
 <span data-ttu-id="bd16a-107">ワークフロー デザイナーのプロパティ グリッドの拡張。</span><span class="sxs-lookup"><span data-stu-id="bd16a-107">Workflow designer property grid extensibility.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bd16a-108">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="bd16a-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bd16a-109">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="bd16a-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bd16a-110">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="bd16a-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bd16a-111">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="bd16a-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`  
  
## <a name="discussion"></a><span data-ttu-id="bd16a-112">説明</span><span class="sxs-lookup"><span data-stu-id="bd16a-112">Discussion</span></span>  
 <span data-ttu-id="bd16a-113">開発者がプロパティ グリッドを拡張できるように、プロパティ グリッド エディターのインラインの外観をカスタマイズするオプションと、高度な編集画面用のダイアログを表示するオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="bd16a-113">To extend the property grid, a developer has options to customize the inline appearance of a property grid editor or provide a dialog that appears for a more advanced editing surface.</span></span> <span data-ttu-id="bd16a-114">このサンプルでは、インライン エディターとダイアログ エディターの 2 種類のエディターを示します。</span><span class="sxs-lookup"><span data-stu-id="bd16a-114">There are two different editors demonstrated in this sample; an inline editor and a dialog editor.</span></span>  
  
## <a name="inline-editor"></a><span data-ttu-id="bd16a-115">インライン エディター</span><span class="sxs-lookup"><span data-stu-id="bd16a-115">Inline Editor</span></span>  
 <span data-ttu-id="bd16a-116">インライン エディターのサンプルで示す内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bd16a-116">The inline editor sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="bd16a-117"><xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor> から派生する型を作成します。</span><span class="sxs-lookup"><span data-stu-id="bd16a-117">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span></span>  
  
-   <span data-ttu-id="bd16a-118">コンス トラクターで、 <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> Windows Presentation Foundation (WPF) データ テンプレートを使用して値を設定します。</span><span class="sxs-lookup"><span data-stu-id="bd16a-118">In the constructor, the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value is set with a Windows Presentation Foundation (WPF) data template.</span></span> <span data-ttu-id="bd16a-119">これは XAML テンプレートにバインドできますが、このサンプルではコードを使用してデータ バインディングを初期化します。</span><span class="sxs-lookup"><span data-stu-id="bd16a-119">This can be bound to a XAML template, but in this sample, code is used to initialize data binding.</span></span>  
  
-   <span data-ttu-id="bd16a-120">プロパティ グリッドに表示される項目の <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> のデータ コンテキストは、データ テンプレートに含まれています。</span><span class="sxs-lookup"><span data-stu-id="bd16a-120">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="bd16a-121">次のコード (CustomInlineEditor.cs のコード) で、このコンテキストが `Value` プロパティにバインドされていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="bd16a-121">Note in the following code (from CustomInlineEditor.cs) that this context then binds to the `Value` property.</span></span>  
  
    ```csharp  
    FrameworkElementFactory stack = new FrameworkElementFactory(typeof(StackPanel));  
    FrameworkElementFactory slider = new FrameworkElementFactory(typeof(Slider));  
    Binding sliderBinding = new Binding("Value");  
    sliderBinding.Mode = BindingMode.TwoWay;  
    slider.SetValue(Slider.MinimumProperty, 0.0);  
    slider.SetValue(Slider.MaximumProperty, 100.0);  
    slider.SetValue(Slider.ValueProperty, sliderBinding);  
    stack.AppendChild(slider);  
    ```  
  
-   <span data-ttu-id="bd16a-122">アクティビティとデザイナーが同じアセンブリにあるため、アクティビティ デザイナーの属性の登録は、アクティビティ自体の静的コンストラクターで行われます。SimpleCodeActivity.cs の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bd16a-122">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>  
  
    ```  
    static SimpleCodeActivity()  
    {  
        AttributeTableBuilder builder = new AttributeTableBuilder();  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));  
        MetadataStore.AddAttributeTable(builder.CreateTable());  
    }  
    ```  
  
## <a name="dialog-editor"></a><span data-ttu-id="bd16a-123">ダイアログ エディター</span><span class="sxs-lookup"><span data-stu-id="bd16a-123">Dialog Editor</span></span>  
 <span data-ttu-id="bd16a-124">ダイアログ エディターのサンプルで示す内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bd16a-124">The dialog editor sample demonstrates the following:</span></span>  
  
1.  <span data-ttu-id="bd16a-125"><xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor> から派生する型を作成します。</span><span class="sxs-lookup"><span data-stu-id="bd16a-125">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span></span>  
  
2.  <span data-ttu-id="bd16a-126">コンストラクターで、<xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> データ テンプレートを使用して [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] 値を設定します。</span><span class="sxs-lookup"><span data-stu-id="bd16a-126">Sets the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value in the constructor with a [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] data template.</span></span> <span data-ttu-id="bd16a-127">これは XAML で作成できますが、このサンプルではコードで作成します。</span><span class="sxs-lookup"><span data-stu-id="bd16a-127">This can be created in XAML, but in this sample, this is created in code.</span></span>  
  
3.  <span data-ttu-id="bd16a-128">プロパティ グリッドに表示される項目の <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> のデータ コンテキストは、データ テンプレートに含まれています。</span><span class="sxs-lookup"><span data-stu-id="bd16a-128">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="bd16a-129">次のコードで、これが `Value` プロパティにバインドされています。</span><span class="sxs-lookup"><span data-stu-id="bd16a-129">In the following code, this then binds to the `Value` property.</span></span> <span data-ttu-id="bd16a-130">FilePickerEditor.cs では、ダイアログを起動するボタンを指定するための <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> を含めることも重要です。</span><span class="sxs-lookup"><span data-stu-id="bd16a-130">It is critical to also include an <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> to provide the button that raises the dialog in FilePickerEditor.cs.</span></span>  
  
    ```  
    this.InlineEditorTemplate = new DataTemplate();  
  
    FrameworkElementFactory stack = new FrameworkElementFactory(typeof(StackPanel));  
    stack.SetValue(StackPanel.OrientationProperty, Orientation.Horizontal);  
    FrameworkElementFactory label = new FrameworkElementFactory(typeof(Label));  
    Binding labelBinding = new Binding("Value");  
    label.SetValue(Label.ContentProperty, labelBinding);  
    label.SetValue(Label.MaxWidthProperty, 90.0);  
  
    stack.AppendChild(label);  
  
    FrameworkElementFactory editModeSwitch = new FrameworkElementFactory(typeof(EditModeSwitchButton));  
  
    editModeSwitch.SetValue(EditModeSwitchButton.TargetEditModeProperty, PropertyContainerEditMode.Dialog);  
  
    stack.AppendChild(editModeSwitch);  
  
    this.InlineEditorTemplate.VisualTree = stack;  
    ```  
  
4.  <span data-ttu-id="bd16a-131">上書き、 <!--zz <xref:Microsoft.Windows.Design.PropertyEditing.ShowDialog%2A>--> `Microsoft.Windows.Design.PropertyEditing.ShowDialog`ダイアログの表示を処理するデザイナー型のメソッドです。</span><span class="sxs-lookup"><span data-stu-id="bd16a-131">Overrides the <!--zz <xref:Microsoft.Windows.Design.PropertyEditing.ShowDialog%2A>--> `Microsoft.Windows.Design.PropertyEditing.ShowDialog` method in the designer type to handle the display of the dialog.</span></span> <span data-ttu-id="bd16a-132">このサンプルでは、基本的な <xref:System.Windows.Forms.FileDialog> を示します。</span><span class="sxs-lookup"><span data-stu-id="bd16a-132">In this sample, a basic <xref:System.Windows.Forms.FileDialog> is shown.</span></span>  
  
    ```  
    public override void ShowDialog(PropertyValue propertyValue, IInputElement commandSource)  
    {  
        Microsoft.Win32.OpenFileDialog ofd = new Microsoft.Win32.OpenFileDialog();  
        if (ofd.ShowDialog() == true)  
        {  
            propertyValue.Value = ofd.FileName;  
        }  
    }  
    ```  
  
5.  <span data-ttu-id="bd16a-133">アクティビティとデザイナーが同じアセンブリにあるため、アクティビティ デザイナーの属性の登録は、アクティビティ自体の静的コンストラクターで行われます。SimpleCodeActivity.cs の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bd16a-133">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>  
  
    ```  
    static SimpleCodeActivity()  
    {  
        AttributeTableBuilder builder = new AttributeTableBuilder();  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));  
        MetadataStore.AddAttributeTable(builder.CreateTable());  
    }  
    ```  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bd16a-134">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="bd16a-134">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="bd16a-135">ソリューションをビルドし、Workflow1.xaml を開きます。</span><span class="sxs-lookup"><span data-stu-id="bd16a-135">Build the solution, and then open Workflow1.xaml.</span></span>  
  
2.  <span data-ttu-id="bd16a-136">ドラッグ、 **SimpleCodeActivity**ツールボックスからデザイナー キャンバスにします。</span><span class="sxs-lookup"><span data-stu-id="bd16a-136">Drag a **SimpleCodeActivity** from the toolbox onto the designer canvas.</span></span>  
  
3.  <span data-ttu-id="bd16a-137">クリックして、 **SimpleCodeActivity**スライダー コントロールとが、ファイルのコントロールを選択し、プロパティ グリッドを開きます。</span><span class="sxs-lookup"><span data-stu-id="bd16a-137">Click the **SimpleCodeActivity** and then open the property grid where there is a slider control and a file picking control.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bd16a-138">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="bd16a-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bd16a-139">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="bd16a-139">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bd16a-140">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="bd16a-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bd16a-141">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="bd16a-141">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`
