---
title: "ダブル バッファリングされたグラフィックス | Microsoft Docs"
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
  - "ダブル バッファリング"
  - "例 [Windows フォーム], ダブル バッファリングされたグラフィックス"
  - "ちらつき, 軽減 (ダブル バッファリングにより)"
  - "グラフィックス, ダブル バッファリング"
ms.assetid: 4f6fef99-0972-436e-9d73-0167e4033f71
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# ダブル バッファリングされたグラフィックス
グラフィックスをプログラミングするときは、ちらつきが一般的な問題になります。  複数の複雑な描画操作を必要とするグラフィックス操作を実行すると、描画されたイメージがちらつきなどによって適切に表示されないことがあります。  このような問題に対処するために、.NET Framework では、ダブル バッファリングを利用できます。  
  
 ダブル バッファリングでは、メモリ バッファーを使用して、複数の描画操作に関連するちらつきの問題に対処します。  ダブル バッファリングを有効にすると、すべての描画操作が画面上の描画サーフェイスではなく、最初にメモリ バッファーに描画されます。  描画操作がすべて完了すると、メモリ バッファーが、関連付けられている描画サーフェイスに直接コピーされます。  画面上で実行されるグラフィックス操作は 1 つだけなので、複雑な描画操作に関連するイメージのちらつきが解消されます。  
  
## 既定のダブル バッファリング  
 アプリケーションでダブル バッファリングを使用するには、.NET Framework に用意されている、フォームやコントロールに対する既定のダブル バッファリングを使用するのが最も簡単です。  Windows フォームや作成した Windows コントロールに対して既定のダブル バッファリングを有効にするには、<xref:System.Windows.Forms.Control.DoubleBuffered%2A> プロパティを `true` に設定するか、<xref:System.Windows.Forms.Control.SetStyle%2A> メソッドを使用します。  詳細については、「[方法 : フォームとコントロールのダブル バッファリングを行うことによってグラフィックスのちらつきを軽減する](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)」を参照してください。  
  
## バッファリングされたグラフィックスの手動管理  
 アニメーションや高度なメモリ管理など、より高度なダブル バッファリングのシナリオでは、.NET Framework クラスを使用して独自のダブル バッファリング ロジックを実装できます。  個々のグラフィックス バッファーの割り当てと管理を担当するクラスは <xref:System.Drawing.BufferedGraphicsContext> クラスです。  各アプリケーション ドメインには、そのアプリケーションの既定のダブル バッファリングをすべて管理する、それぞれ独自の既定の <xref:System.Drawing.BufferedGraphicsContext> インスタンスがあります。  多くの場合、アプリケーションごとに存在するアプリケーション ドメインは 1 つだけなので、通常、アプリケーションごとに 1 つの既定の <xref:System.Drawing.BufferedGraphicsContext> があります。  既定の <xref:System.Drawing.BufferedGraphicsContext> インスタンスは、<xref:System.Drawing.BufferedGraphicsManager> クラスによって管理されます。  既定の <xref:System.Drawing.BufferedGraphicsContext> インスタンスへの参照を取得するには、[BufferedGraphicsManager.Current プロパティ](frlrfSystemDrawingBufferedGraphicsManagerClassCurrentTopic)を呼び出します。  また、専用の <xref:System.Drawing.BufferedGraphicsContext> インスタンスを作成して、グラフィックス重視のアプリケーションのパフォーマンスを向上させることもできます。  <xref:System.Drawing.BufferedGraphicsContext> インスタンスの作成方法については、「[方法 : バッファリングされたグラフィックスを手動で管理する](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)」を参照してください。  
  
## バッファリングされたグラフィックスの手動表示  
 <xref:System.Drawing.BufferedGraphicsContext> クラスのインスタンスを使用して [BufferedGraphicsContext.Allocate メソッド](frlrfSystemDrawingBufferedGraphicsContextClassAllocateTopic)を呼び出すと、グラフィックス バッファーを作成できます。このメソッドは、<xref:System.Drawing.BufferedGraphics> クラスのインスタンスを返します。  <xref:System.Drawing.BufferedGraphics> オブジェクトは、フォームやコントロールなどの描画面に関連付けられたメモリ バッファーを管理します。  
  
 インスタンス化された <xref:System.Drawing.BufferedGraphics> クラスは、メモリ内のグラフィックス バッファーへの描画を管理します。  グラフィックスは、[BufferedGraphics.Graphics プロパティ](frlrfSystemDrawingBufferedGraphicsClassGraphicsTopic)を通じてメモリ バッファーに描画できます。このプロパティは、メモリ バッファーを直接表す <xref:System.Drawing.Graphics> オブジェクトを公開します。  この <xref:System.Drawing.Graphics> オブジェクトには、描画サーフェイスを表す <xref:System.Drawing.Graphics> オブジェクトに描画する場合と同じように描画できます。  すべてのグラフィックスをバッファーに描画すると、[BufferedGraphics.Render メソッド](frlrfSystemDrawingBufferedGraphicsClassRenderTopic)を使用して、バッファーの内容を画面上の描画サーフェイスにコピーできます。  
  
 <xref:System.Drawing.BufferedGraphics> クラスの使い方の詳細については、「[方法 : バッファリングされたグラフィックスを手動で描画する](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)」を参照してください。  グラフィックスの描画の詳細については、「[Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)」を参照してください。  
  
## 参照  
 <xref:System.Drawing.BufferedGraphics>   
 <xref:System.Drawing.BufferedGraphicsContext>   
 <xref:System.Drawing.BufferedGraphicsManager>   
 [方法 : バッファリングされたグラフィックスを手動で描画する](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)   
 [方法 : フォームとコントロールのダブル バッファリングを行うことによってグラフィックスのちらつきを軽減する](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)   
 [方法 : バッファリングされたグラフィックスを手動で管理する](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)   
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)