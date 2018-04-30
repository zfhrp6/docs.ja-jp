---
title: 'チュートリアル : XAML を使用したボタンの作成'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a05e0af94cc84db117c7b8caf389d084cd4c3fd5
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a>チュートリアル : XAML を使用したボタンの作成
このチュートリアルでは、Windows Presentation Foundation (WPF) アプリケーションで使用するためのアニメーションのボタンを作成する方法について説明します。 このチュートリアルでは、スタイルとテンプレートを使用して、コードの再利用やボタン宣言からボタン ロジックを分離するカスタマイズされたボタンのリソースを作成します。 このチュートリアルが完全に書き込まれる[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]です。  
  
> [!IMPORTANT]
>  このチュートリアルでは入力またはコピーして貼り付けることによって、アプリケーションを作成する手順を説明します。[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]に Microsoft Visual Studio です。 デザイン ツール (Microsoft Expression Blend) を使用して、同じアプリケーションを作成する方法を学習したい場合[Microsoft Expression Blend を使用してボタンを作成して](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md)です。  
  
 次の図は、完成したボタンを示しています。  
  
 ![XAML を使用して作成されたカスタム ボタン](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-basic-buttons"></a>基本的なボタンを作成します。  
 新しいプロジェクトを作成し、ウィンドウにいくつかのボタンを追加することから始めましょう。  
  
#### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a>新しい WPF プロジェクトを作成し、ボタン、ウィンドウを追加するには  
  
1.  Visual Studio を起動します。  
  
2.  **新しい WPF プロジェクトの作成:** 上、**ファイル** メニューのをポイント**新規**、順にクリック**プロジェクト**です。 検索、 **Windows アプリケーション (WPF)** テンプレートとプロジェクト"AnimatedButton"の名前。 これにより、アプリケーションのスケルトンが作成されます。  
  
3.  **基本的な既定のボタンの追加:** このチュートリアルに必要なすべてのファイルは、テンプレートによって提供されます。 ダブルクリックして、ソリューション エクスプ ローラーで、Window1.xaml ファイルを開きます。 既定では、 <xref:System.Windows.Controls.Grid> Window1.xaml 内の要素。 削除、<xref:System.Windows.Controls.Grid>要素に、いくつかのボタンを追加して、 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 」と入力またはコピーして貼り付けることによって window1.xaml の名前に次の強調表示されているコード ページ。  
  
    ```xaml  
    <Window x:Class="AnimatedButton.Window1"  
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
      Title="AnimatedButton" Height="300" Width="300"   
      Background="Black">   <!-- Buttons arranged vertically inside a StackPanel. -->   <StackPanel HorizontalAlignment="Left">     <Button>Button 1</Button>     <Button>Button 2</Button>     <Button>Button 3</Button>   </StackPanel>  
  
    </Window>  
    ```  
  
     F5 キーを押してアプリケーションを実行します。次の図のようなボタンのセットが表示されます。  
  
     ![次の 3 つの基本的なボタン](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")  
  
     基本的なボタンを作成するには、Window1.xaml ファイルで作業が終了します。 このチュートリアルの残りの部分は、スタイルとボタンのテンプレートを定義する、app.xaml ファイルについて説明します。  
  
## <a name="set-basic-properties"></a>基本的なプロパティを設定します。  
 次に、これらのボタン、ボタンの外観とレイアウトを制御するいくつかのプロパティを設定してみましょう。 ボタンのプロパティを個別に設定するのではなく、アプリケーション全体のボタンのプロパティを定義するのにリソースを使用します。 アプリケーション リソース、外部に概念的に似ています[!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)]Web ページです。 ただし、リソースがよりもはるかに強力な[!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)]ように、このチュートリアルの最後で表示されます。 リソースの詳細については、次を参照してください。 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)です。  
  
#### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a>プロパティを設定する基本的なボタンのスタイルを使用するには  
  
