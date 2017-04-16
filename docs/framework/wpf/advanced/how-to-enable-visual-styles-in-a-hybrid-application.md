---
title: "方法 : ハイブリッド アプリケーションで視覚スタイルを有効にする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ハイブリッド アプリケーション [WPF 相互運用性]"
  - "視覚スタイル [Windows フォーム]"
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : ハイブリッド アプリケーションで視覚スタイルを有効にする
ここでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ベースのアプリケーションでホストされている [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールで [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] の視覚スタイルを有効にする方法を示します。  
  
 アプリケーションが <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> メソッドを呼び出すと、ほとんどの [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは、アプリケーションが [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] で実行されるときの視覚スタイルを自動的に使用します。  詳細については、「[visual スタイルが使用されているコントロールのレンダリング](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)」を参照してください。  
  
 このトピックで示すタスクの完全なコード一覧については、[ハイブリッド アプリケーションでの視覚スタイルの有効化のサンプル](http://go.microsoft.com/fwlink/?LinkID=159986)を参照してください。  
  
## Windows フォーム視覚スタイルの有効化  
  
#### Windows フォーム視覚スタイルを有効にするには  
  
1.  `HostingWfWithVisualStyles` という名前の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーション プロジェクトを作成します。  
  
2.  ソリューション エクスプローラーで、次のアセンブリへの参照を追加します。  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  ツールボックスで、<xref:System.Windows.Controls.Grid> アイコンをダブルクリックして、<xref:System.Windows.Controls.Grid> 要素をデザイン サーフェイスに配置します。  
  
4.  \[プロパティ\] ウィンドウで、<xref:System.Windows.FrameworkElement.Height%2A> プロパティと <xref:System.Windows.FrameworkElement.Width%2A> プロパティの値を **Auto** に設定します。  
  
5.  デザイン ビューまたは XAML で、<xref:System.Windows.Window> を選択します。  
  
6.  プロパティ ウィンドウの **\[イベント\]** タブをクリックします。  
  
7.  <xref:System.Windows.FrameworkElement.Loaded> イベントをダブルクリックします。  
  
8.  MainWindow.xaml.vb または MainWindow.xaml.cs で、<xref:System.Windows.FrameworkElement.Loaded> イベントを処理する次のコードを挿入します。  
  
     [!code-csharp[HostingWfWithVisualStyles#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. F5 キーを押してアプリケーションをビルドし、実行します。  
  
     [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールが、視覚スタイルで塗りつぶされます。  
  
## Windows フォーム視覚スタイルの無効化  
 視覚スタイルを無効にするには、<xref:System.Windows.Forms.Application.EnableVisualStyles%2A> メソッドの呼び出しを削除します。  
  
#### Windows フォーム視覚スタイルを無効にするには  
  
1.  コード エディターで MainWindow.xaml.vb または MainWindow.xaml.cs を開きます。  
  
2.  <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> メソッドの呼び出しをコメント化します。  
  
3.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
     [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールが既定のシステム スタイルで塗りつぶされます。  
  
## 参照  
 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>   
 <xref:System.Windows.Forms.VisualStyles>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [visual スタイルが使用されているコントロールのレンダリング](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)   
 [チュートリアル: WPF での Windows フォーム コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)