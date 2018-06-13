---
title: Windows フォーム コントロールのレンダリング
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- OnPaintBackground method [Windows Forms], invoking in Windows Forms custom controls
- custom controls [Windows Forms], graphics resources
- custom controls [Windows Forms], invalidation and painting
ms.assetid: aae8e1e6-4786-432b-a15e-f4c44760d302
ms.openlocfilehash: a2d7a02e725e3f8065b80a6b30ea21158be43ea8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541389"
---
# <a name="rendering-a-windows-forms-control"></a>Windows フォーム コントロールのレンダリング
レンダリングは、ユーザーの画面上を示すビジュアル表現を作成するプロセスを指します。 Windows フォームを使用して[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)](新しい Windows グラフィックス ライブラリ) を表示します。 アクセスを提供するマネージ クラス[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]では、<xref:System.Drawing?displayProperty=nameWithType>名前空間とその下位名前空間。  
  
 次の要素は、コントロールのレンダリングに関係しています。  
  
-   基本クラスによって提供される描画機能<xref:System.Windows.Forms.Control?displayProperty=nameWithType>します。  
  
-   重要な要素、[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]グラフィックス ライブラリです。  
  
-   描画領域のジオメトリ。  
  
-   グラフィックス リソースを解放するための手順です。  
  
## <a name="drawing-functionality-provided-by-control"></a>描画コントロールによって提供される機能  
 基本クラス<xref:System.Windows.Forms.Control>を通じて描画機能を提供、<xref:System.Windows.Forms.Control.Paint>イベント。 コントロールを有効に、<xref:System.Windows.Forms.Control.Paint>イベントの表示を更新する必要があるたびにします。 .NET Framework のイベントの詳細については、次を参照してください。[処理とイベントの発生](../../../../docs/standard/events/index.md)です。  
  
 イベント データ クラスを<xref:System.Windows.Forms.Control.Paint>イベント、<xref:System.Windows.Forms.PaintEventArgs>コントロールを描画するために必要なデータを保持、グラフィックス オブジェクトとを描画する領域を表す四角形オブジェクトへのハンドル。 これらのオブジェクトが示すように次のコード フラグメントでは太字です。  
  
```vb  
Public Class PaintEventArgs  
   Inherits EventArgs  
   Implements IDisposable  
  
   Public ReadOnly Property ClipRectangle() As System.Drawing.Rectangle  
      ...  
   End Property  
  
   Public ReadOnly Property Graphics() As System.Drawing.Graphics  
      ...  
   End Property  
   ' Other properties and methods.  
   ...  
End Class  
```  
  
```csharp  
public class PaintEventArgs : EventArgs, IDisposable {  
public System.Drawing.Rectangle ClipRectangle {get;}  
public System.Drawing.Graphics Graphics {get;}  
// Other properties and methods.  
...  
}  
```  
  
 <xref:System.Drawing.Graphics> 描画機能をカプセル化するマネージ クラスの説明で説明した[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]このトピックで後述します。 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>のインスタンス、<xref:System.Drawing.Rectangle>構造体し、コントロールの描画に使用できる利用可能な領域を定義します。 コントロールの開発者が計算できる、<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>を使用して、 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> geometry このトピックの後半の説明」の説明に従って、コントロールのプロパティです。  
  
 コントロールは、オーバーライドすることによってレンダリング ロジックを指定する必要があります、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドから継承する<xref:System.Windows.Forms.Control>です。 <xref:System.Windows.Forms.Control.OnPaint%2A> グラフィックス オブジェクトと経由描画する四角形へのアクセスを取得、<xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A>と<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>のプロパティ、<xref:System.Windows.Forms.PaintEventArgs>にインスタンスが渡されます。  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>メソッド ベースの<xref:System.Windows.Forms.Control>クラスは、描画機能を実装していませんが、単に登録されているイベント デリゲートを呼び出す、<xref:System.Windows.Forms.Control.Paint>イベント。 オーバーライドする場合<xref:System.Windows.Forms.Control.OnPaint%2A>、通常、呼び出す必要があります、<xref:System.Windows.Forms.Control.OnPaint%2A>デリゲートを登録するための基本クラスのメソッドの受信、<xref:System.Windows.Forms.Control.Paint>イベント。 ただし、コントロールの表面全体を描画するには、基本クラスが呼び出す必要がない<xref:System.Windows.Forms.Control.OnPaint%2A>ちらつきが生じます。 オーバーライドする例については、<xref:System.Windows.Forms.Control.OnPaint%2A>イベントを参照してください、[する方法: Windows フォーム コントロールを示しています進行状況を作成する](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)です。  
  
