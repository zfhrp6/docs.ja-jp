---
title: ユーザーの入力の処理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user input using code
- custom controls [Windows Forms], keyboard events using code
- custom controls [Windows Forms], mouse events using code
ms.assetid: d9b12787-86f6-4022-8e0f-e12d312c4af2
ms.openlocfilehash: a230611bfbb0a7f21a96de22674377887cc93c2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527801"
---
# <a name="handling-user-input"></a>ユーザーの入力の処理
このトピックの説明によって提供されるメインのキーボードとマウスのイベント<xref:System.Windows.Forms.Control?displayProperty=nameWithType>です。 イベントを処理するときに、コントロール作成者はイベントにデリゲートを結び付けるのではなく、保護された `On`*EventName* メソッドをオーバーライドする必要があります。 イベントのレビューについては、「[コンポーネントからのイベントの生成](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0)」を参照してください。  
  
> [!NOTE]
>  イベント、基底クラスのインスタンスに関連付けられているデータがないかどうかは<xref:System.EventArgs>に渡す引数として渡される、 `On` *EventName*メソッドです。  
  
## <a name="keyboard-events"></a>キーボード イベント  
 コントロールが処理できる共通のキーボード イベントは、 <xref:System.Windows.Forms.Control.KeyDown>、 <xref:System.Windows.Forms.Control.KeyPress>、および<xref:System.Windows.Forms.Control.KeyUp>です。  
  
|イベント名|オーバーライドするメソッド|イベントの説明|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|キーが最初に押されたときにのみ発生します。|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|キーが押されるたびに発生します。 キーを押した場合、<xref:System.Windows.Forms.Control.KeyPress>オペレーティング システムで定義された間隔でイベントが発生します。|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|キーが離されたときに発生します。|  
  
> [!NOTE]
>  キーボード入力の処理は、前の表のイベントをオーバーライドするよりもかなり複雑であり、このトピックでは触れていません。 詳細については、「 [Windows フォームでのユーザー入力](../../../../docs/framework/winforms/user-input-in-windows-forms.md)」を参照してください。  
  
## <a name="mouse-events"></a>マウス イベント  
 コントロールが処理できる、マウス イベントは<xref:System.Windows.Forms.Control.MouseDown>、 <xref:System.Windows.Forms.Control.MouseEnter>、 <xref:System.Windows.Forms.Control.MouseHover>、 <xref:System.Windows.Forms.Control.MouseLeave>、 <xref:System.Windows.Forms.Control.MouseMove>、および<xref:System.Windows.Forms.Control.MouseUp>です。  
  
|イベント名|オーバーライドするメソッド|イベントの説明|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|ポインターがコントロール上にある状態でマウス ボタンが押されると発生します。|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|ポインターがコントロールの領域に初めて入ったときに発生します。|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|ポインターがコントロールの上に置かれたときに発生します。|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|ポインターがコントロールの領域から離れると発生します。|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|ポインターがコントロールの領域内で移動すると発生します。|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|ポインターがコントロールの上にある状態でマウス ボタンが離されるか、ポインターがコントロールの領域から離れると発生します。|  
  
 次のコード フラグメントをオーバーライドする例を示しています、<xref:System.Windows.Forms.Control.MouseDown>イベント。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 次のコード フラグメントをオーバーライドする例を示しています、<xref:System.Windows.Forms.Control.MouseMove>イベント。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 次のコード フラグメントをオーバーライドする例を示しています、<xref:System.Windows.Forms.Control.MouseUp>イベント。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 `FlashTrackBar` サンプルの完全なソース コードについては、「[方法 : 進行状況を示す Windows フォーム コントロールを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [Windows フォーム コントロールのイベント](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [イベントの定義](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [イベント](../../../../docs/standard/events/index.md)  
 [Windows フォームでのユーザー入力](../../../../docs/framework/winforms/user-input-in-windows-forms.md)
