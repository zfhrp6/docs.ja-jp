---
title: '方法 : 描画する Graphics オブジェクトを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating
- images [Windows Forms], creating
- GDI+, creating images
ms.assetid: 162861f9-f050-445e-8abb-b2c43a918b8b
ms.openlocfilehash: 3c25ddcfb3a566055afd5e233c2a69b3b7a8c66e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526489"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a>方法 : 描画する Graphics オブジェクトを作成する
線と形状を描画することができます、前に、テキストのレンダリングまたは表示し、操作を使用してイメージ[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]、作成する必要があります、<xref:System.Drawing.Graphics>オブジェクト。 <xref:System.Drawing.Graphics>オブジェクトが表す、[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]画面を描画し、グラフィカル イメージを作成するために使用するオブジェクトです。  
  
 グラフィックスの操作には、2 つの手順があります。  
  
1.  作成する、<xref:System.Drawing.Graphics>オブジェクト。  
  
2.  使用して、<xref:System.Drawing.Graphics>直線と図形の描画、テキストのレンダリング、表示やイメージを操作するオブジェクト。  
  
## <a name="creating-a-graphics-object"></a>グラフィック オブジェクトを作成します。  
 グラフィックス オブジェクトは、さまざまな方法で作成できます。  
  
#### <a name="to-create-a-graphics-object"></a>グラフィック オブジェクトを作成するには  
  
-   一部として、グラフィックス オブジェクトへの参照を受け取る、<xref:System.Windows.Forms.PaintEventArgs>で、<xref:System.Windows.Forms.Control.Paint>フォームまたはコントロールのイベントです。 通常はコントロールの描画コードを作成するときに、グラフィックス オブジェクトへの参照を取得する方法です。 同様に、取得することも、グラフィック オブジェクトのプロパティとして、<xref:System.Drawing.Printing.PrintPageEventArgs>を処理するとき、<xref:System.Drawing.Printing.PrintDocument.PrintPage>イベントを<xref:System.Drawing.Printing.PrintDocument>です。  
  
     - または -  
  
-   呼び出す、<xref:System.Windows.Forms.Control.CreateGraphics%2A>コントロールまたはフォームへの参照を取得する方法、<xref:System.Drawing.Graphics>コントロールまたはフォームの描画サーフェイスを表すオブジェクト。 フォームまたは既に存在するコントロールを描画する場合は、このメソッドを使用します。  
  
     - または -  
  
-   作成、<xref:System.Drawing.Graphics>オブジェクトから継承する任意のオブジェクトから<xref:System.Drawing.Image>です。 この方法は、既存のイメージを変更する場合に便利です。  
  
     次のセクションでは、これらの各プロセスの詳細を付けます。  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>Paint イベント ハンドラーで PaintEventArgs  
 プログラミングを行う場合、<xref:System.Windows.Forms.PaintEventHandler>のコントロールまたは<xref:System.Drawing.Printing.PrintDocument.PrintPage>の<xref:System.Drawing.Printing.PrintDocument>のプロパティの 1 つとして、グラフィックス オブジェクトが提供される<xref:System.Windows.Forms.PaintEventArgs>または<xref:System.Drawing.Printing.PrintPageEventArgs>です。  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>Paint イベントで PaintEventArgs からグラフィックス オブジェクトへの参照を取得するには  
  
1.  宣言、<xref:System.Drawing.Graphics>オブジェクト。  
  
2.  参照する変数を割り当てる、<xref:System.Drawing.Graphics>の一部として渡されるオブジェクト、<xref:System.Windows.Forms.PaintEventArgs>です。  
  
3.  フォームまたはコントロールを描画するコードを挿入します。  
  
     次の例を参照する方法を示しています、<xref:System.Drawing.Graphics>オブジェクトから、<xref:System.Windows.Forms.PaintEventArgs>で、<xref:System.Windows.Forms.Control.Paint>イベント。  
  
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
  
## <a name="creategraphics-method"></a>CreateGraphics メソッド  
 使用することも、<xref:System.Windows.Forms.Control.CreateGraphics%2A>コントロールまたはフォームへの参照を取得する方法、<xref:System.Drawing.Graphics>コントロールまたはフォームの描画サーフェイスを表すオブジェクト。  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>CreateGraphics メソッドを使用して、グラフィックス オブジェクトを作成するには  
  
-   呼び出す、<xref:System.Windows.Forms.Control.CreateGraphics%2A>グラフィックスをレンダリングする基になるフォームまたはコントロールのメソッドです。  
  
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
  
## <a name="create-from-an-image-object"></a>Image オブジェクトから作成します。  
 さらから派生した任意のオブジェクトからグラフィックス オブジェクトを作成することができます、<xref:System.Drawing.Image>クラスです。  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>イメージからグラフィックス オブジェクトを作成するには  
  
-   呼び出す、<xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType>メソッドを作成するイメージの変数の名前を指定して、<xref:System.Drawing.Graphics>オブジェクト。  
  
     次の例を使用する方法を示しています、<xref:System.Drawing.Bitmap>オブジェクト。  
  
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
>  のみを作成することができます<xref:System.Drawing.Graphics>16、24 ビットおよび 32 ビットの .bmp ファイルなど、インデックスなしの .bmp ファイルからのオブジェクト。 各ピクセルのない .bmp ファイルでは、ピクセルの色のテーブルにインデックスを保持するインデックス付きの .bmp ファイルとは異なり、色を保持します。  
  
-  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>描画し、図形や画像を操作します。  
 その作成した後、<xref:System.Drawing.Graphics>直線と図形の描画、テキストのレンダリング、表示やイメージを操作するオブジェクトを使用する可能性があります。 使用される主要なオブジェクト、<xref:System.Drawing.Graphics>オブジェクトは。  
  
-   <xref:System.Drawing.Pen>クラス — 線を描画、アウトラインの図形、または幾何学的表現のレンダリングに使用します。  
  
-   <xref:System.Drawing.Brush>クラス — 塗りつぶされた図形、画像、テキストなどのグラフィックスの領域を塗りつぶすときのために使用します。  
  
-   <xref:System.Drawing.Font>クラス-テキストのレンダリング時に使用する図形の新機能の説明を提供します。  
  
-   <xref:System.Drawing.Color>構造体などを表示するさまざまな色を表します。  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>作成したグラフィックス オブジェクトを使用するには  
  
-   必要なものを描画する上に示した適切なオブジェクトを操作します。  
  
     詳細については、次のトピックを参照してください。  
  
    |表示するには|解決方法については、|  
    |---------------|---------|  
    |線|[方法: Windows フォームに直線を描画する](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-on-a-windows-form.md)|  
    |図形|[方法: 形状のアウトラインを描画する](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)|  
    |テキスト|[方法: Windows フォームにテキストを描画する](../../../../docs/framework/winforms/advanced/how-to-draw-text-on-a-windows-form.md)|  
    |イメージ|[方法: GDI+ を使用してイメージをレンダリングする](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a>関連項目  
 [グラフィックス プログラミングについて](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [方法: GDI+ を使用してイメージをレンダリングする](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)
