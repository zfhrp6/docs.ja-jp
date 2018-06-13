---
title: '方法 : バッファリングされたグラフィックスを手動で管理する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually managing graphics
- graphics [Windows Forms], managing buffered
ms.assetid: 4c2a90ee-bbbe-4ff6-9170-1b06c195c918
ms.openlocfilehash: f8675582fe6bafefd94d6a740c3263e407dfd4e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523956"
---
# <a name="how-to-manually-manage-buffered-graphics"></a>方法 : バッファリングされたグラフィックスを手動で管理する
高度なダブル バッファリングのシナリオで使用することができます、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]ダブル バッファリング ロジックを実装するクラス。 割り当てと個々 のグラフィックス バッファーを管理するクラスは、<xref:System.Drawing.BufferedGraphicsContext>クラスです。 すべてのアプリケーションが独自の既定<xref:System.Drawing.BufferedGraphicsContext>ダブル バッファリングをそのアプリケーション用の既定のすべてを管理します。 このインスタンスへの参照を取得するには呼び出すことによって、<xref:System.Drawing.BufferedGraphicsManager.Current%2A>です。  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a>既定値 BufferedGraphicsContext への参照を取得するには  
  
-   設定、<xref:System.Drawing.BufferedGraphicsManager.Current%2A>プロパティ、次のコード例に示すようにします。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    >  呼び出す必要はありません、`Dispose`メソッドを<xref:System.Drawing.BufferedGraphicsContext>から受信する参照、<xref:System.Drawing.BufferedGraphicsManager>クラスです。 <xref:System.Drawing.BufferedGraphicsManager> 、メモリの割り当てと既定の配布をすべて処理<xref:System.Drawing.BufferedGraphicsContext>インスタンス。  
  
     アニメーションなどの画像を多用するアプリケーションは、場合によってパフォーマンスを向上できる専用を使用して<xref:System.Drawing.BufferedGraphicsContext>の代わりに、<xref:System.Drawing.BufferedGraphicsContext>によって提供される、<xref:System.Drawing.BufferedGraphicsManager>です。 これにより、作成し、すべて、その他のバッファリングされたグラフィックス管理アプリケーションを使用して、関連付けられているアプリケーションによって消費されるメモリが大きくなる場合のパフォーマンスのオーバーヘッドは要しませんグラフィックス バッファーを個別に管理することができます。  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a>専用 BufferedGraphicsContext を作成するには  
  
-   宣言し、の新しいインスタンスを作成、<xref:System.Drawing.BufferedGraphicsContext>クラスに、次のコード例に示すようにします。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.BufferedGraphicsContext>  
 [ダブル バッファリングされたグラフィックス](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [方法: バッファリングされたグラフィックスを手動で描画する](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)
