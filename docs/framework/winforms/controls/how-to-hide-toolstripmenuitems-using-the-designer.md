---
title: "方法 : デザイナーを使用して ToolStripMenuItems を非表示にする | Microsoft Docs"
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
  - "メニュー項目, 非表示"
  - "MenuStrip コントロール [Windows フォーム], 非表示 (メニュー項目をデザイナーで)"
  - "ToolStripMenuItem, 非表示 (メニュー項目をデザイナーで)"
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : デザイナーを使用して ToolStripMenuItems を非表示にする
メニュー項目を非表示にすると、アプリケーションのユーザー インターフェイス \(UI\) を制御したり、ユーザーが使用するコマンドを制限したりできます。  通常、メニュー項目がすべて使用不可能なメニューは、メニュー全体を非表示にする必要があります。  使用できないメニューを非表示にすることによって、ユーザーの混乱を避けることができます。  さらに、メニューまたはメニュー項目の非表示と無効化の両方が必要となることがあります。これは非表示にしただけでは、ショートカット キーを使用してメニュー コマンドにアクセスできてしまうためです。  メニュー項目を無効にする方法の詳細については、「[方法 : デザイナーを使用して ToolStripMenuItems を無効にする](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### トップレベル メニュー項目とそのサブメニュー項目を非表示にするには  
  
1.  トップレベル メニュー項目を選択し、その <xref:System.Windows.Forms.ToolStripItem.Visible%2A> プロパティまたは <xref:System.Windows.Forms.ToolStripItem.Available%2A> プロパティを `false` に設定します。  
  
     トップレベル メニュー項目を非表示にすると、そのメニュー内のメニュー項目もすべて非表示になります。  <xref:System.Windows.Forms.ToolStripItem.Visible%2A> を `false` に設定した後で、<xref:System.Windows.Forms.MenuStrip> 以外をクリックすると、トップレベル メニュー項目全体とそのサブメニュー項目がフォームに表示されなくなるため、実行時のアクションの結果がわかります。  デザイン時に非表示のトップレベル メニューを表示するには、**\[コンポーネント トレイ\]**、**\[ドキュメント アウトライン\]**、またはプロパティ グリッドの上部にある <xref:System.Windows.Forms.MenuStrip> をクリックします。  
  
> [!NOTE]
>  マージする場合のマルチ ドキュメント インターフェイス \(MDI\) の子メニュー以外に、メニュー全体を非表示にすることはほとんどありません。  
  
### サブメニュー項目を非表示にするには  
  
1.  サブメニュー項目を選択し、その <xref:System.Windows.Forms.ToolStripItem.Visible%2A> プロパティを `false` に設定します。  
  
     サブメニュー項目を非表示にしても、デザイン時にはフォームにはそのまま表示されるため、その後の作業で簡単に選択できます。  実行時には実際に非表示になります。  
  
## 参照  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>   
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>   
 <xref:System.Windows.Forms.ToolStripItem.Available%2A>   
 <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>   
 [MenuStrip コントロールの概要](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)   
 [方法 : デザイナーを使用して ToolStripMenuItems を無効にする](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md)