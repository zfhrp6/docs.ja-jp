---
title: "CheckBox コントロールの概要 (Windows フォーム) | Microsoft Docs"
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
  - "CheckBox"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "バインド コントロール, チェック ボックス"
  - "チェック ボックス, チェック ボックスの概要"
  - "CheckBox コントロール [Windows フォーム], CheckBox コントロールの概要"
  - "データ バインド, チェック ボックス コントロール"
  - "データ バインド コントロール, チェック ボックス"
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# CheckBox コントロールの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.CheckBox> コントロールでは、特定の条件がオンであるかオフであるかが示されます。  通常は、ユーザーが Yes\/No または True\/False を選択するために使用します。  ユーザーが複数の項目を選択できるように、複数のチェック ボックス コントロールをグループ化することもできます。  
  
 チェック ボックス コントロールは、ユーザーが選択した内容を表示するために使用されるという点で、オプション ボタン コントロールに似ています。  ただし、オプション ボタンの場合、グループ内で選択できるボタンは一度に 1 つだけです。  チェック ボックス コントロールの場合は、チェック ボックスをいくつでも選択できます。  
  
 単純データ連結を使用すると、チェック ボックスをデータベース内の要素に関連付けることができます。  複数のチェック ボックスをグループ化するには、<xref:System.Windows.Forms.GroupBox> コントロールを使用します。  コントロールをグループ化すると、フォーム デザイナー上でまとめて移動できるため、外観を整理したり、ユーザー インターフェイスをデザインしたりするときに便利です。  詳細については、「[Windows フォームでのデータ バインド](../../../../docs/framework/winforms/windows-forms-data-binding.md)」および「[GroupBox コントロール](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)」を参照してください。  
  
 <xref:System.Windows.Forms.CheckBox> コントロールには、<xref:System.Windows.Forms.CheckBox.Checked%2A> および <xref:System.Windows.Forms.CheckBox.CheckState%2A> という 2 つの重要なプロパティがあります。  <xref:System.Windows.Forms.CheckBox.Checked%2A> プロパティは、`true` または `false` を返します。  <xref:System.Windows.Forms.CheckBox.CheckState%2A> プロパティは、<xref:System.Windows.Forms.CheckState> または <xref:System.Windows.Forms.CheckState> を返します。<xref:System.Windows.Forms.CheckBox.ThreeState%2A> プロパティが `true` に設定されている場合、<xref:System.Windows.Forms.CheckBox.CheckState%2A> も <xref:System.Windows.Forms.CheckState> を返すことがあります。  中間状態では、ボックスが淡色表示されてオプションを使用できないことが示されます。  
  
## 参照  
 <xref:System.Windows.Forms.CheckBox>   
 [方法 : Windows フォームの CheckBox コントロールでオプションを設定する](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)   
 [方法 : Windows フォーム CheckBox のクリックに応答する](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)   
 [CheckBox コントロール](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)