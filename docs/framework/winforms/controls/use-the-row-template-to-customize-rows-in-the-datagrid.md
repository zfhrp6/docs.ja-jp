---
title: '方法 : 行テンプレートを使用して Windows フォーム DataGridView コントロールの行をカスタマイズする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: 2bde9b3f6934833804866e29c18f3636c65ba069
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539179"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="8671a-102">方法 : 行テンプレートを使用して Windows フォーム DataGridView コントロールの行をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="8671a-102">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="8671a-103"><xref:System.Windows.Forms.DataGridView>コントロールは基礎として行テンプレートを使用してすべての行のデータ バインディングを使用または呼び出すときに、コントロールに追加される、<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType>メソッドを使用する既存の行の指定なし。</span><span class="sxs-lookup"><span data-stu-id="8671a-103">The <xref:System.Windows.Forms.DataGridView> control uses the row template as a basis for all rows that it adds to the control either through data binding or when you call the <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> method without specifying an existing row to use.</span></span>  
  
 <span data-ttu-id="8671a-104">行テンプレートを使用して外観と動作よりも行のより詳細な制御、<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>プロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="8671a-104">The row template gives you greater control over the appearance and behavior of rows than the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> property provides.</span></span> <span data-ttu-id="8671a-105">行テンプレートを使用して、いずれかを設定できます<xref:System.Windows.Forms.DataGridViewRow>を含むプロパティ<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>です。</span><span class="sxs-lookup"><span data-stu-id="8671a-105">With the row template, you can set any <xref:System.Windows.Forms.DataGridViewRow> properties, including <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.</span></span>  
  
 <span data-ttu-id="8671a-106">状況によっては、特定の効果を実現するために行テンプレートを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8671a-106">There are some situations where you must use the row template to achieve a particular effect.</span></span> <span data-ttu-id="8671a-107">行の高さ情報を格納できないなど、<xref:System.Windows.Forms.DataGridViewCellStyle>ので、すべての行で使用される既定の高さを変更する行のテンプレートを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8671a-107">For example, row height information cannot be stored in a <xref:System.Windows.Forms.DataGridViewCellStyle>, so you must use a row template to change the default height used by all rows.</span></span> <span data-ttu-id="8671a-108">行テンプレートから派生した独自のクラスを作成する際にも役立ちます<xref:System.Windows.Forms.DataGridViewRow>コントロールに新しい行を追加するときに使用してカスタムの型を必要とします。</span><span class="sxs-lookup"><span data-stu-id="8671a-108">The row template is also useful when you create your own classes derived from <xref:System.Windows.Forms.DataGridViewRow> and you want your custom type used when new rows are added to the control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8671a-109">行テンプレートは、行が追加されたときにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="8671a-109">The row template is used only when rows are added.</span></span> <span data-ttu-id="8671a-110">行テンプレートを変更することで既存の行を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="8671a-110">You cannot change existing rows by changing the row template.</span></span>  
  
### <a name="to-use-the-row-template"></a><span data-ttu-id="8671a-111">行テンプレートを使用するには</span><span class="sxs-lookup"><span data-stu-id="8671a-111">To use the row template</span></span>  
  
-   <span data-ttu-id="8671a-112">取得したオブジェクトのプロパティを設定、<xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="8671a-112">Set properties on the object retrieved from the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8671a-113">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="8671a-113">Compiling the Code</span></span>  
 <span data-ttu-id="8671a-114">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8671a-114">This example requires:</span></span>  
  
-   <span data-ttu-id="8671a-115">`dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。</span><span class="sxs-lookup"><span data-stu-id="8671a-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="8671a-116"><xref:System?displayProperty=nameWithType>、<xref:System.Drawing?displayProperty=nameWithType>、および <xref:System.Windows.Forms?displayProperty=nameWithType> の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="8671a-116">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8671a-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="8671a-117">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="8671a-118">Windows フォームの DataGridView コントロールの基本的な書式設定およびスタイル設定</span><span class="sxs-lookup"><span data-stu-id="8671a-118">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="8671a-119">Windows フォーム DataGridView コントロールでのセルのスタイル</span><span class="sxs-lookup"><span data-stu-id="8671a-119">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)
