---
title: "チュートリアル: デザイン時の Windows フォームでの WPF コンテンツの配置 | Microsoft Docs"
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
  - "相互運用性 [WPF]"
  - "Windows フォーム, 固定およびドッキング (WPF コンテンツを)"
  - "Windows フォーム, 配置 (WPF コンテンツをデザイン時に)"
  - "WPF コンテンツ [Windows フォーム], 配置 (デザイン時に)"
  - "WPF コンテンツ, ホスト (Windows フォームで)"
  - "WPF ユーザー コントロール [Windows フォーム], ホスト (レイアウト パネルで)"
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# チュートリアル: デザイン時の Windows フォームでの WPF コンテンツの配置
このチュートリアルでは、固定やスナップ線などの Windows フォームのレイアウト機能を使用して、Windows Presentation Foundation \(WPF\) コントロールを配置する方法を説明します。  
  
 このチュートリアルでは次のタスクを実行します。  
  
-   プロジェクトを作成する。  
  
-   WPF コントロールを作成する。  
  
-   レイアウト パネルで WPF コントロールをホストする。  
  
-   WPF コントロールを配置するスナップ線を使用する。  
  
-   WPF コントロールを固定してドッキングする。  
  
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
  
-   `ArrangeElementHost` という名前の新しい Windows フォーム アプリケーション プロジェクトを Visual Basic または Visual C\# で作成します。  
  
## WPF コントロールの作成  
 プロジェクトに WPF コントロール型を追加したら、フォーム状に配置できます。  
  
#### WPF コントロールを作成するには  
  
1.  新しい WPF <xref:System.Windows.Controls.UserControl> をプロジェクトに追加します。  コントロール型の既定の名前である `UserControl1.xaml` を使用します。  詳細については、「[チュートリアル: デザイン時の Windows フォームでの新しい WPF コンテンツの作成](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)」を参照してください。  
  
