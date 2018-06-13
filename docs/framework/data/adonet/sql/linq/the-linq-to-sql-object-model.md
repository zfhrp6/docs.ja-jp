---
title: LINQ to SQL オブジェクト モデル
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81dd0c37-e2a4-4694-83b0-f2e49e693810
ms.openlocfilehash: c716847c60611a6e8a2911d4b9ae2f1683d2cdd0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365385"
---
# <a name="the-linq-to-sql-object-model"></a>LINQ to SQL オブジェクト モデル
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]開発者のプログラミング言語で表されるオブジェクト モデルは、リレーショナル データベースのデータ モデルにマップします。 データ操作はオブジェクト モデルに従って行われます。  
  
 このシナリオでは、データベースに対してデータベース コマンド (`INSERT` など) を実行する必要はありません。 代わりに、オブジェクト モデル内で値を変更し、メソッドを実行します。 データベースに対してクエリを実行したり、変更を送信する必要がある場合、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、要求を正しい SQL コマンドに変換し、そのコマンドをデータベースに送信します。  
  
 ![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")  
  
 内の最も基本的な要素、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]オブジェクト モデルとリレーショナル データ モデル内の要素との関係は次の表に概要を示します。  
  
|LINQ to SQL オブジェクト モデル|リレーショナル データ モデル|  
|------------------------------|---------------------------|  
|エンティティ クラス|テーブル|  
|クラス メンバー|Column|  
|関連付け|外部キー リレーションシップ|  
|メソッド|ストアド プロシージャまたは関数|  
  
> [!NOTE]
>  次の説明は、リレーショナル データ モデルと規則に関する基本的な知識があることが前提です。  
  
## <a name="linq-to-sql-entity-classes-and-database-tables"></a>LINQ to SQL エンティティ クラスおよびデータベース テーブル  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、データベース テーブルで表現され、*エンティティ クラス*です。 エンティティ クラスは、作成する他のクラスに似ていますが、クラスをデータベース テーブルに関連付ける特別な情報を使用して、クラスに注釈を付ける点が異なります。 次の例に示すように、クラス宣言にカスタム属性 (<xref:System.Data.Linq.Mapping.TableAttribute>) を追加することによって、この注釈を付けます。  
  
### <a name="example"></a>例  
 [!code-csharp[DLinqObjectModel#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#1)]
 [!code-vb[DLinqObjectModel#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#1)]  
  
 テーブルとして宣言されたクラスのインスタンスのみ (つまり、エンティティ クラス)、データベースに保存できます。  
  
 詳細については、テーブルの属性の参照[属性ベースの対応付け](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)です。  
  
## <a name="linq-to-sql-class-members-and-database-columns"></a>LINQ to SQL クラス メンバーおよびデータベース列  
 クラスとテーブルの関連付けに加えて、フィールドまたはプロパティを設定してデータベース列を表すことができます。 このためには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、次の例に示すように <xref:System.Data.Linq.Mapping.ColumnAttribute> 属性を定義します。  
  
### <a name="example"></a>例  
 [!code-csharp[DLinqObjectModel#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#2)]
 [!code-vb[DLinqObjectModel#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#2)]  
  
 列に対応付けられたフィールドおよびプロパティのみ、データベースに保持したり、データベースから取得できます。 列として宣言されていないものは、アプリケーション ロジックの一時的な部分と見なされます。  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute> 属性にはさまざまなプロパティがあり、これを使用することで、列を表すメンバーをカスタマイズできます (たとえば、主キー列を表すメンバーを指定できます)。 詳細についてを参照してください、列の属性の[属性ベースの対応付け](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)です。  
  
## <a name="linq-to-sql-associations-and-database-foreign-key-relationships"></a>LINQ to SQL の関連付けおよびデータベースの外部キー リレーションシップ  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、適用することによってデータベースの関連付け (外部キーと主キーのリレーションシップ) などを表す、<xref:System.Data.Linq.Mapping.AssociationAttribute>属性。 次のコードのセグメントで、`Order`クラスが含まれています、`Customer`プロパティを持つ、<xref:System.Data.Linq.Mapping.AssociationAttribute>属性。 このプロパティとその属性が、`Order` クラスおよび `Customer` クラスとのリレーションシップを提供します。  
  
 `Customer` クラスの `Order` プロパティを表示する方法を次の例に示します。  
  
### <a name="example"></a>例  
 [!code-csharp[DLinqObjectModel#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#3)]
 [!code-vb[DLinqObjectModel#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#3)]  
  
 詳細については、の「Association 属性」セクションを参照してください。[属性ベースの対応付け](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)です。  
  
## <a name="linq-to-sql-methods-and-database-stored-procedures"></a>LINQ to SQL メソッドおよびデータベース ストアド プロシージャ  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、ストアド プロシージャとユーザー定義関数をサポートしています。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、それらをクライアント コードから厳密に型指定された方法でアクセスできるようにするクライアント オブジェクトにこれらのデータベースの定義済みの抽象化をマップします。 メソッド シグネチャは、データベース内で定義されているプロシージャおよび関数のシグネチャと可能な限りよく似ています。 IntelliSense を使用して、これらのメソッドを見つけることができます。  
  
 呼び出しによって対応するプロシージャに返される結果セットは、厳密に型指定されたコレクションです。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、<xref:System.Data.Linq.Mapping.FunctionAttribute> 属性と <xref:System.Data.Linq.Mapping.ParameterAttribute> 属性を使用して、ストアド プロシージャおよび関数をメソッドに対応付けます。 ストアド プロシージャを表すメソッドは、<xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> プロパティによって、ユーザー定義関数を表すメソッドと区別されます。 このプロパティが `false` (既定値) に設定されている場合、メソッドはストアド プロシージャを表します。 `true` に設定されている場合、メソッドはデータベース関数を表します。  
  
> [!NOTE]
>  Visual Studio を使用している場合を使用できます、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]ストアド プロシージャおよびユーザー定義関数にマップされているメソッドを作成します。  
  
### <a name="example"></a>例  
 [!code-csharp[DLinqObjectModel#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#4)]
 [!code-vb[DLinqObjectModel#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#4)]  
  
 詳細については、の関数の属性、Stored Procedure 属性およびパラメーターの属性のセクションを参照してください。[属性ベースの対応付け](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)と[Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)です。  
  
## <a name="see-also"></a>関連項目  
 [属性ベースの対応付け](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [背景情報](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
