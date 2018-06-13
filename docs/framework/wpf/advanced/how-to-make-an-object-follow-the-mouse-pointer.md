---
title: '方法 : オブジェクトをマウス ポインターに追従させる'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- following the mouse pointer (cursor)
- mouse pointer (cursor), making objects follow
- cursor (mouse pointer), making objects follow
ms.assetid: 50b20415-14bc-405c-baf3-2fb254fffde3
ms.openlocfilehash: 860b42f4dc068bc3063001e25e8b012c50b59213
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543873"
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a><span data-ttu-id="1c6e2-102">方法 : オブジェクトをマウス ポインターに追従させる</span><span class="sxs-lookup"><span data-stu-id="1c6e2-102">How to: Make an Object Follow the Mouse Pointer</span></span>
<span data-ttu-id="1c6e2-103">この例では、マウス ポインターを画面に移動すると、オブジェクトのサイズを変更する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1c6e2-103">This example shows how to change the dimensions of an object when the mouse pointer moves on the screen.</span></span>  
  
 <span data-ttu-id="1c6e2-104">この例では、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイルを作成する、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]とイベント ハンドラーを作成する分離コード ファイル。</span><span class="sxs-lookup"><span data-stu-id="1c6e2-104">The example includes an [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file that creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] and a code-behind file that creates the event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c6e2-105">例</span><span class="sxs-lookup"><span data-stu-id="1c6e2-105">Example</span></span>  
 <span data-ttu-id="1c6e2-106">次[!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)]を作成、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]から構成される、<xref:System.Windows.Shapes.Ellipse>内の<xref:System.Windows.Controls.StackPanel>、対応するイベント ハンドラーをアタッチし、<xref:System.Windows.UIElement.MouseMove>イベント。</span><span class="sxs-lookup"><span data-stu-id="1c6e2-106">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], which consists of an <xref:System.Windows.Shapes.Ellipse> inside of a <xref:System.Windows.Controls.StackPanel>, and attaches the event handler for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 <span data-ttu-id="1c6e2-107">次のコードを作成、<xref:System.Windows.UIElement.MouseMove>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="1c6e2-107">The following code behind creates the <xref:System.Windows.UIElement.MouseMove> event handler.</span></span>  <span data-ttu-id="1c6e2-108">マウス ポインターを置いたとき、高さと幅、<xref:System.Windows.Shapes.Ellipse>はして増減します。</span><span class="sxs-lookup"><span data-stu-id="1c6e2-108">When the mouse pointer moves, the height and the width of the <xref:System.Windows.Shapes.Ellipse> are increased and decreased.</span></span>  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a><span data-ttu-id="1c6e2-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="1c6e2-109">See Also</span></span>  
 [<span data-ttu-id="1c6e2-110">入力の概要</span><span class="sxs-lookup"><span data-stu-id="1c6e2-110">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)
