---
title: "SQL Server でのストアド プロシージャの署名 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# SQL Server でのストアド プロシージャの署名
証明書や非対称キーを使用してストアド プロシージャに署名することができます。  この機能は、動的 SQL などのように、組み合わせ所有権によって権限を継承できない場合や、組み合わせ所有権が壊れている場合を想定して用意されています。  証明書に割り当てられたユーザーを作成し、その証明書ユーザーにストアド プロシージャがアクセスする必要があるオブジェクトへの権限を与えることができます。  
  
 ストアド プロシージャが実行されると、証明書ユーザーの権限が呼び出し元の権限と組み合わされます。  EXECUTE AS 句とは異なり、プロシージャの実行コンテキストは変更されません。  ログイン名とユーザー名を返す組み込み関数を実行すると、証明書ユーザーの名前ではなく、呼び出し元の名前が返されます。  
  
 デジタル署名は、署名者の秘密キーで暗号化されたデータ ダイジェストです。  秘密キーにより、デジタル署名がその保持者または所有者に固有であることが保証されます。  ストアド プロシージャ、関数、またはトリガーに署名することができます。  
  
> [!NOTE]
>  マスター データベースに証明書を作成することで、サーバー レベルの権限を許可できます。  
  
## 証明書の作成  
 証明書を使用してストアド プロシージャに署名すると、ストアド プロシージャのコードの暗号化ハッシュで構成されたデータ ダイジェストが秘密キーを使用して作成されます。  実行時に、このデータ ダイジェストが公開キーを使用して復号化され、ストアド プロシージャのハッシュ値と比較されます。  ストアド プロシージャに変更が加えられるとハッシュ値が無効になり、デジタル署名が一致しなくなります。  これによって、秘密キーにアクセスできない人物によってストアド プロシージャのコードが変更されることを防ぎます。  そのため、プロシージャを変更するたびに署名し直す必要があります。  
  
 モジュールへの署名は、次の 4 つの手順で行います。  
  
1.  Transact\-SQL ステートメント `CREATE CERTIFICATE [certificateName]` を使用して、証明書を作成します。  このステートメントには、開始日、終了日、パスワードを設定するためのオプションがあります。  既定の有効期限は 1 年間です。  
  
2.  Transact\-SQL ステートメント `CREATE USER [userName] FROM CERTIFICATE [certificateName]` を使用して、証明書に関連付けられたデータベース ユーザーを作成します。  このユーザーはデータベース内のみに存在し、ログインには関連付けられません。  
  
3.  証明書ユーザーに、データベース オブジェクトに対して必要な権限を与えます。  
  
> [!NOTE]
>  証明書では、DENY ステートメントを使用して権限が取り消されているユーザーに権限を与えることはできません。  DENY は常に GRANT よりも優先されるため、証明書ユーザーに許可された権限を呼び出し元が継承することはできません。  
  
1.  Transact\-SQL ステートメント `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` を使用して、証明書によってプロシージャに署名します。  
  
## 外部リソース  
 詳細については、次のリソースを参照してください。  
  
|リソース|説明|  
|----------|--------|  
|SQL Server オンライン ブックの「[モジュールの署名](http://go.microsoft.com/fwlink/?LinkId=98590)」|モジュールの署名について説明し、サンプル シナリオと、関連する Transact\-SQL のトピックへのリンクを示します。|  
|SQL Server オンライン ブックの「[チュートリアル : 証明書を使用したストアド プロシージャへの署名](http://msdn.microsoft.com/library/bb283630.aspx)」|証明書を使用したストアド プロシージャの署名のチュートリアルです。|  
  
## 参照  
 [ADO.NET アプリケーションのセキュリティ保護](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)   
 [SQL Server セキュリティの概要](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)   
 [SQL Server におけるアプリケーション セキュリティのシナリオ](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)   
 [SQL Server でのストアド プロシージャを使用したアクセス許可の管理](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)   
 [SQL Server での安全な動的 SQL の作成](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)   
 [SQL Server での借用を使用した権限のカスタマイズ](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)   
 [ストアド プロシージャでのデータの変更](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)