1.  **Application.Resources ブロックを定義します。** app.xaml を開き、がない場合は、次の強調表示されているマークアップを追加します。  
  
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
  
     リソースのスコープは、定義したリソースによって決まります。 内のリソースを定義する`Application.Resources`app.xaml では、ファイルは、アプリケーションで任意の場所から使用するリソースをことができます。 リソースのスコープの定義の詳細については、次を参照してください。 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)です。  
  
2.  **スタイルを作成し、それに基本的なプロパティ値を定義します。**に次のマークアップを追加、`Application.Resources`ブロックします。 このマークアップを作成、<xref:System.Windows.Style>設定、アプリケーションのすべてのボタンに適用される、<xref:System.Windows.FrameworkElement.Width%2A>を 90 にボタンのおよび<xref:System.Windows.FrameworkElement.Margin%2A>10。  
  
    ```xaml  
    <Application.Resources>  
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>  
    </Application.Resources>  
    ```  
  
     <xref:System.Windows.Style.TargetType%2A>プロパティでは、型のすべてのオブジェクトへのスタイルが適用されるように指定<xref:System.Windows.Controls.Button>です。 各<xref:System.Windows.Setter>の別のプロパティ値を設定、<xref:System.Windows.Style>です。 そのため、この時点でアプリケーションのすべてのボタンが幅 90、余白は 10 です。  アプリケーションを実行する場合は F5 キーを押した場合、次のウィンドウを参照してください。  
  
     ![幅 90、余白 10 の持つボタン](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")  
  
     たくさんありますのさまざまなオブジェクトが対象となるを微調整する方法を含む、複合型プロパティ値を指定する、およびスタイルを使用する入力として他のスタイルのスタイルを使って実行できます。 詳しくは、「 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)」をご覧ください。  
  
