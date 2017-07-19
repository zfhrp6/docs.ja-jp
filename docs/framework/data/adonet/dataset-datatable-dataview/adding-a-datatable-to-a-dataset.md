---
title: "DataSet への DataTable の追加 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 556d29a3-8fc9-4e38-b3ee-c188f7e7b155
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataSet への DataTable の追加
ADO.NET を使用して <xref:System.Data.DataTable> オブジェクトを作成し、そのオブジェクトを既存の <xref:System.Data.DataSet> に追加できます。  <xref:System.Data.DataTable.PrimaryKey%2A> プロパティと <xref:System.Data.DataColumn.Unique%2A> プロパティを使用することで、<xref:System.Data.DataTable> の制約情報を設定できます。  
  
## 例  
 <xref:System.Data.DataSet> を構築し、<xref:System.Data.DataSet> に新しい <xref:System.Data.DataTable> オブジェクトを追加してから、3 つの <xref:System.Data.DataColumn> オブジェクトをそのテーブルに追加する例を次に示します。  コードの最後では、1 つの列が主キーの列として設定されています。  
  
 [!code-csharp[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/VB/source.vb#1)]  
  
## 大文字と小文字の区別  
 大文字と小文字の区別が異なれば、<xref:System.Data.DataSet> に存在する 2 つ以上のテーブルまたはリレーションが同じ名前を持つことができます。  この場合、名前を使用してテーブルとリレーションを参照する際に大文字と小文字が区別されます。  たとえば、<xref:System.Data.DataSet> **dataSet** に **Table1** と **table1** のテーブルがある場合、**Table1** を参照するには **dataSet.Tables\["Table1"\]**、**table1** を参照するには **dataSet.Tables \["table1"\]** と名前を指定します。  このいずれかのテーブルの参照に **dataSet.Tables \["TABLE1"\]** と指定すると、例外が発生します。  
  
 特定の名前を持つテーブルまたはリレーションが 1 つのみの場合、大文字と小文字は区別されません。  たとえば、<xref:System.Data.DataSet> に **Table1** しか存在しない場合は、**dataSet.Tables\["TABLE1"\]** を使用してそのテーブルを参照できます。  
  
> [!NOTE]
>  この動作は <xref:System.Data.DataSet> の <xref:System.Data.DataSet.CaseSensitive%2A> プロパティの影響を受けません。  <xref:System.Data.DataSet.CaseSensitive%2A> プロパティは、<xref:System.Data.DataSet> 内のデータに適用され、並べ替え、検索、フィルター処理、制約の適用などに影響を及ぼします。  
  
## 名前空間のサポート  
 2.0 より前のバージョンの ADO.NET では、異なる名前空間に存在しているテーブルであっても、2 つのテーブルが同じ名前を持つことはできませんでした。  ADO.NET 2.0 には、この制限はありません。  したがって、<xref:System.Data.DataSet> に、<xref:System.Data.DataTable.Namespace%2A> プロパティ値が異なり、<xref:System.Data.DataTable.TableName%2A> プロパティ値が一致する 2 つのテーブルが存在しても問題ありません。  
  
## 参照  
 [DataSets、DataTables、および DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)