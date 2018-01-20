---
title: DataView
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5b79461a6fc3314ca4178e0f9b1cff1c468cc3e6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="dataviews"></a>DataView
<xref:System.Data.DataView> では、<xref:System.Data.DataTable> に格納されているデータのさまざまなビューを作成できます。この機能は、データ連結アプリケーションで頻繁に使用されます。 使用して、 **DataView**さまざまな並べ替え順序、テーブル内のデータを公開することができます、および行の状態やフィルター式に基づいて、データをフィルター処理できます。  
  
 A **DataView** 、基になるデータの動的なビューを提供**DataTable**: 内容、順序、およびメンバーシップ発生すると、変更を反映します。 この動作は異なります、**選択**のメソッド、 **DataTable**を返す、<xref:System.Data.DataRow>特定のフィルター処理や並べ替え順序に基づいて、テーブルから配列: thiscontent への変更を反映して、テーブルが、メンバーシップを基になると、順序付けは、静的なままです。 動的機能、 **DataView**データ連結アプリケーションに最適です。  
  
 A **DataView**では、別の並べ替えやフィルター処理条件を適用できますデータベース ビューの場合と同様に、データの単一セットの動的な表示します。 ただし、データベース ビューとは異なり、 **DataView**テーブルとして扱うことはできませんし、結合テーブルのビューを提供することはできません。 また、ソース テーブルの既存の列を除外したり、ソース テーブルにない列 (計算列など) を追加することはできません。  
  
 使用することができます、<xref:System.Data.DataView.DataViewManager%2A>内のすべてのテーブルの表示設定を管理する、**データセット**です。 **DataViewManager**テーブルごとに既定の表示設定を管理する便利な手段を提供します。 2 つ以上のテーブルにコントロールをバインドするときに、**データセット**に連結する、 **DataViewManager**理想的なソリューションです。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [DataView の作成](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataview.md)  
 作成する方法について説明します、 **DataView**の**DataTable**です。  
  
 [データの並べ替えとフィルター処理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 プロパティを設定する方法について説明、 **DataView**のサブセットを返すデータ行の特定のフィルター条件を満たす、または特定の並べ替え順序でデータを返します。  
  
 [DataRow および DataRowView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarows-and-datarowviews.md)  
 によって公開されるデータにアクセスする方法について説明します、 **DataView**です。  
  
 [行の検索](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)  
 特定の行を検索する方法について説明、 **DataView**です。  
  
 [ChildView とリレーション](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/childviews-and-relations.md)  
 使用して、親子関係からのデータのビューを作成する方法について説明、 **DataView**です。  
  
 [DataView の変更](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/modifying-dataviews.md)  
 基になるデータを変更する方法について説明**DataTable**を介して、 **DataView**、有効化と更新プログラムを無効にするとします。  
  
 [DataView イベントの処理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataview-events.md)  
 使用する方法について説明します、 **ListChanged**イベント通知を受信するときの内容または順序、 **DataView**を更新しています。  
  
 [DataViews の管理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/managing-dataviews.md)  
 使用する方法について説明します、 **DataViewManager**を管理する**DataView**内の各テーブルの設定、**データセット**です。  
  
## <a name="related-sections"></a>関連項目  
 [ASP.NET Web アプリケーション](http://msdn.microsoft.com/library/a812d7b7-049e-4234-a4c2-6acf690301f6)  
 ASP.NET アプリケーション、Web フォームおよび Web サービスを作成する場合の概要と詳細なステップごとの手順を示します。  
  
 [Windows アプリケーション](http://msdn.microsoft.com/library/a6bb2180-09b1-4738-b9fd-7fb05fc92f23)  
 Windows フォームおよびコンソール アプリケーションの操作に関する詳細情報を提供します。  
  
 [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 について説明します、**データセット**オブジェクトとアプリケーション データの管理を使用する方法です。  
  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 について説明します、 **DataTable**オブジェクトとデータを管理するアプリケーションの一部としてまたは単独で使用する方法、**データセット**です。  
  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 ADO.NET のアーキテクチャとコンポーネントについて説明し、ADO.NET を使用して既存のデータ ソースにアクセスしたり、アプリケーション データを管理する方法について説明します。  
  
## <a name="see-also"></a>参照  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
