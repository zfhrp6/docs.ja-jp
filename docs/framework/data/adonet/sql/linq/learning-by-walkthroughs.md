---
title: "Learning by Walkthroughs | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a8ae2965-6a49-4155-89b0-7fab2c488ab1
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Learning by Walkthroughs
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のドキュメントにはいくつかのチュートリアルが用意されています。  このトピックでは、チュートリアルに関する全般的な話題 \(トラブルシューティングを含む\) を取り上げます。また、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] について学ぶための、いくつかの入門レベルのチュートリアルへのリンクを示します。  
  
> [!NOTE]
>  この「入門のためのチュートリアル」のセクションのチュートリアルでは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 技術をサポートする基本的なコードを紹介します。  実際の開発では、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]と Windows フォーム プロジェクトを使用して [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アプリケーションを実装するのが一般的です。  そのための例とチュートリアルは、[!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] のドキュメントにあります。  
  
## 入門のためのチュートリアル  
 このセクションではいくつかのチュートリアルを示します。  これらのチュートリアルは、Northwind サンプル データベースを基にしており、複雑さを抑えて、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の機能を少しずつ導入していきます。  
  
 一般的な流れは次のとおりです。  
  
|目標|Visual Basic|C\#|  
|--------|------------------|---------|  
|エンティティ クラスを作成し、簡単なクエリを実行します。|[Walkthrough: Simple Object Model and Query \(Visual Basic\)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md)|[Walkthrough: Simple Object Model and Query \(C\#\)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md)|  
|2 番目のクラスを追加し、より複雑なクエリを実行します<br /><br /> \(前のチュートリアルを完了している必要があります\)。|[Walkthrough: Querying Across Relationships \(Visual Basic\)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md)|[Walkthrough: Querying Across Relationships \(C\#\)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md)|  
|データベースの項目を追加、変更、および削除します。|[Walkthrough: Manipulating Data \(Visual Basic\)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)|[Walkthrough: Manipulating Data \(C\#\)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)|  
|ストアド プロシージャを使用します。|[Walkthrough: Using Only Stored Procedures \(Visual Basic\)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-visual-basic.md)|[Walkthrough: Using Only Stored Procedures \(C\#\)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-csharp.md)|  
  
## 全般  
 以下の情報は、これらのチュートリアル全体に該当します。  
  
-   環境 : [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の各チュートリアルでは、統合開発環境 \(IDE: Integrated Development Environment\) として [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] を使用します。  
  
-   SQL エンジン : これらのチュートリアルは、SQL Server Express を使用して実装できるように作成されています。  SQL Server Express を持っていない場合は、無料でダウンロードできます。  詳細については、「[Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)」を参照してください。  
  
    > [!NOTE]
    >  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のチュートリアルでは、ファイル名を接続文字列として使用します。  ファイル名を指定するだけで済むのは、SQL Server Express ユーザーのために [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] に備わっている機能です。  セキュリティ問題には常に注意してください。  詳細については、「[Security in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md)」を参照してください。  
  
-   通常、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のチュートリアルには、Northwind サンプル データベースが必要です。  詳細については、「[Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)」を参照してください。  
  
-   使用している設定または [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] のエディションによっては、チュートリアルの中で、ヘルプの記載と異なるダイアログ ボックスやメニュー コマンドが表示される場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
-   多階層のシナリオに関連するチュートリアルでは、開発用コンピューターとは別のコンピューターにサーバーが配置されていることと、そのサーバーにアクセスするための適切なアクセス許可が必要です。  
  
-   通常、Northwind サンプル データベースの Orders テーブルを表すクラスの名前は `[Order]` です。  エスケープが必要な理由は、`Order` が [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] のキーワードであるためです。  
  
## トラブルシューティング  
 これらのチュートリアルで使用するデータベースにアクセスするための十分なアクセス許可がない場合、ランタイム エラーが発生することがあります。  特に一般的な問題を解決するためのヒントについては、以下の手順を参照してください。  
  
### ログオンの問題  
 アプリケーションが試みているデータベース アクセスの方法が、データベースが受け付けないログオン方法である可能性があります。  
  
##### データベース ログオンを確認または変更するには  
  
1.  Windows の **\[スタート\]** ボタンをクリックし、**\[すべてのプログラム\]** をポイントします。次に **\[Microsoft SQL Server 2005\]** をポイントし、**\[構成ツール\]** をポイントして、**\[SQL Server 構成マネージャー\]** をクリックします。  
  
2.  **SQL Server 構成マネージャー**の左ペインで、**\[SQL Server 2005 のサービス\]** をクリックします。  
  
3.  右ペインで **\[SQL Server \(SQLEXPRESS\)\]** を右クリックし、**\[プロパティ\]** をクリックします。  
  
4.  **\[ログオン\]** タブをクリックして、サーバーにログオンする方法を確認します。  
  
     多くの場合は、**\[ローカル システム\]** で正常に動作します。  
  
     変更を加えた場合は、**\[再起動\]** をクリックしてサービスを再起動します。  
  
### プロトコル  
 場合によっては、アプリケーションがデータベースにアクセスするためのプロトコルが正しく設定されていないこともあります。  たとえば、 **のチュートリアルに必要な[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]名前付きパイプ** プロトコルは、既定では有効になっていません。  
  
##### 名前付きパイプ プロトコルを有効にするには  
  
1.  **SQL Server 構成マネージャー**の左ペインで、**\[SQL Server 2005 ネットワークの構成\]** を展開し、**\[SQLEXPRESS のプロトコル\]** をクリックします。  
  
2.  右ペインで、**\[名前付きパイプ\]** プロトコルが有効になっていることを確認します。  有効になっていない場合は、**\[名前付きパイプ\]** を右クリックし、**\[有効化\]** をクリックします。  
  
     サービスの停止および再起動が必要になります。  次のブロックの手順に従って操作します。  
  
### サービスの停止および再起動  
 変更を有効にするには、サービスを停止し、再起動する必要があります。  
  
##### サービスを停止および再起動するには  
  
1.  **SQL Server 構成マネージャー**の左ペインで、**\[SQL Server 2005 のサービス\]** をクリックします。  
  
2.  右ペインで、**\[SQL Server \(SQLEXPRESS\)\]** を右クリックし、**\[停止\]** をクリックします。  
  
3.  **\[SQL Server \(SQLEXPRESS\)\]** を右クリックし、**\[再起動\]** をクリックします。  
  
## 参照  
 [Getting Started](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)