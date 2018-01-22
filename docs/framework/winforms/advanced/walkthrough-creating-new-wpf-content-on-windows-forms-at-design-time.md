---
title: "チュートリアル: デザイン時の Windows フォームでの新しい WPF コンテンツの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc357b8ad1ff450c699878dfffe1fbb6e2440f49
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time"></a>チュートリアル: デザイン時の Windows フォームでの新しい WPF コンテンツの作成
このトピックでは、Windows フォーム ベースのアプリケーションで使用する Windows Presentation Foundation (WPF) コントロールを作成する方法を示します。  
  
 このチュートリアルでは次のタスクを実行します。  
  
-   プロジェクトを作成する。  
  
-   新しい WPF コントロールを作成する。  
  
-   新しい WPF コントロールを Windows フォームに追加する。 WPF コントロールは <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 まず、Windows フォーム プロジェクトを作成します。  
  
> [!NOTE]
>  WPF コンテンツをホストする場合は、C# プロジェクトと Visual Basic プロジェクトのみがサポートされます。  
  
#### <a name="to-create-the-project"></a>プロジェクトを作成するには  
  
-   Visual Basic または Visual c# のという名前で新しい Windows フォーム アプリケーション プロジェクトを作成`HostingWpf`です。  
  
## <a name="creating-a-new-wpf-control"></a>新しい WPF コントロールの作成  
 新しい WPF コントロールを作成し、プロジェクトに追加するのは、プロジェクトへの他の項目の追加と同じくらい簡単です。 Windows フォーム デザイナーは特定の種類という名前のコントロールの*複合コントロール*、または*ユーザー コントロール*です。 WPF ユーザー コントロールの詳細については、「<xref:System.Windows.Controls.UserControl>」を参照してください。  
  
> [!NOTE]
>  WPF の <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> の種類は、同じ <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType> という名前を持つ、Windows フォームで提供されるユーザー コントロールの種類とは区別されます。  
  
#### <a name="to-create-a-new-wpf-control"></a>新しい WPF コントロールを作成するには  
  
1.  **ソリューション エクスプ ローラー**、追加、新しい**WPF ユーザー コントロール ライブラリ**プロジェクトがソリューションにします。 このコントロール ライブラリの既定の名前である `WpfControlLibrary1` を使用します。 既定のコントロールの名前は `UserControl1.xaml` です。  
  
     新しいコントロールを追加すると次の影響があります。  
  
    -   ファイル UserControl1.xaml が追加されます。  
  
    -   ファイル UserControl1.xaml.cs または UserControl1.xaml.vb のいずれかが追加されます。 このファイルには、イベント ハンドラーとその他の実装のための分離コードが含まれています。  
  
    -   WPF アセンブリへの参照が追加されます。  
  
    -   ファイル UserControl1.xaml が [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] で開きます。  
  
2.  デザイン ビューで `UserControl1` が選択されていることを確認します。 詳細については、次を参照してください。[する方法: Select およびデザイン サーフェイス上の要素の移動](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474)です。  
  
3.  **プロパティ**ウィンドウで、設定の値、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティ`200`です。  
  
4.  **ツールボックス**、ドラッグ、<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>コントロールをデザイン画面にします。  
  
5.  **プロパティ**ウィンドウで、設定の値、<xref:System.Windows.Controls.TextBox.Text%2A>プロパティを**ホストするコンテンツの**します。  
  
    > [!NOTE]
    >  一般的には、もう少し高度な WPF コンテンツをホストしてください。 ここでは、説明する目的でのみ <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> コントロールを使用しています。  
  
6.  プロジェクトをビルドします。  
  
## <a name="adding-a-wpf-control-to-a-windows-form"></a>WPF コントロールを Windows フォームに追加する  
 新しい WPF コントロールは、フォームで使用可能な状態です。 Windows フォームは、<xref:System.Windows.Forms.Integration.ElementHost> コントロールを使用して、WPF コンテンツをホストします。  
  
#### <a name="to-add-a-wpf-control-to-a-windows-form"></a>WPF コントロールを Windows フォームに追加するには  
  
1.  Windows フォーム デザイナーで `Form1` を開きます。  
  
2.  **ツールボックス**、というラベルのタブを見つける**WPFUserControlLibrary WPF ユーザー コントロール**です。  
  
3.  `UserControl1` のインスタンスをフォームにドラッグします。  
  
    -   WPF コントロールをホストするためのフォームの上に、<xref:System.Windows.Forms.Integration.ElementHost> コントロールが自動的に作成されます。  
  
    -   <xref:System.Windows.Forms.Integration.ElementHost>コントロールの名前は`elementHost1`し、[、**プロパティ**] ウィンドウで確認できます、<xref:System.Windows.Forms.Integration.ElementHost.Child%2A>プロパティに設定されている**UserControl1**です。  
  
    -   WPF アセンブリへの参照がプロジェクトに追加されます。  
  
    -   `elementHost1` コントロールに、使用可能なホスティング オプションを示すスマート タグ パネルがあります。  
  
4.  **ElementHost タスク**スマート タグ パネルで、**親コンテナーにドッキング**です。  
  
5.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
## <a name="next-steps"></a>次の手順  
 Windows フォームと WPF は異なるテクノロジですが、密接に相互運用するよう設計されています。 アプリケーションに高度な外観と動作を提供するには、次の手順を実行します。  
  
-   WPF ページで Windows フォーム コントロールをホストします。 詳細については、次を参照してください。[チュートリアル: WPF では、Windows フォーム コントロールをホストしている](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)です。  
  
-   WPF コンテンツに Windows フォームの視覚スタイルを適用します。 詳細については、次を参照してください。[する方法: ハイブリッド アプリケーションで Visual スタイルを有効にする](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)です。  
  
-   WPF コンテンツのスタイルを変更します。 詳細については、次を参照してください。[チュートリアル: WPF コンテンツのスタイル処理の](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md)します。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [移行と相互運用性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [WPF コントロールの使用](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [WPF デザイナー](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
