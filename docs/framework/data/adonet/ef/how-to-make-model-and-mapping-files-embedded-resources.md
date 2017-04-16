---
title: "モデル ファイルとマッピング ファイルを組み込みリソースにする方法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "ESQL"
  - "jsharp"
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# モデル ファイルとマッピング ファイルを組み込みリソースにする方法
[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] を使用すると、モデル ファイルとマッピング ファイルをアプリケーションの組み込みリソースとして配置できます。  モデル ファイルとマッピング ファイルが組み込まれたアセンブリは、エンティティ接続と同じアプリケーション ドメインに読み込む必要があります。  詳細については、「[接続文字列](../../../../../docs/framework/data/adonet/ef/connection-strings.md)」を参照してください。  既定では、[!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] ツールが、モデル ファイルとマッピング ファイルを組み込みます。モデル ファイルとマッピング ファイルを手動で定義する場合は、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] アプリケーションと共にモデル ファイルとマッピング ファイルが組み込みリソースとして確実に配置されるように、この手順を使用します。  
  
> [!NOTE]
>  組み込みリソースを保持するには、モデル ファイルとマッピング ファイルを変更するたびに、この手順を繰り返す必要があります。  
  
### モデル ファイルとマッピング ファイルを組み込むには  
  
1.  **ソリューション エクスプローラー**で、概念 \(.csdl\) ファイルを選択します。  
  
2.  **\[プロパティ\]** ペインで、**\[ビルド アクション\]** を **\[組み込まれたリソース\]** に設定します。  
  
3.  ストレージ \(.ssdl\) ファイルとマッピング \(.msl\) ファイルに対して手順 1. と手順 2. を繰り返します。  
  
4.  **ソリューション エクスプローラー**で、App.config ファイルをダブルクリックし、次のいずれかの形式に基づいて `connectionString` 属性の `Metadata` パラメーターを変更します。  
  
    -   `Metadata=` `res://<assemblyFullName>/<resourceName>;`  
  
    -   `Metadata=` `res://*/<resourceName>;`  
  
    -   `Metadata=res://*;`  
  
     詳細については、「[接続文字列](../../../../../docs/framework/data/adonet/ef/connection-strings.md)」を参照してください。  
  
## 使用例  
 次の接続文字列は、[AdventureWorks Sales Model](http://msdn.microsoft.com/ja-jp/f16cd988-673f-4376-b034-129ca93c7832) の組み込みモデル ファイルとマッピング ファイルを参照しています。  この接続文字列は、プロジェクトの App.config ファイルに格納されています。  
  
  
  
## 参照  
 [モデリングとマッピング](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)   
 [接続文字列を定義する方法](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)   
 [EntityConnection の接続文字列を作成する方法](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)   
 [ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/ja-jp/91076853-0881-421b-837a-f582f36be527)