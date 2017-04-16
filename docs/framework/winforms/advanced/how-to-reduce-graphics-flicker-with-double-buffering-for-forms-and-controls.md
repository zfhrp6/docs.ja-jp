---
title: "方法 : フォームとコントロールのダブル バッファリングを行うことによってグラフィックスのちらつきを軽減する | Microsoft Docs"
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
  - "DoubleBuffered プロパティ"
  - "ちらつき, 低減 (Windows フォーム内の)"
  - "グラフィックス, 軽減 (ダブル バッファリングによってちらつきを)"
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : フォームとコントロールのダブル バッファリングを行うことによってグラフィックスのちらつきを軽減する
ダブル バッファリングでは、メモリ バッファーを使用して、複数の描画操作に関連するちらつきの問題に対処します。  ダブル バッファリングを有効にすると、すべての描画操作が画面上の描画サーフェイスではなく、最初にメモリ バッファーに描画されます。  描画操作がすべて完了すると、メモリ バッファーが、関連付けられている描画サーフェイスに直接コピーされます。  画面上で実行されるグラフィックス操作は 1 つだけなので、複雑な描画操作に関連するイメージのちらつきが解消されます。ほとんどのアプリケーションでは、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] が提供する既定のダブル バッファリングにより最善の結果が得られます。  標準の Windows フォーム コントロールは既定でダブル バッファリングをサポートしています。  フォームおよび作成済みコントロール内では既定のダブル バッファリングを 2 とおりの方法で有効にできます。  <xref:System.Windows.Forms.Control.DoubleBuffered%2A> プロパティを `true` に設定するか、<xref:System.Windows.Forms.Control.SetStyle%2A> メソッドを呼び出して <xref:System.Windows.Forms.ControlStyles> フラグを `true` に設定します。  どちらの方法でも、フォームまたはコントロールに対して既定のダブル バッファリングが有効になり、ちらつきのないグラフィックが描画されます。  <xref:System.Windows.Forms.Control.SetStyle%2A> メソッドの呼び出しは、ユーザーがすべてのレンダリング処理コードを記述したカスタム コントロールに対してのみ実行するようにお勧めします。  
  
 アニメーションや高度なメモリ管理など、より高度なダブル バッファリングのシナリオでは、独自のダブル バッファリング ロジックを実装できます。  詳細については、「[方法 : バッファリングされたグラフィックスを手動で管理する](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)」を参照してください。  
  
### ちらつきを軽減するには  
  
-   <xref:System.Windows.Forms.Control.DoubleBuffered%2A> プロパティを `true` に設定します。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 または  
  
-   <xref:System.Windows.Forms.Control.SetStyle%2A> メソッドを呼び出して、<xref:System.Windows.Forms.ControlStyles> フラグを `true` に設定します。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## 参照  
 <xref:System.Windows.Forms.Control.DoubleBuffered%2A>   
 <xref:System.Windows.Forms.Control.SetStyle%2A>   
 [ダブル バッファリングされたグラフィックス](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)   
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)