---
title: "方法 : セットとして機能する Windows フォーム RadioButton コントロールをグループ化する | Microsoft Docs"
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
  - "コントロール [Windows フォーム], グループ化"
  - "オプション ボタン, グループ化"
  - "RadioButton コントロール [Windows フォーム], グループ化"
  - "Windows フォーム コントロール, グループ化"
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : セットとして機能する Windows フォーム RadioButton コントロールをグループ化する
Windows フォーム <xref:System.Windows.Forms.RadioButton> コントロールは、ユーザーが 2 つ以上の設定から 1 つだけを選択できるようにデザインされています。これらの設定は、プロシージャまたはオブジェクトに対して 1 つだけ割り当てることができます。  たとえば、<xref:System.Windows.Forms.RadioButton> コントロールのグループでは、1 つの注文に対して複数のパッケージ運送業者を表示できますが、使用する運送業者は 1 つだけです。  このため、機能グループの一部であっても、一度に選択できる <xref:System.Windows.Forms.RadioButton> は 1 つだけとなります。  
  
 <xref:System.Windows.Forms.Panel> コントロール、<xref:System.Windows.Forms.GroupBox> コントロール、フォームなどのコンテナーに配置することによって、オプション ボタンをグループ化します。  1 つのフォームに直接追加したすべてのオプション ボタンは、1 つのグループとなります。  異なるグループを追加するには、パネルまたはグループ ボックス内にグループを配置する必要があります。  パネルまたはグループ ボックスの詳細については、「[Panel コントロールの概要](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)」または「[GroupBox コントロールの概要](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)」を参照してください。  
  
### 独立した機能のセットとして RadioButton コントロールをグループ化するには  
  
1.  **\[ツールボックス\]** の **\[Windows フォーム\]** タブから <xref:System.Windows.Forms.GroupBox> コントロールまたは <xref:System.Windows.Forms.Panel> コントロールをフォームにドラッグします。  
  
2.  <xref:System.Windows.Forms.RadioButton> コントロールを <xref:System.Windows.Forms.GroupBox> または <xref:System.Windows.Forms.Panel> コントロールに配置します。  
  
## 参照  
 <xref:System.Windows.Forms.RadioButton>   
 [RadioButton コントロールの概要](../../../../docs/framework/winforms/controls/radiobutton-control-overview-windows-forms.md)   
 [Panel コントロールの概要](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)   
 [GroupBox コントロールの概要](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)   
 [CheckBox コントロールの概要](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)   
 [RadioButton コントロール](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)