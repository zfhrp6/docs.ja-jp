---
title: "方法 : データ形式がデータ オブジェクトに存在するかどうかを判別する | Microsoft Docs"
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
  - "データ形式 [WPF], 判断 (存在するかどうかを)"
  - "DataFormats クラス [WPF]"
  - "ドラッグ アンド ドロップ [WPF], 存在するデータ形式"
ms.assetid: e487a454-c9fc-4e53-aeaa-c458d059ad4c
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : データ形式がデータ オブジェクトに存在するかどうかを判別する
さまざまな <xref:System.Windows.DataObject.GetDataPresent%2A> メソッドのオーバーロードを使用して、特定のデータ形式がデータ オブジェクトに存在するかどうかを照会する方法を次の例に示します。  
  
## 例  
  
### Description  
 <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> オーバーロードを使用して、記述子文字列ごとに特定のデータ形式の存在を照会するコード例を次に示します。  
  
### コード  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_string)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_string)]  
  
## 例  
  
### Description  
 <xref:System.Windows.DataObject.GetDataPresent%28System.Type%29> オーバーロードを使用して、型ごとに特定のデータ形式の存在を照会するコード例を次に示します。  
  
### コード  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_type)]  
  
## 例  
  
### Description  
 <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> オーバーロードを使用して記述子文字列ごとにデータを照会し、自動変換が可能なデータ形式の処理方法を指定するコード例を次に示します。  
  
### コード  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_autoconvert)]  
  
## 参照  
 <xref:System.Windows.IDataObject>