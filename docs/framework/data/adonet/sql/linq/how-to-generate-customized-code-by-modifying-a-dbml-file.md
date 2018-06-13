---
title: '方法 : DBML ファイルを変更してカスタマイズ コードを生成する'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: 806d0ebc0e9ce970e144d80dbbd4910f9d271e56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354573"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a>方法 : DBML ファイルを変更してカスタマイズ コードを生成する
データベース マークアップ言語 (.dbml) メタデータ ファイルから、Visual Basic または c# のソース コードを生成できます。 この方法を使用すると、アプリケーション マッピング コードを生成する前に、既定の .dbml ファイルをカスタマイズできます。 これは高度な機能です。  
  
 実行手順は次のとおりです。  
  
1.  .dbml ファイルを生成します。  
  
2.  エディターを使用して .dbml ファイルを変更します。 .Dbml ファイルがのスキーマ定義 (.xsd) ファイルに対して検証する必要があります注[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].dbml ファイル。 詳細については、次を参照してください。 [LINQ to SQL でのコード生成](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)です。  
  
3.  Visual Basic または c# ソース コードを生成します。  
  
 次の例では、SQLMetal コマンド ライン ツールを使用します。 詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。  
  
## <a name="example"></a>例  
 次のコードでは、Northwind サンプル データベースから .dbml ファイルを生成します。 データベース メタデータのソースとして、データベースの名前または .mdf ファイルの名前を使用します。  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a>例  
 次のコードは、.dbml ファイルから Visual Basic または c# のソース コード ファイルを生成します。  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a>関連項目  
 [LINQ to SQL でのコード生成](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [SqlMetal.exe (コード生成ツール)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [オブジェクト モデルの作成](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
