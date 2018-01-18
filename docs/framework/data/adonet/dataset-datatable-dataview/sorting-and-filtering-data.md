---
title: "データの並べ替えとフィルター処理"
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
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2411307623c714ae521d00dcffca05d3569a656e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="sorting-and-filtering-data"></a>データの並べ替えとフィルター処理
<xref:System.Data.DataView> には、<xref:System.Data.DataTable> のデータの並べ替えとフィルター処理を行うさまざまな方法が用意されています。  
  
-   <xref:System.Data.DataView.Sort%2A> プロパティを使用すれば、1 列または複数列の並べ替え順序を指定し、ASC (昇順) パラメーターと DESC (降順) パラメーターを含めることができます。  
  
-   <xref:System.Data.DataView.ApplyDefaultSort%2A> プロパティを使用すると、テーブルの主キー列 (1 列または複数列) に基づいて、昇順の並べ替え順序を自動的に作成できます。 <xref:System.Data.DataView.ApplyDefaultSort%2A>場合のみ適用されます、**並べ替え**プロパティが null 参照または空の文字列には、テーブルで定義された主キーが場合。  
  
-   <xref:System.Data.DataView.RowFilter%2A> プロパティを使用すると、列の値に基づいて行のサブセットを指定できます。 有効な式の詳細について、 **RowFilter**プロパティに関するリファレンス情報を参照してください、<xref:System.Data.DataColumn.Expression%2A>のプロパティ、<xref:System.Data.DataColumn>クラスです。  
  
     取得、データのサブセットの動的なビューではなく、データに対する特定のクエリの結果を使用する場合、<xref:System.Data.DataView.Find%2A>または<xref:System.Data.DataView.FindRows%2A>のメソッド、 **DataView**最高のパフォーマンスを実現するためになく設定、 **RowFilter**プロパティです。 設定、 **RowFilter**プロパティは、アプリケーションにオーバーヘッドを追加して、パフォーマンスが低下、データのインデックスを再構築します。 **RowFilter**プロパティは最適使用、データ連結アプリケーションでバインドされたコントロールがフィルター選択された結果が表示されます。 **検索**と**FindRows**メソッドが再構築するインデックスを必要とせず、現在のインデックスを活用します。 詳細については、**検索**と**FindRows**メソッドを参照してください[を検索する行](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)です。  
  
-   <xref:System.Data.DataView.RowStateFilter%2A> プロパティを使用して、表示する行バージョンを指定できます。 **DataView**に応じてを公開する行バージョンを暗黙的に管理、 **RowState**の基になる行のです。 たとえば場合、 **RowStateFilter**に設定されている**DataViewRowState.Deleted**、 **DataView**公開、**元**行バージョンのすべて**Deleted**行があるためありません**現在**行バージョン。 使用して公開される行の行バージョンを指定できます、 **RowVersion**のプロパティ、 **DataRowView**です。  
  
     次の表は、オプションの**DataViewRowState**です。  
  
    |DataViewRowState のオプション|説明|  
    |------------------------------|-----------------|  
    |**CurrentRows**|**現在**行バージョンのすべて**Unchanged**、 **Added**、および**Modified**行です。 既定値です。|  
    |**追加**|**現在**行バージョンのすべて**Added**行です。|  
    |**削除**|**元**行バージョンのすべて**Deleted**行です。|  
    |**ModifiedCurrent**|**現在**行バージョンのすべて**Modified**行です。|  
    |**ModifiedOriginal**|**元**行バージョンのすべて**Modified**行です。|  
    |**None**|行がありません。|  
    |**OriginalRows**|**元**行バージョンのすべて**Unchanged**、 **Modified**、および**Deleted**行です。|  
    |**Unchanged**|**現在**行バージョンのすべて**Unchanged**行です。|  
  
 行の状態と行のバージョンの詳細については、次を参照してください。[行の状態と行のバージョン](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)します。  
  
 在庫数が標準在庫数以下である製品を、仕入先 ID (supplier ID) で並べ替え、さらに製品名 (product name) で並べ替えたビューを作成するコード サンプルを次に示します。  
  
```vb  
Dim prodView As DataView = New DataView(prodDS.Tables("Products"), _  
   "UnitsInStock <= ReorderLevel", _  
   "SupplierID, ProductName", _  
   DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView prodView = new DataView(prodDS.Tables["Products"],  
   "UnitsInStock <= ReorderLevel",  
   "SupplierID, ProductName",  
   DataViewRowState.CurrentRows);  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.Data.DataViewRowState>  
 <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
