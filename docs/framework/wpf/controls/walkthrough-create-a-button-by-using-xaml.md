---
title: "チュートリアル : XAML を使用したボタンの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ボタン"
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# チュートリアル : XAML を使用したボタンの作成
このチュートリアルでは、[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] アプリケーションで使用するアニメーション ボタンの作成方法について説明します。  このチュートリアルでは、カスタマイズされたボタン リソースを作成するのにスタイルとテンプレートを使用します。これにより、コードを再利用したり、ボタン ロジックをボタン宣言から分離したりできるようになります。  このチュートリアルはすべて [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] で記述されています。  
  
> [!IMPORTANT]
>  このチュートリアルでは、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を Microsoft [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] に入力するか、コピーと貼り付けを行うことでアプリケーションを作成する手順について説明します。  同じアプリケーションをデザイン ツール \(Microsoft Expression Blend\) を使用して作成する方法の詳細については、「[Microsoft Expression Blend を使用してボタンを作成する](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md)」を参照してください。  
  
 次の図は、完成したボタンの外観を示しています。  
  
 ![XAML を使用して作成されたカスタム ボタン](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.png "custom\_button\_AnimatedButton\_5")  
  
## 基本ボタンの作成  
 まず、新しいプロジェクトを作成し、ウィンドウにボタンをいくつか追加します。  
  
#### 新しい WPF プロジェクトを作成し、ウィンドウにボタンを追加するには  
  
1.  [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] を起動します。  
  
2.  **新しい WPF プロジェクトの作成 :** **\[ファイル\]** メニューの **\[新規\]** をポイントし、**\[プロジェクト\]** をクリックします。  **\[Windows アプリケーション\]** テンプレートを選択し、プロジェクトに「AnimatedButton」という名前を付けます。  これで、アプリケーションのスケルトンが作成されます。  
  
3.  **既定の基本ボタンの追加 :** このチュートリアルで必要となるファイルは、すべてテンプレートに用意されています。  ソリューション エクスプローラーで、Window1.xaml をダブルクリックして開きます。  Window1.xaml には、既定で <xref:System.Windows.Controls.Grid> 要素があります。  <xref:System.Windows.Controls.Grid> 要素を削除し、次の強調表示されたコードを Window1.xaml に入力するかコピーして貼り付けて、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ページにボタンをいくつか追加します。  
  
    ```  
    <Window x:Class="AnimatedButton.Window1"  
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
      Title="AnimatedButton" Height="300" Width="300"   
      Background="Black">  
  
      <!-- Buttons arranged vertically inside a StackPanel. -->  
      <StackPanel HorizontalAlignment="Left">  
        <Button>Button 1</Button>  
        <Button>Button 2</Button>  
        <Button>Button 3</Button>  
      </StackPanel>  
  
    </Window>  
    ```  
  
     F5 キーを押してアプリケーションを実行します。次の図のようなボタンのセットが表示されます。  
  
     ![3 つの基本的なボタン](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-1.png "custom\_button\_AnimatedButton\_1")  
  
     基本ボタンを作成したので、Window1.xaml ファイルに対する作業は終わりです。  これ以降は、ボタンのスタイルとテンプレートを定義する app.xaml ファイルを中心に説明します。  
  
## 基本プロパティの設定  
 次に、これらのボタンについて、外観とレイアウトをコントロールするためのプロパティをいくつか設定します。  その際、プロパティをボタン別に設定するのではなく、アプリケーション全体のボタン プロパティを定義するリソースを使用します。  アプリケーション リソースは Web ページ用の外部 [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)] と概念的には似ていますが、このチュートリアルを通じて説明されるように、リソースの方が [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)] よりはるかに強力です。  リソースの詳細については、「[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)」を参照してください。  
  
#### ボタンの基本プロパティを設定するためのスタイルを使用するには  
  
