---
title: "SQL Server の CLR 統合の概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# SQL Server の CLR 統合の概要
共通言語ランタイム \(CLR\) は、Microsoft .NET Framework の中核であり、すべての .NET Framework コードの実行環境を提供します。  CLR の内部で実行されるコードはマネージ コードと呼ばれます。  CLR は、ジャストインタイム \(JIT\) コンパイル、メモリの割り当てと管理、タイプ セーフの設定、例外処理、スレッド管理、セキュリティなど、プログラムの実行に必要なさまざまな機能やサービスを備えています。  
  
 Microsoft SQL Server にホストされる CLR \(CLR 統合と呼ばれる\) を利用することで、ストアド プロシージャ、トリガー、ユーザー定義関数、ユーザー定義型、およびユーザー定義集計をマネージ コードで作成できます。  マネージ コードは実行前にネイティブ コードにコンパイルされるため、状況によっては、パフォーマンスが大幅に向上します。  
  
 マネージ コードは、コード アクセス セキュリティ \(CAS\)、コード リンク、およびアプリケーション ドメインを使用して、アセンブリが特定の操作を実行することを防止します。  SQL Server は、CAS を使用して、マネージ コードをセキュリティ保護し、オペレーティング システムやデータベース サーバーへの侵害を防止します。  
  
 このセクションは、SQL Server の CLR 統合を利用したプログラミングを始めるのに十分な情報を提供することを目的としており、包括的な情報の提供は目的としていません。  詳細については、ご使用中の SQL Server のバージョンに対応するバージョンの SQL Server オンライン ブックを参照してください。  
  
 **SQL Server オンライン ブック**  
  
-   [共通言語ランタイム \(CLR\) 統合の概要](http://go.microsoft.com/fwlink/?LinkId=115242)  
  
## CLR 統合の有効化  
 Microsoft SQL Server では共通言語ランタイム \(CLR\) 統合機能が既定でオフになっているため、CLR 統合を利用して実装されるオブジェクトを使用するには、CLR 統合機能を有効にする必要があります。  Transact\-SQL を使用して CLR 統合を有効にするには、次に示すように、`sp_configure` ストアド プロシージャの `clr enabled` オプションを使用します。  
  
```  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 `clr enabled` オプションを 0 に設定することにより、CLR 統合を無効にできます。  CLR 統合を無効にすると、SQL Server ではすべての CLR ルーチンの実行が停止され、すべてのアプリケーション ドメインがアンロードされます。  
  
 詳細については、ご使用中の SQL Server のバージョンに対応するバージョンの SQL Server オンライン ブックを参照してください。  
  
 **SQL Server オンライン ブック**  
  
-   [CLR 統合の有効化](http://go.microsoft.com/fwlink/?LinkId=115230)  
  
## CLR アセンブリの配置  
 CLR メソッドをテスト サーバーでテストおよび検証すると、配置スクリプトを使用してこれらを実稼働サーバーに配布できます。  配置スクリプトは手動で生成するか、SQL Server Management Studio を使用して生成することができます。  詳細については、ご使用中の SQL Server のバージョンに対応するバージョンの SQL Server オンライン ブックを参照してください。  
  
 **SQL Server オンライン ブック**  
  
1.  [CLR データベース オブジェクトの展開](http://go.microsoft.com/fwlink/?LinkId=115232)  
  
## CLR 統合セキュリティ  
 Microsoft SQL Server と Microsoft .NET Framework 共通言語ランタイム \(CLR\) との統合のセキュリティ モデルは、SQL Server 内部で実行されるさまざまなタイプの CLR オブジェクトおよび非 CLR オブジェクトの間のアクセスを管理し、セキュリティで保護します。  これらのオブジェクトは、Transact\-SQL ステートメントまたはサーバーで実行される別の CLR オブジェクトから呼び出される可能性があります。  
  
 詳細については、ご使用中の SQL Server のバージョンに対応するバージョンの SQL Server オンライン ブックを参照してください。  
  
 **SQL Server オンライン ブック**  
  
-   [CLR 統合のセキュリティ](http://go.microsoft.com/fwlink/?LinkId=115234)  
  
## CLR アセンブリのデバッグ  
 Microsoft SQL Server は、データベース内の Transact\-SQL オブジェクトおよび共通言語ランタイム \(CLR\) オブジェクトのデバッグをサポートしています。  デバッグは言語をまたがって機能します。ユーザーは、Transact\-SQL から CLR オブジェクトへ、または CLR オブジェクトから Transact\-SQL へシームレスにデバッグできます。  
  
 詳細については、ご使用中の SQL Server のバージョンに対応するバージョンの SQL Server オンライン ブックを参照してください。  
  
 **SQL Server オンライン ブック**  
  
-   [CLR データベース オブジェクト](http://go.microsoft.com/fwlink/?LinkId=115236)  
  
## 参照  
 [Creating SQL Server 2005 Objects In Managed Code](http://msdn.microsoft.com/ja-jp/5358a825-e19b-49aa-8214-674ce5fed1da)   
 [コード アクセス セキュリティと ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)