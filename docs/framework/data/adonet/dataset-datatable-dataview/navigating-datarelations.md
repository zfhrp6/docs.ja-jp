---
title: "DataRelation の移動"
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
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5b90b58595c86fc3c4dcaf7fd453c517d6f14904
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="navigating-datarelations"></a>DataRelation の移動
<xref:System.Data.DataRelation> の主な機能の 1 つは、<xref:System.Data.DataTable> の 1 つの <xref:System.Data.DataSet> から別の  を移動できることです。 すべてを取得できます、関連する<xref:System.Data.DataRow>いずれかのオブジェクト**DataTable** 、1 つを指定すると**DataRow**関連から**DataTable**です。 確立した後など、 **DataRelation**を使用して特定の顧客行のすべての注文行を取得するテーブルと顧客の注文のテーブル、 **GetChildRows**です。  
  
 次のコード例を作成、 **DataRelation**間、**顧客**テーブルおよび**Orders**のテーブル、**データセット**を返します各顧客のすべての注文します。  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 上記の例に基づいて、4 つのテーブルを相互に関連付け、そのテーブルのリレーションシップ間を移動する例を次に示します。 前の例のように**CustomerID**関連、**顧客**テーブル、 **Orders**テーブル。 顧客ごとに、**顧客**テーブル内のすべての子行、 **Orders** 、特定の顧客が注文の数を返すために、テーブルが決定され、その**OrderID**値。  
  
 展開された例もから値を返します、 **OrderDetails**と**製品**テーブル。 **Orders**に関連するテーブル、 **OrderDetails**テーブルを使用して**OrderID**調べるには、各顧客の注文、製品と数量を注文しました。 **OrderDetails**テーブルのみを含む、 **ProductID** 、オーダーされた製品の**OrderDetails**に関連する**製品**使用して**ProductID**を返すために、 **ProductName**です。 このリレーションシップで、**製品**テーブルが親と**Order Details**テーブルが子。 その結果、反復処理時、 **OrderDetails**テーブル、 **GetParentRow**取得、関連するために呼び出される**ProductName**値。  
  
 場合に、 **DataRelation**の作成、**顧客**と**Orders**テーブル、値が指定されていない、 **createConstraints**フラグ (既定値は**true**)。 これが想定されるすべての行、 **Orders**テーブルが、 **CustomerID**親内に存在する値**顧客**テーブル。 場合、 **CustomerID**内に存在する、 **Orders**テーブルに存在しない、**顧客**、テーブル、<xref:System.Data.ForeignKeyConstraint>例外がスローされます。  
  
 子の列には、親の列を含まない値が含まれている可能性がある場合の設定、 **createConstraints**フラグを**false**を追加するとき、 **DataRelation**です。 例では、 **createConstraints**にフラグが設定されている**false**の**DataRelation**間、 **Orders**テーブルと、 **OrderDetails**テーブル。 これにより、アプリケーションからのすべてのレコードを返す、 **OrderDetails**テーブルとのレコードのサブセットのみ、 **Orders**せず、実行時に例外を生成するテーブル。 展開された例では、次の形式で出力が生成されます。  
  
```  
Customer ID: NORTS  
  Order ID: 10517  
        Order Date: 4/24/1997 12:00:00 AM  
           Product: Filo Mix  
          Quantity: 6  
           Product: Raclette Courdavault  
          Quantity: 4  
           Product: Outback Lager  
          Quantity: 6  
  Order ID: 11057  
        Order Date: 4/29/1998 12:00:00 AM  
           Product: Outback Lager  
          Quantity: 3  
```  
  
 次のコード例は、展開された例をどこからの値、 **OrderDetails**と**製品**内のレコードのサブセットのみを含むテーブルが返されます、 **Orders**返されるテーブル。  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
