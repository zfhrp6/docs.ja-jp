---
title: "方法 : DBML ファイルを変更してカスタマイズ コードを生成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: efff585cff127e71e2dedd8abf2f502ca28e8df7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a>方法 : DBML ファイルを変更してカスタマイズ コードを生成する
生成することができます[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]または c# ソース コード データベース マークアップ言語 (.dbml) メタデータ ファイルからです。 この方法を使用すると、アプリケーション マッピング コードを生成する前に、既定の .dbml ファイルをカスタマイズできます。 これは高度な機能です。  
  
 実行手順は次のとおりです。  
  
1.  .dbml ファイルを生成します。  
  
2.  エディターを使用して .dbml ファイルを変更します。 .Dbml ファイルがのスキーマ定義 (.xsd) ファイルに対して検証する必要があります注[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].dbml ファイル。 詳細については、次を参照してください。 [LINQ to SQL でのコード生成](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)です。  
  
3.  [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] または C# のソース コードを生成します。  
  
 次の例では、SQLMetal コマンド ライン ツールを使用します。 詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。  
  
## <a name="example"></a>例  
 次のコードでは、Northwind サンプル データベースから .dbml ファイルを生成します。 データベース メタデータのソースとして、データベースの名前または .mdf ファイルの名前を使用します。  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a>例  
 次のコードでは、.dbml ファイルから [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] または C# のソース コードを生成します。  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a>参照  
 [LINQ to SQL でのコード生成](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [SqlMetal.exe (コード生成ツール)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [オブジェクト モデルの作成](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
