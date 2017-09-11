---
title: "方法:&2; つの DataRepeater コントロール (Visual Studio) を使用してマスター/詳細フォームを作成 |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, master/detail tables
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 4ed0b1fa0e7fac96cef3bde61efac66681f2507b
ms.contentlocale: ja-jp
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-create-a-masterdetail-form-by-using-two-datarepeater-controls-visual-studio"></a><span data-ttu-id="89904-102">方法 :&2; つの DataRepeater コントロールを使用してマスター/詳細形式のフォームを作成する (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="89904-102">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>
<span data-ttu-id="89904-103">2 つ以上を使用して関連データを表示できる<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>マスター/詳細フォームを作成するコントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="89904-103">You can display related data by using two or more <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controls to create a master/detail form.</span></span> <span data-ttu-id="89904-104">いずれかで顧客の一覧を表示するなど、 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>、ユーザーは、顧客を選択するときに、1 秒あたり<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>その顧客の注文の一覧を表示および</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="89904-104">For example, you might want to display a list of customers in one <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, and when the user selects a customer, display a list of that customer's orders in a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span></span>  
  
 <span data-ttu-id="89904-105">共有から同じマスター テーブル ノードの詳細項目をドラッグして関連データを表示できる、**データ ソース**ウィンドウ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="89904-105">You can display related data by dragging detail items that share the same master table node from the **Data Sources** window onto a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="89904-106">たとえば、Customers テーブルと関連する Orders テーブルを持つデータ ソースがあれば、両方のテーブルとして表示ツリー ビューで、最上位ノード、**データソース**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="89904-106">For example, if you have a data source that has a Customers table and a related Orders table, you see both tables as top-level nodes in the tree view in the **Data Sources** window.</span></span> <span data-ttu-id="89904-107">列が表示されるように、Customers ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="89904-107">Expand the Customers node so that you can see the columns.</span></span> <span data-ttu-id="89904-108">一覧の最後の列は、Orders テーブルを表す展開可能なノードであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="89904-108">Notice that the last column in the list is an expandable node that represents the Orders table.</span></span> <span data-ttu-id="89904-109">このノードは、顧客に関連する注文を表します。</span><span class="sxs-lookup"><span data-stu-id="89904-109">This node represents the related orders for a customer.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-display-related-data-in-two-datarepeater-controls"></a><span data-ttu-id="89904-110">2 つの DataRepeater コントロールに関連するデータを表示するには</span><span class="sxs-lookup"><span data-stu-id="89904-110">To display related data in two DataRepeater controls</span></span>  
  
1.  <span data-ttu-id="89904-111">2 つをドラッグして<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールを**Visual Basic power Packs**  タブで、**ツールボックス**フォームまたはコンテナー コントロールにします</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="89904-111">Drag two <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controls from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="89904-112">コントロールをサイズ変更、サイド バイ サイドの配置へのサイズおよび位置のハンドルをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="89904-112">Drag the sizing and position handles to size the controls and position them side-by-side.</span></span>  
  
3.  <span data-ttu-id="89904-113">**[データ]** メニューの **[データ ソースの表示]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="89904-113">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="89904-114">場合、**データソース**ウィンドウが空で、データ ソースを追加します。</span><span class="sxs-lookup"><span data-stu-id="89904-114">If the **Data Sources** window is empty, add a data source to it.</span></span> <span data-ttu-id="89904-115">詳細については、次を参照してください。[新しいデータ ソースを追加](https://docs.microsoft.com/visualstudio/data-tools/add-new-data-sources)します。</span><span class="sxs-lookup"><span data-stu-id="89904-115">For more information, see [Add new data sources](https://docs.microsoft.com/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
4.  <span data-ttu-id="89904-116">**データソース**ウィンドウで、マスター テーブルの最上位ノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="89904-116">In the **Data Sources** window, select the top-level node for the master table.</span></span>  
  
5.  <span data-ttu-id="89904-117">クリックして、マスター テーブルのドロップ タイプの詳細に変更**詳細**テーブル ノードのドロップダウン リストにします。</span><span class="sxs-lookup"><span data-stu-id="89904-117">Change the drop type of the master table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="89904-118">最初の項目テンプレートの領域上にマスター テーブル ノードをドラッグして<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="89904-118">Drag the master table node onto the item template region of the first <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
7.  <span data-ttu-id="89904-119">マスター テーブル ノードを展開し、関連するテーブルの詳細のノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="89904-119">Expand the master table node and select the detail node for the related table.</span></span>  
  
8.  <span data-ttu-id="89904-120">クリックして、[詳細] テーブルのドロップ タイプの詳細に変更**詳細**テーブル ノードのドロップダウン リストにします。</span><span class="sxs-lookup"><span data-stu-id="89904-120">Change the drop type of the detail table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
9. <span data-ttu-id="89904-121">このテーブルのノードを選択し、2 番目の項目テンプレートの領域にドラッグ<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="89904-121">Select this table node and drag it onto the item template region of the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89904-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="89904-122">See Also</span></span>  
 <span data-ttu-id="89904-123"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="89904-123"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span></span>   
<span data-ttu-id="89904-124"> [DataRepeater コントロールの概要](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="89904-124"> [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="89904-125"> [方法: DataRepeater コントロールにバインドされたデータの表示](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="89904-125"> [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="89904-126"> [方法: 関連するデータを Windows フォーム アプリケーションの表示します。](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd) </span><span class="sxs-lookup"><span data-stu-id="89904-126"> [How to: Display Related Data in a Windows Forms Application](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd) </span></span>  
<span data-ttu-id="89904-127"> [方法: DataRepeater コントロールの外観を変更します。](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="89904-127"> [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="89904-128"> [DataRepeater コントロールのトラブルシューティング](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="89904-128"> [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)</span></span>
