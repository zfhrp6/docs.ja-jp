---
title: "プロパティ変更イベント | Microsoft Docs"
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
  - "カスタム コントロール [Windows フォーム], プロパティの変更 (コードを使用)"
  - "プロパティ [Windows フォーム], 変更点"
ms.assetid: 268039ec-5aaa-4d76-b902-acccb036c850
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# プロパティ変更イベント
*PropertyName* というプロパティが変更されたときに、コントロールから通知が送信されるようにするには、*PropertyName*`Changed` というイベントと、イベントを発生させる `On`*PropertyName*`Changed` というメソッドを定義します。  Windows フォームの名前付け規則に従い、プロパティ名の前に *Changed* という単語が付け加えられます。  プロパティ変更イベントの型に関連付けられているイベント デリゲート型は <xref:System.EventHandler> であり、イベント データ型は <xref:System.EventArgs> です。  基本クラスの <xref:System.Windows.Forms.Control> は、<xref:System.Windows.Forms.Control.BackColorChanged>、<xref:System.Windows.Forms.Control.BackgroundImageChanged>、<xref:System.Windows.Forms.Control.FontChanged>、<xref:System.Windows.Forms.Control.LocationChanged> など、多くのプロパティ変更イベントを定義します。  イベントに関する背景情報については、「[イベント](../../../../docs/standard/events/index.md)」と「[Windows フォーム コントロールのイベント](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)」を参照してください。  
  
 プロパティ変更イベントを使用すると、変更に反応するイベント ハンドラーをコントロールのコンシューマーが追加できるため、便利です。  コントロールが発生させたプロパティ変更イベントへこのコントロール自体が応答する必要がある場合には、デリゲートをイベントへアタッチする代わりに、対応する `On`*PropertyName*`Changed` メソッドをオーバーライドします。  通常、プロパティ変更イベントに対して応答するときに、コントロールは他のプロパティを更新するか、コントロールの描画面全体または一部を再描画します。  
  
 <xref:System.Windows.Forms.Control> から継承したプロパティ変更イベントの一部に対して `FlashTrackBar` カスタム コントロールが応答する部分を示す例を次に示します。  サンプル全体については、「[方法 : 進行状況を示す Windows フォーム コントロールを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)」を参照してください。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#2)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#2)]  
  
## 参照  
 [イベント](../../../../docs/standard/events/index.md)   
 [Windows フォーム コントロールのイベント](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)   
 [Windows フォーム コントロールのプロパティ](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)