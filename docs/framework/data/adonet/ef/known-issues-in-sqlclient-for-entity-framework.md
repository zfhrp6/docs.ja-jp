---
title: "Entity Framework 用の .NET Framework Data Provider for SQL Server (SqlClient) の既知の問題"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48fe4912-4d0f-46b6-be96-3a42c54780f6
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 67d4c4f08661bbf2febefead64e62c8a84045f47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="known-issues-in-sqlclient-for-entity-framework"></a>Entity Framework 用の .NET Framework Data Provider for SQL Server (SqlClient) の既知の問題
ここでは、.NET Framework Data Provider for SQL Server (SqlClient) に関連する既知の問題について説明します。  
  
## <a name="trailing-spaces-in-string-functions"></a>文字列関数の末尾のスペース  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] では、文字列値の末尾のスペースは無視されます。 そのため、文字列の末尾にスペースを挿入すると、予期できない結果が生じたり、場合によってはエラーが発生することもあります。  
  
 文字列の末尾にスペースを挿入する必要がある場合は、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] が文字列を切り捨てることがないように、空白文字を挿入することを検討してください。 末尾のスペースが不要である場合は、クエリ パイプラインに渡す前にスペースを削除してください。  
  
## <a name="right-function"></a>RIGHT 関数  
 `null`, 0`RIGHT(nvarchar(max)` または `)`, 0`RIGHT(varchar(max)` に、最初の引数として `)` 以外の値を、2 番目の引数として 0 を渡すと、`NULL` 文字列の代わりに `empty` 値が返されます。  
  
## <a name="cross-and-outer-apply-operators"></a>CROSS APPLY 演算子および OUTER APPLY 演算子  
 CROSS APPLY 演算子および OUTER APPLY 演算子は [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)] で導入されました。 場合によっては、クエリ パイプラインにより、CROSS APPLY 演算子または OUTER APPLY 演算子を含む Transact-SQL ステートメントが生成されることがあります。 一部のバックエンド プロバイダー ([!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] より古いバージョンの [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)] など) では、これらの演算子がサポートされていません。したがって、このようなクエリをこれらのバックエンド プロバイダーで実行することはできません。  
  
 CROSS APPLY 演算子または OUTER APPLY 演算子を含むクエリの生成につながる可能性がある一般的なシナリオを次に示します。  
  
-   ページングを使用した相関サブクエリ  
  
-   相関サブクエリ全体、またはナビゲーションによって生成されたコレクション全体を対象とした `AnyElement`  
  
-   要素セレクターを受け取るグループ化メソッドを使用する LINQ クエリ  
  
-   CROSS APPLY 演算子または OUTER APPLY 演算子が明示的に指定されたクエリ  
  
-   REF コンストラクターを引数に取る DEREF コンストラクターを含むクエリ。  
  
## <a name="skip-operator"></a>SKIP 演算子  
 使用している場合[!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]、非キー列で ORDER BY と共に SKIP を使用すると、誤った結果が返される可能性があります。 キー以外の列に重複するデータが存在する場合、指定された数を超える行はスキップされます。 これは、[!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] 用に SKIP が変換される方法によるものです。 たとえば、次のクエリでは、5 つを超える行はスキップされる場合`E.NonKeyColumn`は重複する値があります。  
  
```  
SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L  
```  
  
## <a name="targeting-the-correct-sql-server-version"></a>適切なバージョンの SQL Server を対象としたクエリの実行  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]ターゲット、[!INCLUDE[tsql](../../../../../includes/tsql-md.md)]で指定されている SQL Server のバージョンに基づくクエリ、`ProviderManifestToken`ストレージ モデル (.ssdl) ファイル内のスキーマ要素の属性です。 このバージョンは、実際に接続する SQL Server のバージョンとは異なる場合があります。 たとえば、使用している SQL Server のバージョンが 2005 で、`ProviderManifestToken` 属性が 2008 に設定されている場合、生成された [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] クエリがサーバーで実行されないことがあります。 たとえば、SQL Server 2008 で導入された新しい日付時刻型を使用するクエリは、SQL Server の以前のバージョンでは実行されません。 SQL Server 2005 を使用している場合は、`ProviderManifestToken`属性が 2000年に設定されて、生成される[!INCLUDE[tsql](../../../../../includes/tsql-md.md)]クエリがあります、十分に最適化するクエリがサポートされていないことを示す例外が発生する可能性があります。 詳細については、このトピックの「CROSS APPLY 演算子および OUTER APPLY 演算子」を参照してください。  
  
 データベースの一部の動作は、データベースの互換性レベルの設定に依存します。 使用している SQL Server のバージョンが 2005 で、`ProviderManifestToken` 属性が 2005 に、データベースの互換性レベルが "80" (SQL Server 2000) に設定されている場合、生成された [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] の実行対象は SQL Server 2005 になりますが、互換性レベルの設定が原因で予期したとおりに実行されないことがあります。 たとえば、ORDER BY リストの列名とセレクターの列名が一致する場合、順序付けが失われることがあります。  
  
## <a name="nested-queries-in-projection"></a>投影内の入れ子になったクエリ  
 projection 句内の入れ子になったクエリは、サーバーでデカルト積に変換されないことがあります。 SLQ Server などの一部のバックエンド サーバーでは、これによって TempDB テーブルのサイズが非常に大きくなり、 サーバーのパフォーマンスが低下する可能性があります。  
  
 projection 句内の入れ子になったクエリの例を次に示します。  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="server-generated-guid-identity-values"></a>サーバー生成の GUID ID 値  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] では、サーバー生成の GUID 型 ID 値がサポートされますが、プロバイダーは、サーバー生成の ID 値を行の挿入後に返す動作をサポートする必要があります。 以降で[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]2005 でサーバー生成 GUID 型を返すことができます、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]を通じてデータベース、 [OUTPUT 句](http://go.microsoft.com/fwlink/?LinkId=169400)です。  
  
## <a name="see-also"></a>関連項目  
 [Entity Framework 用 SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)  
 [既知の問題とエンティティを LINQ での考慮事項](../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)
