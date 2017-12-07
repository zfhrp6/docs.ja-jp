---
title: "方法: カスタム アクティビティ デザイナーを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f0b1f27af6b4ec372b9dbd63e4bc89a5c435efe6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-custom-activity-designer"></a><span data-ttu-id="b1bdf-102">方法: カスタム アクティビティ デザイナーを作成する</span><span class="sxs-lookup"><span data-stu-id="b1bdf-102">How to: Create a Custom Activity Designer</span></span>
<span data-ttu-id="b1bdf-103">カスタム アクティビティ デザイナーは、通常、関連付けられたアクティビティを他のアクティビティと組み合わせることができるように実装されます。他のアクティビティのデザイナーは、アクティビティと一緒にデザイン サーフェイスにドロップできます。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-103">Custom activity designers are typically implemented so that their associated activities are composable with other activities whose designers can be dropped on to the design surface with them.</span></span> <span data-ttu-id="b1bdf-104">この機能は、カスタム アクティビティ デザイナーが、任意のアクティビティを配置できる「ドロップ ゾーン」とも、デザイン画面上の要素の結果のコレクションを管理するための手段を提供することが必要です。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-104">This functionality requires that a custom activity designer provide a "drop zone" where an arbitrary activity can be placed and also the means to manage the resulting collection of elements on the design surface.</span></span> <span data-ttu-id="b1bdf-105">ここでは、そのようなドロップ ゾーンを含むカスタム アクティビティ デザイナーを作成する方法と、デザイナー要素のコレクションを管理するために必要な編集機能を提供するカスタム アクティビティ デザイナーを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-105">This topic describes how to create a custom activity designer that contains such a drop zone and how to create a custom activity designer that provides that editing functionality needed to manage the collection of designer elements.</span></span>  
  
 <span data-ttu-id="b1bdf-106">カスタム アクティビティ デザイナーは、通常、<xref:System.Activities.Presentation.ActivityDesigner> を継承します。これは、特定のデザイナーを持たないアクティビティの既定の基本アクティビティ デザイナー型です。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-106">Custom activity designers typically inherit from <xref:System.Activities.Presentation.ActivityDesigner> which is the default base activity designer type for any activities without a specific designer.</span></span> <span data-ttu-id="b1bdf-107">この型には、プロパティ グリッドと対話し、色やアイコンの管理などの基本的な側面を構成するデザイン時の機能があります。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-107">This type provides the design-time experience of interacting with the property grid and configuring basic aspects such as managing colors and icons.</span></span>  
  
 <span data-ttu-id="b1bdf-108"><xref:System.Activities.Presentation.ActivityDesigner> では、カスタム アクティビティ デザイナーを開発しやすくする 2 つのヘルパー コントロール <xref:System.Activities.Presentation.WorkflowItemPresenter> と <xref:System.Activities.Presentation.WorkflowItemsPresenter> を使用します。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-108"><xref:System.Activities.Presentation.ActivityDesigner> uses two helper controls, <xref:System.Activities.Presentation.WorkflowItemPresenter> and <xref:System.Activities.Presentation.WorkflowItemsPresenter> to make it easier to develop custom activity designers.</span></span> <span data-ttu-id="b1bdf-109">これらは、子要素のドラッグ アンド ドロップ、その子要素の削除、選択、追加などの一般的な機能を処理します。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-109">They handle common functionality like dragging and dropping of child elements, deletion, selection, and addition of those child elements.</span></span> <span data-ttu-id="b1bdf-110"><xref:System.Activities.Presentation.WorkflowItemPresenter> 1 つの子 UI 要素の許可中、「ドロップ ゾーン」を提供する一方、<xref:System.Activities.Presentation.WorkflowItemsPresenter>複数の UI 要素の順序付けなどの機能のサポートを提供することができます、移動、削除、および子要素の追加。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-110">The <xref:System.Activities.Presentation.WorkflowItemPresenter> allows a single child UI element inside, providing the "drop zone", it while the <xref:System.Activities.Presentation.WorkflowItemsPresenter> can provide support multiple UI elements, including additional functionality like the ordering, moving, deleting, and adding of child elements.</span></span>  
  
 <span data-ttu-id="b1bdf-111">カスタム アクティビティ デザイナーの実装におけるもう 1 つの重要なポイントは、ビジュアル編集が、デザイナーで編集している対象のメモリ内インスタンスに、[!INCLUDE[avalon2](../../../includes/avalon2-md.md)] データ バインディングを使用してバインドされるしくみに関係しています。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-111">The other key part of the story that needs highlighting in the implementation of a custom activity designer concerns the way in which the visual edits are bound using [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] data binding to the instance stored in memory of what we are editing in the designer.</span></span> <span data-ttu-id="b1bdf-112">これは、モデル アイテム ツリーによって実現されます。モデル アイテム ツリーは、変更通知やイベント (状態の変化など) の追跡を実現するためにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-112">This is accomplished by the Model Item tree, which is also responsible for enabling change notification and the tracking of events like changes in states.</span></span>  
  
 <span data-ttu-id="b1bdf-113">ここでは、次の 2 つの手順の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-113">This topic outlines two procedures.</span></span>  
  
