---
title: "方法 : フォームの端に合わせてコントロールを配置する | Microsoft Docs"
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
  - "コントロール [Windows フォーム], 配置 (フォームでの)"
  - "カスタム コントロール [Windows フォーム], ドッキング (コードを使用)"
  - "Dock プロパティ, 配置 (コントロールを、コードを使用)"
  - "フォーム, 配置 (コントロールを)"
ms.assetid: 5994cb59-242b-4e75-bd0e-62879c34d702
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : フォームの端に合わせてコントロールを配置する
<xref:System.Windows.Forms.Control.Dock%2A> プロパティを設定することにより、フォームの端に合わせてコントロールを配置することができます。  このプロパティは、フォーム内のコントロールの場所を指定します。  <xref:System.Windows.Forms.Control.Dock%2A> プロパティには次の値のいずれかを設定できます。  
  
|設定|コントロールへの影響|  
|--------|----------------|  
|<xref:System.Windows.Forms.DockStyle>|フォームの下部にドッキングします。|  
|<xref:System.Windows.Forms.DockStyle>|フォームの残りの全スペースを埋めます。|  
|<xref:System.Windows.Forms.DockStyle>|フォームの左側にドッキングします。|  
|<xref:System.Windows.Forms.DockStyle>|どこにもドッキングせず、その <xref:System.Windows.Forms.Control.Location%2A> プロパティで指定された位置に表示されます。|  
|<xref:System.Windows.Forms.DockStyle>|フォームの右側にドッキングします。|  
|<xref:System.Windows.Forms.DockStyle>|フォームの上部にドッキングします。|  
  
 Visual Studio では、この機能のデザイン時サポートがあります。  
  
### 実行時にコントロールの Dock プロパティを設定するには  
  
1.  コードで <xref:System.Windows.Forms.Control.Dock%2A> プロパティを適切な値に設定します。  
  
    ```vb  
    ' To set the Dock property internally.  
    Me.Dock = DockStyle.Top  
    ' To set the Dock property from another object.  
    UserControl1.Dock = DockStyle.Top  
    ```  
  
    ```csharp  
    // To set the Dock property internally.  
    this.Dock = DockStyle.Top;  
    // To set the Dock property from another object.  
    UserControl1.Dock = DockStyle.Top;  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=fullName>   
 [.NET Framework を使用したカスタム Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)   
 [方法 : FlowLayoutPanel コントロールで子コントロールを固定およびドッキングする](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)   
 [方法 : TableLayoutPanel コントロールで子コントロールを固定およびドッキングする](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)   
 [AutoSize プロパティの概要](../../../../docs/framework/winforms/controls/autosize-property-overview.md)