3.  **リソースにスタイル プロパティの値を設定:** リソースが簡単に一般的に定義されるオブジェクトとの値を再利用を有効にします。 コードにモジュール化するためのリソースを使用して複雑な値を定義すると特に便利です。 App.xaml に次の強調表示されているマークアップを追加します。  
  
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
  
     直下にある、`Application.Resources`ブロック"GrayBlueGradientBrush"という名前のリソースを作成します。 このリソースは、水平方向のグラデーションを定義します。 このリソースをどこからでもプロパティの値として使用できますのボタンのスタイル セッターの内側など、アプリケーションで、<xref:System.Windows.Controls.Control.Background%2A>プロパティです。 ここで、すべてのボタンが、<xref:System.Windows.Controls.Control.Background%2A>このグラデーションのプロパティの値。  
  
     F5 キーを押してアプリケーションを実行します。 次のようになります。  
  
     ![グラデーション背景を持つボタン](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")  
  
## <a name="create-a-template-that-defines-the-look-of-the-button"></a>ボタンの外観を定義するテンプレートを作成します。  
 このセクションでは、ボタンの外観 (presentation) をカスタマイズするテンプレートを作成します。 ボタンのプレゼンテーションで構成された四角形とその他のコンポーネントを含む複数のオブジェクト、ボタンの外観を一意にします。  
  
 これまでに、アプリケーションでのボタンの外観の制御は、ボタンのプロパティを変更するのに制限されていましたがします。 ボタンの外観をより大きく変更する場合ですか。 テンプレートには、オブジェクトのプレゼンテーションに強力な制御が有効にします。 スタイル内では、テンプレートを使用できますが、ために、スタイルに適用されます (このチュートリアルでは、ボタン) のすべてのオブジェクトにテンプレートを適用することができます。  
  
#### <a name="to-use-the-template-to-define-the-look-of-the-button"></a>ボタンの外観を定義するテンプレートを使用するには  
  
1.  **テンプレートのセットアップ:** コントロールなどのため<xref:System.Windows.Controls.Button>が、<xref:System.Windows.Controls.Control.Template%2A>プロパティで設定した他のプロパティ値と同じようにテンプレートのプロパティ値を定義することができます、<xref:System.Windows.Style>を使用して、<xref:System.Windows.Setter>です。 次の強調表示されているマークアップをボタンのスタイルに追加します。  
  
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
  
2.  **ボタンのプレゼンテーションを alter:** この時点では、テンプレートを定義する必要があります。 次の強調表示されているマークアップを追加します。 このマークアップでは、2 つを指定します<xref:System.Windows.Shapes.Rectangle>角の丸いを持つ要素が続く、<xref:System.Windows.Controls.DockPanel>です。 <xref:System.Windows.Controls.DockPanel>が使用されるホストに、<xref:System.Windows.Controls.ContentPresenter>ボタンのです。 A<xref:System.Windows.Controls.ContentPresenter>ボタンのコンテンツを表示します。 このチュートリアルでは、コンテンツは、テキスト (「ボタン 1」、「ボタン 2」、「ボタン 3」) です。 すべてのテンプレートのコンポーネント (四角形と<xref:System.Windows.Controls.DockPanel>) 内のレイアウト、<xref:System.Windows.Controls.Grid>です。  
  
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
  
     F5 キーを押してアプリケーションを実行します。 次のようになります。  
  
     ![](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")  
  
3.  **グラスをテンプレートに追加:** 次ガラスに追加します。 まず、ガラスのグラデーション効果を作成するリソースを作成します。 リソースを追加するこれらグラデーション任意の場所内で、`Application.Resources`ブロック。  
  
    ```xaml  
    <Application.Resources>  
      <GradientStopCollection x:Key="MyGlassGradientStopsResource">     <GradientStop Color="WhiteSmoke" Offset="0.2" />     <GradientStop Color="Transparent" Offset="0.4" />     <GradientStop Color="WhiteSmoke" Offset="0.5" />     <GradientStop Color="Transparent" Offset="0.75" />     <GradientStop Color="WhiteSmoke" Offset="0.9" />     <GradientStop Color="Transparent" Offset="1" />   </GradientStopCollection>   <LinearGradientBrush x:Key="MyGlassBrushResource"     StartPoint="0,0" EndPoint="1,1" Opacity="0.75"     GradientStops="{StaticResource MyGlassGradientStopsResource}" />  
    <!-- Styles and other resources below here. -->  
    ```  
  
     これらのリソースとして使用、<xref:System.Windows.Shapes.Shape.Fill%2A>に挿入する四角形の<xref:System.Windows.Controls.Grid>button テンプレートのです。 次の強調表示されているマークアップをテンプレートに追加します。  
  
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
  
     注意して、<xref:System.Windows.UIElement.Opacity%2A>を含む四角形の`x:Name`"glassCube"のプロパティが 0 で、サンプルを実行するときに、上部にオーバーレイ グラス四角形は表示されないようにします。 これはおは後でトリガーを追加のテンプレートのボタンで、ユーザーが操作するときにあるためです。 ただし、ご覧のボタンの外観と同様に今すぐ変更することによって、 <xref:System.Windows.UIElement.Opacity%2A> 1 およびアプリケーションを実行する値。 次の図を参照してください。 次の手順に前に、変更、 <xref:System.Windows.UIElement.Opacity%2A> 0 に戻します。  
  
     ![XAML を使用して作成されたカスタム ボタン](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-button-interactivity"></a>ボタンの対話機能を作成します。  
 このセクションでは、プロパティ トリガーと、プロパティ値を変更し、ボタンにマウス ポインターを移動しをクリックするとなどのユーザー アクションへの応答でアニメーションを実行するイベントのトリガーを作成します。  
  
 対話機能 (マウス オーバー、マウスのままにしてをクリックし、およびなど) を追加する簡単な方法では、テンプレートまたはスタイル内でトリガーを定義します。 作成する、<xref:System.Windows.Trigger>など「条件」プロパティを定義する: ボタン<xref:System.Windows.UIElement.IsMouseOver%2A>プロパティの値と等しい`true`です。 トリガー条件が true のときに行われる setter (アクション) を定義します。  
  
#### <a name="to-create-button-interactivity"></a>ボタンの対話機能を作成するには  
  
1.  **テンプレートのトリガーを追加:** マークアップを強調表示されているテンプレートに追加します。  
  
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
  
2.  **プロパティ トリガーを追加:** 強調表示されているマークアップを追加、`ControlTemplate.Triggers`ブロック。  
  
    ```  
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>  
  
    <ControlTemplate.Triggers/>  
    ```  
  
     F5 キーを押してアプリケーションを実行し、ボタンの上にマウス ポインターを実行するように影響を確認します。  
  
3.  **フォーカス トリガーを追加する:** 次に、ボタンに (たとえば、ユーザーがクリックした後) のフォーカスがあるときに、ケースを処理するいくつかのような set アクセス操作子を追加します。  
  
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
  
     F5 キーを押してアプリケーションを実行し、ボタンのいずれかをクリックします。 フォーカスがあるために、クリックした後、ボタンが強調表示されたままことに注意してください。 別のボタンをクリックした場合は、新しいボタンにフォーカスが最後の 1 つでは、それが失われます。  
  
4.  **アニメーションの追加**<xref:System.Windows.UIElement.MouseEnter> **と** <xref:System.Windows.UIElement.MouseLeave> **:** 次にいくつかのアニメーションのトリガーに追加します。   任意の場所内の次のマークアップを追加、`ControlTemplate.Triggers`ブロックします。  
  
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
  
     グラス四角形は、マウス ポインターが、ボタンの上に移動し、ポインターから離れたときに通常のサイズを返しますと縮小します。  
  
     ポインターがボタンの上になるときにトリガーされる 2 つのアニメーションがある (<xref:System.Windows.UIElement.MouseEnter>イベントが発生)。 これらのアニメーションでは、X と Y 軸に沿ったグラス四角形を縮小します。 プロパティを確認、<xref:System.Windows.Media.Animation.DoubleAnimation>要素 —<xref:System.Windows.Media.Animation.Timeline.Duration%2A>と<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>です。 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>アニメーションに秒、半分以上が発生することを指定し、<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>ガラスが 10% が圧縮を指定します。  
  
     2 番目のイベント トリガー (<xref:System.Windows.UIElement.MouseLeave>) が停止される最初の 1 つだけです。 停止すると、<xref:System.Windows.Media.Animation.Storyboard>既定値にアニメーション化されたすべてのプロパティを返します。 そのため、ボタンからポインターを動かしたときに、ボタンに戻ります前に、の状態、ボタンにマウス ポインターを移動します。 アニメーションの詳細については、次を参照してください。[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)です。  
  
5.  **ボタンがクリックされたときのアニメーションの追加:** 最後に、ユーザーがボタンをクリックしたときにトリガーを追加します。 任意の場所内の次のマークアップを追加、`ControlTemplate.Triggers`ブロック。  
  
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
  
     F5 キーを押して、アプリケーションを実行し、ボタンのいずれかをクリックします。 ボタンをクリックしたときにグラス四角形が回転します。  
  
## <a name="summary"></a>まとめ  
 このチュートリアルでは、次の演習を実行しました。  
  
-   対象となる、<xref:System.Windows.Style>オブジェクト型 (<xref:System.Windows.Controls.Button>)。  
  
-   使用して、アプリケーション全体のボタンの基本プロパティを制御、<xref:System.Windows.Style>です。  
  
-   グラデーションのプロパティ値を使用するようにリソースを作成、 <xref:System.Windows.Style> set アクセス操作子。  
  
-   アプリケーション全体のボタンの外観をカスタマイズするには、ボタンにテンプレートを適用します。  
  
-   ユーザーの操作への応答のボタンの動作のカスタマイズ (など<xref:System.Windows.UIElement.MouseEnter>、 <xref:System.Windows.UIElement.MouseLeave>、および<xref:System.Windows.Controls.Primitives.ButtonBase.Click>) アニメーション効果を含めることです。  
  
## <a name="see-also"></a>関連項目  
 [Microsoft Expression Blend を使用してボタンを作成する](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md)  
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [ビットマップ効果の概要](../../../../docs/framework/wpf/graphics-multimedia/bitmap-effects-overview.md)