1.  <span data-ttu-id="b1bdf-114">1 つ目の手順では、他のアクティビティを受け取るドロップ ゾーンを提供する <xref:System.Activities.Presentation.WorkflowItemPresenter> を使用してカスタム アクティビティ デザイナーを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-114">The first procedure describes how to create a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter> that provides the drop zone that receives other activities.</span></span> <span data-ttu-id="b1bdf-115">この手順がに基づいて、[カスタム複合デザイナー - Workflow 項目プレゼンター](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-item-presenter.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-115">This procedure is based on the [Custom Composite Designers - Workflow Item Presenter](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-item-presenter.md) sample.</span></span>  
  
2.  <span data-ttu-id="b1bdf-116">2 つ目の手順では、含まれている要素のコレクションを編集するために必要な機能を提供する <xref:System.Activities.Presentation.WorkflowItemsPresenter> を使用してカスタム アクティビティ デザイナーを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-116">The second procedure describes how to create a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter> that provides the functionality needed to edit of a collection of contained elements.</span></span> <span data-ttu-id="b1bdf-117">この手順がに基づいて、[カスタム複合デザイナー - Workflow Items Presenter](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-items-presenter.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-117">This procedure is based on the [Custom Composite Designers - Workflow Items Presenter](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-items-presenter.md) sample.</span></span>  
  
### <a name="to-create-a-custom-activity-designer-with-a-drop-zone-using-workflowitempresenter"></a><span data-ttu-id="b1bdf-118">WorkflowItemPresenter を使用してドロップ ゾーンを含むカスタム アクティビティ デザイナーを作成するには</span><span class="sxs-lookup"><span data-stu-id="b1bdf-118">To create a custom activity designer with a drop zone using WorkflowItemPresenter</span></span>  
  
1.  <span data-ttu-id="b1bdf-119">[!INCLUDE[vs2010](../../../includes/vs2010-md.md)] を起動します。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-119">Start [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="b1bdf-120">**ファイル**] メニューのをポイント**新規**、し、[**プロジェクト...**.</span><span class="sxs-lookup"><span data-stu-id="b1bdf-120">On the **File** menu, point to **New**, and then select **Project…**.</span></span>  
  
     <span data-ttu-id="b1bdf-121">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-121">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="b1bdf-122">**インストールされたテンプレート**ペインで、 **Windows**優先する言語のカテゴリからです。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-122">In the **Installed Templates** pane, select **Windows** from your preferred language category.</span></span>  
  
4.  <span data-ttu-id="b1bdf-123">**テンプレート**ペインで、 **WPF アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-123">In the **Templates** pane, select **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="b1bdf-124">**名前**ボックスに、入力`UsingWorkflowItemPresenter`です。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-124">In the **Name** box, enter `UsingWorkflowItemPresenter`.</span></span>  
  
6.  <span data-ttu-id="b1bdf-125">**場所**ボックスで、プロジェクトを保存ディレクトリを入力**参照**まで移動します。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-125">In the **Location** box, enter the directory in which you want to save your project, or click **Browse** to navigate to it.</span></span>  
  
