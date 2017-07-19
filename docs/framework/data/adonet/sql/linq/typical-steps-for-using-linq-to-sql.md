---
title: "Typical Steps for Using LINQ to SQL | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Typical Steps for Using LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アプリケーションを実装するには、このトピックで説明する手順に従います。  多くの手順は省略できます。  既定の状態でオブジェクト モデルを使用することもできます。  
  
 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]を使用してオブジェクト モデルを作成し、クエリのコーディングを開始すると、非常に簡単です。  
  
## オブジェクト モデルの作成  
 最初に、既存のリレーショナル データベースのメタデータからオブジェクト モデルを作成します。  オブジェクト モデルは、開発者のプログラミング言語に従ってデータベースを表します。  詳細については、「[The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)」を参照してください。  
  
### 1.モデルを作成するツールを選択します。  
 モデルを作成するツールとして、3 つのツールを使用できます。  
  
-   [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]  
  
     このデザイナーは、既存のデータベースからモデルを作成する多機能なユーザー インターフェイスを備えています。  このツールは [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] IDE の一部であり、小規模または中規模のデータベースに最適です。  
  
-   SQLMetal コード生成ツール  
  
     このコマンド ライン ユーティリティは、[!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]と多少異なるオプション セットを備えています。  このツールは、大規模なデータベースのモデル化に適しています。  詳細については、「[SqlMetal.exe \(コード生成ツール\)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)」を参照してください。  
  
-   コード エディター  
  
     [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] コード エディターまたは他のエディターを使用して、独自のコードを作成できます。  既存のデータベースがあり、[!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]または SQLMetal ツールを使用できる場合は、この方法はエラーを発生する可能性が高いため、その使用はお勧めできません。  ただし、コード エディターは、他のツールを使用して既に生成されたコードを調整または変更する場合に役立ちます。  詳細については、「[How to: Customize Entity Classes by Using the Code Editor](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)」を参照してください。  
  
### 2.生成するコードの種類を選択します。  
  
-   属性ベースの対応付け用の C\# または [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ソース コード。  
  
     このコード ファイルを、[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] プロジェクトに含めます。詳細については、「[Attribute\-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)」を参照してください。  
  
-   外部マッピング用の XML ファイル。  
  
     この方法を使用すると、アプリケーション コードとは別にマッピング メタデータを保持できます。  詳細については、「[External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)」を参照してください。  
  
    > [!NOTE]
    >  [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]は、外部マッピング ファイルの生成をサポートしていません。  SQLMetal ツールを使用してこの機能を実装する必要があります。  
  
-   最終コード ファイルを生成する前に変更できる DBML ファイル。  
  
     これは高度な機能です。  
  
### 3.コード ファイルを調整して、アプリケーションのニーズを反映します。  
 この目的で、[!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]またはコード エディターを使用できます。  
  
## オブジェクト モデルの使用  
 2 層シナリオでの開発者とデータの関係を次の図に示します。  その他のシナリオについては、「[N\-Tier and Remote Applications with LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)」を参照してください。  
  
 ![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")  
  
 オブジェクト モデルが完成したので、そのモデル内で情報要求を記述し、データを操作します。  オブジェクト モデルのオブジェクトとプロパティを使用し、データベースの行と列は使用しません。  データベースを直接操作することはありません。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] に対して、記述したクエリの実行、または操作したデータに対する `SubmitChanges()` の呼び出しを指示すると、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、データベースの言語でデータベースと通信します。  
  
 作成したオブジェクト モデルの典型的な使用手順を次に示します。  
  
### 1.クエリを作成し、データベースから情報を取得します。  
 詳細については、「[Query Concepts](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)」および「[Query Examples](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)」を参照してください。  
  
### 2.挿入、更新、および削除の既定の動作をオーバーライドします。  
 この手順は省略できます。  詳細については、「[Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)」を参照してください。  
  
### 3.適切なオプションを設定し、同時実行の競合を検出およびレポートします。  
 同時実行の競合の処理について、モデルの既定値をそのまま使用することも、目的に合わせて変更することもできます。  詳細については、「[How to: Specify Which Members are Tested for Concurrency Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) および「[How to: Specify When Concurrency Exceptions are Thrown](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md)」を参照してください。  
  
### 4.継承階層を確立します。  
 この手順は省略できます。  詳細については、「[Inheritance Support](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)」を参照してください。  
  
### 5.適切なユーザー インターフェイスを提供します。  
 この手順は省略でき、アプリケーションの使用方法によって異なります。  
  
### 6.アプリケーションをデバッグおよびテストします。  
 詳細については、「[Debugging Support](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)」を参照してください。  
  
## 参照  
 [Getting Started](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)   
 [Creating the Object Model](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)   
 [Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)