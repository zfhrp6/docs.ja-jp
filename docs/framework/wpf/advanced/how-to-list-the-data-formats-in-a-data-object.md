---
title: "方法 : データ オブジェクト内のデータ形式の一覧を表示する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], listing data formats
- DataFormats class [WPF]
- data formats [WPF], listing
ms.assetid: 18e7ba4b-ccef-4815-ae2d-3a32891010c0
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cb27928031b551da2957aab0696646e8adc3f803
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-list-the-data-formats-in-a-data-object"></a><span data-ttu-id="9eba0-102">方法 : データ オブジェクト内のデータ形式の一覧を表示する</span><span class="sxs-lookup"><span data-stu-id="9eba0-102">How to: List the Data Formats in a Data Object</span></span>
<span data-ttu-id="9eba0-103">次の例を使用する方法を示して、<xref:System.Windows.DataObject.GetFormats%2A>メソッドのオーバー ロードは、各データ オブジェクトで使用可能なデータ形式を示す文字列の配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="9eba0-103">The following examples show how to use the <xref:System.Windows.DataObject.GetFormats%2A> method overloads get an array of strings denoting each data format that is available in a data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9eba0-104">例</span><span class="sxs-lookup"><span data-stu-id="9eba0-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="9eba0-105">説明</span><span class="sxs-lookup"><span data-stu-id="9eba0-105">Description</span></span>  
 <span data-ttu-id="9eba0-106">次のコード例を使用して、 <xref:System.Windows.DataObject.GetFormats%2A> (ネイティブおよび自動変換可能) は、データ オブジェクトで使用可能なすべてのデータ形式を示す文字列の配列を取得するオーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="9eba0-106">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting all data formats available in a data object (both native and auto-convertible).</span></span>  
  
### <a name="code"></a><span data-ttu-id="9eba0-107">コード</span><span class="sxs-lookup"><span data-stu-id="9eba0-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
## <a name="example"></a><span data-ttu-id="9eba0-108">例</span><span class="sxs-lookup"><span data-stu-id="9eba0-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="9eba0-109">説明</span><span class="sxs-lookup"><span data-stu-id="9eba0-109">Description</span></span>  
 <span data-ttu-id="9eba0-110">次のコード例を使用して、<xref:System.Windows.DataObject.GetFormats%2A>データ オブジェクト (自動変換可能データの形式がフィルター選択) で使用可能なデータ形式のみを示す文字列の配列を取得するオーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="9eba0-110">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting only data formats available in a data object (auto-convertible data formats are filtered).</span></span>  
  
### <a name="code"></a><span data-ttu-id="9eba0-111">コード</span><span class="sxs-lookup"><span data-stu-id="9eba0-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats_nativeonly)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats_nativeonly)]  
  
## <a name="see-also"></a><span data-ttu-id="9eba0-112">参照</span><span class="sxs-lookup"><span data-stu-id="9eba0-112">See Also</span></span>  
 <xref:System.Windows.IDataObject>  
 [<span data-ttu-id="9eba0-113">ドラッグ アンド ドロップの概要</span><span class="sxs-lookup"><span data-stu-id="9eba0-113">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
