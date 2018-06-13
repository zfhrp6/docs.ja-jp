---
title: '方法 : データ オブジェクト内のデータ形式の一覧を表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], listing data formats
- DataFormats class [WPF]
- data formats [WPF], listing
ms.assetid: 18e7ba4b-ccef-4815-ae2d-3a32891010c0
ms.openlocfilehash: c0e5917d52d9253737a56307beed69bc0255807c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543482"
---
# <a name="how-to-list-the-data-formats-in-a-data-object"></a><span data-ttu-id="b425b-102">方法 : データ オブジェクト内のデータ形式の一覧を表示する</span><span class="sxs-lookup"><span data-stu-id="b425b-102">How to: List the Data Formats in a Data Object</span></span>
<span data-ttu-id="b425b-103">次の例を使用する方法を示して、<xref:System.Windows.DataObject.GetFormats%2A>メソッドのオーバー ロードは、各データ オブジェクトで使用可能なデータ形式を示す文字列の配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="b425b-103">The following examples show how to use the <xref:System.Windows.DataObject.GetFormats%2A> method overloads get an array of strings denoting each data format that is available in a data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b425b-104">例</span><span class="sxs-lookup"><span data-stu-id="b425b-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="b425b-105">説明</span><span class="sxs-lookup"><span data-stu-id="b425b-105">Description</span></span>  
 <span data-ttu-id="b425b-106">次のコード例を使用して、 <xref:System.Windows.DataObject.GetFormats%2A> (ネイティブおよび自動変換可能) は、データ オブジェクトで使用可能なすべてのデータ形式を示す文字列の配列を取得するオーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="b425b-106">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting all data formats available in a data object (both native and auto-convertible).</span></span>  
  
### <a name="code"></a><span data-ttu-id="b425b-107">コード</span><span class="sxs-lookup"><span data-stu-id="b425b-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
## <a name="example"></a><span data-ttu-id="b425b-108">例</span><span class="sxs-lookup"><span data-stu-id="b425b-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="b425b-109">説明</span><span class="sxs-lookup"><span data-stu-id="b425b-109">Description</span></span>  
 <span data-ttu-id="b425b-110">次のコード例を使用して、<xref:System.Windows.DataObject.GetFormats%2A>データ オブジェクト (自動変換可能データの形式がフィルター選択) で使用可能なデータ形式のみを示す文字列の配列を取得するオーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="b425b-110">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting only data formats available in a data object (auto-convertible data formats are filtered).</span></span>  
  
### <a name="code"></a><span data-ttu-id="b425b-111">コード</span><span class="sxs-lookup"><span data-stu-id="b425b-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats_nativeonly)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats_nativeonly)]  
  
## <a name="see-also"></a><span data-ttu-id="b425b-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="b425b-112">See Also</span></span>  
 <xref:System.Windows.IDataObject>  
 [<span data-ttu-id="b425b-113">ドラッグ アンド ドロップの概要</span><span class="sxs-lookup"><span data-stu-id="b425b-113">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
