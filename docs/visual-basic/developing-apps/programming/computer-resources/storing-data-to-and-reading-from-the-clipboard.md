---
title: "クリップボードのデータの格納と読み取り (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e7bb4ad56f0a039aa7b23d7f0612aaab9366cb9e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a><span data-ttu-id="eeabd-102">クリップボードのデータの格納と読み取り (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eeabd-102">Storing data to and reading from the Clipboard (Visual Basic)</span></span>
<span data-ttu-id="eeabd-103">クリップボードは、テキスト、イメージなどのデータの格納に使用できます。</span><span class="sxs-lookup"><span data-stu-id="eeabd-103">The Clipboard can be used to store data, such as text and images.</span></span> <span data-ttu-id="eeabd-104">アクティブなプロセスすべてがこのクリップボードを共有しているため、クリップボードを使ってデータをプロセス間で転送することができます。</span><span class="sxs-lookup"><span data-stu-id="eeabd-104">Because the Clipboard is shared by all active processes, it can be used to transfer data between them.</span></span> <span data-ttu-id="eeabd-105">`My.Computer.Clipboard` オブジェクトを使用すると、クリップボードに簡単にアクセスして、読み込みや書き込みを実行できます。</span><span class="sxs-lookup"><span data-stu-id="eeabd-105">The `My.Computer.Clipboard` object allows you to easily access the Clipboard and to read from and write to it.</span></span>  
  
