---
title: "方法 : データ オブジェクトへ複数のデータ形式を格納する | Microsoft Docs"
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
  - "DataFormats クラス [WPF], 格納 (複数の形式を)"
  - "DataObject クラス [WPF], 格納 (複数の形式を)"
  - "ドラッグ アンド ドロップ [WPF], 格納 (複数の形式を)"
ms.assetid: 941ace29-29c4-4c26-b75b-ea7d06aa0d69
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : データ オブジェクトへ複数のデータ形式を格納する
次の例は、<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> メソッドを使用してデータを複数の形式のデータ オブジェクトに追加する方法を示しています。  
  
## 例  
  
### Description  
  
### コード  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
## 参照  
 <xref:System.Windows.IDataObject>   
 [ドラッグ アンド ドロップの概要](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)