---
title: "ユーザー描画コントロール | Microsoft Docs"
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
  - "カスタム コントロール [Windows フォーム], ユーザー描画"
  - "OnPaint メソッド [Windows フォーム]"
  - "ユーザー描画コントロール [Windows フォーム]"
ms.assetid: 034af4b5-457f-4160-a937-22891817faa8
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# ユーザー描画コントロール
.NET Framework には、独自のコントロールを簡単に開発する機能が用意されています。  いくつかの標準コントロールをコードで結び付けることにより、ユーザー コントロールを作成できます。または、独自のコントロールを一から設計することもできます。  さらには、継承機能を利用して、既存のコントロールを継承するコントロールを作成し、本来の機能を拡張することもできます。  どのようなアプローチの場合でも、.NET Framework には、作成するコントロールに対してカスタム グラフィカル インターフェイスを描画する機能が用意されています。  
  
 コントロールの描画は、コントロールの <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドのコードを実行することで行われます。  <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドの引数は <xref:System.Windows.Forms.PaintEventArgs> オブジェクトであり、コントロールのレンダリングに必要な情報と機能をすべて提供します。  <xref:System.Windows.Forms.PaintEventArgs> はプロパティとして、コントロールのレンダリングで使用される 2 つの主要なオブジェクトを提供します。  
  
-   <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> オブジェクト \- 描画されるコントロールの一部を表す四角形です。  コントロールの描画方法によって、コントロール全体またはコントロールの一部になります。  
  
-   <xref:System.Drawing.Graphics> オブジェクト \- コントロールを描画するために必要な機能を提供するいくつかのグラフィック指向オブジェクトとメソッドをカプセル化します。  
  
 <xref:System.Drawing.Graphics> オブジェクトとその使い方の詳細については、「[方法 : 描画する Graphics オブジェクトを作成する](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)」を参照してください。  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A> イベントは、コントロールが描画されるか、表示が更新されるたびに発生します。<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> オブジェクトは、コントロールが描画される四角形を表します。  コントロール全体を更新する必要がある場合、<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> オブジェクトはコントロール全体のサイズを表します。  ただし、コントロールの一部だけを更新する必要がある場合、<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> オブジェクトは再描画する必要のある領域だけを表します。  ユーザー インターフェイスで別のコントロールまたはフォームが重なっているためにコントロールの一部が見えない場合などはその一例です。  
  
 <xref:System.Windows.Forms.Control> クラスから継承する場合は、<xref:System.Windows.Forms.Control.OnPaint%2A> メソッドをオーバーライドし、その中にグラフィック レンダリング コードを記述する必要があります。  ユーザー コントロールまたは継承したコントロールにカスタム グラフィカル インターフェイスを提供する場合も、<xref:System.Windows.Forms.Control.OnPaint%2A> メソッドをオーバーライドします。  次に例を示します。  
  
```vb  
Protected Overrides Sub OnPaint(ByVal pe As PaintEventArgs)  
   ' Call the OnPaint method of the base class.  
   MyBase.OnPaint(pe)  
  
   ' Declare and instantiate a drawing pen.  
   Dim myPen As System.Drawing.Pen = New System.Drawing.Pen(Color.Aqua)  
  
   ' Draw an aqua rectangle in the rectangle represented by the control.  
   pe.Graphics.DrawRectangle(myPen, New Rectangle(Me.Location, Me.Size))  
End Sub  
  
```  
  
```csharp  
protected override void OnPaint(PaintEventArgs pe)  
{  
   // Call the OnPaint method of the base class.  
   base.OnPaint(pe);  
  
   // Declare and instantiate a new pen.  
   System.Drawing.Pen myPen = new System.Drawing.Pen(Color.Aqua);  
  
   // Draw an aqua rectangle in the rectangle represented by the control.  
   pe.Graphics.DrawRectangle(myPen, new Rectangle(this.Location,   
      this.Size));  
}  
  
```  
  
 この例は、単純なグラフィカル表示によってコントロールをレンダリングする方法を示しています。  このコードは基本クラスの <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドを呼び出し、描画に使用する <xref:System.Drawing.Pen> オブジェクトを作成して、コントロールの <xref:System.Windows.Forms.Control.Location%2A> と <xref:System.Windows.Forms.Control.Size%2A> で指定された四角形に楕円を描画します。  ほとんどのレンダリング コードはこの例よりもかなり複雑ですが、この例は <xref:System.Windows.Forms.PaintEventArgs> オブジェクトに含まれる <xref:System.Drawing.Graphics> オブジェクトの使用方法を示しています。  <xref:System.Windows.Forms.UserControl> や <xref:System.Windows.Forms.Button> など、既にグラフィカル表示が使用されているクラスから継承し、そのグラフィカル表示をコントロールのレンダリングに使用しない場合は、基本クラスの <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドを呼び出さないでください。  
  
 コントロールの <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドのコードは、コントロールが最初に描画されるとき、および表示が更新されたときに実行されます。  サイズが変更されたときにコントロールが必ず再描画されるようにするには、コントロールのコンストラクターに次の行を追加する必要があります。  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
  
```  
  
> [!NOTE]
>  四角形以外のコントロールを実装するには、<xref:System.Windows.Forms.Control.Region%2A?displayProperty=fullName> プロパティを使用します。  
  
## 参照  
 <xref:System.Windows.Forms.Control.Region%2A>   
 <xref:System.Windows.Forms.ControlStyles>   
 <xref:System.Drawing.Graphics>   
 <xref:System.Windows.Forms.Control.OnPaint%2A>   
 <xref:System.Windows.Forms.PaintEventArgs>   
 [方法 : 描画する Graphics オブジェクトを作成する](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)   
 [内在コントロール](../../../../docs/framework/winforms/controls/constituent-controls.md)   
 [さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)