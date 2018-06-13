---
title: Windows フォーム アプリケーションにおけるユーザー入力
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, user input
ms.assetid: 9d61fa96-70f7-4754-885a-49a4a6316bdb
ms.openlocfilehash: 4f1b96ab53b30d045a315b43abd0e38157e26c07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538364"
---
# <a name="user-input-in-a-windows-forms-application"></a>Windows フォーム アプリケーションにおけるユーザー入力
Windows フォームでは、ユーザー入力が Windows メッセージの形式でアプリケーションに送信されます。 一連のオーバーライド可能なメソッドは、アプリケーションでは、フォーム、これらのメッセージを処理し、レベルを制御します。 これらのメソッドは、マウスとキーボードのメッセージを受信するときに、マウスの情報を取得またはキーボード入力を処理できるイベントが発生します。 多くの場合、Windows フォーム アプリケーションはこれらのイベントを処理するだけですべてのユーザー入力を処理することになります。 それ以外の場合、アプリケーションは、アプリケーション、フォーム、またはコントロールによって受信される前に、特定のメッセージを傍受するためにメッセージを処理する方法の 1 つをオーバーライドする必要があります。  
  
## <a name="mouse-and-keyboard-events"></a>マウスとキーボード イベント  
 すべての Windows フォーム コントロールは、マウスおよびキーボード入力に関連するイベントのセットを継承します。 たとえば、コントロールで処理する、<xref:System.Windows.Forms.Control.KeyPress>イベントが押されたキーの文字コードを確認するか、コントロールが処理できる、<xref:System.Windows.Forms.Control.MouseClick>にマウスの位置をクリックします。 マウスとキーボード イベントの詳細については、次を参照してください。[キーボード イベントを使用した](../../../docs/framework/winforms/using-keyboard-events.md)と[Windows フォームにおけるマウス イベント](../../../docs/framework/winforms/mouse-events-in-windows-forms.md)です。  
  
## <a name="methods-that-process-user-input-messages"></a>ユーザーの入力メッセージを処理するメソッド  
 フォームとコントロールへのアクセスがある、<xref:System.Windows.Forms.IMessageFilter>インターフェイスと一連のメッセージ キューでさまざまなポイントで Windows メッセージを処理するメソッドをオーバーライド可能です。 これらのメソッドがすべて、<xref:System.Windows.Forms.Message>パラメーターで、Windows メッセージの低レベルの詳細をカプセル化します。 実装したり、メッセージを確認し、メッセージが処理またはメッセージ キューでは、次のコンシューマーに渡すこれらのメソッドをオーバーライドすることができます。 次の表は、Windows フォーム内のすべての Windows メッセージを処理するメソッドを表示します。  
  
|メソッド|メモ|  
|------------|-----------|  
|<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A>|このメソッドは、アプリケーション レベル (ポストされたとも呼ばれます) の Windows メッセージをキューに置かれたを受け取ります。|  
|<xref:System.Windows.Forms.Control.PreProcessMessage%2A>|このメソッドが処理される前に、フォームとコントロールのレベルでの Windows メッセージを受け取ります。|  
|<xref:System.Windows.Forms.Control.WndProc%2A>|このメソッドは、フォームとコントロールのレベルでの Windows メッセージを処理します。|  
|<xref:System.Windows.Forms.Control.DefWndProc%2A>|このメソッドは、フォームとコントロールのレベルでの Windows メッセージの既定の処理を実行します。 これは、ウィンドウの最小限の機能を提供します。|  
|<xref:System.Windows.Forms.Control.OnNotifyMessage%2A>|このメソッドは、処理された後に、フォームとコントロールのレベルでメッセージを受け取ります。 <xref:System.Windows.Forms.ControlStyles.EnableNotifyMessage>このメソッドが呼び出されるのスタイル ビットが設定する必要があります。|  
  
 キーボードとマウスのメッセージは、追加のメッセージの種類に固有のオーバーライド可能なメソッドのセットでも処理されます。 詳細については、次を参照してください。[キーボード入力のしくみ](../../../docs/framework/winforms/how-keyboard-input-works.md)と[マウス入力のしくみ Windows フォームで](../../../docs/framework/winforms/how-mouse-input-works-in-windows-forms.md)です。  
  
## <a name="see-also"></a>関連項目  
 [Windows フォームでのユーザー入力](../../../docs/framework/winforms/user-input-in-windows-forms.md)  
 [Windows フォーム アプリケーションにおけるキーボード入力](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [Windows フォーム アプリケーションにおけるマウス入力](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
