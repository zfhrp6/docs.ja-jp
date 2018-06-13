---
title: '方法: 2 つの DataRepeater コントロール (Visual Studio) を使用してマスター/詳細フォームを作成します。'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, master/detail tables
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
ms.openlocfilehash: 84639a5d49a3fa4a8c6845793c39fc8a67c31e02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590908"
---
# <a name="how-to-create-a-masterdetail-form-by-using-two-datarepeater-controls-visual-studio"></a><span data-ttu-id="1d96a-102">方法 : 2 つの DataRepeater コントロールを使用してマスター/詳細形式のフォームを作成する (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="1d96a-102">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>
<span data-ttu-id="1d96a-103">関連するデータを表示するには 2 つ以上を使用して<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>マスター/詳細フォームを作成するコントロール。</span><span class="sxs-lookup"><span data-stu-id="1d96a-103">You can display related data by using two or more <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controls to create a master/detail form.</span></span> <span data-ttu-id="1d96a-104">いずれかで顧客の一覧を表示するなど、 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>、ユーザーは、顧客を選択するときに、1 秒あたりその顧客の注文の一覧を表示および<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>です。</span><span class="sxs-lookup"><span data-stu-id="1d96a-104">For example, you might want to display a list of customers in one <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, and when the user selects a customer, display a list of that customer's orders in a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span></span>  
  
 <span data-ttu-id="1d96a-105">関連するデータを表示するには、同じマスター テーブルのノードから共有詳細項目をドラッグして、**データ ソース** ウィンドウ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。</span><span class="sxs-lookup"><span data-stu-id="1d96a-105">You can display related data by dragging detail items that share the same master table node from the **Data Sources** window onto a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="1d96a-106">たとえば、Customers テーブルと関連する Orders テーブルを持つデータ ソースがあれば、両方のテーブルとして表示ツリー ビューで、最上位のノード、**データソース**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="1d96a-106">For example, if you have a data source that has a Customers table and a related Orders table, you see both tables as top-level nodes in the tree view in the **Data Sources** window.</span></span> <span data-ttu-id="1d96a-107">列を認識できるように、Customers ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="1d96a-107">Expand the Customers node so that you can see the columns.</span></span> <span data-ttu-id="1d96a-108">一覧の最後の列は、Orders テーブルを表す展開可能なノードであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1d96a-108">Notice that the last column in the list is an expandable node that represents the Orders table.</span></span> <span data-ttu-id="1d96a-109">このノードは、顧客に関連する注文を表します。</span><span class="sxs-lookup"><span data-stu-id="1d96a-109">This node represents the related orders for a customer.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-display-related-data-in-two-datarepeater-controls"></a><span data-ttu-id="1d96a-110">2 つの DataRepeater コントロールに関連するデータを表示するには</span><span class="sxs-lookup"><span data-stu-id="1d96a-110">To display related data in two DataRepeater controls</span></span>  
  
1.  <span data-ttu-id="1d96a-111">2 つをドラッグして<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>から制御、 **Visual Basic PowerPacks**  タブで、**ツールボックス**フォームまたはコンテナー コントロールにします。</span><span class="sxs-lookup"><span data-stu-id="1d96a-111">Drag two <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controls from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="1d96a-112">コントロールをサイズ変更、サイド バイ サイド配置へのサイズと位置のハンドルをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="1d96a-112">Drag the sizing and position handles to size the controls and position them side-by-side.</span></span>  
  
3.  <span data-ttu-id="1d96a-113">**[データ]** メニューの **[データ ソースの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d96a-113">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1d96a-114">場合、**データソース**ウィンドウが空の場合に、データ ソースを追加します。</span><span class="sxs-lookup"><span data-stu-id="1d96a-114">If the **Data Sources** window is empty, add a data source to it.</span></span> <span data-ttu-id="1d96a-115">詳細については、「[新しいデータ ソースの追加](/visualstudio/data-tools/add-new-data-sources)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d96a-115">For more information, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
4.  <span data-ttu-id="1d96a-116">**データソース**ウィンドウで、マスター テーブルの最上位ノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="1d96a-116">In the **Data Sources** window, select the top-level node for the master table.</span></span>  
  
5.  <span data-ttu-id="1d96a-117">クリックして、マスター テーブルのドロップ タイプの詳細に変更**詳細**テーブル ノードのドロップダウン リストでします。</span><span class="sxs-lookup"><span data-stu-id="1d96a-117">Change the drop type of the master table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="1d96a-118">最初の項目テンプレート領域上にマスター テーブル ノードをドラッグして<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。</span><span class="sxs-lookup"><span data-stu-id="1d96a-118">Drag the master table node onto the item template region of the first <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
7.  <span data-ttu-id="1d96a-119">マスター テーブル ノードを展開し、関連するテーブルの詳細ノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="1d96a-119">Expand the master table node and select the detail node for the related table.</span></span>  
  
8.  <span data-ttu-id="1d96a-120">クリックして、[詳細] テーブルのドロップ タイプの詳細に変更**詳細**テーブル ノードのドロップダウン リストでします。</span><span class="sxs-lookup"><span data-stu-id="1d96a-120">Change the drop type of the detail table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
9. <span data-ttu-id="1d96a-121">このテーブル ノードを選択し、2 番目の項目テンプレート領域にドラッグ<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。</span><span class="sxs-lookup"><span data-stu-id="1d96a-121">Select this table node and drag it onto the item template region of the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d96a-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d96a-122">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="1d96a-123">DataRepeater コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="1d96a-123">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="1d96a-124">方法: DataRepeater コントロールに、バインドされたデータを表示する</span><span class="sxs-lookup"><span data-stu-id="1d96a-124">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="1d96a-125">方法: 関連するデータを Windows フォーム アプリケーションに表示する</span><span class="sxs-lookup"><span data-stu-id="1d96a-125">How to: Display Related Data in a Windows Forms Application</span></span>](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)  
 [<span data-ttu-id="1d96a-126">方法: DataRepeater コントロールの外観を変更する</span><span class="sxs-lookup"><span data-stu-id="1d96a-126">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="1d96a-127">DataRepeater コントロールのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="1d96a-127">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
