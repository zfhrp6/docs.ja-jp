---
title: "方法 : 特定のデータ形式でデータを取得する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DataFormats クラス [WPF], 取得 (データを)"
  - "DataObject クラス [WPF], 取得 (データを)"
  - "ドラッグ アンド ドロップ [WPF], 取得 (データを)"
ms.assetid: a625acf3-1144-44cd-add7-456aefc3859f
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : 特定のデータ形式でデータを取得する
指定された形式でデータ オブジェクトからデータを取得する方法を次の例に示します。  
  
## 例  
  
### Description  
 次のコード例では、<xref:System.Windows.DataObject.GetDataPresent%28System.String%29> オーバーロードを使用して、指定したデータ形式が \(ネイティブで、または自動変換により\) 使用可能かどうかを最初に確認します。指定した形式が使用可能な場合は、<xref:System.Windows.DataObject.GetData%28System.String%29> メソッドを使用してデータを取得します。  
  
### コード  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
## 例  
  
### Description  
 次のコード例では、<xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> オーバーロードを使用して、指定したデータ形式がネイティブで使用可能かどうか \(自動変換可能なデータ形式はフィルター処理されます\) を最初に確認します。指定した形式が使用可能な場合は、<xref:System.Windows.DataObject.GetData%28System.String%29> メソッドを使用してデータを取得します。  
  
### コード  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat_native)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat_native)]  
  
## 参照  
 <xref:System.Windows.IDataObject>   
 [ドラッグ アンド ドロップの概要](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)