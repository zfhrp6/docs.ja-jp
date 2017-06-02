---
title: "Security in LINQ to SQL | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d49787f7-414e-4c71-aa33-80a5895536b1
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Security in LINQ to SQL
データベースに接続するときは、常にセキュリティのリスクがあります。  LINQ to SQL には SQL Server のデータを操作する新しい方法が含まれていますが、セキュリティ メカニズムは追加されていません。  
  
## アクセス制御と認証  
 LINQ to SQL には独自のユーザー モデルや認証メカニズムがありません。  オブジェクト モデルにマッピングされるデータベース、データベースのテーブル、ビュー、ストアド プロシージャなどへのアクセス制御には SQL Server のセキュリティを使用します。  ユーザーには必要最小限のアクセス権を与え、ユーザー認証には強力なパスワードを要求してください。  
  
## マッピングとスキーマ情報  
 オブジェクト モデルまたは外部マッピング ファイルにある、SQL\-CLR 型マッピングとデータベース スキーマ情報は、ファイル システムでこれらのファイルに対してアクセス権を持つ全ユーザーに公開されます。  オブジェクト モデルや外部マッピング ファイルにアクセスできるユーザーはすべてスキーマ情報を使用できると想定してください。スキーマ情報へのアクセスを制限するには、ファイルのセキュリティ メカニズムを使用してソース ファイルとマッピング ファイルのセキュリティを確保します。  
  
## 接続文字列  
 接続文字列にパスワードを使用することは、できるだけ避けてください。  接続文字列自体がセキュリティのリスクであるうえに、接続文字列はオブジェクト リレーショナル デザイナーまたは SQLMetal コマンド ライン ツールの使用時にオブジェクト モデルや外部マッピング ファイルにクリア テキストで追加できます。  ファイル システムでオブジェクト モデルまたは外部マッピング ファイルに対してアクセス権があれば、どのユーザーでも接続パスワードを見ることができます \(パスワードが接続文字列に含まれている場合\)。  
  
 このようなリスクを最小限に抑えるには、統合セキュリティを使用して [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] との信頼関係接続を作成します。  この方法を使用すると、接続文字列にパスワードを含める必要がなくなります。  詳細については、「[SQL Server のセキュリティ](../../../../../../docs/framework/data/adonet/sql/sql-server-security.md)」を参照してください。  
  
 統合セキュリティがない場合は、接続文字列にクリア テキストのパスワードが必要になります。  以下は、接続文字列のセキュリティ保護に最も有効な手段です。  
  
-   統合セキュリティを使用します。  
  
-   接続文字列をパスワードで保護し、接続文字列の配布を最小限にします。  
  
-   接続文字列の代わりに、表示時間に制限のある <xref:System.Data.SqlClient.SqlConnection?displayProperty=fullName> クラスを使用します。  LINQ to SQL の <xref:System.Data.Linq.DataContext?displayProperty=fullName> クラスは <xref:System.Data.SqlClient.SqlConnection> を使用してインスタンス化できます。  
  
-   すべての接続文字列の期限と接触点を最小限にします。  
  
## 参照  
 [Background Information](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)   
 [Frequently Asked Questions](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)