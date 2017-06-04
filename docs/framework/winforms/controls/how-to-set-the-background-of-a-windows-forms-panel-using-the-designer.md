---
title: "方法 : デザイナーを使って Windows フォーム パネルの背景を設定する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "背景色, Windows フォーム Panel コントロール"
  - "背景イメージ, Windows フォーム Panel コントロール"
  - "色, Windows フォーム Panel コントロール"
  - "Panel コントロール [Windows フォーム], バックグラウンド"
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : デザイナーを使って Windows フォーム パネルの背景を設定する
Windows フォーム <xref:System.Windows.Forms.Panel> コントロールでは、背景色と背景イメージの両方を表示できます。  ラベルやオプション ボタンなど、パネルに含まれるコントロールの背景色を設定するには、<xref:System.Windows.Forms.Control.BackColor%2A> プロパティを使用します。  <xref:System.Windows.Forms.Control.BackgroundImage%2A> プロパティを設定していない場合は、<xref:System.Windows.Forms.Control.BackColor%2A> で選択した色でパネルが完全に塗りつぶされます。  <xref:System.Windows.Forms.Control.BackgroundImage%2A> プロパティを設定している場合は、パネルに含まれるコントロールの背景にイメージが表示されます。  
  
 次の手順では、<xref:System.Windows.Forms.Panel> コントロールが含まれているフォームを持つ **Windows アプリケーション** プロジェクトが必要です。  このプロジェクトの設定の詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」および「[方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### Windows フォーム デザイナーで背景を設定するには  
  
1.  <xref:System.Windows.Forms.Panel> コントロールを選択します。  
  
2.  **\[プロパティ\]** ウィンドウで <xref:System.Windows.Forms.Control.BackColor%2A> プロパティの横にある矢印をクリックして、3 つのタブを含むウィンドウを表示します。  
  
3.  **\[カスタム\]** タブをクリックして、カラー パレットを表示します。  
  
4.  **\[Web\]** タブまたは **\[システム\]** タブをクリックして、定義済みの色名の一覧を表示し、そこから色を選択します。  
  
5.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.Forms.Control.BackgroundImage%2A> プロパティの横にある矢印ボタンをクリックします。  
  
6.  **\[リソースの選択\]** ダイアログ ボックスで、表示するファイルを選択します。  
  
## 参照  
 <xref:System.Windows.Forms.Control.BackColor%2A>   
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>   
 [Panel コントロール](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)   
 [Panel コントロールの概要](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)   
 [方法 : デザイナーを使用して Windows フォーム Panel コントロールでコントロールをグループ化する](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)