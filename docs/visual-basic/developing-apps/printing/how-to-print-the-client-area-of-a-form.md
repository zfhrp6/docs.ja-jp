---
title: '方法: フォームのクライアント領域を印刷する (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- client area [Visual Basic], printing
ms.assetid: c06c9c0e-bc07-48cd-9596-e29a2ff96236
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ef42dd3c809ff0a1594350e252d4c4aa2f0ec004
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2018
---
# <a name="how-to-print-the-client-area-of-a-form-visual-basic"></a>方法: フォームのクライアント領域を印刷する (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントを使用すると、 <xref:System.Drawing.Printing.PrintDocument> コンポーネントを使わなくてもフォームのイメージをすばやく印刷できます。 次の手順では、タイトル バー、罫線、およびスクロール バー以外の、フォームのクライアント領域だけを印刷する方法を示します。  
  
 PowerPack コントロールは、Visual Studio には含まれなくなりましたが、 [ダウンロード センター](http://www.microsoft.com/en-us/download/details.aspx?id=25169)からダウンロードできます。  
  
### <a name="to-print-the-client-area-of-a-form"></a>フォームのクライアント領域を印刷するには  
  
1.  **ツールボックス**で、 **[Visual Basic PowerPacks]** タブをクリックして、 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントをフォームにドラッグします。  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントをコンポーネント トレイに追加します。  
  
2.  **[プロパティ]** ウィンドウで、 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> プロパティを <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>に設定します。  
  
3.  適切なイベント ハンドラー (たとえば `Click` [印刷] **の**`Button`イベント ハンドラー) に、次のコードを追加します。  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.ClientAreaOnly)  
    ```  
  
    > [!NOTE]
    >  オペレーティング システムによっては、 <xref:System.Drawing.Graphics> メソッドによって描画されたテキストやグラフィックスが正しく印刷されないことがあります。 この場合は、互換性のある印刷メソッドを使用します。 `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [PrintForm コンポーネント](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [方法: フォームのクライアント領域と非クライアント領域を印刷する](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [方法: スクロール可能フォームを印刷する](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
