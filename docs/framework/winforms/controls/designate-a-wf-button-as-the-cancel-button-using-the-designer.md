---
title: "方法 : デザイナーを使用して Windows フォームの Button コントロールをキャンセル ボタンとして指定する | Microsoft Docs"
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
  - "Button コントロール [Windows フォーム], 指定 (キャンセル ボタンとして)"
  - "ボタン, キャンセル ボタン"
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : デザイナーを使用して Windows フォームの Button コントロールをキャンセル ボタンとして指定する
すべての Windows フォーム上で、<xref:System.Windows.Forms.Button> コントロールをキャンセル ボタンとして指定できます。  ユーザーが Esc キーを押すと、フォームの他のコントロールにフォーカスがある場合でも、このキャンセル ボタンがクリックされます。  このようなボタンは、通常、ユーザーがどのアクションにもコミットせずに、すばやく操作を終了できるようにするために設定されます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### キャンセル ボタンを指定するには  
  
1.  ボタンを配置するフォームを選択します。  
  
2.  **\[プロパティ\]** ウィンドウで、フォームの <xref:System.Windows.Forms.Form.CancelButton%2A> プロパティを <xref:System.Windows.Forms.Button> コントロールの名前に設定します。  
  
## 参照  
 <xref:System.Windows.Forms.Form.CancelButton%2A>   
 [Button コントロールの概要](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)   
 [Windows フォームの Button コントロールを選択する方法](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)   
 [方法 : Windows フォームのボタンのクリックに応答する](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)   
 [方法 : デザイナーを使用して Windows フォームの Button コントロールを承認ボタンとして指定する](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)   
 [Button コントロール](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)