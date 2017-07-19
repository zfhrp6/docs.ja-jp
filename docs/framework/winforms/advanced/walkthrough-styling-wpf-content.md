---
title: "チュートリアル: WPF コンテンツへのスタイルの適用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "相互運用性 [WDF]"
  - "スタイル, WPF コンテンツ"
  - "WPF デザイナー, スタイル設定 (WPF コンテンツを)"
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# チュートリアル: WPF コンテンツへのスタイルの適用
このチュートリアルでは、Windows フォームでホストされている Windows Presentation Foundation \(WPF\) コントロールにスタイルを適用する方法について説明します。  
  
 このチュートリアルでは次のタスクを行います。  
  
-   プロジェクトを作成します。  
  
-   WPF コントロール型を作成します。  
  
-   WPF コントロールにスタイルを適用します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]。  
  
## プロジェクトの作成  
 まず、Windows フォーム プロジェクトを作成します。  
  
> [!NOTE]
>  WPF コンテンツをホストする場合は、C\# プロジェクトと Visual Basic プロジェクトのみがサポートされます。  
  
#### プロジェクトを作成するには  
  
-   `StylingWpfContent` という名前の新しい Windows フォーム アプリケーション プロジェクトを Visual Basic または Visual C\# で作成します。  
  
## WPF コントロール型の作成  
 プロジェクトに追加した WPF コントロール型は、<xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストできます。  
  
#### WPF コントロール型を作成するには  
  
1.  新しい WPF <xref:System.Windows.Controls.UserControl> プロジェクトをソリューションに追加します。  名前はこのコントロール型の既定である `UserControl1.xaml` を使用します。  詳細については、「[チュートリアル: デザイン時の Windows フォームでの新しい WPF コンテンツの作成](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)」を参照してください。  
  
