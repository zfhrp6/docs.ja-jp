---
title: "方法 : Windows フォームで複数ページのテキスト ファイルを印刷する"
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
- printing [Windows Forms], printing multiple pages
- text [Windows Forms], printing Windows Forms
- Windows Forms, printing text
- printing [Windows Forms], text
ms.assetid: 362427f8-03d4-4826-b49f-60ab066ad322
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4576e969ba917b845cc8fbd6420741e2b24062fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a><span data-ttu-id="02004-102">方法 : Windows フォームで複数ページのテキスト ファイルを印刷する</span><span class="sxs-lookup"><span data-stu-id="02004-102">How to: Print a Multi-Page Text File in Windows Forms</span></span>
<span data-ttu-id="02004-103">Windows ベースのアプリケーションでは、テキストを印刷することは非常に一般的です。</span><span class="sxs-lookup"><span data-stu-id="02004-103">It is very common for Windows-based applications to print text.</span></span> <span data-ttu-id="02004-104"><xref:System.Drawing.Graphics> クラスは、画面やプリンターなどのデバイスにオブジェクト (グラフィックスやテキスト) を描画するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="02004-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects (graphics or text) to a device, such as a screen or printer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02004-105"><xref:System.Windows.Forms.TextRenderer> の <xref:System.Windows.Forms.TextRenderer.DrawText%2A> メソッドでは、印刷はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="02004-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of <xref:System.Windows.Forms.TextRenderer> are not supported for printing.</span></span> <span data-ttu-id="02004-106">印刷用にテキストを描画するには、次のコード例で示すように、<xref:System.Drawing.Graphics> の <xref:System.Drawing.Graphics.DrawString%2A> メソッドを常に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="02004-106">You should always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of <xref:System.Drawing.Graphics>, as shown in the following code example, to draw text for printing purposes.</span></span>  
  
### <a name="to-print-text"></a><span data-ttu-id="02004-107">テキストを印刷するには</span><span class="sxs-lookup"><span data-stu-id="02004-107">To print text</span></span>  
  
1.  <span data-ttu-id="02004-108">フォームに <xref:System.Drawing.Printing.PrintDocument> コンポーネントと文字列を追加します。</span><span class="sxs-lookup"><span data-stu-id="02004-108">Add a <xref:System.Drawing.Printing.PrintDocument> component and a string to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2.  <span data-ttu-id="02004-109">ドキュメントを印刷する場合は、<xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> プロパティを印刷するドキュメントに設定し、ドキュメントの内容を開いて前に追加した文字列に読み取ります。</span><span class="sxs-lookup"><span data-stu-id="02004-109">If printing a document, set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the documents contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3.  <span data-ttu-id="02004-110"><xref:System.Drawing.Printing.PrintDocument.PrintPage> イベント ハンドラーで、<xref:System.Drawing.Printing.PrintPageEventArgs> クラスの <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> プロパティとドキュメントの内容を使用して、行の長さと 1 ページあたりの行数を計算します。</span><span class="sxs-lookup"><span data-stu-id="02004-110">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the document contents to calculate line length and lines per page.</span></span> <span data-ttu-id="02004-111">各ページを描画した後で、最後のページかどうかを確認し、<xref:System.Drawing.Printing.PrintPageEventArgs> の <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> プロパティを適切に設定します。</span><span class="sxs-lookup"><span data-stu-id="02004-111">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="02004-112"><xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> が `false` になるまで <xref:System.Drawing.Printing.PrintDocument.PrintPage> イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="02004-112">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="02004-113">また、<xref:System.Drawing.Printing.PrintDocument.PrintPage> イベントがイベント処理メソッドに関連付けられていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="02004-113">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
     <span data-ttu-id="02004-114">次のコード例では、イベント ハンドラーは、フォームで使用されているものと同じフォントで "testPage.txt" ファイルの内容を印刷するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="02004-114">In the following code example, the event handler is used to print the contents of the "testPage.txt" file in the same font as is used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4.  <span data-ttu-id="02004-115"><xref:System.Drawing.Printing.PrintDocument.Print%2A> メソッドを呼び出して <xref:System.Drawing.Printing.PrintDocument.PrintPage> イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="02004-115">Call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to raise the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="02004-116">例</span><span class="sxs-lookup"><span data-stu-id="02004-116">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="02004-117">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="02004-117">Compiling the Code</span></span>  
 <span data-ttu-id="02004-118">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="02004-118">This example requires:</span></span>  
  
-   <span data-ttu-id="02004-119">C:\\ ドライブのルートにある、印刷するテキストを含む testPage.txt という名前のテキスト ファイル。</span><span class="sxs-lookup"><span data-stu-id="02004-119">A text file named testPage.txt containing the text to print, located in the root of drive C:\\.</span></span> <span data-ttu-id="02004-120">別のファイルを印刷するようコードを編集します。</span><span class="sxs-lookup"><span data-stu-id="02004-120">Edit the code to print a different file.</span></span>  
  
-   <span data-ttu-id="02004-121">System、System.Windows.Forms、System.Drawing の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="02004-121">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
-   <span data-ttu-id="02004-122">[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法については、「[コマンド ラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)」または「[csc.exe を使用したコマンド ラインからのビルド](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02004-122">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="02004-123">また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="02004-123">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="02004-124">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="02004-124">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02004-125">参照</span><span class="sxs-lookup"><span data-stu-id="02004-125">See Also</span></span>  
 <xref:System.Drawing.Graphics>  
 <xref:System.Drawing.Brush>  
 [<span data-ttu-id="02004-126">Windows フォームにおける印刷のサポート</span><span class="sxs-lookup"><span data-stu-id="02004-126">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