1.  **Application.Resources ブロックの定義 :** app.xaml を開き、次の強調表示されたマークアップが含まれていない場合は追加します。  
  
    ```  
    <Application x:Class="AnimatedButton.App"  
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
      StartupUri="Window1.xaml"  
      >  
      <Application.Resources>  
  
        <!-- Resources for the entire application can be   
             defined here. -->  
  
      </Application.Resources>  
    </Application>  
    ```  
  
     リソースのスコープは、リソースを定義する場所で決定されます。  app.xaml ファイルの `Application.Resoureses` で定義されたリソースは、アプリケーションのどこででも使用できます。  リソースのスコープの定義の詳細については、「[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)」を参照してください。  
  
2.  **スタイルの作成と、基本プロパティ値の定義 :** 次のマークアップを `Application.Resources` ブロックに追加します。  このマークアップは、アプリケーションに含まれるすべてのボタンに適用される <xref:System.Windows.Style> を作成します。このスタイルにより、ボタンの <xref:System.Windows.FrameworkElement.Width%2A> は 90 に設定され、<xref:System.Windows.FrameworkElement.Margin%2A> は 10 に設定されます。  
  
    ```  
    <Application.Resources>  
  
      <Style TargetType="Button">  
        <Setter Property="Width" Value="90" />  
        <Setter Property="Margin" Value="10" />  
      </Style>  
  
    </Application.Resources>  
    ```  
  
     <xref:System.Windows.Style.TargetType%2A> プロパティは、<xref:System.Windows.Controls.Button> 型のすべてのオブジェクトに適用されるスタイルを指定します。  各 <xref:System.Windows.Setter> は <xref:System.Windows.Style> に異なるプロパティ値を設定します。  したがって、この時点では、アプリケーションに含まれるすべてのボタンの幅は 90 で、余白は 10 です。  F5 キーを押してアプリケーションを実行すると、次のようなウィンドウが表示されます。  
  
     ![幅 90、余白 10 のボタン](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-2.png "custom\_button\_AnimatedButton\_2")  
  
     スタイルを使用すると、他にもさまざまなことができます。たとえば、対象オブジェクトを微調整する方法が各種用意されているほか、複雑なプロパティ値を指定したり、あるスタイルを他のスタイルの入力として使用したりすることもできます。  詳細については、「[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)」を参照してください。  
  
3.  **スタイルのプロパティ値のリソースへの設定 :** リソースを使用することで、一般的に定義されるオブジェクトや値を簡単に再利用できます。  複雑な値をリソースを使用して定義することは、コードをモジュール化するのにたいへん便利です。  次の強調表示されたマークアップを app.xaml に追加します。  
  
    ```  
    <Application.Resources>  
  
      <LinearGradientBrush x:Key="GrayBlueGradientBrush"   
        StartPoint="0,0" EndPoint="1,1">  
        <GradientStop Color="DarkGray" Offset="0" />  
        <GradientStop Color="#CCCCFF" Offset="0.5" />  
        <GradientStop Color="DarkGray" Offset="1" />  
      </LinearGradientBrush>  
  
      <Style TargetType="{x:Type Button}">  
        <Setter Property="Background"   
          Value="{StaticResource GrayBlueGradientBrush}" />  
        <Setter Property="Width" Value="80" />  
        <Setter Property="Margin" Value="10" />  
      </Style>  
  
    </Application.Resources>  
    ```  
  
     `Application.Resources` ブロックの直下に、"GrayBlueGradientBrush" というリソースが作成されています。  このリソースは、水平方向のグラデーションを定義します。  このリソースは、<xref:System.Windows.Controls.Control.Background%2A> プロパティのボタン スタイルの Setter の内部からなど、アプリケーションのどこからでもプロパティ値として使用できます。  これで、すべてのボタンがこのグラデーションの <xref:System.Windows.Controls.Control.Background%2A> プロパティを持つようになりました。  
  
     F5 キーを押してアプリケーションを実行します。  結果は次のようになります。  
  
     ![グラデーション背景を持つボタン](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-3.png "custom\_button\_AnimatedButton\_3")  
  
