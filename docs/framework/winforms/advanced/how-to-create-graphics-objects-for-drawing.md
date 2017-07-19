---
title: "方法 : 描画する Graphics オブジェクトを作成する | Microsoft Docs"
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
  - "GDI+, 作成 (イメージを)"
  - "グラフィックス [Windows フォーム], 作成"
  - "Graphics クラス"
  - "イメージ [Windows フォーム], 作成"
ms.assetid: 162861f9-f050-445e-8abb-b2c43a918b8b
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 方法 : 描画する Graphics オブジェクトを作成する
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] を使用して線や形状の描画、テキストのレンダリング、イメージの表示と操作などを行うには、<xref:System.Drawing.Graphics> オブジェクトを作成する必要があります。  <xref:System.Drawing.Graphics> オブジェクトは、[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] の描画サーフェイスを表し、グラフィカル イメージの作成に使用します。  
  
 グラフィックスの操作には 2 つの手順があります。  
  
1.  <xref:System.Drawing.Graphics> オブジェクトを構築する。  
  
2.  <xref:System.Drawing.Graphics> オブジェクトを使用して、線や形状の描画、テキストのレンダリング、またはイメージの表示と操作を実行する。  
  
## Graphics オブジェクトの作成  
 グラフィックス オブジェクトはさまざまな方法で作成できます。  
  
#### グラフィックス オブジェクトを作成するには  
  
-   グラフィックス オブジェクトへの参照を、フォームまたはコントロールの <xref:System.Windows.Forms.Control.Paint> イベントの <xref:System.Windows.Forms.PaintEventArgs> の一部として受け取ります。  これは、コントロールの描画コードを作成するときにグラフィックス オブジェクトへの参照を取得するための一般的な方法です。  同様に、<xref:System.Drawing.Printing.PrintDocument> の <xref:System.Drawing.Printing.PrintDocument.PrintPage> イベントを処理するときに、<xref:System.Drawing.Printing.PrintPageEventArgs> のプロパティとしてグラフィックス オブジェクトとして取得することもできます。  
  
     または  
  
-   コントロールまたはフォームの <xref:System.Windows.Forms.Control.CreateGraphics%2A> メソッドを呼び出して、そのコントロールまたはフォームの描画サーフェイスを表す <xref:System.Drawing.Graphics> オブジェクトへの参照を取得します。  このメソッドは、既に存在するフォームまたはコントロール上に描画する場合に使用します。  
  
     または  
  
-   <xref:System.Drawing.Image> を継承する任意のオブジェクトから <xref:System.Drawing.Graphics> オブジェクトを作成します。  この方法は、既存のイメージを変更する場合に便利です。  
  
     これらのそれぞれの方法について、以降で詳しく説明します。  
  
## Paint イベント ハンドラーの PaintEventArgs  
 コントロールの <xref:System.Windows.Forms.PaintEventHandler>、または <xref:System.Drawing.Printing.PrintDocument> の <xref:System.Drawing.Printing.PrintDocument.PrintPage> をプログラミングする場合、グラフィックス オブジェクトが <xref:System.Windows.Forms.PaintEventArgs> または <xref:System.Drawing.Printing.PrintPageEventArgs> のプロパティの 1 つとして用意されています。  
  
#### Paint イベントの PaintEventArgs から Graphics オブジェクトへの参照を取得するには  
  
1.  <xref:System.Drawing.Graphics> オブジェクトを宣言します。  
  
2.  <xref:System.Windows.Forms.PaintEventArgs> の一部として渡された <xref:System.Drawing.Graphics> オブジェクトを参照する変数を割り当てます。  
  
3.  フォームまたはコントロールを描画するコードを挿入します。  
  
     <xref:System.Windows.Forms.Control.Paint> イベントの <xref:System.Windows.Forms.PaintEventArgs> から <xref:System.Drawing.Graphics> オブジェクトを参照する方法を次の例に示します。  
  
    ```vb  
    Private Sub Form1_Paint(sender As Object, pe As PaintEventArgs) Handles _  
       MyBase.Paint  
       ' Declares the Graphics object and sets it to the Graphics object  
       ' supplied in the PaintEventArgs.  
       Dim g As Graphics = pe.Graphics  
       ' Insert code to paint the form here.  
    End Sub  
  
    ```  
  
    ```csharp  
    private void Form1_Paint(object sender,   
       System.Windows.Forms.PaintEventArgs pe)   
    {  
       // Declares the Graphics object and sets it to the Graphics object  
       // supplied in the PaintEventArgs.  
       Graphics g = pe.Graphics;  
       // Insert code to paint the form here.  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void Form1_Paint(System::Object ^ sender,  
          System::Windows::Forms::PaintEventArgs ^ pe)  
       {  
          // Declares the Graphics object and sets it to the Graphics object  
          // supplied in the PaintEventArgs.  
          Graphics ^ g = pe->Graphics;  
          // Insert code to paint the form here.  
       }  
    ```  
  
