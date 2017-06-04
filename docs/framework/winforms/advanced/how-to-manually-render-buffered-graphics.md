---
title: "方法 : バッファリングされたグラフィックスを手動で描画する | Microsoft Docs"
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
  - "BufferedGraphics クラス"
  - "ちらつき, 軽減 (グラフィックスを手動で描画することで)"
  - "グラフィックス [Windows フォーム], 描画"
ms.assetid: 5192295e-bd8e-45f7-8bd6-5c4f6bd21e61
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : バッファリングされたグラフィックスを手動で描画する
独自のバッファリングされたグラフィックスを管理している場合は、グラフィックス バッファーを作成して表示できるようにする必要があります。  <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> メソッドを呼び出すことで、画面の描画サーフェイスに関連付けられている <xref:System.Drawing.BufferedGraphics> クラスのインスタンスを作成できます。  このメソッドは、フォームやコントロールなど、特定の表示サーフェイスに関連付けられている <xref:System.Drawing.BufferedGraphics> インスタンスを作成します。  <xref:System.Drawing.BufferedGraphics> インスタンスを作成した後、<xref:System.Drawing.BufferedGraphics.Graphics%2A> プロパティを通じて表すバッファーにグラフィックスを描画することができます。  グラフィックスのすべての操作を実行した後で、<xref:System.Drawing.BufferedGraphics.Render%2A> メソッドを呼び出すことで、バッファーの内容を画面にコピーできます。  
  
> [!NOTE]
>  独自の表示を実行する場合、わずかですがメモリ消費量が増加します。  
  
### バッファリングされたグラフィックスを手動で描画するには  
  
1.  <xref:System.Drawing.BufferedGraphicsContext> クラスのインスタンスへの参照を取得します。  詳細については、「[方法 : バッファリングされたグラフィックスを手動で管理する](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)」を参照してください。  
  
2.  次のコード例に示すように、<xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> メソッドを呼び出して <xref:System.Drawing.BufferedGraphics> クラスのインスタンスを作成します。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3.  <xref:System.Drawing.BufferedGraphics.Graphics%2A> プロパティを設定することで、グラフィックスのバッファーにグラフィックスを描画します。  次に例を示します。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4.  グラフィックス バッファーへのすべての描画操作が完了したら、次のコード例に示すように、<xref:System.Drawing.BufferedGraphics.Render%2A> メソッドを呼び出して、そのバッファーに関連付けられている描画サーフェイス、または指定された描画サーフェイスのいずれかにバッファーを表示します。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5.  グラフィックのレンダリングが完了した後、<xref:System.Drawing.BufferedGraphics> インスタンスの `Dispose` メソッドを呼び出し、システム リソースを解放します。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## 参照  
 <xref:System.Drawing.BufferedGraphicsContext>   
 <xref:System.Drawing.BufferedGraphics>   
 [ダブル バッファリングされたグラフィックス](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)   
 [方法 : バッファリングされたグラフィックスを手動で管理する](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)