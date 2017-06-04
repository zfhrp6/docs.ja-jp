---
title: "NumericUpDown コントロールの概要 (Windows フォーム) | Microsoft Docs"
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
  - "NumericUpDown"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "数値のスピン ボタン コントロール, Windows フォーム"
  - "NumericUpDown コントロール [Windows フォーム], NumericUpDown コントロールの概要"
  - "スピン ボタン コントロール, Windows フォーム"
ms.assetid: cff3cf30-4d46-4381-87df-37bfe83c71c5
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# NumericUpDown コントロールの概要 (Windows フォーム)
<xref:System.Windows.Forms.NumericUpDown> コントロールの外観は、テキスト ボックスと、数値を変更するための矢印で構成されています。  このコントロールでは、固定の数値の選択肢のリストから 1 つの数値を表示および設定します。  ユーザーは、上向きおよび下向きの矢印ボタンをクリックするか、↑キーと↓キーを押すことで、数値を増加または減少できます。また、コントロールのテキスト ボックス部分に数字を直接入力することもできます。  ↑キーをクリックすると最大値を上限に数値が増加し、↓キーをクリックすると最小値を下限に数値が減少します。  
  
 このコントロールは多用途の機能を備えるため、音楽再生アプリケーションのボリューム コントロールを作成する場合などに便利です。  <xref:System.Windows.Forms.NumericUpDown> コントロールは、Windows の多くのコントロール パネル アプリケーションで使用されています。  
  
## 主要なプロパティおよびメソッド  
 コントロールのテキスト ボックスに表示する数値は、16 進数などさまざまな形式を使用できます。  詳細については、「[方法 : Windows フォームの NumericUpDown コントロールの書式を設定する](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)」を参照してください。  コントロールの主なプロパティは、<xref:System.Windows.Forms.NumericUpDown.Value%2A>、<xref:System.Windows.Forms.NumericUpDown.Maximum%2A> \(既定値は 100\)、<xref:System.Windows.Forms.NumericUpDown.Minimum%2A> \(既定値は 0\)、および <xref:System.Windows.Forms.NumericUpDown.Increment%2A> \(既定値は 1\) です。  <xref:System.Windows.Forms.NumericUpDown.Value%2A> プロパティには、コントロールで現在選択している値を設定します。  <xref:System.Windows.Forms.NumericUpDown.Increment%2A> プロパティには、上向きの矢印または下向きの矢印を 1 回クリックするごとに増加または減少される数値を設定します。  コントロールからフォーカスが移動するときに、直接入力した値が最小数値および最大数値と照合され、妥当性が検査されます。  <xref:System.Windows.Forms.NumericUpDown.Accelerations%2A> プロパティを設定すると、ユーザーが連続的に上向きまたは下向きの矢印を押したときに、コントロールの数値が変化する速度を上げることができます。  コントロールの主要なメソッドは、<xref:System.Windows.Forms.NumericUpDown.UpButton%2A> および <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> です。  
  
## 参照  
 <xref:System.Windows.Forms.NumericUpDown>   
 [NumericUpDown コントロール](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)   
 [方法 : Windows フォームの NumericUpDown コントロールの書式を設定する](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)   
 [TextBox コントロール](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)