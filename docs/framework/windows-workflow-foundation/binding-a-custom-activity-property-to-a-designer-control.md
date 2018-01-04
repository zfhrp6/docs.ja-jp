---
title: "デザイナー コントロールへのカスタム アクティビティ プロパティのバインド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e8061ea-10f5-407c-a31f-d0d74ce12f27
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79ceeb7406fdae9b4044053e12bec2aad926f26e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="binding-a-custom-activity-property-to-a-designer-control"></a><span data-ttu-id="50a1d-102">デザイナー コントロールへのカスタム アクティビティ プロパティのバインド</span><span class="sxs-lookup"><span data-stu-id="50a1d-102">Binding a custom activity property to a designer control</span></span>
<span data-ttu-id="50a1d-103">テキスト ボックスのデザイナー コントロールをアクティビティ引数にバインドする方法はきわめて簡単ですが、コンボ ボックスなどの複合デザイナー コントロールをアクティビティ引数にバインドする場合は困難が伴うことがあります。</span><span class="sxs-lookup"><span data-stu-id="50a1d-103">Binding a text box designer control to an activity argument is fairly straightforward; binding a complex designer control (such as a combo box) to an activity argument may present challenges, however.</span></span> <span data-ttu-id="50a1d-104">このトピックでは、カスタム アクティビティ デザイナーでアクティビティ引数をコンボ ボックス コントロールにバインドする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="50a1d-104">This topic discusses how to bind an activity argument to a combo box control on a custom activity designer.</span></span>  
  
#### <a name="creating-the-combo-box-item-converter"></a><span data-ttu-id="50a1d-105">コンボ ボックス項目コンバーターの作成</span><span class="sxs-lookup"><span data-stu-id="50a1d-105">Creating the combo box item converter</span></span>  
  
1.  <span data-ttu-id="50a1d-106">Visual Studio で、CustomProperty という名前で新しい空のソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="50a1d-106">Create a new empty solution in Visual Studio called CustomProperty.</span></span>  
  
2.  <span data-ttu-id="50a1d-107">ComboBoxItemConverter という名前で新しいクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="50a1d-107">Create a new class called ComboBoxItemConverter.</span></span> <span data-ttu-id="50a1d-108">System.Windows.Data に参照を追加し、<xref:System.Windows.Data.IValueConverter> の派生クラスを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="50a1d-108">Add a reference to System.Windows.Data, and have the class derive from <xref:System.Windows.Data.IValueConverter>.</span></span> <span data-ttu-id="50a1d-109">Visual Studio で、`Convert` および `ConvertBack` のスタブを生成するインターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="50a1d-109">Have Visual Studio implement the interface to generate stubs for `Convert` and `ConvertBack`.</span></span>  
  
3.  <span data-ttu-id="50a1d-110">`Convert` メソッドに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="50a1d-110">Add the following code to the `Convert` method.</span></span> <span data-ttu-id="50a1d-111">次のコードはアクティビティの <xref:System.Activities.InArgument%601> 型の <xref:System.String> をデザイナーに配置される値に変換します。</span><span class="sxs-lookup"><span data-stu-id="50a1d-111">This code converts the activity's <xref:System.Activities.InArgument%601> of type <xref:System.String> to the value to be placed in the designer.</span></span>  
  
    ```  
    ModelItem modelItem = value as ModelItem;  
    if (value != null)  
    {  
        InArgument<string> inArgument = modelItem.GetCurrentValue() as InArgument<string>;  
  
        if (inArgument != null)  
        {  
            Activity<string> expression = inArgument.Expression;  
            VisualBasicValue<string> vbexpression = expression as VisualBasicValue<string>;  
            Literal<string> literal = expression as Literal<string>;  
  
            if (literal != null)  
            {  
                return "\"" + literal.Value + "\"";  
            }  
            else if (vbexpression != null)  
            {  
                return vbexpression.ExpressionText;  
            }  
        }  
    }  
    return null;  
    ```  
  
     <span data-ttu-id="50a1d-112">上のコード スニペットの式は、<xref:Microsoft.CSharp.Activities.CSharpValue%601> の代わりに <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> を使用しても作成できます。</span><span class="sxs-lookup"><span data-stu-id="50a1d-112">The expression in the above code snippet can also be created using <xref:Microsoft.CSharp.Activities.CSharpValue%601> instead of <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span></span>  
  
    ```  
    ModelItem modelItem = value as ModelItem;  
    if (value != null)  
    {  
        InArgument<string> inArgument = modelItem.GetCurrentValue() as InArgument<string>;  
  
        if (inArgument != null)  
        {  
            Activity<string> expression = inArgument.Expression;  
            CSharpValue<string> csexpression = expression as CSharpValue<string>;  
            Literal<string> literal = expression as Literal<string>;  
  
            if (literal != null)  
            {  
                return "\"" + literal.Value + "\"";  
            }  
            else if (csexpression != null)  
            {  
                return csexpression.ExpressionText;  
            }  
        }  
    }  
    return null;  
    ```  
  
