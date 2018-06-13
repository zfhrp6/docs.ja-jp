---
title: ADO.NET データセット
ms.date: 03/30/2017
ms.assetid: 82b641bb-6001-4512-bf1a-2830acdd92ab
ms.openlocfilehash: d7a73b11cae02abf8f61372c8d8684499781dda4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758517"
---
# <a name="adonet-datasets"></a>ADO.NET データセット
<xref:System.Data.DataSet> オブジェクトは、[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] で非接続型分散データ シナリオをサポートするうえで中心的な役割を果たします。 **データセット**データ ソースに関係なく一貫したリレーショナル プログラミング モデルを提供するデータのメモリ常駐型表現です。 複数の異なるデータ ソースや XML データと組み合わせて使用でき、アプリケーションにとってローカルなデータの管理にも使用できます。 **データセット**関連テーブル、制約、およびテーブル間のリレーションシップを含む、データの完全なセットを表します。 次の図は、**データセット**オブジェクト モデルです。  
  
 ![ADO.Net グラフィック](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
DataSet オブジェクト モデル  
  
 メソッドと内のオブジェクト、**データセット**リレーショナル データベースのモデルと一致します。  
  
 **データセット**も永続化し、その内容として、XML と XML スキーマ定義言語 (XSD) スキーマとしてスキーマを再度読み込むことができます。 詳しくは、「[DataSet での XML の使用](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)」を参照してください。  
  
## <a name="the-datatablecollection"></a>DataTableCollection  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] **データセット**によって表現される 0 個以上のテーブルのコレクションを格納<xref:System.Data.DataTable>オブジェクト。 <xref:System.Data.DataTableCollection>すべてが含まれています、 **DataTable**内のオブジェクト、**データセット**です。  
  
 A **DataTable**で定義された、<xref:System.Data>名前空間、メモリ常駐のデータの 1 つのテーブルを表します。 このテーブルには、共にテーブルのスキーマを定義する <xref:System.Data.DataColumnCollection> で表現される列と <xref:System.Data.ConstraintCollection> で表現される制約のコレクションが含まれます。 A **DataTable**もによって表される行のコレクションを含む、<xref:System.Data.DataRowCollection>テーブル内のデータが含まれています。 <xref:System.Data.DataRow> には、行に格納された値の変更を識別できるように、行の現在の状態と共に、行の現在のバージョンと元のバージョンの両方が保持されます。  
  
## <a name="the-dataview-class"></a>DataView クラス  
 <xref:System.Data.DataView> では、<xref:System.Data.DataTable> に格納されているデータのさまざまなビューを作成できます。この機能は、データ連結アプリケーションで頻繁に使用されます。 <xref:System.Data.DataView> を使用すると、テーブルのデータをさまざまな並べ替え順序で公開したり、行の状態やフィルター式に基づいてデータをフィルター処理したりできます。 詳細については、次を参照してください。 [Dataview](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)です。  
  
## <a name="the-datarelationcollection"></a>DataRelationCollection  
 A**データセット**内のリレーションシップが含まれています、<xref:System.Data.DataRelationCollection>オブジェクト。 によって表される、リレーションシップ、<xref:System.Data.DataRelation>オブジェクト、行に関連付けます**DataTable**別の行を含む**DataTable**です。 リレーションシップは、リレーショナル データベースの主キー列と外部キー列の間に存在する結合パスに似ています。 A **DataRelation**の 2 つのテーブルに一致する列を識別、**データセット**です。  
  
 リレーションシップが 1 つのテーブル内の別のナビゲーションを有効にする、**データセット**です。 重要な要素、 **DataRelation**はリレーションシップの名前、関連するテーブルの名前および関連する列の各テーブルにします。 <xref:System.Data.DataColumn> オブジェクトの配列をキー列として指定することによって、テーブルごとに複数の列を使用してリレーションシップを構築できます。 リレーションシップを追加すると、 <xref:System.Data.DataRelationCollection>、必要に応じて追加することができます、 **UniqueKeyConstraint**と**ForeignKeyConstraint**関連する列が変更されたときに、整合性制約を適用するには値。  
  
 詳細については、次を参照してください。 [Datarelation の追加](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)です。  
  
## <a name="xml"></a>XML  
 入力することを**データセット**XML ストリームまたはドキュメントからです。 指定する XML ストリームまたはドキュメントを使用することができます、**データセット**データ、スキーマ情報、またはその両方です。 XML ストリームまたはドキュメントから提供される情報は、既存のデータまたはスキーマ情報に既に存在と組み合わせることができます、**データセット**です。 詳しくは、「[DataSet での XML の使用](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)」を参照してください。  
  
## <a name="extendedproperties"></a>ExtendedProperties  
 **データセット**、 **DataTable**、および**DataColumn**がすべて、 **ExtendedProperties**プロパティです。 **ExtendedProperties**は、 **PropertyCollection**結果セットの生成に使用された SELECT ステートメントまたはデータの生成日時などのカスタム情報を配置することができます。 **ExtendedProperties**コレクションがのスキーマ情報と共に永続化、**データセット**です。  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] は、DataSet に格納された非接続型データに対する統合言語クエリ機能を提供します。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 標準の使用[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]構文し、Visual Studio IDE を使用しているときに、コンパイル時の構文チェック、静的な型指定、および IntelliSense のサポートを提供します。  
  
 詳細については、「[LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [ADO.NET の概要](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [DataSet、DataTable、および DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET でのデータの取得および変更](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