2.  デザイン ビューで `UserControl1` が選択されていることを確認します。  詳細については、「[方法 : デザイン画面上で要素を選択して移動する](http://msdn.microsoft.com/ja-jp/54cb70b6-b35b-46e4-a0cc-65189399c474)」を参照してください。  
  
3.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.FrameworkElement.Width%2A> プロパティおよび <xref:System.Windows.FrameworkElement.Height%2A> プロパティの値を `200` に設定します。  
  
4.  <xref:System.Windows.Controls.Control.Background%2A> プロパティの値を `[青]` に設定します。  
  
5.  プロジェクトをビルドします。  
  
## レイアウト パネルで WPF コントロールをホストする  
 その他の Windows フォーム コントロールを使用するのと同じ方法で、レイアウト パネルで WPF コントロールを使用できます。  
  
#### レイアウト パネルで WPF コントロールをホストするには  
  
1.  Windows フォーム デザイナーで `Form1` を開きます。  
  
2.  **ツールボックス**から、<xref:System.Windows.Forms.TableLayoutPanel> コントロールをフォームにドラッグします。  
  
3.  <xref:System.Windows.Forms.TableLayoutPanel> コントロールのスマート タグ パネルで、**\[最後の行を削除する\]** を選択します。  
  
4.  幅と高さが大きくなるよう <xref:System.Windows.Forms.TableLayoutPanel> コントロールのサイズを変更します。  
  
5.  **\[ツールボックス\]** で `UserControl1` をダブルクリックして、<xref:System.Windows.Forms.TableLayoutPanel> コントロールの最初のセルに `UserControl1` のインスタンスを作成します。  
  
     `UserControl1` のインスタンスは、`elementHost1` という名前の新しい <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。  
  
6.  **\[ツールボックス\]** で `UserControl1` をダブルクリックして、<xref:System.Windows.Forms.TableLayoutPanel> コントロールの 2 番目のセルの別のインスタンスを作成します。  
  
7.  **\[ドキュメント アウトライン\]** ウィンドウで、`tableLayoutPanel1` を選択します。  詳細については、「[Document Outline Window](http://msdn.microsoft.com/ja-jp/9054f2bc-f6f8-4242-9fe0-be71089b12f8)」を参照してください。  
  
8.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.Forms.Control.Padding%2A> プロパティの値を `10、10、10、10` に設定します。  
  
     両方の <xref:System.Windows.Forms.Integration.ElementHost> コントロールが、新しいレイアウトに収まるようにサイズ変更されました。  
  
## WPF コントロールを配置するスナップ線を使用する  
 スナップ線により、フォームのコントロールの配置を簡単に調整できます。  スナップ線を使用して、WPF コントロールも配置することができます。  詳細については、「[チュートリアル : スナップ線を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)」を参照してください。  
  
#### WPF コントロールを配置するスナップ線を使用するには  
  
1.  **ツールボックス**から、`UserControl1` のインスタンスをフォームにドラッグして、<xref:System.Windows.Forms.TableLayoutPanel> コントロールの下の領域に配置します。  
  
     `UserControl1` のインスタンスは、`elementHost3` という名前の新しい <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。  
  
2.  スナップ線を使用して、`elementHost3` の左端を <xref:System.Windows.Forms.TableLayoutPanel> コントロールの左端に揃えます。  
  
3.  スナップ線を使用して、`elementHost3` のサイズを <xref:System.Windows.Forms.TableLayoutPanel> コントロールと同じ幅にします。  
  
4.  コントロール間に中央揃えのスナップ線が表示されるまで`elementHost3` を <xref:System.Windows.Forms.TableLayoutPanel> コントロールの方へ移動します。  
  
5.  **\[プロパティ\]** ウィンドウで、余白プロパティの値を `20、20、20、20` に設定します。  
  
6.  中央揃えのスナップ線がもう一度表示されるまで、`elementHost3` を <xref:System.Windows.Forms.TableLayoutPanel> コントロールから移動します。  中央揃えのスナップ線が、余白 20 を示すようになりました。  
  
7.  左端が `elementHost1` の左端に配置されるまで、`elementHost3` を右に移動します。  
  
8.  右端が `elementHost2` の右端に配置されるまで、`elementHost3` の幅を変更します。  
  
## WPF コントロールの固定およびドッキング  
 フォームでホストされている WPF コントロールは、他の Windows フォーム コントロールと同じ固定とドッキングの動作を持ちます。  
  
#### WPF コントロールを固定してドッキングするには  
  
1.  `elementHost1` を選択します。  
  
2.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.Forms.Control.Anchor%2A> プロパティを **\[Top, Bottom, Left, Right\]** に設定します。  
  
3.  <xref:System.Windows.Forms.TableLayoutPanel> コントロールを大きなサイズに変更します。  
  
     `elementHost1` コントロールがセルを満たすようサイズ変更されます。  
  
4.  `elementHost2` を選択します。  
  
5.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.Forms.Control.Dock%2A> プロパティの値を <xref:System.Windows.Forms.DockStyle> に設定します。  
  
     `elementHost2` コントロールがセルを満たすようサイズ変更されます。  
  
6.  <xref:System.Windows.Forms.TableLayoutPanel> コントロールを選択します。  
  
7.  <xref:System.Windows.Forms.Control.Dock%2A> プロパティの値を <xref:System.Windows.Forms.DockStyle> に設定します。  
  
8.  `elementHost3` を選択します。  
  
9. <xref:System.Windows.Forms.Control.Dock%2A> プロパティの値を <xref:System.Windows.Forms.DockStyle> に設定します。  
  
     `elementHost3` コントロールが、フォームの残りの領域を満たすようサイズ変更されます。  
  
10. フォームのサイズを変更します。  
  
     3 つすべての <xref:System.Windows.Forms.Integration.ElementHost> コントロールのサイズを適切に変更します。  
  
     詳細については、「[方法 : TableLayoutPanel コントロールで子コントロールを固定およびドッキングする](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [方法 : TableLayoutPanel コントロールで子コントロールを固定およびドッキングする](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)   
 [方法 : デザイン時にフォームの端に合わせてコントロールを配置する](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)   
 [チュートリアル : スナップ線を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)   
 [移行と相互運用性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)   
 [WPF コントロールの使用](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)   
 [WPF デザイナー](http://msdn.microsoft.com/ja-jp/c6c65214-8411-4e16-b254-163ed4099c26)