## ボタンの外観を定義するテンプレートの作成  
 ここでは、ボタンの外観 \(プレゼンテーション\) をカスタマイズするテンプレートを作成します。  ボタン プレゼンテーションは、四角形などのコンポーネントを含むいくつかのオブジェクトで構成され、ボタンに固有の外観を指定します。  
  
 これまで、アプリケーションにおけるボタンの外観のコントロールは、ボタンのプロパティを変更することに制限されていました。  ボタンの外観をより大きく変更するにはどうしたらよいでしょうか。  テンプレートを使用すると、オブジェクトのプレゼンテーションを強力にコントロールできます。  テンプレートはスタイル内で使用できるので、スタイルが適用されるすべてのオブジェクト \(このチュートリアルではボタン\) にテンプレートを適用できます。  
  
#### ボタンの外観を定義するテンプレートを使用するには  
  
1.  **テンプレートのセットアップ :** <xref:System.Windows.Controls.Button> などのコントロールには <xref:System.Windows.Controls.Control.Template%2A> プロパティがあるので、テンプレートのプロパティ値は、<xref:System.Windows.Style> で <xref:System.Windows.Setter> を使用して設定した他のプロパティと同じようにして定義できます。  次の強調表示されたマークアップをボタン スタイルに追加します。  
  
    ```  
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
  
2.  **ボタン プレゼンテーションの変更 :** この時点でテンプレートを定義する必要があります。  次の強調表示されたマークアップを追加します。  このマークアップは、角が丸い 2 つの <xref:System.Windows.Shapes.Rectangle> 要素を指定し、続いて <xref:System.Windows.Controls.DockPanel> を指定します。  <xref:System.Windows.Controls.DockPanel> はボタンの <xref:System.Windows.Controls.ContentPresenter> をホストするために使用されます。  <xref:System.Windows.Controls.ContentPresenter> にはボタンのコンテンツが表示されます。  このチュートリアルでは、コンテンツはテキスト \("Button 1"、"Button 2"、"Button 3"\) です。  テンプレート コンポーネント \(四角形と <xref:System.Windows.Controls.DockPanel>\) はすべて <xref:System.Windows.Controls.Grid> 内部にレイアウトされます。  
  
    ```  
    <Setter.Value>  
      <ControlTemplate TargetType="Button">  
        <Grid Width="{TemplateBinding Width}"   
         Height="{TemplateBinding Height}" ClipToBounds="True">  
  
          <!-- Outer Rectangle with rounded corners. -->  
          <Rectangle x:Name="outerRectangle"   
            HorizontalAlignment="Stretch"   
            VerticalAlignment="Stretch"   
            Stroke="{TemplateBinding Background}"   
            RadiusX="20" RadiusY="20" StrokeThickness="5"   
            Fill="Transparent" />  
  
          <!-- Inner Rectangle with rounded corners. -->  
          <Rectangle x:Name="innerRectangle"   
            HorizontalAlignment="Stretch"   
            VerticalAlignment="Stretch" Stroke="Transparent"   
            StrokeThickness="20"   
            Fill="{TemplateBinding Background}"   
            RadiusX="20" RadiusY="20"   />  
  
          <!-- Present Content (text) of the button. -->  
          <DockPanel Name="myContentPresenterDockPanel">  
            <ContentPresenter x:Name="myContentPresenter" Margin="20"   
              Content="{TemplateBinding  Content}"   
              TextBlock.Foreground="Black" />  
          </DockPanel>  
        </Grid>  
      </ControlTemplate>  
    </Setter.Value>  
    ```  
  
     F5 キーを押してアプリケーションを実行します。  結果は次のようになります。  
  
     ![](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-4.gif "custom\_button\_AnimatedButton\_4")  
  
3.  **テンプレートへのグラス効果の追加 :** 次に、グラスを追加します。  まず、グラス グラデーション効果を作成するリソースをいくつか作成します。  これらのグラデーション リソースを `Application.Resources` ブロック内のどこかに追加します。  
  
    ```  
    <Application.Resources>  
      <GradientStopCollection x:Key="MyGlassGradientStopsResource">  
        <GradientStop Color="WhiteSmoke" Offset="0.2" />  
        <GradientStop Color="Transparent" Offset="0.4" />  
        <GradientStop Color="WhiteSmoke" Offset="0.5" />  
        <GradientStop Color="Transparent" Offset="0.75" />  
        <GradientStop Color="WhiteSmoke" Offset="0.9" />  
        <GradientStop Color="Transparent" Offset="1" />  
      </GradientStopCollection>  
  
      <LinearGradientBrush x:Key="MyGlassBrushResource"   
       StartPoint="0,0" EndPoint="1,1" Opacity="0.75"   
       GradientStops="{StaticResource MyGlassGradientStopsResource}" />  
    <!-- Styles and other resources below here. -->  
    ```  
  
     これらのリソースは、ボタン テンプレートの <xref:System.Windows.Controls.Grid> に挿入する四角形の <xref:System.Windows.Shapes.Shape.Fill%2A> として使用されます。  次の強調表示されたマークアップをテンプレートに追加します。  
  
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
  
          <!-- These transforms have no effect as they are declared here.   
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
    </ControlTemplate>  
    </Setter.Value>  
    ```  
  
     "glassCube" の `x:Name` プロパティを持つ四角形の <xref:System.Windows.UIElement.Opacity%2A> は 0 なので、このサンプルを実行すると、グラス四角形は最前面にオーバーレイ表示されません。  これは、ユーザーがボタンを使用して対話操作を行う場合について、後でトリガーをテンプレートに追加するからです。  ただし、<xref:System.Windows.UIElement.Opacity%2A> 値を 1 に変更してアプリケーションを実行すると、ボタンの外観をすぐに確認できます。  次の図を参照してください。  次の手順に進む前に、<xref:System.Windows.UIElement.Opacity%2A> を 0 に戻してください。  
  
     ![XAML を使用して作成されたカスタム ボタン](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.png "custom\_button\_AnimatedButton\_5")  
  
