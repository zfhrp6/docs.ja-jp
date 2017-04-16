---
title: "方法 : データ オブジェクト内のデータ形式の一覧を表示する | Microsoft Docs"
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
  - "データ形式 [WPF], リスト"
  - "DataFormats クラス [WPF]"
  - "ドラッグ アンド ドロップ [WPF], 一覧表示 (データ形式を)"
ms.assetid: 18e7ba4b-ccef-4815-ae2d-3a32891010c0
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : データ オブジェクト内のデータ形式の一覧を表示する
<xref:System.Windows.DataObject.GetFormats%2A> メソッドのオーバーロードを使用して、データ オブジェクトで使用可能な各データ形式を示す文字列の配列を取得する方法を次の例に示します。  
  
## 例  
  
### Description  
 <xref:System.Windows.DataObject.GetFormats%2A> オーバーロードを使用して、データ オブジェクトで使用可能なすべてのデータ形式 \(ネイティブおよび自動変換可能の両方\) を示す一連の文字列を取得するコード例を次に示します。  
  
### コード  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
## 例  
  
### Description  
 <xref:System.Windows.DataObject.GetFormats%2A> オーバーロードを使用して、データ オブジェクトで使用できるデータ形式のみを示す一連の文字列を取得するコード例を次に示します \(自動変換可能なデータ形式はフィルター処理されます\)。  
  
### コード  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats_nativeonly)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats_nativeonly)]  
  
## 参照  
 <xref:System.Windows.IDataObject>   
 [ドラッグ アンド ドロップの概要](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)