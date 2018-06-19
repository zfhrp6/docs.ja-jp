---
title: '方法 : DataRepeater コントロールでデータを検索する (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, implementing search
- DataRepeater, searching data
ms.assetid: a8ab5d17-b94f-43c4-8dd7-d0450226d73f
ms.openlocfilehash: 689990ee125c85c3151a4e965b619fde068d220e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588055"
---
# <a name="how-to-search-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="55616-102">方法 : DataRepeater コントロールでデータを検索する (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="55616-102">How to: Search Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="55616-103">使用する場合、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールを特定のレコードを使用すると、ユーザーによる検索をすることが多くのレコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="55616-103">When you are using a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control that contains many records, you may want to let users search for a specific record.</span></span> <span data-ttu-id="55616-104">基になるクエリを実行して、検索を実装するコントロール自体にデータを検索するのではなく<xref:System.Windows.Forms.BindingSource>です。</span><span class="sxs-lookup"><span data-stu-id="55616-104">Rather than searching the data in the control itself, you can implement a search by querying the underlying <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="55616-105">項目が見つかった場合、行うこともできますし、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A>プロパティを項目を選択し、スクロールして表示します。</span><span class="sxs-lookup"><span data-stu-id="55616-105">If the item is found, you can then use the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A> property to select the item and scroll it into view.</span></span>  
  
### <a name="to-implement-search"></a><span data-ttu-id="55616-106">検索を実装する</span><span class="sxs-lookup"><span data-stu-id="55616-106">To implement search</span></span>  
  
1.  <span data-ttu-id="55616-107"><xref:System.Windows.Forms.TextBox> コントロールが含まれるフォーム上に、 **ツールボックス** から <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="55616-107">Drag a <xref:System.Windows.Forms.TextBox> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="55616-108">[プロパティ] ウィンドウで、 **Name** プロパティを **SearchTextBox**に変更します。</span><span class="sxs-lookup"><span data-stu-id="55616-108">In the Properties window, change the **Name** property to **SearchTextBox**.</span></span>  
  
3.  <span data-ttu-id="55616-109"><xref:System.Windows.Forms.Button> コントロールが含まれるフォーム上に、 **ツールボックス** から <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="55616-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
4.  <span data-ttu-id="55616-110">[プロパティ] ウィンドウで、 **Name** プロパティを **SearchButton**に変更します。</span><span class="sxs-lookup"><span data-stu-id="55616-110">In the Properties window, change the **Name** property to **SearchButton**.</span></span> <span data-ttu-id="55616-111">**Text** プロパティを **Search**に変更します。</span><span class="sxs-lookup"><span data-stu-id="55616-111">Change the **Text** property to **Search**.</span></span>  
  
5.  <span data-ttu-id="55616-112"><xref:System.Windows.Forms.Button> コントロールをダブルクリックしてコード エディターを開き、 `SearchButton_Click` イベント ハンドラーに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="55616-112">Double-click the <xref:System.Windows.Forms.Button> control to open the Code Editor, and add the following code to the `SearchButton_Click` event handler.</span></span>  
  
     [!code-vb[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-search-data-in-a-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-search-data-in-a-datarepeater-control-visual-studio_1.cs)]  
  
     <span data-ttu-id="55616-113">置き換える*ProductsBindingSource*の名前を持つ、<xref:System.Windows.Forms.BindingSource>の<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>と置換*ProductID*を検索するフィールドの名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="55616-113">Replace *ProductsBindingSource* with the name of the <xref:System.Windows.Forms.BindingSource> for your <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, and replace *ProductID* with the name of the field that you want to search.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55616-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="55616-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="55616-115">DataRepeater コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="55616-115">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="55616-116">DataRepeater コントロールのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="55616-116">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="55616-117">方法: DataRepeater コントロールの外観を変更する</span><span class="sxs-lookup"><span data-stu-id="55616-117">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
