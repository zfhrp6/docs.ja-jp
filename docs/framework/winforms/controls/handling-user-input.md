---
title: "ユーザーの入力の処理 | Microsoft Docs"
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
  - "カスタム コントロール [Windows フォーム], キーボード イベント (コードを使用)"
  - "カスタム コントロール [Windows フォーム], マウス イベント (コードを使用)"
  - "カスタム コントロール [Windows フォーム], ユーザー入力 (コードを使用)"
ms.assetid: d9b12787-86f6-4022-8e0f-e12d312c4af2
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# ユーザーの入力の処理
このトピックでは、<xref:System.Windows.Forms.Control?displayProperty=fullName> によって提供される主要なキーボード イベントとマウス イベントについて説明します。  イベントを処理する場合、コントロールの作成者はイベントにデリゲートをアタッチする代わりに、`On`*EventName* プロテクト メソッドをオーバーライドする必要があります。  イベントの詳細については、「[コンポーネントからのイベントの生成](../Topic/Raising%20Events%20from%20a%20Component.md)」を参照してください。  
  
> [!NOTE]
>  イベントに関連付けられているデータがない場合には、`On`*EventName* メソッドの引数として <xref:System.EventArgs> 基本クラスのインスタンスが渡されます。  
  
## キーボード イベント  
 コントロールで処理できる一般的なキーボード イベントとして、<xref:System.Windows.Forms.Control.KeyDown>、<xref:System.Windows.Forms.Control.KeyPress>、<xref:System.Windows.Forms.Control.KeyUp> などがあります。  
  
|イベント名|オーバーライドするメソッド|イベントに関する説明|  
|-----------|-------------------|----------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|初めてキーを押すときにだけ発生します。|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|キーを押すたびに発生します。  キーを押したままの状態にすると、オペレーティング システムで定義されているリピート間隔で <xref:System.Windows.Forms.Control.KeyPress> イベントが発生します。|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|キーを離すと発生します。|  
  
> [!NOTE]
>  キーボードからの入力の処理は、上記の表に示すイベントのオーバーライドよりもかなり複雑です。キーボードからの入力の処理については、このトピックでは詳しく説明しません。  詳細については、「[Windows フォームでのユーザー入力](../../../../docs/framework/winforms/user-input-in-windows-forms.md)」を参照してください。  
  
## マウス イベント  
 コントロールで処理できるマウス イベントには、<xref:System.Windows.Forms.Control.MouseDown>、<xref:System.Windows.Forms.Control.MouseEnter>、<xref:System.Windows.Forms.Control.MouseHover>、<xref:System.Windows.Forms.Control.MouseLeave>、<xref:System.Windows.Forms.Control.MouseMove>、および <xref:System.Windows.Forms.Control.MouseUp> などがあります。  
  
|イベント名|オーバーライドするメソッド|イベントに関する説明|  
|-----------|-------------------|----------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|ポインターがコントロール上に置かれている状態でマウス ボタンを押すと発生します。|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|コントロール領域内にポインターが初めて入るときに発生します。|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|ポインターがコントロール上を移動するときに発生します。|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|コントロール領域内からポインターが出るときに発生します。|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|コントロール領域内でポインターを移動すると発生します。|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|ポインターがコントロールに置かれた状態でマウス ボタンを離すか、またはコントロール領域からポインターが出るときに発生します。|  
  
 <xref:System.Windows.Forms.Control.MouseDown> イベントをオーバーライドするコード片の例を次に示します。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 <xref:System.Windows.Forms.Control.MouseMove> イベントをオーバーライドするコード片の例を次に示します。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 <xref:System.Windows.Forms.Control.MouseUp> イベントをオーバーライドするコード片の例を次に示します。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 `FlashTrackBar` のソース コード例全体については、「[方法 : 進行状況を示す Windows フォーム コントロールを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)」を参照してください。  
  
## 参照  
 [Windows フォーム コントロールのイベント](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)   
 [イベントの定義](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)   
 [イベント](../../../../docs/standard/events/index.md)   
 [Windows フォームでのユーザー入力](../../../../docs/framework/winforms/user-input-in-windows-forms.md)