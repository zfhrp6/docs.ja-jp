---
title: "データ定義言語の操作 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# データ定義言語の操作
[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] バージョン 4 以降では、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] でデータ定義言語 \(DDL\) がサポートされています。  これにより、接続文字列、およびストレージ \(SSDL\) モデルのメターデータに基づいて、データベース インスタンスを作成または削除できます。  
  
 <xref:System.Data.Objects.ObjectContext> の次のメソッドでは、接続文字列と SSDL の内容を使用して、データベースの作成と削除、データベースが存在するかどうかの確認、生成された DDL スクリプトの表示を実行します。  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
>  DDL コマンドを実行するには、十分なアクセス許可が必要です。  
  
 上記に示したメソッドは、ほとんどの作業を基になる ADO.NET データ プロバイダーに委任します。  データベース オブジェクトの生成に使用される名前付け規則が、照会および更新に使用される規則と一致していることは、プロバイダーによって保証されています。  
  
 次の例は、既存のモデルを基にデータベースを生成する方法を示しています。  また、新しいエンティティ オブジェクトはオブジェクト コンテキストに追加され、データベースに保存されます。  
  
## 手順  
  
#### 既存のモデルに基づいてデータベースを定義するには  
  
1.  コンソール アプリケーションを作成します。  
  
2.  既存のモデルをアプリケーションに追加します。  
  
    1.  `SchoolModel` という名前の空のモデルを追加します。  空のモデルを作成するには、「[How to: Create a New .edmx File](http://msdn.microsoft.com/ja-jp/beb8189e-e51c-4051-839c-9902c224abf2)」を参照してください。  
  
     SchoolModel.edmx ファイルがプロジェクトに追加されます。  
  
    1.  「[School Model](http://msdn.microsoft.com/ja-jp/859a9587-81ea-4a45-9bc0-f8d330e1adac)」から、School モデルの概念、ストレージ、およびマッピングの内容をコピーします。  
  
    2.  SchoolModel.edmx ファイルを開き、`edmx:Runtime` タグ内にその内容を貼り付けます。  
  
3.  main 関数に次のコードを追加します。  このコードでは、データベース サーバーへの接続文字列を初期化し、DDL スクリプトを表示して、データベースを作成します。さらに、コンテキストに新しいエンティティを追加して、データベースに変更内容を保存します。  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]