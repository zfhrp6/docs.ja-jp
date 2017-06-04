---
title: "Panel コントロールの概要 (Windows フォーム) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Panel"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "グループ化 (コントロールを), Panel コントロール"
  - "Panel コントロール [Windows フォーム], Panel コントロールの概要"
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Panel コントロールの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.Panel> コントロールを使用すると、他のコントロールと区別できるようにグループ化できます。  通常は、機能別にフォームを細分化するためにパネルを使用します。  たとえば、どの宅配業者を使用するかなどの発送情報を指定する注文フォームを作成できます。  すべてのオプションをパネルにグループ化することにより、論理的な関連性を視覚的に表現できます。  デザイン時に、すべてのコントロールを簡単に移動できます。<xref:System.Windows.Forms.Panel> コントロールを移動すると、そこに含まれるすべてのコントロールも一緒に移動します。  パネルにグループ化されたコントロールは <xref:System.Windows.Forms.Control.Controls%2A> プロパティを使ってアクセスできます。  このプロパティは <xref:System.Windows.Forms.Control> インスタンスのコレクションを返すため、通常は、このように取得したコントロールを特定の型にキャストする必要があります。  
  
## Panel と GroupBox  
 <xref:System.Windows.Forms.Panel> コントロールは <xref:System.Windows.Forms.GroupBox> コントロールに似ていますが、スクロール バーを表示できるのは <xref:System.Windows.Forms.Panel> コントロールだけであり、キャプションを表示できるのは <xref:System.Windows.Forms.GroupBox> コントロールだけです。  
  
## 主要なプロパティ  
 スクロール バーを表示するには、<xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> プロパティを真 \(`true`\) に設定します。  <xref:System.Windows.Forms.Control.BackColor%2A>、<xref:System.Windows.Forms.Control.BackgroundImage%2A>、および<xref:System.Windows.Forms.Panel.BorderStyle%2A> の各プロパティを設定して、パネルの表示形式をカスタマイズすることもできます。  <xref:System.Windows.Forms.Control.BackColor%2A> プロパティおよび <xref:System.Windows.Forms.Control.BackgroundImage%2A> プロパティの詳細については、「[方法 : パネルの背景を設定する](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md)」を参照してください。  <xref:System.Windows.Forms.Panel.BorderStyle%2A> プロパティを使用すると、パネルのアウトラインを非可視の境界線 \(<xref:System.Windows.Forms.BorderStyle>\)、単線 \(<xref:System.Windows.Forms.BorderStyle>\)、または影付き線 \(<xref:System.Windows.Forms.BorderStyle>\) のいずれかに設定できます。  
  
## 参照  
 <xref:System.Windows.Forms.Panel>   
 [GroupBox コントロール](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)   
 [方法 : デザイナーを使用して Windows フォーム Panel コントロールでコントロールをグループ化する](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)   
 [方法 : デザイナーを使って Windows フォーム パネルの背景を設定する](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)