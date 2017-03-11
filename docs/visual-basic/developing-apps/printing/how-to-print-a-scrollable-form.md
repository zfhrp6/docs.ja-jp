---
title: "方法: スクロール可能フォームを印刷する (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "フォーム全体, 印刷"
  - "スクロール可能フォーム, 印刷"
ms.assetid: 1196e1cf-b77f-4928-a3e4-85b51ba3787d
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# 方法: スクロール可能フォームを印刷する (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントを使用すると、<xref:System.Drawing.Printing.PrintDocument> コンポーネントを使わなくてもフォームのイメージをすばやく印刷できます。 既定では、フォームの現在見えている部分だけが印刷されます。ユーザーが実行時にフォームのサイズを変更した場合、イメージは意図されたとおりに印刷されない可能性があります。 次の手順は、フォームのサイズが変更された場合でもスクロール可能フォームのクライアント領域全体を印刷する方法を示します。  
  
 PowerPack コントロールは、Visual Studio には含まれなくなりましたが、[ダウンロード センター](http://www.microsoft.com/en-us/download/details.aspx?id=25169)からダウンロードできます。  
  
### スクロール可能フォームのクライアント領域全体を印刷するには  
  
1.  **ツールボックス**で、**\[Visual Basic PowerPacks\]** タブをクリックして、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントをフォームにドラッグします。  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントがコンポーネント トレイに追加されます。  
  
2.  **\[プロパティ\]** ウィンドウで、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> プロパティを <xref:System.Drawing.Printing.PrintAction> に設定します。  
  
3.  適切なイベント ハンドラー \(たとえば **\[印刷\]**`Button` の `Click` イベント ハンドラー\) に、次のコードを追加します。  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.Scrollable)  
    ```  
  
    > [!NOTE]
    >  オペレーティング システムによっては、<xref:System.Drawing.Graphics> メソッドによって描画されたテキストやグラフィックスが正しく印刷されないことがあります。 その場合、`Scrollable` パラメーターを使用して印刷することはできません。  
  
## 参照  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>   
 [PrintForm Component](../../../visual-basic/developing-apps/printing/printform-component.md)   
 [方法: フォームのクライアント領域を印刷する](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)   
 [方法: フォームのクライアント領域と非クライアント領域を印刷する](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)