---
title: "方法 : デザイン時に ElementHost コントロールをコピーして貼り付ける | Microsoft Docs"
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
  - "ElementHost コントロール, コピーと貼り付け (デザイン時に)"
  - "相互運用性 [WPF]"
  - "Windows フォーム, コンテンツのコピーと貼り付け"
  - "WPF ユーザー コントロール, ホスト (Windows フォームで)"
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : デザイン時に ElementHost コントロールをコピーして貼り付ける
ここでは、Windows Presentation Foundation \(WPF\) コントロールを Windows フォームにコピーする方法について説明します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### デザイン時に ElementHost コントロールをコピーして貼り付けるには  
  
1.  新しい WPF <xref:System.Windows.Controls.UserControl> を Windows フォーム プロジェクトに追加します。  名前はこのコントロール型の既定である `UserControl1.xaml` を使用します。  詳細については、「[チュートリアル: デザイン時の Windows フォームでの新しい WPF コンテンツの作成](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)」を参照してください。  
  
2.  **\[プロパティ\]** ウィンドウで、`UserControl1` の <xref:System.Windows.FrameworkElement.Width%2A> プロパティおよび <xref:System.Windows.FrameworkElement.Height%2A> プロパティの値を `200` に設定します。  
  
3.  <xref:System.Windows.Controls.Control.Background%2A> プロパティの値を `Blue` に設定します。  
  
4.  プロジェクトをビルドします。  
  
5.  Windows フォーム デザイナーで `Form1` を開きます。  
  
6.  **\[ツールボックス\]** から `UserControl1` のインスタンスをフォームにドラッグします。  
  
     `UserControl1` のインスタンスは、`elementHost1` という名前の <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。  
  
7.  `elementHost1` が選択された状態で Ctrl キーを押しながら C キーを押して、クリップボードにコピーします。  
  
8.  Ctrl キーを押しながら V キーを押して、コピーしたコントロールをフォームに貼り付けます。  
  
     `elementHost2` という名前の新しい <xref:System.Windows.Forms.Integration.ElementHost> コントロールがフォームに作成されます。  
  
## 参照  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [チュートリアル : ElementHost コントロールの別の Windows フォームへのコピーと貼り付け](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)   
 [移行と相互運用性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)   
 [WPF コントロールの使用](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)   
 [WPF デザイナー](http://msdn.microsoft.com/ja-jp/c6c65214-8411-4e16-b254-163ed4099c26)