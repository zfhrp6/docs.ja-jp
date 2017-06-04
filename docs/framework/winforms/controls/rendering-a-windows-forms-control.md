---
title: "Windows フォーム コントロールのレンダリング | Microsoft Docs"
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
  - "カスタム コントロール [Windows フォーム], グラフィックス リソース"
  - "カスタム コントロール [Windows フォーム], 無効化と描画"
  - "カスタム コントロール [Windows フォーム], 描画"
  - "OnPaintBackground メソッド, 呼び出し (Windows フォーム カスタム コントロールで)"
ms.assetid: aae8e1e6-4786-432b-a15e-f4c44760d302
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Windows フォーム コントロールのレンダリング
レンダリングとは、ユーザーの画面にコントロールのビジュアル表現を作成する操作です。  Windows フォームは、[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] \(新しい Windows グラフィックス ライブラリ\) を使用してレンダリングを行います。  [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] へのアクセスを提供するマネージ クラスは、<xref:System.Drawing?displayProperty=fullName> 名前空間とその下位名前空間に格納されています。  
  
 コントロールのレンダリングに使用される要素を次に示します。  
  
-   <xref:System.Windows.Forms.Control?displayProperty=fullName> 基本クラスによって提供される描画機能  
  
-   [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] グラフィックス ライブラリの必須要素。  
  
-   描画領域のジオメトリ  
  
-   グラフィック リソースを解放するためのプロシージャ  
  
## コントロールの描画機能  
 <xref:System.Windows.Forms.Control> 基本クラスは、その <xref:System.Windows.Forms.Control.Paint> イベントを介して描画機能を提供します。  コントロールの表示を更新する必要がある場合は、このコントロールが常に <xref:System.Windows.Forms.Control.Paint> イベントを発生させます。  .NET Framework のイベントの詳細については、「[イベントの処理と発生](../../../../docs/standard/events/index.md)」を参照してください。  
  
 <xref:System.Windows.Forms.Control.Paint> イベントのイベント データ クラスである <xref:System.Windows.Forms.PaintEventArgs> は、コントロールの描画に必要なデータ、つまりグラフィックス オブジェクト、および描画する領域を表す四角形オブジェクトへのハンドルを維持します。  次のコード片では、これらのオブジェクトを太字で示します。  
  
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
  
 <xref:System.Drawing.Graphics> は描画機能をカプセル化するマネージ クラスです。このクラスについては、このトピックの [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] のセクションで説明します。  <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> は <xref:System.Drawing.Rectangle> 構造体のインスタンスです。コントロールを描画するために使用できる領域を定義します。  コントロール開発者は、コントロールの <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> プロパティを使用して <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> を算出できます。これについては、このトピックの後半のジオメトリのセクションで説明します。  
  
 コントロールは、<xref:System.Windows.Forms.Control> から継承する <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドをオーバーライドすることによって、レンダリング ロジックを提供する必要があります。  <xref:System.Windows.Forms.Control.OnPaint%2A> は、グラフィックス オブジェクトと四角形へアクセスし、渡された <xref:System.Windows.Forms.PaintEventArgs> インスタンスの <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> プロパティと <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> プロパティを使用してこれらのオブジェクトを描画します。  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 <xref:System.Windows.Forms.Control> 基本クラスの <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドは描画機能を実装しません。このメソッドは、<xref:System.Windows.Forms.Control.Paint> イベントに登録されているイベント デリゲートを呼び出すだけです。  <xref:System.Windows.Forms.Control.OnPaint%2A> をオーバーライドする場合は、登録デリゲートが <xref:System.Windows.Forms.Control.Paint> イベントを受信できるように、常に基本クラスの <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドを呼び出す必要があります。  ただし描画面全体を描画するコントロールでは、基本クラスの <xref:System.Windows.Forms.Control.OnPaint%2A> を呼び出すとちらつきが発生するため、これを呼び出さないようにします。  <xref:System.Windows.Forms.Control.OnPaint%2A> イベントのオーバーライドの例については、「[方法 : 進行状況を示す Windows フォーム コントロールを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)」を参照してください。  
  
