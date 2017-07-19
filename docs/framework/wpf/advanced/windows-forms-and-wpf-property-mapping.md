---
title: "Windows フォームと WPF プロパティの割り当て | Microsoft Docs"
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
  - "相互運用性 [WPF], Windows フォーム"
  - "プロパティの割り当て [WPF 相互運用性]"
  - "Windows フォーム [WPF], 相互運用性"
  - "Windows フォーム, WPF 相互運用"
  - "WindowsFormsHost 要素のプロパティの割り当て"
ms.assetid: 999d8298-9c04-467d-a453-86e41002057d
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# Windows フォームと WPF プロパティの割り当て
[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] テクノロジと [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] テクノロジは、類似する 2 つのプロパティ モデルを使用しますが、まったく同じというわけではありません。  *プロパティの割り当て*は、2 つのアーキテクチャ間の相互運用をサポートし、次の機能を提供します。  
  
-   ホスト環境での関連するプロパティの変更を、ホストされるコントロールまたは要素に簡単に割り当てられるようにします。  
  
-   最もよく使用されるプロパティの割り当てに対する既定の処理を提供します。  
  
-   既定のプロパティを簡単に削除、オーバーライド、または拡張できるようにします。  
  
-   ホストでのプロパティ値の変更が自動的に検出され、ホストされるコントロールまたは要素に変換されるようにします。  
  
> [!NOTE]
>  プロパティ変更イベントは、コントロールまたは要素のホスト階層を上方には伝達されません。  プロパティの値を変更する直接設定、スタイル、継承、データ バインディング、またはその他の機構のため、プロパティのローカル値が変更されない場合は、プロパティの変換は行われません。  
  
 プロパティの割り当てにアクセスするには、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素の <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> プロパティおよび <xref:System.Windows.Forms.Integration.ElementHost> コントロールの <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> プロパティを使用します。  
  
## WindowsFormsHost 要素を使用したプロパティの割り当て  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は、次の変換テーブルを使用して、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の既定のプロパティを [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]でそれに相当するものに変換します。  
  
