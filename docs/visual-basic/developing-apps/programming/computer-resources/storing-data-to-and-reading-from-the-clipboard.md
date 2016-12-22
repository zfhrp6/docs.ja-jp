---
title: "Storing Data to and Reading from the Clipboard (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Clipboard, storing data to (My.Computer.Clipboard)"
  - "Clipboard, reading from (My.Computer.Clipboard)"
  - "Clipboard"
  - "My.Computer.Clipboard object, tasks"
  - "data [Visual Basic], Clipboard"
  - "reading data, from Clipboard"
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Storing Data to and Reading from the Clipboard (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

クリップボードは、テキストやイメージなどのデータの格納に使用できます。  クリップボードはすべてのアクティブ プロセスが共有しているので、プロセス間でのデータの転送に使用できます。  `My.Computer.Clipboard` のオブジェクトの割り当て簡単にクリップボード アクセスでき、読み書きに読み込む。  
  
## クリップボードから読み取ったり  
 クリップボードからテキストを読み取るために <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> のメソッドを使用します。  次のコードでは、テキストを読み込み、メッセージ ボックスに表示します。  この例が正しく動作するためには、クリップボードにテキストが格納されている必要があります。  
  
 [!code-vb[VbVbcnMyClipboard#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_1.vb)]  
  
 このコードの例は、IntelliSense コード スニペットとしても利用できます。  コード スニペット ピッカーでは、これは **\[Windows Forms Applications\]** の \[Clipboard\] にあります。  詳細については、「[コード スニペット](/visual-studio/ide/code-snippets)」を参照してください。  
  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> メソッドを使用して、クリップボードからイメージを取得します。  この例では、クリップボードにイメージが格納されているかどうかを確認してから、そのイメージを取得し、 `PictureBox1` に割り当てます。  
  
 [!code-vb[VbResourceTasks#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_2.vb)]  
  
 このコードの例は、IntelliSense コード スニペットとしても利用できます。  コード スニペット ピッカーでは、これは **\[Windows Forms Applications\]** の \[Clipboard\] にあります。詳細については、「[コード スニペット](/visual-studio/ide/code-snippets)」を参照してください。  
  
 クリップボードに格納したアイテムは、アプリケーションの終了後も保持されます。  
  
## クリップボードに格納されているファイルの種類を決定します。  
 クリップボードのデータは、テキスト、オーディオ ファイル、イメージなど、さまざまな形式をとります。  クリップボードに格納されているファイルの種類を判断するには、<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>、<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>、<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>、および <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A> の各メソッドを使用できます。  <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> メソッドを使用すると、カスタムの形式をチェックできます。  
  
 `ContainsImage` 関数を使用して、クリップボードに格納されているデータがイメージかどうかを判断します。  次のコードは、データがイメージかどうかを確認し、それに応じて報告します。  
  
 [!code-vb[VbResourceTasks#13](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_3.vb)]  
  
## クリップボードを消去  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> メソッドは、クリップボードを消去します。  クリップボードは他のプロセスと共有されているので、クリップボードを消去すると他のプロセスに影響が及ぶことがあります。  
  
 `Clear` メソッドの使用例を次のコードに示します。  
  
 [!code-vb[VbVbcnMyClipboard#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_4.vb)]  
  
## クリップボードに書き込みます  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> メソッドを使用して、クリップボードにテキストを書き込みます。  次のコードは、文字列 "This is a test string" をクリップボードに書き込みます。  
  
 [!code-vb[VbVbcnMyClipboard#1](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_5.vb)]  
  
 `SetText` のメソッドは <xref:System.Windows.Forms.TextDataFormat>の型を含むフォーム パラメーターを使用できます。  次のコードは、文字列 "This is a test string" を RTF テキストとしてクリップボードに書き込みます。  
  
 [!code-vb[VbVbcnMyClipboard#2](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_6.vb)]  
  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> メソッドを使用して、クリップボードにデータを書き込みます。  この例は、`DataObject` `dataChunk` をカスタム形式 `specialFormat` でクリップボードに書き込みます。  
  
 [!code-vb[VbVbcnMyClipboard#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_7.vb)]  
  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> メソッドを使用して、オーディオ データをクリップボードに書き込みます。  この例では、バイト配列 `musicReader` を作成し、ファイル `cool.wav` をその中に読み込んでから、クリップボードに書き込みます。  
  
 [!code-vb[VbResourceTasks#5](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_8.vb)]  
  
> [!IMPORTANT]
>  クリップボードには他のユーザーからもアクセス可能なので、クリップボードを使ってパスワードや極秘データなどの機密情報を格納しないでください。  
  
## 参照  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>   
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>   
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>   
 [方法: XML ファイルからオブジェクト データを読み込む](../Topic/How%20to:%20Read%20Object%20Data%20from%20an%20XML%20File%20\(C%23%20and%20Visual%20Basic\).md)   
 [方法: XML ファイルにオブジェクト データを書き込む](../Topic/How%20to:%20Write%20Object%20Data%20to%20an%20XML%20File%20\(C%23%20and%20Visual%20Basic\).md)