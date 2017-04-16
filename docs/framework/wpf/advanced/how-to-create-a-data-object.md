---
title: "方法 : データ オブジェクトを作成する | Microsoft Docs"
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
  - "データ オブジェクト [WPF], 作成"
  - "DataObject クラス [WPF], 作成"
  - "ドラッグ アンド ドロップ [WPF], 作成 (データ オブジェクトを)"
ms.assetid: 022fa142-717d-4fea-a53c-3b52e9d91aff
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : データ オブジェクトを作成する
<xref:System.Windows.DataObject> クラスによって提供されるコンストラクターを使用してデータ オブジェクトを作成するためのさまざまな方法を次の例に示します。  
  
## 例  
  
### Description  
 新しいデータ オブジェクトを作成し、オーバーロードされたコンストラクターのいずれか \(<xref:System.Windows.DataObject.%23ctor%28System.Object%29>\) を使用して、文字列でデータ オブジェクトを初期化するコード例を次に示します。  ここでは、格納されているデータの型に応じて適切なデータ形式が自動的に判別されます。既定では、格納されるデータの自動変換が有効です。  
  
### コード  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple)]  
  
### Description  
 次のコード例は、上記のコードの縮小バージョンです。  
  
### コード  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple_condensed)]  
  
## 例  
  
### Description  
 新しいデータ オブジェクトを作成し、オーバーロードされたこのコンストラクターのいずれか \(<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>\) を使用して、文字列と指定したデータ形式でデータ オブジェクトを初期化するコード例を次に示します。  ここでは、データ形式は文字列によって指定されます。<xref:System.Windows.DataFormats> クラスは、事前定義されている一連の型文字列を提供します。  既定では、格納されるデータの自動変換が有効です。  
  
### コード  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
### Description  
 次のコード例は、上記のコードの縮小バージョンです。  
  
### コード  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring_condensed)]  
  
## 例  
  
### Description  
 新しいデータ オブジェクトを作成し、オーバーロードされたこのコンストラクターのいずれか \(<xref:System.Windows.DataObject.%23ctor%2A>\) を使用して、文字列と指定したデータ形式でデータ オブジェクトを初期化するコード例を次に示します。  この場合、データ形式は <xref:System.Type> パラメーターによって指定されます。  既定では、格納されるデータの自動変換が有効です。  
  
### コード  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type)]  
  
### Description  
 次のコード例は、上記のコードの縮小バージョンです。  
  
### コード  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type_condensed)]  
  
## 例  
  
### Description  
 新しいデータ オブジェクトを作成し、オーバーロードされたこのコンストラクターのいずれか \(<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%2CSystem.Boolean%29>\) を使用して、文字列と指定したデータ形式でデータ オブジェクトを初期化するコード例を次に示します。  ここでは、データ形式は文字列によって指定されます。<xref:System.Windows.DataFormats> クラスは、事前定義されている一連の型文字列を提供します。  この特定のコンストラクター オーバーロードにより、呼び出し元で自動変換を有効にするかどうかを指定できます。  
  
### コード  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert)]  
  
### Description  
 次のコード例は、上記のコードの縮小バージョンです。  
  
### コード  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert_condensed)]  
  
## 参照  
 <xref:System.Windows.IDataObject>