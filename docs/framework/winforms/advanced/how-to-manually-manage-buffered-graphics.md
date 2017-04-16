---
title: "方法 : バッファリングされたグラフィックスを手動で管理する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "BufferedGraphicsContext クラス"
  - "ちらつき, 軽減 (グラフィックスを手動で管理することで)"
  - "グラフィックス, 管理 (バッファーに格納された)"
ms.assetid: 4c2a90ee-bbbe-4ff6-9170-1b06c195c918
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : バッファリングされたグラフィックスを手動で管理する
高度なダブル バッファリング シナリオでは、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] クラスを使用して独自のダブル バッファリング ロジックを実装できます。  個々のグラフィックス バッファーの割り当てと管理を担当するクラスは <xref:System.Drawing.BufferedGraphicsContext> クラスです。  各アプリケーションには、そのアプリケーションの既定のダブル バッファリングをすべて管理する、それぞれ独自の既定の <xref:System.Drawing.BufferedGraphicsContext> があります。  このインスタンスへの参照は、<xref:System.Drawing.BufferedGraphicsManager.Current%2A> を呼び出して取得できます。  
  
### 既定の BufferedGraphicsContext への参照を取得するには  
  
-   次のコード例に示すように、<xref:System.Drawing.BufferedGraphicsManager.Current%2A> プロパティを設定します。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    >  <xref:System.Drawing.BufferedGraphicsManager> クラスから受け取る <xref:System.Drawing.BufferedGraphicsContext> 参照で `Dispose` メソッドを呼び出す必要はありません。  <xref:System.Drawing.BufferedGraphicsManager> は、既定の <xref:System.Drawing.BufferedGraphicsContext> インスタンスのメモリの割り当てと配布をすべて処理します。  
  
     アニメーションなど、グラフィックスを多用するアプリケーションでは、<xref:System.Drawing.BufferedGraphicsManager> が提供する <xref:System.Drawing.BufferedGraphicsContext> ではなく、専用の <xref:System.Drawing.BufferedGraphicsContext> を使用することによってパフォーマンスを向上できる場合があります。  これによって、アプリケーションに関連する他のバッファー内グラフィックスをすべて管理することによるパフォーマンスのオーバーヘッドを生じることなく、グラフィックス バッファーを個々に作成および管理できます。ただし、アプリケーションが消費するメモリは多くなります。  
  
### 専用の BufferedGraphicsContext を作成するには  
  
-   次のコード例に示すように、<xref:System.Drawing.BufferedGraphicsContext> クラスの新しいインスタンスを宣言して作成します。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## 参照  
 <xref:System.Drawing.BufferedGraphicsContext>   
 [ダブル バッファリングされたグラフィックス](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)   
 [方法 : バッファリングされたグラフィックスを手動で描画する](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)