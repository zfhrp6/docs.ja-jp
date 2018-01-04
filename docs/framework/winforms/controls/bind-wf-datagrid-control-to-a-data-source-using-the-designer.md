---
title: "方法 : デザイナーを使ってデータ ソースに Windows フォーム DataGrid コントロールをバインドする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- Windows Forms controls, data binding
- bound controls [Windows Forms]
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e0bde96442e09ee33a63cecd56a4cd6e2cf19a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a><span data-ttu-id="35cc4-102">方法 : デザイナーを使ってデータ ソースに Windows フォーム DataGrid コントロールをバインドする</span><span class="sxs-lookup"><span data-stu-id="35cc4-102">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>
> [!NOTE]
>  <span data-ttu-id="35cc4-103"><xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。</span><span class="sxs-lookup"><span data-stu-id="35cc4-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="35cc4-104">詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35cc4-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="35cc4-105">Windows フォーム<xref:System.Windows.Forms.DataGrid>コントロールは具体的には、データ ソースから情報を表示するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="35cc4-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="35cc4-106">デザイン時に設定して、コントロールをバインドする、<xref:System.Windows.Forms.DataGrid.DataSource%2A>と<xref:System.Windows.Forms.DataGrid.DataMember%2A>プロパティ、または呼び出すことによって実行時に、<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="35cc4-106">You bind the control at design time by setting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties, or at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="35cc4-107">さまざまなデータ ソースからデータを表示できますが、最も一般的なソース、データセットとデータのビューです。</span><span class="sxs-lookup"><span data-stu-id="35cc4-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
 <span data-ttu-id="35cc4-108">デザイン時に、データ ソースが利用可能な場合は — たとえば、フォームには、データセットまたはデータ ビューのインスタンスが含まれている場合: デザイン時に、データ ソースにグリッドをバインドすることができます。</span><span class="sxs-lookup"><span data-stu-id="35cc4-108">If the data source is available at design time—for example, if the form contains an instance of a dataset or a data view—you can bind the grid to the data source at design time.</span></span> <span data-ttu-id="35cc4-109">グリッドで、データのようをプレビューできます。</span><span class="sxs-lookup"><span data-stu-id="35cc4-109">You can then preview what the data will look like in the grid.</span></span>  
  
 <span data-ttu-id="35cc4-110">実行時にプログラムでは、グリッドをバインドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="35cc4-110">You can also bind the grid programmatically, at run time.</span></span> <span data-ttu-id="35cc4-111">これは、実行時に取得した情報に基づいてデータ ソースを設定する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="35cc4-111">This is useful when you want to set a data source based on information you get at run time.</span></span> <span data-ttu-id="35cc4-112">たとえば、アプリケーションは、ユーザーに表示するテーブルの名前を指定を使用できます可能性があります。</span><span class="sxs-lookup"><span data-stu-id="35cc4-112">For example, the application might let the user specify the name of a table to view.</span></span> <span data-ttu-id="35cc4-113">データ ソースがデザイン時に存在しない状況で必要です。</span><span class="sxs-lookup"><span data-stu-id="35cc4-113">It is also necessary in situations where the data source does not exist at design time.</span></span> <span data-ttu-id="35cc4-114">これには、配列、コレクション、型指定されていないデータセット、およびデータ リーダーなどのデータ ソースが含まれます。</span><span class="sxs-lookup"><span data-stu-id="35cc4-114">This includes data sources such as arrays, collections, untyped datasets, and data readers.</span></span>  
  
 <span data-ttu-id="35cc4-115">次の手順が必要です、 **Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.DataGrid>コントロール。</span><span class="sxs-lookup"><span data-stu-id="35cc4-115">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="35cc4-116">このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="35cc4-116">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span> <span data-ttu-id="35cc4-117">[!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)]、<xref:System.Windows.Forms.DataGrid>コントロールに含まれていない、**ツールボックス**既定です。</span><span class="sxs-lookup"><span data-stu-id="35cc4-117">In [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], the <xref:System.Windows.Forms.DataGrid> control is not in the **Toolbox** by default.</span></span> <span data-ttu-id="35cc4-118">追加の詳細については、次を参照してください。[する方法: ツールボックス アイテムの追加](http://msdn.microsoft.com/en-us/458e119e-17fe-450b-b889-e31c128bd7e0)です。</span><span class="sxs-lookup"><span data-stu-id="35cc4-118">For information about adding it, see [How to: Add Items to the Toolbox](http://msdn.microsoft.com/en-us/458e119e-17fe-450b-b889-e31c128bd7e0).</span></span> <span data-ttu-id="35cc4-119">また、 [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)]、使用することができます、**データ ソース**デザイン時のデータ バインディングのウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="35cc4-119">Additionally in [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], you can use the **Data Sources** window for design-time data binding.</span></span> <span data-ttu-id="35cc4-120">詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインド](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)です。</span><span class="sxs-lookup"><span data-stu-id="35cc4-120">For more information see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35cc4-121">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="35cc4-121">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="35cc4-122">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="35cc4-122">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="35cc4-123">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35cc4-123">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a><span data-ttu-id="35cc4-124">デザイナーで 1 つのテーブルにデータ グリッド コントロールにデータ バインドする</span><span class="sxs-lookup"><span data-stu-id="35cc4-124">To data-bind the DataGrid control to a single table in the designer</span></span>  
  
1.  <span data-ttu-id="35cc4-125">コントロールの設定<xref:System.Windows.Forms.DataGrid.DataSource%2A>プロパティにバインドするデータ項目を含むオブジェクトをします。</span><span class="sxs-lookup"><span data-stu-id="35cc4-125">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>  
  
2.  <span data-ttu-id="35cc4-126">データ ソースがデータセットの場合は、設定、<xref:System.Windows.Forms.DataGrid.DataMember%2A>プロパティにバインドするテーブルの名前にします。</span><span class="sxs-lookup"><span data-stu-id="35cc4-126">If the data source is a dataset, set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the table to bind to.</span></span>  
  
3.  <span data-ttu-id="35cc4-127">データ ソースが、データセットまたはデータセットのテーブルに基づいたデータ ビューの場合は、データセットへのデータ、フォームにコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="35cc4-127">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="35cc4-128">実際に使用するコードは、データセットがデータを取得する場所によって異なります。</span><span class="sxs-lookup"><span data-stu-id="35cc4-128">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="35cc4-129">データセットは、データベースから直接登録されているが、通常を呼び出した場合、`Fill`という名前のデータセットに読み込まれる次のコード例のように、データ アダプターの`DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="35cc4-129">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following code example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
4.  <span data-ttu-id="35cc4-130">(省略可能)グリッドに適切なテーブルのスタイルおよび列のスタイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="35cc4-130">(Optional) Add the appropriate table styles and column styles to the grid.</span></span>  
  
     <span data-ttu-id="35cc4-131">テーブルのスタイルがない場合、テーブルが表示されますが、最低限の書式とすべての列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="35cc4-131">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a><span data-ttu-id="35cc4-132">デザイナーでデータセットの複数のテーブルにデータ グリッド コントロールにデータ バインドする</span><span class="sxs-lookup"><span data-stu-id="35cc4-132">To data-bind the DataGrid control to multiple tables in a dataset in the designer</span></span>  
  
1.  <span data-ttu-id="35cc4-133">コントロールの設定<xref:System.Windows.Forms.DataGrid.DataSource%2A>プロパティにバインドするデータ項目を含むオブジェクトをします。</span><span class="sxs-lookup"><span data-stu-id="35cc4-133">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>  
  
2.  <span data-ttu-id="35cc4-134">(つまり、relation オブジェクトが含まれている) 場合、データセットに関連するテーブルが含まれる場合、設定、<xref:System.Windows.Forms.DataGrid.DataMember%2A>プロパティを親テーブルの名前にします。</span><span class="sxs-lookup"><span data-stu-id="35cc4-134">If the dataset contains related tables (that is, if it contains a relation object), set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the parent table.</span></span>  
  
3.  <span data-ttu-id="35cc4-135">データセットを読み込むコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="35cc4-135">Write code to fill the dataset.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35cc4-136">参照</span><span class="sxs-lookup"><span data-stu-id="35cc4-136">See Also</span></span>  
 [<span data-ttu-id="35cc4-137">DataGrid コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="35cc4-137">DataGrid Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [<span data-ttu-id="35cc4-138">方法: Windows フォーム DataGrid コントロールにテーブルと列を追加する</span><span class="sxs-lookup"><span data-stu-id="35cc4-138">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [<span data-ttu-id="35cc4-139">DataGrid コントロール</span><span class="sxs-lookup"><span data-stu-id="35cc4-139">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [<span data-ttu-id="35cc4-140">Windows フォームでのデータ バインディング</span><span class="sxs-lookup"><span data-stu-id="35cc4-140">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="35cc4-141">Visual Studio でのデータへのアクセス</span><span class="sxs-lookup"><span data-stu-id="35cc4-141">Accessing data in Visual Studio</span></span>](/visualstudio/data-tools/accessing-data-in-visual-studio)
