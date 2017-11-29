---
title: "Entity SQL 言語"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 08e366e8bbd9df31f367496ca5e106b876921896
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="entity-sql-language"></a>Entity SQL 言語
Entity SQL は、ストレージに依存しない SQL と似たクエリ言語です。 Entity SQL を使用すると、オブジェクトとして、または表形式でエンティティ データに対してクエリを実行できます。 次の場合には Entity SQL の使用を検討してください。  
  
-   クエリを実行時に動的に作成する必要がある場合。 その場合、実行時に Entity SQL クエリ文字列を作成する代わりに、<xref:System.Data.Objects.ObjectQuery%601> のクエリ ビルダー メソッドを使用することも検討してください。  
  
-   モデル定義の一部としてクエリを定義する場合。 データ モデルでは Entity SQL のみがサポートされます。 詳細については、次を参照してください[QueryView 要素 (MSL)。](http://msdn.microsoft.com/en-us/f0426b34-45cb-4fd7-9777-e0570c5e0e80)  
  
-   EntityClient で <xref:System.Data.EntityClient.EntityDataReader> を使用して行セットとして読み取り専用エンティティ データを返す場合。 詳細については、次を参照してください。 [Entity Framework の EntityClient プロバイダー](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)です。  
  
-   SQL ベースのクエリ言語に詳しい場合、Entity SQL の使用が最も適切に思われるでしょう。  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a>Entity SQL と EntityClient プロバイダーの使用  
 Entity SQL を EntityClient プロバイダーと一緒に使用する際の詳細については、次のトピックを参照してください。  
  
 [Entity Framework の EntityClient プロバイダー](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [方法: EntityConnection の接続文字列を作成します。](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [方法: PrimitiveType 結果を返すクエリを実行](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [方法: StructuralType 結果を返すクエリを実行](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [方法: RefType 結果を返すクエリを実行](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [方法: 複合型を返すクエリを実行](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [方法: 入れ子になったコレクションを返すクエリを実行](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [方法: EntityCommand を使用してパラメーター化 Entity SQL クエリを実行](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [方法: EntityCommand を使用してパラメーター化されたストアド プロシージャの実行](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [方法: ポリモーフィック クエリを実行](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [方法: でリレーションシップをナビゲート、Navigate 演算子](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a>Entity SQL とオブジェクト クエリの使用  
 Entity SQL をオブジェクト クエリと一緒に使用する際の詳細については、次のトピックを参照してください。  
  
 [方法: エンティティ型のオブジェクトを返すクエリを実行](http://msdn.microsoft.com/en-us/f73e137d-1534-42bb-9e31-99ca42c19b48)  
  
 [方法: パラメーター化クエリを実行します。](http://msdn.microsoft.com/en-us/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
  
 [方法: ナビゲーション プロパティを使用するリレーションシップの移動](http://msdn.microsoft.com/en-us/b1d71c7d-16a7-4b46-96ac-690176bd5057)  
  
 [方法: ユーザー定義関数を呼び出す](http://msdn.microsoft.com/en-us/ad131b86-8b4e-4747-8605-d4fc64fb9d02)  
  
 [方法: データをフィルター処理](http://msdn.microsoft.com/en-us/776f8556-3350-4572-804a-b1513515c1b2)  
  
 [方法: データの並べ替え](http://msdn.microsoft.com/en-us/c05f2506-cb9d-4ebc-822b-300042ad53e7)  
  
 [方法: データをグループ化](http://msdn.microsoft.com/en-us/df801d9d-9a8a-4157-97a6-5016b18998e1)  
  
 [方法: データを集計します。](http://msdn.microsoft.com/en-us/4cf04ce8-3c0f-4f88-9d97-8fac8622598d)  
  
 [方法: 匿名型のオブジェクトを返すクエリを実行](http://msdn.microsoft.com/en-us/3b264025-e911-4d73-90ce-992d2b9d189d)  
  
 [方法: プリミティブ型のコレクションを返すクエリを実行](http://msdn.microsoft.com/en-us/115b52c0-4f27-4253-8991-284b450000b5)  
  
 [方法: EntityCollection 内の関連オブジェクトをクエリ](http://msdn.microsoft.com/en-us/11ce946f-16f8-4c1d-9d80-f740853807ba)  
  
 [方法: 2 つのクエリの和集合を注文](http://msdn.microsoft.com/en-us/853c583a-eaba-4400-830d-be974e735313)  
  
 [方法: 結果をクエリ ページング](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a>関連項目  
 [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)  
 [言語リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
