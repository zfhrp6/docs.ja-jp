---
title: "How to: Generate Customized Code by Modifying a DBML File | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# How to: Generate Customized Code by Modifying a DBML File
データベース マークアップ言語 \(.dbml\) メタデータ ファイルから、[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] または C\# のソース コードを生成できます。  この方法を使用すると、アプリケーション マッピング コードを生成する前に、既定の .dbml ファイルをカスタマイズできます。  これは高度な機能です。  
  
 実行手順は次のとおりです。  
  
1.  .dbml ファイルを生成します。  
  
2.  エディターを使用して .dbml ファイルを変更します。  .dbml ファイルは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml ファイルのスキーマ定義 \(.xsd\) ファイルに照らして検証する必要があることに注意してください。  詳細については、「[Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)」を参照してください。  
  
3.  [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] または C\# のソース コードを生成します。  
  
 次の例では、SQLMetal コマンド ライン ツールを使用します。  詳細については、「[SqlMetal.exe \(コード生成ツール\)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)」を参照してください。  
  
## 使用例  
 次のコードでは、Northwind サンプル データベースから .dbml ファイルを生成します。  データベース メタデータのソースとして、データベースの名前または .mdf ファイルの名前を使用します。  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## 使用例  
 次のコードでは、.dbml ファイルから [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] または C\# のソース コードを生成します。  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## 参照  
 [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)   
 [SqlMetal.exe \(コード生成ツール\)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)   
 [Creating the Object Model](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)