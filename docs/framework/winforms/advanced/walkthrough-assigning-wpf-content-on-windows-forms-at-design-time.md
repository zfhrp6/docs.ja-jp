---
title: "チュートリアル: デザイン時の Windows フォームでの WPF コンテンツの割り当て | Microsoft Docs"
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
  - "ElementHost コントロール, 割り当て (WPF コンテンツをデザイン時に)"
  - "相互運用性 [WPF]"
  - "Windows フォーム, コンテンツ割り当て"
  - "WPF コンテンツ [Windows フォーム], 割り当て (デザイン時に)"
  - "WPF ユーザー コントロール, ホスト (Windows フォームで)"
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# チュートリアル: デザイン時の Windows フォームでの WPF コンテンツの割り当て
このチュートリアルでは、フォームに表示する Windows Presentation Foundation \(WPF\) コントロール型を選択する方法について説明します。  プロジェクトに含まれている WPF コントロール型であれば、どれでも選択できます。  
  
 このチュートリアルでは次のタスクを実行します。  
  
-   プロジェクトを作成する。  
  
-   WPF コントロール型を作成する。  
  
-   WPF コントロールを選択する。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## プロジェクトの作成  
 まず、Windows フォーム プロジェクトを作成します。  
  
> [!NOTE]
>  WPF コンテンツをホストする場合は、C\# プロジェクトと Visual Basic プロジェクトのみがサポートされます。  
  
#### プロジェクトを作成するには  
  
-   `SelectingWpfContent` という名前の新しい Windows フォーム アプリケーション プロジェクトを Visual Basic または Visual C\# で作成します。  
  
## WPF コントロール型の作成  
 プロジェクトに追加した WPF コントロール型は、さまざまな <xref:System.Windows.Forms.Integration.ElementHost> コントロール内でホストできます。  
  
#### WPF コントロール型を作成するには  
  
1.  新しい WPF <xref:System.Windows.Controls.UserControl> プロジェクトをソリューションに追加します。  コントロール型の既定の名前である `UserControl1.xaml` を使用します。  詳細については、「[チュートリアル: デザイン時の Windows フォームでの新しい WPF コンテンツの作成](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)」を参照してください。  
  
2.  デザイン ビューで `UserControl1` が選択されていることを確認します。  詳細については、「[方法 : デザイン画面上で要素を選択して移動する](http://msdn.microsoft.com/ja-jp/54cb70b6-b35b-46e4-a0cc-65189399c474)」を参照してください。  
  
3.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.FrameworkElement.Width%2A> プロパティおよび <xref:System.Windows.FrameworkElement.Height%2A> プロパティの値を `200` に設定します。  
  
4.  <xref:System.Windows.Controls.TextBox?displayProperty=fullName> コントロールを <xref:System.Windows.Controls.UserControl> に追加し、<xref:System.Windows.Controls.TextBox.Text%2A> プロパティの値を「Hosted Content」に設定します。  
  
5.  WPF <xref:System.Windows.Controls.UserControl> をプロジェクトにもう 1 つ追加します。  コントロール型の既定の名前である `UserControl2.xaml` を使用します。  
  
6.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.FrameworkElement.Width%2A> プロパティおよび <xref:System.Windows.FrameworkElement.Height%2A> プロパティの値を `200` に設定します。  
  
7.  <xref:System.Windows.Controls.TextBox?displayProperty=fullName> コントロールを <xref:System.Windows.Controls.UserControl> に追加し、<xref:System.Windows.Controls.TextBox.Text%2A> プロパティの値を「Hosted Content 2」に設定します。  
  
 **メモ** 一般的には、もう少し高度な WPF コンテンツをホストします。  ここでは、説明する目的でのみ <xref:System.Windows.Controls.TextBox?displayProperty=fullName> コントロールを使用しています。  
  
1.  プロジェクトをビルドします。  
  
## WPF コントロールの選択  
 既にコンテンツをホストしている <xref:System.Windows.Forms.Integration.ElementHost> コントロールに異なる WPF コンテンツを割り当てることができます。  
  
#### WPF コントロールを選択するには  
  
1.  Windows フォーム デザイナーで `Form1` を開きます。  
  
2.  **\[ツールボックス\]** で `UserControl1` をダブルクリックして、フォーム上に `UserControl1` のインスタンスを作成します。  
  
     `UserControl1` のインスタンスは、`elementHost1` という名前の新しい <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。  
  
3.  `elementHost1` のスマート タグ パネルで、**\[ホストするコンテンツの選択\]** ドロップダウン リストを開きます。  
  
4.  ドロップダウン リスト ボックスの **\[UserControl2\]** を選択します。  
  
     これで、`elementHost1` コントロールが `UserControl2` 型のインスタンスをホストするようになりました。  
  
5.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.Forms.Integration.ElementHost.Child%2A> プロパティが **\[UserControl2\]** に設定されていることを確認します。  
  
6.  **\[ツールボックス\]** の **\[WPF 相互運用性\]** グループから、<xref:System.Windows.Forms.Integration.ElementHost> コントロールをフォームにドラッグしします。  
  
     新しい名前として、このコントロールの既定である `elementHost2` を使用します。  
  
7.  `elementHost2` のスマート タグ パネルで、**\[ホストするコンテンツの選択\]** ドロップダウン リストを開きます。  
  
8.  ドロップダウン リストの **\[UserControl1\]** を選択します。  
  
9. これで、`elementHost2` コントロールが `UserControl1` 型のインスタンスをホストするようになりました。  
  
## 参照  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [移行と相互運用性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)   
 [WPF コントロールの使用](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)   
 [WPF デザイナー](http://msdn.microsoft.com/ja-jp/c6c65214-8411-4e16-b254-163ed4099c26)