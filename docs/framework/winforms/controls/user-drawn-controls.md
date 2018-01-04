---
title: "ユーザー描画コントロール"
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
- custom controls [Windows Forms], user-drawn
- OnPaint method [Windows Forms]
- user-drawn controls [Windows Forms]
ms.assetid: 034af4b5-457f-4160-a937-22891817faa8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e9e486058850616c2304ce0032c35baa855fdf2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="user-drawn-controls"></a><span data-ttu-id="66df5-102">ユーザー描画コントロール</span><span class="sxs-lookup"><span data-stu-id="66df5-102">User-Drawn Controls</span></span>
<span data-ttu-id="66df5-103">.NET Framework では、独自のコントロールを簡単に開発する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="66df5-103">The .NET Framework provides you with the ability to easily develop your own controls.</span></span> <span data-ttu-id="66df5-104">コードによって結合されて標準のコントロールのセットにある、ユーザー コントロールを作成するかを一から独自のコントロールをデザインすることができます。</span><span class="sxs-lookup"><span data-stu-id="66df5-104">You can create a user control, which is a set of standard controls bound together by code, or you can design your own control from the ground up.</span></span> <span data-ttu-id="66df5-105">既存のコントロールから継承されるコントロールを作成し、本質的な機能を追加する継承を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="66df5-105">You can even use inheritance to create a control that inherits from an existing control and add to its inherent functionality.</span></span> <span data-ttu-id="66df5-106">どのようなアプローチを使用すると、.NET Framework では、任意のコントロールを作成するためのカスタムのグラフィカル インターフェイスを描画する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="66df5-106">Whatever approach you use, the .NET Framework provides the functionality to draw a custom graphical interface for any control you create.</span></span>  
  
 <span data-ttu-id="66df5-107">コントロールの描画には、コントロールのコードの実行、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="66df5-107">Painting of a control is accomplished by the execution of code in the control's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="66df5-108">単一の引数、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドは、<xref:System.Windows.Forms.PaintEventArgs>のすべての情報と、コントロールを表示するために必要な機能を提供するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="66df5-108">The single argument of the <xref:System.Windows.Forms.Control.OnPaint%2A> method is a <xref:System.Windows.Forms.PaintEventArgs> object that provides all of the information and functionality required to render your control.</span></span> <span data-ttu-id="66df5-109"><xref:System.Windows.Forms.PaintEventArgs>プロパティとして、コントロールのレンダリングに使用される 2 つのプリンシパル オブジェクトを提供します。</span><span class="sxs-lookup"><span data-stu-id="66df5-109">The <xref:System.Windows.Forms.PaintEventArgs> provides as properties two principal objects that will be used in the rendering of your control:</span></span>  
  
-   <span data-ttu-id="66df5-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>オブジェクトの四角形を描画するか、コントロールの部分を表すです。</span><span class="sxs-lookup"><span data-stu-id="66df5-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object - the rectangle that represents the part of the control that will be drawn.</span></span> <span data-ttu-id="66df5-111">これには、全体をコントロール、またはコントロールの描画方法に応じて、コントロールの一部です。</span><span class="sxs-lookup"><span data-stu-id="66df5-111">This can be the entire control, or part of the control depending on how the control is drawn.</span></span>  
  