7.  <span data-ttu-id="b1bdf-126">**ソリューション**ボックスで、既定値をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-126">In the **Solution** box, accept the default value.</span></span>  
  
8.  <span data-ttu-id="b1bdf-127">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-127">Click **OK**.</span></span>  
  
9. <span data-ttu-id="b1bdf-128">MainWindows.xaml ファイルを右クリックして、**ソリューション エクスプ ローラー**[**削除**ことを確認および**[ok]**で、 **Microsoft Visual Studio**] ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-128">Right-click the MainWindows.xaml file in the **Solution Explorer**, select **Delete** and confirm **OK** in the **Microsoft Visual Studio** dialogue box.</span></span>  
  
10. <span data-ttu-id="b1bdf-129">UsingWorkflowItemPresenter プロジェクトを右クリックして**ソリューション エクスプ ローラー****追加**、し**新しい項目の追加.**</span><span class="sxs-lookup"><span data-stu-id="b1bdf-129">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="b1bdf-130">呼び出すこと、**新しい項目の追加**ダイアログし、選択、 **WPF**からカテゴリ、**インストールされたテンプレート**左側のセクションでします。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-130">to bring up the **Add New Item** dialogue and select the **WPF** category from the **Installed Templates** section on the left.</span></span>  
  
11. <span data-ttu-id="b1bdf-131">選択、**ウィンドウ (WPF)**テンプレート、名前を付けます`RehostingWFDesigner`、 をクリック**追加**です。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-131">Select the  **Window (WPF)** template, name it `RehostingWFDesigner`, and click **Add**.</span></span>  
  
12. <span data-ttu-id="b1bdf-132">RehostingWFDesigner.xaml ファイルを開き、次のコードを貼り付けてアプリケーションの UI を定義します。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-132">Open the RehostingWFDesigner.xaml file and paste the following code into it to define the UI for the application.</span></span>  
  
    ```xml  
    <Window x:Class=" UsingWorkflowItemPresenter.RehostingWFDesigner"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:sapt="clr-namespace:System.Activities.Presentation.Toolbox;assembly=System.Activities.Presentation"  
            xmlns:sys="clr-namespace:System;assembly=mscorlib"  
            Title="Window1" Height="600" Width="900">  
        <Window.Resources>  
            <sys:String x:Key="AssemblyName">System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</sys:String>  
        </Window.Resources>  
        <Grid>  
            <Grid.ColumnDefinitions>  
                <ColumnDefinition Width="2*"/>  
                <ColumnDefinition Width="7*"/>  
                <ColumnDefinition Width="3*"/>  
            </Grid.ColumnDefinitions>  
            <Border Grid.Column="0">  
                <sapt:ToolboxControl Name="Toolbox">  
                    <sapt:ToolboxCategory CategoryName="Basic">  
                        <sapt:ToolboxItemWrapper AssemblyName="{StaticResource AssemblyName}" >  
                            <sapt:ToolboxItemWrapper.ToolName>  
                                System.Activities.Statements.Sequence  
                            </sapt:ToolboxItemWrapper.ToolName>  
                           </sapt:ToolboxItemWrapper>  
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                            <sapt:ToolboxItemWrapper.ToolName>  
                                System.Activities.Statements.WriteLine  
                            </sapt:ToolboxItemWrapper.ToolName>  
  
                        </sapt:ToolboxItemWrapper>  
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                            <sapt:ToolboxItemWrapper.ToolName>  
                                System.Activities.Statements.If  
                            </sapt:ToolboxItemWrapper.ToolName>  
  
                        </sapt:ToolboxItemWrapper>  
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                            <sapt:ToolboxItemWrapper.ToolName>  
                                System.Activities.Statements.While  
                            </sapt:ToolboxItemWrapper.ToolName>  
  
                        </sapt:ToolboxItemWrapper>  
                    </sapt:ToolboxCategory>  
                </sapt:ToolboxControl>  
            </Border>  
            <Border Grid.Column="1" Name="DesignerBorder"/>  
            <Border Grid.Column="2" Name="PropertyBorder"/>  
        </Grid>  
    </Window>  
    ```  
  
