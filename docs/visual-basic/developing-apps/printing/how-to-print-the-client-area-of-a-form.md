---
title: "方法: フォームのクライアント領域を印刷する (Visual Basic) | Microsoft Docs"
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
  - "クライアント領域、印刷"
ms.assetid: c06c9c0e-bc07-48cd-9596-e29a2ff96236
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法: フォームのクライアント領域を印刷する (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントを使用すると、<xref:System.Drawing.Printing.PrintDocument> コンポーネントを使わなくてもフォームのイメージをすばやく印刷できます。 次の手順では、タイトル バー、罫線、およびスクロール バー以外の、フォームのクライアント領域だけを印刷する方法を示します。  
  
 PowerPack コントロールは、Visual Studio には含まれなくなりましたが、[ダウンロード センター](http://www.microsoft.com/en-us/download/details.aspx?id=25169)からダウンロードできます。  
  
### フォームのクライアント領域を印刷するには  
  
1.  **ツールボックス**で、**\[Visual Basic PowerPacks\]** タブをクリックして、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントをフォームにドラッグします。  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントをコンポーネント トレイに追加します。  
  
2.  **\[プロパティ\]** ウィンドウで、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> プロパティを <xref:System.Drawing.Printing.PrintAction> に設定します。  
  
3.  適切なイベント ハンドラー \(たとえば **\[印刷\]**`Button` の `Click` イベント ハンドラー\) に、次のコードを追加します。  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.ClientAreaOnly)  
    ```  
  
    > [!NOTE]
    >  オペレーティング システムによっては、<xref:System.Drawing.Graphics> メソッドによって描画されたテキストやグラフィックスが正しく印刷されないことがあります。 この場合は、互換性のある印刷メソッドを使用します。`PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`  
  
## 参照  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>   
 [PrintForm Component](../../../visual-basic/developing-apps/printing/printform-component.md)   
 [方法: フォームのクライアント領域と非クライアント領域を印刷する](../Topic/How%20to:%20Print%20Client%20and%20Non-Client%20Areas%20of%20a%20Form%20\(Visual%20Basic\).md)   
 [方法: スクロール可能フォームを印刷する](../Topic/How%20to:%20Print%20a%20Scrollable%20Form%20\(Visual%20Basic\).md)