## CreateGraphics メソッド  
 コントロールまたはフォームの <xref:System.Windows.Forms.Control.CreateGraphics%2A> メソッドを使用して、そのコントロールまたはフォームの描画サーフェイスを表す <xref:System.Drawing.Graphics> オブジェクトへの参照を取得することもできます。  
  
#### CreateGraphics メソッドで Graphics オブジェクトを作成するには  
  
-   グラフィックをレンダリングするフォームまたはコントロールの <xref:System.Windows.Forms.Control.CreateGraphics%2A> メソッドを呼び出します。  
  
    ```vb  
    Dim g as Graphics  
    ' Sets g to a Graphics object representing the drawing surface of the  
    ' control or form g is a member of.  
    g = Me.CreateGraphics  
  
    ```  
  
    ```csharp  
    Graphics g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this.CreateGraphics();  
  
    ```  
  
    ```cpp  
    Graphics ^ g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this->CreateGraphics();  
    ```  
  
## Image オブジェクトからの作成  
 <xref:System.Drawing.Image> クラスから派生した任意のオブジェクトからグラフィックス オブジェクトを作成することもできます。  
  
#### Image から Graphics オブジェクトを作成するには  
  
-   <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=fullName> オブジェクトの作成元となる Image 変数の名前を指定して、<xref:System.Drawing.Graphics> メソッドを呼び出します。  
  
     <xref:System.Drawing.Bitmap> オブジェクトを使用する方法を次の例に示します。  
  
    ```vb  
    Dim myBitmap as New Bitmap("C:\Documents and Settings\Joe\Pics\myPic.bmp")  
    Dim g as Graphics = Graphics.FromImage(myBitmap)  
  
    ```  
  
    ```csharp  
    Bitmap myBitmap = new Bitmap(@"C:\Documents and   
       Settings\Joe\Pics\myPic.bmp");  
    Graphics g = Graphics.FromImage(myBitmap);  
  
    ```  
  
    ```cpp  
    Bitmap ^ myBitmap = gcnew  
       Bitmap("D:\\Documents and Settings\\Joe\\Pics\\myPic.bmp");  
    Graphics ^ g = Graphics::FromImage(myBitmap);  
    ```  
  
> [!NOTE]
>  <xref:System.Drawing.Graphics> オブジェクトを作成できるのは、16 ビット .bmp ファイル、24 ビット .bmp ファイル、32 ビット .bmp ファイルなどの、インデックスのない .bmp ファイルからだけです。  インデックスのない .bmp ファイルの各ピクセルは色を保持します。これに対して、インデックス付き .bmp ファイルのピクセルはカラー テーブルに対するインデックスを保持します。  
  
## 形状およびイメージの描画と操作  
 作成した <xref:System.Drawing.Graphics> オブジェクトを使用して、線や形状の描画、テキストのレンダリング、およびイメージの表示と操作を行うことができます。  <xref:System.Drawing.Graphics> オブジェクトと一緒に使用される主要なオブジェクトを次に示します。  
  
-   <xref:System.Drawing.Pen> クラス \- 線の描画、形状のアウトラインの作成、またはその他の幾何学表現に使用します。  
  
-   <xref:System.Drawing.Brush> クラス \- 形状、イメージ、テキストの塗りつぶしなど、グラフィック領域の塗りつぶしに使用します。  
  
-   <xref:System.Drawing.Font> クラス \- テキストのレンダリング時に使用する形状についての説明を提供します。  
  
-   <xref:System.Drawing.Color> 構造体 \- 各種の表示色を表します。  
  
#### 作成した Graphics オブジェクトを使用するには  
  
-   上記のオブジェクトを使用して目的の項目を描画します。  
  
     詳細については、次のトピックを参照してください。  
  
    |レンダリング対象|参照項目|  
    |--------------|----------|  
    |線|[方法 : Windows フォームに直線を描画する](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-on-a-windows-form.md)|  
    |図形|[方法 : 形状のアウトラインを描画する](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)|  
    |テキスト|[方法 : Windows フォームにテキストを描画する](../../../../docs/framework/winforms/advanced/how-to-draw-text-on-a-windows-form.md)|  
    |\[イメージ\]|[方法 : GDI\+ を使用してイメージをレンダリングする](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)|  
  
## 参照  
 [グラフィックス プログラミングについて](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)   
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [方法 : GDI\+ を使用してイメージをレンダリングする](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)