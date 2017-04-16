---
title: "データとデータ オブジェクト | Microsoft Docs"
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
  - "データ転送 [WPF], ドラッグ アンド ドロップ"
  - "DataFormats クラス [WPF]"
  - "DataObject クラス [WPF]"
ms.assetid: 5967d557-1867-420f-a524-ae3af78402da
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# データとデータ オブジェクト
ドラッグ アンド ドロップ操作の一部として転送されるデータは、データ オブジェクトに格納されます。  概念上、データ オブジェクトは、次の項目の 1 つ以上のペアで構成されます。  
  
-   実際のデータを格納する <xref:System.Object>。  
  
-   対応するデータ形式の識別子。  
  
 データ自体は、基本 <xref:System.Object> として表すことができる任意の項目で構成できます。  対応するデータ形式は、データの形式に関するヒントを提供する文字列または <xref:System.Type> です。  データ オブジェクトは、データとデータ形式の複数ペアのホストをサポートします。これにより、単一のデータ オブジェクトでデータを複数の形式で提供できます。  
  
<a name="Data_and_Data_Objects"></a>   
## データ オブジェクト  
 すべてのデータ オブジェクトで、<xref:System.Windows.IDataObject> インターフェイスを実装する必要があります。このインターフェイスは、データ転送を可能にし、容易にする次の標準メソッド セットを提供します。  
  
|メソッド|概要|  
|----------|--------|  
|<xref:System.Windows.IDataObject.GetData%2A>|データ オブジェクトを指定したデータ形式で取得します。|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|データが指定した形式で使用可能かどうか、または指定した形式に変換可能かどうかをチェックします。|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|このデータ オブジェクトのデータが格納されているか、または変換可能である形式のリストを返します。|  
|<xref:System.Windows.IDataObject.SetData%2A>|指定したデータをこのデータ オブジェクトに格納します。|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、<xref:System.Windows.DataObject> クラスの <xref:System.Windows.IDataObject> の基本実装を提供します。  多くの一般的なデータ転送シナリオでは、標準の <xref:System.Windows.DataObject> クラスで十分です。  
  
 ビットマップ、CSV、ファイル、HTML、RTF、文字列、テキスト、オーディオなど、複数の定義済みの形式があります。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で提供される定義済みのデータ形式については、<xref:System.Windows.DataFormats> クラスのリファレンス トピックを参照してください。  
  
 一般的に、データ オブジェクトには、データの抽出時にある形式で格納されているデータを別の形式に自動的に変換する機能が含まれています。この機能は自動変換と呼ばれます。  データ オブジェクトで使用できるデータ形式を照会するときに、<xref:System.Windows.DataObject.GetFormats%28System.Boolean%29> メソッドまたは <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> メソッドを呼び出して `autoConvert` パラメーターを `false` に指定することで、自動変換可能なデータ形式をネイティブ データ形式からフィルター処理することができます。  <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29> メソッドを使用してデータをデータ オブジェクトに追加する場合、`autoConvert` パラメーターを `false` に設定してデータの自動変換を禁止することができます。  
  
<a name="Working_with_Data_Objects"></a>   
## データ オブジェクトの操作  
 ここでは、データ オブジェクトを作成および操作する一般的な手法について説明します。  
  
### 新しいデータ オブジェクトの作成  
 <xref:System.Windows.DataObject> クラスは、新しい <xref:System.Windows.DataObject> インスタンスに単一のデータとデータ形式のペアを容易に設定できるようにするいくつかのオーバーロードされたコンストラクターを提供します。  
  
 新しいデータ オブジェクトを作成し、オーバーロードされたこのコンストラクター <xref:System.Windows.DataObject.%23ctor%2A> \(<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>\) のいずれかを使用して、文字列と指定したデータ形式でデータ オブジェクトを初期化するコード例を次に示します。  ここでは、データ形式は文字列によって指定されます。<xref:System.Windows.DataFormats> クラスは、事前定義されている一連の型文字列を提供します。  既定では、格納されるデータの自動変換が有効です。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 データ オブジェクトを作成するコードの例については、「[データ オブジェクトを作成する](../../../../docs/framework/wpf/advanced/how-to-create-a-data-object.md)」を参照してください。  
  
