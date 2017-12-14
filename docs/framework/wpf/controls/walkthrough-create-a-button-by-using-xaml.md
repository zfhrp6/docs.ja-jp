---
title: "チュートリアル : XAML を使用したボタンの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 543e6496c826c864dc77e50fd096fc4cb43f600e
ms.sourcegitcommit: 01ea3686e74ff05e4f6de3d8d46dc603d051ec00
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/13/2017
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a><span data-ttu-id="dd9e8-102">チュートリアル : XAML を使用したボタンの作成</span><span class="sxs-lookup"><span data-stu-id="dd9e8-102">Walkthrough: Create a Button by Using XAML</span></span>
<span data-ttu-id="dd9e8-103">このチュートリアルの目的で使用するためのアニメーションのボタンを作成する方法については、[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-103">The objective of this walkthrough is to learn how to create an animated button for use in a [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] application.</span></span> <span data-ttu-id="dd9e8-104">このチュートリアルでは、スタイルとテンプレートを使用して、コードの再利用やボタン宣言からボタン ロジックを分離するカスタマイズされたボタンのリソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-104">This walkthrough uses styles and a template to create a customized button resource that allows reuse of code and separation of button logic from the button declaration.</span></span> <span data-ttu-id="dd9e8-105">このチュートリアルが完全に書き込まれる[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-105">This walkthrough is written entirely in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dd9e8-106">このチュートリアルでは入力またはコピーして貼り付けることによって、アプリケーションを作成する手順を説明します。 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] microsoft[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-106">This walkthrough guides you through the steps for creating the application by typing or copying and pasting [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] into Microsoft [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="dd9e8-107">デザイン ツール (Microsoft Expression Blend) を使用して、同じアプリケーションを作成する方法を学習したい場合[Microsoft Expression Blend を使用してボタンを作成して](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md)です。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-107">If you would prefer to learn how to use a design tool (Microsoft Expression Blend) to create the same application, see [Create a Button by Using Microsoft Expression Blend](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span></span>  
  
 <span data-ttu-id="dd9e8-108">次の図は、完成したボタンを示しています。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-108">The following figure shows the finished buttons.</span></span>  
  
 <span data-ttu-id="dd9e8-109">![XAML を使用して作成されたカスタム ボタン](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="dd9e8-109">![Custom buttons that were created by using XAML](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>  
  
## <a name="create-basic-buttons"></a><span data-ttu-id="dd9e8-110">基本的なボタンを作成します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-110">Create Basic Buttons</span></span>  
 <span data-ttu-id="dd9e8-111">新しいプロジェクトを作成し、ウィンドウにいくつかのボタンを追加することから始めましょう。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-111">Let's start by creating a new project and adding a few buttons to the window.</span></span>  
  
#### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a><span data-ttu-id="dd9e8-112">新しい WPF プロジェクトを作成し、ボタン、ウィンドウを追加するには</span><span class="sxs-lookup"><span data-stu-id="dd9e8-112">To create a new WPF project and add buttons to the window</span></span>  
  
1.  <span data-ttu-id="dd9e8-113">開始[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-113">Start[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span>  
  
2.  <span data-ttu-id="dd9e8-114">**新しい WPF プロジェクトの作成:**上、**ファイル** メニューのをポイント**新規**、順にクリック**プロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-114">**Create a new WPF project:** On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="dd9e8-115">検索、 **Windows アプリケーション (WPF)**テンプレートとプロジェクト"AnimatedButton"の名前。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-115">Find the **Windows Application (WPF)** template and name the project "AnimatedButton".</span></span> <span data-ttu-id="dd9e8-116">これにより、アプリケーションのスケルトンが作成されます。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-116">This will create the skeleton for the application.</span></span>  
  
3.  <span data-ttu-id="dd9e8-117">**基本的な既定のボタンの追加:**このチュートリアルに必要なすべてのファイルは、テンプレートによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-117">**Add basic default buttons:** All the files you need for this walkthrough are provided by the template.</span></span> <span data-ttu-id="dd9e8-118">ダブルクリックして、ソリューション エクスプ ローラーで、Window1.xaml ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-118">Open the Window1.xaml file by double clicking it in Solution Explorer.</span></span> <span data-ttu-id="dd9e8-119">既定では、 <xref:System.Windows.Controls.Grid> Window1.xaml 内の要素。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-119">By default, there is a <xref:System.Windows.Controls.Grid> element in Window1.xaml.</span></span> <span data-ttu-id="dd9e8-120">削除、<xref:System.Windows.Controls.Grid>要素に、いくつかのボタンを追加して、 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 」と入力またはコピーして貼り付けることによって window1.xaml の名前に次の強調表示されているコード ページ。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-120">Remove the <xref:System.Windows.Controls.Grid> element and add a few buttons to the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page by typing or copy and pasting the following highlighted code to Window1.xaml:</span></span>  
  
    ```xaml  
    <Window x:Class="AnimatedButton.Window1"  
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
      Title="AnimatedButton" Height="300" Width="300"   
      Background="Black">   <!-- Buttons arranged vertically inside a StackPanel. -->   <StackPanel HorizontalAlignment="Left">     <Button>Button 1</Button>     <Button>Button 2</Button>     <Button>Button 3</Button>   </StackPanel>  
  
    </Window>  
    ```  
  
     <span data-ttu-id="dd9e8-121">F5 キーを押してアプリケーションを実行します。次の図のようなボタンのセットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-121">Press F5 to run the application; you should see a set of buttons that looks like the following figure.</span></span>  
  
     <span data-ttu-id="dd9e8-122">![次の 3 つの基本的なボタン](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span><span class="sxs-lookup"><span data-stu-id="dd9e8-122">![Three basic buttons](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span></span>  
  
     <span data-ttu-id="dd9e8-123">基本的なボタンを作成するには、Window1.xaml ファイルで作業が終了します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-123">Now that you have created the basic buttons, you are finished working in the Window1.xaml file.</span></span> <span data-ttu-id="dd9e8-124">このチュートリアルの残りの部分は、スタイルとボタンのテンプレートを定義する、app.xaml ファイルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-124">The rest of the walkthrough focuses on the app.xaml file, defining styles and a template for the buttons.</span></span>  
  
## <a name="set-basic-properties"></a><span data-ttu-id="dd9e8-125">基本的なプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-125">Set Basic Properties</span></span>  
 <span data-ttu-id="dd9e8-126">次に、これらのボタン、ボタンの外観とレイアウトを制御するいくつかのプロパティを設定してみましょう。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-126">Next, let's set some properties on these buttons to control the button appearance and layout.</span></span> <span data-ttu-id="dd9e8-127">ボタンのプロパティを個別に設定するのではなく、アプリケーション全体のボタンのプロパティを定義するのにリソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-127">Rather than setting properties on the buttons individually, you will use resources to define button properties for the entire application.</span></span> <span data-ttu-id="dd9e8-128">アプリケーション リソース、外部に概念的に似ています[!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)]Web ページです。 ただし、リソースがよりもはるかに強力な[!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)]ように、このチュートリアルの最後で表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-128">Application resources are conceptually similar to external [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)] for Web pages; however, resources are much more powerful than [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)], as you will see by the end of this walkthrough.</span></span> <span data-ttu-id="dd9e8-129">リソースの詳細については、次を参照してください。 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)です。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-129">To learn more about resources, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
#### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a><span data-ttu-id="dd9e8-130">プロパティを設定する基本的なボタンのスタイルを使用するには</span><span class="sxs-lookup"><span data-stu-id="dd9e8-130">To use styles to set basic properties on the buttons</span></span>  
  
1.  <span data-ttu-id="dd9e8-131">**Application.Resources ブロックを定義します。** app.xaml を開き、がない場合は、次の強調表示されているマークアップを追加します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-131">**Define an Application.Resources block:** Open app.xaml and add the following highlighted markup if it is not already there:</span></span>  
  
    ```xaml  
    <Application x:Class="AnimatedButton.App"  
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
      StartupUri="Window1.xaml"  
      >  
      <Application.Resources>
        <!-- Resources for the entire application can be defined here. -->
      </Application.Resources>  
    </Application>  
    ```  
  
     <span data-ttu-id="dd9e8-132">リソースのスコープは、定義したリソースによって決まります。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-132">Resource scope is determined by where you define the resource.</span></span> <span data-ttu-id="dd9e8-133">内のリソースを定義する`Application.Resources`app.xaml では、ファイルは、アプリケーションで任意の場所から使用するリソースをことができます。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-133">Defining resources in `Application.Resources` in the app.xaml file enables the resource to be used from anywhere in the application.</span></span> <span data-ttu-id="dd9e8-134">リソースのスコープの定義の詳細については、次を参照してください。 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)です。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-134">To learn more about defining the scope of your resources, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
2.  <span data-ttu-id="dd9e8-135">**スタイルを作成し、それに基本的なプロパティ値を定義します。**に次のマークアップを追加、`Application.Resources`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-135">**Create a style and define basic property values with it:** Add the following markup to the `Application.Resources` block.</span></span> <span data-ttu-id="dd9e8-136">このマークアップを作成、<xref:System.Windows.Style>設定、アプリケーションのすべてのボタンに適用される、<xref:System.Windows.FrameworkElement.Width%2A>を 90 にボタンのおよび<xref:System.Windows.FrameworkElement.Margin%2A>10。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-136">This markup creates a <xref:System.Windows.Style> that applies to all buttons in the application, setting the <xref:System.Windows.FrameworkElement.Width%2A> of the buttons to 90 and the <xref:System.Windows.FrameworkElement.Margin%2A> to 10:</span></span>  
  
    ```xaml  
    <Application.Resources>  
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>  
    </Application.Resources>  
    ```  
  
     <span data-ttu-id="dd9e8-137"><xref:System.Windows.Style.TargetType%2A>プロパティでは、型のすべてのオブジェクトへのスタイルが適用されるように指定<xref:System.Windows.Controls.Button>です。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-137">The <xref:System.Windows.Style.TargetType%2A> property specifies that the style applies to all objects of type <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="dd9e8-138">各<xref:System.Windows.Setter>の別のプロパティ値を設定、<xref:System.Windows.Style>です。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-138">Each <xref:System.Windows.Setter> sets a different property value for the <xref:System.Windows.Style>.</span></span> <span data-ttu-id="dd9e8-139">そのため、この時点でアプリケーションのすべてのボタンが幅 90、余白は 10 です。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-139">Therefore, at this point every button in the application has a width of 90 and a margin of 10.</span></span>  <span data-ttu-id="dd9e8-140">アプリケーションを実行する場合は F5 キーを押した場合、次のウィンドウを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-140">If you press F5 to run the application, you see the following window.</span></span>  
  
     <span data-ttu-id="dd9e8-141">![幅 90、余白 10 の持つボタン](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span><span class="sxs-lookup"><span data-stu-id="dd9e8-141">![Buttons with a width of 90 and a margin of 10](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span></span>  
  
     <span data-ttu-id="dd9e8-142">たくさんありますのさまざまなオブジェクトが対象となるを微調整する方法を含む、複合型プロパティ値を指定する、およびスタイルを使用する入力として他のスタイルのスタイルを使って実行できます。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-142">There is much more you can do with styles, including a variety of ways to fine-tune what objects are targeted, specifying complex property values, and even using styles as input for other styles.</span></span> <span data-ttu-id="dd9e8-143">詳しくは、「 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-143">For more information, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>  
  
3.  <span data-ttu-id="dd9e8-144">**リソースにスタイル プロパティの値を設定:**リソースが簡単に一般的に定義されるオブジェクトとの値を再利用を有効にします。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-144">**Set a style property value to a resource:** Resources enable a simple way to reuse commonly defined objects and values.</span></span> <span data-ttu-id="dd9e8-145">コードにモジュール化するためのリソースを使用して複雑な値を定義すると特に便利です。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-145">It is especially useful to define complex values using resources to make your code more modular.</span></span> <span data-ttu-id="dd9e8-146">App.xaml に次の強調表示されているマークアップを追加します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-146">Add the following highlighted markup to app.xaml.</span></span>  
  
    ```xaml  
    <Application.Resources>  
      <LinearGradientBrush x:Key="GrayBlueGradientBrush" StartPoint="0,0" EndPoint="1,1">
        <GradientStop Color="DarkGray" Offset="0" />
        <GradientStop Color="#CCCCFF" Offset="0.5" />
        <GradientStop Color="DarkGray" Offset="1" />
      </LinearGradientBrush>  
      <Style TargetType="{x:Type Button}">  
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />  
        <Setter Property="Width" Value="80" />  
        <Setter Property="Margin" Value="10" />  
      </Style>  
    </Application.Resources>  
    ```  
  
     <span data-ttu-id="dd9e8-147">直下にある、`Application.Resources`ブロック"GrayBlueGradientBrush"という名前のリソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-147">Directly under the `Application.Resources` block, you created a resource called "GrayBlueGradientBrush".</span></span> <span data-ttu-id="dd9e8-148">このリソースは、水平方向のグラデーションを定義します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-148">This resource defines a horizontal gradient.</span></span> <span data-ttu-id="dd9e8-149">このリソースをどこからでもプロパティの値として使用できますのボタンのスタイル セッターの内側など、アプリケーションで、<xref:System.Windows.Controls.Control.Background%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-149">This resource can be used as a property value from anywhere in the application, including inside the button style setter for the <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="dd9e8-150">ここで、すべてのボタンが、<xref:System.Windows.Controls.Control.Background%2A>このグラデーションのプロパティの値。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-150">Now, all the buttons have a <xref:System.Windows.Controls.Control.Background%2A> property value of this gradient.</span></span>  
  
     <span data-ttu-id="dd9e8-151">F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-151">Press F5 to run the application.</span></span> <span data-ttu-id="dd9e8-152">次のようになります。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-152">It should look like the following.</span></span>  
  
     <span data-ttu-id="dd9e8-153">![グラデーション背景を持つボタン](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span><span class="sxs-lookup"><span data-stu-id="dd9e8-153">![Buttons with a gradient background](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span></span>  
  
## <a name="create-a-template-that-defines-the-look-of-the-button"></a><span data-ttu-id="dd9e8-154">ボタンの外観を定義するテンプレートを作成します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-154">Create a Template That Defines the Look of the Button</span></span>  
 <span data-ttu-id="dd9e8-155">このセクションでは、ボタンの外観 (presentation) をカスタマイズするテンプレートを作成します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-155">In this section, you create a template that customizes the appearance (presentation) of the button.</span></span> <span data-ttu-id="dd9e8-156">ボタンのプレゼンテーションで構成された四角形とその他のコンポーネントを含む複数のオブジェクト、ボタンの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-156">The button presentation is made up of several objects including rectangles and other components to give the button a unique look.</span></span>  
  
 <span data-ttu-id="dd9e8-157">これまでに、アプリケーションでのボタンの外観の制御は、ボタンのプロパティを変更するのに制限されていましたがします。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-157">So far, the control of how buttons look in the application has been confined to changing properties of the button.</span></span> <span data-ttu-id="dd9e8-158">ボタンの外観をより大きく変更する場合ですか。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-158">What if you want to make more radical changes to the button's appearance?</span></span> <span data-ttu-id="dd9e8-159">テンプレートには、オブジェクトのプレゼンテーションに強力な制御が有効にします。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-159">Templates enable powerful control over the presentation of an object.</span></span> <span data-ttu-id="dd9e8-160">スタイル内では、テンプレートを使用できますが、ために、スタイルに適用されます (このチュートリアルでは、ボタン) のすべてのオブジェクトにテンプレートを適用することができます。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-160">Because templates can be used within styles, you can apply a template to all objects that the style applies to (in this walkthrough, the button).</span></span>  
  
#### <a name="to-use-the-template-to-define-the-look-of-the-button"></a><span data-ttu-id="dd9e8-161">ボタンの外観を定義するテンプレートを使用するには</span><span class="sxs-lookup"><span data-stu-id="dd9e8-161">To use the template to define the look of the button</span></span>  
  
1.  <span data-ttu-id="dd9e8-162">**テンプレートのセットアップ:**コントロールなどのため<xref:System.Windows.Controls.Button>が、<xref:System.Windows.Controls.Control.Template%2A>プロパティで設定した他のプロパティ値と同じようにテンプレートのプロパティ値を定義することができます、<xref:System.Windows.Style>を使用して、<xref:System.Windows.Setter>です。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-162">**Set up the template:** Because controls like <xref:System.Windows.Controls.Button> have a <xref:System.Windows.Controls.Control.Template%2A> property, you can define the template property value just like the other property values we have set in a <xref:System.Windows.Style> using a <xref:System.Windows.Setter>.</span></span> <span data-ttu-id="dd9e8-163">次の強調表示されているマークアップをボタンのスタイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-163">Add the following highlighted markup to your button style.</span></span>  
  
    ```xaml
    <Application.Resources>  
      <LinearGradientBrush x:Key="GrayBlueGradientBrush"   
        StartPoint="0,0" EndPoint="1,1">  
        <GradientStop Color="DarkGray" Offset="0" />  
        <GradientStop Color="#CCCCFF" Offset="0.5" />  
        <GradientStop Color="DarkGray" Offset="1" />  
      </LinearGradientBrush>  
      <Style TargetType="{x:Type Button}">  
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />  
        <Setter Property="Width" Value="80" />  
        <Setter Property="Margin" Value="10" />  
        <Setter Property="Template">
          <Setter.Value>
            <!-- The button template is defined here. -->
          </Setter.Value>
        </Setter>  
      </Style>  
    </Application.Resources>  
    ```  
  
2.  <span data-ttu-id="dd9e8-164">**ボタンのプレゼンテーションを alter:**この時点では、テンプレートを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-164">**Alter button presentation:** At this point, you need to define the template.</span></span> <span data-ttu-id="dd9e8-165">次の強調表示されているマークアップを追加します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-165">Add the following highlighted markup.</span></span> <span data-ttu-id="dd9e8-166">このマークアップでは、2 つを指定します<xref:System.Windows.Shapes.Rectangle>角の丸いを持つ要素が続く、<xref:System.Windows.Controls.DockPanel>です。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-166">This markup specifies two <xref:System.Windows.Shapes.Rectangle> elements with rounded edges, followed by a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="dd9e8-167"><xref:System.Windows.Controls.DockPanel>が使用されるホストに、<xref:System.Windows.Controls.ContentPresenter>ボタンのです。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-167">The <xref:System.Windows.Controls.DockPanel> is used to host the <xref:System.Windows.Controls.ContentPresenter> of the button.</span></span> <span data-ttu-id="dd9e8-168">A<xref:System.Windows.Controls.ContentPresenter>ボタンのコンテンツを表示します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-168">A <xref:System.Windows.Controls.ContentPresenter> displays the content of the button.</span></span> <span data-ttu-id="dd9e8-169">このチュートリアルでは、コンテンツは、テキスト (「ボタン 1」、「ボタン 2」、「ボタン 3」) です。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-169">In this walkthrough, the content is text ("Button 1", "Button 2", "Button 3").</span></span> <span data-ttu-id="dd9e8-170">すべてのテンプレートのコンポーネント (四角形と<xref:System.Windows.Controls.DockPanel>) 内のレイアウト、<xref:System.Windows.Controls.Grid>です。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-170">All of the template components (the rectangles and the <xref:System.Windows.Controls.DockPanel>) are laid out inside of a <xref:System.Windows.Controls.Grid>.</span></span>  
  
    ```xaml  
    <Setter.Value>  
      <ControlTemplate TargetType="Button">
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}" ClipToBounds="True">
          <!-- Outer Rectangle with rounded corners. -->
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}" RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />
          <!-- Inner Rectangle with rounded corners. -->
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20" Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />
          <!-- Present Content (text) of the button. -->
          <DockPanel Name="myContentPresenterDockPanel">
            <ContentPresenter x:Name="myContentPresenter" Margin="20" Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
          </DockPanel>
        </Grid>
      </ControlTemplate>  
    </Setter.Value>  
    ```  
  
     <span data-ttu-id="dd9e8-171">F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-171">Press F5 to run the application.</span></span> <span data-ttu-id="dd9e8-172">次のようになります。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-172">It should look like the following.</span></span>  
  
     <span data-ttu-id="dd9e8-173">![](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")</span><span class="sxs-lookup"><span data-stu-id="dd9e8-173">![](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")</span></span>  
  
3.  <span data-ttu-id="dd9e8-174">**グラスをテンプレートに追加:**次ガラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-174">**Add a glasseffect to the template:** Next you will add the glass.</span></span> <span data-ttu-id="dd9e8-175">まず、ガラスのグラデーション効果を作成するリソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-175">First you create some resources that create a glass gradient effect.</span></span> <span data-ttu-id="dd9e8-176">リソースを追加するこれらグラデーション任意の場所内で、`Application.Resources`ブロック。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-176">Add these gradient resources anywhere within the `Application.Resources` block:</span></span>  
  
    ```xaml  
    <Application.Resources>  
      <GradientStopCollection x:Key="MyGlassGradientStopsResource">     <GradientStop Color="WhiteSmoke" Offset="0.2" />     <GradientStop Color="Transparent" Offset="0.4" />     <GradientStop Color="WhiteSmoke" Offset="0.5" />     <GradientStop Color="Transparent" Offset="0.75" />     <GradientStop Color="WhiteSmoke" Offset="0.9" />     <GradientStop Color="Transparent" Offset="1" />   </GradientStopCollection>   <LinearGradientBrush x:Key="MyGlassBrushResource"     StartPoint="0,0" EndPoint="1,1" Opacity="0.75"     GradientStops="{StaticResource MyGlassGradientStopsResource}" />  
    <!-- Styles and other resources below here. -->  
    ```  
  
     <span data-ttu-id="dd9e8-177">これらのリソースとして使用、<xref:System.Windows.Shapes.Shape.Fill%2A>に挿入する四角形の<xref:System.Windows.Controls.Grid>button テンプレートのです。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-177">These resources are used as the <xref:System.Windows.Shapes.Shape.Fill%2A> for a rectangle that we insert into the <xref:System.Windows.Controls.Grid> of the button template.</span></span> <span data-ttu-id="dd9e8-178">次の強調表示されているマークアップをテンプレートに追加します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-178">Add the following highlighted markup to the template.</span></span>  
  
    ```  
    <Setter.Value>  
      <ControlTemplate TargetType="{x:Type Button}">  
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}"  
    ClipToBounds="True">  
  
        <!-- Outer Rectangle with rounded corners. -->  
        <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"   
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"   
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />  
  
        <!-- Inner Rectangle with rounded corners. -->  
        <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"   
          VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20"   
          Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />  
  
        <!-- Glass Rectangle -->     <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"       VerticalAlignment="Stretch"       StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"       Fill="{StaticResource MyGlassBrushResource}"       RenderTransformOrigin="0.5,0.5">       <Rectangle.Stroke>         <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">           <LinearGradientBrush.GradientStops>             <GradientStop Offset="0.0" Color="LightBlue" />             <GradientStop Offset="1.0" Color="Gray" />           </LinearGradientBrush.GradientStops>         </LinearGradientBrush>       </Rectangle.Stroke>       <!-- These transforms have no effect as they are declared here.             The reason the transforms are included is to be targets             for animation (see later). -->       <Rectangle.RenderTransform>         <TransformGroup>           <ScaleTransform />           <RotateTransform />         </TransformGroup>       </Rectangle.RenderTransform>       <!-- A BevelBitmapEffect is applied to give the button a             "Beveled" look. -->       <Rectangle.BitmapEffect>         <BevelBitmapEffect />       </Rectangle.BitmapEffect>     </Rectangle>  
  
        <!-- Present Text of the button. -->  
        <DockPanel Name="myContentPresenterDockPanel">  
          <ContentPresenter x:Name="myContentPresenter" Margin="20"   
            Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />  
        </DockPanel>  
      </Grid>  
    </ControlTemplate>  
    </Setter.Value>  
    ```  
  
     <span data-ttu-id="dd9e8-179">注意して、<xref:System.Windows.UIElement.Opacity%2A>を含む四角形の`x:Name`"glassCube"のプロパティが 0 で、サンプルを実行するときに、上部にオーバーレイ グラス四角形は表示されないようにします。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-179">Notice that the <xref:System.Windows.UIElement.Opacity%2A> of the rectangle with the `x:Name` property of "glassCube" is 0, so when you run the sample, you do not see the glass rectangle overlaid on top.</span></span> <span data-ttu-id="dd9e8-180">これはおは後でトリガーを追加のテンプレートのボタンで、ユーザーが操作するときにあるためです。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-180">This is because we will later add triggers to the template for when the user interacts with the button.</span></span> <span data-ttu-id="dd9e8-181">ただし、ご覧のボタンの外観と同様に今すぐ変更することによって、 <xref:System.Windows.UIElement.Opacity%2A> 1 およびアプリケーションを実行する値。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-181">However, you can see what the button looks like now by changing the <xref:System.Windows.UIElement.Opacity%2A> value to 1 and running the application.</span></span> <span data-ttu-id="dd9e8-182">次の図を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-182">See the following figure.</span></span> <span data-ttu-id="dd9e8-183">次の手順に前に、変更、 <xref:System.Windows.UIElement.Opacity%2A> 0 に戻します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-183">Before proceeding to the next step, change the <xref:System.Windows.UIElement.Opacity%2A> back to 0.</span></span>  
  
     <span data-ttu-id="dd9e8-184">![XAML を使用して作成されたカスタム ボタン](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="dd9e8-184">![Custom buttons that were created by using XAML](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>  
  
## <a name="create-button-interactivity"></a><span data-ttu-id="dd9e8-185">ボタンの対話機能を作成します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-185">Create Button Interactivity</span></span>  
 <span data-ttu-id="dd9e8-186">このセクションでは、プロパティ トリガーと、プロパティ値を変更し、ボタンにマウス ポインターを移動しをクリックするとなどのユーザー アクションへの応答でアニメーションを実行するイベントのトリガーを作成します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-186">In this section, you will create property triggers and event triggers to change property values and run animations in response to user actions such as moving the mouse pointer over the button and clicking.</span></span>  
  
 <span data-ttu-id="dd9e8-187">対話機能 (マウス オーバー、マウスのままにしてをクリックし、およびなど) を追加する簡単な方法では、テンプレートまたはスタイル内でトリガーを定義します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-187">An easy way to add interactivity (mouse-over, mouse-leave, click, and so on) is to define triggers within your template or style.</span></span> <span data-ttu-id="dd9e8-188">作成する、<xref:System.Windows.Trigger>など「条件」プロパティを定義する: ボタン<xref:System.Windows.UIElement.IsMouseOver%2A>プロパティの値と等しい`true`です。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-188">To create a <xref:System.Windows.Trigger>, you define a property "condition" such as: The button <xref:System.Windows.UIElement.IsMouseOver%2A> property value is equal to `true`.</span></span> <span data-ttu-id="dd9e8-189">トリガー条件が true のときに行われる setter (アクション) を定義します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-189">You then define setters (actions) that take place when the trigger condition is true.</span></span>  
  
#### <a name="to-create-button-interactivity"></a><span data-ttu-id="dd9e8-190">ボタンの対話機能を作成するには</span><span class="sxs-lookup"><span data-stu-id="dd9e8-190">To create button interactivity</span></span>  
  
1.  <span data-ttu-id="dd9e8-191">**テンプレートのトリガーを追加:**マークアップを強調表示されているテンプレートに追加します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-191">**Add template triggers:** Add the highlighted markup to your template.</span></span>  
  
    ```  
    <Setter.Value>  
      <ControlTemplate TargetType="{x:Type Button}">  
        <Grid Width="{TemplateBinding Width}"   
          Height="{TemplateBinding Height}" ClipToBounds="True">  
  
          <!-- Outer Rectangle with rounded corners. -->  
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"   
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"   
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />  
  
          <!-- Inner Rectangle with rounded corners. -->  
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"   
            VerticalAlignment="Stretch" Stroke="Transparent"   
            StrokeThickness="20"   
            Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20"   
          />  
  
          <!-- Glass Rectangle -->  
          <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"  
            VerticalAlignment="Stretch"  
            StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"  
            Fill="{StaticResource MyGlassBrushResource}"  
            RenderTransformOrigin="0.5,0.5">  
            <Rectangle.Stroke>  
              <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">  
                <LinearGradientBrush.GradientStops>  
                  <GradientStop Offset="0.0" Color="LightBlue" />  
                  <GradientStop Offset="1.0" Color="Gray" />  
                </LinearGradientBrush.GradientStops>  
              </LinearGradientBrush>  
            </Rectangle.Stroke>  
  
            <!-- These transforms have no effect as they   
                 are declared here.   
                 The reason the transforms are included is to be targets   
                 for animation (see later). -->  
            <Rectangle.RenderTransform>  
              <TransformGroup>  
                <ScaleTransform />  
                <RotateTransform />  
              </TransformGroup>  
            </Rectangle.RenderTransform>  
  
              <!-- A BevelBitmapEffect is applied to give the button a   
                   "Beveled" look. -->  
            <Rectangle.BitmapEffect>  
              <BevelBitmapEffect />  
            </Rectangle.BitmapEffect>  
          </Rectangle>  
  
          <!-- Present Text of the button. -->  
          <DockPanel Name="myContentPresenterDockPanel">  
            <ContentPresenter x:Name="myContentPresenter" Margin="20"   
              Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />  
          </DockPanel>  
        </Grid>  
  
        <ControlTemplate.Triggers>       <!-- Set action triggers for the buttons and define            what the button does in response to those triggers. -->     </ControlTemplate.Triggers>  
      </ControlTemplate>  
    </Setter.Value>  
    ```  
  
2.  <span data-ttu-id="dd9e8-192">**プロパティ トリガーを追加:**強調表示されているマークアップを追加、`ControlTemplate.Triggers`ブロック。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-192">**Add property triggers:** Add the highlighted markup to the `ControlTemplate.Triggers` block:</span></span>  
  
    ```  
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>  
  
    <ControlTemplate.Triggers/>  
    ```  
  
     <span data-ttu-id="dd9e8-193">F5 キーを押してアプリケーションを実行し、ボタンの上にマウス ポインターを実行するように影響を確認します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-193">Press F5 to run the application and see the effect as you run the mouse pointer over the buttons.</span></span>  
  
3.  <span data-ttu-id="dd9e8-194">**フォーカス トリガーを追加する:**次に、ボタンに (たとえば、ユーザーがクリックした後) のフォーカスがあるときに、ケースを処理するいくつかのような set アクセス操作子を追加します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-194">**Add a focus trigger:** Next, we'll add some similar setters to handle the case when the button has focus (for example, after the user clicks it).</span></span>  
  
    ```  
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->  
      <Trigger Property="IsMouseOver" Value="True">  
  
        <!-- Below are three property settings that occur when the   
             condition is met (user mouses over button).  -->  
        <!-- Change the color of the outer rectangle when user          mouses over it. -->  
        <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"  
          Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />  
  
        <!-- Sets the glass opacity to 1, therefore, the          glass "appears" when user mouses over it. -->  
        <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />  
  
        <!-- Makes the text slightly blurry as though you were          looking at it through blurry glass. -->  
        <Setter Property="ContentPresenter.BitmapEffect"       TargetName="myContentPresenter">  
          <Setter.Value>  
            <BlurBitmapEffect Radius="1" />  
          </Setter.Value>  
        </Setter>  
      </Trigger>  
      <!-- Set properties when button has focus. -->   <Trigger Property="IsFocused" Value="true">     <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />     <Setter Property="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />   </Trigger>  
  
    </ControlTemplate.Triggers>  
    ```  
  
     <span data-ttu-id="dd9e8-195">F5 キーを押してアプリケーションを実行し、ボタンのいずれかをクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-195">Press F5 to run the application and click on one of the buttons.</span></span> <span data-ttu-id="dd9e8-196">フォーカスがあるために、クリックした後、ボタンが強調表示されたままことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-196">Notice that the button stays highlighted after you click it because it still has focus.</span></span> <span data-ttu-id="dd9e8-197">別のボタンをクリックした場合は、新しいボタンにフォーカスが最後の 1 つでは、それが失われます。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-197">If you click another button, the new button gains focus while the last one loses it.</span></span>  
  
4.  <span data-ttu-id="dd9e8-198">**アニメーションの追加**<xref:System.Windows.UIElement.MouseEnter> **と** <xref:System.Windows.UIElement.MouseLeave> **:**次にいくつかのアニメーションのトリガーに追加します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-198">**Add animations for**  <xref:System.Windows.UIElement.MouseEnter> **and** <xref:System.Windows.UIElement.MouseLeave> **:** Next we add some animations to the triggers.</span></span> <span data-ttu-id="dd9e8-199">任意の場所内の次のマークアップを追加、`ControlTemplate.Triggers`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-199">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block.</span></span>  
  
    ```  
    <!-- Animations that start when mouse enters and leaves button. -->  
    <EventTrigger RoutedEvent="Mouse.MouseEnter">  
      <EventTrigger.Actions>  
        <BeginStoryboard Name="mouseEnterBeginStoryboard">  
          <Storyboard>  
          <!-- This animation makes the glass rectangle shrink in the X direction. -->  
            <DoubleAnimation Storyboard.TargetName="glassCube"   
              Storyboard.TargetProperty=  
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleX)"  
              By="-0.1" Duration="0:0:0.5" />  
            <!-- This animation makes the glass rectangle shrink in the Y direction. -->  
            <DoubleAnimation  
            Storyboard.TargetName="glassCube"   
              Storyboard.TargetProperty=  
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleY)"   
              By="-0.1" Duration="0:0:0.5" />  
          </Storyboard>  
        </BeginStoryboard>  
      </EventTrigger.Actions>  
    </EventTrigger>  
    <EventTrigger RoutedEvent="Mouse.MouseLeave">  
      <EventTrigger.Actions>  
        <!-- Stopping the storyboard sets all animated properties back to default. -->  
        <StopStoryboard BeginStoryboardName="mouseEnterBeginStoryboard" />  
      </EventTrigger.Actions>  
    </EventTrigger>  
    ```  
  
     <span data-ttu-id="dd9e8-200">グラス四角形は、マウス ポインターが、ボタンの上に移動し、ポインターから離れたときに通常のサイズを返しますと縮小します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-200">The glass rectangle shrinks when the mouse pointer moves over the button and returns back to normal size when the pointer leaves.</span></span>  
  
     <span data-ttu-id="dd9e8-201">ポインターがボタンの上になるときにトリガーされる 2 つのアニメーションがある (<xref:System.Windows.UIElement.MouseEnter>イベントが発生)。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-201">There are two animations that are triggered when the pointer goes over the button (<xref:System.Windows.UIElement.MouseEnter> event is raised).</span></span> <span data-ttu-id="dd9e8-202">これらのアニメーションでは、X と Y 軸に沿ったグラス四角形を縮小します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-202">These animations shrink the glass rectangle along the X and Y axis.</span></span> <span data-ttu-id="dd9e8-203">プロパティを確認、<xref:System.Windows.Media.Animation.DoubleAnimation>要素 —<xref:System.Windows.Media.Animation.Timeline.Duration%2A>と<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>です。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-203">Notice the properties on the <xref:System.Windows.Media.Animation.DoubleAnimation> elements — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.</span></span> <span data-ttu-id="dd9e8-204"><xref:System.Windows.Media.Animation.Timeline.Duration%2A>アニメーションに秒、半分以上が発生することを指定し、<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>ガラスが 10% が圧縮を指定します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-204">The <xref:System.Windows.Media.Animation.Timeline.Duration%2A> specifies that the animation occurs over half a second, and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> specifies that the glass shrinks by 10%.</span></span>  
  
     <span data-ttu-id="dd9e8-205">2 番目のイベント トリガー (<xref:System.Windows.UIElement.MouseLeave>) が停止される最初の 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-205">The second event trigger (<xref:System.Windows.UIElement.MouseLeave>) simply stops the first one.</span></span> <span data-ttu-id="dd9e8-206">停止すると、<xref:System.Windows.Media.Animation.Storyboard>既定値にアニメーション化されたすべてのプロパティを返します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-206">When you stop a <xref:System.Windows.Media.Animation.Storyboard>, all the animated properties return to their default values.</span></span> <span data-ttu-id="dd9e8-207">そのため、ボタンからポインターを動かしたときに、ボタンに戻ります前に、の状態、ボタンにマウス ポインターを移動します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-207">Therefore, when the user moves the pointer off the button, the button goes back to the way it was before the mouse pointer moved over the button.</span></span> <span data-ttu-id="dd9e8-208">アニメーションの詳細については、次を参照してください。[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-208">For more information about animations, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span>  
  
5.  <span data-ttu-id="dd9e8-209">**ボタンがクリックされたときのアニメーションの追加:**最後に、ユーザーがボタンをクリックしたときにトリガーを追加します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-209">**Add an animation for when the button is clicked:** The final step is to add a trigger for when the user clicks the button.</span></span> <span data-ttu-id="dd9e8-210">任意の場所内の次のマークアップを追加、`ControlTemplate.Triggers`ブロック。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-210">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block:</span></span>  
  
    ```  
    <!-- Animation fires when button is clicked, causing glass to spin.  -->  
    <EventTrigger RoutedEvent="Button.Click">  
      <EventTrigger.Actions>  
        <BeginStoryboard>  
          <Storyboard>  
            <DoubleAnimation Storyboard.TargetName="glassCube"   
              Storyboard.TargetProperty=  
              "(Rectangle.RenderTransform).(TransformGroup.Children)[1].(RotateTransform.Angle)"   
              By="360" Duration="0:0:0.5" />  
          </Storyboard>  
        </BeginStoryboard>  
      </EventTrigger.Actions>  
    </EventTrigger>  
    ```  
  
     <span data-ttu-id="dd9e8-211">F5 キーを押して、アプリケーションを実行し、ボタンのいずれかをクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-211">Press F5 to run the application, and click one of the buttons.</span></span> <span data-ttu-id="dd9e8-212">ボタンをクリックしたときにグラス四角形が回転します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-212">When you click a button, the glass rectangle spins around.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="dd9e8-213">概要</span><span class="sxs-lookup"><span data-stu-id="dd9e8-213">Summary</span></span>  
 <span data-ttu-id="dd9e8-214">このチュートリアルでは、次の演習を実行しました。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-214">In this walkthrough, you performed the following exercises:</span></span>  
  
-   <span data-ttu-id="dd9e8-215">対象となる、<xref:System.Windows.Style>オブジェクト型 (<xref:System.Windows.Controls.Button>)。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-215">Targeted a <xref:System.Windows.Style> to an object type (<xref:System.Windows.Controls.Button>).</span></span>  
  
-   <span data-ttu-id="dd9e8-216">使用して、アプリケーション全体のボタンの基本プロパティを制御、<xref:System.Windows.Style>です。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-216">Controlled basic properties of the buttons in the entire application using the <xref:System.Windows.Style>.</span></span>  
  
-   <span data-ttu-id="dd9e8-217">グラデーションのプロパティ値を使用するようにリソースを作成、 <xref:System.Windows.Style> set アクセス操作子。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-217">Created resources like gradients to use for property values of the <xref:System.Windows.Style> setters.</span></span>  
  
-   <span data-ttu-id="dd9e8-218">アプリケーション全体のボタンの外観をカスタマイズするには、ボタンにテンプレートを適用します。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-218">Customized the look of buttons in the entire application by applying a template to the buttons.</span></span>  
  
-   <span data-ttu-id="dd9e8-219">ユーザーの操作への応答のボタンの動作のカスタマイズ (など<xref:System.Windows.UIElement.MouseEnter>、 <xref:System.Windows.UIElement.MouseLeave>、および<xref:System.Windows.Controls.Primitives.ButtonBase.Click>) アニメーション効果を含めることです。</span><span class="sxs-lookup"><span data-stu-id="dd9e8-219">Customized behavior for the buttons in response to user actions (such as <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, and <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) that included animation effects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd9e8-220">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd9e8-220">See Also</span></span>  
 [<span data-ttu-id="dd9e8-221">Microsoft Expression Blend を使用してボタンを作成する</span><span class="sxs-lookup"><span data-stu-id="dd9e8-221">Create a Button by Using Microsoft Expression Blend</span></span>](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md)  
 [<span data-ttu-id="dd9e8-222">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="dd9e8-222">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="dd9e8-223">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="dd9e8-223">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="dd9e8-224">純色およびグラデーションによる塗りつぶしの概要</span><span class="sxs-lookup"><span data-stu-id="dd9e8-224">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="dd9e8-225">ビットマップ効果の概要</span><span class="sxs-lookup"><span data-stu-id="dd9e8-225">Bitmap Effects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/bitmap-effects-overview.md)
