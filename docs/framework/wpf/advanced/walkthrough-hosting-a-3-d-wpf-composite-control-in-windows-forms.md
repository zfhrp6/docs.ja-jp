---
title: "チュートリアル: Windows フォームでの 3D WPF 複合コントロールのホスト | Microsoft Docs"
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
  - "複合コントロール, ホスト (WPF を)"
  - "ホスト (Windows フォームの WPF コンテンツを)"
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# チュートリアル: Windows フォームでの 3D WPF 複合コントロールのホスト
このチュートリアルでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 複合コントロールを作成し、それを <xref:System.Windows.Forms.Integration.ElementHost> コントロールを使用して [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]のコントロールおよびフォームでホストする方法を示します。  
  
 ここでは、2 つの子コントロールを含む [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> を実装します。  <xref:System.Windows.Controls.UserControl> は、3 次元 \(3\-D\) の円錐形を表示します。  3\-D オブジェクトのレンダリングは、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]より [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で行う方がはるかに簡単です。  したがって、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]で [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> クラスをホストして 3\-D グラフィックスを作成することには意味があります。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> の作成  
  
-   Windows フォームのホスト プロジェクトの作成  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> のホスト  
  
 このチュートリアルで示すタスクの完全なコード一覧については、[Windows フォームでの 3\-D WPF 複合コントロールのホストのサンプル](http://go.microsoft.com/fwlink/?LinkID=160001)を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
<a name="To_Create_the_UserControl"></a>   
## UserControl の作成  
  
#### UserControl を作成するには  
  
1.  `HostingWpfUserControlInWf` という名前の WPF ユーザー コントロール ライブラリ プロジェクトを作成します。  
  
2.  [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]で UserControl1.xaml を開きます。  
  
3.  生成されているコードを次のコードに置き換えます。  
  
     このコードでは、2 つの子コントロールを含む <xref:System.Windows.Controls.UserControl?displayProperty=fullName> が定義されています。  1 番目の子コントロールは <xref:System.Windows.Controls.Label?displayProperty=fullName> コントロールで、2 番目は 3\-D の円錐形を表示する <xref:System.Windows.Controls.Viewport3D> コントロールです。  
  
     [!code-xml[HostingWpfUserControlInWf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
<a name="To_Create_the_Windows_Forms_Host_Project"></a>   
## Windows フォームのホスト プロジェクトの作成  
  
#### ホスト プロジェクトを作成するには  
  
1.  `WpfUserControlHost` という名前の Windows アプリケーション プロジェクトをソリューションに追加します。  詳細については、「[方法 : 新しい WPF アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/ja-jp/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)」を参照してください。  
  
2.  ソリューション エクスプローラーで、WindowsFormsIntegration.dll という名前の WindowsFormsIntegration アセンブリへの参照を追加します。  
  
3.  次の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アセンブリへの参照を追加します。  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
4.  `HostingWpfUserControlInWf` プロジェクトへの参照を追加します。  
  
5.  ソリューション エクスプローラーで、`WpfUserControlHost` プロジェクトをスタートアップ プロジェクトとして設定します。  
  
<a name="To_Host_the_Windows_Presentation_Foundation"></a>   
## Windows Presentation Foundation UserControl のホスト  
  
#### UserControl をホストするには  
  
1.  Windows フォーム デザイナーで、Form1 を開きます。  
  
2.  \[プロパティ\] ウィンドウで、\[イベント\] をクリックし、<xref:System.Windows.Forms.Form.Load> イベントをダブルクリックしてイベント ハンドラーを作成します。  
  
     コード エディターで、新しく生成された `Form1_Load` イベント ハンドラーが開かれます。  
  
3.  Form1.cs 内のコードを次のコードに置き換えます。  
  
     `Form1_Load` イベント ハンドラーは、`UserControl1` のインスタンスを作成し、<xref:System.Windows.Forms.Integration.ElementHost> コントロールの子コントロールのコレクションにそれを追加します `` 。  フォームの子コントロールのコレクションには、<xref:System.Windows.Forms.Integration.ElementHost> コントロールが追加されます。  
  
     [!code-csharp[HostingWpfUserControlInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]  
  
4.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
## 参照  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [WPF デザイナー](http://msdn.microsoft.com/ja-jp/c6c65214-8411-4e16-b254-163ed4099c26)   
 [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)   
 [チュートリアル: WPF での Windows フォーム複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)   
 [Windows フォームでの WPF 複合コントロールのホストのサンプル](http://go.microsoft.com/fwlink/?LinkID=160001)