## ボタンの対話機能の作成  
 ここでは、マウス ポインターをボタンに合わせてクリックするなどのユーザー アクションに対応して、プロパティ値を変更してアニメーションを実行するプロパティ トリガーおよびイベント トリガーを作成します。  
  
 対話機能 \(マウスオーバー、マウスリーブ、クリックなど\) を追加する簡単な方法は、テンプレートまたはスタイルの内部にトリガーを定義することです。  <xref:System.Windows.Trigger> を作成するには、ボタンの <xref:System.Windows.UIElement.IsMouseOver%2A> プロパティが `true` に等しい、といったプロパティ "条件" を作成します。  次に、トリガー条件が true になったときに実行される setter \(アクション\) を定義します。  
  
#### ボタンの対話機能を作成するには  
  
1.  **テンプレート トリガーの追加 :** 次の強調表示されたマークアップをテンプレートに追加します。  
  
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
  
        <ControlTemplate.Triggers>  
          <!-- Set action triggers for the buttons and define  
               what the button does in response to those triggers. -->  
        </ControlTemplate.Triggers>  
      </ControlTemplate>  
    </Setter.Value>  
    ```  
  
2.  **プロパティ トリガーの追加 :** 次の強調表示されたマークアップを `ControlTemplate.Triggers` ブロックに追加します。  
  
    ```  
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->  
      <Trigger Property="IsMouseOver" Value="True">  
  
        <!-- Below are three property settings that occur when the   
             condition is met (user mouses over button).  -->  
        <!-- Change the color of the outer rectangle when user   
             mouses over it. -->  
        <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"  
          Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />  
  
        <!-- Sets the glass opacity to 1, therefore, the   
             glass "appears" when user mouses over it. -->  
        <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />  
  
        <!-- Makes the text slightly blurry as though you   
             were looking at it through blurry glass. -->  
        <Setter Property="ContentPresenter.BitmapEffect"   
          TargetName="myContentPresenter">  
          <Setter.Value>  
            <BlurBitmapEffect Radius="1" />  
          </Setter.Value>  
        </Setter>  
      </Trigger>  
  
    <ControlTemplate.Triggers/>  
    ```  
  
     F5 キーを押してアプリケーションを実行し、マウス ポインターをボタンに合わせたときの効果を確認します。  
  
3.  **フォーカス トリガーの追加 :** 次に、ボタンにフォーカスがある場合 \(ユーザーがクリックした後など\) を処理する同様の setter を追加します。  
  
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
      <!-- Set properties when button has focus. -->  
      <Trigger Property="IsFocused" Value="true">  
        <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />  
        <Setter Property="Rectangle.Stroke" TargetName="outerRectangle"  
          Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />  
        <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />  
      </Trigger>  
  
    </ControlTemplate.Triggers>  
    ```  
  
     F5 キーを押してアプリケーションを実行し、いずれかのボタンをクリックします。  クリックされた後でもフォーカスがあるので、ボタンは強調表示されたままになります。  別のボタンをクリックすると、新しいボタンにフォーカスが移り、それまでのボタンはフォーカスを失います。  
  
