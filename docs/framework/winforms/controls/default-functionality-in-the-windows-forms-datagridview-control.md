---
title: "Windows フォーム DataGridView コントロールの既定の機能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ecb8cdaa4e8eb0498259c597e0de3f80c3106549
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="8f7f3-102">Windows フォーム DataGridView コントロールの既定の機能</span><span class="sxs-lookup"><span data-stu-id="8f7f3-102">Default Functionality in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="8f7f3-103">Windows フォーム<xref:System.Windows.Forms.DataGridView>コントロール膨大な量の既定の機能をユーザーに提供します。</span><span class="sxs-lookup"><span data-stu-id="8f7f3-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control provides users with a significant amount of default functionality.</span></span>  
  
## <a name="default-functionality"></a><span data-ttu-id="8f7f3-104">既定の機能</span><span class="sxs-lookup"><span data-stu-id="8f7f3-104">Default Functionality</span></span>  
 <span data-ttu-id="8f7f3-105">既定では、<xref:System.Windows.Forms.DataGridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="8f7f3-105">By default, a <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
-   <span data-ttu-id="8f7f3-106">列ヘッダーおよびテーブルを垂直方向にスクロールしても表示したまま行ヘッダーを自動的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="8f7f3-106">Automatically displays column headers and row headers that remain visible as the table scrolls vertically.</span></span>  
  
-   <span data-ttu-id="8f7f3-107">現在の行の選択インジケーターを含む行ヘッダーがあります。</span><span class="sxs-lookup"><span data-stu-id="8f7f3-107">Has a row header that contains a selection indicator for the current row.</span></span>  
  
-   <span data-ttu-id="8f7f3-108">最初のセルに四角形を描くを持っています。</span><span class="sxs-lookup"><span data-stu-id="8f7f3-108">Has a selection rectangle in the first cell.</span></span>  
  
-   <span data-ttu-id="8f7f3-109">自動的にサイズを変更できるユーザーが列の区分線をダブルクリックすると、列があります。</span><span class="sxs-lookup"><span data-stu-id="8f7f3-109">Has columns that can be automatically resized when the user double-clicks the column dividers.</span></span>  
  
-   <span data-ttu-id="8f7f3-110">Windows XP および Windows Server 2003 ファミリで visual スタイルを自動的にサポートされるときに、<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>メソッドは、アプリケーションから`Main`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="8f7f3-110">Automatically supports visual styles on Windows XP and the Windows Server 2003 family when the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method is called from the application's `Main` method.</span></span>  
  
 <span data-ttu-id="8f7f3-111">さらの内容、<xref:System.Windows.Forms.DataGridView>コントロールは既定では編集できます。</span><span class="sxs-lookup"><span data-stu-id="8f7f3-111">Additionally, the contents of a <xref:System.Windows.Forms.DataGridView> control can be edited by default:</span></span>  
  
-   <span data-ttu-id="8f7f3-112">場合は、ユーザーは、ダブルクリックするか、セルの f2 キーを押す、コントロールは自動的にセルが編集モードにし、ユーザーの種類として、セルの内容を更新します。</span><span class="sxs-lookup"><span data-stu-id="8f7f3-112">If the user double-clicks or presses F2 in a cell, the control automatically puts the cell into edit mode and updates the contents of the cell as the user types.</span></span>  
  
-   <span data-ttu-id="8f7f3-113">ユーザーは、グリッドの最後にスクロールする場合、新しいレコードを追加するための行が存在するユーザーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8f7f3-113">If the user scrolls to the end of the grid, the user will see that a row for adding new records is present.</span></span> <span data-ttu-id="8f7f3-114">新しい行を追加、ユーザーは、この行をクリックすると、<xref:System.Windows.Forms.DataGridView>コントロールは、既定値を使用します。</span><span class="sxs-lookup"><span data-stu-id="8f7f3-114">When the user clicks this row, a new row is added to the <xref:System.Windows.Forms.DataGridView> control, with default values.</span></span> <span data-ttu-id="8f7f3-115">ユーザーは、esc キーを押すと、この新しい行は表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="8f7f3-115">When the user presses ESC, this new row disappears.</span></span>  
  
-   <span data-ttu-id="8f7f3-116">ユーザーには、行ヘッダーがクリックすると、行全体が選択されます。</span><span class="sxs-lookup"><span data-stu-id="8f7f3-116">If the user clicks a row header, the whole row is selected.</span></span>  
  
 <span data-ttu-id="8f7f3-117">バインドすると、<xref:System.Windows.Forms.DataGridView>コントロールを設定して、データ ソースをその<xref:System.Windows.Forms.DataGridView.DataSource%2A>プロパティ、コントロール。</span><span class="sxs-lookup"><span data-stu-id="8f7f3-117">When you bind a <xref:System.Windows.Forms.DataGridView> control to a data source by setting its <xref:System.Windows.Forms.DataGridView.DataSource%2A> property, the control:</span></span>  
  
-   <span data-ttu-id="8f7f3-118">列ヘッダーのテキストとしてデータ ソースの列の名前が自動的に使用します。</span><span class="sxs-lookup"><span data-stu-id="8f7f3-118">Automatically uses the names of the data source's columns as the column header text.</span></span>  
  
-   <span data-ttu-id="8f7f3-119">データ ソースの内容が格納されます。</span><span class="sxs-lookup"><span data-stu-id="8f7f3-119">Is populated with the contents of the data source.</span></span> <span data-ttu-id="8f7f3-120"><xref:System.Windows.Forms.DataGridView>列は、データ ソース内の各列に対して自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="8f7f3-120"><xref:System.Windows.Forms.DataGridView> columns are automatically created for each column in the data source.</span></span>  
  
-   <span data-ttu-id="8f7f3-121">テーブルに 1 行ごとに表示される行のデータを作成します。</span><span class="sxs-lookup"><span data-stu-id="8f7f3-121">Creates a row for each visible row in the table.</span></span>  
  
-   <span data-ttu-id="8f7f3-122">自動的にユーザーが列見出しをクリックしたときに、基になるデータに基づく行を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="8f7f3-122">Automatically sorts the rows based on the underlying data when the user clicks a column header.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f7f3-123">参照</span><span class="sxs-lookup"><span data-stu-id="8f7f3-123">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="8f7f3-124">DataGridView コントロール</span><span class="sxs-lookup"><span data-stu-id="8f7f3-124">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
