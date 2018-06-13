---
title: データとデータ オブジェクト
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data transfer [WPF], drag-and-drop
- DataFormats class [WPF]
- DataObject class [WPF]
ms.assetid: 5967d557-1867-420f-a524-ae3af78402da
ms.openlocfilehash: ff596dc7428c9d105a27999f216d33e735e35a22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540320"
---
# <a name="data-and-data-objects"></a>データとデータ オブジェクト
ドラッグ アンド ドロップ操作の一部として転送されるデータは、データ オブジェクトに格納されます。  概念的には、データ オブジェクトは、1 つ以上の次のペアで構成されます。  
  
-   <xref:System.Object>実際のデータを格納しています。  
  
-   対応するデータ形式の識別子。  
  
 データ自体をベースとして表すことができるもので構成できます<xref:System.Object>です。  対応するデータ形式は、文字列または<xref:System.Type>では、データの書式設定についてのヒントを提供します。  複数のデータ/データ形式のペア; をホストしているデータ オブジェクトのサポートこれにより、複数の形式でデータを提供する 1 つのデータ オブジェクト。  
  
<a name="Data_and_Data_Objects"></a>   
## <a name="data-objects"></a>データ オブジェクト  
 すべてのデータ オブジェクトを実装する必要があります、<xref:System.Windows.IDataObject>次の標準セットを有効にして、データ転送を容易にするメソッドを提供するインターフェイスです。  
  
