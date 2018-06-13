---
title: Windows フォーム DataGridView コントロールの既定の機能
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
ms.openlocfilehash: a475d8bce388860c88571fbf638d206bfe01223d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526628"
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="ff648-102">Windows フォーム DataGridView コントロールの既定の機能</span><span class="sxs-lookup"><span data-stu-id="ff648-102">Default Functionality in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="ff648-103">Windows フォーム<xref:System.Windows.Forms.DataGridView>コントロールは多くの既定の機能をユーザーに提供します。</span><span class="sxs-lookup"><span data-stu-id="ff648-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control provides users with a significant amount of default functionality.</span></span>  
  
## <a name="default-functionality"></a><span data-ttu-id="ff648-104">既定の機能</span><span class="sxs-lookup"><span data-stu-id="ff648-104">Default Functionality</span></span>  
 <span data-ttu-id="ff648-105"><xref:System.Windows.Forms.DataGridView>コントロールは、既定で次のような機能を持ちます:</span><span class="sxs-lookup"><span data-stu-id="ff648-105">By default, a <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
-   <span data-ttu-id="ff648-106">テーブルを垂直方向にスクロールしても列ヘッダーおよび行ヘッダーが見える状態のまま自動的に表示します。</span><span class="sxs-lookup"><span data-stu-id="ff648-106">Automatically displays column headers and row headers that remain visible as the table scrolls vertically.</span></span>  
  
-   <span data-ttu-id="ff648-107">現在の行を示す選択を含む行ヘッダーがあります。</span><span class="sxs-lookup"><span data-stu-id="ff648-107">Has a row header that contains a selection indicator for the current row.</span></span>  
  
-   <span data-ttu-id="ff648-108">最初のセルに選択を示す四角形があります。</span><span class="sxs-lookup"><span data-stu-id="ff648-108">Has a selection rectangle in the first cell.</span></span>  
  
-   <span data-ttu-id="ff648-109">自動的にサイズを変更できるユーザーが列の区分線をダブルクリックすると、列があります。</span><span class="sxs-lookup"><span data-stu-id="ff648-109">Has columns that can be automatically resized when the user double-clicks the column dividers.</span></span>  
  
-   <span data-ttu-id="ff648-110">Windows XP および Windows Server 2003 ファミリで visual スタイルを自動的にサポートされるときに、<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>メソッドは、アプリケーションから`Main`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="ff648-110">Automatically supports visual styles on Windows XP and the Windows Server 2003 family when the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method is called from the application's `Main` method.</span></span>  
  
 <span data-ttu-id="ff648-111">さらに、<xref:System.Windows.Forms.DataGridView>コントロールの内容は既定で編集できます:</span><span class="sxs-lookup"><span data-stu-id="ff648-111">Additionally, the contents of a <xref:System.Windows.Forms.DataGridView> control can be edited by default:</span></span>  
  
-   <span data-ttu-id="ff648-112">ユーザーがダブルクリックするか、セル中で F2 キーを押した場合、コントロールは自動的にセルを編集モードにし、ユーザーが入力したセルの内容を更新します。</span><span class="sxs-lookup"><span data-stu-id="ff648-112">If the user double-clicks or presses F2 in a cell, the control automatically puts the cell into edit mode and updates the contents of the cell as the user types.</span></span>  
  
-   <span data-ttu-id="ff648-113">ユーザーは、グリッドの最後にスクロールする場合、新しいレコードを追加するための行が存在するユーザーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ff648-113">If the user scrolls to the end of the grid, the user will see that a row for adding new records is present.</span></span> <span data-ttu-id="ff648-114">新しい行を追加、ユーザーは、この行をクリックすると、<xref:System.Windows.Forms.DataGridView>コントロールは、既定値を使用します。</span><span class="sxs-lookup"><span data-stu-id="ff648-114">When the user clicks this row, a new row is added to the <xref:System.Windows.Forms.DataGridView> control, with default values.</span></span> <span data-ttu-id="ff648-115">ユーザーは、esc キーを押すと、この新しい行は表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="ff648-115">When the user presses ESC, this new row disappears.</span></span>  
  
-   <span data-ttu-id="ff648-116">ユーザーには、行ヘッダーがクリックすると、行全体が選択されます。</span><span class="sxs-lookup"><span data-stu-id="ff648-116">If the user clicks a row header, the whole row is selected.</span></span>  
  
 <span data-ttu-id="ff648-117"><xref:System.Windows.Forms.DataGridView> プロパティの設定から<xref:System.Windows.Forms.DataGridView.DataSource%2A> コントロールをデータ ソースにバインドしたとき、コントロールは次のように振る舞います:</span><span class="sxs-lookup"><span data-stu-id="ff648-117">When you bind a <xref:System.Windows.Forms.DataGridView> control to a data source by setting its <xref:System.Windows.Forms.DataGridView.DataSource%2A> property, the control:</span></span>  
  
-   <span data-ttu-id="ff648-118">列ヘッダーのテキストとしてデータ ソースの列の名前が自動的に使用します。</span><span class="sxs-lookup"><span data-stu-id="ff648-118">Automatically uses the names of the data source's columns as the column header text.</span></span>  
  
-   <span data-ttu-id="ff648-119">データ ソースの内容が格納されます。</span><span class="sxs-lookup"><span data-stu-id="ff648-119">Is populated with the contents of the data source.</span></span> <span data-ttu-id="ff648-120"><xref:System.Windows.Forms.DataGridView> 列は、データ ソース内の各列に対して自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="ff648-120"><xref:System.Windows.Forms.DataGridView> columns are automatically created for each column in the data source.</span></span>  
  
-   <span data-ttu-id="ff648-121">テーブルに 1 行ごとに表示される行のデータを作成します。</span><span class="sxs-lookup"><span data-stu-id="ff648-121">Creates a row for each visible row in the table.</span></span>  
  
-   <span data-ttu-id="ff648-122">自動的にユーザーが列見出しをクリックしたときに、基になるデータに基づく行を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="ff648-122">Automatically sorts the rows based on the underlying data when the user clicks a column header.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff648-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff648-123">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="ff648-124">DataGridView コントロール</span><span class="sxs-lookup"><span data-stu-id="ff648-124">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
