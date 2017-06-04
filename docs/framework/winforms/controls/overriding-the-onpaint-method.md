---
title: "OnPaint メソッドのオーバーライド | Microsoft Docs"
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
  - "OnPaint メソッド, オーバーライド (Windows フォーム カスタム コントロール内の)"
  - "Paint イベント, 処理 (Windows フォーム カスタム コントロール内の)"
ms.assetid: e9ca2723-0107-4540-bb21-4f5ffb4a9906
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# OnPaint メソッドのオーバーライド
[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] で定義されているイベントをオーバーライドするための基本的な手順はすべてのイベントで同一です。次にこの手順を示します。  
  
#### 継承したイベントをオーバーライドするには  
  
1.  プロテクト メソッド `On`*EventName* をオーバーライドします。  
  
2.  オーバーライドされた `On`*EventName* メソッドから基本クラスの `On`*EventName* メソッドを呼び出します。その結果、登録デリゲートがイベントを受信します。  
  
 すべての Windows フォーム コントロールでは <xref:System.Windows.Forms.Control> から継承する <xref:System.Windows.Forms.Control.Paint> イベントをオーバーライドする必要があるため、<xref:System.Windows.Forms.Control.Paint> イベントについて詳しく説明します。  基本の <xref:System.Windows.Forms.Control> クラスは、派生するコントロールの描画方法については認識せず、<xref:System.Windows.Forms.Control.OnPaint%2A> メソッドでは描画ロジックを提供しません。  <xref:System.Windows.Forms.Control> の <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドは、<xref:System.Windows.Forms.Control.Paint> イベントを登録イベント レシーバーへディスパッチします。  
  
 [方法 : シンプルな Windows フォーム コントロールを開発する](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md) のサンプルで作業すると、<xref:System.Windows.Forms.Control.OnPaint%2A> メソッドのオーバーライド例を確認できます。  このサンプルの一部であるコード片を次に示します。  
  
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
  
 <xref:System.Windows.Forms.PaintEventArgs> クラスには、<xref:System.Windows.Forms.Control.Paint> イベントのデータが格納されます。  次のコードに示すように、**PaintEventArgs** クラスには 2 つのプロパティがあります。  
  
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
  
 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> は、描画される四角形で、<xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> プロパティは、<xref:System.Drawing.Graphics> を参照します。  <xref:System.Drawing?displayProperty=fullName> 名前空間のクラスは、新しい Windows グラフィック ライブラリである [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] の機能へのアクセスを提供するマネージ クラスです。  <xref:System.Drawing.Graphics> オブジェクトには、ポイント、文字列、線、曲線、楕円などのさまざまな形状を描画するメソッドがあります。  
  
 ビジュアル表示を変更する必要がある場合は、コントロールは常に <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドを呼び出します。  呼び出された `OnPaint` メソッドは <xref:System.Windows.Forms.Control.Paint> イベントを発生させます。  
  
## 参照  
 [イベント](../../../../docs/standard/events/index.md)   
 [Windows フォーム コントロールのレンダリング](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)   
 [イベントの定義](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)