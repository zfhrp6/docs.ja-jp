---
title: "チュートリアル: WPF での ActiveX コントロールのホスト"
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
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b0e85c715db30c6e577980376d25d56238e2835a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a>チュートリアル: WPF での ActiveX コントロールのホスト
ブラウザーでの強化された操作を有効にするを使用することができます[!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)]コントロールで、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-ベースのアプリケーションです。 このチュートリアルでは、ホストする方法、[!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)]上のコントロールとして、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ページ。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   プロジェクトの作成。  
  
-   ActiveX コントロールを作成します。  
  
-   WPF ページ上の ActiveX コントロールをホストします。  
  
 このチュートリアルを完了する際に、使用する方法を把握して、[!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)]コントロールで、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-ベースのアプリケーションです。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)]コンピューターにインストールされている場所[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]がインストールされています。  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
  
#### <a name="to-create-and-set-up-the-project"></a>プロジェクトを作成し、設定するには  
  
1.  という名前の WPF アプリケーション プロジェクトを作成する`HostingAxInWpf`です。  
  
2.  Windows フォーム コントロール ライブラリ プロジェクト、ソリューションを追加し、プロジェクトに名前を`WmpAxLib`です。  
  
3.  プロジェクトで、WmpAxLib wmp.dll の名前は、Windows Media Player アセンブリへの参照を追加します。  
  
4.  開く、**ツールボックス**です。  
  
5.  右クリックし、**ツールボックス**、順にクリック**アイテムの選択**です。  
  
6.  をクリックして、 **COM コンポーネント** タブで、 **Windows Media Player**を制御して、をクリックして**OK**です。  
  
     Windows Media Player のコントロールに追加、**ツールボックス**です。  
  
7.  ソリューション エクスプ ローラーで右クリックし、 **UserControl1**ファイルを開き、をクリックして**の名前を変更**です。  
  
8.  名前を変更`WmpAxControl.vb`または`WmpAxControl.cs`、言語によって異なります。  
  
9. すべての参照の名前を変更するメッセージが表示されたら、クリックして**はい**です。  
  
## <a name="creating-the-activex-control"></a>ActiveX コントロールを作成します。  
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]自動的に生成、<xref:System.Windows.Forms.AxHost>のラッパー クラス、[!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)]デザイン サーフェイスにコントロールを追加する場合を制御します。 次の手順では、AxInterop.WMPLib.dll をという名前のマネージ アセンブリを作成します。  
  
#### <a name="to-create-the-activex-control"></a>ActiveX コントロールを作成するには  
  
1.  Windows フォーム デザイナーで WmpAxControl.vb またはに応じてを開きます。  
  
2.  **ツールボックス**、デザイン画面に、Windows Media Player のコントロールを追加します。  
  
3.  [プロパティ] ウィンドウで、Windows Media Player のコントロールの値を設定<xref:System.Windows.Forms.Control.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.Fill>です。  
  
4.  WmpAxLib コントロール ライブラリ プロジェクトをビルドします。  
  
## <a name="hosting-the-activex-control-on-a-wpf-page"></a>WPF ページ上の ActiveX コントロールをホストしています。  
  
#### <a name="to-host-the-activex-control"></a>ActiveX コントロールをホストするには  
  
1.  HostingAxInWpf プロジェクトで、生成されたへの参照を追加[!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)]相互運用機能アセンブリ。  
  
     このアセンブリは、AxInterop.WMPLib.dll の名前は、Windows Media Player のコントロールをインポートしたときに、WmpAxLib プロジェクトのデバッグ フォルダーに追加されました。  
  
2.  WindowsFormsIntegration.dll と呼ばれる WindowsFormsIntegration アセンブリへの参照を追加します。  
  
3.  参照を追加、 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] System.Windows.Forms.dll をという名前のアセンブリ。  
  
4.  WPF デザイナーで、MainWindow.xaml を開きます。  
  
5.  名前、<xref:System.Windows.Controls.Grid>要素`grid1`です。  
  
     [!code-xaml[HostingAxInWpf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]  
  
6.  [デザイン] ビューまたは XAML ビューで、選択、<xref:System.Windows.Window>要素。  
  
7.  [プロパティ] ウィンドウ、**イベント**タブです。  
  
8.  ダブルクリックして、<xref:System.Windows.FrameworkElement.Loaded>イベント。  
  
9. 処理する次のコードを挿入、<xref:System.Windows.FrameworkElement.Loaded>イベント。  
  
     このコードのインスタンスを作成、<xref:System.Windows.Forms.Integration.WindowsFormsHost>を制御しのインスタンスを追加、`AxWindowsMediaPlayer`の子と同様に制御します。  
  
     [!code-csharp[HostingAxInWpf#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. F5 キーを押してアプリケーションをビルドし、実行します。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF デザイナー](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [チュートリアル: WPF での Windows フォーム複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
