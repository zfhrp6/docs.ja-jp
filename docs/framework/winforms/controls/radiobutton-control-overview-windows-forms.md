---
title: "RadioButton コントロールの概要 (Windows フォーム) | Microsoft Docs"
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
  - "RadioButton"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "オプション ボタン, オプション ボタンの概要"
  - "オプション ボタン, 判断 (状態を)"
  - "RadioButton コントロール [Windows フォーム], RadioButton コントロールの概要"
  - "RadioButton コントロール [Windows フォーム], 判断 (状態を)"
ms.assetid: cd11f0c2-d098-4022-adf9-1455bc166a13
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# RadioButton コントロールの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.RadioButton> コントロールを使用すると、相互に排他的な選択項目を 2 つ以上含むセットを設定できます。  オプション ボタンとチェック ボックスは機能が似ているように見えますが、重要な違いがあります。ユーザーがオプション ボタンをクリックした場合、同じグループ内の他のオプション ボタンと同時にオンにすることはできません。  これに対し、チェック ボックスはいくつでもオンにできます。  オプション ボタン グループは、"内部で 1 つだけ選択できる選択項目のセット" と定義されます。  
  
## コントロールの使用  
 <xref:System.Windows.Forms.RadioButton> コントロールをクリックすると、<xref:System.Windows.Forms.RadioButton.Checked%2A> プロパティが `true` に設定され、<xref:System.Windows.Forms.Control.Click> イベント ハンドラーが呼び出されます。  <xref:System.Windows.Forms.RadioButton.CheckedChanged> イベントは、<xref:System.Windows.Forms.RadioButton.Checked%2A> プロパティの値が変更されるときに発生します。  <xref:System.Windows.Forms.RadioButton.AutoCheck%2A> プロパティを `true` \(既定\) に設定した場合、オプション ボタンをクリックすると、グループ内の他のすべての項目が自動的にオフにされます。  選択したオプション ボタンが有効なオプションであることを確認するための検証コードを使用する場合、通常はこのプロパティを `false` に設定します。  コントロールに表示されるテキストは、<xref:System.Windows.Forms.Control.Text%2A> プロパティによって設定します。このプロパティには、アクセス キー ショートカットが含まれることがあります。  ユーザーは、Alt キーを押しながらアクセス キーを押すことによって、コントロールを "クリック" した場合と同様の操作ができます。  詳細については、「[方法 : Windows フォーム コントロールのアクセス キーを作成する](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)」および「[方法 : Windows フォーム コントロールによって表示されるテキストを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)」を参照してください。  
  
 <xref:System.Windows.Forms.RadioButton> コントロールは、コマンド ボタンのように表示できます。<xref:System.Windows.Forms.RadioButton.Appearance%2A> プロパティが <xref:System.Windows.Forms.Appearance> に設定されている場合、選択されている状態では押し下げられているように表示されます。  <xref:System.Windows.Forms.ButtonBase.Image%2A> プロパティと <xref:System.Windows.Forms.ButtonBase.ImageList%2A> プロパティを使用すると、オプション ボタンでイメージを表示することもできます。  詳細については、「[方法 : Windows フォーム コントロールによって表示されるイメージを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.RadioButton>   
 [Panel コントロールの概要](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)   
 [GroupBox コントロールの概要](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)   
 [CheckBox コントロールの概要](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)   
 [方法 : Windows フォーム コントロールのアクセス キーを作成する](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)   
 [方法 : Windows フォーム コントロールによって表示されるテキストを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)   
 [方法 : セットとして機能する Windows フォーム RadioButton コントロールをグループ化する](../../../../docs/framework/winforms/controls/how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)   
 [RadioButton コントロール](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)