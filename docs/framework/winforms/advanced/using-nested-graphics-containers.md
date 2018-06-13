---
title: 入れ子になっているグラフィックス コンテナーの使用
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], nested containers
- graphics [Windows Forms], clipping
- graphics [Windows Forms], transformations in nested objects
ms.assetid: a0d9f178-43a4-4323-bb5a-d3e3f77ae6c1
ms.openlocfilehash: ba6bba84100a0ddcc87894710a6d3099ab0ccff5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529062"
---
# <a name="using-nested-graphics-containers"></a>入れ子になっているグラフィックス コンテナーの使用
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 置換またはで状態の一部を強化を一時的に使用できるコンテナーを提供する<xref:System.Drawing.Graphics>オブジェクト。 呼び出して、コンテナーを作成した、<xref:System.Drawing.Graphics.BeginContainer%2A>のメソッド、<xref:System.Drawing.Graphics>オブジェクト。 呼び出すことができます<xref:System.Drawing.Graphics.BeginContainer%2A>繰り返しを入れ子になったコンテナーを形成します。 各呼び出し<xref:System.Drawing.Graphics.BeginContainer%2A>への呼び出しと組み合わせる必要がある<xref:System.Drawing.Graphics.EndContainer%2A>です。  
  
## <a name="transformations-in-nested-containers"></a>入れ子になったコンテナー内の変換  
 次の例を作成、<xref:System.Drawing.Graphics>オブジェクトとそのコンテナー<xref:System.Drawing.Graphics>オブジェクト。 ワールド変換、<xref:System.Drawing.Graphics>オブジェクトが x 軸方向に 100 の翻訳単位であり、y 方向では 80 単位です。 コンテナーのワールド変換は、30 ° 回転します。 呼び出しは、コードは`DrawRectangle(pen, -60, -30, 120, 60)`2 回クリックします。 最初に呼び出す<xref:System.Drawing.Graphics.DrawRectangle%2A>; コンテナー内の呼び出しは、呼び出しの間に<xref:System.Drawing.Graphics.BeginContainer%2A>と<xref:System.Drawing.Graphics.EndContainer%2A>です。 2 番目の呼び出し<xref:System.Drawing.Graphics.DrawRectangle%2A>への呼び出し後は<xref:System.Drawing.Graphics.EndContainer%2A>します。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 上記のコードでは、コンテナー内から描画する四角形が最初に変換 (回転) コンテナーのワールド変換とのワールド変換、<xref:System.Drawing.Graphics>オブジェクト (変換)。 ワールド変換でのみ、コンテナーの外部から描画された四角形を変換、<xref:System.Drawing.Graphics>オブジェクト (変換)。 次の図は、次の 2 つの四角形を示します。  
  
 ![コンテナーを入れ子になった](../../../../docs/framework/winforms/advanced/media/csnestedcontainers1.png "csnestedcontainers1")  
  
## <a name="clipping-in-nested-containers"></a>入れ子になったコンテナー内の領域  
 次の例では、入れ子になったコンテナー クリッピング領域を処理します。 このコードを作成、<xref:System.Drawing.Graphics>オブジェクトとそのコンテナー<xref:System.Drawing.Graphics>オブジェクト。 クリッピング領域、<xref:System.Drawing.Graphics>オブジェクトは、四角形であり、コンテナーのクリッピング領域は楕円を描画します。 2 つの呼び出しは、コードは、<xref:System.Drawing.Graphics.DrawLine%2A>メソッドです。 最初の呼び出し<xref:System.Drawing.Graphics.DrawLine%2A>、コンテナー、および 2 番目の呼び出し内部にある<xref:System.Drawing.Graphics.DrawLine%2A>がコンテナーの範囲外です (呼び出しの後に<xref:System.Drawing.Graphics.EndContainer%2A>)。 最初の行が 2 つのクリッピング領域の交差点で切り取られます。 2 番目の行はの四角形のクリッピング領域によってのみクリップ、<xref:System.Drawing.Graphics>オブジェクト。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 次の図は、次の 2 つのクリップされた行を示します。  
  
 ![コンテナーを入れ子になった](../../../../docs/framework/winforms/advanced/media/nestedcontainers2.png "nestedcontainers2")  
  
 2 つの例のように変換およびクリッピング領域は入れ子になったコンテナーに累積されます。 コンテナーのワールド変換を設定した場合、<xref:System.Drawing.Graphics>オブジェクトの両方の変換は、コンテナー内から描画された項目に適用されます。 コンテナーの変換はされ、適用されている最初の変換、<xref:System.Drawing.Graphics>オブジェクトが適用されます。 コンテナーのクリッピング領域を設定した場合、<xref:System.Drawing.Graphics>オブジェクト、2 つのクリッピング領域の交差部分では、コンテナー内から描画された項目、クリップされます。  
  
