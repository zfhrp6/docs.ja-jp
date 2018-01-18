---
title: "DataSet のクエリ (LINQ to DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c9830587e70d7671200fac20c8384f1a470a751e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="querying-datasets-linq-to-dataset"></a>DataSet のクエリ (LINQ to DataSet)
<xref:System.Data.DataSet> オブジェクトへのデータの読み込みが完了すると、そのデータセットに対してクエリを実行できるようになります。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] を使ったクエリの作成方法は、他の [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] 対応データ ソースに対して [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] を使用する方法と似ています。 ただしを使用すると[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]経由でクエリを実行、<xref:System.Data.DataSet>オブジェクトの列挙クエリを実行する<xref:System.Data.DataRow>カスタム型の列挙体ではなく、オブジェクトです。 つまりのメンバーのいずれかを使用できます、<xref:System.Data.DataRow>クラス内で、[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]クエリ。 これにより、高度で複雑なクエリの作成が可能となります。  
  
 その他の実装と同様[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]、作成することができます[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]2 つの異なる形式でのクエリ: クエリ式の構文とメソッド ベースのクエリ構文です。 これら 2 つの形式の詳細については、次を参照してください。 [LINQ の概要](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9)です。 クエリ式の構文またはメソッド ベースのクエリ構文を使用して、<xref:System.Data.DataSet> 内の単一テーブル、<xref:System.Data.DataSet> 内の複数テーブル、または、型指定された <xref:System.Data.DataSet> 内のテーブルを対象にクエリを実行できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [単一テーブルのクエリ](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 単一テーブルのクエリを実行する方法について説明します。  
  
 [複数テーブルにまたがるクエリ](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 複数テーブルにまたがるクエリを実行する方法について説明します。  
  
 [型指定された DataSet のクエリ](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 型指定された <xref:System.Data.DataSet> オブジェクトに対してクエリを実行する方法について説明します。  
  
## <a name="see-also"></a>参照  
 [LINQ to DataSet の例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [DataSet へのデータの読み込み](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
