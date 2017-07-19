---
title: "LINQ to SQL | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] Version 3.5 のコンポーネントであり、リレーショナル データをオブジェクトとして管理するためのランタイム インフラストラクチャを提供します。  
  
> [!NOTE]
>  リレーショナル データは 2 次元テーブル \(*リレーション*または*フラット ファイル*\) のコレクションで表され、共通の列がテーブルを相互に関連付けます。  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を効果的に使用するには、リレーショナル データベースの基本原則を理解している必要があります。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、リレーショナル データベースのデータ モデルが、開発者のプログラミング言語で表されるオブジェクト モデルに対応付けられています。  アプリケーションが実行されると、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、オブジェクト モデルの統合言語クエリを SQL に変換し、それをデータベースに送信して実行します。データベースから結果が返されると、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] はそれをプログラミング言語で操作できるオブジェクトに変換し直します。  
  
 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] を使用する開発者は、通常、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]を使用します。これには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の機能の多くを実装するためのユーザー インターフェイスが用意されています。  
  
 このリリースの [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] に含まれているドキュメントでは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アプリケーションを構築するのに必要な基本的なビルド ブロック、プロセス、および手法について説明します。  特定の問題について MSDN ライブラリを検索したり、[LINQ フォーラム](http://go.microsoft.com/fwlink/?LinkId=76488)に参加して、複雑なトピックについて専門家と検討したりすることもできます。  また、「[LINQ to SQL: リレーショナル データのための .NET 統合言語クエリ](http://go.microsoft.com/fwlink/?LinkId=93205)」ホワイト ペーパーには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] テクノロジの詳細と、[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] および C\# のコード例が記載されています。  
  
## このセクションの内容  
 [Getting Started](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の簡単な概要と、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を使用して作業を始める方法を示します。  
  
 [プログラミング ガイド](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 マップ、クエリ、更新、デバッグ、および同様の操作を行う手順を示します。  
  
 [Reference](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のさまざまな側面に関するリファレンス情報を示します。  SQL\-CLR 型マッピング、標準クエリ演算子変換などのトピックが含まれます。  
  
 [Samples](../../../../../../docs/framework/data/adonet/sql/linq/samples.md)  
 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] および C\# のサンプルへのリンクを示します。  
  
## 関連項目  
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)  
 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] テクノロジの概要を示します。  
  
 [LINQ](../Topic/LINQ%20in%20Visual%20Basic.md)  
 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] ユーザーを対象に [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] テクノロジについて説明します。  
  
 [LINQ to ADO.NET](http://msdn.microsoft.com/ja-jp/be3297b9-1b54-4d4c-82a8-add0d79c2006)  
 [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] ポータルにリンクします。  
  
 [LINQ to SQL チュートリアル](http://msdn.microsoft.com/ja-jp/308e66ac-f704-4e00-9b4e-7af0045a2374)  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のチュートリアルを一覧します。  
  
 [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 ドキュメントで使用されるサンプル データベースをダウンロードする方法について説明します。  
  
 [LinqDataSource テクノロジの概要](http://msdn.microsoft.com/ja-jp/104cfc3f-7385-47d3-8a51-830dfa791136)  
 <xref:System.Web.UI.WebControls.LinqDataSource> コントロールが [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] データソース コントロールのアーキテクチャを通じて[!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] を Web 開発者に公開する方法について説明します。