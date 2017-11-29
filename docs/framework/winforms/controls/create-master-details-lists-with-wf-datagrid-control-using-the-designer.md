---
title: "方法 : デザイナーで Windows フォーム DataGrid コントロールを使用してマスター/詳細リストを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 66de6fb17e3ee5b916c4bb20dfa0799758375406
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a><span data-ttu-id="8fc7a-102">方法 : デザイナーで Windows フォーム DataGrid コントロールを使用してマスター/詳細リストを作成する</span><span class="sxs-lookup"><span data-stu-id="8fc7a-102">How to: Create Master-Details Lists with the Windows Forms DataGrid Control Using the Designer</span></span>
> [!NOTE]
>  <span data-ttu-id="8fc7a-103"><xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="8fc7a-104">詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="8fc7a-105">場合、<xref:System.Data.DataSet>は一連の関連テーブルの 2 つ使用できます<xref:System.Windows.Forms.DataGrid>マスター/詳細形式でデータを表示するコントロール。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-105">If your <xref:System.Data.DataSet> contains a series of related tables, you can use two <xref:System.Windows.Forms.DataGrid> controls to display the data in a master-detail format.</span></span> <span data-ttu-id="8fc7a-106">1 つ<xref:System.Windows.Forms.DataGrid>マスター グリッドに指定し、詳細グリッドに、もう一方を指定します。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-106">One <xref:System.Windows.Forms.DataGrid> is designated to be the master grid, and the second is designated to be the details grid.</span></span> <span data-ttu-id="8fc7a-107">マスターの一覧にエントリを選択すると、詳細の一覧ですべての関連する子エントリのとおりです。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-107">When you select an entry in the master list, all of the related child entries are shown in the details list.</span></span> <span data-ttu-id="8fc7a-108">たとえば場合、 <xref:System.Data.DataSet> Customers テーブルと関連の Orders テーブルを含むマスター グリッドに Customers テーブルと Orders テーブルに、詳細グリッドを指定するとします。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-108">For example, if your <xref:System.Data.DataSet> contains a Customers table and a related Orders table, you would specify the Customers table to be the master grid and the Orders table to be the details grid.</span></span> <span data-ttu-id="8fc7a-109">マスター グリッドから、顧客がオンの場合、すべての注文を Orders テーブル内でその顧客に関連付けられているの詳細グリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-109">When a customer is selected from the master grid, all of the orders associated with that customer in the Orders table would be displayed in the details grid.</span></span>  
  
 <span data-ttu-id="8fc7a-110">次の手順が必要です、 **Windows アプリケーション**プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-110">The following procedure requires a **Windows Application** project.</span></span> <span data-ttu-id="8fc7a-111">このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)です。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-111">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8fc7a-112">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8fc7a-113">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8fc7a-114">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-114">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-a-master-details-list-in-the-designer"></a><span data-ttu-id="8fc7a-115">デザイナーでマスター/詳細リストを作成するには</span><span class="sxs-lookup"><span data-stu-id="8fc7a-115">To create a master-details list in the designer</span></span>  
  
