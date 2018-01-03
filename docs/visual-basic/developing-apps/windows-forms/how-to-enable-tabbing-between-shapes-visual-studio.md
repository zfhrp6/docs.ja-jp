---
title: "方法 : 図形間のタブ移動を有効にする (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Line control [Visual Basic], implementing tabbing
- Shape control [Visual Basic], implementing tabbing
ms.assetid: 09731b34-3900-4fcb-a9df-ce5280328433
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0b1e8b0378e65becd80324491632ecd8dbffdbbf
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-enable-tabbing-between-shapes-visual-studio"></a><span data-ttu-id="f8f67-102">方法 : 図形間のタブ移動を有効にする (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="f8f67-102">How to: Enable Tabbing Between Shapes (Visual Studio)</span></span>
<span data-ttu-id="f8f67-103">ライン コントロールとシェイプ コントロールはありません`TabStop`または`TabIndex`プロパティも、することができますも有効にそれらの間のタブ移動します。</span><span class="sxs-lookup"><span data-stu-id="f8f67-103">Line and shape controls do not have `TabStop` or `TabIndex` properties, but you can still enable tabbing among them.</span></span> <span data-ttu-id="f8f67-104">次の例では、図形間で、ctrl キーと TAB キーを押してはタブします。ボタンの間 タブは TAB キーのみです。</span><span class="sxs-lookup"><span data-stu-id="f8f67-104">In the following example, pressing both the CTRL and the TAB keys will tab between shapes; pressing only the TAB key will tab between the buttons.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8f67-105">次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f8f67-105">Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions.</span></span> <span data-ttu-id="f8f67-106">これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。</span><span class="sxs-lookup"><span data-stu-id="f8f67-106">The Visual Studio edition that you have and the settings that you use determine these elements.</span></span> <span data-ttu-id="f8f67-107">詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8f67-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="to-enable-tabbing-among-shapes"></a><span data-ttu-id="f8f67-108">図形間のタブ移動を有効にするには</span><span class="sxs-lookup"><span data-stu-id="f8f67-108">To enable tabbing among shapes</span></span>  
  
1.  <span data-ttu-id="f8f67-109">3 つをドラッグして<xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>コントロールと 2 つ<xref:System.Windows.Forms.Button>から制御、**ツールボックス**をフォームにします。</span><span class="sxs-lookup"><span data-stu-id="f8f67-109">Drag three <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> controls and two <xref:System.Windows.Forms.Button> controls from the **Toolbox** to a form.</span></span>  
  
2.  <span data-ttu-id="f8f67-110">**コード エディター**、追加、`Imports`または`using`モジュールの上部にあるステートメント。</span><span class="sxs-lookup"><span data-stu-id="f8f67-110">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  

3.  <span data-ttu-id="f8f67-111">イベント プロシージャでは、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="f8f67-111">Add the following code in an event procedure:</span></span>  
  
[!code-csharp[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_1.cs)]
[!code-vb[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_1.vb)]  
  
4.  <span data-ttu-id="f8f67-112">次のコードを追加、`Button1_PreviewKeyDown`イベント プロシージャ。</span><span class="sxs-lookup"><span data-stu-id="f8f67-112">Add the following code in the `Button1_PreviewKeyDown` event procedure:</span></span>  
  
[!code-csharp[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_2.cs)]
[!code-vb[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f8f67-113">参照</span><span class="sxs-lookup"><span data-stu-id="f8f67-113">See Also</span></span>  
 [<span data-ttu-id="f8f67-114">方法: OvalShape コントロールおよび RectangleShape コントロールを使用して図形を描画する</span><span class="sxs-lookup"><span data-stu-id="f8f67-114">How to: Draw Shapes with the OvalShape and RectangleShape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)  
 [<span data-ttu-id="f8f67-115">方法: LineShape コントロールを使用して線を描画する</span><span class="sxs-lookup"><span data-stu-id="f8f67-115">How to: Draw Lines with the LineShape Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)  
 [<span data-ttu-id="f8f67-116">ライン コントロールとシェイプ コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="f8f67-116">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)