4.  <xref:System.Windows.UIElement.MouseEnter>  **と**  <xref:System.Windows.UIElement.MouseLeave>  **へのアニメーションの追加**  **:** 次に、トリガーにアニメーションを追加します。  次のマークアップを `ControlTemplate.Triggers` ブロックの中に追加します。  
  
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
  
     グラス四角形は、マウス ポインターをボタンに合わせると小さくなり、ポインターが離れると標準サイズに戻ります。  
  
     ポインターをボタンに合わせたとき \(<xref:System.Windows.UIElement.MouseEnter> イベントが生成されたとき\) にトリガーされるアニメーションは 2 つあります。  これらのアニメーションは、グラス四角形をそれぞれ X 軸および Y 軸方向に縮小します。  <xref:System.Windows.Media.Animation.DoubleAnimation> 要素のプロパティは、<xref:System.Windows.Media.Animation.Timeline.Duration%2A> と <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> です。  <xref:System.Windows.Media.Animation.Timeline.Duration%2A> はアニメーションが 0.5 秒間発生するように指定し、<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> はグラスが 10% 縮小されるように指定します。  
  
     2 番目のイベント トリガー \(<xref:System.Windows.UIElement.MouseLeave>\) は、単純に最初のイベントを停止します。  <xref:System.Windows.Media.Animation.Storyboard> を停止すると、アニメーション化されたすべてのプロパティが既定値に戻ります。  したがって、ユーザーがポインターをボタンから離すと、ボタンはマウス ポインターをボタンに合わせる前の状態に戻ります。  アニメーションの詳細については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。  
  
5.  **ボタンがクリックされたときのアニメーションの追加 :** 最後の手順は、ユーザーがボタンをクリックしたときのトリガーの追加です。  次のマークアップを `ControlTemplate.Triggers` ブロックの中に追加します。  
  
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
  
     F5 キーを押してアプリケーションを実行し、いずれかのボタンをクリックします。  ボタンをクリックすると、グラス四角形が回転します。  
  
## 概要  
 このチュートリアルでは、次の演習を行いました。  
  
-   <xref:System.Windows.Style> をオブジェクト型 \(<xref:System.Windows.Controls.Button>\) に適用しました。  
  
-   アプリケーション全体のボタンの基本プロパティを <xref:System.Windows.Style> を使用してコントロールしました。  
  
-   <xref:System.Windows.Style> setter のプロパティ値で使用するグラデーションなどのリソースを作成しました。  
  
-   テンプレートをボタンに適用することで、アプリケーション全体のボタンの外観をカスタマイズしました。  
  
-   アニメーション効果を含むユーザー アクション \(<xref:System.Windows.UIElement.MouseEnter>、<xref:System.Windows.UIElement.MouseLeave>、<xref:System.Windows.Controls.Primitives.ButtonBase.Click> など\) に対応するボタンの動作をカスタマイズしました。  
  
## 参照  
 [Microsoft Expression Blend を使用してボタンを作成する](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md)   
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)   
 [ビットマップ効果の概要](../../../../docs/framework/wpf/graphics-multimedia/bitmap-effects-overview.md)