|Windows Presentation Foundation ホスト|Windows フォーム|相互運用動作|  
|-----------------------------------------|------------------|------------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> \(<xref:System.Windows.Media.Brush?displayProperty=fullName>\)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> \(<xref:System.Drawing.Color?displayProperty=fullName>\)|<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は、ホストされるコントロールの <xref:System.Windows.Forms.Control.BackColor%2A> プロパティおよび <xref:System.Windows.Forms.Control.BackgroundImage%2A> プロパティを設定します。  割り当ては、次のルールを使用して行われます。<br /><br /> -   <xref:System.Windows.Controls.Control.Background%2A> が純色の場合は、変換されて、ホストされるコントロールの <xref:System.Windows.Forms.Control.BackColor%2A> プロパティを設定するために使用されます。  ホストされるコントロールは <xref:System.Windows.Forms.Control.BackColor%2A> プロパティの値を継承できるため、ホストされるコントロールでは <xref:System.Windows.Forms.Control.BackColor%2A> プロパティは設定されません。 **Note:**  ホストされるコントロールは透過性をサポートしません。  <xref:System.Windows.Forms.Control.BackColor%2A> に割り当てられる色は、アルファ値が 0xFF で、完全に不透明でなければなりません。 <br /><br /> -   <xref:System.Windows.Controls.Control.Background%2A> が純色でない場合、<xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールは <xref:System.Windows.Controls.Control.Background%2A> プロパティからビットマップを作成します。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールは、このビットマップをホストされるコントロールの <xref:System.Windows.Forms.Control.BackgroundImage%2A> プロパティに割り当てます。  これにより、透過性に似た効果が実現します。 **Note:**  この動作をオーバーライドしたり、<xref:System.Windows.Controls.Control.Background%2A> プロパティの割り当てを削除することができます。|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|既定の割り当てが再割り当てされていない場合、<xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールは、<xref:System.Windows.FrameworkElement.Cursor%2A> プロパティが設定されている先祖が見つかるまで、先祖の階層を処理します。  この値は、対応する最も近い [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] カーソルに変換されます。<br /><br /> <xref:System.Windows.FrameworkElement.ForceCursor%2A> プロパティの既定の割り当てが再割り当てされていない場合、処理は、<xref:System.Windows.FrameworkElement.ForceCursor%2A> が `true` に設定されている最初の先祖で停止します。|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> \(<xref:System.Windows.FlowDirection?displayProperty=fullName>\)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> \(<xref:System.Windows.Forms.RightToLeft?displayProperty=fullName>\)|<xref:System.Windows.FlowDirection> は <xref:System.Windows.Forms.RightToLeft> にマップされます。<br /><br /> <xref:System.Windows.FlowDirection> は <xref:System.Windows.Forms.RightToLeft> にマップされます。<br /><br /> <xref:System.Windows.Forms.RightToLeft> は割り当てられません。<br /><br /> <xref:System.Windows.FlowDirection?displayProperty=fullName> は <xref:System.Windows.Forms.RightToLeft?displayProperty=fullName> にマップされます。|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|ホストされているコントロールの <xref:System.Drawing.Font.Style%2A> の <xref:System.Drawing.Font?displayProperty=fullName>|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のプロパティ セットは、対応する <xref:System.Drawing.Font> に変換されます。  これらのプロパティのいずれかが変更された場合は、新しい <xref:System.Drawing.Font> が作成されます。  <xref:System.Windows.FontStyles.Normal%2A> の場合、<xref:System.Drawing.FontStyle> は無効です。  <xref:System.Windows.FontStyles.Italic%2A> または <xref:System.Windows.FontStyles.Oblique%2A> の場合、<xref:System.Drawing.FontStyle> は有効です。|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|ホストされているコントロールの <xref:System.Drawing.Font.Style%2A> の <xref:System.Drawing.Font?displayProperty=fullName>|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のプロパティ セットは、対応する <xref:System.Drawing.Font> に変換されます。  これらのプロパティのいずれかが変更された場合は、新しい <xref:System.Drawing.Font> が作成されます。  <xref:System.Windows.FontWeights.Black%2A>、<xref:System.Windows.FontWeights.Bold%2A>、<xref:System.Windows.FontWeights.DemiBold%2A>、<xref:System.Windows.FontWeights.ExtraBold%2A>、<xref:System.Windows.FontWeights.Heavy%2A>、<xref:System.Windows.FontWeights.Medium%2A>、<xref:System.Windows.FontWeights.SemiBold%2A>、または <xref:System.Windows.FontWeights.UltraBold%2A> の場合、<xref:System.Drawing.FontStyle> は有効です。  <xref:System.Windows.FontWeights.ExtraLight%2A>、<xref:System.Windows.FontWeights.Light%2A>、<xref:System.Windows.FontWeights.Normal%2A>、<xref:System.Windows.FontWeights.Regular%2A>、<xref:System.Windows.FontWeights.Thin%2A>、または <xref:System.Windows.FontWeights.UltraLight%2A> の場合、<xref:System.Drawing.FontStyle> は無効です。|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> \(<xref:System.Drawing.Font?displayProperty=fullName>\)|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のプロパティ セットは、対応する <xref:System.Drawing.Font> に変換されます。  これらのプロパティのいずれかが変更された場合は、新しい <xref:System.Drawing.Font> が作成されます。  ホストされる [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは、フォント サイズに基づいてサイズを変更します。<br /><br /> フォント サイズは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では 1\/96 インチで表され、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]では 1\/72 インチで表されます。  対応する変換は次のとおりです。<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]のフォント サイズ \= [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のフォント サイズ \* 72.0 \/ 96.0|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> \(<xref:System.Windows.Media.Brush?displayProperty=fullName>\)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> \(<xref:System.Drawing.Color?displayProperty=fullName>\)|<xref:System.Windows.Controls.Control.Foreground%2A> プロパティの割り当ては、次のルールを使用して行われます。<br /><br /> -   <xref:System.Windows.Controls.Control.Foreground%2A> が <xref:System.Windows.Media.SolidColorBrush> の場合、<xref:System.Windows.Forms.Control.ForeColor%2A> には <xref:System.Windows.Media.SolidColorBrush.Color%2A> を使用します。<br />-   <xref:System.Windows.Controls.Control.Foreground%2A> が <xref:System.Windows.Media.GradientBrush> の場合、<xref:System.Windows.Forms.Control.ForeColor%2A> には <xref:System.Windows.Media.GradientStop> の色と最低のオフセット値を使用します。<br />-   他の <xref:System.Windows.Media.Brush> 型の場合は、<xref:System.Windows.Forms.Control.ForeColor%2A> は変更されません。  これは、既定値が使用されることを意味します。|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A> が設定されていると、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素はホストされるコントロールの <xref:System.Windows.Forms.Control.Enabled%2A> プロパティを設定します。|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|ホストされる [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールの <xref:System.Windows.Forms.Control.Padding%2A> プロパティの 4 つの値はすべて、同じ <xref:System.Windows.Thickness> 値に設定されます。<br /><br /> -   <xref:System.Int32.MaxValue> より大きい値は、<xref:System.Int32.MaxValue> に設定されます。<br />-   <xref:System.Int32.MinValue> より小さい値は、<xref:System.Int32.MinValue> に設定されます。|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility> は、<xref:System.Windows.Forms.Control.Visible%2A> \= `true` に割り当てられます。  ホストされる [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは表示されます。  ホストされているコントロールに対して <xref:System.Windows.Forms.Control.Visible%2A> プロパティを明示的に `false` に設定することはお勧めしません。<br />-   <xref:System.Windows.Visibility> は、<xref:System.Windows.Forms.Control.Visible%2A> \= `true` または `false` に割り当てられます。  ホストされる [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは描画されず、領域は折りたたまれます。<br />-   <xref:System.Windows.Visibility> : ホストされる [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールはレイアウトのスペースを使用しますが、表示はされません。  この場合、<xref:System.Windows.Forms.Control.Visible%2A> プロパティは `true` に設定されます。  ホストされているコントロールに対して <xref:System.Windows.Forms.Control.Visible%2A> プロパティを明示的に `false` に設定することはお勧めしません。|  
  
 コンテナー要素の添付プロパティは、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素によって完全にサポートされます。  
  
 詳細については、「[チュートリアル : WindowsFormsHost 要素を使用したプロパティの割り当て](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-windowsformshost-element.md)」を参照してください。  
  
## 親プロパティの更新  
 ほとんどの親プロパティに対する変更は、ホストされる子コントロールに通知されます。  値が変更されても通知が行われないプロパティを次に示します。  
  
-   <xref:System.Windows.Controls.Control.Background%2A>  
  
-   <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
-   <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
-   <xref:System.Windows.UIElement.Visibility%2A>  
  
 たとえば、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素の <xref:System.Windows.Controls.Control.Background%2A> プロパティの値を変更しても、ホストされるコントロールの <xref:System.Windows.Forms.Control.BackColor%2A> プロパティは変更されません。  
  
## ElementHost コントロールを使用したプロパティの割り当て  
 次のプロパティは、組み込みの変更通知を提供します。  これらのプロパティを割り当てるときは、<xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> メソッドを呼び出さないでください。  
  
-   AutoSize  
  
-   BackColor  
  
-   BackgroundImage  
  
-   BackgroundImageLayout  
  
-   BindingContext  
  
-   CausesValidation  
  
-   ContextMenu  
  
-   ContextMenuStrip  
  
-   Cursor  
  
-   Dock  
  
-   Enabled  
  
-   フォント  
  
-   ForeColor  
  
-   場所  
  
-   Margin  
  
-   Padding  
  
-   Parent  
  
-   Region  
  
-   RightToLeft  
  
-   サイズ  
  
-   TabIndex  
  
-   TabStop  
  
-   テキスト  
  
-   Visible  
  
 <xref:System.Windows.Forms.Integration.ElementHost> コントロールは、次の変換テーブルを使用して、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]の既定のプロパティを [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でそれに相当するものに変換します。  
  
 詳細については、「[チュートリアル : ElementHost コントロールを使用したプロパティの割り当て](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-elementhost-control.md)」を参照してください。  
  
|Windows フォーム ホスト|Windows Presentation Foundation|相互運用動作|  
|----------------------|-------------------------------------|------------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> \(<xref:System.Drawing.Color?displayProperty=fullName>\)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> \(ホストされている要素の <xref:System.Windows.Media.Brush?displayProperty=fullName>\)|このプロパティを設定すると、<xref:System.Windows.Media.ImageBrush> での再描画が強制されます。  <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> プロパティが `false` \(既定値\) に設定されている場合、この <xref:System.Windows.Media.ImageBrush> は、<xref:System.Windows.Forms.Control.BackColor%2A>、<xref:System.Windows.Forms.Control.BackgroundImage%2A>、<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> プロパティやアタッチされている描画ハンドラーなど、<xref:System.Windows.Forms.Integration.ElementHost> コントロールの外観に基づいています。<br /><br /> <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> が `true` に設定されている場合、<xref:System.Windows.Media.ImageBrush> は、親の <xref:System.Windows.Forms.Control.BackColor%2A>、<xref:System.Windows.Forms.Control.BackgroundImage%2A>、<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> プロパティやアタッチされている描画ハンドラーなど、<xref:System.Windows.Forms.Integration.ElementHost> コントロールの親の外観に基づいています。|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> \(<xref:System.Drawing.Image?displayProperty=fullName>\)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> \(ホストされている要素の <xref:System.Windows.Media.Brush?displayProperty=fullName>\)|このプロパティを設定すると、<xref:System.Windows.Forms.Control.BackColor%2A> のマッピングに関する記述と同じ動作が発生します。|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> \(ホストされている要素の <xref:System.Windows.Media.Brush?displayProperty=fullName>\)|このプロパティを設定すると、<xref:System.Windows.Forms.Control.BackColor%2A> のマッピングに関する記述と同じ動作が発生します。|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> \(<xref:System.Windows.Forms.Cursor?displayProperty=fullName>\)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> \(<xref:System.Windows.Input.Cursor?displayProperty=fullName>\)|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]の標準カーソルは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の対応する標準カーソルに変換されます。  [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]が標準カーソルでない場合は、既定値が割り当てられます。|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A> が設定されていると、<xref:System.Windows.Forms.Integration.ElementHost> コントロールはホストされる要素の <xref:System.Windows.UIElement.IsEnabled%2A> プロパティを設定します。|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> \(<xref:System.Drawing.Font?displayProperty=fullName>\)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A> の値は、対応する [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] フォント プロパティのセットに変換されます。|  
|<xref:System.Drawing.Font.Bold%2A>|ホストされている要素の <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Drawing.Font.Bold%2A> が `true` の場合は、<xref:System.Windows.Controls.Control.FontWeight%2A> が <xref:System.Windows.FontWeights.Bold%2A> に設定されます。<br /><br /> <xref:System.Drawing.Font.Bold%2A> が `false` の場合は、<xref:System.Windows.Controls.Control.FontWeight%2A> が <xref:System.Windows.FontWeights.Normal%2A> に設定されます。|  
|<xref:System.Drawing.Font.Italic%2A>|ホストされている要素の <xref:System.Windows.Controls.Control.FontStyle%2A>|<xref:System.Drawing.Font.Italic%2A> が `true` の場合は、<xref:System.Windows.Controls.Control.FontStyle%2A> が <xref:System.Windows.FontStyles.Italic%2A> に設定されます。<br /><br /> <xref:System.Drawing.Font.Italic%2A> が `false` の場合は、<xref:System.Windows.Controls.Control.FontStyle%2A> が <xref:System.Windows.FontStyles.Normal%2A> に設定されます。|  
|<xref:System.Drawing.Font.Strikeout%2A>|ホストされている要素の <xref:System.Windows.TextDecorations>|<xref:System.Windows.Controls.TextBlock> コントロールをホストしている場合のみ適用されます。|  
|<xref:System.Drawing.Font.Underline%2A>|ホストされている要素の <xref:System.Windows.TextDecorations>|<xref:System.Windows.Controls.TextBlock> コントロールをホストしている場合のみ適用されます。|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> \(<xref:System.Windows.Forms.RightToLeft?displayProperty=fullName>\)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> \(<xref:System.Windows.FlowDirection>\)|<xref:System.Windows.Forms.RightToLeft> は <xref:System.Windows.FlowDirection> にマップされます。<br /><br /> <xref:System.Windows.Forms.RightToLeft> は <xref:System.Windows.FlowDirection> にマップされます。|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Integration.ElementHost> コントロールは、次のルールを使用して、ホストされる要素の <xref:System.Windows.UIElement.Visibility%2A> プロパティを設定します。<br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> \= `true` は <xref:System.Windows.Visibility> にマップされます。<br />-   <xref:System.Windows.Forms.Control.Visible%2A> \= `false` は <xref:System.Windows.Visibility> にマップされます。|  
  
## 参照  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [WPF と Win32 の相互運用性](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)   
 [WPF と Windows フォームの相互運用性](../../../../docs/framework/wpf/advanced/wpf-and-windows-forms-interoperation.md)   
 [チュートリアル : WindowsFormsHost 要素を使用したプロパティの割り当て](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-windowsformshost-element.md)   
 [チュートリアル : ElementHost コントロールを使用したプロパティの割り当て](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-elementhost-control.md)