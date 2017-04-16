---
title: "方法 : デザイン時にフォームの端に合わせてコントロールを配置する | Microsoft Docs"
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
  - "カスタム コントロール [Windows フォーム], ドッキング (デザイナーを使用)"
  - "Dock プロパティ, 配置 (コントロールをデザイナーで)"
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : デザイン時にフォームの端に合わせてコントロールを配置する
<xref:System.Windows.Forms.Control.Dock%2A> を設定することにより、フォームの端に合わせてコントロールを配置できます。  このプロパティは、フォーム内における目的のコントロールの配置位置を指定します。  <xref:System.Windows.Forms.Control.Dock%2A> プロパティには、次の値を設定できます。  
  
|設定|コントロールに対する効果|  
|--------|------------------|  
|<xref:System.Windows.Forms.DockStyle>|フォームの下部にドッキングします。|  
|<xref:System.Windows.Forms.DockStyle>|フォームの余白領域をすべて使用します。|  
|<xref:System.Windows.Forms.DockStyle>|フォームの左側にドッキングします。|  
|<xref:System.Windows.Forms.DockStyle>|ドッキングしません。<xref:System.Windows.Forms.Control.Location%2A> で指定された場所に表示します。|  
|<xref:System.Windows.Forms.DockStyle>|フォームの右側にドッキングします。|  
|<xref:System.Windows.Forms.DockStyle>|フォームの上部にドッキングします。|  
  
 これらの値は、コードでも設定できます。  詳細については、「[方法 : フォームの端に合わせてコントロールを配置する](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### デザイン時にコントロールの Dock プロパティを設定するには  
  
1.  Windows フォーム デザイナーでコントロールを選択します。  
  
2.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.Forms.Control.Dock%2A> プロパティの横にあるドロップダウン ボックスをクリックします。  
  
     設定可能な 6 つの <xref:System.Windows.Forms.Control.Dock%2A> 設定を示すグラフィカル インターフェイスが表示されます。  
  
3.  適切な設定を選択します。  
  
4.  目的のコントロールがこの設定に従ってドッキングされます。  
  
## 参照  
 <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=fullName>   
 [方法 : フォームの端に合わせてコントロールを配置する](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md)   
 [チュートリアル : スナップ線を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)   
 [方法 : Windows フォームにコントロールを固定する](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)   
 [方法 : TableLayoutPanel コントロールで子コントロールを固定およびドッキングする](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)   
 [方法 : FlowLayoutPanel コントロールで子コントロールを固定およびドッキングする](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)   
 [チュートリアル : TableLayoutPanel を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)   
 [チュートリアル : FlowLayoutPanel を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)   
 [デザイン時の Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)