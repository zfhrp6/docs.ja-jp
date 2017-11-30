---
title: "チュートリアル: Windows フォームでの 3D WPF 複合コントロールのホスト"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c5af705509d30f7dfd50ade0c07aca242deff4dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a>チュートリアル: Windows フォームでの 3D WPF 複合コントロールのホスト
このチュートリアルでは、作成する方法、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]複合を制御し、ホストすることで[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールおよびフォームを使用して、<xref:System.Windows.Forms.Integration.ElementHost>コントロール。  
  
 このチュートリアルでは、実装、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> 2 つの子コントロールを格納しています。 <xref:System.Windows.Controls.UserControl> 3 次元 (3 D) 円錐型が表示されます。 3-D オブジェクトを表示することが非常に簡単、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]よりと[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]です。 そのため、これがわかりやすいホスト、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>で 3-D グラフィックスを作成するクラス[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]です。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   作成する、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>です。  
  
-   Windows フォーム ホスト プロジェクトを作成します。  
  
-   ホストしている、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>です。  
  
 このチュートリアルでタスクの完全なコードについては、次を参照してください。 [Windows フォームのサンプルの 3-D WPF 複合コントロールをホストしている](http://go.microsoft.com/fwlink/?LinkID=160001)です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]。  
  
<a name="To_Create_the_UserControl"></a>   
## <a name="creating-the-usercontrol"></a>ユーザー コントロールを作成します。  
  
#### <a name="to-create-the-usercontrol"></a>ユーザー コントロールを作成するには  
  
1.  という名前の WPF ユーザー コントロール ライブラリ プロジェクトを作成する`HostingWpfUserControlInWf`です。  
  
2.  UserControl1.xaml を開き、[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]です。  
  
3.  生成されたコードを次のコードに置き換えます。  
  
     このコードを定義、 <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> 2 つの子コントロールを格納しています。 最初の子コントロールは、<xref:System.Windows.Controls.Label?displayProperty=nameWithType>コントロール以外の 2 つ目は、 <xref:System.Windows.Controls.Viewport3D> 3-D 円錐型を表示するコントロール。  
  
     [!code-xaml[HostingWpfUserControlInWf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
<a name="To_Create_the_Windows_Forms_Host_Project"></a>   
## <a name="creating-the-windows-forms-host-project"></a>Windows フォーム ホスト プロジェクトを作成します。  
  
#### <a name="to-create-the-host-project"></a>ホスト プロジェクトを作成するには  
  
1.  という名前の Windows アプリケーション プロジェクトを追加`WpfUserControlHost`をソリューションにします。 詳細については、次を参照してください。[する方法: 新しい WPF アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)です。  
  
2.  ソリューション エクスプ ローラーで、WindowsFormsIntegration.dll と呼ばれる WindowsFormsIntegration アセンブリへの参照を追加します。  
  
3.  次の参照を追加[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アセンブリ。  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
4.  `HostingWpfUserControlInWf` への参照をプロジェクトに追加します。  
  
5.  ソリューション エクスプ ローラーで、設定、`WpfUserControlHost`プロジェクトをスタートアップ プロジェクト。  
  
<a name="To_Host_the_Windows_Presentation_Foundation"></a>   
## <a name="hosting-the-windows-presentation-foundation-usercontrol"></a>Windows Presentation Foundation ユーザー コントロールをホストしています。  
  
#### <a name="to-host-the-usercontrol"></a>ユーザー コントロールをホストするには  
  
1.  Windows フォーム デザイナーで、Form1 を開きます。  
  
2.  [プロパティ] ウィンドウでをクリックして**イベント**、順にダブルクリックし、<xref:System.Windows.Forms.Form.Load>イベント ハンドラーを作成するイベントです。  
  
     コード エディターが新たに生成されたに`Form1_Load`イベント ハンドラー。  
  
3.  Form1.cs のコードを次のコードに置き換えます。  
  
     `Form1_Load`イベント ハンドラーのインスタンスを作成する`UserControl1`し、追加の接続を受け付ける、<xref:System.Windows.Forms.Integration.ElementHost>子コントロールのコントロールのコレクション。 <xref:System.Windows.Forms.Integration.ElementHost>コントロールが子コントロールのフォームのコレクションに追加します。  
  
     [!code-csharp[HostingWpfUserControlInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]  
  
4.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF デザイナー](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [チュートリアル: WPF での Windows フォーム複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Windows フォームのサンプルでの WPF 複合コントロールをホストしています。](http://go.microsoft.com/fwlink/?LinkID=160001)