### 複数の形式のデータの格納  
 単一のデータ オブジェクトに複数の形式でデータを格納できます。  単一のデータ オブジェクト内で複数のデータ形式を戦略的に使用すると、単一のデータ形式のみを表す場合よりも、データ オブジェクトを幅広いドロップ ターゲットで使用できる可能性が高くなります。  通常、ドラッグ ソースは潜在的なドロップ ターゲットで使用できるデータ形式に依存しない必要があることに注意してください。  
  
 次の例は、<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> メソッドを使用してデータを複数の形式のデータ オブジェクトに追加する方法を示しています。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### データ オブジェクトで使用可能な形式の照会  
 単一のデータ オブジェクトに任意の数のデータ形式を含めることができるため、データ オブジェクトには、使用可能なデータ形式のリストを取得する機能が含まれています。  
  
 <xref:System.Windows.DataObject.GetFormats%2A> オーバーロードを使用して、データ オブジェクトで使用可能なすべてのデータ形式 \(ネイティブおよび自動変換の両方で使用可能\) を示す一連の文字列を取得するコード例を次に示します。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 データ オブジェクトで使用可能なデータ形式を照会するコードの例については、「[データ オブジェクト内のデータ形式の一覧を表示する](../../../../docs/framework/wpf/advanced/how-to-list-the-data-formats-in-a-data-object.md)」を参照してください。  特定のデータ形式が存在するかどうかをデータ オブジェクトに照会する例については、「[データ形式がデータ オブジェクトに存在するかどうかを判別する](../../../../docs/framework/wpf/advanced/how-to-determine-if-a-data-format-is-present-in-a-data-object.md)」を参照してください。  
  
### データ オブジェクトからのデータの取得  
 データ オブジェクトから特定の形式のデータを取得するには、単に <xref:System.Windows.DataObject.GetData%2A> メソッドのいずれかを呼び出して目的のデータ形式を指定します。  <xref:System.Windows.DataObject.GetDataPresent%2A> メソッドのいずれかを使用すると、特定のデータ形式が存在するかどうかを確認できます。  <xref:System.Windows.DataObject.GetData%2A> は、<xref:System.Object> 内のデータを返します。データ形式に応じて、このオブジェクトを型固有のコンテナーにキャストできます。  
  
 <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> オーバーロードを使用して、指定したデータ形式が \(ネイティブで、または自動変換により\) 使用可能かどうかを確認するコード例を次に示します。  指定した形式が使用可能な場合は、<xref:System.Windows.DataObject.GetData%28System.String%29> メソッドを使用してデータを取得します。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 データ オブジェクトからデータを取得するコードの例については、「[特定のデータ形式でデータを取得する](../../../../docs/framework/wpf/advanced/how-to-retrieve-data-in-a-particular-data-format.md)」を参照してください。  
  
### データ オブジェクトからのデータの削除  
 データは、データ オブジェクトから直接削除できません。  データ オブジェクトからデータを事実上削除するには、次の手順に従います。  
  
1.  保持するデータのみを含む新しいデータ オブジェクトを作成します。  
  
2.  古いデータ オブジェクトから新しいデータ オブジェクトに目的のデータを "コピー" します。  データをコピーするには、<xref:System.Windows.DataObject.GetData%2A> メソッドのいずれかを使用して未処理データを含む <xref:System.Object> を取得し、<xref:System.Windows.DataObject.SetData%2A> メソッドのいずれかを使用してデータを新しいデータ オブジェクトに追加します。  
  
3.  古いデータ オブジェクトを新しいデータ オブジェクトに置き換えます。  
  
> [!NOTE]
>  <xref:System.Windows.DataObject.SetData%2A> メソッドは、データ オブジェクトへのデータの追加のみを行います。データとデータ形式が前回の呼び出しとまったく同じ場合でも、データの置換は行いません。  同じデータとデータ形式に対して <xref:System.Windows.DataObject.SetData%2A> を 2 回呼び出すと、そのデータとデータ形式がデータ オブジェクトに 2 回存在することになります。