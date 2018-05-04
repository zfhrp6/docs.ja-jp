---
title: DiffGrams
ms.date: 03/30/2017
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
ms.openlocfilehash: 2b04fd69af94ce49fb5973af5ac74c2933fe58bf
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="diffgrams"></a>DiffGrams
DiffGram は、データ要素の現在のバージョンと元のバージョンを識別する XML 形式です。 <xref:System.Data.DataSet> では、 の内容を読み込んで永続化するため、およびネットワーク接続経由で転送する場合にこの内容をシリアル化するために、DiffGram 形式が使用されます。 ときに、<xref:System.Data.DataSet>正確を再作成する内容、ただし、スキーマのすべての必要な情報を DiffGram に格納を DiffGram として書き込まれますが、 <xref:System.Data.DataSet>、両方の列の値を含む、**元**と**現在**行のバージョン、行エラー情報、および行の順序。  
  
 XML Web サービスから <xref:System.Data.DataSet> を送信または取得するときには、DiffGram 形式が暗黙的に使用されます。 さらの内容を読み込むときに、 <xref:System.Data.DataSet> XML を使用してから、 **ReadXml**メソッドの内容を記述する場合、または、 <xref:System.Data.DataSet> XML を使用して、 **WriteXml**メソッドを指定できますある内容読み取りまたは書き込みを DiffGram として。 詳細については、次を参照してください。 [XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)と[書き込み DataSet の内容を XML データとして](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)です。  
  
 .NET Framework では、DiffGram 形式は主に <xref:System.Data.DataSet> の内容をシリアル化するときの形式として使用されますが、Microsoft SQL Server データベース内のテーブル データを変更するときにも DiffGrams を使用できます。  
  
 Diffgram は、すべてのテーブルの内容の書き込みによって生成される、  **\<diffgram >** 要素。  
  
### <a name="to-generate-a-diffgram"></a>Diffgram を生成するには  
  
1.  ルート テーブル (親を一切持たないテーブル) のリストを生成します。  
  
2.  リストの各テーブルとその子孫について、すべての行の現在のバージョンを最初の Diffgram セクションに書き込みます。  
  
3.  各テーブルに対して、 <xref:System.Data.DataSet>、存在する場合に、すべての行の元のバージョンを書き出すの**\<する前に >** Diffgram のセクションでします。  
  
4.  行、エラーが発生したエラーの内容の書き込み、 **\<エラー >** Diffgram のセクションでします。  
  
 Diffgram は XML ファイルの上から下に向かって処理されます。  
  
### <a name="to-process-a-diffgram"></a>Diffgram を処理するには  
  
1.  Diffgram の最初のセクションを処理します。このセクションには、行の現在のバージョンが格納されています。  
  
2.  2 つ目の処理、または**\<する前に >** の元の行バージョンを格納するセクションを変更または削除された行。  
  
    > [!NOTE]
    >  行が削除済みとしてマークされていた場合、削除操作によってその行の子孫も削除される場合があります。この点は、現在の `Cascade` の <xref:System.Data.DataSet> プロパティに依存します。  
  
3.  プロセス、 **\<エラー >** セクションです。 このセクションの各項目について、指定された行および列のエラー情報を設定します。  
  
> [!NOTE]
>  <xref:System.Data.XmlWriteMode> を Diffgram に設定した場合、ターゲット <xref:System.Data.DataSet> の内容が、元の <xref:System.Data.DataSet> の内容と異なる場合があります。  
  
## <a name="diffgram-format"></a>DiffGram 形式  
 DiffGram 形式は、現在のデータ、元のデータ (または前のデータ)、エラーの 3 つのセクションから構成されています。DiffGram の例を次に示します。  
  
```xml  
<?xml version="1.0"?>  
<diffgr:diffgram   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"  
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1"  
         xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  
   <DataInstance>  
   </DataInstance>  
  
  <diffgr:before>  
  </diffgr:before>  
  
  <diffgr:errors>  
  </diffgr:errors>  
</diffgr:diffgram>  
```  
  
 DiffGram 形式を構成するデータ ブロックについて次に説明します。  
  
 **\<**  ***DataInstance***  **>**  
 この要素の名前***DataInstance***、このドキュメントでは説明のために使用します。 A ***DataInstance***要素を表します、<xref:System.Data.DataSet>の行または、<xref:System.Data.DataTable>です。 代わりに*DataInstance*、要素の名前には、<xref:System.Data.DataSet>または<xref:System.Data.DataTable>です。 DiffGram 形式のこのブロックには現在のデータが含まれています。現在のデータは、変更されている場合と未変更の場合があります。 要素、または変更された行が付いた、 **diffgr:hasChanges**注釈。  
  
 **\<diffgr:before>**  
 DiffGram 形式のこのブロックには、行の元の内容が含まれています。 このブロック内の要素が要素に一致する、 ***DataInstance***ブロックを使用して、 **diffgr:id**注釈。  
  
 **\<diffgr:errors>**  
 DiffGram 形式のこのブロックには、特定の行のエラー情報が含まれています、 ***DataInstance***ブロックします。 このブロック内の要素が要素に一致する、 ***DataInstance***ブロックを使用して、 **diffgr:id**注釈。  
  
