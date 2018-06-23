---
title: '方法: テキストでのアンチエイリアシングの使用'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [Windows Forms], smoothing drawn
- antialiasing [Windows Forms], using with text
- text [Windows Forms], smoothing
- text [Windows Forms], antialiasing
- strings [Windows Forms], antialiasing when drawing
ms.assetid: 48fc34f3-f236-4b01-a0cb-f0752e6d22ae
ms.openlocfilehash: 2adb33e3d05e38ee71be8a12cdc2e20dc8c55c72
ms.sourcegitcommit: ceca5a1c027627abcca2767567703c3879f33325
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/23/2018
ms.locfileid: "36338131"
---
# <a name="how-to-use-antialiasing-with-text"></a>方法: テキストでのアンチエイリアシングの使用
*アンチエイリアシング*描画されたグラフィックスとテキストの外観または読みやすさを向上させるにギザギザした境界のスムージングを指します。 マネージで[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]クラス、低品質テキストだけでなく、高画質のアンチ エイリアス化テキストを描画できます。 通常、高品質のレンダリングより低い品質レンダリング処理時間がかかります。 テキスト品質レベルを設定するには、設定、<xref:System.Drawing.Graphics.TextRenderingHint%2A>のプロパティ、<xref:System.Drawing.Graphics>の要素のいずれかに、<xref:System.Drawing.Text.TextRenderingHint>列挙型  
  
## <a name="example"></a>例  
 次のコード例では、2 つの異なる品質設定でテキストを描画します。  
  
 [!code-csharp[System.Drawing.FontsAndText#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
 
 次の図は、コード例の出力を示しています。  
  
 ![フォント テキスト](../../../../docs/framework/winforms/advanced/media/fontstext10.png "FontsText10")  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前のコード例は、Windows フォームで使用するために設計されていて、必要な<xref:System.Windows.Forms.PaintEventArgs> `e`、パラメーターのある<xref:System.Windows.Forms.PaintEventHandler>です。  
  
## <a name="see-also"></a>関連項目  
 [フォントとテキストの使用](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
