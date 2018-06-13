---
title: Windows フォーム コントロールのイベント
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: 5d51b6a71bffb546c85ba253181453f6deecfa64
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525884"
---
# <a name="events-in-windows-forms-controls"></a>Windows フォーム コントロールのイベント
Windows フォーム コントロールから 60 以上のイベントを継承する<xref:System.Windows.Forms.Control?displayProperty=nameWithType>です。 ように、<xref:System.Windows.Forms.Control.Paint>イベントは、これにより、コントロールを描画するなど、ウィンドウの表示に関連するイベント、<xref:System.Windows.Forms.Control.Resize>と<xref:System.Windows.Forms.Control.Layout>イベント、および低レベルのマウスとキーボード イベント。 一部の低レベルのイベントは、合成<xref:System.Windows.Forms.Control>ようセマンティックなイベントに<xref:System.Windows.Forms.Control.Click>と<xref:System.Windows.Forms.Control.DoubleClick>です。 継承されたイベントに関する詳細については、「<xref:System.Windows.Forms.Control>です。  
  
 継承されたイベントの機能をカスタム コントロールでオーバーライドする必要がある場合、デリゲートを結び付けるのではなく、継承された `On`*EventName* メソッドをオーバーライドします。 .NET Framework でのイベント モデルに詳しくない場合は、「[コンポーネントからのイベントの生成](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [OnPaint メソッドのオーバーライド](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)  
 [ユーザーの入力の処理](../../../../docs/framework/winforms/controls/handling-user-input.md)  
 [イベントの定義](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [イベント](../../../../docs/standard/events/index.md)
