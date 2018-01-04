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
# <a name="how-to-retrieve-data-in-a-particular-data-format"></a>方法 : 特定のデータ形式でデータを取得する
次の例では、指定した形式でデータ オブジェクトからデータを取得する方法を示します。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次のコード例を使用して、 <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> (ネイティブまたは自動変換を) は、最初に指定されたデータが書式設定を確認するオーバー ロードを利用できます。 例では、がを使用してデータを取得する場合は、指定した書式を使用できる、<xref:System.Windows.DataObject.GetData%28System.String%29>メソッドです。  
  
### <a name="code"></a>コード  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次のコード例を使用して、<xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29>のオーバー ロードを指定したデータ形式が使用可能なネイティブをまず確認 (自動変換可能なデータ形式は、フィルター選択); の例が、を使用して、データを取得する指定の形式が使用可能な場合は、<xref:System.Windows.DataObject.GetData%28System.String%29>メソッドです。  
  
### <a name="code"></a>コード  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat_native)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat_native)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.IDataObject>  
 [ドラッグ アンド ドロップの概要](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
