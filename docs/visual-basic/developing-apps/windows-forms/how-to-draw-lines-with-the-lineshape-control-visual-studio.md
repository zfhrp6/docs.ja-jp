---
title: '方法 : LineShape コントロールを使用して線を描画する (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- LineShape control [Visual Basic]
- lines, drawing
ms.assetid: 83e71b4e-aa76-4f9b-b547-8704309fd1e5
ms.openlocfilehash: 5e1a837578aab4b4609a58ffee46406b022b8f97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587346"
---
# <a name="how-to-draw-lines-with-the-lineshape-control-visual-studio"></a>方法 : LineShape コントロールを使用して線を描画する (Visual Studio)
使用することができます、<xref:Microsoft.VisualBasic.PowerPacks.LineShape>デザイン時および実行時の両方のフォームまたはコンテナー、水平、垂直、または斜めの線を描画するコントロール。  
  
 **注**コンピューター可能性があります異なる名前や場所がいくつかの Visual Studio ユーザー インターフェイス要素次の手順でします。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-draw-a-line-at-design-time"></a>デザイン時に線を描画するには  
  
1.  ドラッグ、<xref:Microsoft.VisualBasic.PowerPacks.LineShape>から制御、 **Visual Basic PowerPacks**  タブで、**ツールボックス**フォームまたはコンテナーのコントロールをドラッグします。  
  
2.  サイズ変更をドラッグし、サイズし、位置の行へのハンドルを移動します。  
  
     ことができますものサイズし、位置の行を変更して、 `X1`、 `X2`、 `Y1`、および`Y2`プロパティで、**プロパティ**ウィンドウです。  
  
3.  **プロパティ**ウィンドウで、必要に応じて設定その他のプロパティなど`BorderStyle`または`BorderColor`線の外観を変更します。  
  
### <a name="to-draw-a-line-at-run-time"></a>実行時に線を描画するには  
  
1.  **[プロジェクト]** メニューの **[参照の追加]** をクリックします。  
  
2.  **参照の追加**ダイアログ ボックスで、 **[microsoft.visualbasic.powerpacks.vs]**、順にクリック**OK**です。  
  
3.  **コード エディター**、追加、`Imports`または`using`モジュールの上部にあるステートメント。  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  `Event` プロシージャに次のコードを追加します。  
  
     [!code-csharp[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.PowerPacks.LineShape>  
 [ライン コントロールとシェイプ コントロールの概要](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [方法: OvalShape コントロールおよび RectangleShape コントロールを使用して図形を描画する](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)
