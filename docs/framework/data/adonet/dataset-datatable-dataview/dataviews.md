---
title: "DataViews | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataViews
<xref:System.Data.DataView> では、<xref:System.Data.DataTable> に格納されているデータのさまざまなビューを作成できます。この機能は、データ連結アプリケーションで頻繁に使用されます。  **DataView** を使用すると、さまざまな並べ替え順序を使用してテーブルのデータを公開したり、行の状態やフィルター式に基づいてデータをフィルター処理したりできます。  
  
 **DataView** では、基になる **DataTable** のデータの動的ビューが作成されます。ビューの内容、順序、メンバーシップには、変更が反映されます。  これは、**DataTable** の **Select** メソッドとは異なります。このメソッドでは、特定のフィルターまたは並べ替え順序ごとにテーブルから <xref:System.Data.DataRow> 配列が戻されます。戻される配列の内容には、基になるテーブルの変更内容が反映されていますが、メンバーシップと順序は静的です。  **DataView** は動的機能を備えているため、データ連結アプリケーションにとって理想的なオブジェクトです。  
  
 **DataView** は、1 つのデータ セットの動的ビューです。データベースのビューと同様に、この動的ビューには、さまざまな並べ替え順序やフィルター処理条件を適用できます。  ただし、データベース ビューとは異なり、**DataView** は、テーブルとしては処理できず、結合テーブルのビューも作成できません。  また、ソース テーブルの既存の列を除外したり、ソース テーブルにない列 \(計算列など\) を追加することはできません。  
  
 **DataSet** のすべてのテーブルのビュー設定を管理するには、<xref:System.Data.DataView.DataViewManager%2A> を使用します。  **DataViewManager** を使用すると、各テーブルの既定のビュー設定を簡単に管理できます。  **DataSet** の複数のテーブルにコントロールを連結する最適な方法は、**DataViewManager** に連結する方法です。  
  
## このセクションの内容  
 [DataView の作成](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataview.md)  
 **DataTable** の **DataView** の作成方法について説明します。  
  
 [データの並べ替えとフィルター処理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 特定のフィルター条件を満たすデータ行のサブセットを返すか、または特定の並べ替え順序でデータを返すように **DataView** のプロパティを設定する方法について説明します。  
  
 [DataRow および DataRowView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarows-and-datarowviews.md)  
 **DataView** によって公開されるデータへのアクセス方法について説明します。  
  
 [行の検索](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)  
 **DataView** での特定の行の検索方法について説明します。  
  
 [ChildView とリレーション](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/childviews-and-relations.md)  
 **DataView** を使用して親子のリレーションシップからデータ ビューを作成する方法について説明します。  
  
 [DataView の変更](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/modifying-dataviews.md)  
 **DataView** を使用して、基になる **DataTable** のデータを変更する方法について説明します。また、更新の有効化と無効化についても説明します。  
  
 [DataView イベントの処理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataview-events.md)  
 **DataView** の内容または順序が更新されるときに、**ListChanged** イベントを使用して通知を受信する方法について説明します。  
  
 [DataViews の管理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/managing-dataviews.md)  
 **DataViewManager** を使用して **DataSet** の各テーブルの **DataView** 設定を管理する方法について説明します。  
  
## 関連項目  
 [ASP.NET Web Applications](http://msdn.microsoft.com/ja-jp/a812d7b7-049e-4234-a4c2-6acf690301f6)  
 ASP.NET アプリケーション、Web フォームおよび Web サービスを作成する場合の概要と詳細なステップごとの手順を示します。  
  
 [Windows Applications](http://msdn.microsoft.com/ja-jp/a6bb2180-09b1-4738-b9fd-7fb05fc92f23)  
 Windows フォームおよびコンソール アプリケーションの操作に関する詳細情報を提供します。  
  
 [DataSets、DataTables、および DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 **DataSet** オブジェクトについて説明し、**DataSet** オブジェクトを使用してアプリケーション データを管理する方法も示します。  
  
 [DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 **DataTable** オブジェクトについて説明し、アプリケーション データを単独でまたは **DataSet** の一部として管理するために **DataTable** オブジェクトを使用する方法も示します。  
  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 ADO.NET のアーキテクチャとコンポーネントについて説明し、ADO.NET を使用して既存のデータ ソースにアクセスしたり、アプリケーション データを管理する方法について説明します。  
  
## 参照  
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)