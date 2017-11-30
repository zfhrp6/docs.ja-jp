---
title: "方法 : Windows フォーム DataGrid コントロールの列を削除するまたは非表示にする"
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
helpviewer_keywords:
- data grids [Windows Forms], deleting columns
- DataGrid control [Windows Forms], deleting columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
- columns [Windows Forms], deleting in data grids
- DataGrid control [Windows Forms], hiding columns
ms.assetid: bcd0dd96-6687-4c48-b0e1-d5287b93ac91
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1d89f14d034c1050d364282c04424b1326bcff9e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="0b581-102">方法 : Windows フォーム DataGrid コントロールの列を削除するまたは非表示にする</span><span class="sxs-lookup"><span data-stu-id="0b581-102">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="0b581-103"><xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。</span><span class="sxs-lookup"><span data-stu-id="0b581-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="0b581-104">詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0b581-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="0b581-105">プログラムで削除するか、Windows フォーム内の列を非表示に<xref:System.Windows.Forms.DataGrid>のプロパティとメソッドを使用して、コントロール、<xref:System.Windows.Forms.GridColumnStylesCollection>と<xref:System.Windows.Forms.DataGridColumnStyle>オブジェクト (のメンバーである、<xref:System.Windows.Forms.DataGridTableStyle>クラス)。</span><span class="sxs-lookup"><span data-stu-id="0b581-105">You can programmatically delete or hide columns in the Windows Forms <xref:System.Windows.Forms.DataGrid> control by using the properties and methods of the <xref:System.Windows.Forms.GridColumnStylesCollection> and <xref:System.Windows.Forms.DataGridColumnStyle> objects (which are members of the <xref:System.Windows.Forms.DataGridTableStyle> class).</span></span>  
  
 <span data-ttu-id="0b581-106">削除または非表示の列は、データ ソース、グリッドがバインドされ、プログラムでアクセスできますにまだ存在します。</span><span class="sxs-lookup"><span data-stu-id="0b581-106">The deleted or hidden columns still exist in the data source the grid is bound to, and can still be accessed programmatically.</span></span> <span data-ttu-id="0b581-107">データ グリッドに表示されますなくなるだけです。</span><span class="sxs-lookup"><span data-stu-id="0b581-107">They are just no longer visible in the datagrid.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b581-108">アプリケーションが特定の列のデータにアクセスできません、データ グリッドに表示しない場合は、し、必要がある可能性がありますこれらに含めるデータ ソースの最初の場所。</span><span class="sxs-lookup"><span data-stu-id="0b581-108">If your application does not access certain columns of data, and you do not want them displayed in the datagrid, then it is probably not necessary to include them in the data source in the first place.</span></span>  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a><span data-ttu-id="0b581-109">データ グリッドから列をプログラムで削除するには</span><span class="sxs-lookup"><span data-stu-id="0b581-109">To delete a column from the DataGrid programmatically</span></span>  
  
1.  <span data-ttu-id="0b581-110">フォームの宣言領域内の新しいインスタンスを宣言、<xref:System.Windows.Forms.DataGridTableStyle>クラスです。</span><span class="sxs-lookup"><span data-stu-id="0b581-110">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2.  <span data-ttu-id="0b581-111">設定、<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType>スタイルを適用するデータ ソース内のテーブルにプロパティです。</span><span class="sxs-lookup"><span data-stu-id="0b581-111">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> property to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="0b581-112">次の例では、<xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType>プロパティで、既に設定されていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="0b581-112">The following example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3.  <span data-ttu-id="0b581-113">新しい追加<xref:System.Windows.Forms.DataGridTableStyle>を datagrid のテーブル スタイルのコレクション オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0b581-113">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4.  <span data-ttu-id="0b581-114">呼び出す、<xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A>のメソッド、<xref:System.Windows.Forms.DataGrid>の<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>コレクションを削除する列の列インデックスを指定します。</span><span class="sxs-lookup"><span data-stu-id="0b581-114">Call the <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.DataGrid>'s <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> collection, specifying the column index of the column to delete.</span></span>  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub DeleteColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Delete the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles.RemoveAt(0)  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void deleteColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Delete the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles.RemoveAt(0);  
    }  
    ```  
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a><span data-ttu-id="0b581-115">DataGrid の列をプログラムで非表示にするには</span><span class="sxs-lookup"><span data-stu-id="0b581-115">To hide a column in the DataGrid programmatically</span></span>  
  
1.  <span data-ttu-id="0b581-116">フォームの宣言領域内の新しいインスタンスを宣言、<xref:System.Windows.Forms.DataGridTableStyle>クラスです。</span><span class="sxs-lookup"><span data-stu-id="0b581-116">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2.  <span data-ttu-id="0b581-117">設定、<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>のプロパティ、<xref:System.Windows.Forms.DataGridTableStyle>スタイルを適用するデータ ソース内のテーブルにします。</span><span class="sxs-lookup"><span data-stu-id="0b581-117">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property of the <xref:System.Windows.Forms.DataGridTableStyle> to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="0b581-118">次のコード例では、<xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType>プロパティで、既に設定されていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="0b581-118">The following code example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3.  <span data-ttu-id="0b581-119">新しい追加<xref:System.Windows.Forms.DataGridTableStyle>を datagrid のテーブル スタイルのコレクション オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0b581-119">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4.  <span data-ttu-id="0b581-120">設定して、列を非表示にその`Width`プロパティを非表示にするのには、列の列インデックスを指定する 0 にします。</span><span class="sxs-lookup"><span data-stu-id="0b581-120">Hide the column by setting its `Width` property to 0, specifying the column index of the column to hide.</span></span>  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub HideColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Hide the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles(0).Width = 0  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void hideColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Hide the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles[0].Width = 0;  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0b581-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b581-121">See Also</span></span>  
 [<span data-ttu-id="0b581-122">方法: Windows フォーム DataGrid コントロールに表示されるデータを実行時に変更する</span><span class="sxs-lookup"><span data-stu-id="0b581-122">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/change-displayed-data-at-run-time-wf-datagrid-control.md)  
 [<span data-ttu-id="0b581-123">方法: Windows フォーム DataGrid コントロールにテーブルと列を追加する</span><span class="sxs-lookup"><span data-stu-id="0b581-123">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