1.  <span data-ttu-id="8fc7a-116">2 つ追加<xref:System.Windows.Forms.DataGrid>フォームのコントロールです。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-116">Add two <xref:System.Windows.Forms.DataGrid> controls to the form.</span></span> <span data-ttu-id="8fc7a-117">詳細については、次を参照してください。[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-117">For more information, see [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span> <span data-ttu-id="8fc7a-118">[!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)]、<xref:System.Windows.Forms.DataGrid>コントロールに含まれていない、**ツールボックス**既定です。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-118">In [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], the <xref:System.Windows.Forms.DataGrid> control is not in the **Toolbox** by default.</span></span> <span data-ttu-id="8fc7a-119">詳細については、次を参照してください。[する方法: ツールボックス アイテムの追加](http://msdn.microsoft.com/en-us/458e119e-17fe-450b-b889-e31c128bd7e0)です。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-119">For more information, see [How to: Add Items to the Toolbox](http://msdn.microsoft.com/en-us/458e119e-17fe-450b-b889-e31c128bd7e0).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8fc7a-120">次の手順には適用されない[!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)]が使用される、**データ ソース**デザイン時のデータ バインディングのウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-120">The following steps are not applicable to [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], which uses the **Data Sources** window for design-time data binding.</span></span> <span data-ttu-id="8fc7a-121">詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインド](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)と[する方法: Windows フォーム アプリケーションで関連するデータを表示](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd)です。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-121">For more information, see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio) and [How to: Display Related Data in a Windows Forms Application](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd).</span></span>  
  
2.  <span data-ttu-id="8fc7a-122">次の 2 つ以上のテーブルをドラッグして**サーバー エクスプ ローラー**をフォームにします。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-122">Drag two or more tables from **Server Explorer** to the form.</span></span>  
  
3.  <span data-ttu-id="8fc7a-123">**データ**メニューの **データセットの生成**です。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-123">From the **Data** menu, select **Generate DataSet**.</span></span>  
  
4.  <span data-ttu-id="8fc7a-124">XML デザイナーを使用してテーブル間のリレーションシップを設定します。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-124">Set the relationships between the tables using the XML Designer.</span></span> <span data-ttu-id="8fc7a-125">詳細については、次を参照してください。"する方法: 一対多を作成する XML スキーマおよびデータセットでリレーションシップ"msdn です。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-125">For details, see "How to: Create One-to-Many Relationships in XML Schemas and Datasets" on MSDN.</span></span>  
  
5.  <span data-ttu-id="8fc7a-126">選択して、リレーションシップを保存**すべて保存**から、**ファイル**メニュー。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-126">Save the relationships by selecting **Save All** from the **File** menu.</span></span>  
  
6.  <span data-ttu-id="8fc7a-127">構成、<xref:System.Windows.Forms.DataGrid>マスター グリッドを次のように指定するコントロール。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-127">Configure the <xref:System.Windows.Forms.DataGrid> control that you want to designate the master grid, as follows:</span></span>  
  
    1.  <span data-ttu-id="8fc7a-128">選択、<xref:System.Data.DataSet>のドロップ ダウン リストから、<xref:System.Windows.Forms.DataGrid.DataSource%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-128">Select the <xref:System.Data.DataSet> from the drop-down list in the <xref:System.Windows.Forms.DataGrid.DataSource%2A> property.</span></span>  
  
    2.  <span data-ttu-id="8fc7a-129">ドロップダウン リストからマスター テーブル (たとえば、"Customers") を選択、<xref:System.Windows.Forms.DataGrid.DataMember%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-129">Select the master table (for example, "Customers") from the drop-down list in the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property.</span></span>  
  
7.  <span data-ttu-id="8fc7a-130">構成、<xref:System.Windows.Forms.DataGrid>詳細グリッドを次のように指定するコントロール。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-130">Configure the <xref:System.Windows.Forms.DataGrid> control that you want to designate the details grid, as follows:</span></span>  
  
    1.  <span data-ttu-id="8fc7a-131">選択、<xref:System.Data.DataSet>のドロップ ダウン リストから、<xref:System.Windows.Forms.DataGrid.DataSource%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-131">Select the <xref:System.Data.DataSet> from the drop-down list in the <xref:System.Windows.Forms.DataGrid.DataSource%2A> property.</span></span>  
  
    2.  <span data-ttu-id="8fc7a-132">ドロップダウン リストから、マスター/詳細テーブル間の関係 (たとえば、"Customers.CustOrd") を選択、<xref:System.Windows.Forms.DataGrid.DataMember%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-132">Select the relationship (for example, "Customers.CustOrd") between the master and detail tables from the drop-down list in the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property.</span></span> <span data-ttu-id="8fc7a-133">リレーションシップを表示するために、プラス記号をクリックすると、ノードを展開します (**+**) ドロップダウン リストのマスター テーブルの横にある記号。</span><span class="sxs-lookup"><span data-stu-id="8fc7a-133">In order to see the relationship, expand the node by clicking on the plus (**+**) sign next to the master table in the drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fc7a-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="8fc7a-134">See Also</span></span>  
 [<span data-ttu-id="8fc7a-135">DataGrid コントロール</span><span class="sxs-lookup"><span data-stu-id="8fc7a-135">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [<span data-ttu-id="8fc7a-136">DataGrid コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="8fc7a-136">DataGrid Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [<span data-ttu-id="8fc7a-137">方法: データ ソースに Windows フォーム DataGrid コントロールをバインドする</span><span class="sxs-lookup"><span data-stu-id="8fc7a-137">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 [<span data-ttu-id="8fc7a-138">Visual Studio でのデータへのコントロールのバインド</span><span class="sxs-lookup"><span data-stu-id="8fc7a-138">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
