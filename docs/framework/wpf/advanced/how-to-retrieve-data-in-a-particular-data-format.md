---
title: "方法 : 特定のデータ形式でデータを取得する"
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
- drag-and-drop [WPF], retrieving data
- DataFormats class [WPF], retrieving data
- DataObject class [WPF], retrieving data
ms.assetid: a625acf3-1144-44cd-add7-456aefc3859f
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 884b017a69e55cfccc9201ad2d101017b0c290b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-data-in-a-particular-data-format"></a><span data-ttu-id="aaeb0-102">方法 : 特定のデータ形式でデータを取得する</span><span class="sxs-lookup"><span data-stu-id="aaeb0-102">How to: Retrieve Data in a Particular Data Format</span></span>
<span data-ttu-id="aaeb0-103">次の例では、指定した形式でデータ オブジェクトからデータを取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="aaeb0-103">The following examples show how to retrieve data from a data object in a specified format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aaeb0-104">例</span><span class="sxs-lookup"><span data-stu-id="aaeb0-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="aaeb0-105">説明</span><span class="sxs-lookup"><span data-stu-id="aaeb0-105">Description</span></span>  
 <span data-ttu-id="aaeb0-106">次のコード例を使用して、 <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> (ネイティブまたは自動変換を) は、最初に指定されたデータが書式設定を確認するオーバー ロードを利用できます。 例では、がを使用してデータを取得する場合は、指定した書式を使用できる、<xref:System.Windows.DataObject.GetData%28System.String%29>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="aaeb0-106">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to first check if a specified data format is available (natively or by auto-convert); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="aaeb0-107">コード</span><span class="sxs-lookup"><span data-stu-id="aaeb0-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
## <a name="example"></a><span data-ttu-id="aaeb0-108">例</span><span class="sxs-lookup"><span data-stu-id="aaeb0-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="aaeb0-109">説明</span><span class="sxs-lookup"><span data-stu-id="aaeb0-109">Description</span></span>  
 <span data-ttu-id="aaeb0-110">次のコード例を使用して、<xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29>のオーバー ロードを指定したデータ形式が使用可能なネイティブをまず確認 (自動変換可能なデータ形式は、フィルター選択); の例が、を使用して、データを取得する指定の形式が使用可能な場合は、<xref:System.Windows.DataObject.GetData%28System.String%29>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="aaeb0-110">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> overload to first check if a specified data format is available natively (auto-convertible data formats are filtered); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="aaeb0-111">コード</span><span class="sxs-lookup"><span data-stu-id="aaeb0-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat_native)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat_native)]  
  
## <a name="see-also"></a><span data-ttu-id="aaeb0-112">参照</span><span class="sxs-lookup"><span data-stu-id="aaeb0-112">See Also</span></span>  
 <xref:System.Windows.IDataObject>  
 [<span data-ttu-id="aaeb0-113">ドラッグ アンド ドロップの概要</span><span class="sxs-lookup"><span data-stu-id="aaeb0-113">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