-   <span data-ttu-id="66df5-112"><xref:System.Drawing.Graphics>オブジェクト - いくつかのグラフィック指向オブジェクトとコントロールを描画するために必要な機能を提供するメソッドをカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="66df5-112"><xref:System.Drawing.Graphics> object - encapsulates several graphics-oriented objects and methods that provide the functionality necessary to draw your control.</span></span>  
  
 <span data-ttu-id="66df5-113">詳細については、<xref:System.Drawing.Graphics>オブジェクトとを使用してを参照してください方法[する方法: 描画グラフィック オブジェクトを作成する](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)です。</span><span class="sxs-lookup"><span data-stu-id="66df5-113">For more information on the <xref:System.Drawing.Graphics> object and how to use it, see [How to: Create Graphics Objects for Drawing](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
 <span data-ttu-id="66df5-114"><xref:System.Windows.Forms.Control.OnPaint%2A>コントロールの描画または画面上で更新されるたびにイベントが発生し、<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>オブジェクトを表す四角形を描画場所になります。</span><span class="sxs-lookup"><span data-stu-id="66df5-114">The <xref:System.Windows.Forms.Control.OnPaint%2A> event is fired whenever the control is drawn or refreshed on the screen, and the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object represents the rectangle in which painting will take place.</span></span> <span data-ttu-id="66df5-115">コントロール全体は、更新する必要がある場合、<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>コントロール全体のサイズを表します。</span><span class="sxs-lookup"><span data-stu-id="66df5-115">If the entire control needs to be refreshed, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> will represent the size of the entire control.</span></span> <span data-ttu-id="66df5-116">コントロールの一部は、更新するただし、必要なだけの場合、<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>再描画する必要のある領域のみを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="66df5-116">If only part of the control needs to be refreshed, however, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object will represent only the region that needs to be redrawn.</span></span> <span data-ttu-id="66df5-117">別のコントロールまたはユーザー インターフェイスでのフォーム コントロールの一部が見えない場合、このような場合の例が挙げられます。</span><span class="sxs-lookup"><span data-stu-id="66df5-117">An example of such a case would be when a control was partially obscured by another control or form in the user interface.</span></span>  
  
 <span data-ttu-id="66df5-118">継承する場合、<xref:System.Windows.Forms.Control>クラスがオーバーライドする必要があります、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッド内でのグラフィック表示コードを提供します。</span><span class="sxs-lookup"><span data-stu-id="66df5-118">When inheriting from the <xref:System.Windows.Forms.Control> class, you must override the <xref:System.Windows.Forms.Control.OnPaint%2A> method and provide graphics-rendering code within.</span></span> <span data-ttu-id="66df5-119">ユーザー コントロールまたは継承されたコントロールをカスタムのグラフィカル インターフェイスを提供する場合もこれを行うオーバーライドすることで、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="66df5-119">If you want to provide a custom graphical interface to a user control or an inherited control, you can also do so by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="66df5-120">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="66df5-120">An example is shown below:</span></span>  
  
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
  
 <span data-ttu-id="66df5-121">前の例では、非常にシンプルなグラフィカルな表現のコントロールを描画する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="66df5-121">The preceding example demonstrates how to render a control with a very simple graphical representation.</span></span> <span data-ttu-id="66df5-122">呼び出す、 <xref:System.Windows.Forms.Control.OnPaint%2A> 、基底クラスのメソッドは、その作成、<xref:System.Drawing.Pen>描くには、対象のオブジェクトし、四角形の楕円を描画が最後にによって決定されます、<xref:System.Windows.Forms.Control.Location%2A>と<xref:System.Windows.Forms.Control.Size%2A>コントロールのです。</span><span class="sxs-lookup"><span data-stu-id="66df5-122">It calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class, it creates a <xref:System.Drawing.Pen> object with which to draw, and finally draws an ellipse in the rectangle determined by the <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Size%2A> of the control.</span></span> <span data-ttu-id="66df5-123">ほとんどのレンダリングのコードは、これよりもかなり複雑にすることは、この例の使用、<xref:System.Drawing.Graphics>オブジェクト内に含まれる、<xref:System.Windows.Forms.PaintEventArgs>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="66df5-123">Although most rendering code will be significantly more complicated than this, this example demonstrates the use of the <xref:System.Drawing.Graphics> object contained within the <xref:System.Windows.Forms.PaintEventArgs> object.</span></span> <span data-ttu-id="66df5-124">既にグラフィック表示をなど、クラスから継承している場合<xref:System.Windows.Forms.UserControl>または<xref:System.Windows.Forms.Button>と、レンダリングにこの表現を組み込むしたくないの基本クラスを呼び出す必要はありません<xref:System.Windows.Forms.Control.OnPaint%2A>メソッド。</span><span class="sxs-lookup"><span data-stu-id="66df5-124">Note that if you are inheriting from a class that already has a graphical representation, such as <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Button>, and you do not wish to incorporate that representation into your rendering, you should not call your base class's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
 <span data-ttu-id="66df5-125">内のコード、<xref:System.Windows.Forms.Control.OnPaint%2A>およびが更新される、コントロールが最初に描画されるときに、コントロールのメソッドが実行されます。</span><span class="sxs-lookup"><span data-stu-id="66df5-125">The code in the <xref:System.Windows.Forms.Control.OnPaint%2A> method of your control will execute when the control is first drawn, and whenever it is refreshed.</span></span> <span data-ttu-id="66df5-126">サイズが変更されるたびに、コントロールが再描画されることを確認するには、コントロールのコンス トラクターに次の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="66df5-126">To ensure that your control is redrawn every time it is resized, add the following line to the constructor of your control:</span></span>  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
>  <span data-ttu-id="66df5-127">使用して、<xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType>四角形以外のコントロールを実装するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="66df5-127">Use the <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> property to implement a non-rectangular control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66df5-128">参照</span><span class="sxs-lookup"><span data-stu-id="66df5-128">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Region%2A>  
 <xref:System.Windows.Forms.ControlStyles>  
 <xref:System.Drawing.Graphics>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <xref:System.Windows.Forms.PaintEventArgs>  
 [<span data-ttu-id="66df5-129">方法: 描画する Graphics オブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="66df5-129">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="66df5-130">内在コントロール</span><span class="sxs-lookup"><span data-stu-id="66df5-130">Constituent Controls</span></span>](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 [<span data-ttu-id="66df5-131">さまざまなカスタム コントロール</span><span class="sxs-lookup"><span data-stu-id="66df5-131">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
