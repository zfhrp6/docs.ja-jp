---
title: "チュートリアル: WPF での ActiveX コントロールのホスト | Microsoft Docs"
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
  - "ActiveX コントロール [WPF 相互運用性]"
  - "ホスト (ActiveX コントロールを)"
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
caps.latest.revision: 30
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 30
---
# チュートリアル: WPF での ActiveX コントロールのホスト
ブラウザーでの操作を改善するには、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ベースのアプリケーションで [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] コントロールを使用できます。  このチュートリアルでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ページ上のコントロールとして [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] をホストする方法を示します。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   プロジェクトの作成。  
  
-   ActiveX コントロールの作成。  
  
-   WPF ページでの ActiveX コントロールのホスティング。  
  
 このチュートリアルを完了すると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ベースのアプリケーションで [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] コントロールを使用する方法を理解できます。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] がインストールされているコンピューターにインストールされた [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)]。  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## プロジェクトの作成  
  
#### プロジェクトを作成し、設定するには  
  
1.  `HostingAxInWpf` という名前の WPF アプリケーション プロジェクトを作成します。  
  
2.  ソリューションに Windows フォーム コントロール ライブラリ プロジェクトを追加し、プロジェクトに `WmpAxLib` という名前を付けます。  
  
3.  WmpAxLib プロジェクトで、wmp.dll という名前の Windows Media Player アセンブリへの参照を追加します。  
  
4.  **\[ツールボックス\]** を開きます。  
  
5.  **ツールボックス**内を右クリックし、**\[アイテムの選択\]** をクリックします。  
  
6.  **\[COM コンポーネント\]** タブをクリックし、**\[Windows Media Player\]** コントロールを選択し、**\[OK\]** をクリックします。  
  
     Windows Media Player コントロールが**ツールボックス**に追加されます。  
  
7.  ソリューション エクスプローラーで、**\[UserControl1\]** ファイルを右クリックし、**\[名前の変更\]** をクリックします。  
  
8.  言語に応じて名前を `WmpAxControl.vb` または `WmpAxControl.cs` に変更します。  
  
9. 全ての参照名を変更するかを確認するメッセージが表示されたら、**\[はい\]** をクリックします。  
  
## ActiveX コントロールの作成  
 コントロールがデザイン サーフェイスに追加されると、[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] によって [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] コントロールの <xref:System.Windows.Forms.AxHost> ラッパー クラスが自動的に生成されます。  次の手順では、AxInterop.WMPLib.dll という名前の管理アセンブリが作成されます。  
  
#### ActiveX コントロールを作成するには  
  
1.  Windows フォーム デザイナーで、WmpAxControl.vb または WmpAxControl.cs を開きます。  
  
2.  **ツールボックス**から Windows Media Player コントロールをデザイン サーフェイスに追加します。  
  
3.  \[プロパティ\] ウィンドウで、Windows Media Player コントロールの <xref:System.Windows.Forms.Control.Dock%2A> プロパティの値を <xref:System.Windows.Forms.DockStyle> に設定します。  
  
4.  WmpAxLib コントロール ライブラリ プロジェクトをビルドします。  
  
## WPF ページでの ActiveX コントロールのホスティング  
  
#### ActiveX コントロールをホストするには  
  
1.  HostingAxInWpf プロジェクトで、生成された [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] 相互運用アセンブリに参照を追加します。  
  
     このアセンブリ名は AxInterop.WMPLib.dll で、Windows Media Player コントロールをインポートした時点で、WmpAxLib プロジェクトの Debug フォルダーに追加されています。  
  
2.  WindowsFormsIntegration.dll という名前の WindowsFormsIntegration アセンブリに参照を追加します。  
  
3.  System.Windows.Forms.dll という名前の [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] アセンブリに参照を追加します。  
  
4.  WPF デザイナーで、MainWindow.xaml を開きます。  
  
5.  <xref:System.Windows.Controls.Grid> 要素に `grid1` という名前を付けます。  
  
     [!code-xml[HostingAxInWpf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]  
  
6.  デザイン ビューまたは XAML ビューで、<xref:System.Windows.Window> 要素を選択します。  
  
7.  プロパティ ウィンドウの **\[イベント\]** タブをクリックします。  
  
8.  <xref:System.Windows.FrameworkElement.Loaded> イベントをダブルクリックします。  
  
9. <xref:System.Windows.FrameworkElement.Loaded> イベントを処理するには、次のコードを挿入します。  
  
     このコードは、<xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールのインスタンスを作成し、`AxWindowsMediaPlayer` コントロールのインスタンスをその子として追加します。  
  
     [!code-csharp[HostingAxInWpf#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. F5 キーを押してアプリケーションをビルドし、実行します。  
  
## 参照  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [WPF デザイナー](http://msdn.microsoft.com/ja-jp/c6c65214-8411-4e16-b254-163ed4099c26)   
 [チュートリアル: WPF での Windows フォーム複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)   
 [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)