13. <span data-ttu-id="b1bdf-133">アクティビティ デザイナーをアクティビティ タイプと関連付けるには、そのアクティビティ デザイナーをメタデータ ストアを使用して登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-133">To associate an activity designer with an activity type, you must register that activity designer with the metadata store.</span></span> <span data-ttu-id="b1bdf-134">この操作を行うには、`RegisterMetadata` メソッドを `RehostingWFDesigner` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-134">To do this, add the `RegisterMetadata` method to the `RehostingWFDesigner` class.</span></span> <span data-ttu-id="b1bdf-135">`RegisterMetadata` メソッドのスコープで <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> オブジェクトを作成し、<xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> メソッドを呼び出して属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-135">Within the scope of the  `RegisterMetadata` method, create an <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> object and call the <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> method to add the attributes to it.</span></span> <span data-ttu-id="b1bdf-136"><xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> メソッドを呼び出して <xref:System.Activities.Presentation.Metadata.AttributeTable> をメタデータ ストアに追加します。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-136">Call the <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> method to add the <xref:System.Activities.Presentation.Metadata.AttributeTable> to the metadata store.</span></span> <span data-ttu-id="b1bdf-137">次のコードには、デザイナーの再ホスト ロジックが含まれています </span><span class="sxs-lookup"><span data-stu-id="b1bdf-137">The following code contains the rehosting logic for the designer.</span></span> <span data-ttu-id="b1bdf-138">(メタデータの登録、`SimpleNativeActivity` のツールボックスへの追加、およびワークフローの作成)。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-138">It registers the metadata, puts the `SimpleNativeActivity` into the toolbox, and creates the workflow.</span></span> <span data-ttu-id="b1bdf-139">このコードを RehostingWFDesigner.xaml.cs ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-139">Put this code into the RehostingWFDesigner.xaml.cs file.</span></span>  
  
    ```  
    using System;  
    using System.Activities.Core.Presentation;  
    using System.Activities.Presentation;  
    using System.Activities.Presentation.Metadata;  
    using System.Activities.Presentation.Toolbox;  
    using System.Activities.Statements;  
    using System.ComponentModel;  
    using System.Windows;  
  
    namespace UsingWorkflowItemPresenter  
    {  
        // Interaction logic for RehostingWFDesigner.xaml  
        public partial class RehostingWFDesigner  
        {  
            public RehostingWFDesigner()  
            {  
                InitializeComponent();  
            }  
  
            protected override void OnInitialized(EventArgs e)  
            {  
                base.OnInitialized(e);  
                // register metadata  
                (new DesignerMetadata()).Register();  
                RegisterCustomMetadata();  
                // add custom activity to toolbox  
                Toolbox.Categories.Add(new ToolboxCategory("Custom activities"));  
                Toolbox.Categories[1].Add(new ToolboxItemWrapper(typeof(SimpleNativeActivity)));  
  
                // create the workflow designer  
                WorkflowDesigner wd = new WorkflowDesigner();  
                wd.Load(new Sequence());  
                DesignerBorder.Child = wd.View;  
                PropertyBorder.Child = wd.PropertyInspectorView;  
  
            }  
  
            void RegisterCustomMetadata()  
            {  
                AttributeTableBuilder builder = new AttributeTableBuilder();  
                builder.AddCustomAttributes(typeof(SimpleNativeActivity), new DesignerAttribute(typeof(SimpleNativeDesigner)));  
                MetadataStore.AddAttributeTable(builder.CreateTable());  
            }  
        }  
    }  
    ```  
  
14. <span data-ttu-id="b1bdf-140">ソリューション エクスプ ローラーで 参照設定 ディレクトリを右クリックし **の参照を追加しています.**</span><span class="sxs-lookup"><span data-stu-id="b1bdf-140">Right-click the References directory in Solution Explorer and select **Add Reference …**</span></span> <span data-ttu-id="b1bdf-141">呼び出すこと、**参照の追加**ダイアログ。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-141">to bring up the **Add Reference** dialogue.</span></span>  
  