4.  <span data-ttu-id="50a1d-113">`ConvertBack` メソッドに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="50a1d-113">Add the following code to the `ConvertBack` method.</span></span> <span data-ttu-id="50a1d-114">このコードは受信コンボ ボックス項目を <xref:System.Activities.InArgument%601> に戻します。</span><span class="sxs-lookup"><span data-stu-id="50a1d-114">This code converts the incoming combo box item back to an <xref:System.Activities.InArgument%601>.</span></span>  
  
    ```  
    // Convert combo box value to InArgument<string>  
                string itemContent = (string)((ComboBoxItem)value).Content;  
                VisualBasicValue<string> vbArgument = new VisualBasicValue<string>(itemContent);  
                InArgument<string> inArgument = new InArgument<string>(vbArgument);  
                return inArgument;  
    ```  
  
     <span data-ttu-id="50a1d-115">上のコード スニペットの式は、<xref:Microsoft.CSharp.Activities.CSharpValue%601> の代わりに <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> を使用しても作成できます。</span><span class="sxs-lookup"><span data-stu-id="50a1d-115">The expression in the above code snippet can also be created using <xref:Microsoft.CSharp.Activities.CSharpValue%601> instead of <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span></span>  
  
    ```  
    // Convert combo box value to InArgument<string>  
                string itemContent = (string)((ComboBoxItem)value).Content;  
                CSharpValue<string> csArgument = new CSharpValue<string>(itemContent);  
                InArgument<string> inArgument = new InArgument<string>(csArgument);  
                return inArgument;  
    ```  
  
#### <a name="adding-the-comboboxitemconverter-to-the-custom-designer-of-an-activity"></a><span data-ttu-id="50a1d-116">アクティビティのカスタム デザイナーへの ComboBoxItemConverter の追加</span><span class="sxs-lookup"><span data-stu-id="50a1d-116">Adding the ComboBoxItemConverter to the custom designer of an activity</span></span>  
  
1.  <span data-ttu-id="50a1d-117">新しい項目をプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="50a1d-117">Add a new item to the project.</span></span> <span data-ttu-id="50a1d-118">[新しい項目] ダイアログ ボックスで [ワークフロー] ノードを選択し、新しい項目の種類として [アクティビティ デザイナー] を選択します。</span><span class="sxs-lookup"><span data-stu-id="50a1d-118">In the New Item dialog, select the Workflow node and select Activity Designer as the type of the new item.</span></span> <span data-ttu-id="50a1d-119">項目に CustomPropertyDesigner という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="50a1d-119">Name the item CustomPropertyDesigner.</span></span>  
  
2.  <span data-ttu-id="50a1d-120">新しいデザイナーにコンボ ボックスを追加します。</span><span class="sxs-lookup"><span data-stu-id="50a1d-120">Add a Combo Box to the new designer.</span></span> <span data-ttu-id="50a1d-121">Items プロパティには、コンボ ボックスに 2 つの項目を追加し、コンテンツの値に "Item1" および "Item2" を指定します。</span><span class="sxs-lookup"><span data-stu-id="50a1d-121">In the Items property, add a couple of items to the combo box, with Content values of "Item1" and 'Item2".</span></span>  
  
