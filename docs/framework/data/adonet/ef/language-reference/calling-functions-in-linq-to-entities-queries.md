---
title: "LINQ to Entities クエリ内の関数の呼び出し"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6e50147d356ad9e389a87868205bb9b8b6b3e7b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="calling-functions-in-linq-to-entities-queries"></a>LINQ to Entities クエリ内の関数の呼び出し
このセクションの各トピックでは、LINQ to Entities クエリで関数を呼び出す方法について説明します。  
  
 <xref:System.Data.Objects.EntityFunctions> クラスおよび <xref:System.Data.Objects.SqlClient.SqlFunctions> クラスを使用すると、Entity Framework の一部として正規関数およびデータベース関数にアクセスできます。 詳細については、次を参照してください。[する方法: 正規の関数を呼び出す](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)と[する方法: データベース関数を呼び出す](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)です。  
  
 カスタム関数を呼び出すプロセスには、3 つの基本的な手順が必要です。  
  
1.  概念モデルで関数を定義するか、ストレージ モデルで関数を宣言します。  
  
2.  メソッドをアプリケーションに追加し、<xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> を使用してこれをモデルの関数にマップします。  
  
3.  LINQ to Entities クエリから関数を呼び出します。  
  
 詳細については、このセクションの各トピックを参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: 正規関数を呼び出す](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [方法: データベース関数を呼び出す](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [方法: カスタム データベース関数を呼び出す](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [方法: クエリでモデル定義関数を呼び出す](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [方法: オブジェクトのメソッドとしてのモデル定義関数を呼び出す](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a>関連項目  
 [LINQ to Entities でのクエリ](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [正規関数](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)  
 [.edmx ファイルの概要](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [方法: カスタム関数を概念モデルの定義](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f)
