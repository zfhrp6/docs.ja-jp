---
title: "DataSet への DataTable の追加"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 556d29a3-8fc9-4e38-b3ee-c188f7e7b155
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: c5846f93cfa75d7f0e760a24ee65fa838abc1eb8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="adding-a-datatable-to-a-dataset"></a>DataSet への DataTable の追加
ADO.NET を使用して <xref:System.Data.DataTable> オブジェクトを作成し、そのオブジェクトを既存の <xref:System.Data.DataSet> に追加できます。 <xref:System.Data.DataTable> プロパティと <xref:System.Data.DataTable.PrimaryKey%2A> プロパティを使用することで、<xref:System.Data.DataColumn.Unique%2A> の制約情報を設定できます。  
  
## <a name="example"></a>例  
 <xref:System.Data.DataSet> を構築し、<xref:System.Data.DataTable> に新しい <xref:System.Data.DataSet> オブジェクトを追加してから、3 つの <xref:System.Data.DataColumn> オブジェクトをそのテーブルに追加する例を次に示します。 コードの最後では、1 つの列が主キーの列として設定されています。  
  
 [!code-csharp[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/VB/source.vb#1)]  
  
## <a name="case-sensitivity"></a>大文字と小文字の区別  
 大文字と小文字の区別が異なれば、<xref:System.Data.DataSet> に存在する 2 つ以上のテーブルまたはリレーションが同じ名前を持つことができます。 この場合、名前を使用してテーブルとリレーションを参照する際に大文字と小文字が区別されます。 たとえば場合、 <xref:System.Data.DataSet> **データセット**テーブルを含む**Table1**と**table1**を参照する**Table1**と名前**dataSet.Tables["Table1"]**、および**table1**として**dataSet.Tables["table1"]**です。 テーブルのいずれかを参照しようとして**dataSet.Tables["TABLE1"]**例外が生成されます。  
  
 特定の名前を持つテーブルまたはリレーションが 1 つのみの場合、大文字と小文字は区別されません。 たとえば場合、<xref:System.Data.DataSet>のみが**Table1**を使用してそれを参照することができます**dataSet.Tables["TABLE1"]**です。  
  
> [!NOTE]
>  この動作は <xref:System.Data.DataSet.CaseSensitive%2A> の <xref:System.Data.DataSet> プロパティの影響を受けません。 <xref:System.Data.DataSet.CaseSensitive%2A> プロパティは、<xref:System.Data.DataSet> 内のデータに適用され、並べ替え、検索、フィルター処理、制約の適用などに影響を及ぼします。  
  
## <a name="namespace-support"></a>名前空間のサポート  
 2.0 より前のバージョンの ADO.NET では、異なる名前空間に存在しているテーブルであっても、2 つのテーブルが同じ名前を持つことはできませんでした。 ADO.NET 2.0 には、この制限はありません。 したがって、<xref:System.Data.DataSet> に、<xref:System.Data.DataTable.TableName%2A> プロパティ値が異なり、<xref:System.Data.DataTable.Namespace%2A> プロパティ値が一致する 2 つのテーブルが存在しても問題ありません。  
  
## <a name="see-also"></a>参照  
 [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