|メソッド|まとめ|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|指定したデータ形式のデータ オブジェクトを取得します。|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|データで使用可能でまたは指定された形式に変換できるかどうかを確認します。|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|このデータ オブジェクトのデータでは、またはに変換できる形式の一覧を返します。|  
|<xref:System.Windows.IDataObject.SetData%2A>|このデータ オブジェクトに指定されたデータを格納します。|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 基本実装を提供<xref:System.Windows.IDataObject>で、<xref:System.Windows.DataObject>クラスです。 ストック<xref:System.Windows.DataObject>クラスは多くの一般的なデータ転送のシナリオのための十分なです。  
  
 ビットマップ、CSV、ファイル、HTML、RTF、文字列、テキスト、およびオーディオなど、いくつかの定義済みの形式があります。 提供される定義済みのデータ形式については[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を参照してください、<xref:System.Windows.DataFormats>クラスのリファレンス トピックです。  
  
 通常、データ オブジェクトでは、データの抽出中に 1 つの形式を別の形式で格納されているデータを自動的に変換するための機能この機能は、"自動変換"と呼ばれます。 データ形式のデータ オブジェクトで使用可能な場合、クエリを実行するときに自動変換可能なデータ形式をフィルター処理するネイティブ データ形式から呼び出し、<xref:System.Windows.DataObject.GetFormats%28System.Boolean%29>または<xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29>メソッドを指定して、`autoConvert`パラメーターとして`false`です。  データを使用して、データ オブジェクトに追加するときに、<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29>を設定して、メソッドのデータの自動変換を禁止することができます、`autoConvert`パラメーターを`false`です。  
  
<a name="Working_with_Data_Objects"></a>   
## <a name="working-with-data-objects"></a>データ オブジェクトの操作  
 このセクションでは、データ オブジェクトの作成と操作の一般的な手法について説明します。  
  
### <a name="creating-new-data-objects"></a>新しいデータ オブジェクトの作成  
 <xref:System.Windows.DataObject>クラスには、新しい設定を容易にするいくつかのオーバー ロードされたコンス トラクターが用意されています<xref:System.Windows.DataObject>1 つのデータ/データ形式のペアを持つインスタンス。  
  
 次のコード例は、新しいデータ オブジェクトを作成し、オーバー ロードされたコンス トラクターのいずれかを使用して<xref:System.Windows.DataObject.%23ctor%2A>(<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>) 文字列と指定したデータ形式でデータ オブジェクトを初期化します。  データの形式が文字列で指定されたこのケースでは、<xref:System.Windows.DataFormats>クラスには、事前に定義された型の文字列のセットが用意されています。 既定では、格納されたデータの自動変換を許可します。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 データ オブジェクトを作成するコードの例については、次を参照してください。[データ オブジェクトを作成](../../../../docs/framework/wpf/advanced/how-to-create-a-data-object.md)です。  
  
### <a name="storing-data-in-multiple-formats"></a>複数の形式でデータを格納します。  
 単一のデータ オブジェクトは、複数の形式でデータを格納することです。   1 つのデータ オブジェクト内の複数のデータ形式を戦略的に使用可能性のあるにより、データ オブジェクトのドロップ ターゲットをよりも多様なで使用できるだけの場合、1 つのデータ形式を表すことができます。  なお、一般に、ドラッグ ソースがドロップ ターゲットを潜在的なデータ形式に依存しない必要があります。  
  
 次の例を使用する方法を示しています、<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29>複数の形式でデータ オブジェクトにデータを追加します。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a>使用可能な形式のデータ オブジェクトを照会します。  
 単一のデータ オブジェクトには、データ形式の任意の数が含まれていることができます、ために、データ オブジェクトには、使用可能なデータ形式の一覧を取得するための機能が含まれます。  
  
 次のコード例を使用して、 <xref:System.Windows.DataObject.GetFormats%2A> (ネイティブおよび自動変換によって) データ オブジェクトで使用可能なすべてのデータ形式を示す文字列の配列を取得するオーバー ロードします。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 使用可能なデータ形式のデータ オブジェクトのクエリを実行するコードの例については、次を参照してください。[データ オブジェクト内のデータ形式を一覧表示](../../../../docs/framework/wpf/advanced/how-to-list-the-data-formats-in-a-data-object.md)です。  特定のデータ形式が存在するためのデータ オブジェクトを照会する例については、次を参照してください。[データ形式が存在かどうかを判断データ オブジェクトで](../../../../docs/framework/wpf/advanced/how-to-determine-if-a-data-format-is-present-in-a-data-object.md)です。  
  
### <a name="retrieving-data-from-a-data-object"></a>データ オブジェクトからのデータの取得  
 いずれかの呼び出しでは、特定の形式でデータ オブジェクトからデータを取得するだけで、<xref:System.Windows.DataObject.GetData%2A>メソッドと目的のデータ形式を指定します。  1 つ、<xref:System.Windows.DataObject.GetDataPresent%2A>特定のデータ形式の存在をチェックするメソッドを使用できます。  <xref:System.Windows.DataObject.GetData%2A> 内のデータを返します、<xref:System.Object>以外の場合は、データ形式によってこのオブジェクトは、型固有のコンテナーにキャストすることができます。  
  
 次のコード例を使用して、<xref:System.Windows.DataObject.GetDataPresent%28System.String%29>のオーバー ロードを確認して、指定したデータ形式が使用可能なかどうか (ネイティブまたは自動変換)。 例を使用してデータを取得する場合は、指定した書式を使用できる、<xref:System.Windows.DataObject.GetData%28System.String%29>メソッドです。  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 データ オブジェクトからデータを取得するコードの例については、次を参照してください。 [、特定のデータ形式でデータの取得](../../../../docs/framework/wpf/advanced/how-to-retrieve-data-in-a-particular-data-format.md)です。  
  
### <a name="removing-data-from-a-data-object"></a>データ オブジェクトからデータを削除します。  
 データは、データ オブジェクトから直接削除できません。  効果的にデータ オブジェクトからデータを削除するには、次の手順を実行します。  
  
1.  保持するデータのみを格納する新しいデータ オブジェクトを作成します。  
  
2.  ""、必要なデータ old data オブジェクトから、新しいデータをオブジェクトにコピーします。  データをコピーするには、いずれかを使用、<xref:System.Windows.DataObject.GetData%2A>を取得するメソッド、<xref:System.Object>を生のデータを格納し、いずれかの<xref:System.Windows.DataObject.SetData%2A>新しいデータ オブジェクトにデータを追加する方法です。  
  
3.  古いデータ オブジェクトを新しいものに置き換えます。  
  
> [!NOTE]
>  <xref:System.Windows.DataObject.SetData%2A>メソッドは、データ オブジェクトをデータを追加するだけは、データとデータ形式が正確に前の呼び出しと同じ場合でも、データの置換は行いません。 呼び出す<xref:System.Windows.DataObject.SetData%2A>と同じデータに対して 2 回形式がデータ オブジェクトに 2 回含まれているデータ/データの形式で発生します。