2.  デザイン ビューで `UserControl1` が選択されていることを確認します。  詳細については、「[方法 : デザイン画面上で要素を選択して移動する](http://msdn.microsoft.com/ja-jp/54cb70b6-b35b-46e4-a0cc-65189399c474)」を参照してください。  
  
3.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.FrameworkElement.Width%2A> プロパティおよび <xref:System.Windows.FrameworkElement.Height%2A> プロパティの値を `200` に設定します。  
  
4.  <xref:System.Windows.Controls.Button?displayProperty=fullName> コントロールを <xref:System.Windows.Controls.UserControl> に追加し、<xref:System.Windows.Controls.ContentControl.Content%2A> プロパティの値を「Cancel」に設定します。  
  
5.  2 つ目の<xref:System.Windows.Controls.Button?displayProperty=fullName> コントロールを <xref:System.Windows.Controls.UserControl> に追加し、<xref:System.Windows.Controls.ContentControl.Content%2A> プロパティの値を「OK」に設定します。  
  
6.  プロジェクトをビルドします。  
  
## WPF コントロールへのスタイルの適用  
 さまざまなスタイルを WPF コントロールに適用することで、外観や動作を変えることができます。  
  
#### WPF コントロールにスタイルを適用するには  
  
1.  Windows フォーム デザイナーで `Form1` を開きます。  
  
2.  **\[ツールボックス\]** で `UserControl1` をダブルクリックして、フォーム上に `UserControl1` のインスタンスを作成します。  
  
     `UserControl1` のインスタンスは、`elementHost1` という名前の新しい <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。  
  
3.  `elementHost1` のスマート タグ パネルで、ドロップダウン リストから \[**ホストするコンテンツの編集**\] をクリックします。  
  
     `UserControl1` が [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] で開きます。  
  
4.  XAML ビューで、次の XAML を `<UserControl>` の開始タグの後に挿入します。  
  
     この XAML は、明暗のあるグラデーション境界を持つグラデーションを作成します。  このコントロールをクリックすると、グラデーションが変わり、ボタンを押したような外観が生成されます。  詳細については、「[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)」を参照してください。  
  
```xaml  
<UserControl.Resources>  
    <LinearGradientBrush x:Key="NormalBrush" EndPoint="0,1" StartPoint="0,0">  
        <GradientStop Color="#FFF" Offset="0.0"/>  
        <GradientStop Color="#CCC" Offset="1.0"/>  
    </LinearGradientBrush>  
    <LinearGradientBrush x:Key="PressedBrush" EndPoint="0,1" StartPoint="0,0">  
        <GradientStop Color="#BBB" Offset="0.0"/>  
        <GradientStop Color="#EEE" Offset="0.1"/>  
        <GradientStop Color="#EEE" Offset="0.9"/>  
        <GradientStop Color="#FFF" Offset="1.0"/>  
    </LinearGradientBrush>  
    <LinearGradientBrush x:Key="NormalBorderBrush" EndPoint="0,1" StartPoint="0,0">  
        <GradientStop Color="#CCC" Offset="0.0"/>  
        <GradientStop Color="#444" Offset="1.0"/>  
    </LinearGradientBrush>  
    <LinearGradientBrush x:Key="BorderBrush" EndPoint="0,1" StartPoint="0,0">  
        <GradientStop Color="#CCC" Offset="0.0"/>  
        <GradientStop Color="#444" Offset="1.0"/>  
    </LinearGradientBrush>  
    <LinearGradientBrush x:Key="PressedBorderBrush" EndPoint="0,1" StartPoint="0,0">  
        <GradientStop Color="#444" Offset="0.0"/>  
        <GradientStop Color="#888" Offset="1.0"/>  
    </LinearGradientBrush>  
  
    <Style x:Key="SimpleButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">  
        <Setter Property="Background" Value="{StaticResource NormalBrush}"/>  
        <Setter Property="BorderBrush" Value="{StaticResource NormalBorderBrush}"/>  
        <Setter Property="Template">  
            <Setter.Value>  
                <ControlTemplate TargetType="{x:Type Button}">  
                    <Grid x:Name="Grid">  
                        <Border x:Name="Border" Background="{TemplateBinding Background}" BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}" Padding="{TemplateBinding Padding}"/>  
                        <ContentPresenter HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="{TemplateBinding Padding}" VerticalAlignment="{TemplateBinding VerticalContentAlignment}" RecognizesAccessKey="True"/>  
                    </Grid>  
                    <ControlTemplate.Triggers>  
                        <Trigger Property="IsPressed" Value="true">  
                            <Setter Property="Background" Value="{StaticResource PressedBrush}" TargetName="Border"/>  
                            <Setter Property="BorderBrush" Value="{StaticResource PressedBorderBrush}" TargetName="Border"/>  
                        </Trigger>  
                    </ControlTemplate.Triggers>  
                </ControlTemplate>  
            </Setter.Value>  
        </Setter>  
    </Style>  
</UserControl.Resources>  
```  
  
1.  \[Cancel\] ボタンの `<Button>` タグに次の XAML を挿入することで、前の手順で定義した `SimpleButton` スタイルを \[Cancel\] ボタンに適用します。  
  
    ```  
    Style="{StaticResource SimpleButton}  
    ```  
  
     ボタン宣言は次の XAML のようになります。  
  
```xaml  
<Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"  
                Style="{StaticResource SimpleButton}">Cancel</Button>  
```  
  
1.  プロジェクトをビルドします。  
  
2.  Windows フォーム デザイナーで `Form1` を開きます。  
  
3.  新しいスタイルが Button コントロールに適用されます。  
  
4.  **\[デバッグ\]** メニューから **\[デバッグ開始\]** を選択して、アプリケーションを実行します。  
  
5.  \[OK\] ボタンと \[Cancel\] ボタンをクリックして、違いを確認します。  
  
## 参照  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [移行と相互運用性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)   
 [WPF コントロールの使用](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)   
 [WPF デザイナー](http://msdn.microsoft.com/ja-jp/c6c65214-8411-4e16-b254-163ed4099c26)   
 [XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)