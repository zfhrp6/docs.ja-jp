---
title: "DataTable イベントの処理 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62f404a5-13ea-4b93-a29f-55b74a16c9d3
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataTable イベントの処理
<xref:System.Data.DataTable> オブジェクトは、アプリケーションが処理できる一連のイベントを提供します。  `DataTable` のイベントを次の表に示します。  
  
|Event|説明|  
|-----------|--------|  
|<xref:System.Data.DataTable.Initialized>|`DataTable` の <xref:System.Data.DataTable.EndInit%2A> メソッドが呼び出された後に発生します。  このイベントは、主にデザイン時のシナリオをサポートすることを目的としています。|  
|<xref:System.Data.DataTable.ColumnChanged>|<xref:System.Data.DataColumn> で値が正常に変更された後に発生します。|  
|<xref:System.Data.DataTable.ColumnChanging>|`DataColumn` に対して値が送信されたときに発生します。|  
|<xref:System.Data.DataTable.RowChanged>|`DataColumn` 値または `DataTable` の <xref:System.Data.DataRow> の <xref:System.Data.DataRow.RowState%2A> が正常に変更された後で発生します。|  
|<xref:System.Data.DataTable.RowChanging>|`DataColumn` 値または `DataTable` の `DataRow` の `RowState` に対して変更が送信されたときに発生します。|  
|<xref:System.Data.DataTable.RowDeleted>|`DataTable` の `DataRow` が `Deleted` としてマークされた後に発生します。|  
|<xref:System.Data.DataTable.RowDeleting>|`DataTable` の `DataRow` が `Deleted` としてマークされる前に発生します。|  
|<xref:System.Data.DataTable.TableCleared>|`DataTable` の <xref:System.Data.DataTable.Clear%2A> メソッドがすべての `DataRow` を正常にクリアした後で発生します。|  
|<xref:System.Data.DataTable.TableClearing>|`Clear` メソッドが呼び出された後、`Clear` 操作が開始される前に発生します。|  
|<xref:System.Data.DataTable.TableNewRow>|`DataTable` の `NewRow` メソッドの呼び出しにより、新しい `DataRow` が作成された後で発生します。|  
|<xref:System.ComponentModel.MarshalByValueComponent.Disposed>|`DataTable` が破棄 \(`Disposed`\) されたときに発生します。  このプロパティは、<xref:System.ComponentModel.MarshalByValueComponent> から継承されています。|  
  
> [!NOTE]
>  行の追加または削除を行う操作の多くは、`ColumnChanged` イベントも `ColumnChanging` イベントも生成しません。  ただし、`ReadXml` メソッドでは、`XmlReadMode` が `DiffGram` または `Auto` \(読み込む XML ドキュメントが `DiffGram` の場合\) に設定されていない限り、`ColumnChanged` イベントおよび `ColumnChanging` イベントが生成されます。  
  
> [!WARNING]
>  `RowChanged` イベントの生成元の `DataSet` でデータが変更されると、データが破損する可能性があります。  このようなデータの破損が起きた場合、例外は発生しません。  
  
## その他の関連イベント  
 <xref:System.Data.DataTable.Constraints%2A> プロパティは <xref:System.Data.ConstraintCollection> インスタンスを保持します。  <xref:System.Data.ConstraintCollection> クラスは、<xref:System.Data.ConstraintCollection.CollectionChanged> イベントを公開します。  このイベントは、`ConstraintCollection` に対して制約の追加、変更、または削除が実行されたときに発生します。  
  
 <xref:System.Data.DataTable.Columns%2A> プロパティは <xref:System.Data.DataColumnCollection> インスタンスを保持します。  `DataColumnCollection` クラスは、<xref:System.Data.DataColumnCollection.CollectionChanged> イベントを公開します。  このイベントは、`DataColumn` が追加、変更、または `DataColumnCollection` から削除されたときに発生します。  イベントの発生を伴う変更には、名前の変更、型の変更、式の変更、列の序数位置の変更などがあります。  
  
 <xref:System.Data.DataSet> の <xref:System.Data.DataSet.Tables%2A> プロパティは <xref:System.Data.DataTableCollection> インスタンスを保持します。  `DataTableCollection` クラスは、`CollectionChanged` イベントと `CollectionChanging` イベントの両方を公開します。  これらのイベントは、`DataSet` に対して、`DataTable` の追加、変更、または削除が実行されたときに発生します。  
  
 `DataRows` への変更によって、関連する <xref:System.Data.DataView> のイベントがトリガーされる場合もあります。  `DataView` クラスは、`DataColumn` 値が変更されたとき、または、ビューの構成や並べ替え順が変更されたときに発生する <xref:System.Data.DataView.ListChanged> イベントを公開します。  <xref:System.Data.DataRowView> クラスは、関連する `DataColumn` 値が変更されたときに発生する <xref:System.Data.DataRowView.PropertyChanged> イベントを公開します。  
  
## 操作の順序  
 `DataRow` が追加、変更、または削除されたときに発生する操作の順序について説明します。  
  
1.  提示されたレコードを作成し、変更を適用します。  
  
2.  式以外の列の制約をチェックします。  
  
3.  適宜 `RowChanging` イベントまたは `RowDeleting` イベントを発生させます。  
  
4.  提示されたレコードを現在のレコードとして設定します。  
  
5.  関連するインデックスをすべて更新します。  
  
6.  関連する `DataView` オブジェクトの `ListChanged` イベントおよび関連する `DataRowView` オブジェクトの `PropertyChanged` イベントを発生させます。  
  
7.  すべての式列を評価します。ただし、これらの列に対する制約のチェックは、この段階では行われません。  
  
8.  式列の評価によって影響を受ける、関連する `DataView` オブジェクトの `ListChanged` イベントおよび関連する `DataRowView` オブジェクトの `PropertyChanged` イベントを発生させます。  
  
9. 適宜 `RowChanged` イベントまたは `RowDeleted` イベントを発生させます。  
  
10. 式列の制約をチェックします。  
  
> [!NOTE]
>  式列に対する変更で `DataTable` のイベントが発生することはありません。  式列に対する変更で発生するのは、`DataView` と `DataRowView` のイベントだけです。  式列には他の複数の列に対する依存関係が存在することもあるため、1 回の `DataRow` 操作で複数回、評価される場合もあります。  イベントは式が評価されるたびに発生するため、式列が変更された場合、1 回の `DataRow` 操作で複数の `ListChanged` イベントおよび `PropertyChanged` イベントが発生し、同じ式列に対して複数のイベントが発生する場合もあります。  
  
> [!WARNING]
>  <xref:System.NullReferenceException> を `RowChanged` イベント ハンドラー内でスローしないでください。  <xref:System.NullReferenceException> が `DataTable` の `RowChanged` イベント内でスローされると、`DataTable` が破損します。  
  
### 例  
 次の例では、`RowChanged`、`RowChanging`、`RowDeleted`、`RowDeleting`、`ColumnChanged`、`ColumnChanging`、`TableNewRow`、`TableCleared`、`TableClearing` の各イベントについてイベント ハンドラーを作成しています。  イベントが発生すると、各イベント ハンドラーによって、出力結果がコンソール ウィンドウに表示されます。  
  
 [!code-csharp[DataWorks DataTable.Events#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.Events/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.Events#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.Events/VB/source.vb#1)]  
  
## 参照  
 [DataTable 内のデータの操作](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)   
 [DataAdapter のイベント処理](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md)   
 [DataSet のイベント処理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)