---
title: "チュートリアル: WPF での、XAML を使用した Windows フォーム コントロールのホスト"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 65afce3e5a5b113b5243d68fd3b35231e2d92f86
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a>チュートリアル: WPF での、XAML を使用した Windows フォーム コントロールのホスト
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]豊富な機能セットには、多くのコントロールを提供します。 ただし、場合がありますも使用する[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールに対して、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ページ。 たとえば、既存のかなりの投資がある[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール、またはする必要があります、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ユニークな機能を提供するコントロール。  
  
 このチュートリアルでは、Windows フォームをホストする方法<xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType>の control 権限、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を使用してページ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]です。  
  
 このチュートリアルで説明するタスクの完全なコードについては、次を参照してください。[を使用して XAML サンプルでの WPF での Windows フォーム コントロールをホストしている](http://go.microsoft.com/fwlink/?LinkID=160000)です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]。  
  
## <a name="hosting-the-windows-forms-control"></a>Windows フォーム コントロールをホストしています。  
  
#### <a name="to-host-the-maskedtextbox-control"></a>MaskedTextBox コントロールをホストするには  
  
1.  という名前の WPF アプリケーション プロジェクトを作成する`HostingWfInWpfWithXaml`です。  
  
2.  次のアセンブリへの参照を追加します。  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  MainWindow.xaml を開き、[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]です。  
  
4.  <xref:System.Windows.Window>要素では、次の名前空間のマッピングを追加します。 `wf`名前空間のマッピングを含むアセンブリへの参照の確立、[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)]コントロール。  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <xref:System.Windows.Controls.Grid>要素は、次の XAML を追加します。  
  
     <xref:System.Windows.Forms.MaskedTextBox>コントロールの子として作成された、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロール。  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF デザイナー](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [チュートリアル: WPF での Windows フォーム コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [チュートリアル: WPF での Windows フォーム複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [Windows フォーム コントロールおよび同等の WPF コントロール](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)  
 [XAML のサンプルを使用して、WPF では、Windows フォーム コントロールをホストしています。](http://go.microsoft.com/fwlink/?LinkID=160000)