3.  <span data-ttu-id="50a1d-122">コンボ ボックスの XAML を変更し、新しい項目コンバーターをコンボ ボックスに使用する項目コンバーターとして追加します。</span><span class="sxs-lookup"><span data-stu-id="50a1d-122">Modify the XAML of the combo box to add the new item converter as the item converter to be used for the combo box.</span></span> <span data-ttu-id="50a1d-123">コンバーターは ActivityDesigner.Resources セグメントにリソースとして追加され、<xref:System.Windows.Controls.ComboBox> の Converter 属性にコンバーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="50a1d-123">The converter is added as a resource in the ActivityDesigner.Resources segment, and specifies the converter in the Converter attribute for the <xref:System.Windows.Controls.ComboBox>.</span></span> <span data-ttu-id="50a1d-124">プロジェクトの名前空間はアクティビティ デザイナーの名前空間属性で指定します。デザイナーを別のプロジェクトで使用する場合は、この名前空間を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="50a1d-124">Note that the namespace of the project is specified in the namespaces attributes for the activity designer; if the designer is to be used in a different project, this namespace will need to be changed.</span></span>  
  
    ```  
    <sap:ActivityDesigner x:Class="CustomProperty.CustomPropertyDesigner"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:c="clr-namespace:CustomProperty"  
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"  
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">  
  
        <sap:ActivityDesigner.Resources>  
            <ResourceDictionary>  
                <c:ComboBoxItemConverter x:Key="comboBoxItemConverter"/>  
            </ResourceDictionary>  
        </sap:ActivityDesigner.Resources>  
        <Grid>  
            <ComboBox SelectedValue="{Binding Path=ModelItem.Text, Mode=TwoWay, Converter={StaticResource comboBoxItemConverter}}"  Height="23" HorizontalAlignment="Left" Margin="132,5,0,0" Name="comboBox1" VerticalAlignment="Top" Width="120" ItemsSource="{Binding}">  
                <ComboBoxItem>item1</ComboBoxItem>  
                <ComboBoxItem>item2</ComboBoxItem>  
            </ComboBox>  
        </Grid>  
    </sap:ActivityDesigner>  
    ```  
  
4.  <span data-ttu-id="50a1d-125"><xref:System.Activities.CodeActivity> 型の新しい項目を作成します。</span><span class="sxs-lookup"><span data-stu-id="50a1d-125">Create a new item of type <xref:System.Activities.CodeActivity>.</span></span> <span data-ttu-id="50a1d-126">この例では、アクティビティの IDE によって作成された既定のコードで十分です。</span><span class="sxs-lookup"><span data-stu-id="50a1d-126">The default code created by the IDE for the activity will be sufficient for this example.</span></span>  
  
5.  <span data-ttu-id="50a1d-127">クラス定義に次の属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="50a1d-127">Add the following attribute to the class definition:</span></span>  
  
    ```  
    [Designer(typeof(CustomPropertyDesigner))]  
    ```  
  
     <span data-ttu-id="50a1d-128">この行は、新しいデザイナーを新しいクラスに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="50a1d-128">This line associates the new designer with the new class.</span></span>  
  
 <span data-ttu-id="50a1d-129">これで新しいアクティビティがデザイナーに関連付けられました。</span><span class="sxs-lookup"><span data-stu-id="50a1d-129">The new activity should now be associated with the designer.</span></span> <span data-ttu-id="50a1d-130">新しいアクティビティをテストするには、アクティビティをワークフローに追加し、コンボ ボックスに 2 つの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="50a1d-130">To test the new activity, add it to a workflow, and set the combo box to the two values.</span></span> <span data-ttu-id="50a1d-131">プロパティ ウィンドウが更新されてコンボ ボックスの値が反映されます。</span><span class="sxs-lookup"><span data-stu-id="50a1d-131">The properties window should update to reflect the combo box value.</span></span>
