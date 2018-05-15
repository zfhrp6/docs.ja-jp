---
title: '方法: JPEG 圧縮レベルの設定'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], changing encoder parameters
- JPEG images [Windows Forms], setting quality level
ms.assetid: 4b9a74e3-9504-43c1-9f28-ace651d0772e
ms.openlocfilehash: 5f12f0ed8bae7b6cfb6f3162848e3c3761f7dbbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-jpeg-compression-level"></a><span data-ttu-id="c6fbd-102">方法: JPEG 圧縮レベルの設定</span><span class="sxs-lookup"><span data-stu-id="c6fbd-102">How to: Set JPEG Compression Level</span></span>
<span data-ttu-id="c6fbd-103">イメージをディスクに保存するときに、ファイル サイズを最小化したり品質を向上させるために、イメージのパラメーターを修正したりする必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="c6fbd-103">You may want to modify the parameters of an image when you save the image to disk to minimize the file size or improve its quality.</span></span> <span data-ttu-id="c6fbd-104">圧縮レベルを修正して、JPEG イメージの品質を調整することができます。</span><span class="sxs-lookup"><span data-stu-id="c6fbd-104">You can adjust the quality of a JPEG image by modifying its compression level.</span></span> <span data-ttu-id="c6fbd-105">JPEG 画像を保存するときに、圧縮レベルを指定するに作成する必要があります、<xref:System.Drawing.Imaging.EncoderParameters>オブジェクトに渡すと、<xref:System.Drawing.Image.Save%2A>のメソッド、<xref:System.Drawing.Image>クラスです。</span><span class="sxs-lookup"><span data-stu-id="c6fbd-105">To specify the compression level when you save a JPEG image, you must create an <xref:System.Drawing.Imaging.EncoderParameters> object and pass it to the <xref:System.Drawing.Image.Save%2A> method of the <xref:System.Drawing.Image> class.</span></span> <span data-ttu-id="c6fbd-106">初期化、<xref:System.Drawing.Imaging.EncoderParameters>オブジェクトのいずれかで構成される配列を持つこと、<xref:System.Drawing.Imaging.EncoderParameter>です。</span><span class="sxs-lookup"><span data-stu-id="c6fbd-106">Initialize the <xref:System.Drawing.Imaging.EncoderParameters> object so that it has an array that consists of one <xref:System.Drawing.Imaging.EncoderParameter>.</span></span> <span data-ttu-id="c6fbd-107">作成するときに、<xref:System.Drawing.Imaging.EncoderParameter>を指定して、<xref:System.Drawing.Imaging.Encoder.Quality>エンコーダー、その、必要な圧縮レベルです。</span><span class="sxs-lookup"><span data-stu-id="c6fbd-107">When you create the <xref:System.Drawing.Imaging.EncoderParameter>, specify the <xref:System.Drawing.Imaging.Encoder.Quality> encoder, and the desired compression level.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6fbd-108">例</span><span class="sxs-lookup"><span data-stu-id="c6fbd-108">Example</span></span>  
 <span data-ttu-id="c6fbd-109">次のコード例を作成、<xref:System.Drawing.Imaging.EncoderParameter>オブジェクトし、次の 3 つの JPEG 画像を保存します。</span><span class="sxs-lookup"><span data-stu-id="c6fbd-109">The following example code creates an <xref:System.Drawing.Imaging.EncoderParameter> object and saves three JPEG images.</span></span> <span data-ttu-id="c6fbd-110">各 JPEG イメージは変更することにより、さまざまな品質レベルで保存、`long`に渡された値、<xref:System.Drawing.Imaging.EncoderParameter>コンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="c6fbd-110">Each JPEG image is saved with a different quality level, by modifying the `long` value passed to the <xref:System.Drawing.Imaging.EncoderParameter> constructor.</span></span> <span data-ttu-id="c6fbd-111">品質レベル 0 は最も圧縮率が高く、品質レベル 100 は最も低い圧縮率に対応します。</span><span class="sxs-lookup"><span data-stu-id="c6fbd-111">A quality level of 0 corresponds to the greatest compression, and a quality level of 100 corresponds to the least compression.</span></span>  
  