## <a name="reading-from-the-clipboard"></a><span data-ttu-id="eeabd-106">クリップボードからの読み取り</span><span class="sxs-lookup"><span data-stu-id="eeabd-106">Reading from the Clipboard</span></span>  
 <span data-ttu-id="eeabd-107"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> メソッドを使用すると、クリップボードからテキストを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="eeabd-107">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> method to read the text in the Clipboard.</span></span> <span data-ttu-id="eeabd-108">次のコードはテキストを読み取って、メッセージ ボックスに表示します。</span><span class="sxs-lookup"><span data-stu-id="eeabd-108">The following code reads the text and displays it in a message box.</span></span> <span data-ttu-id="eeabd-109">この例を正しく動作させるには、クリップボードにテキストが格納されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="eeabd-109">There must be text stored on the Clipboard for the example to run correctly.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_1.vb)]  
  
 <span data-ttu-id="eeabd-110">このコード例は、IntelliSense コード スニペットとしても利用できます。</span><span class="sxs-lookup"><span data-stu-id="eeabd-110">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="eeabd-111">コード スニペット ピッカーでこのスニペットにアクセスするには、**[Windows フォーム アプリケーション]、[クリップボード]** の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="eeabd-111">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.</span></span> <span data-ttu-id="eeabd-112">詳細については、「[Code Snippets](/visualstudio/ide/code-snippets)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eeabd-112">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="eeabd-113"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> メソッドを使用すると、クリップボードからイメージを取得できます。</span><span class="sxs-lookup"><span data-stu-id="eeabd-113">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> method to retrieve an image from the Clipboard.</span></span> <span data-ttu-id="eeabd-114">この例では、イメージを取得して `PictureBox1` に割り当てる前に、そのイメージがクリップボードにあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="eeabd-114">This example checks to see if there is an image on the Clipboard before retrieving it and assigning it to `PictureBox1`.</span></span>  
  
 [!code-vb[VbResourceTasks#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_2.vb)]  
  
 <span data-ttu-id="eeabd-115">このコード例は、IntelliSense コード スニペットとしても利用できます。</span><span class="sxs-lookup"><span data-stu-id="eeabd-115">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="eeabd-116">コード スニペット ピッカーでこのスニペットにアクセスするには、**[Windows フォーム アプリケーション]、[クリップボード]** の順に移動します。詳細については、「[コード スニペット](/visualstudio/ide/code-snippets)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eeabd-116">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="eeabd-117">クリップボード内のアイテムは、アプリケーションの終了後も保持されます。</span><span class="sxs-lookup"><span data-stu-id="eeabd-117">Items placed on the Clipboard will persist even after the application is shut down.</span></span>  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a><span data-ttu-id="eeabd-118">クリップボードに格納されているファイルの種類の確認</span><span class="sxs-lookup"><span data-stu-id="eeabd-118">Determining the type of file stored in the Clipboard</span></span>  
 <span data-ttu-id="eeabd-119">クリップボードには、テキスト、オーディオ ファイル、イメージなど、さまざまな形式のデータを格納できます。</span><span class="sxs-lookup"><span data-stu-id="eeabd-119">Data on the Clipboard may take a number of different forms, such as text, an audio file, or an image.</span></span> <span data-ttu-id="eeabd-120">クリップボード内のファイルの種類を確認するには、<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>、<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>、<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>、<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A> などのメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="eeabd-120">In order to determine what sort of file is on the Clipboard, you can use methods such as <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, and <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span></span> <span data-ttu-id="eeabd-121">確認対象にカスタム形式が含まれる場合は、<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="eeabd-121">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> method can be used if you have a custom format that you want to check.</span></span>  
  
 <span data-ttu-id="eeabd-122">`ContainsImage` 関数を使用すると、クリップボードに含まれるデータがイメージかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="eeabd-122">Use the `ContainsImage` function to determine whether the data contained on the Clipboard is an image.</span></span> <span data-ttu-id="eeabd-123">次のコードでは、データがイメージかどうかを確認し、それに応じて報告します。</span><span class="sxs-lookup"><span data-stu-id="eeabd-123">The following code checks to see whether the data is an image and reports accordingly.</span></span>  
  
 [!code-vb[VbResourceTasks#13](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_3.vb)]  
  
## <a name="clearing-the-clipboard"></a><span data-ttu-id="eeabd-124">クリップボードのクリア</span><span class="sxs-lookup"><span data-stu-id="eeabd-124">Clearing the Clipboard</span></span>  
 <span data-ttu-id="eeabd-125"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> メソッドはクリップボードをクリアします。</span><span class="sxs-lookup"><span data-stu-id="eeabd-125">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> method clears the Clipboard.</span></span> <span data-ttu-id="eeabd-126">クリップボードは他のプロセスによって共有されているため、クリップボードをクリアすると、こうしたプロセスに影響することがあります。</span><span class="sxs-lookup"><span data-stu-id="eeabd-126">Because the Clipboard is shared by other processes, clearing it may have an impact on those processes.</span></span>  
  
 <span data-ttu-id="eeabd-127">`Clear` メソッドの使用例を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="eeabd-127">The following code shows how to use the `Clear` method.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_4.vb)]  
  
## <a name="writing-to-the-clipboard"></a><span data-ttu-id="eeabd-128">クリップボードへの書き込み</span><span class="sxs-lookup"><span data-stu-id="eeabd-128">Writing to the Clipboard</span></span>  
 <span data-ttu-id="eeabd-129"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> メソッドを使用して、クリップボードにテキストを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="eeabd-129">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> method to write text to the Clipboard.</span></span> <span data-ttu-id="eeabd-130">次のコードでは、"This is a test string" という文字列をクリップボードに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="eeabd-130">The following code writes the string "This is a test string" to the Clipboard.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#1](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_5.vb)]  
  
 <span data-ttu-id="eeabd-131">`SetText` メソッドは、<xref:System.Windows.Forms.TextDataFormat> 型を含む書式パラメーターを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="eeabd-131">The `SetText` method can accept a format parameter that contains a type of <xref:System.Windows.Forms.TextDataFormat>.</span></span> <span data-ttu-id="eeabd-132">次のコードでは、"This is a test string" という文字列を RTF テキストとしてクリップボードに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="eeabd-132">The following code writes the string "This is a test string" to the Clipboard as RTF text.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#2](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_6.vb)]  
  
 <span data-ttu-id="eeabd-133"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> メソッドを使用して、クリップボードにデータを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="eeabd-133">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> method to write data to the Clipboard.</span></span> <span data-ttu-id="eeabd-134">この例では、`DataObject``dataChunk` をカスタム書式 `specialFormat` でクリップボードに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="eeabd-134">This example writes the `DataObject``dataChunk` to the Clipboard in the custom format `specialFormat`.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_7.vb)]  
  
 <span data-ttu-id="eeabd-135"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> メソッドを使用して、クリップボードにオーディオ データを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="eeabd-135">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> method to write audio data to the Clipboard.</span></span> <span data-ttu-id="eeabd-136">この例では、バイト配列 `musicReader` を作成し、`cool.wav` ファイルを読み込んでから、それをクリップボードに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="eeabd-136">This example creates the byte array `musicReader`, reads the file `cool.wav` into it, and then writes it to the Clipboard.</span></span>  
  
 [!code-vb[VbResourceTasks#5](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_8.vb)]  
  
> [!IMPORTANT]
>  <span data-ttu-id="eeabd-137">クリップボードには他のユーザーもアクセスできるため、パスワード、機密データなどの機密情報は格納しないでください。</span><span class="sxs-lookup"><span data-stu-id="eeabd-137">Because the Clipboard can be accessed by other users, do not use it to store sensitive information, such as passwords or confidential data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeabd-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="eeabd-138">See also</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>  
 [<span data-ttu-id="eeabd-139">方法: XML ファイルからオブジェクト データを読み込む</span><span class="sxs-lookup"><span data-stu-id="eeabd-139">How to: Read Object Data from an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
 [<span data-ttu-id="eeabd-140">方法: XML ファイルにオブジェクト データを書き込む</span><span class="sxs-lookup"><span data-stu-id="eeabd-140">How to: Write Object Data to an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
