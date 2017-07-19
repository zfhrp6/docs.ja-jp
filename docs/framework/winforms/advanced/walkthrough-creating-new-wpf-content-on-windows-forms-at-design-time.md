---
title: "チュートリアル: デザイン時の Windows フォームでの新しい WPF コンテンツの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ElementHost コントロール"
  - "ホスト (Windows フォームの WPF コンテンツを)"
  - "相互運用性, WPF と Windows フォーム"
  - "WPF コンテンツ, ホスト (Windows フォームで)"
  - "WPF ユーザー コントロール, ホスト (Windows フォームで)"
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# チュートリアル: デザイン時の Windows フォームでの新しい WPF コンテンツの作成
このトピックでは、Windows フォーム ベースのアプリケーションで使用する Windows Presentation Foundation \(WPF\) コントロールを作成する方法を示します。  
  
 このチュートリアルでは次のタスクを実行します。  
  
-   プロジェクトを作成する。  
  
-   新しい WPF コントロールを作成する。  
  
-   新しい WPF コントロールを Windows フォームに追加する。  WPF コントロールは <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
## プロジェクトの作成  
 まず、Windows フォーム プロジェクトを作成します。  
  
> [!NOTE]
>  WPF コンテンツをホストする場合は、C\# プロジェクトと Visual Basic プロジェクトのみがサポートされます。  
  
#### プロジェクトを作成するには  
  
-   `HostingWpf` という名前の新しい Windows フォーム アプリケーション プロジェクトを Visual Basic または Visual C\# で作成します。  
  
## 新しい WPF コントロールの作成  
 新しい WPF コントロールを作成し、プロジェクトに追加するのは、プロジェクトへの他の項目の追加と同じくらい簡単です。  Windows フォーム デザイナーは、*複合コントロール*、または*ユーザー コントロール*という名前の特定の種類のコントロールと連携します。  WPF ユーザー コントロールの詳細については、「<xref:System.Windows.Controls.UserControl>」を参照してください。  
  
> [!NOTE]
>  WPF の <xref:System.Windows.Controls.UserControl?displayProperty=fullName> の種類は、同じ <xref:System.Windows.Forms.UserControl?displayProperty=fullName> という名前を持つ、Windows フォームで提供されるユーザー コントロールの種類とは区別されます。  
  
#### 新しい WPF コントロールを作成するには  
  
1.  **ソリューション エクスプローラー**で、新しい **WPF ユーザー コントロール ライブラリ** プロジェクトをソリューションに追加します。  このコントロール ライブラリの既定の名前である `WpfControlLibrary1` を使用します。  既定のコントロールの名前は `UserControl1.xaml` です。  
  
     新しいコントロールを追加すると次の影響があります。  
  
    -   ファイル UserControl1.xaml が追加されます。  
  
    -   ファイル UserControl1.xaml.cs または UserControl1.xaml.vb のいずれかが追加されます。  このファイルには、イベント ハンドラーとその他の実装のための分離コードが含まれています。  
  
    -   WPF アセンブリへの参照が追加されます。  
  
    -   ファイル UserControl1.xaml が [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] で開きます。  
  
2.  デザイン ビューで `UserControl1` が選択されていることを確認します。  詳細については、「[方法 : デザイン画面上で要素を選択して移動する](http://msdn.microsoft.com/ja-jp/54cb70b6-b35b-46e4-a0cc-65189399c474)」を参照してください。  
  
3.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.FrameworkElement.Width%2A> プロパティおよび <xref:System.Windows.FrameworkElement.Height%2A> プロパティの値を `200` に設定します。  
  
4.  **\[ツールボックス\]**から、<xref:System.Windows.Controls.TextBox?displayProperty=fullName> コントロールをデザイン画面にドラッグします。  
  
5.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.Controls.TextBox.Text%2A> プロパティの値を \[ホストするコンテンツ\] に設定します。  
  
    > [!NOTE]
    >  一般的には、もう少し高度な WPF コンテンツをホストしてください。  ここでは、説明する目的でのみ <xref:System.Windows.Controls.TextBox?displayProperty=fullName> コントロールを使用しています。  
  
6.  プロジェクトをビルドします。  
  
## WPF コントロールを Windows フォームに追加する  
 新しい WPF コントロールは、フォームで使用可能な状態です。  Windows フォームは、<xref:System.Windows.Forms.Integration.ElementHost> コントロールを使用して、WPF コンテンツをホストします。  
  
#### WPF コントロールを Windows フォームに追加するには  
  
1.  Windows フォーム デザイナーで `Form1` を開きます。  
  
2.  **ツールボックス**で、**\[WPFUserControlLibrary WPF ユーザー コントロール\]** というラベルの付いたタブを探します。  
  
3.  `UserControl1` のインスタンスをフォームにドラッグします。  
  
    -   WPF コントロールをホストするためのフォームの上に、<xref:System.Windows.Forms.Integration.ElementHost> コントロールが自動的に作成されます。  
  
    -   <xref:System.Windows.Forms.Integration.ElementHost> コントロールに `elementHost1` という名前が付き、**\[プロパティ\]** ウィンドウで <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> プロパティが **UserControl1** に設定されていることが確認できます。  
  
    -   WPF アセンブリへの参照がプロジェクトに追加されます。  
  
    -   `elementHost1` コントロールに、使用可能なホスティング オプションを示すスマート タグ パネルがあります。  
  
4.  **ElementHost タスク**のスマート タグ パネルで、**\[親コンテナーにドッキング\]** を選択します。  
  
5.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
## 次の手順  
 Windows フォームと WPF は異なるテクノロジですが、密接に相互運用するよう設計されています。  アプリケーションに高度な外観と動作を提供するには、次の手順を実行します。  
  
-   WPF ページで Windows フォーム コントロールをホストします。  詳細については、「[チュートリアル: WPF での Windows フォーム コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)」を参照してください。  
  
-   WPF コンテンツに Windows フォームの視覚スタイルを適用します。  詳細については、「[方法 : ハイブリッド アプリケーションで視覚スタイルを有効にする](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)」を参照してください。  
  
-   WPF コンテンツのスタイルを変更します。  詳細については、「[チュートリアル: WPF コンテンツへのスタイルの適用](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [移行と相互運用性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)   
 [WPF コントロールの使用](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)   
 [WPF デザイナー](http://msdn.microsoft.com/ja-jp/c6c65214-8411-4e16-b254-163ed4099c26)