> [!NOTE]
>  コントロールから直接 <xref:System.Windows.Forms.Control.OnPaint%2A> を呼び出さないでください。<xref:System.Windows.Forms.Control> から継承された <xref:System.Windows.Forms.Control.Invalidate%2A> メソッドを呼び出すか、または <xref:System.Windows.Forms.Control.Invalidate%2A> を呼び出す他のメソッドを呼び出してください。  <xref:System.Windows.Forms.Control.Invalidate%2A> メソッドが <xref:System.Windows.Forms.Control.OnPaint%2A> を呼び出します。  <xref:System.Windows.Forms.Control.Invalidate%2A> メソッドはオーバーロードされます。また、<xref:System.Windows.Forms.Control.Invalidate%2A> メソッドに渡される引数によって、コントロールの描画領域が画面領域の全体または一部のどちらであるかが決まります。  
  
 <xref:System.Windows.Forms.Control> 基本クラスは、描画に役立つもう 1 つのメソッドである <xref:System.Windows.Forms.Control.OnPaintBackground%2A> メソッドを定義します。  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> はウィンドウの背景 \(ウィンドウの形状\) を描画するメソッドであり、高速処理が保証されています。一方、<xref:System.Windows.Forms.Control.OnPaint%2A> は詳細を描画するメソッドです。個々の描画要求が 1 つの <xref:System.Windows.Forms.Control.Paint> イベントに結合されますが、このイベントは再描画する必要のある領域をすべてカバーしているため、このメソッドの処理には時間がかかることがあります。  たとえば、コントロールのグラデーション色の背景を描画するには、<xref:System.Windows.Forms.Control.OnPaintBackground%2A> を呼び出します。  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> にはイベントに似た命名規則があり、`OnPaint` メソッドと同じ引数を受け取ります。ただし、<xref:System.Windows.Forms.Control.OnPaintBackground%2A> は厳密にはイベント メソッドではありません。  `PaintBackground` というイベントは存在せず、<xref:System.Windows.Forms.Control.OnPaintBackground%2A> はイベント デリゲートを呼び出しません。  <xref:System.Windows.Forms.Control.OnPaintBackground%2A> メソッドをオーバーライドする場合は、派生クラスがその基本クラスの <xref:System.Windows.Forms.Control.OnPaintBackground%2A> メソッドを呼び出す必要はありません。  
  
## GDI\+ の基本事項  
 <xref:System.Drawing.Graphics> クラスには、テキストを表示するメソッドと同様に円形、三角形、円弧、楕円形などのさまざまな形状を描画するメソッドがあります。  形状 \(円形、四角形、円弧など\)、色、フォント、ブラシなどのグラフィックス要素をカプセル化したクラスは、<xref:System.Drawing?displayProperty=fullName> 名前空間とその下位名前空間に格納されています。  [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] の詳細については、「[マネージ グラフィックス クラスの使用](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)」を参照してください。  また、[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] の基本については「[方法 : 進行状況を示す Windows フォーム コントロールを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)」にも説明されています。  
  
## 描画領域のジオメトリ  
 <xref:System.Windows.Forms.PaintEventArgs> の <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> プロパティが実際に描画される領域を指定している一方、コントロールの <xref:System.Windows.Forms.Control.ClientRectangle%2A> プロパティはユーザーの画面上のコントロールに使用できる四角形の領域を指定します。  実際に描画が実行されるのは、<xref:System.Windows.Forms.PaintEventArgs> インスタンスを引数として受け取る <xref:System.Windows.Forms.Control.Paint> イベント メソッドです。  コントロールでは、使用できる領域の一部を描画するだけで済む場合があります。たとえば、コントロールの表示領域の一部だけが変更された場合などです。  このような場合、コントロールの開発者は実際に描画する領域を計算し、算出された値を <xref:System.Windows.Forms.Control.Invalidate%2A> へ渡す必要があります。  引数として <xref:System.Drawing.Rectangle> または <xref:System.Drawing.Region> を受け取る <xref:System.Windows.Forms.Control.Invalidate%2A> のオーバーロードされたバージョンでは、その引数を使用して <xref:System.Windows.Forms.PaintEventArgs> の <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> プロパティを生成します。  
  
 `FlashTrackBar` カスタム コントロールが、描画する四角形領域を計算する処理を次のコード片に示します。  `client` 変数は <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> プロパティを示します。  サンプル全体については、「[方法 : 進行状況を示す Windows フォーム コントロールを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)」を参照してください。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## グラフィック リソースの解放  
 グラフィック オブジェクトはシステム リソースを消費するため、パフォーマンスへの影響が大きいオブジェクトです。  そのようなオブジェクトは、<xref:System.Drawing.Graphics?displayProperty=fullName> クラスのインスタンスに加えて、<xref:System.Drawing.Brush?displayProperty=fullName> クラス、<xref:System.Drawing.Pen?displayProperty=fullName> クラス、およびその他のグラフィックス クラスのインスタンスを含みます。  必要な場合にだけグラフィック リソースを作成し、リソースの利用が終わったらすぐにリソースを解放することが重要です。  <xref:System.IDisposable> インターフェイスを実装する型を作成する場合には、処理が完了したら、リソースを解放するために <xref:System.IDisposable.Dispose%2A> メソッドを呼び出します。  
  
 `FlashTrackBar` カスタム コントロールによる <xref:System.Drawing.Brush> リソースの作成と解放を、次のコード片に示します。  ソース コード全体については、「[方法 : 進行状況を示す Windows フォーム コントロールを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)」を参照してください。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## 参照  
 [方法 : 進行状況を示す Windows フォーム コントロールを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)