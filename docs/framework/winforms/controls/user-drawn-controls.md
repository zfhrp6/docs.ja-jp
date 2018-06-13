---
title: ユーザー描画コントロール
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user-drawn
- OnPaint method [Windows Forms]
- user-drawn controls [Windows Forms]
ms.assetid: 034af4b5-457f-4160-a937-22891817faa8
ms.openlocfilehash: 26b4f062c120bf543a5e597fc8c734e8cc336bd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542198"
---
# <a name="user-drawn-controls"></a>ユーザー描画コントロール
.NET Framework では、独自のコントロールを簡単に開発する機能を提供します。 コードによって結合されて標準のコントロールのセットにある、ユーザー コントロールを作成するかを一から独自のコントロールをデザインすることができます。 既存のコントロールから継承されるコントロールを作成し、本質的な機能を追加する継承を使用することもできます。 どのようなアプローチを使用すると、.NET Framework では、任意のコントロールを作成するためのカスタムのグラフィカル インターフェイスを描画する機能を提供します。  
  
 コントロールの描画には、コントロールのコードの実行、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドです。 単一の引数、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドは、<xref:System.Windows.Forms.PaintEventArgs>のすべての情報と、コントロールを表示するために必要な機能を提供するオブジェクト。 <xref:System.Windows.Forms.PaintEventArgs>プロパティとして、コントロールのレンダリングに使用される 2 つのプリンシパル オブジェクトを提供します。  
  
-   <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> オブジェクトの四角形を描画するか、コントロールの部分を表すです。 これには、全体をコントロール、またはコントロールの描画方法に応じて、コントロールの一部です。  
  
-   <xref:System.Drawing.Graphics> オブジェクト - いくつかのグラフィック指向オブジェクトとコントロールを描画するために必要な機能を提供するメソッドをカプセル化します。  
  
 詳細については、<xref:System.Drawing.Graphics>オブジェクトとを使用してを参照してください方法[する方法: 描画グラフィック オブジェクトを作成する](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)です。  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>コントロールの描画または画面上で更新されるたびにイベントが発生し、<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>オブジェクトを表す四角形を描画場所になります。 コントロール全体は、更新する必要がある場合、<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>コントロール全体のサイズを表します。 コントロールの一部は、更新するただし、必要なだけの場合、<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>再描画する必要のある領域のみを表すオブジェクト。 別のコントロールまたはユーザー インターフェイスでのフォーム コントロールの一部が見えない場合、このような場合の例が挙げられます。  
  
 継承する場合、<xref:System.Windows.Forms.Control>クラスがオーバーライドする必要があります、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッド内でのグラフィック表示コードを提供します。 ユーザー コントロールまたは継承されたコントロールをカスタムのグラフィカル インターフェイスを提供する場合もこれを行うオーバーライドすることで、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドです。 次に例を示します。  
  
```vb  
Protected Overrides Sub OnPaint(ByVal e As PaintEventArgs)  
   ' Call the OnPaint method of the base class.  
   MyBase.OnPaint(e)  
  
   ' Declare and instantiate a drawing pen.  
   Using myPen As System.Drawing.Pen = New System.Drawing.Pen(Color.Aqua)  
      ' Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, New Rectangle(Me.Location, Me.Size))  
   End Using
End Sub  
```  
  
```csharp  
protected override void OnPaint(PaintEventArgs e)  
{  
   // Call the OnPaint method of the base class.  
   base.OnPaint(e);  
  
   // Declare and instantiate a new pen.  
   using (System.Drawing.Pen myPen = new System.Drawing.Pen(Color.Aqua))  
   {
      // Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, new Rectangle(this.Location,   
         this.Size));  
   }
}  
```  
  
 前の例では、非常にシンプルなグラフィカルな表現のコントロールを描画する方法を示します。 呼び出す、 <xref:System.Windows.Forms.Control.OnPaint%2A> 、基底クラスのメソッドは、その作成、<xref:System.Drawing.Pen>描くには、対象のオブジェクトし、四角形の楕円を描画が最後にによって決定されます、<xref:System.Windows.Forms.Control.Location%2A>と<xref:System.Windows.Forms.Control.Size%2A>コントロールのです。 ほとんどのレンダリングのコードは、これよりもかなり複雑にすることは、この例の使用、<xref:System.Drawing.Graphics>オブジェクト内に含まれる、<xref:System.Windows.Forms.PaintEventArgs>オブジェクト。 既にグラフィック表示をなど、クラスから継承している場合<xref:System.Windows.Forms.UserControl>または<xref:System.Windows.Forms.Button>と、レンダリングにこの表現を組み込むしたくないの基本クラスを呼び出す必要はありません<xref:System.Windows.Forms.Control.OnPaint%2A>メソッド。  
  
 内のコード、<xref:System.Windows.Forms.Control.OnPaint%2A>およびが更新される、コントロールが最初に描画されるときに、コントロールのメソッドが実行されます。 サイズが変更されるたびに、コントロールが再描画されることを確認するには、コントロールのコンス トラクターに次の行を追加します。  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
>  使用して、<xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType>四角形以外のコントロールを実装するプロパティです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Control.Region%2A>  
 <xref:System.Windows.Forms.ControlStyles>  
 <xref:System.Drawing.Graphics>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <xref:System.Windows.Forms.PaintEventArgs>  
 [方法: 描画する Graphics オブジェクトを作成する](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [内在コントロール](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 [さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
