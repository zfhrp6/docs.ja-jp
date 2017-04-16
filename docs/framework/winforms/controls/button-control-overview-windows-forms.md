---
title: "Button コントロールの概要 (Windows フォーム) | Microsoft Docs"
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
  - "Button"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Button コントロール [Windows フォーム], Button コントロールの概要"
  - "ボタン, ボタンの概要"
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Button コントロールの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.Button> コントロールを使用すると、ユーザーはボタンをクリックしてアクションを実行できます。  このボタンをクリックすると、ボタンを実際に押して離したかのように表示されます。  ユーザーがボタンをクリックするたびに、<xref:System.Windows.Forms.Control.Click> イベント ハンドラーが呼び出されます。  選択したアクションを実行するように、<xref:System.Windows.Forms.Control.Click> イベント ハンドラーにコードを割り当てます。  
  
 ボタン上に表示されるテキストは、<xref:System.Windows.Forms.Control.Text%2A> プロパティに含まれています。  テキストの長さがボタンの幅を超える場合は、次の行に折り返されて表示されます。  ただし、コントロール内に全体の高さが収まらない場合は、テキストがクリッピングされます。  詳細については、「[方法 : Windows フォーム コントロールによって表示されるテキストを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)」を参照してください。  <xref:System.Windows.Forms.Control.Text%2A> プロパティには、アクセス キーを含めることができます。ユーザーは、Alt キーを押しながらアクセス キーを押して、コントロールを "クリック" するのと同じ操作ができます。  詳細については、「[方法 : Windows フォーム コントロールのアクセス キーを作成する](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)」を参照してください。  テキストの表示形式は、<xref:System.Windows.Forms.Control.Font%2A> プロパティと <xref:System.Windows.Forms.ButtonBase.TextAlign%2A> プロパティによって決まります。  
  
 <xref:System.Windows.Forms.ButtonBase.Image%2A> プロパティと <xref:System.Windows.Forms.ButtonBase.ImageList%2A> プロパティを使用すると、<xref:System.Windows.Forms.Button> コントロールでイメージを表示することもできます。  詳細については、「[方法 : Windows フォーム コントロールによって表示されるイメージを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.Button>   
 [方法 : Windows フォームのボタンのクリックに応答する](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)   
 [Windows フォームの Button コントロールを選択する方法](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)   
 [方法 : デザイナーを使用して Windows フォームの Button コントロールを承認ボタンとして指定する](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)   
 [方法 : デザイナーを使用して Windows フォームの Button コントロールをキャンセル ボタンとして指定する](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)   
 [Button コントロール](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)