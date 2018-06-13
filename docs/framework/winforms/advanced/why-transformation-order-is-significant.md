---
title: 変換順序が重要となる理由
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], order signficance
ms.assetid: 37d5f9dc-a5cf-4475-aa5d-34d714e808a9
ms.openlocfilehash: 943bfa73b54a1ac5d68d21d2bb6e271133db595a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526078"
---
# <a name="why-transformation-order-is-significant"></a>変換順序が重要となる理由
1 つ<xref:System.Drawing.Drawing2D.Matrix>オブジェクトは、単一の変換または変換のシーケンスを格納できます。 後者を複合変換と呼びます。 複合変換のマトリックスは、個々 の変換行列を乗算することによって取得されます。  
  
## <a name="composite-transform-examples"></a>複合変換の例  
 複合変換では、個々 の変換の順序が重要です。 など、回転、まずしてから、スケール、変換、最初に変換する場合、回転し、スケールよりも異なる結果が得です。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]、複合変換は、左から右に構築されます。 S、R、T は、スケール、回転、および平行移動行列をそれぞれが場合、し、製品 (その順序で) SRT 複合変換のマトリックスを最初にスケーリングは回転し、変換します。 製品によって生成されるマトリックス SRT は、製品 TRS によって生成されるマトリックスと異なります。  
  
 順序は重要な理由の 1 つは、座標系の原点を基準の回転とスケーリングのような変換を行うことです。 原点を中心とするオブジェクトをスケーリングすると、原点から離れているオブジェクトをスケーリング異なる結果が生成されます。 同様に、原点を中心とするオブジェクトを回転させるには、原点から離れているオブジェクトを回転異なる結果が生成されます。  
  
 次の例では、複合変換を拡大/縮小、回転、およびその順序で翻訳を結合します。 引数<xref:System.Drawing.Drawing2D.MatrixOrder.Append>に渡される、<xref:System.Drawing.Graphics.RotateTransform%2A>メソッドでは、拡大/縮小、回転を従うことを示します。 同様に、引数<xref:System.Drawing.Drawing2D.MatrixOrder.Append>に渡される、<xref:System.Drawing.Graphics.TranslateTransform%2A>メソッドは、翻訳は、回転に従うことを示します。 <xref:System.Drawing.Drawing2D.MatrixOrder.Append> および<xref:System.Drawing.Drawing2D.MatrixOrder.Prepend>のメンバーである、<xref:System.Drawing.Drawing2D.MatrixOrder>列挙します。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#21)]  
  
 次の例で、前の例と同じメソッドを呼び出してが、呼び出しの順序を反転します。 操作の結果として得られる順序が最初に平行移動、回転、最初の小数点以下桁数よりも大幅に異なる結果を生成するには、小数点以下桁数を回転させて、し、変換します。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#22)]  
  
 複合変換の個々 の変換の順序を反転させる 1 つの方法は、一連のメソッド呼び出しの順序を逆です。 操作の順序を制御する 2 番目の方法では、マトリックスの order 引数を変更します。 次の例は、点を除いて、上記の例と同じ<xref:System.Drawing.Drawing2D.MatrixOrder.Append>に変わりました<xref:System.Drawing.Drawing2D.MatrixOrder.Prepend>です。 SRT、S、R、T があるスケールのマトリックスの順序では、行列乗算を実行してください。、回転、および翻訳に、それぞれします。 複合変換の順序は最初の小数点以下桁数、回転、変換します。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#23)]  
  
 直前の例の結果は、このトピックの最初の例の結果と同じです。 これは、メソッド呼び出しの順序と行列乗算の順序の両方は元に戻すためにです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.Drawing2D.Matrix>  
 [座標系と変換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [マネージ GDI+ での変換の使用](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
