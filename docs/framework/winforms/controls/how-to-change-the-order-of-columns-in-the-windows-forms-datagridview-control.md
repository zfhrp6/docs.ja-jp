---
title: "方法 : Windows フォーム DataGridView コントロールの列の順序を変更する"
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
- columns [Windows Forms], changing order
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], changing column order
ms.assetid: 5e9ac3bc-b0f0-48cb-a3d5-b005af905395
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2107da50f3b8a569bc329dbb1ae1722141921e11
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="aa6bf-102">方法 : Windows フォーム DataGridView コントロールの列の順序を変更する</span><span class="sxs-lookup"><span data-stu-id="aa6bf-102">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="aa6bf-103"><xref:System.Windows.Forms.DataGridView> を使用してデータをデータ ソースから表示する場合、データ ソースのスキーマの列が、表示したい順序で表示されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="aa6bf-103">When you use a <xref:System.Windows.Forms.DataGridView> to display data from a data source, the columns in the data source's schema sometimes do not appear in the order you would like to display them.</span></span> <span data-ttu-id="aa6bf-104"><xref:System.Windows.Forms.DataGridViewColumn> クラスの <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> プロパティを使用して、列の表示順序を変更できます。</span><span class="sxs-lookup"><span data-stu-id="aa6bf-104">You can change the displayed order of the columns by using the <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> property of the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <span data-ttu-id="aa6bf-105">次のコード例は、Northwind サンプル データベース内の Customers テーブルにバインドするときに自動的に生成される列のいくつかを再配置します。</span><span class="sxs-lookup"><span data-stu-id="aa6bf-105">The following code example repositions some of the columns automatically generated when binding to the Customers table in the Northwind sample database.</span></span> <span data-ttu-id="aa6bf-106">バインドする方法について、<xref:System.Windows.Forms.DataGridView>コントロール、データベース テーブルを参照してください[する方法: Windows フォーム DataGridView コントロールにデータをバインド](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="aa6bf-106">For more information about how to bind the <xref:System.Windows.Forms.DataGridView> control to a database table, see [How to: Bind Data to the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="aa6bf-107">Visual Studio では、このタスクに対するサポートが用意されています。</span><span class="sxs-lookup"><span data-stu-id="aa6bf-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="aa6bf-108">参照してください[する方法: Windows フォーム DataGridView コントロールを使用して、デザイナーで列の順序を変更します。](http://msdn.microsoft.com/library/hb1dk7ax\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="aa6bf-108">Also see [How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/hb1dk7ax\(v=vs.110\))</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa6bf-109">例</span><span class="sxs-lookup"><span data-stu-id="aa6bf-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#040)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#040)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="aa6bf-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="aa6bf-110">Compiling the Code</span></span>  
 <span data-ttu-id="aa6bf-111">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="aa6bf-111">This example requires:</span></span>  
  
-   <span data-ttu-id="aa6bf-112">Northwind サンプル データベース内の <xref:System.Windows.Forms.DataGridView> テーブルなど、示されている列の名前を持つテーブルにバインドされた、`customersDataGridView` という名前の `Customers` コントロール。</span><span class="sxs-lookup"><span data-stu-id="aa6bf-112">A <xref:System.Windows.Forms.DataGridView> control named `customersDataGridView` that is bound to a table with the indicated column names, such as the `Customers` table in the Northwind sample database.</span></span>  
  
-   <span data-ttu-id="aa6bf-113"><xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType>、<xref:System.Data?displayProperty=nameWithType>、および <xref:System.Xml?displayProperty=nameWithType> の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="aa6bf-113">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, and <xref:System.Xml?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa6bf-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="aa6bf-114">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="aa6bf-115">Windows フォーム DataGridView コントロールでのデータの表示</span><span class="sxs-lookup"><span data-stu-id="aa6bf-115">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="aa6bf-116">方法: データを Windows フォーム DataGridView コントロールにバインドする</span><span class="sxs-lookup"><span data-stu-id="aa6bf-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)
