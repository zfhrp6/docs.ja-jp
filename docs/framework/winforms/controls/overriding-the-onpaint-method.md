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
# <a name="overriding-the-onpaint-method"></a><span data-ttu-id="1a5a3-102">OnPaint メソッドのオーバーライド</span><span class="sxs-lookup"><span data-stu-id="1a5a3-102">Overriding the OnPaint Method</span></span>
<span data-ttu-id="1a5a3-103">定義されているすべてのイベントをオーバーライドするための基本的な手順、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]が同じであり、次の一覧にまとめます。</span><span class="sxs-lookup"><span data-stu-id="1a5a3-103">The basic steps for overriding any event defined in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] are identical and are summarized in the following list.</span></span>  
  
#### <a name="to-override-an-inherited-event"></a><span data-ttu-id="1a5a3-104">継承されたイベントをオーバーライドするには</span><span class="sxs-lookup"><span data-stu-id="1a5a3-104">To override an inherited event</span></span>  
  
1.  <span data-ttu-id="1a5a3-105">保護されたオーバーライド`On` *EventName*メソッドです。</span><span class="sxs-lookup"><span data-stu-id="1a5a3-105">Override the protected `On`*EventName* method.</span></span>  
  
2.  <span data-ttu-id="1a5a3-106">呼び出す、 `On` *EventName* 、オーバーライドされた基底クラスのメソッド`On` *EventName*デリゲートを登録するためのメソッドがイベントを受信します。</span><span class="sxs-lookup"><span data-stu-id="1a5a3-106">Call the `On`*EventName* method of the base class from the overridden `On`*EventName* method, so that registered delegates receive the event.</span></span>  
  
 <span data-ttu-id="1a5a3-107"><xref:System.Windows.Forms.Control.Paint>イベント詳細についてはここですべての Windows フォーム コントロールをオーバーライドする必要がありますので、<xref:System.Windows.Forms.Control.Paint>から継承するイベント<xref:System.Windows.Forms.Control>です。</span><span class="sxs-lookup"><span data-stu-id="1a5a3-107">The <xref:System.Windows.Forms.Control.Paint> event is discussed in detail here because every Windows Forms control must override the <xref:System.Windows.Forms.Control.Paint> event that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="1a5a3-108">基本<xref:System.Windows.Forms.Control>クラスが派生したコントロールが描画されなければならない方法が認識していないの描画ロジックは提供されません、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="1a5a3-108">The base <xref:System.Windows.Forms.Control> class does not know how a derived control needs to be drawn and does not provide any painting logic in the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="1a5a3-109"><xref:System.Windows.Forms.Control.OnPaint%2A>メソッドの<xref:System.Windows.Forms.Control>は単に、<xref:System.Windows.Forms.Control.Paint>に登録されているイベント レシーバーのイベントです。</span><span class="sxs-lookup"><span data-stu-id="1a5a3-109">The <xref:System.Windows.Forms.Control.OnPaint%2A> method of <xref:System.Windows.Forms.Control> simply dispatches the <xref:System.Windows.Forms.Control.Paint> event to registered event receivers.</span></span>  
  
 <span data-ttu-id="1a5a3-110">サンプルを使用していた場合[する方法: シンプルな Windows フォーム コントロールを開発](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)、オーバーライドする例を見てきました、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="1a5a3-110">If you worked through the sample in [How to: Develop a Simple Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md), you have seen an example of overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="1a5a3-111">次のコード フラグメントは、そのサンプルから取得されます。</span><span class="sxs-lookup"><span data-stu-id="1a5a3-111">The following code fragment is taken from that sample.</span></span>  
  
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
  
 <span data-ttu-id="1a5a3-112"><xref:System.Windows.Forms.PaintEventArgs>クラスにはデータが含まれています、<xref:System.Windows.Forms.Control.Paint>イベント。</span><span class="sxs-lookup"><span data-stu-id="1a5a3-112">The <xref:System.Windows.Forms.PaintEventArgs> class contains data for the <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="1a5a3-113">次のコードに示すように、2 つのプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="1a5a3-113">It has two properties, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="1a5a3-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>四角形を描画するのには、および<xref:System.Windows.Forms.PaintEventArgs.Graphics%2A>プロパティを指す、<xref:System.Drawing.Graphics>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="1a5a3-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> is the rectangle to be painted, and the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property refers to a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="1a5a3-115">内のクラス、<xref:System.Drawing?displayProperty=nameWithType>名前空間は、管理の機能へのアクセスを提供するクラス[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]、新しい Windows グラフィックス ライブラリです。</span><span class="sxs-lookup"><span data-stu-id="1a5a3-115">The classes in the <xref:System.Drawing?displayProperty=nameWithType> namespace are managed classes that provide access to the functionality of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], the new Windows graphics library.</span></span> <span data-ttu-id="1a5a3-116"><xref:System.Drawing.Graphics>オブジェクトをポイント、文字列、線、円弧、省略記号、およびその他の多くの図形を描画するメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="1a5a3-116">The <xref:System.Drawing.Graphics> object has methods to draw points, strings, lines, arcs, ellipses, and many other shapes.</span></span>  
  
 <span data-ttu-id="1a5a3-117">コントロールを呼び出す、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッド ビジュアル表示を変更する必要があるたびにします。</span><span class="sxs-lookup"><span data-stu-id="1a5a3-117">A control invokes its <xref:System.Windows.Forms.Control.OnPaint%2A> method whenever it needs to change its visual display.</span></span> <span data-ttu-id="1a5a3-118">このメソッドを生成させる、<xref:System.Windows.Forms.Control.Paint>イベント。</span><span class="sxs-lookup"><span data-stu-id="1a5a3-118">This method in turn raises the <xref:System.Windows.Forms.Control.Paint> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a5a3-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="1a5a3-119">See Also</span></span>  
 [<span data-ttu-id="1a5a3-120">イベント</span><span class="sxs-lookup"><span data-stu-id="1a5a3-120">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="1a5a3-121">Windows フォーム コントロールのレンダリング</span><span class="sxs-lookup"><span data-stu-id="1a5a3-121">Rendering a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 [<span data-ttu-id="1a5a3-122">イベントの定義</span><span class="sxs-lookup"><span data-stu-id="1a5a3-122">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