> [!NOTE]
>  呼び出されません<xref:System.Windows.Forms.Control.OnPaint%2A>直接コントロールからその代わりに、起動、<xref:System.Windows.Forms.Control.Invalidate%2A>メソッド (から継承された<xref:System.Windows.Forms.Control>) またはその他の方法を呼び出す<xref:System.Windows.Forms.Control.Invalidate%2A>です。 <xref:System.Windows.Forms.Control.Invalidate%2A>メソッドを呼び出す<xref:System.Windows.Forms.Control.OnPaint%2A>です。 <xref:System.Windows.Forms.Control.Invalidate%2A>と、メソッドはオーバー ロードに渡される引数に基づいて<xref:System.Windows.Forms.Control.Invalidate%2A> `e`、一部またはすべての画面領域のコントロールが再描画します。  
  
 基本<xref:System.Windows.Forms.Control>クラス描画のために役立つもう 1 つのメソッドを定義する —、<xref:System.Windows.Forms.Control.OnPaintBackground%2A>メソッドです。  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> 背景を描画します (これにより図形) ウィンドウの中に、高速にすることが保証と<xref:System.Windows.Forms.Control.OnPaint%2A>と個々 の描画要求を組み合わせて 1 つあるため低速になる場合の詳細を描画<xref:System.Windows.Forms.Control.Paint>に必要なすべての点について説明するイベント再描画されます。 呼び出すことができます、<xref:System.Windows.Forms.Control.OnPaintBackground%2A>など、コントロール用のグラデーションの色の背景を描画する場合。  
  
 中に<xref:System.Windows.Forms.Control.OnPaintBackground%2A>イベントのような用語があり、として表された同じ引数を受け取り、`OnPaint`メソッド、 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> true イベント メソッドではありません。 ない`PaintBackground`イベントと<xref:System.Windows.Forms.Control.OnPaintBackground%2A>イベント デリゲートは呼び出されません。 オーバーライドする場合、<xref:System.Windows.Forms.Control.OnPaintBackground%2A>メソッド、派生クラスに呼び出す必要はありません、<xref:System.Windows.Forms.Control.OnPaintBackground%2A>基底クラスのメソッドです。  
  
## <a name="gdi-basics"></a>GDI + の基礎  
 <xref:System.Drawing.Graphics>クラスには、円、三角形、円弧、楕円などのさまざまな図形を描画するためのメソッドだけでなくテキストを表示するためのメソッドが用意されています。 <xref:System.Drawing?displayProperty=nameWithType>名前空間とその下位名前空間には図形 (円、四角形、円弧、およびその他)、色、フォント、ブラシなどのグラフィック要素をカプセル化するクラスが含まれています。 詳細については[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]を参照してください[マネージ グラフィックス クラスの使用](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)です。 基本[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]にも記載されて、[する方法: Windows フォーム コントロールを示しています進行状況を作成する](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)です。  
  
## <a name="geometry-of-the-drawing-region"></a>描画領域のジオメトリ  
 <xref:System.Windows.Forms.Control.ClientRectangle%2A>コントロールのプロパティの ユーザーの画面で、コントロールに使用可能な四角形の領域を指定するときに、<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>のプロパティ<xref:System.Windows.Forms.PaintEventArgs>が実際に描画される領域を指定します。 (に描画を行うことに注意してください、<xref:System.Windows.Forms.Control.Paint>使用イベント メソッドを<xref:System.Windows.Forms.PaintEventArgs>インスタンスの引数として)。 コントロールは、コントロールの表示の変更の場合と、わずかなセクションと同様に、使用可能な領域の一部のみを描画する必要があります。 ような場合、コントロールの開発者が実際の四角形を描画するを渡すを計算する必要があります<xref:System.Windows.Forms.Control.Invalidate%2A>です。 オーバー ロードされたバージョンの<xref:System.Windows.Forms.Control.Invalidate%2A>を受け取る、<xref:System.Drawing.Rectangle>または<xref:System.Drawing.Region>を引数としてその引数を使用して生成する、<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>プロパティ<xref:System.Windows.Forms.PaintEventArgs>です。  
  
 次のコード フラグメントの表示方法、`FlashTrackBar`カスタム コントロールを描画する四角形の領域を計算します。 `client`変数を表します、<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>プロパティです。 完全なサンプルについてを参照してください。[する方法: Windows フォーム コントロールを示しています進行状況を作成する](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)です。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a>グラフィックス リソースの解放  
 グラフィックス オブジェクトは、システム リソースを使用するために高価です。 このようなオブジェクトのインスタンスは含まれて、<xref:System.Drawing.Graphics?displayProperty=nameWithType>クラスのインスタンスだけでなく<xref:System.Drawing.Brush?displayProperty=nameWithType>、 <xref:System.Drawing.Pen?displayProperty=nameWithType>、およびその他のグラフィックス クラスです。 リリースし、それを必要とする場合にのみ、グラフィックス リソースを作成することが重要であるように使用することが完了したらすぐにします。 実装する型を作成する場合、<xref:System.IDisposable>インターフェイスを呼び出してその<xref:System.IDisposable.Dispose%2A>メソッドが完了したらそれにリソースを解放するためにします。  
  
 次のコード フラグメントの表示方法、`FlashTrackBar`カスタム コントロールを作成し、解放、<xref:System.Drawing.Brush>リソース。 完全なソース コードでは、次を参照してください。[する方法: Windows フォーム コントロールを示しています進行状況を作成する](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)です。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a>関連項目  
 [方法: 進行状況を示す Windows フォーム コントロールを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)
