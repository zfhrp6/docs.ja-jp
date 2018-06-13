---
title: '方法 : Windows フォーム ListView コントロール内の項目を選択する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lists [Windows Forms], selecting items
- ListView control [Windows Forms], selecting items
- selection [Windows Forms], in list views
- list views [Windows Forms], selecting items
ms.assetid: ddea918e-1ddf-47f4-bd09-1e9b4c9d0c39
ms.openlocfilehash: 8256eaeddf98c5a0dd80357bcd562e8f66db85b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532822"
---
# <a name="how-to-select-an-item-in-the-windows-forms-listview-control"></a><span data-ttu-id="ea707-102">方法 : Windows フォーム ListView コントロール内の項目を選択する</span><span class="sxs-lookup"><span data-stu-id="ea707-102">How to: Select an Item in the Windows Forms ListView Control</span></span>
<span data-ttu-id="ea707-103">この例は、プログラムで Windows フォーム内の項目を選択する方法を示します<xref:System.Windows.Forms.ListView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="ea707-103">This example demonstrates how to programmatically select an item in a Windows Forms <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="ea707-104">項目をプログラムでを選択すると自動的に変わらないので、フォーカスを<xref:System.Windows.Forms.ListView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="ea707-104">Selecting an item programmatically does not automatically change the focus to the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="ea707-105">このため、通常もするように項目を選択するときに重点を置いた項目を設定します。</span><span class="sxs-lookup"><span data-stu-id="ea707-105">For this reason, you will typically also want to set the item as focused when selecting an item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea707-106">例</span><span class="sxs-lookup"><span data-stu-id="ea707-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ea707-107">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="ea707-107">Compiling the Code</span></span>  
 <span data-ttu-id="ea707-108">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ea707-108">This example requires:</span></span>  
  
-   <span data-ttu-id="ea707-109">A<xref:System.Windows.Forms.ListView>という名前のコントロール`listView1`には、少なくとも 1 つの項目を格納しています。</span><span class="sxs-lookup"><span data-stu-id="ea707-109">A <xref:System.Windows.Forms.ListView> control named `listView1` that contains at least one item.</span></span>  
  
-   <span data-ttu-id="ea707-110"><xref:System?displayProperty=nameWithType> 名前空間と <xref:System.Windows.Forms?displayProperty=nameWithType> 名前空間への参照。</span><span class="sxs-lookup"><span data-stu-id="ea707-110">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea707-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea707-111">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=nameWithType>
