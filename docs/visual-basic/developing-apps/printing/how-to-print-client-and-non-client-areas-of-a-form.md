---
title: "方法: フォームのクライアント領域と非クライアント領域を印刷する (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "タイトル バー, 印刷"
  - "印刷"
  - "境界, 印刷"
  - "全体 (フォームの)"
  - "非クライアント領域, 印刷"
ms.assetid: 856bb0e4-dbc3-47e2-81cd-4b376cf07757
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# 方法: フォームのクライアント領域と非クライアント領域を印刷する (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントを使用すると、<xref:System.Drawing.Printing.PrintDocument> コンポーネントを使わなくても、画面に表示されているとおりにフォームのイメージをすぐに印刷することができます。 次の手順では、クライアント領域と非クライアント領域の両方を含むフォームを印刷する方法を示します。 非クライアント領域にはタイトル バー、境界、およびスクロール バーが含まれます。  
  
 PowerPack コントロールは、Visual Studio には含まれなくなりましたが、[ダウンロード センター](http://www.microsoft.com/en-us/download/details.aspx?id=25169)からダウンロードできます。  
  
### フォームのクライアント領域と非クライアント領域の両方を印刷するには  
  
1.  **ツールボックス**で、**\[Visual Basic PowerPacks\]** タブをクリックして、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントをフォームにドラッグします。  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントをコンポーネント トレイに追加します。  
  
2.  **\[プロパティ\]** ウィンドウで、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> プロパティを <xref:System.Drawing.Printing.PrintAction> に設定します。  
  
3.  適切なイベント ハンドラー \(たとえば \[印刷\] `Button` の `Click` イベント ハンドラー\) に、次のコードを追加します。  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.FullWindow)  
    ```  
  
    > [!NOTE]
    >  オペレーティング システムによっては、<xref:System.Drawing.Graphics> メソッドによって描画されたテキストやグラフィックスが正しく印刷されないことがあります。 この場合は、互換性のある印刷メソッド `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.CompatibleModeFullWindow` を使用してください。  
  
## 参照  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>   
 [PrintForm Component](../../../visual-basic/developing-apps/printing/printform-component.md)   
 [方法: スクロール可能フォームを印刷する](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)