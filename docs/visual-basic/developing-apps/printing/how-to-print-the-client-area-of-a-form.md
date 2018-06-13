---
title: '方法: フォームのクライアント領域を印刷する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- client area [Visual Basic], printing
ms.assetid: c06c9c0e-bc07-48cd-9596-e29a2ff96236
ms.openlocfilehash: 361db89f0880a03273aac7fc36b5c5faa825486f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583992"
---
# <a name="how-to-print-the-client-area-of-a-form-visual-basic"></a><span data-ttu-id="0d32c-102">方法: フォームのクライアント領域を印刷する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d32c-102">How to: Print the Client Area of a Form (Visual Basic)</span></span>
<span data-ttu-id="0d32c-103"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントを使用すると、 <xref:System.Drawing.Printing.PrintDocument> コンポーネントを使わなくてもフォームのイメージをすばやく印刷できます。</span><span class="sxs-lookup"><span data-stu-id="0d32c-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="0d32c-104">次の手順では、タイトル バー、罫線、およびスクロール バー以外の、フォームのクライアント領域だけを印刷する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0d32c-104">The following procedure shows how to print just the client area of a form, without the title bar, borders, and scroll bars.</span></span>  
  
 <span data-ttu-id="0d32c-105">PowerPack コントロールは、Visual Studio には含まれなくなりましたが、 [ダウンロード センター](http://www.microsoft.com/en-us/download/details.aspx?id=25169)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="0d32c-105">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-the-client-area-of-a-form"></a><span data-ttu-id="0d32c-106">フォームのクライアント領域を印刷するには</span><span class="sxs-lookup"><span data-stu-id="0d32c-106">To print the client area of a form</span></span>  
  
1.  <span data-ttu-id="0d32c-107">**ツールボックス**で、 **[Visual Basic PowerPacks]** タブをクリックして、 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントをフォームにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0d32c-107">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="0d32c-108"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントをコンポーネント トレイに追加します。</span><span class="sxs-lookup"><span data-stu-id="0d32c-108">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="0d32c-109">**[プロパティ]** ウィンドウで、 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> プロパティを <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>に設定します。</span><span class="sxs-lookup"><span data-stu-id="0d32c-109">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="0d32c-110">適切なイベント ハンドラー (たとえば `Click` [印刷] **の**`Button`イベント ハンドラー) に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="0d32c-110">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.ClientAreaOnly)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="0d32c-111">オペレーティング システムによっては、 <xref:System.Drawing.Graphics> メソッドによって描画されたテキストやグラフィックスが正しく印刷されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="0d32c-111">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="0d32c-112">この場合は、互換性のある印刷メソッドを使用します。 `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`</span><span class="sxs-lookup"><span data-stu-id="0d32c-112">In this case, use the compatible printing method: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d32c-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="0d32c-113">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [<span data-ttu-id="0d32c-114">PrintForm コンポーネント</span><span class="sxs-lookup"><span data-stu-id="0d32c-114">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [<span data-ttu-id="0d32c-115">方法: フォームのクライアント領域と非クライアント領域を印刷する</span><span class="sxs-lookup"><span data-stu-id="0d32c-115">How to: Print Client and Non-Client Areas of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [<span data-ttu-id="0d32c-116">方法: スクロール可能フォームを印刷する</span><span class="sxs-lookup"><span data-stu-id="0d32c-116">How to: Print a Scrollable Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
