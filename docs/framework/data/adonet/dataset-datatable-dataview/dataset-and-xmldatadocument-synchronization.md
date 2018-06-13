---
title: DataSet と XmlDataDocument の同期
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
ms.openlocfilehash: cb16d4fae5dc153361fe2cb31cfd6af9b4b83c68
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759167"
---
# <a name="dataset-and-xmldatadocument-synchronization"></a>DataSet と XmlDataDocument の同期
ADO.NET の <xref:System.Data.DataSet> には、データのリレーショナル表現があります。 階層データにアクセスするには、.NET Framework で使用できる XML クラスを使用できます。 従来、この 2 つのデータ表現は個別に使用されていました。 ただし、.NET Framework によりを使用してデータのリレーショナルおよび階層表現の両方へリアルタイムに同期のアクセス、**データセット**オブジェクトおよび<xref:System.Xml.XmlDataDocument>オブジェクト、それぞれします。  
  
 ときに、**データセット**と同期されて、 **XmlDataDocument**、両方のオブジェクトは単一のデータのセットを使用します。 つまり、変更する場合、**データセット**で、変更が反映されます、 **XmlDataDocument**、およびその逆です。 間のリレーションシップ、**データセット**と**XmlDataDocument**の構築されたサービス スイート全体にアクセスする、データの 1 つのセットを使用して、1 つのアプリケーションを許可することで優れた柔軟性を作成囲む、**データセット**(Web フォームや Windows フォーム コントロールの Visual Studio .NET デザイナーなど)、Extensible Stylesheet Language (XSL)、XSL Transformations (XSLT)、および XML パスを含む XML サービス スイートのだけでなく言語 (XPath)。 アプリケーションでアクセス対象とするサービス セットを選択する必要はありません。どちらのサービス セットにもアクセスできます。  
  
 同期するいくつかの方法、**データセット**で、 **XmlDataDocument**です。 次の操作を行うことができます。  
  
-   追加、**データセット**スキーマ (つまり、リレーショナル構造) とデータを使用し、それを新しい同期**XmlDataDocument**です。 この方法では、既存のリレーショナル データの階層ビューが作成されます。 例えば:  
  
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
  
-   追加、**データセット**スキーマのみを使用 (厳密に型指定されたなど**データセット**)、同期で、 **XmlDataDocument**、し、ロード、 **XmlDataDocument** XML ドキュメントからです。 この方法では、既存の階層データのリレーショナル ビューが作成されます。 テーブル名と列名、**データセット**スキーマは、同期をとる XML 要素の名前と一致する必要があります。 この名前の一致では、大文字と小文字が区別されます。  
  
     なおのスキーマ、**データセット**のみ、リレーショナル ビューで公開する、XML 要素と一致する必要があります。 つまり、このドキュメント上に非常に大きい XML ドキュメントと非常に小さなリレーショナル ウィンドウを作成できます。 **XmlDataDocument**いなくても、XML ドキュメント全体を保持、**データセット**ことの一部を公開するだけです。 (これの詳細な例についてを参照してください[DataSet と XmlDataDocument の同期](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)。)。  
  
     次のコード例を作成するための手順を示しています、**データセット**してそのスキーマを読み込みと同期して、 **XmlDataDocument**です。 なお、**データセット**スキーマだけの要素を照合する必要があります、 **XmlDataDocument**を使用して公開する、**データセット**です。  
  
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
  
     読み込むことはできません、 **XmlDataDocument**と同期されている場合、**データセット**データが含まれます。 読み込もうとすると例外がスローされます。  
  
-   新規作成**XmlDataDocument** 、XML ドキュメントからそれを読み込むしを使用して、データのリレーショナル ビューにアクセスし、**データセット**のプロパティ、 **XmlDataDocument**です。 スキーマを設定する必要があります、**データセット**内のデータのいずれかを表示する前に、 **XmlDataDocument**を使用して、**データセット**です。 ここでも、テーブル名と列名が、**データセット**スキーマは、同期をとる XML 要素の名前と一致する必要があります。 この名前の一致では、大文字と小文字が区別されます。  
  
     次のコード例は、内のデータのリレーショナル ビューにアクセスする方法を示しています、 **XmlDataDocument**です。  
  
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
  
 同期するもう 1 つの利点、 **XmlDataDocument**で、**データセット**XML ドキュメントの忠実性が維持されることができます。 場合、**データセット**による XML ドキュメントから読み込んだ**ReadXml**として XML ドキュメントを使用して、バックアップ データが書き込まれるときに、 **WriteXml**から大幅に異なる場合があります、元の XML ドキュメントです。 これは、ため、**データセット**空白、または XML ドキュメントからの要素の順序などの階層情報などの書式設定を保持しません。 **データセット**もこれらのスキーマが一致しないために無視された XML ドキュメントから要素を含んでいない、**データセット**です。 同期中、 **XmlDataDocument**で、**データセット**で保持するのには、元の XML ドキュメントの書式設定や階層要素の構造、 **XmlDataDocument**中、**データセット**データとスキーマの適切な情報だけを含む、**データセット**です。  
  
 同期するときに、**データセット**で、 **XmlDataDocument**、かどうかによって結果が異なる場合があります、<xref:System.Data.DataRelation>オブジェクトが入れ子になった。 詳細については、次を参照してください。 [Datarelation の入れ子](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [DataSet と XmlDataDocument の同期](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)  
 厳密に型指定の同期を示しています**データセット**、最小限のスキーマで、 **XmlDataDocument**です。  
  
 [DataSet に対する XPath クエリの実行](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/performing-an-xpath-query-on-a-dataset.md)  
 内容に対する XPath クエリの実行を示しています、**データセット**です。  
  
 [DataSet への XSLT 変換の適用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)  
 内容に対する XSLT 変換の適用を示しています、**データセット**です。  
  
## <a name="related-sections"></a>関連項目  
 [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 について説明しますが、どのように**データセット**読み込みの内容を保持するなど、データ ソースとして XML と対話、**データセット**XML データとして。  
  
 [DataRelation の入れ子化](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 重要性について説明入れ子になった**DataRelation**オブジェクトの内容を表す時に、**データセット**XML データとしてこれらのリレーションを作成する方法について説明します。  
  
 [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 について説明します、**データセット**およびアプリケーション データを管理し、リレーショナル データベースや XML などのデータ ソースと対話する方法です。  
  
 <xref:System.Xml.XmlDataDocument>  
 に関するリファレンス情報を含む、 **XmlDataDocument**クラスです。  
  
## <a name="see-also"></a>関連項目  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
