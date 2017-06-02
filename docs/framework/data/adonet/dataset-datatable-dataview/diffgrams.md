---
title: "DiffGram | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DiffGram
DiffGram は、データ要素の現在のバージョンと元のバージョンを識別する XML 形式です。  <xref:System.Data.DataSet> では、<xref:System.Data.DataSet> の内容を読み込んで永続化するため、およびネットワーク接続経由で転送する場合にこの内容をシリアル化するために、DiffGram 形式が使用されます。  DiffGram として作成された <xref:System.Data.DataSet> は、スキーマを使用せずに <xref:System.Data.DataSet> の内容を正確に再作成するために必要なすべての情報を DiffGram に格納します。このような情報には、**Original** 行バージョンと **Current** 行バージョンの両方の列値、行エラー情報、行順序などが含まれています。  
  
 XML Web サービスから <xref:System.Data.DataSet> を送信または取得するときには、DiffGram 形式が暗黙的に使用されます。  また、**ReadXml** メソッドを使用して XML から <xref:System.Data.DataSet> の内容を読み取るときや、**WriteXml** メソッドを使用して XML に <xref:System.Data.DataSet> の内容を書き込むときは、読み取りまたは書き込みの形式として DiffGram を指定できます。  詳細については、「[XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)」および「[DataSet 内容の XML データとしての書き込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)」を参照してください。  
  
 .NET Framework では、DiffGram 形式は主に <xref:System.Data.DataSet> の内容をシリアル化するときの形式として使用されますが、Microsoft SQL Server データベース内のテーブル データを変更するときにも DiffGrams を使用できます。  
  
 Diffgram は、すべてのテーブルの内容を **\<diffgram\>** 要素に書き込むことによって生成されます。  
  
### Diffgram を生成するには  
  
1.  ルート テーブル \(親を一切持たないテーブル\) のリストを生成します。  
  
2.  リストの各テーブルとその子孫について、すべての行の現在のバージョンを最初の Diffgram セクションに書き込みます。  
  
3.  <xref:System.Data.DataSet> の各テーブルについて、すべての行の元のバージョン \(存在する場合\) を Diffgram の **\<before\>** セクションに書き込みます。  
  
4.  エラーのある行については、そのエラーの内容を Diffgram の **\<errors\>** セクションに書き込みます。  
  
 Diffgram は XML ファイルの上から下に向かって処理されます。  
  
### Diffgram を処理するには  
  
1.  Diffgram の最初のセクションを処理します。このセクションには、行の現在のバージョンが格納されています。  
  
2.  2 番目のセクションまたは **\<before\>** セクションを処理します。このセクションには、修正または削除された行の元のバージョンが格納されています。  
  
    > [!NOTE]
    >  行が削除済みとしてマークされていた場合、削除操作によってその行の子孫も削除される場合があります。この点は、現在の <xref:System.Data.DataSet> の `Cascade` プロパティに依存します。  
  
3.  **\<errors\>** セクションを処理します。  このセクションの各項目について、指定された行および列のエラー情報を設定します。  
  
> [!NOTE]
>  <xref:System.Data.XmlWriteMode> を Diffgram に設定した場合、ターゲット <xref:System.Data.DataSet> の内容が、元の <xref:System.Data.DataSet> の内容と異なる場合があります。  
  
## DiffGram 形式  
 DiffGram 形式は、現在のデータ、元のデータ \(または前のデータ\)、エラーの 3 つのセクションから構成されています。DiffGram の例を次に示します。  
  