15. <span data-ttu-id="b1bdf-142">クリックして、 **.NET**という名前のアセンブリの検索 タブで、 **System.Activities.Core.Presentation**選択して、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-142">Click the **.NET** tab, locate the assembly named **System.Activities.Core.Presentation**, select it and click **OK**.</span></span>  
  
16. <span data-ttu-id="b1bdf-143">同じ手順で次のアセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-143">Using the same procedure, add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="b1bdf-144">System.Data.DataSetExtensions.dll</span><span class="sxs-lookup"><span data-stu-id="b1bdf-144">System.Data.DataSetExtensions.dll</span></span>  
  
    2.  <span data-ttu-id="b1bdf-145">System.Activities.Presentation.dll</span><span class="sxs-lookup"><span data-stu-id="b1bdf-145">System.Activities.Presentation.dll</span></span>  
  
    3.  <span data-ttu-id="b1bdf-146">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="b1bdf-146">System.ServiceModel.Activities.dll</span></span>  
  
17. <span data-ttu-id="b1bdf-147">App.xaml ファイルを開き、StartUpUri の値を"RehostingWFDesigner.xaml"に変更します。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-147">Open the App.xaml file and change the value of the StartUpUri to "RehostingWFDesigner.xaml".</span></span>  
  
18. <span data-ttu-id="b1bdf-148">UsingWorkflowItemPresenter プロジェクトを右クリックして**ソリューション エクスプ ローラー****追加**、し**新しい項目の追加.**</span><span class="sxs-lookup"><span data-stu-id="b1bdf-148">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="b1bdf-149">呼び出すこと、**新しい項目の追加**ダイアログし、選択、**ワークフロー**カテゴリ フォーム、**インストールされたテンプレート**左側のセクションでします。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-149">to bring up the **Add New Item** dialogue and select the **Workflow** category form the **Installed Templates** section on the left.</span></span>  
  
19. <span data-ttu-id="b1bdf-150">選択、**アクティビティ デザイナー**テンプレート、名前を付けます`SimpleNativeDesigner`、 をクリック**追加**です。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-150">Select the **Activity Designer** template, name it `SimpleNativeDesigner`, and click **Add**.</span></span>  
  
20. <span data-ttu-id="b1bdf-151">SimpleNativeDesigner.xaml ファイルを開いて次のコードを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-151">Open the SimpleNativeDesigner.xaml file and paste the following code into it.</span></span> <span data-ttu-id="b1bdf-152">このコードは、<xref:System.Activities.Presentation.ActivityDesigner> をルート要素として使用し、子の型を複合アクティビティ デザイナーに表示できるように、バインディングを使用してデザイナーに <xref:System.Activities.Presentation.WorkflowItemPresenter> を統合する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-152">Note this code uses <xref:System.Activities.Presentation.ActivityDesigner> as your root element and shows how binding is used to integrate <xref:System.Activities.Presentation.WorkflowItemPresenter> into your designer so a child type can be displayed in your composite activity designer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b1bdf-153"><xref:System.Activities.Presentation.ActivityDesigner> のスキーマでは、カスタム アクティビティ デザイナー定義に 1 つの子要素のみを追加できます。ただし、この要素は、`StackPanel`、`Grid` などの複合 UI 要素の可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-153">The schema for <xref:System.Activities.Presentation.ActivityDesigner> allows the addition of only one child element to your custom activity designer definition; however, this element could be a `StackPanel`, `Grid`, or some other composite UI element.</span></span>  
  
    ```xml  
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemPresenter.SimpleNativeDesigner"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"  
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">  
        <sap:ActivityDesigner.Resources>  
            <DataTemplate x:Key="Collapsed">  
                <StackPanel>  
                    <TextBlock>This is the collapsed view</TextBlock>  
                </StackPanel>  
            </DataTemplate>  
            <DataTemplate x:Key="Expanded">  
                <StackPanel>  
                    <TextBlock>Custom Text</TextBlock>  
                    <sap:WorkflowItemPresenter Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"  
                                            HintText="Please drop an activity here" />  
                </StackPanel>  
            </DataTemplate>  
            <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">  
                <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>  
                <Style.Triggers>  
                    <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">  
                        <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>  
                    </DataTrigger>  
                </Style.Triggers>  
            </Style>  
        </sap:ActivityDesigner.Resources>  
        <Grid>  
            <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}" />  
        </Grid>  
    </sap:ActivityDesigner>  
    ```  
  
