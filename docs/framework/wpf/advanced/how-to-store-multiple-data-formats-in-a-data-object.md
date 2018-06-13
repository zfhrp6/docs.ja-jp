---
title: '方法 : データ オブジェクトへ複数のデータ形式を格納する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataObject class [WPF], storing multiple formats
- DataFormats class [WPF], storing multiple formats
- drag-and-drop [WPF], storing multiple formats
ms.assetid: 941ace29-29c4-4c26-b75b-ea7d06aa0d69
ms.openlocfilehash: e47d0aa2fe1c573314551ad91a2199ca97fd61a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543469"
---
# <a name="how-to-store-multiple-data-formats-in-a-data-object"></a><span data-ttu-id="d0ecd-102">方法 : データ オブジェクトへ複数のデータ形式を格納する</span><span class="sxs-lookup"><span data-stu-id="d0ecd-102">How to: Store Multiple Data Formats in a Data Object</span></span>
<span data-ttu-id="d0ecd-103">次の例を使用する方法を示しています、<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29>複数の形式でデータ オブジェクトにデータを追加します。</span><span class="sxs-lookup"><span data-stu-id="d0ecd-103">The following example shows how to use the <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> method to add data to a data object in multiple formats.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0ecd-104">例</span><span class="sxs-lookup"><span data-stu-id="d0ecd-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="d0ecd-105">説明</span><span class="sxs-lookup"><span data-stu-id="d0ecd-105">Description</span></span>  
  
### <a name="code"></a><span data-ttu-id="d0ecd-106">コード</span><span class="sxs-lookup"><span data-stu-id="d0ecd-106">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
## <a name="see-also"></a><span data-ttu-id="d0ecd-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="d0ecd-107">See Also</span></span>  
 <xref:System.Windows.IDataObject>  
 [<span data-ttu-id="d0ecd-108">ドラッグ アンド ドロップの概要</span><span class="sxs-lookup"><span data-stu-id="d0ecd-108">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
