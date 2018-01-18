---
title: DataTables
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 439b951779393d6ac232e6a1a622515905e837ad
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="datatables"></a>DataTables
<xref:System.Data.DataSet> は、テーブル、リレーションシップ、および制約のコレクションで構成されます。 ADO.NET では、<xref:System.Data.DataTable>内のテーブルを表すオブジェクトを使用する**データセット**です。 A **DataTable**のインメモリ リレーショナル データの 1 つのテーブルを表すデータがローカルに、します。NET ベースのアプリケーションをそれが存在するが、Microsoft SQL Server を使用するなどのデータ ソースからデータを読み込むことができます、 **DataAdapter**詳細については、次を参照してください[DataAdapter からの DataSet の読み込み](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md).  
  
 **DataTable**クラスのメンバーである、 **System.Data** .NET Framework クラス ライブラリ内で名前空間。 作成して使用することができます、 **DataTable**とは独立してまたはのメンバーとして、**データセット**、および**DataTable**オブジェクトは、他の .NET Framework のオブジェクトと組み合わせても使用できます含む、<xref:System.Data.DataView>です。 コレクション内のテーブルにアクセスする、**データセット**を通じて、**テーブル**のプロパティ、**データセット**オブジェクト。  
  
 テーブルのスキーマ (構造) は、列と制約で表されます。 スキーマを定義する、 **DataTable**を使用して<xref:System.Data.DataColumn>オブジェクトだけでなく<xref:System.Data.ForeignKeyConstraint>と<xref:System.Data.UniqueConstraint>オブジェクト。 テーブルの列は、データ ソースの列に割り当てたり、式で算出された値を格納したり、格納されている値を自動的にインクリメントしたり、主キー値を格納したりできます。  
  
 スキーマだけでなく、 **DataTable**行が含まれており、データを注文する必要があります。 <xref:System.Data.DataRow> クラスは、テーブルに格納される実際のデータを表します。 使用する、 **DataRow**し、そのプロパティおよびメソッドを取得するには、評価、およびテーブル内のデータを操作します。 アクセスし、行のデータを変更すると、 **DataRow**オブジェクトは、両方の現在と元の状態を保持します。  
  
 テーブル間で 1 つ以上の列を関連付け、テーブル間の親子のリレーションシップを作成できます。 間のリレーションシップを作成する**DataTable**オブジェクトを使用して、<xref:System.Data.DataRelation>です。 **DataRelation**オブジェクトは、特定の行の関連する子または親の行を返すし、使用できます。 詳細については、次を参照してください。 [Datarelation の追加](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [DataTable の作成](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datatable.md)  
 作成する方法について説明します、 **DataTable**に追加し、**データセット**です。  
  
 [DataTable スキーマの定義](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 作成と使用に関する情報を提供**DataColumn**オブジェクトと制約。  
  
 [DataTable 内のデータの操作](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 テーブル内のデータを追加、変更、および削除する方法について説明します。 使用する方法について説明します**DataTable**を調べるテーブル内のデータへの変更イベント。  
  
 [DataTable イベントの処理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 使用するために使用できるイベントに関する情報を提供する**DataTable**列の値が変更され、行を追加または削除されたときにイベントを含むです。  
  
## <a name="related-sections"></a>関連項目  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 ADO.NET のアーキテクチャとコンポーネントについて説明し、ADO.NET を使用して既存のデータ ソースにアクセスしたり、アプリケーション データを管理する方法について説明します。  
  
 [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 ADO.NET に関する情報を提供**データセット**テーブル間のリレーションシップを作成する方法などです。  
  
 <xref:System.Data.Constraint>  
 参照情報を提供、**制約**オブジェクト。  
  
 <xref:System.Data.DataColumn>  
 参照情報を提供、 **DataColumn**オブジェクト。  
  
 <xref:System.Data.DataSet>  
 参照情報を提供、**データセット**オブジェクト。  
  
 <xref:System.Data.DataTable>  
 参照情報を提供、 **DataTable**オブジェクト。  
  
 [クラス ライブラリの概要](../../../../../docs/standard/class-library-overview.md)  
 .NET Framework クラス ライブラリの概要を説明を含む、**システム**名前空間、第 2 レベルの名前空間だけでなく**System.Data**です。  
  
## <a name="see-also"></a>参照  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
