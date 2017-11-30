---
title: "方法 : LineShape コントロールを使用して線を描画する (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- LineShape control [Visual Basic]
- lines, drawing
ms.assetid: 83e71b4e-aa76-4f9b-b547-8704309fd1e5
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f170250dde2f6db31ed68908936c0e9714a7e846
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-lines-with-the-lineshape-control-visual-studio"></a><span data-ttu-id="ddd20-102">方法 : LineShape コントロールを使用して線を描画する (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="ddd20-102">How to: Draw Lines with the LineShape Control (Visual Studio)</span></span>
<span data-ttu-id="ddd20-103">使用することができます、<xref:Microsoft.VisualBasic.PowerPacks.LineShape>デザイン時および実行時の両方のフォームまたはコンテナー、水平、垂直、または斜めの線を描画するコントロール。</span><span class="sxs-lookup"><span data-stu-id="ddd20-103">You can use the <xref:Microsoft.VisualBasic.PowerPacks.LineShape> control to draw horizontal, vertical, or diagonal lines on a form or container, both at design time and at run time.</span></span>  
  
 <span data-ttu-id="ddd20-104">**注**コンピューター可能性があります異なる名前や場所がいくつかの Visual Studio ユーザー インターフェイス要素次の手順でします。</span><span class="sxs-lookup"><span data-stu-id="ddd20-104">**Note** Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions.</span></span> <span data-ttu-id="ddd20-105">これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。</span><span class="sxs-lookup"><span data-stu-id="ddd20-105">The Visual Studio edition that you have and the settings that you use determine these elements.</span></span> <span data-ttu-id="ddd20-106">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddd20-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-draw-a-line-at-design-time"></a><span data-ttu-id="ddd20-107">デザイン時に線を描画するには</span><span class="sxs-lookup"><span data-stu-id="ddd20-107">To draw a line at design time</span></span>  
  
1.  <span data-ttu-id="ddd20-108">ドラッグ、<xref:Microsoft.VisualBasic.PowerPacks.LineShape>から制御、 **Visual Basic PowerPacks**  タブで、**ツールボックス**フォームまたはコンテナーのコントロールをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ddd20-108">Drag the <xref:Microsoft.VisualBasic.PowerPacks.LineShape> control from the **Visual Basic PowerPacks** tab in the **Toolbox** drag to a form or container control.</span></span>  
  
2.  <span data-ttu-id="ddd20-109">サイズ変更をドラッグし、サイズし、位置の行へのハンドルを移動します。</span><span class="sxs-lookup"><span data-stu-id="ddd20-109">Drag the sizing and move handles to size and position the line.</span></span>  
  
     <span data-ttu-id="ddd20-110">ことができますものサイズし、位置の行を変更して、 `X1`、 `X2`、 `Y1`、および`Y2`プロパティで、**プロパティ**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="ddd20-110">You can also size and position the line by changing the `X1`, `X2`, `Y1`, and `Y2` properties in the **Properties** window.</span></span>  
  
3.  <span data-ttu-id="ddd20-111">**プロパティ**ウィンドウで、必要に応じて設定その他のプロパティなど`BorderStyle`または`BorderColor`線の外観を変更します。</span><span class="sxs-lookup"><span data-stu-id="ddd20-111">In the **Properties** window, optionally set additional properties such as `BorderStyle` or `BorderColor` to change the appearance of the line.</span></span>  
  
### <a name="to-draw-a-line-at-run-time"></a><span data-ttu-id="ddd20-112">実行時に線を描画するには</span><span class="sxs-lookup"><span data-stu-id="ddd20-112">To draw a line at run time</span></span>  
  
1.  <span data-ttu-id="ddd20-113">**[プロジェクト]** メニューの **[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ddd20-113">On the **Project** menu, click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="ddd20-114">**参照の追加**ダイアログ ボックスで、 **[microsoft.visualbasic.powerpacks.vs]**、順にクリック**OK**です。</span><span class="sxs-lookup"><span data-stu-id="ddd20-114">In the **Add Reference** dialog box, select **Microsoft.VisualBasic.PowerPacks.VS**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="ddd20-115">**コード エディター**、追加、`Imports`または`using`モジュールの上部にあるステートメント。</span><span class="sxs-lookup"><span data-stu-id="ddd20-115">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  <span data-ttu-id="ddd20-116">`Event` プロシージャに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="ddd20-116">Add the following code in an `Event` procedure:</span></span>  
  
     [!code-csharp[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ddd20-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="ddd20-117">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.LineShape>  
 [<span data-ttu-id="ddd20-118">ライン コントロールとシェイプ コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="ddd20-118">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [<span data-ttu-id="ddd20-119">方法: OvalShape コントロールおよび RectangleShape コントロールを使用して図形を描画する</span><span class="sxs-lookup"><span data-stu-id="ddd20-119">How to: Draw Shapes with the OvalShape and RectangleShape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)
