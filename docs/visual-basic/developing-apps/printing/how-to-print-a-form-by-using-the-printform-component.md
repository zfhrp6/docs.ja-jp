---
title: "方法: PrintForm コンポーネントを使用してフォームを印刷する (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "フォーム, 印刷"
ms.assetid: df963bf6-3ee1-49f4-8b2e-1d95d1beb0be
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# 方法: PrintForm コンポーネントを使用してフォームを印刷する (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントを使用すると、<xref:System.Drawing.Printing.PrintDocument> コンポーネントを使わなくても、画面に表示されているとおりにフォームのイメージをすぐに印刷することができます。 次の手順では、プリンター、印刷プレビュー ウィンドウ、およびカプセル化された PostScript ファイルにフォームを印刷する方法を示します。  
  
 PowerPack コントロールは、Visual Studio には含まれなくなりましたが、[ダウンロード センター](http://www.microsoft.com/en-us/download/details.aspx?id=25169)からダウンロードできます。  
  
### 既定のプリンターにフォームを印刷するには  
  
1.  **ツールボックス**で、**\[Visual Basic PowerPacks\]** タブをクリックして、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントをフォームにドラッグします。  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントをコンポーネント トレイに追加します。  
  
2.  **\[プロパティ\]** ウィンドウで、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> プロパティを <xref:System.Drawing.Printing.PrintAction> に設定します。  
  
3.  適切なイベント ハンドラー \(たとえば **\[印刷\]**`Button` の `Click` イベント ハンドラー\) に、次のコードを追加します。  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### \[印刷プレビュー\] ウィンドウでフォームを表示するには  
  
1.  **ツールボックス**で、**\[Visual Basic PowerPacks\]** タブをクリックして、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントをフォームにドラッグします。  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントをコンポーネント トレイに追加します。  
  
2.  **\[プロパティ\]** ウィンドウで、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> プロパティを <xref:System.Drawing.Printing.PrintAction> に設定します。  
  
3.  適切なイベント ハンドラー \(たとえば **\[印刷\]**`Button` の `Click` イベント ハンドラー\) に、次のコードを追加します。  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### ファイルにフォームを印刷するには  
  
1.  **ツールボックス**で、**\[Visual Basic PowerPacks\]** タブをクリックして、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントをフォームにドラッグします。  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントをコンポーネント トレイに追加します。  
  
2.  **\[プロパティ\]** ウィンドウで、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> プロパティを <xref:System.Drawing.Printing.PrintAction> に設定します。  
  
3.  必要に応じて、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> プロパティを選択して、対象ファイルの完全なパスとファイル名を入力します。  
  
     この手順をスキップすると、ユーザーは実行時にファイル名を求められます。  
  
4.  適切なイベント ハンドラー \(たとえば **\[印刷\]**`Button` の `Click` イベント ハンドラー\) に、次のコードを追加します。  
  
    ```  
    PrintForm1.Print()  
    ```  
  
## 参照  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A>   
 [方法: フォームのクライアント領域を印刷する](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)   
 [方法: フォームのクライアント領域と非クライアント領域を印刷する](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)   
 [方法: スクロール可能フォームを印刷する](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)   
 [PrintForm Component](../../../visual-basic/developing-apps/printing/printform-component.md)