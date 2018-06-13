---
title: 'チュートリアル: WPF での Windows フォーム コントロールのホスト'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: 515135893c0d6cf251977bbddc13241e8b6b60bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546830"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a>チュートリアル: WPF での Windows フォーム コントロールのホスト
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 豊富な機能セットには、多くのコントロールを提供します。 ただし、場合がありますも使用する[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールに対して、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ページ。 たとえば、既存のかなりの投資がある[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール、またはする必要があります、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ユニークな機能を提供するコントロール。  
  
 このチュートリアルでは、ホストする方法、 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType>の control 権限、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コードを使用してページ。  
  
 このチュートリアルで説明するタスクの完全なコードについては、次を参照してください。 [WPF サンプル Windows フォーム コントロールをホストしている](http://go.microsoft.com/fwlink/?LinkID=160057)です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]。  
  
## <a name="hosting-the-windows-forms-control"></a>Windows フォーム コントロールをホストしています。  
  
#### <a name="to-host-the-maskedtextbox-control"></a>MaskedTextBox コントロールをホストするには  
  
1.  という名前の WPF アプリケーション プロジェクトを作成する`HostingWfInWpf`です。  
  
2.  次のアセンブリへの参照を追加します。  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  MainWindow.xaml を開き、[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]です。  
  
4.  名前、<xref:System.Windows.Controls.Grid>要素`grid1`です。  
  
     [!code-xaml[HostingWfInWPF#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]  
  
5.  [デザイン] ビューまたは XAML ビューで、選択、<xref:System.Windows.Window>要素。  
  
6.  [プロパティ] ウィンドウ、**イベント**タブです。  
  
7.  ダブルクリックして、<xref:System.Windows.FrameworkElement.Loaded>イベント。  
  
8.  処理する次のコードを挿入、<xref:System.Windows.FrameworkElement.Loaded>イベント。  
  
     [!code-csharp[HostingWfInWPF#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]  
  
9. ファイルの上部には、次のコードを追加`Imports`または`using`ステートメントです。  
  
     [!code-csharp[HostingWfInWPF#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]  
  
10. F5 キーを押してアプリケーションをビルドし、実行します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF デザイナー](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [チュートリアル: WPF での XAML を使用した Windows フォーム コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)  
 [チュートリアル: WPF での Windows フォーム複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [Windows フォーム コントロールおよび同等の WPF コントロール](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)  
 [WPF サンプル Windows フォーム コントロールのホスト](http://go.microsoft.com/fwlink/?LinkID=160057)