## <a name="diffgram-annotations"></a>DiffGram 注釈  
 DiffGram では、<xref:System.Data.DataSet> の行バージョンやエラー情報を表すさまざまな DiffGram ブロックの要素を関連付けるため、いくつかの注釈が使用されます。  
  
 次の表では、DiffGram 名前空間で定義されている DiffGram 注釈**urn: スキーマ-microsoft-{urn:schemas-microsoft-com:xml-sql}-diffgram-v1**です。  
  
|注釈|説明|  
|----------------|-----------------|  
|**ID**|内の要素を組み合わせるために使用、  **\<diffgr: する前に >** と **\<diffgr:errors >** ブロック内の要素を**\<*****DataInstance*** **>** ブロックします。 値を使った、 **diffgr:id**注釈は、形式で *[TableName] [RowIdentifier]* です。 たとえば、`<Customers diffgr:id="Customers1">` のように指定します。|  
|**parentId**|要素を識別、 **\<** ***DataInstance*** **>** ブロックは、現在の要素の親要素です。 値を使った、 **diffgr:parentId**注釈は、形式で *[TableName] [RowIdentifier]* です。 たとえば、`<Orders diffgr:parentId="Customers1">` のように指定します。|  
|**hasChanges**|内の行を識別、 **\<** ***DataInstance*** **>** 変更をブロックします。 **HasChanges**注釈は、次の 2 つの値のいずれかを持つことができます。<br /><br /> **inserted**<br /> 識別、 **Added**行です。<br /><br /> **変更されました。**<br /> 識別、 **Modified**を含む行、**元**で行のバージョン、  **\<diffgr: する前に >** ブロックします。 注意してください**Deleted**の行、**元**で行のバージョン、  **\<diffgr: する前に >** ブロックが存在しません、注釈付き要素**\<**  ***DataInstance*** **>** ブロックします。|  
|**hasErrors**|内の行を識別、 **\<** ***DataInstance*** **>** ブロックを**RowError**です。 エラー要素を配置している、  **\<diffgr:errors >** ブロックします。|  
|**エラー**|テキストを含む、 **RowError**で特定の要素に対して、  **\<diffgr:errors >** ブロックします。|  
  
 <xref:System.Data.DataSet> の内容が DiffGram として読み取られる、または書き込まれるときには、上記以外の注釈も含まれます。 次の表に、これらの注釈を追加、名前空間で定義されている**urn: スキーマ-microsoft-{urn:schemas-microsoft-com:xml-sql}-msdata**です。  
  
|注釈|説明|  
|----------------|-----------------|  
|**RowOrder**|元のデータの行順序を保持し、特定の <xref:System.Data.DataTable> の行のインデックスを識別します。|  
|**非表示**|持つものとして列を識別、 **ColumnMapping**プロパティに設定**MappingType.Hidden**です。 属性は、の形式で記述された**msdata: 隠し** *[ColumnName]*="*値*"です。 たとえば、`<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">` のように指定します。<br /><br /> データが格納されている隠し列だけが DiffGram 属性として書き込まれます。 それ以外の場合は無視されます。|  
  
## <a name="sample-diffgram"></a>DiffGram のサンプル  
 DiffGram 形式の例を次に示します。 この例では、変更のコミット前のテーブル内の行に対する更新結果が示されています。 CustomerID の "ALFKI" である行は変更されていますが、更新されていません。 その結果は、**現在**で行の**diffgr:id** "Customers1"での**\<** ***DataInstance*** **>** ブロック、および**元**で行の**diffgr:id** "Customers1"での **\<diffgr: する前に >** ブロックします。 Customerid が"ANATR"の行が含まれています、 **RowError**で注釈が付いているため、`diffgr:hasErrors="true"`に関連する要素が存在しないと、  **\<diffgr:errors >** ブロックします。  
  
```xml  
<diffgr:diffgram xmlns:msdata="urn:schemas-microsoft-com:xml-msdata" xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
  <CustomerDataSet>  
    <Customers diffgr:id="Customers1" msdata:rowOrder="0" diffgr:hasChanges="modified">  
      <CustomerID>ALFKI</CustomerID>  
      <CompanyName>New Company</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers2" msdata:rowOrder="1" diffgram:hasErrors="true">  
      <CustomerID>ANATR</CustomerID>  
      <CompanyName>Ana Trujillo Emparedados y Helados</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers3" msdata:rowOrder="2">  
      <CustomerID>ANTON</CustomerID>  
      <CompanyName>Antonio Moreno Taquera</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers4" msdata:rowOrder="3">  
      <CustomerID>AROUT</CustomerID>  
      <CompanyName>Around the Horn</CompanyName>  
    </Customers>  
  </CustomerDataSet>  
  <diffgr:before>  
    <Customers diffgr:id="Customers1" msdata:rowOrder="0">  
      <CustomerID>ALFKI</CustomerID>  
      <CompanyName>Alfreds Futterkiste</CompanyName>  
    </Customers>  
  </diffgr:before>  
  <diffgr:errors>  
    <Customers diffgr:id="Customers2" diffgr:Error="An optimistic concurrency violation has occurred for this row."/>  
  </diffgr:errors>  
</diffgr:diffgram>  
```  
  
## <a name="see-also"></a>関連項目  
 [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [DataSet 内容の XML データとしての書き込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
