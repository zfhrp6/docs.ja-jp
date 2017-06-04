---
title: "方法 :ピクセルをコピーして Windows フォームのちらつきを低減する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ビット ブロック転送"
  - "bitblt"
  - "ちらつき"
  - "ちらつき, 低減 (Windows フォーム内の)"
  - "グラフィックス, コピー"
  - "グラフィックス, 低減 (ちらつきを)"
  - "ピクセル, コピー"
ms.assetid: 33b76910-13a3-4521-be98-5c097341ae3b
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 :ピクセルをコピーして Windows フォームのちらつきを低減する
単純なグラフィックをアニメーション化する場合、ちらつきやその他の望ましくない視覚効果が生じる可能性があります。  この問題を抑制する 1 つの方法は、グラフィックに対して "BitBlt" プロセスを使用することです。  BitBlt とは、転送元のピクセルの四角形から転送先のピクセルの四角形へカラー データを "ビット ブロック転送" することです。  
  
 Windows フォームでは、BitBlt は <xref:System.Drawing.Graphics> クラスの <xref:System.Drawing.Graphics.CopyFromScreen%2A> メソッドを使用して行われます。  メソッドの各パラメーターに、転送元と転送先 \(頂点\)、コピーする領域のサイズ、および新しい形状の描画に使用するグラフィックス オブジェクトを指定します。  
  
 次の例では、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラー内でフォーム上に形状を描画します。  次に、<xref:System.Drawing.Graphics.CopyFromScreen%2A> メソッドを使用してその形状を複製します。  
  
> [!NOTE]
>  フォームの <xref:System.Windows.Forms.Control.DoubleBuffered%2A> プロパティを `true` に設定すると、<xref:System.Windows.Forms.Control.Paint> イベント内にあるグラフィックス ベースのコードがダブル バッファー化されます。  以下のコードを使用しても明確なパフォーマンスの向上は見られませんが、より複雑なグラフィックス操作コードを使用する場合には、この設定が重要になります。  
  
## 使用例  
  
```vb  
Private Sub Form1_Paint(ByVal sender As Object, ByVal e As _  
    System.Windows.Forms.PaintEventArgs) Handles MyBase.Paint  
    ' Draw a circle with a bar on top.  
        e.Graphics.FillEllipse(Brushes.DarkBlue, New Rectangle _  
             (10, 10, 60, 60))  
        e.Graphics.FillRectangle(Brushes.Khaki, New Rectangle _  
             (20, 30, 60, 10))  
    ' Copy the graphic to a new location.  
        e.Graphics.CopyFromScreen(New Point(10, 10), New Point _  
             (100, 100), New Size(70, 70))  
End Sub  
  
```  
  
```csharp  
private void Form1_Paint(System.Object sender,  
    System.Windows.Forms.PaintEventArgs e)  
        {  
        e.Graphics.FillEllipse(Brushes.DarkBlue, new  
            Rectangle(10,10,60,60));  
        e.Graphics.FillRectangle(Brushes.Khaki, new  
            Rectangle(20,30,60,10));  
        e.Graphics.CopyFromScreen(new Point(10, 10), new Point(100, 100),   
            new Size(70, 70));  
}  
```  
  
## コードのコンパイル  
 上のコードは、フォームの再描画時にグラフィックスが保持されるように、フォームの <xref:System.Windows.Forms.Control.Paint> イベント ハンドラー内で実行されます。  したがって、<xref:System.Windows.Forms.Form.Load> イベント ハンドラー内ではグラフィックス関連のメソッドを呼び出さないようにします。呼び出すと、フォームをサイズ変更したり、フォームが他のフォームによって隠されたりしている場合に、内容が再描画されなくなります。  
  
## 参照  
 <xref:System.Drawing.CopyPixelOperation>   
 <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=fullName>   
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [ペンを使用した直線と図形の描画](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)