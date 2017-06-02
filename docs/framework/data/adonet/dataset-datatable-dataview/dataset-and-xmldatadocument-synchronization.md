---
title: "DataSet と XmlDataDocument の同期 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataSet と XmlDataDocument の同期
ADO.NET の <xref:System.Data.DataSet> には、データのリレーショナル表現があります。  階層データにアクセスするには、.NET Framework で使用できる XML クラスを使用できます。  従来、この 2 つのデータ表現は個別に使用されていました。  .NET Framework では、データのリレーショナル表現と階層表現の両方へリアルタイムに同期的な方法でアクセスできます。リレーショナル表現にアクセスするには **DataSet** オブジェクトを使用します。階層表現にアクセスするには <xref:System.Xml.XmlDataDocument> オブジェクトを使用します。  
  
 **DataSet** を **XmlDataDocument** と同期するときには、**DataSet** と **XmlDataDocument** で 1 つのデータ セットが使用されます。  つまり **DataSet** が変更されると、その変更内容が **XmlDataDocument** に反映されます。この逆の反映も行われます。  **DataSet** と **XmlDataDocument** の間のリレーションシップにより、1 つのアプリケーションから 1 つのデータ セットを使用して、**DataSet** の周囲に構築されたサービス スイート全体 \(Web フォーム、Windows フォーム コントロール、Visual Studio、.NET デザイナーなど\) にアクセスしたり、XML サービス スイート \(XSL \(Extensible Stylesheet Language\)、XSLT \(XSL Transformations\)、XPath \(XML Path Language\) など\) にアクセスしたりできる優れた柔軟性を実現します。  アプリケーションでアクセス対象とするサービス セットを選択する必要はありません。どちらのサービス セットにもアクセスできます。  
  
 **DataSet** を **XmlDataDocument** と同期する方法は数種類あります。  次の操作を行うことができます。  
  
-   **DataSet** にスキーマ \(リレーショナル構造\) とデータを読み込み、この **DataSet** を新しい **XmlDataDocument** と同期します。  この方法では、既存のリレーショナル データの階層ビューが作成されます。  次に例を示します。  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema and data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema and data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    ```  
  
-   **DataSet** にスキーマだけを読み込み、この **DataSet** \(厳密に型指定された **DataSet** など\) を **XmlDataDocument** と同期します。次に、XML ドキュメントから **XmlDataDocument** を読み込みます。  この方法では、既存の階層データのリレーショナル ビューが作成されます。  **DataSet** スキーマのテーブル名と列名が、同期をとる XML 要素の名前と一致している必要があります。  この名前の一致では、大文字と小文字が区別されます。  
  
     **DataSet** のスキーマが一致する必要があるのは、リレーショナル ビューで公開する XML 要素だけです。  つまり、このドキュメント上に非常に大きい XML ドキュメントと非常に小さなリレーショナル ウィンドウを作成できます。  **DataSet** が XML ドキュメントの一部だけを公開する場合でも、**XmlDataDocument** は XML ドキュメント全体を保持します。  この説明に関する詳しい例については、「[Dataset と XmlDataDocument の同期](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)」を参照してください。  
  
     **DataSet** を作成してそのスキーマを読み込み、**XmlDataDocument** と同期する手順を示すコード サンプルを次に示します。  **DataSet** スキーマが一致する必要があるのは、**XmlDataDocument** の中で **DataSet** を使用して公開する要素だけです。  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema, but not data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema, but not data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
     データが含まれている **DataSet** を **XmlDataDocument** と同期する場合には、**XmlDataDocument** を読み込むことはできません。  読み込もうとすると例外がスローされます。  
  
-   新しい **XmlDataDocument** を作成して、XML ドキュメントからこの **XmlDataDocument** を読み込みます。次に、**XmlDataDocument** の **DataSet** プロパティを使用してデータのリレーショナル ビューにアクセスします。  **DataSet** を使用して **XmlDataDocument** のデータを表示するには、**DataSet** スキーマを設定する必要があります。  この場合も、**DataSet** スキーマのテーブル名と列名が、同期をとる XML 要素の名前と一致している必要があります。  この名前の一致では、大文字と小文字が区別されます。  
  
     **XmlDataDocument** のデータのリレーショナル ビューにアクセスする方法を次のコード サンプルに示します。  
  
    ```vb  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument  
    Dim dataSet As DataSet = xmlDoc.DataSet  
  
    ' Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml")  
  
    ```  
  
    ```csharp  
    XmlDataDocument xmlDoc = new XmlDataDocument();  
    DataSet dataSet = xmlDoc.DataSet;  
  
    // Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
 **DataSet** を **XmlDataDocument** と同期するもう 1 つの利点は、XML ドキュメントが完全に保持されることです。  **ReadXml** を使用して XML ドキュメントのデータを **DataSet** に格納すると、**WriteXml** を使用してデータが XML ドキュメントとして書き込まれるときに、この XML ドキュメントと元の XML ドキュメントが大幅に異なる場合があります。  これは、**DataSet** では XML ドキュメントから読み込んだ空白などの書式設定や、要素順序などの階層情報が維持されないためです。  **DataSet** には、XML ドキュメントで無視された要素も含まれていません。これは、これらの要素が **Dataset** のスキーマに一致しないためです。  **XmlDataDocument** を **DataSet** と同期することで、元の XML ドキュメントの書式設定要素や階層要素の構造が **XmlDataDocument** で維持され、**DataSet** には **DataSet** に適切なデータおよびスキーマ情報だけが含まれます。  
  
 **DataSet** を **XmlDataDocument** と同期する場合、<xref:System.Data.DataRelation> オブジェクトが入れ子かどうかによって同期結果が異なります。  詳細については、「[DataRelation の入れ子化](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)」を参照してください。  
  
## このセクションの内容  
 [Dataset と XmlDataDocument の同期](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)  
 最小限のスキーマが含まれており、厳密に型指定された **DataSet** を **XmlDataDocument** と同期させるサンプルを示します。  
  
 [DataSet に対する XPath クエリの実行](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/performing-an-xpath-query-on-a-dataset.md)  
 **DataSet** の内容に対する XPath クエリの実行のサンプルを示します。  
  
 [DataSet への XSLT 変換の適用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)  
 **DataSet** の内容に対する XSLT 変換の適用サンプルを示します。  
  
## 関連項目  
 [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 **DataSet** がデータ ソースとして XML と対話する方法を、**DataSet** の内容を XML データとして読み込んで永続化する方法と共に説明します。  
  
 [DataRelation の入れ子化](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 **DataSet** の内容を XML データとして表現する場合における、入れ子になった **DataRelation** オブジェクトの重要性について説明します。また、このようなリレーションを作成する方法について説明します。  
  
 [DataSets、DataTables、および DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 **DataSet** について説明し、**DataSet** を使用したアプリケーション データの管理方法と、**DataSet** を使用したデータ ソース \(リレーショナル データベースや XML など\) との対話方法について説明します。  
  
 [XmlDataDocument クラス](frlrfSystemXmlXmlDataDocumentClassTopic)  
 **XmlDataDocument** クラスに関するリファレンス情報が収録されています。  
  
## 参照  
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)