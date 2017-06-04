---
title: "ADO.NET データセット | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 82b641bb-6001-4512-bf1a-2830acdd92ab
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# ADO.NET データセット
<xref:System.Data.DataSet>オブジェクトがサポートするための要に切断されると、分散データ シナリオを[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]します。 **データセット**データ ソースに関係なく、一貫性のあるリレーショナル プログラミング モデルを提供するデータのメモリ常駐型表現です。 複数の異なるデータ ソースや XML データと組み合わせて使用でき、アプリケーションにとってローカルなデータの管理にも使用できます。 **データセット**関連テーブル、制約、およびテーブル間のリレーションシップを含む、データの完全なセットを表します。 次の図は、**データセット**オブジェクト モデルです。  
  
 ![ADO.Net グラフィック](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
DataSet オブジェクト モデル  
  
 メソッドと内のオブジェクト、**データセット**リレーショナル データベースのモデルと一致します。  
  
 **データセット**永続化してその内容を XML としてとそのスキーマを XML スキーマ定義言語 (XSD) スキーマとして再読み込みできます。 詳細については、次を参照してください。[データセットを使用して XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)します。  
  
## <a name="the-datatablecollection"></a>DataTableCollection  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] **データセット**によって表現される&0; 個以上のテーブルのコレクションを含む<xref:System.Data.DataTable>オブジェクトです。 <xref:System.Data.DataTableCollection>すべてを含む、 **DataTable**内のオブジェクト、**データセット**します。  
  
 A **DataTable**で定義された、 <xref:System.Data>名前空間、メモリ常駐データの&1; つのテーブルを表します。 によって表される列のコレクションが含まれています、 <xref:System.Data.DataColumnCollection>、および制約で表される、 <xref:System.Data.ConstraintCollection>、共にテーブルのスキーマを定義します。 A **DataTable**もで表現される行のコレクションを格納、 <xref:System.Data.DataRowCollection>テーブルにデータを格納します。 現在の状態と共に、 <xref:System.Data.DataRow>両方のバージョンを保持現在と元の行に格納された値に対する変更を識別します。  
  
## <a name="the-dataview-class"></a>DataView クラス  
 A <xref:System.Data.DataView>に格納されたデータのさまざまなビューを作成することができます、 <xref:System.Data.DataTable>、データ連結アプリケーションでよく使用されている機能です。 使用して、 <xref:System.Data.DataView>さまざまな並べ替え順序のテーブル内のデータを公開する、および行の状態やフィルター式に基づいて、データをフィルター処理できます。 詳細については、次を参照してください。 [Dataview](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)します。  
  
## <a name="the-datarelationcollection"></a>DataRelationCollection  
 A**データセット**リレーションシップに含まれているその<xref:System.Data.DataRelationCollection>オブジェクトです。 によって表される、リレーションシップ、 <xref:System.Data.DataRelation>オブジェクト、行に関連付けます**DataTable**の行を別**DataTable**します。 リレーションシップは、リレーショナル データベースの主キー列と外部キー列の間に存在する結合パスに似ています。 A **DataRelation**の&2; つのテーブルで一致する列を識別、**データセット**します。  
  
 リレーションシップは、1 つのテーブル内の別のナビゲーションを有効にする、**データセット**します。 必須の要素、 **DataRelation**はリレーションシップの名前、関連するテーブルの名前、および各テーブルに関連する列。 配列を指定して&1; つのテーブルの&1; つ以上の列を持つリレーションシップを構築できます<xref:System.Data.DataColumn>オブジェクトをキー列として。 リレーションシップを追加すると、 <xref:System.Data.DataRelationCollection>、必要に応じて追加することができます、 **UniqueKeyConstraint**と**ForeignKeyConstraint**関連列の値に変更が加えられたときに整合性制約を適用します。  
  
 詳細については、次を参照してください。 [Datarelation の追加](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)します。  
  
## <a name="xml"></a>XML  
 入力することができます、**データセット**から XML ストリームまたはドキュメント。 XML ストリームまたはドキュメントを使用するときに提供する、**データセット**データ、スキーマ情報、またはその両方です。 XML ストリームまたはドキュメントから提供される情報は、既存のデータまたはスキーマ情報に既に存在と組み合わせることができます、**データセット**します。 詳細については、次を参照してください。[データセットを使用して XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)します。  
  
## <a name="extendedproperties"></a>ExtendedProperties  
 **データセット**、 **DataTable**、および**DataColumn**すべてである、 **ExtendedProperties**プロパティです。 **ExtendedProperties**は、 **PropertyCollection**結果セットの生成に使用された SELECT ステートメントまたはデータが生成された時刻などの独自の情報を配置することができます。 **ExtendedProperties**コレクションがのスキーマ情報と共に永続化、**データセット**します。  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] は、DataSet に格納された非接続型データに対する統合言語クエリ機能を提供します。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]規格を使用して[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]構文を使用しているときに、コンパイル時の構文チェック、静的な型指定、および IntelliSense のサポートを提供し、 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] IDE です。  
  
 詳細については、次を参照してください。 [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md)します。  
  
## <a name="see-also"></a>関連項目  
 [ADO.NET の概要](../../../../docs/framework/data/adonet/ado-net-overview.md)   
 [Dataset、Datatable、および Dataview](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [取得して、ADO.NET でのデータを変更します。](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [ADO.NET マネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)