21. <span data-ttu-id="b1bdf-154">UsingWorkflowItemPresenter プロジェクトを右クリックして**ソリューション エクスプ ローラー****追加**、し**新しい項目の追加.**</span><span class="sxs-lookup"><span data-stu-id="b1bdf-154">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="b1bdf-155">呼び出すこと、**新しい項目の追加**ダイアログし、選択、**ワークフロー**カテゴリ フォーム、**インストールされたテンプレート**左側のセクションでします。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-155">to bring up the **Add New Item** dialogue and select the **Workflow** category form the **Installed Templates** section on the left.</span></span>  
  
22. <span data-ttu-id="b1bdf-156">選択、**コード アクティビティ**テンプレート、名前を付けます`SimpleNativeActivity`、 をクリック**追加**です。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-156">Select the  **Code Activity** template, name it `SimpleNativeActivity`, and click **Add**.</span></span>  
  
23. <span data-ttu-id="b1bdf-157">SimpleNativeActivity.cs ファイルに次のコードを入力して、`SimpleNativeActivity` クラスを実装します。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-157">Implement the `SimpleNativeActivity` class by entering the following code into the SimpleNativeActivity.cs file.</span></span>  
  
    ```  
    using System.Activities;  
  
    namespace UsingWorkflowItemPresenter  
    {  
        public sealed class SimpleNativeActivity : NativeActivity  
        {  
            // this property contains an activity that will be scheduled in the execute method  
    // the WorkflowItemPresenter in the designer is bound to this to enable editing  
    // of the value  
            public Activity Body { get; set; }  
  
            protected override void CacheMetadata(NativeActivityMetadata metadata)  
            {  
               metadata.AddChild(Body);  
               base.CacheMetadata(metadata);  
  
            }  
  
            protected override void Execute(NativeActivityContext context)  
            {  
                context.ScheduleActivity(Body);  
            }  
        }  
    }  
    ```  
  
24. <span data-ttu-id="b1bdf-158">選択**ソリューションのビルド**から、**ビルド**メニュー。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-158">Select **Build Solution** from the **Build** menu.</span></span>  
  
25. <span data-ttu-id="b1bdf-159">選択**デバッグなしで開始**から、**デバッグ**を開くには、再ホストされたカスタム デザイン ウィンドウのメニュー。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-159">Select **Start Without Debugging** from the **Debug** menu to open the rehosted custom design window.</span></span>  
  
### <a name="to-create-a-custom-activity-designer-using-workflowitemspresenter"></a><span data-ttu-id="b1bdf-160">WorkflowItemsPresenter を使用してカスタム アクティビティ デザイナーを作成するには</span><span class="sxs-lookup"><span data-stu-id="b1bdf-160">To create a custom activity designer using WorkflowItemsPresenter</span></span>  
  
1.  <span data-ttu-id="b1bdf-161">2 番目のカスタム アクティビティ デザイナーの手順は、2 番目のアプリケーションの名前を修正して、いくつか、最初の 1 つは、parallels`UsingWorkflowItemsPresenter`です。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-161">The procedure for the second custom activity designer is the parallels the first with a few modifications, the first of which is to name the second application `UsingWorkflowItemsPresenter`.</span></span> <span data-ttu-id="b1bdf-162">また、このアプリケーションでは新しいカスタム アクティビティを定義しません。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-162">Also this application does not define a new custom activity.</span></span>  
  
