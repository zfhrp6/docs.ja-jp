---
title: '方法 : ハイブリッド アプリケーションで視覚スタイルを有効にする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- visual styles [Windows Forms]
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
ms.openlocfilehash: 2d714ad020f2f7b6a6343c8f8e3901b59dfd23a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a>方法 : ハイブリッド アプリケーションで視覚スタイルを有効にする
このトピックは、有効にする方法を示しています。[!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]上の visual スタイル、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]でホストされるコントロール、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-ベースのアプリケーションです。  
  
 アプリケーションが呼び出す場合、<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>メソッド、ほとんどの[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールが自動的に使用の visual スタイルでアプリケーションを実行時に[!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]です。 詳細については、次を参照してください。 [Visual スタイルを使用しているコントロールのレンダリング](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)です。  
  
 このトピックで示すタスクの完全なコードについては、次を参照してください。[ハイブリッド アプリケーションのサンプルの Visual スタイルを有効にすると](http://go.microsoft.com/fwlink/?LinkID=159986)です。  
  
## <a name="enabling-windows-forms-visual-styles"></a>Windows フォーム視覚スタイルの有効化  
  
#### <a name="to-enable-windows-forms-visual-styles"></a>Windows フォーム視覚スタイルを有効にするには  
  
1.  作成、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]という名前のアプリケーション プロジェクト`HostingWfWithVisualStyles`です。  
  
2.  ソリューション エクスプローラーで、次のアセンブリへの参照を追加します。  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  ツールボックスでダブルクリックして、<xref:System.Windows.Controls.Grid>を配置するにはアイコン、<xref:System.Windows.Controls.Grid>デザイン サーフェイス上の要素。  
  
4.  [プロパティ] ウィンドウでの値を設定、<xref:System.Windows.FrameworkElement.Height%2A>と<xref:System.Windows.FrameworkElement.Width%2A>プロパティ**自動**です。  
  
5.  [デザイン] ビューまたは XAML ビューで、選択、<xref:System.Windows.Window>です。  
  
6.  [プロパティ] ウィンドウ、**イベント**タブです。  
  
7.  ダブルクリックして、<xref:System.Windows.FrameworkElement.Loaded>イベント。
  
8.  MainWindow.xaml.vb または MainWindow.xaml.cs で処理する次のコードを挿入、<xref:System.Windows.FrameworkElement.Loaded>イベント。  
  
     [!code-csharp[HostingWfWithVisualStyles#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. F5 キーを押してアプリケーションをビルドし、実行します。  
  
     [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールが visual スタイルで描画します。  
  
## <a name="disabling-windows-forms-visual-styles"></a>Windows フォーム視覚スタイルの無効化  
 Visual スタイルを無効にするには、削除するだけを呼び出し、<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>メソッドです。  
  
#### <a name="to-disable-windows-forms-visual-styles"></a>Windows フォーム視覚スタイルを無効にするには  
  
1.  コード エディターで MainWindow.xaml.vb または MainWindow.xaml.cs を開きます。  
  
2.  呼び出しをコメント、<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>メソッドです。  
  
3.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
     [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールが既定のシステムのスタイルで描画します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>  
 <xref:System.Windows.Forms.VisualStyles>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [visual スタイルが使用されているコントロールのレンダリング](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 [チュートリアル: WPF での Windows フォーム コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
