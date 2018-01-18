---
title: "チュートリアルによる学習"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8ae2965-6a49-4155-89b0-7fab2c488ab1
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 56852fece0ca1f2dbb70b1bb29c09205b97faf56
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="learning-by-walkthroughs"></a>チュートリアルによる学習
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ドキュメントには、いくつかのチュートリアルが用意されています。 このトピックでは、チュートリアルに関する全般的な話題 (トラブルシューティングを含む) を取り上げます。また、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] について学ぶための、いくつかの入門レベルのチュートリアルへのリンクを示します。  
  
> [!NOTE]
>  この「入門のためのチュートリアル」のセクションのチュートリアルでは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 技術をサポートする基本的なコードを紹介します。 実際の開発では、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]と Windows フォーム プロジェクトを使用して [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アプリケーションを実装するのが一般的です。 そのための例とチュートリアルは、[!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] のドキュメントにあります。  
  
## <a name="getting-started-walkthroughs"></a>入門のためのチュートリアル  
 このセクションではいくつかのチュートリアルを示します。 これらのチュートリアルは、Northwind サンプル データベースを基にしており、複雑さを抑えて、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の機能を少しずつ導入していきます。  
  
 一般的な流れは次のとおりです。  
  
|目標|Visual Basic|C#|  
|---------------|------------------|---------|  
|エンティティ クラスを作成し、簡単なクエリを実行します。|[チュートリアル : 簡単なオブジェクト モデルとクエリ (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md)|[チュートリアル : 簡単なオブジェクト モデルとクエリ (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md)|  
|2 番目のクラスを追加し、より複雑なクエリを実行します <br /><br /> (前のチュートリアルを完了している必要があります)。|[チュートリアル : リレーションシップ間でのクエリの実行 (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md)|[チュートリアル : リレーションシップ間でのクエリの実行 (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md)|  
|データベースの項目を追加、変更、および削除します。|[チュートリアル : データの操作 (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)|[チュートリアル : データの操作 (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)|  
|ストアド プロシージャを使用します。|[チュートリアル : ストアド プロシージャのみの使用 (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-visual-basic.md)|[チュートリアル : ストアド プロシージャのみを使用する (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-csharp.md)|  
  
## <a name="general"></a>全般  
 以下の情報は、これらのチュートリアル全体に該当します。  
  
-   環境 : [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の各チュートリアルでは、統合開発環境 (IDE: Integrated Development Environment) として [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] を使用します。  
  
-   SQL エンジン : これらのチュートリアルは、SQL Server Express を使用して実装できるように作成されています。 SQL Server Express を持っていない場合は、無料でダウンロードできます。 詳細については、次を参照してください。[サンプル データベースのダウンロード](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)です。  
  
    > [!NOTE]
    >  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のチュートリアルでは、ファイル名を接続文字列として使用します。 ファイル名を指定するだけで済むのは、SQL Server Express ユーザーのために [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] に備わっている機能です。 セキュリティ問題には常に注意してください。 詳細については、次を参照してください。 [LINQ to SQL でセキュリティ](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md)です。  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]チュートリアルでは、Northwind サンプル データベースが通常必要とします。 詳細については、次を参照してください。[サンプル データベースのダウンロード](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)です。  
  
-   使用している設定または [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] のエディションによっては、チュートリアルの中で、ヘルプの記載と異なるダイアログ ボックスやメニュー コマンドが表示される場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
-   多階層のシナリオに関連するチュートリアルでは、開発用コンピューターとは別のコンピューターにサーバーが配置されていることと、そのサーバーにアクセスするための適切なアクセス許可が必要です。  
  
-   通常、Northwind サンプル データベースの Orders テーブルを表すクラスの名前は `[Order]` です。 エスケープが必要な理由は、`Order` が [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] のキーワードであるためです。  
  
## <a name="troubleshooting"></a>トラブルシューティング  
 これらのチュートリアルで使用するデータベースにアクセスするための十分なアクセス許可がない場合、ランタイム エラーが発生することがあります。 特に一般的な問題を解決するためのヒントについては、以下の手順を参照してください。  
  
### <a name="log-on-issues"></a>ログオンの問題  
 アプリケーションが試みているデータベース アクセスの方法が、データベースが受け付けないログオン方法である可能性があります。  
  
##### <a name="to-verify-or-change-the-database-log-on"></a>データベース ログオンを確認または変更するには  
  
1.  Windows の**開始** メニューのをポイント**すべてのプログラム**、 **Microsoft SQL Server 2005**、 をポイント**構成ツール**をクリックし、**SQL Server 構成マネージャー**です。  
  
2.  左側のウィンドウで、 **SQL Server 構成マネージャー**をクリックして**SQL Server 2005 Services**です。  
  
3.  右側のペインで右クリック**SQL Server (SQLEXPRESS)**、クリックして**プロパティ**です。  
  
4.  クリックして、**ログオン**タブし、サーバーにログオンを行う方法を確認してください。  
  
     ほとんどの場合、**ローカル システム**動作します。  
  
     変更を加えた場合はクリックして**再起動**サービスを再起動します。  
  
### <a name="protocols"></a>プロトコル  
 場合によっては、アプリケーションがデータベースにアクセスするためのプロトコルが正しく設定されていないこともあります。 たとえば、**名前付きパイプ**のチュートリアルに必要なプロトコル[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]既定で無効になっています。  
  
##### <a name="to-enable-the-named-pipes-protocol"></a>名前付きパイプ プロトコルを有効にするには  
  
1.  左側のウィンドウで、 **SQL Server 構成マネージャー**、展開**SQL Server 2005 ネットワークの構成**、クリックして**SQLEXPRESS のプロトコル**です。  
  
2.  右側のウィンドウでことを確認、**名前付きパイプ**プロトコルを有効にします。 そうでない場合は右クリック**名前付きパイプ** をクリックし、**を有効にする**です。  
  
     サービスの停止および再起動が必要になります。 次のブロックの手順に従って操作します。  
  
### <a name="stopping-and-restarting-the-service"></a>サービスの停止および再起動  
 変更を有効にするには、サービスを停止し、再起動する必要があります。  
  
##### <a name="to-stop-and-restart-the-service"></a>サービスを停止および再起動するには  
  
1.  左側のウィンドウで、 **SQL Server 構成マネージャー**をクリックして**SQL Server 2005 Services**です。  
  
2.  右側のペインで右クリック**SQL Server (SQLEXPRESS)**、クリックして**停止**です。  
  
3.  右クリック**SQL Server (SQLEXPRESS)**、クリックして**再起動**です。  
  
## <a name="see-also"></a>参照  
 [はじめに](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
