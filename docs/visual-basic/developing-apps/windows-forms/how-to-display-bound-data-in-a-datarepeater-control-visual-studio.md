---
title: "方法: DataRepeater コントロール (Visual Studio) にバインドされたデータを表示 |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, data-binding
- DataRepeater, displaying bound controls
ms.assetid: 56a15326-1334-4275-af4e-075cad79e6f7
caps.latest.revision: 11
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
ms.openlocfilehash: 677c964ee9ebbad6ec712a29c8b9c8920aa7e7ec
ms.contentlocale: ja-jp
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-display-bound-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="0a935-102">方法 : DataRepeater コントロールにバインドされたデータを表示する (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="0a935-102">How to: Display Bound Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="0a935-103">最も一般的な用途、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールでは、データベースやその他のデータ ソースからバインドされたデータを表示します</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="0a935-103">The most common use of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control is to display bound data from a database or other data source.</span></span>  
  
 <span data-ttu-id="0a935-104">バインドされたコントロールだけでなく静的ラベルなどの各アイテムに対して繰り返されるイメージの他のコントロールに追加することがあります、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="0a935-104">In addition to bound controls, you may want to add other controls, such as a static label or an image that is repeated on each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="0a935-105">詳細については、次を参照してください。[方法: DataRepeater コントロールにバインドされていないコントロールを表示](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)します。</span><span class="sxs-lookup"><span data-stu-id="0a935-105">For more information, see [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).</span></span>  
  
 <span data-ttu-id="0a935-106">バインドすることできますもデータ ソースに実行時に設定して、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>プロパティを`True`とするデータ ソースを割り当て、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A>プロパティ</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>。</span><span class="sxs-lookup"><span data-stu-id="0a935-106">You can also bind to a data source at run time by setting the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> property to `True` and assigning a data source to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> property.</span></span> <span data-ttu-id="0a935-107">この場合は、データ ソースのすべての対話を管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a935-107">In this case, you will need to manage all interaction with the data source.</span></span> <span data-ttu-id="0a935-108">詳細については、次を参照してください。 [DataRepeater コントロールでの仮想モード](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md)します。</span><span class="sxs-lookup"><span data-stu-id="0a935-108">For more information, see [Virtual Mode in the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-data-bound-datarepeater"></a><span data-ttu-id="0a935-109">データ バインド DataRepeater を作成するには</span><span class="sxs-lookup"><span data-stu-id="0a935-109">To create a data-bound DataRepeater</span></span>  
  
1.  <span data-ttu-id="0a935-110">ドラッグ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールから、 **Visual Basic power Packs**  タブで、**ツールボックス**フォームまたはコンテナー コントロールにします</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="0a935-110">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="0a935-111">サイズにサイズと位置のハンドルをドラッグし、コントロールを配置します。</span><span class="sxs-lookup"><span data-stu-id="0a935-111">Drag the sizing and position handles to size and position the control.</span></span>  
  
     <span data-ttu-id="0a935-112">コントロールに&2; つの四角形の領域があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0a935-112">Note that the control has two rectangular regions.</span></span> <span data-ttu-id="0a935-113">上の領域は、*項目テンプレート*; 内の各項目で、テンプレートに追加されたコントロールが繰り返されます、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>実行時にコントロールできます</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="0a935-113">The upper region is the *item template*; controls added to the template will be repeated in each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at run time.</span></span> <span data-ttu-id="0a935-114">下部の領域は、*ビューポート*項目が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a935-114">The lower region is the *viewport*, where the items will be displayed.</span></span>  
  
     <span data-ttu-id="0a935-115">サイズし、変更することで、コントロールまたは項目テンプレートを配置できます、**サイズ**と**位置**のプロパティ ウィンドウでプロパティです。</span><span class="sxs-lookup"><span data-stu-id="0a935-115">You can also size and position the control or the item template by changing the **Size** and **Position** properties in the Properties window.</span></span>  
  
3.  <span data-ttu-id="0a935-116">**[データ]** メニューの **[データ ソースの表示]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a935-116">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0a935-117">場合、**データソース**ウィンドウが空で、データ ソースを追加します。</span><span class="sxs-lookup"><span data-stu-id="0a935-117">If the **Data Sources** window is empty, add a data source to it.</span></span> <span data-ttu-id="0a935-118">詳細については、次を参照してください。[新しいデータ ソースを追加](https://docs.microsoft.com/visualstudio/data-tools/add-new-data-sources)します。</span><span class="sxs-lookup"><span data-stu-id="0a935-118">For more information, see [Add new data sources](https://docs.microsoft.com/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
4.  <span data-ttu-id="0a935-119">**データソース** ウィンドウをバインドするデータを含むテーブルの最上位ノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="0a935-119">In the **Data Sources** window, select the top-level node for the table that contains the data that you want to bind.</span></span>  
  
5.  <span data-ttu-id="0a935-120">テーブルのドロップ タイプを変更する`Details`をクリックして`Details`テーブル ノードのドロップダウン リストにします。</span><span class="sxs-lookup"><span data-stu-id="0a935-120">Change the drop type of the table to `Details` by clicking `Details` in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="0a935-121">テーブル ノードを選択し、項目テンプレートの領域にドラッグ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="0a935-121">Select the table node and drag it onto the item template region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="0a935-122">コントロールの種類は各フィールドに表示を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="0a935-122">You can specify which types of controls are displayed for each field.</span></span> <span data-ttu-id="0a935-123">詳細については、次を参照してください。[データ ソース ウィンドウからドラッグしたときに作成されるコントロールを設定](https://docs.microsoft.com/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window)します。</span><span class="sxs-lookup"><span data-stu-id="0a935-123">For more information, see [Set the control to be created when dragging from the Data Sources window](https://docs.microsoft.com/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a935-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="0a935-124">See Also</span></span>  
 <span data-ttu-id="0a935-125"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="0a935-125"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span></span>   
<span data-ttu-id="0a935-126"> [DataRepeater コントロールの概要](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="0a935-126"> [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="0a935-127"> [方法: DataRepeater コントロールでコントロールが画面にバインドされていません。](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="0a935-127"> [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="0a935-128"> [方法:&2; つの DataRepeater コントロール (Visual Studio) を使用してマスター/詳細フォームを作成](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md) </span><span class="sxs-lookup"><span data-stu-id="0a935-128"> [How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md) </span></span>  
<span data-ttu-id="0a935-129"> [方法: DataRepeater コントロールの外観を変更します。](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="0a935-129"> [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="0a935-130"> [DataRepeater コントロールのトラブルシューティング](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="0a935-130"> [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)</span></span>
