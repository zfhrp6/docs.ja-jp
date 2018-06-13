---
title: '方法 : TabControl を使用して側面に位置を合わせて表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tab pages [Windows Forms], displaying side-aligned tabs
- tabs [Windows Forms], displaying side-aligned tabs
- TabControl control [Windows Forms], displaying side-aligned tabs
ms.assetid: 110d5abd-3ae3-4ded-95bf-778aaac798a0
ms.openlocfilehash: e145547ba4c8648a765e9507b7f35e50cb15fd82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532462"
---
# <a name="how-to-display-side-aligned-tabs-with-tabcontrol"></a><span data-ttu-id="ee06b-102">方法 : TabControl を使用して側面に位置を合わせて表示する</span><span class="sxs-lookup"><span data-stu-id="ee06b-102">How to: Display Side-Aligned Tabs with TabControl</span></span>
<span data-ttu-id="ee06b-103"><xref:System.Windows.Forms.TabControl> の <xref:System.Windows.Forms.TabControl.Alignment%2A> プロパティは、水平方向 (コントロールの上部または下部) ではなく、垂直方向 (コントロールの左端または右端) でのタブの表示をサポートします。</span><span class="sxs-lookup"><span data-stu-id="ee06b-103">The <xref:System.Windows.Forms.TabControl.Alignment%2A> property of <xref:System.Windows.Forms.TabControl> supports displaying tabs vertically (along the left or right edge of the control), as opposed to horizontally (across the top or bottom of the control).</span></span> <span data-ttu-id="ee06b-104"><xref:System.Windows.Forms.TabPage> オブジェクトの <xref:System.Windows.Forms.TabPage.Text%2A> プロパティは、視覚スタイルを有効にしたときにタブが表示されないため、既定では、この垂直方向の表示はユーザーの操作性が低下します。</span><span class="sxs-lookup"><span data-stu-id="ee06b-104">By default, this vertical display results in a poor user experience, because the <xref:System.Windows.Forms.TabPage.Text%2A> property of the <xref:System.Windows.Forms.TabPage> object does not display in the tab when visual styles are enabled.</span></span> <span data-ttu-id="ee06b-105">また、タブ内のテキストの方向を制御する直接的な方法がありません。この操作性を向上させるために、<xref:System.Windows.Forms.TabControl> でオーナー描画を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ee06b-105">There is also no direct way to control the direction of the text within the tab. You can use owner draw on <xref:System.Windows.Forms.TabControl> to improve this experience.</span></span>  
  
 <span data-ttu-id="ee06b-106">次の手順では、「オーナー描画」機能を使用して、タブのテキストが左から右に実行されているときに、右揃えのタブを表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ee06b-106">The following procedure shows how to render right-aligned tabs, with the tab text running from left to right, by using the "owner draw" feature.</span></span>  
  
### <a name="to-display-right-aligned-tabs"></a><span data-ttu-id="ee06b-107">右揃えのタブを表示するには</span><span class="sxs-lookup"><span data-stu-id="ee06b-107">To display right-aligned tabs</span></span>  
  
1.  <span data-ttu-id="ee06b-108"><xref:System.Windows.Forms.TabControl> をフォームに追加します。</span><span class="sxs-lookup"><span data-stu-id="ee06b-108">Add a <xref:System.Windows.Forms.TabControl> to your form.</span></span>  
  
2.  <span data-ttu-id="ee06b-109"><xref:System.Windows.Forms.TabControl.Alignment%2A> プロパティを <xref:System.Windows.Forms.TabAlignment.Right> に設定します。</span><span class="sxs-lookup"><span data-stu-id="ee06b-109">Set the <xref:System.Windows.Forms.TabControl.Alignment%2A> property to <xref:System.Windows.Forms.TabAlignment.Right>.</span></span>  
  
3.  <span data-ttu-id="ee06b-110"><xref:System.Windows.Forms.TabControl.SizeMode%2A> プロパティを <xref:System.Windows.Forms.TabSizeMode.Fixed> に設定して、すべてのタブが同じ幅になるようにします。</span><span class="sxs-lookup"><span data-stu-id="ee06b-110">Set the <xref:System.Windows.Forms.TabControl.SizeMode%2A> property to <xref:System.Windows.Forms.TabSizeMode.Fixed>, so that all tabs are the same width.</span></span>  
  
4.  <span data-ttu-id="ee06b-111">タブの <xref:System.Windows.Forms.TabControl.ItemSize%2A> プロパティを任意の固定サイズに設定します。</span><span class="sxs-lookup"><span data-stu-id="ee06b-111">Set the <xref:System.Windows.Forms.TabControl.ItemSize%2A> property to the preferred fixed size for the tabs.</span></span> <span data-ttu-id="ee06b-112"><xref:System.Windows.Forms.TabControl.ItemSize%2A> プロパティは、タブが右揃えでも、最上部にあるように機能することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ee06b-112">Keep in mind that the <xref:System.Windows.Forms.TabControl.ItemSize%2A> property behaves as though the tabs were on top, although they are right-aligned.</span></span> <span data-ttu-id="ee06b-113">その結果、タブを広くするには <xref:System.Drawing.Size.Height%2A> プロパティを変更する必要があり、高くするには <xref:System.Drawing.Size.Width%2A> プロパティを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee06b-113">As a result, in order to make the tabs wider, you must change the <xref:System.Drawing.Size.Height%2A> property, and in order to make them taller, you must change the <xref:System.Drawing.Size.Width%2A> property.</span></span>  
  
     <span data-ttu-id="ee06b-114">次のコード例で最適な結果を得るには、タブの <xref:System.Drawing.Size.Width%2A> を 25 に設定し、<xref:System.Drawing.Size.Height%2A> を 100 に設定します。</span><span class="sxs-lookup"><span data-stu-id="ee06b-114">For best result with the code example below, set the <xref:System.Drawing.Size.Width%2A> of the tabs to 25 and the <xref:System.Drawing.Size.Height%2A> to 100.</span></span>  
  
5.  <span data-ttu-id="ee06b-115"><xref:System.Windows.Forms.TabControl.DrawMode%2A> プロパティを <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> に設定します。</span><span class="sxs-lookup"><span data-stu-id="ee06b-115">Set the <xref:System.Windows.Forms.TabControl.DrawMode%2A> property to <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.</span></span>  
  
6.  <span data-ttu-id="ee06b-116">テキストを左から右に表示する <xref:System.Windows.Forms.TabControl> の <xref:System.Windows.Forms.TabControl.DrawItem> イベントのハンドラーを定義します。</span><span class="sxs-lookup"><span data-stu-id="ee06b-116">Define a handler for the <xref:System.Windows.Forms.TabControl.DrawItem> event of <xref:System.Windows.Forms.TabControl> that renders the text from left to right.</span></span>  
  
     [!code-csharp[TabControl.RightAlignedTabs#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/TabControl.RightAlignedTabs/CS/Form1.cs#1)]
     [!code-vb[TabControl.RightAlignedTabs#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/TabControl.RightAlignedTabs/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ee06b-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="ee06b-117">See Also</span></span>  
 [<span data-ttu-id="ee06b-118">TabControl コントロール</span><span class="sxs-lookup"><span data-stu-id="ee06b-118">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)