```csharp  
private void VaryQualityLevel()  
    {  
        // Get a bitmap. The using statement ensures objects  
        // are automatically disposed from memory after use.  
        using (Bitmap bmp1 = new Bitmap(@"C:\TestPhoto.jpg"))  
        {  
            ImageCodecInfo jpgEncoder = GetEncoder(ImageFormat.Jpeg);  
  
            // Create an Encoder object based on the GUID  
            // for the Quality parameter category.  
            System.Drawing.Imaging.Encoder myEncoder =  
                System.Drawing.Imaging.Encoder.Quality;  
  
            // Create an EncoderParameters object.  
            // An EncoderParameters object has an array of EncoderParameter  
            // objects. In this case, there is only one  
            // EncoderParameter object in the array.  
            EncoderParameters myEncoderParameters = new EncoderParameters(1);  
  
            EncoderParameter myEncoderParameter = new EncoderParameter(myEncoder, 50L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"c:\TestPhotoQualityFifty.jpg", jpgEncoder, myEncoderParameters);  
  
            myEncoderParameter = new EncoderParameter(myEncoder, 100L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"C:\TestPhotoQualityHundred.jpg", jpgEncoder, myEncoderParameters);  
  
            // Save the bitmap as a JPG file with zero quality level compression.  
            myEncoderParameter = new EncoderParameter(myEncoder, 0L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"C:\TestPhotoQualityZero.jpg", jpgEncoder, myEncoderParameters);  
        }  
    }  
```  
  
```vb  
Private Sub VaryQualityLevel()  
    ' Get a bitmap. The Using statement ensures objects  
    ' are automatically disposed from memory after use.  
    Using bmp1 As New Bitmap("C:\test\TestPhoto.jpg")  
        Dim jpgEncoder As ImageCodecInfo = GetEncoder(ImageFormat.Jpeg)  
  
        ' Create an Encoder object based on the GUID  
        ' for the Quality parameter category.  
        Dim myEncoder As System.Drawing.Imaging.Encoder = System.Drawing.Imaging.Encoder.Quality  
  
        ' Create an EncoderParameters object.  
        ' An EncoderParameters object has an array of EncoderParameter  
        ' objects. In this case, there is only one  
        ' EncoderParameter object in the array.  
        Dim myEncoderParameters As New EncoderParameters(1)  
  
        Dim myEncoderParameter As New EncoderParameter(myEncoder, 50L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("c:\test\TestPhotoQualityFifty.jpg", jpgEncoder, myEncoderParameters)  
  
        myEncoderParameter = New EncoderParameter(myEncoder, 100L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("C:\test\TestPhotoQualityHundred.jpg", jpgEncoder, myEncoderParameters)  
  
        ' Save the bitmap as a JPG file with zero quality level compression.  
        myEncoderParameter = New EncoderParameter(myEncoder, 0L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("C:\test\TestPhotoQualityZero.jpg", jpgEncoder, myEncoderParameters)  
    End Using  
End Sub  
```  
  
```csharp  
private ImageCodecInfo GetEncoder(ImageFormat format)  
{  
    ImageCodecInfo[] codecs = ImageCodecInfo.GetImageDecoders();  
    foreach (ImageCodecInfo codec in codecs)  
    {  
        if (codec.FormatID == format.Guid)  
        {  
            return codec;  
        }  
    }  
    return null;  
}  
```  
  
```vb  
Private Function GetEncoder(ByVal format As ImageFormat) As ImageCodecInfo  
  
    Dim codecs As ImageCodecInfo() = ImageCodecInfo.GetImageDecoders()  
    Dim codec As ImageCodecInfo  
    For Each codec In codecs  
        If codec.FormatID = format.Guid Then  
            Return codec  
        End If  
    Next codec  
    Return Nothing  
  
End Function  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c6fbd-112">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="c6fbd-112">Compiling the Code</span></span>  
 <span data-ttu-id="c6fbd-113">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c6fbd-113">This example requires:</span></span>  
  
-   <span data-ttu-id="c6fbd-114">Windows フォーム アプリケーション</span><span class="sxs-lookup"><span data-stu-id="c6fbd-114">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="c6fbd-115">A <xref:System.Windows.Forms.PaintEventArgs>、パラメーターのある<xref:System.Windows.Forms.PaintEventHandler>です。</span><span class="sxs-lookup"><span data-stu-id="c6fbd-115">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
-   <span data-ttu-id="c6fbd-116">`TestPhoto.jpg` という名前のイメージ ファイル。保存場所は **c:\\** です。</span><span class="sxs-lookup"><span data-stu-id="c6fbd-116">An image file that is named `TestPhoto.jpg` and located at **c:\\**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6fbd-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6fbd-117">See Also</span></span>  
 [<span data-ttu-id="c6fbd-118">方法: エンコーダーがサポートするパラメーターの確認</span><span class="sxs-lookup"><span data-stu-id="c6fbd-118">How to: Determine the Parameters Supported by an Encoder</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)  
 [<span data-ttu-id="c6fbd-119">ビットマップの種類</span><span class="sxs-lookup"><span data-stu-id="c6fbd-119">Types of Bitmaps</span></span>](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)  
 [<span data-ttu-id="c6fbd-120">マネージ GDI+ でのイメージ エンコーダーおよびイメージ デコーダーの使用</span><span class="sxs-lookup"><span data-stu-id="c6fbd-120">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
