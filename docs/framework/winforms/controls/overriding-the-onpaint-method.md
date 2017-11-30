---
title: "OnPaint メソッドのオーバーライド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Paint event [Windows Forms], handling in Windows Forms custom control
- OnPaint method [Windows Forms], overriding in Windows Forms custom controls
ms.assetid: e9ca2723-0107-4540-bb21-4f5ffb4a9906
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 41205f7f0ec21e27b97d0b12415fca89ae526552
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="overriding-the-onpaint-method"></a>OnPaint メソッドのオーバーライド
定義されているすべてのイベントをオーバーライドするための基本的な手順、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]が同じであり、次の一覧にまとめます。  
  
#### <a name="to-override-an-inherited-event"></a>継承されたイベントをオーバーライドするには  
  
1.  保護されたオーバーライド`On` *EventName*メソッドです。  
  
2.  呼び出す、 `On` *EventName* 、オーバーライドされた基底クラスのメソッド`On` *EventName*デリゲートを登録するためのメソッドがイベントを受信します。  
  
 <xref:System.Windows.Forms.Control.Paint>イベント詳細についてはここですべての Windows フォーム コントロールをオーバーライドする必要がありますので、<xref:System.Windows.Forms.Control.Paint>から継承するイベント<xref:System.Windows.Forms.Control>です。 基本<xref:System.Windows.Forms.Control>クラスが派生したコントロールが描画されなければならない方法が認識していないの描画ロジックは提供されません、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドです。 <xref:System.Windows.Forms.Control.OnPaint%2A>メソッドの<xref:System.Windows.Forms.Control>は単に、<xref:System.Windows.Forms.Control.Paint>に登録されているイベント レシーバーのイベントです。  
  
 サンプルを使用していた場合[する方法: シンプルな Windows フォーム コントロールを開発](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)、オーバーライドする例を見てきました、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドです。 次のコード フラグメントは、そのサンプルから取得されます。  
  
```vb  
Public Class FirstControl  
   Inherits Control  
  
   Public Sub New()  
   End Sub  
  
   Protected Overrides Sub OnPaint(e As PaintEventArgs)  
      ' Call the OnPaint method of the base class.  
      MyBase.OnPaint(e)  
      ' Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, New SolidBrush(ForeColor), RectangleF.op_Implicit(ClientRectangle))  
   End Sub  
End Class   
```  
  
```csharp  
public class FirstControl : Control{  
   public FirstControl() {}  
   protected override void OnPaint(PaintEventArgs e) {  
      // Call the OnPaint method of the base class.  
      base.OnPaint(e);  
      // Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, new SolidBrush(ForeColor), ClientRectangle);  
   }   
}   
```  
  
 <xref:System.Windows.Forms.PaintEventArgs>クラスにはデータが含まれています、<xref:System.Windows.Forms.Control.Paint>イベント。 次のコードに示すように、2 つのプロパティがあります。  
  
```vb  
Public Class PaintEventArgs  
   Inherits EventArgs  
   ...  
   Public ReadOnly Property ClipRectangle() As System.Drawing.Rectangle  
      ...  
   End Property  
  
   Public ReadOnly Property Graphics() As System.Drawing.Graphics  
      ...  
   End Property   
   ...  
End Class  
```  
  
```csharp  
public class PaintEventArgs : EventArgs {  
...  
    public System.Drawing.Rectangle ClipRectangle {}  
    public System.Drawing.Graphics Graphics {}  
...  
}  
```  
  
 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>四角形を描画するのには、および<xref:System.Windows.Forms.PaintEventArgs.Graphics%2A>プロパティを指す、<xref:System.Drawing.Graphics>オブジェクト。 内のクラス、<xref:System.Drawing?displayProperty=nameWithType>名前空間は、管理の機能へのアクセスを提供するクラス[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]、新しい Windows グラフィックス ライブラリです。 <xref:System.Drawing.Graphics>オブジェクトをポイント、文字列、線、円弧、省略記号、およびその他の多くの図形を描画するメソッドがあります。  
  
 コントロールを呼び出す、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッド ビジュアル表示を変更する必要があるたびにします。 このメソッドを生成させる、<xref:System.Windows.Forms.Control.Paint>イベント。  
  
## <a name="see-also"></a>関連項目  
 [イベント](../../../../docs/standard/events/index.md)  
 [Windows フォーム コントロールのレンダリング](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 [イベントの定義](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