```  
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
  
 **\<**  ***DataInstance***  **\>**  
 このドキュメントでは、説明の目的でこの要素の名前である ***DataInstance*** を使用します。  ***DataInstance*** 要素は、<xref:System.Data.DataTable> の行または <xref:System.Data.DataSet> を表します。  実際には *DataInstance* の代わりに <xref:System.Data.DataSet> または <xref:System.Data.DataTable> の名前がこの要素に含まれます。  DiffGram 形式のこのブロックには現在のデータが含まれています。現在のデータは、変更されている場合と未変更の場合があります。  変更されている要素 \(行\) を識別するため、このような要素には **diffgr:hasChanges** 注釈が付きます。  
  
 **\<diffgr:before\>**  
 DiffGram 形式のこのブロックには、行の元の内容が含まれています。  このブロックの要素は、**diffgr:id** 注釈を使用して ***DataInstance*** ブロックの内容と対応しています。  
  
 **\<diffgr:errors\>**  
 DiffGram 形式のこのブロックには、***DataInstance*** ブロックの特定の行に関するエラー情報が含まれています。  このブロックの要素は、**diffgr:id** 注釈を使用して ***DataInstance*** ブロックの内容と対応しています。  
  
## DiffGram 注釈  
 DiffGram では、<xref:System.Data.DataSet> の行バージョンやエラー情報を表すさまざまな DiffGram ブロックの要素を関連付けるため、いくつかの注釈が使用されます。  
  
 DiffGram 名前空間 **urn:schemas\-microsoft\-com:xml\-diffgram\-v1** で定義されている DiffGram 注釈を次の表に示します。  
  
|注釈|説明|  
|--------|--------|  
|**id**|**\<diffgr:before\>** ブロックと **\<diffgr:errors\>** ブロックの要素を **\<** ***DataInstance*** **\>** ブロックの要素と対応させるために使用されます。  **diffgr:id** 注釈の値は *\[TableName\]\[RowIdentifier\]* という形式で指定されます。  たとえば、`<Customers diffgr:id="Customers1">` のように指定します。|  
|**parentId**|現在の要素の親要素である **\<** ***DataInstance*** **\>** ブロックの要素を識別します。  **diffgr:parentId** 注釈の値は *\[TableName\]\[RowIdentifier\]* という形式で指定されます。  たとえば、`<Orders diffgr:parentId="Customers1">` のように指定します。|  
|**hasChanges**|**\<**  ***DataInstance***  **\>** ブロックの行を変更済みとして識別します。  **hasChanges** 注釈には、次の 2 つのうち、いずれかの値を指定できます。<br /><br /> **inserted**<br /> **Added** 行を識別します。<br /><br /> **modified**<br /> 対応する **Original** 行バージョンが **\<\<diffgr:before\>\>** ブロックに含まれている **Modified** 行を識別します。  **Deleted** 行の場合、対応する **Original** 行バージョンが **\<diffgr:before\>** ブロックには存在しますが、**\<** ***DataInstance*** **\>** ブロックには注釈付き要素が存在しません。|  
|**hasErrors**|**\<**  ***DataInstance***  **\>** ブロック内で **RowError** がある行を識別します。  エラー要素は **\<diffgr:errors\>** ブロックに挿入されます。|  
|**Error**|**\<diffgr:errors\>** ブロック内の特定の要素に関する **RowError** のテキストが含まれています。|  
  
 <xref:System.Data.DataSet> の内容が DiffGram として読み取られる、または書き込まれるときには、上記以外の注釈も含まれます。  名前空間 **urn:schemas\-microsoft\-com:xml\-msdata** で定義されている追加の注釈を次の表に示します。  
  
|注釈|説明|  
|--------|--------|  
|**RowOrder**|元のデータの行順序を保持し、特定の <xref:System.Data.DataTable> の行のインデックスを識別します。|  
|**非表示**|特定の列を **ColumnMapping** プロパティが **MappingType.Hidden** に設定されている列として識別します。  この属性は、**msdata:hidden** *\[ColumnName\]*\="*value*" という形式で書き込まれます。  たとえば、`<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">` のように指定します。<br /><br /> データが格納されている隠し列だけが DiffGram 属性として書き込まれます。  それ以外の場合は無視されます。|  
  
## DiffGram のサンプル  
 DiffGram 形式の例を次に示します。  この例では、変更のコミット前のテーブル内の行に対する更新結果が示されています。  CustomerID の "ALFKI" である行は変更されていますが、更新されていません。  このため、**\<** ***DataInstance*** **\>** ブロックに **diffgr:id** が "Customers1" の **Current** 行があり、**\<diffgr:before\>** ブロックに **diffgr:id** が "Customers1" の **Original** 行があります。  CustomerID が "ANATR" である行には **RowError** が含まれているため、この行には `diffgr:hasErrors="true"` という注釈が付いています。**\<diffgr:errors\>** ブロックに、この行に関連する要素があります。  
  
```  
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
  
## 参照  
 [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)   
 [DataSet 内容の XML データとしての書き込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)   
 [DataSets、DataTables、および DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)