## <a name="quality-settings-in-nested-containers"></a>入れ子になったコンテナーの画質の設定  
 品質の設定 (<xref:System.Drawing.Graphics.SmoothingMode%2A>、<xref:System.Drawing.Graphics.TextRenderingHint%2A>など) では入れ子になったコンテナーは累積されません。 代わりに、コンテナーの品質設定を一時的に交換の品質設定、<xref:System.Drawing.Graphics>オブジェクト。 新しいコンテナーを作成するときに、そのコンテナーの品質設定は、既定値に設定されます。 たとえば、ある場合、<xref:System.Drawing.Graphics>のスムージング モードを使ってオブジェクト<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>です。 コンテナーを作成するときに、コンテナー内のスムージング モードは既定のスムージング モードです。 自由に、コンテナーのスムージング モードを設定し、設定されているモードに従って、コンテナー内から描画された任意の項目を描画するか。 呼び出しの後に描画された項目<xref:System.Drawing.Graphics.EndContainer%2A>スムージング モードに基づいて描画されます (<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>) を呼び出す前に有効になっていたを<xref:System.Drawing.Graphics.BeginContainer%2A>です。  
  
## <a name="several-layers-of-nested-containers"></a>入れ子になったコンテナーの複数のレイヤー  
 1 つのコンテナーに限定されない、<xref:System.Drawing.Graphics>オブジェクト。 コンテナーのシーケンスを作成することができます、それぞれ、上記の入れ子になったおよびワールド変換、クリッピング領域、およびその入れ子になったコンテナーのそれぞれの品質設定を指定することができます。 メソッドを呼び出す場合、描画から最も内側のコンテナー、変換は、最も外側のコンテナーで最も内側のコンテナーで開始および終了の順序で適用されます。 最も内側のコンテナーから描画された項目は、すべてのクリッピング領域の交差点でクリッピングされます。  
  
 次の例を作成、<xref:System.Drawing.Graphics>オブジェクトし、レンダリングのヒントをテキストに設定<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>です。 コードでは、いずれかの入れ子、他の 2 つのコンテナーを作成します。 外側のコンテナーのテキスト レンダリングのヒントに設定されている<xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>、内側のコンテナーのテキスト レンダリングのヒントに設定されていると<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>です。 コードは、3 つの文字列を描画: から内側のコンテナー、外側のコンテナーから、1 つから 1 つ、<xref:System.Drawing.Graphics>オブジェクト自体です。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 次の図は、3 つの文字列を示します。 描画および内側のコンテナーから、文字列、<xref:System.Drawing.Graphics>によってオブジェクトが滑らかにします。 外側のコンテナーから描画された文字列がによって滑らかになっているため、<xref:System.Drawing.Graphics.TextRenderingHint%2A>プロパティに設定されている<xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>です。  
  
 ![コンテナーを入れ子になった](../../../../docs/framework/winforms/advanced/media/nestedcontainers3.png "nestedcontainers3")  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.Graphics>  
 [Graphics オブジェクトの状態の管理](../../../../docs/framework/winforms/advanced/managing-the-state-of-a-graphics-object.md)
