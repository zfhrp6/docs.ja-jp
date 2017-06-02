---
title: "型指定された DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 型指定された DataSet
厳密に型指定されていない変数を使用した値への遅延バインディング アクセスに加えて、<xref:System.Data.DataSet> には、厳密に型指定された変数を使用したデータへのアクセスも用意されています。  **DataSet** の一部であるテーブルと列は、ユーザーが認識しやすい名前と厳密に型指定された変数を使用してアクセスできます。  
  
 型指定された **DataSet** とは、**DataSet** から派生するクラスのことです。  したがって、型指定された **DataSet** は **DataSet** のすべてのメソッド、イベント、およびプロパティを継承します。  さらに、型指定された **DataSet** には、厳密に型指定されたメソッド、イベント、およびプロパティが用意されています。  つまり、コレクションベースのメソッドを使用せずに名前でテーブルおよび列にアクセスできます。  コードが読みやすく変更されただけでなく、型指定された **DataSet** を使用して、入力するとおりにラインを Visual Studio .NET コード エディターに自動挿入できます。  
  
 さらに、厳密に型指定された **DataSet** を使用してコンパイル時に正しい型で値にアクセスできます。  厳密に型指定された **DataSet** を使用すると、型の不一致が実行時ではなく、コードのコンパイル時にキャッチされます。  
  
## このセクションの内容  
 [厳密に型指定された DataSet の生成](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-strongly-typed-datasets.md)  
 厳密に型指定された **DataSet** の作成および使用方法について説明します。  
  
 [型指定された DataSet の注釈](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/annotating-typed-datasets.md)  
 基になるスキーマを変更せずに **DataSet** の要素に表示名を付けるために、厳密に型指定された **DataSet** の生成に使用する XML スキーマ定義言語 \(XSD\) スキーマに注釈を付ける方法について説明します。  
  
## 参照  
 [DataSets、DataTables、および DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)