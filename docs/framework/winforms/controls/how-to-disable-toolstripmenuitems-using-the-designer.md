---
title: "方法 : デザイナーを使用して ToolStripMenuItems を無効にする | Microsoft Docs"
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
  - "メニュー項目, 無効化"
  - "メニュー, 無効化 (項目を)"
  - "MenuStrip コントロール [Windows フォーム], 無効化 (メニュー項目をデザイナーで)"
  - "ToolStripMenuItem, 無効化 (デザイナーで)"
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : デザイナーを使用して ToolStripMenuItems を無効にする
ユーザーのアクティビティに応じてメニュー項目を有効および無効にすることによって、ユーザーが実行できるコマンドを制限したり、増やしたりできます。  メニュー項目は作成時に既定で有効になっていますが、これは <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> プロパティを介して調整できます。  このプロパティはデザイン時に **\[プロパティ\]** ウィンドウで操作できます。また、コード内で設定することによりプログラムで操作できます。  詳細については、「[方法 : ToolStripMenuItems を無効にする](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### デザイン時にメニュー項目を無効にするには  
  
1.  フォームのメニュー項目を選択して、<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> プロパティを `false` に設定します。  
  
    > [!TIP]
    >  メニュー内の最初の、つまりトップレベルのメニュー項目を無効にすると、そのメニューに含まれるすべてのメニュー項目が無効になります。  同様に、サブメニュー項目を持つメニュー項目を無効にすると、サブメニュー項目も無効になります。  指定したメニューのすべてのコマンドをユーザーが使用できない場合は、ユーザー インターフェイスを簡潔にするために、メニュー全体を非表示にし、無効にするようにプログラミングすることをお勧めします。  メニューを非表示にしただけの場合、ショートカット キーを使用してメニュー コマンドにアクセスできるため、メニューを非表示にして、さらに無効にする必要があります。  トップレベルのメニュー項目の <xref:System.Windows.Forms.ToolStripItem.Visible%2A> プロパティを `false` に設定してメニュー全体を非表示にします。  
  
## 参照  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStripMenuItem>   
 [方法 : ToolStripMenuItems を非表示にする](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)   
 [MenuStrip コントロールの概要](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)