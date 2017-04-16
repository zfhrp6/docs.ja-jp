---
title: "LINQ と ADO.NET | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# LINQ と ADO.NET
今日、ビジネス アプリケーション開発者の多くは、2 つ \(またはそれ以上\) のプログラミング言語を使ってアプリケーションを開発しています。ビジネス ロジックやプレゼンテーション層には高級言語 \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] など\) が、データベースとの対話にはクエリ言語 \([!INCLUDE[tsql](../../../../includes/tsql-md.md)] など\) が使用されています。  開発者は実質的に複数の言語に精通していることが要求され、開発環境における言語の不整合が生じる原因にもなっています。  たとえば、データ アクセス API を使用してデータベースを照会するアプリケーションでは、クエリは文字列リテラルとして引用符で囲んで指定する必要があります。  コンパイラはこのクエリ文字列を認識できないため、エラー \(無効な構文、参照されている列または行が実際に存在するかどうかなど\) のチェック機構が働きません。  クエリ パラメーターの型チェックや `IntelliSense` のサポートもありません。  
  
 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] により、開発者はアプリケーション コード内でプログラミング言語とクエリ言語を使い分けることなく、セット ベースのクエリを作成できます。  インメモリのデータ構造、XML ドキュメント、SQL データベース、<xref:System.Data.DataSet> オブジェクトなど、列挙可能な各種データ ソース \(つまり、<xref:System.Collections.IEnumerable> インターフェイスを実装するデータ ソース\) に対する [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] クエリを作成できます。  実装方法には違いがありますが、こうした列挙可能なデータ ソースはすべて同じ構文および言語構造を公開しています。  クエリはプログラミング言語のみで作成できるため、コンパイラによる認識も検証もできない文字列リテラルとしてクエリ言語を記述する必要はありません。  クエリをプログラミング言語に統合することにより、コンパイル時の型チェックや構文チェック、`IntelliSense` の使用などが可能となるため、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] プログラマは生産性を高めることができます。  クエリのデバッグやエラーの修正に伴う手間は、これらの機能によって軽減されます。  
  
 SQL テーブルのデータをメモリ内のオブジェクトに転送することは、面倒であるだけでなく間違いの元にもなります。  [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] および [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] で実装された [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] プロバイダーは、ソース データを <xref:System.Collections.IEnumerable> ベースのオブジェクト コレクションに変換します。  プログラマからは、クエリの実行時も更新時も常にデータが <xref:System.Collections.IEnumerable> コレクションとして見えます。  これらのコレクションに対するクエリを記述する際には、`IntelliSense` の機能を完全に利用できます。  
  
 ADO.NET [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] には、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]、[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]、および [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)] の 3 つのテクノロジがあります。  [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] は、<xref:System.Data.DataSet> に対する高度で最適化されたクエリの実行を可能にします。一方、[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] は、[!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] データベース スキーマに対して直接クエリを実行できるようにします。また、[!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)] は、[!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] をクエリできるようにします。  
  
 次の図は、ADO.NET LINQ テクノロジが、高級プログラミング言語および LINQ 対応のデータ ソースとどのように関係しているかを簡単に表したものです。  
  
 ![LINQ to ADO.NET の概要](../../../../docs/framework/data/adonet/media/dpue-linqtoadonetoverview-bpuedev11.png "DPUE\_LinqToAdoNetOverview\_bpuedev11")  
  
 LINQ 言語機能に関する全般的な情報については、「[Introduction to LINQ](../../../../ocs/visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)」を参照してください。  アプリケーションで LINQ を使用する方法については、「[NOT IN BUILD: LINQ General Programming Guide](http://msdn.microsoft.com/ja-jp/609c7a6b-cbdd-429d-99f3-78d13d3bc049)」を参照してください。このガイドには、LINQ テクノロジの使用方法に関する詳細が記述されています。  
  
 以降のセクションで、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]、[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]、および [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)] について詳しく説明します。  
  
## LINQ to DataSet  
 <xref:System.Data.DataSet> は、[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] の基礎である非接続型プログラミング モデルの重要な要素であり幅広く使用されています。  [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] により、開発者は、他の多くのデータ ソースで利用できる共通のクエリ作成メカニズムを使用しながら、より高度なクエリ機能を <xref:System.Data.DataSet> に組み込むことができます。  詳細については、「[LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md)」を参照してください。  
  
## LINQ to SQL  
 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] は、概念モデルへのマッピングを必要としない開発者にとって有用なツールです。  [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] では、[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] プログラミング モデルを既存のデータベース スキーマ上で直接利用できるようになります。  開発者は、データを表現する [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] クラスを、[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] を使って生成できます。  こうして生成されたクラスは、概念データ モデルではなく、直接データベースのテーブル、ビュー、ストアド プロシージャ、およびユーザー定義関数にマッピングされます。  
  
 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] では、開発者が、XML などのデータ ソースに加え、インメモリ コレクションや <xref:System.Data.DataSet> と同じ [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] プログラミング パターンを使用して、ストレージ スキーマに対して直接コードを記述できます。  詳細については、「[LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)」を参照してください。  
  
## LINQ to Entities  
 現在、多くのアプリケーションが、リレーショナル データベースを基にして作成されています。  ある時点で、これらのアプリケーションにはリレーショナル形式で表されるデータと対話する必要が生じます。  データベース スキーマはアプリケーションの構築に理想的であるとは限らず、アプリケーションの概念モデルはデータベースの論理モデルと同じではありません。  [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)]は、アプリケーションがデータをオブジェクトとして操作するために特定のドメインのデータをモデル化するときに使用できる概念データ モデルです。  詳細については、「[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)」を参照してください。  
  
 [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)]を介して、リレーショナル データは .NET 環境でオブジェクトとして公開されます。  これにより、[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] の利用に最適なオブジェクト レイヤーが実現されます。開発者は、ビジネス ロジックの構築に使用する言語で、データベースを照会するクエリを作成できます。  この機能は、[!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)] と呼ばれます。  詳細については、「[LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)」を参照してください。  
  
## 参照  
 [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md)   
 [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)   
 [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)   
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)