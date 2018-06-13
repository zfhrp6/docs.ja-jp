---
title: '方法 : ドラッグされた GridView 列ヘッダーのスタイルを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 0b999645-0313-4b33-80b9-19ece08b5459
ms.openlocfilehash: 2e57b4cb1b8ddb90e8e6e0abc6db3e7f0b864cfa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554574"
---
# <a name="how-to-create-a-style-for-a-dragged-gridview-column-header"></a><span data-ttu-id="8e476-102">方法 : ドラッグされた GridView 列ヘッダーのスタイルを作成する</span><span class="sxs-lookup"><span data-stu-id="8e476-102">How to: Create a Style for a Dragged GridView Column Header</span></span>
<span data-ttu-id="8e476-103">この例は、ドラッグしたの外観を変更する方法を示します<xref:System.Windows.Controls.GridViewColumnHeader>ユーザーが列の位置を変更するときにします。</span><span class="sxs-lookup"><span data-stu-id="8e476-103">This example shows how to change the appearance of a dragged <xref:System.Windows.Controls.GridViewColumnHeader> when the user changes the position of a column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e476-104">例</span><span class="sxs-lookup"><span data-stu-id="8e476-104">Example</span></span>  
 <span data-ttu-id="8e476-105">内の別の場所に列ヘッダーをドラッグすると、<xref:System.Windows.Controls.ListView>を使用して<xref:System.Windows.Controls.GridView>その表示モードの場合、列が新しい位置へ移動します。</span><span class="sxs-lookup"><span data-stu-id="8e476-105">When you drag a column header to another location in a <xref:System.Windows.Controls.ListView> that uses <xref:System.Windows.Controls.GridView> for its view mode, the column moves to the new position.</span></span> <span data-ttu-id="8e476-106">列ヘッダーをドラッグすると、元のヘッダーだけでなく、ヘッダーの浮動小数点のコピーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8e476-106">While you are dragging the column header, a floating copy of the header appears in addition to the original header.</span></span> <span data-ttu-id="8e476-107">列ヘッダーを<xref:System.Windows.Controls.GridView>で表される、<xref:System.Windows.Controls.GridViewColumnHeader>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8e476-107">A column header in a <xref:System.Windows.Controls.GridView> is represented by a <xref:System.Windows.Controls.GridViewColumnHeader> object.</span></span>  
  
 <span data-ttu-id="8e476-108">浮動小数点と元の両方のヘッダーの外観をカスタマイズするには設定<xref:System.Windows.Controls.ControlTemplate.Triggers%2A>を変更する、 <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>です。</span><span class="sxs-lookup"><span data-stu-id="8e476-108">To customize the appearance of both the floating and original headers, you can set <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> to modify the <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>.</span></span> <span data-ttu-id="8e476-109">これら<xref:System.Windows.Controls.ControlTemplate.Triggers%2A>場合に適用されます、<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A>プロパティの値が`true`と<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A>プロパティの値が<xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>です。</span><span class="sxs-lookup"><span data-stu-id="8e476-109">These <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> are applied when the <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> property value is `true` and the <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> property value is <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span></span>  
  
 <span data-ttu-id="8e476-110">ユーザーがマウス ボタンを押すし、を押したことで、マウスが一時停止中に、 <xref:System.Windows.Controls.GridViewColumnHeader>、<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A>プロパティの値に変更`true`です。</span><span class="sxs-lookup"><span data-stu-id="8e476-110">When the user presses the mouse button and holds it down while the mouse pauses on the <xref:System.Windows.Controls.GridViewColumnHeader>, the <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> property value changes to `true`.</span></span> <span data-ttu-id="8e476-111">同様に、ユーザーがドラッグ操作を開始するとき、<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A>プロパティに対する変更を<xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>です。</span><span class="sxs-lookup"><span data-stu-id="8e476-111">Likewise, when the user begins the drag operation, the <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> property changes to <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span></span>  
  
 <span data-ttu-id="8e476-112">次の例は、設定する方法を示します<xref:System.Windows.Controls.ControlTemplate.Triggers%2A>を変更する、<xref:System.Windows.Controls.Control.Foreground%2A>と<xref:System.Windows.Controls.Control.Background%2A>元および浮動小数点のヘッダー、ユーザーが列の新しい位置にドラッグしたときの色。</span><span class="sxs-lookup"><span data-stu-id="8e476-112">The following example shows how to set <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> to change the <xref:System.Windows.Controls.Control.Foreground%2A> and <xref:System.Windows.Controls.Control.Background%2A> colors of the original and floating headers when the user drags a column to a new position.</span></span>  
  
 [!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplatestart)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersstart)]  
[!code-xaml[ListViewHeaderRoleStyle#IsPressed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#ispressed)]  
[!code-xaml[ListViewHeaderRoleStyle#Floating](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#floating)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersend)]  
[!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplateend)]  
  
## <a name="see-also"></a><span data-ttu-id="8e476-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="8e476-113">See Also</span></span>  
 <xref:System.Windows.Controls.GridViewColumnHeader>  
 <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="8e476-114">方法トピック</span><span class="sxs-lookup"><span data-stu-id="8e476-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="8e476-115">ListView の概要</span><span class="sxs-lookup"><span data-stu-id="8e476-115">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="8e476-116">GridView の概要</span><span class="sxs-lookup"><span data-stu-id="8e476-116">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
