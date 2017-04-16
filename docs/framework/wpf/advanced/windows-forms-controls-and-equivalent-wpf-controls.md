---
title: "Windows フォーム コントロールおよび同等の WPF コントロール | Microsoft Docs"
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
  - "Windows フォーム [WPF], 相互運用性"
  - "Windows フォーム, WPF 相互運用"
ms.assetid: 8a157e6b-8054-46db-a5cf-a78966acc7a1
caps.latest.revision: 27
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 27
---
# Windows フォーム コントロールおよび同等の WPF コントロール
多くの場合、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールには同等の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールがありますが、中には [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールと同等のコントロールが [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] にない場合もあります。  ここでは、2 つのテクノロジによって提供されるコントロール型を比較します。  
  
 相互運用を利用すると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ベースのアプリケーションに同等のコントロールがない [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールを常にホストできます。  
  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールおよびコンポーネントと同等の機能を持つ [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールを次の表に示します。  
  
|Windows フォーム コントロール|WPF の同等コントロール|解説|  
|-------------------------|-------------------|--------|  
|<xref:System.Windows.Forms.BindingNavigator>|同等のコントロールはありません。||  
|<xref:System.Windows.Forms.BindingSource>|<xref:System.Windows.Data.CollectionViewSource>||  
|<xref:System.Windows.Forms.Button>|<xref:System.Windows.Controls.Button>||  
|<xref:System.Windows.Forms.CheckBox>|<xref:System.Windows.Controls.CheckBox>||  
|<xref:System.Windows.Forms.CheckedListBox>|コンポジションを使用した <xref:System.Windows.Controls.ListBox>。||  
|<xref:System.Windows.Forms.ColorDialog>|同等のコントロールはありません。||  
|<xref:System.Windows.Forms.ComboBox>|<xref:System.Windows.Controls.ComboBox>|<xref:System.Windows.Controls.ComboBox> は、オート コンプリートをサポートしていません。|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<xref:System.Windows.Controls.ContextMenu>||  
|<xref:System.Windows.Forms.DataGridView>|<xref:System.Windows.Controls.DataGrid>||  
|<xref:System.Windows.Forms.DateTimePicker>|<xref:System.Windows.Controls.DatePicker>||  
|<xref:System.Windows.Forms.DomainUpDown>|<xref:System.Windows.Controls.TextBox> と 2 つの <xref:System.Windows.Controls.Primitives.RepeatButton> コントロール。||  
|<xref:System.Windows.Forms.ErrorProvider>|同等のコントロールはありません。||  
|<xref:System.Windows.Forms.FlowLayoutPanel>|<xref:System.Windows.Controls.WrapPanel> または <xref:System.Windows.Controls.StackPanel>||  
|<xref:System.Windows.Forms.FolderBrowserDialog>|同等のコントロールはありません。||  
|<xref:System.Windows.Forms.FontDialog>|同等のコントロールはありません。||  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Window>|<xref:System.Windows.Window> は子ウィンドウをサポートしていません。|  
|<xref:System.Windows.Forms.GroupBox>|<xref:System.Windows.Controls.GroupBox>||  
|<xref:System.Windows.Forms.HelpProvider>|同等のコントロールはありません。|F1 ヘルプはありません。  "ポップ ヒント" ヘルプはツールヒントに置き換えられます。|  
|<xref:System.Windows.Forms.HScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|スクロールは、コンテナー コントロールに組み込まれます。|  
|<xref:System.Windows.Forms.ImageList>|同等のコントロールはありません。||  
|<xref:System.Windows.Forms.Label>|<xref:System.Windows.Controls.Label>||  
|<xref:System.Windows.Forms.LinkLabel>|同等のコントロールはありません。|<xref:System.Windows.Documents.Hyperlink> クラスを使用すると、フロー コンテンツ内でハイパーリンクをホストできます。|  
|<xref:System.Windows.Forms.ListBox>|<xref:System.Windows.Controls.ListBox>||  
|<xref:System.Windows.Forms.ListView>|<xref:System.Windows.Controls.ListView>|<xref:System.Windows.Controls.ListView> コントロールは、読み取り専用の詳細表示を提供します。|  
|<xref:System.Windows.Forms.MaskedTextBox>|同等のコントロールはありません。||  
|<xref:System.Windows.Forms.MenuStrip>|<xref:System.Windows.Controls.Menu>|<xref:System.Windows.Controls.Menu> コントロールのスタイル設定は、<xref:System.Windows.Forms.ToolStripProfessionalRenderer?displayProperty=fullName> クラスとほぼ同様の動作および外観を提供できます。|  
|<xref:System.Windows.Forms.MonthCalendar>|<xref:System.Windows.Controls.Calendar>||  
|<xref:System.Windows.Forms.NotifyIcon>|同等のコントロールはありません。||  
|<xref:System.Windows.Forms.NumericUpDown>|<xref:System.Windows.Controls.TextBox> と 2 つの <xref:System.Windows.Controls.Primitives.RepeatButton> コントロール。||  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:Microsoft.Win32.OpenFileDialog>|<xref:Microsoft.Win32.OpenFileDialog> クラスは、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] コントロールの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ラッパー クラスです。|  
|<xref:System.Windows.Forms.PageSetupDialog>|同等のコントロールはありません。||  
|<xref:System.Windows.Forms.Panel>|<xref:System.Windows.Controls.Canvas>||  
|<xref:System.Windows.Forms.PictureBox>|<xref:System.Windows.Controls.Image>||  
|<xref:System.Windows.Forms.PrintDialog>|<xref:System.Windows.Controls.PrintDialog>||  
|<xref:System.Drawing.Printing.PrintDocument>|同等のコントロールはありません。||  
|<xref:System.Windows.Forms.PrintPreviewControl>|<xref:System.Windows.Controls.DocumentViewer>||  
|<xref:System.Windows.Forms.PrintPreviewDialog>|同等のコントロールはありません。||  
|<xref:System.Windows.Forms.ProgressBar>|<xref:System.Windows.Controls.ProgressBar>||  
|<xref:System.Windows.Forms.PropertyGrid>|同等のコントロールはありません。||  
|<xref:System.Windows.Forms.RadioButton>|<xref:System.Windows.Controls.RadioButton>||  
|<xref:System.Windows.Forms.RichTextBox>|<xref:System.Windows.Controls.RichTextBox>||  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:Microsoft.Win32.SaveFileDialog>|<xref:Microsoft.Win32.SaveFileDialog> クラスは、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] コントロールの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ラッパー クラスです。|  
|<xref:System.Windows.Forms.ScrollableControl>|<xref:System.Windows.Controls.ScrollViewer>||  
|<xref:System.Media.SoundPlayer>|<xref:System.Windows.Media.MediaPlayer>||  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Controls.GridSplitter>||  
|<xref:System.Windows.Forms.StatusStrip>|<xref:System.Windows.Controls.Primitives.StatusBar>||  
|<xref:System.Windows.Forms.TabControl>|<xref:System.Windows.Controls.TabControl>||  
|<xref:System.Windows.Forms.TableLayoutPanel>|<xref:System.Windows.Controls.Grid>||  
|<xref:System.Windows.Forms.TextBox>|<xref:System.Windows.Controls.TextBox>||  
|<xref:System.Windows.Forms.Timer>|<xref:System.Windows.Threading.DispatcherTimer>||  
|<xref:System.Windows.Forms.ToolStrip>|<xref:System.Windows.Controls.ToolBar>||  
|<xref:System.Windows.Forms.ToolStripContainer>|コンポジションを使用した <xref:System.Windows.Controls.ToolBar>。||  
|<xref:System.Windows.Forms.ToolStripDropDown>|コンポジションを使用した <xref:System.Windows.Controls.ToolBar>。||  
|<xref:System.Windows.Forms.ToolStripDropDownMenu>|コンポジションを使用した <xref:System.Windows.Controls.ToolBar>。||  
|<xref:System.Windows.Forms.ToolStripPanel>|コンポジションを使用した <xref:System.Windows.Controls.ToolBar>。||  
|<xref:System.Windows.Forms.ToolTip>|<xref:System.Windows.Controls.ToolTip>||  
|<xref:System.Windows.Forms.TrackBar>|<xref:System.Windows.Controls.Slider>||  
|<xref:System.Windows.Forms.TreeView>|<xref:System.Windows.Controls.TreeView>||  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Controls.UserControl>||  
|<xref:System.Windows.Forms.VScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|スクロールは、コンテナー コントロールに組み込まれます。|  
|<xref:System.Windows.Forms.WebBrowser>|<xref:System.Windows.Controls.Frame>, <xref:System.Windows.Controls.WebBrowser?displayProperty=fullName>|<xref:System.Windows.Controls.Frame> コントロールは、HTML ページをホストできます。<br /><br /> [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)] から、<xref:System.Windows.Controls.WebBrowser?displayProperty=fullName> コントロールは HTML ページをホストできるほか、<xref:System.Windows.Controls.Frame> コントロールをサポートできます。|  
  
## 参照  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [Windows フォーム開発者向け WPF デザイナー](http://msdn.microsoft.com/ja-jp/47ad0909-e89b-4996-b4ac-874d929f94ca)   
 [チュートリアル: WPF での Windows フォーム コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)   
 [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)   
 [移行と相互運用性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)