2.  <span data-ttu-id="b1bdf-163">主な相違点は、CustomParallelDesigner.xaml ファイルと RehostingWFDesigner.xaml.cs ファイルに含まれています。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-163">Key differences are contained in the CustomParallelDesigner.xaml and RehostingWFDesigner.xaml.cs files.</span></span> <span data-ttu-id="b1bdf-164">次のコードは、UI を定義する CustomParallelDesigne.xaml ファイルのコードです。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-164">Here is the code from the CustomParallelDesigne.xaml file that defines the UI.</span></span>  
  
    ```xml  
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemsPresenter.CustomParallelDesigner"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"  
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">  
        <sap:ActivityDesigner.Resources>  
            <DataTemplate x:Key="Collapsed">  
                <TextBlock>This is the Collapsed View</TextBlock>  
            </DataTemplate>  
            <DataTemplate x:Key="Expanded">  
                <StackPanel>  
                    <TextBlock HorizontalAlignment="Center">This is the</TextBlock>  
                    <TextBlock HorizontalAlignment="Center">extended view</TextBlock>  
                    <sap:WorkflowItemsPresenter HintText="Drop Activities Here"  
                                        Items="{Binding Path=ModelItem.Branches}">  
                        <sap:WorkflowItemsPresenter.SpacerTemplate>  
                            <DataTemplate>  
                                <Ellipse Width="10" Height="10" Fill="Black"/>  
                            </DataTemplate>  
                        </sap:WorkflowItemsPresenter.SpacerTemplate>  
                        <sap:WorkflowItemsPresenter.ItemsPanel>  
                            <ItemsPanelTemplate>  
                                <StackPanel Orientation="Horizontal"/>  
                            </ItemsPanelTemplate>  
                        </sap:WorkflowItemsPresenter.ItemsPanel>  
                    </sap:WorkflowItemsPresenter>  
                </StackPanel>  
            </DataTemplate>  
            <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">  
                <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>  
                <Style.Triggers>  
                    <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">  
                        <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>  
                    </DataTrigger>  
                </Style.Triggers>  
            </Style>  
        </sap:ActivityDesigner.Resources>  
        <Grid>  
            <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>  
        </Grid>  
    </sap:ActivityDesigner>  
    ```  
  
3.  <span data-ttu-id="b1bdf-165">次のコードは、再ホスト ロジックを提供する RehostingWFDesigner.xaml.cs ファイルのコードです。</span><span class="sxs-lookup"><span data-stu-id="b1bdf-165">Here is the code from the RehostingWFDesigner.xaml.cs file that provides the rehosting logic.</span></span>  
  
    ```  
    using System;  
    using System.Activities.Core.Presentation;  
    using System.Activities.Presentation;  
    using System.Activities.Presentation.Metadata;  
    using System.Activities.Statements;  
    using System.ComponentModel;  
    using System.Windows;  
  
    namespaceUsingWorkflowItemsPresenter  
    {  
        public partial class RehostingWfDesigner : Window  
        {  
            public RehostingWfDesigner()  
            {  
                InitializeComponent();  
            }  
  
            protected override void OnInitialized(EventArgs e)  
            {  
                base.OnInitialized(e);  
                // register metadata  
                (new DesignerMetadata()).Register();  
                RegisterCustomMetadata();  
  
                // create the workflow designer  
                WorkflowDesigner wd = new WorkflowDesigner();  
                wd.Load(new Sequence());  
                DesignerBorder.Child = wd.View;  
                PropertyBorder.Child = wd.PropertyInspectorView;  
  
            }  
  
            void RegisterCustomMetadata()  
            {  
                AttributeTableBuilder builder = new AttributeTableBuilder();  
                builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));  
                MetadataStore.AddAttributeTable(builder.CreateTable());  
            }  
        }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b1bdf-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1bdf-166">See Also</span></span>  
 <xref:System.Activities.Presentation.ActivityDesigner>  
 <xref:System.Activities.Presentation.WorkflowItemPresenter>  
 <xref:System.Activities.Presentation.WorkflowItemsPresenter>  
 <xref:System.Activities.Presentation.WorkflowViewElement>  
 <xref:System.Activities.Presentation.Model.ModelItem>  
 [<span data-ttu-id="b1bdf-167">ワークフロー デザイン操作のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="b1bdf-167">Customizing the Workflow Design Experience</span></span>](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)
