---
title: "Querying DataSets (LINQ to DataSet) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Querying DataSets (LINQ to DataSet)
<xref:System.Data.DataSet> オブジェクトへのデータの読み込みが完了すると、そのデータセットに対してクエリを実行できるようになります。  [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] を使ったクエリの作成方法は、他の [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 対応データ ソースに対して [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] を使用する方法と似ています。  ただし、<xref:System.Data.DataSet> オブジェクトに対して [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] クエリを実行する場合、カスタム型の列挙体ではなく、<xref:System.Data.DataRow> オブジェクトの列挙体を照会しているという点に留意してください。  つまり、[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] クエリでは、<xref:System.Data.DataRow> クラスの任意のメンバーを使用できるということです。  これにより、高度で複雑なクエリの作成が可能となります。  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] クエリには、[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] の他の実装と同様、クエリ式の構文とメソッド ベースのクエリ構文という 2 とおりの作成形式があります。  この 2 つの形式の詳細については、「[Getting Started with LINQ](http://msdn.microsoft.com/ja-jp/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9)」を参照してください。クエリ式の構文またはメソッド ベースのクエリ構文を使用して、<xref:System.Data.DataSet> 内の単一テーブル、<xref:System.Data.DataSet> 内の複数テーブル、または、型指定された <xref:System.Data.DataSet> 内のテーブルを対象にクエリを実行できます。  
  
## このセクションの内容  
 [Single\-Table Queries](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 単一テーブルのクエリを実行する方法について説明します。  
  
 [Cross\-Table Queries](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 複数テーブルにまたがるクエリを実行する方法について説明します。  
  
 [Querying Typed DataSets](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 型指定された <xref:System.Data.DataSet> オブジェクトに対してクエリを実行する方法について説明します。  
  
## 参照  
 [LINQ to DataSet Examples](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)   
 [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)