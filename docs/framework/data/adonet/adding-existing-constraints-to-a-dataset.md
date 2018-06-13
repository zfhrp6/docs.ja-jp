---
title: DataSet への既存の制約の追加
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: c3c28392a9e4bee0e2f9e0dcf553e13b67c378dd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758358"
---
# <a name="adding-existing-constraints-to-a-dataset"></a>DataSet への既存の制約の追加
**塗りつぶし**のメソッド、 **DataAdapter**塗りつぶします、<xref:System.Data.DataSet>のみテーブルの列およびデータ ソースからの行も制約は一般設定、データ ソースによって、 **を塗りつぶす**メソッドでは、このスキーマ情報には追加されません、**データセット**既定です。 設定する、**データセット**呼び出すかを使用してデータ ソースから既存の主キー制約情報できます、 **FillSchema**のメソッド、 **DataAdapter**、設定や、**MissingSchemaAction**のプロパティ、 **DataAdapter**に**AddWithKey**呼び出す前に**塗りつぶし**です。 これが主キーをにより、内の制約、**データセット**データ ソースに反映します。 外部キー制約情報が含まれていないのように、明示的に作成する必要があります[DataTable の制約](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)です。  
  
 スキーマ情報を追加する、**データセット**主キー制約に含まれているようにデータを設定する前に、<xref:System.Data.DataTable>内のオブジェクト、**データセット**です。 その結果、追加時に入力への呼び出し、**データセット**が行われますが、プライマリ キー列情報を使用して、現在の行の各データ ソースから新しい行と一致**DataTable**との現在のデータテーブルは、データ ソースのデータで上書きされます。 スキーマ情報がない場合、新しいデータ ソースから行が、**データセット**、その結果が重複する行にします。  
  
> [!NOTE]
>  データ ソース内の列が自動インクリメントとして識別された場合、 **FillSchema**メソッド、または**塗りつぶし**メソッドを**MissingSchemaAction**の**AddWithKey**、作成、 **DataColumn**で、 **AutoIncrement**プロパティに設定`true`です。 ただしを設定する必要がありますには、 **AutoIncrementStep**と**AutoIncrementSeed**値を自分でします。 自動インクリメント列の詳細については、次を参照してください。 [AutoIncrement 列の作成](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)です。  
  
 使用して**FillSchema**またはの設定、 **MissingSchemaAction**に**AddWithKey**主キー列情報を確認するのにはデータ ソースで余分な処理が必要です。 この追加の処理によりパフォーマンスが低下する場合があります。 デザイン時に主キー情報がわかっている場合は、最適のパフォーマンスを得るために主キー列 (複数の場合もある) を明示的に指定することをお勧めします。 テーブルの主キーの情報を明示的に設定については、次を参照してください。[主キーを定義する](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)です。  
  
 次のコード例は、スキーマ情報を追加する方法を示しています、**データセット**を使用して**FillSchema**です。  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers")  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers");  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
 次のコード例は、スキーマ情報を追加する方法を示しています、**データセット**を使用して、 **MissingSchemaAction.AddWithKey**のプロパティ、**塗りつぶし**メソッドです。  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
## <a name="handling-multiple-result-sets"></a>複数の結果セットの処理  
 場合、 **DataAdapter**から返された複数の結果セットが発生した、 **SelectCommand**、複数のテーブルが作成されます、**データセット**です。 テーブルが、0 から始まるインクリメンタル既定名を指定する**テーブル** *N*以降で、**テーブル**したがって"Table0"の代わりにします。 テーブル名がへの引数として渡されたかどうか、 **FillSchema**メソッド、テーブルがある、0 から始まるインクリメンタル名**TableName** *N*始まる**TableName** "TableName0"ではなくです。  
  
> [!NOTE]
>  場合、 **FillSchema**のメソッド、 **OleDbDataAdapter**を複数の結果セットを返すコマンドのオブジェクトが呼び出されると、最初の結果セットからスキーマ情報のみが返されます。 ときに複数の結果のスキーマ情報セットを返すを使用して、 **OleDbDataAdapter**を指定することをお勧め、 **MissingSchemaAction**の**AddWithKey**呼び出すときに、スキーマ情報を取得し、**塗りつぶし**メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [DataAdapter と DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [DataSet、DataTable、および DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET でのデータの取得および変更](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
