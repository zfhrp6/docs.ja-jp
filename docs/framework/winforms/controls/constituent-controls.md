---
title: "内在コントロール | Microsoft Docs"
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
  - "内在コントロール"
  - "カスタム コントロール [Windows フォーム], 内在コントロール"
  - "ユーザー コントロール [Windows フォーム], 内在コントロール"
  - "UserControl クラス"
ms.assetid: 5565e720-198b-4bbd-a2bd-c447ba641798
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 内在コントロール
ユーザー コントロールを構成する各コントロールは "*内在コントロール*" と呼ばれます。内在コントロールでは、カスタム グラフィック レンダリングに関する柔軟性が比較的低くなります。  Windows フォーム コントロールはすべて、独自の <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドを使用して独自のレンダリングを処理します。  このメソッドはプロテクトされているため、開発者がアクセスすることはできません。したがって、コントロールが描画されるときに、このメソッドが実行されないようにすることはできません。  ただし、内在コントロールの外観に影響するコードを追加できないという意味ではありません。  追加のレンダリングは、イベント ハンドラーを追加することで実現できます。  たとえば、`MyButton` という名前のボタンを使用して <xref:System.Windows.Forms.UserControl> を編集するとします。  [Button クラス](frlrfSystemWebUIWebControlsButtonClassTopic)によって提供される外観に独自のレンダリングを追加する場合は、次のようなコードをユーザー コントロールに追加します。  
  
```vb  
Public Sub MyPaint(ByVal sender as Object, e as PaintEventArgs) Handles _  
   MyButton.Paint  
   'Additional rendering code goes here  
End Sub  
  
```  
  
```csharp  
// Add the event handler to the button's Paint event.  
MyButton.Paint +=   
   new System.Windows.Forms.PaintEventHandler (this.MyPaint);  
// Create the custom painting method.  
protected void MyPaint (object sender,   
System.Windows.Forms.PaintEventArgs e)  
{  
   // Additional rendering code goes here.  
}  
```  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextBox> など、一部の Windows フォーム コントロールは、直接 Windows によって描画されます。  そのような場合、<xref:System.Windows.Forms.Control.OnPaint%2A> メソッドは呼び出されないため、例に示したコードも呼び出されません。  
  
 このコードは、`MyButton.Paint` イベントが実行されるたびに実行されるメソッドを作成して、コントロールに独自のグラフィカル表示を追加します。  これは `MyButton.OnPaint` の実行を妨げるものではなく、カスタム描画に加えて、ボタンによって通常実行される描画もすべて実行されます。  GDI\+ テクノロジとカスタム レンダリングの詳細については、「[GDI\+ によるグラフィカル イメージの作成](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)」を参照してください。  コントロールに固有の表示を行うための最善の方法は、継承したコントロールを作成して、それに対するカスタム レンダリング コードを記述することです。  詳細については、「[ユーザー描画コントロール](../../../../docs/framework/winforms/controls/user-drawn-controls.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.UserControl>   
 <xref:System.Windows.Forms.Control.OnPaint%2A>   
 [ユーザー描画コントロール](../../../../docs/framework/winforms/controls/user-drawn-controls.md)   
 [方法 : 描画する Graphics オブジェクトを作成する](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)   
 [さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)