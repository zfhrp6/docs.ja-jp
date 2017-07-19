---
title: "The LINQ to SQL Object Model | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 81dd0c37-e2a4-4694-83b0-f2e49e693810
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# The LINQ to SQL Object Model
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、開発者のプログラミング言語で表されるオブジェクト モデルが、リレーショナル データベースのデータ モデルに対応付けられています。  データ操作はオブジェクト モデルに従って行われます。  
  
 このシナリオでは、データベースに対してデータベース コマンド \(`INSERT` など\) を実行する必要はありません。  代わりに、オブジェクト モデル内で値を変更し、メソッドを実行します。  データベースに対してクエリを実行したり、変更を送信する必要がある場合、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、要求を正しい SQL コマンドに変換し、そのコマンドをデータベースに送信します。  
  
 ![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] オブジェクト モデル内の最も基本的な要素と、リレーショナル データ モデル内の要素との関係を、次の表に示します。  
  
|LINQ to SQL オブジェクト モデル|リレーショナル データ モデル|  
|----------------------------|---------------------|  
|エンティティ クラス|テーブル|  
|クラス メンバー|Column|  
|関連付け|外部キー リレーションシップ|  
|メソッド|ストアド プロシージャまたは関数|  
  
> [!NOTE]
>  次の説明は、リレーショナル データ モデルと規則に関する基本的な知識があることが前提です。  
  
## LINQ to SQL エンティティ クラスおよびデータベース テーブル  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、データベース テーブルは*エンティティ クラス*で表されます。  エンティティ クラスは、作成する他のクラスに似ていますが、クラスをデータベース テーブルに関連付ける特別な情報を使用して、クラスに注釈を付ける点が異なります。  次の例に示すように、クラス宣言にカスタム属性 \(<xref:System.Data.Linq.Mapping.TableAttribute>\) を追加することによって、この注釈を付けます。  
  
### 例  
 [!code-csharp[DLinqObjectModel#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#1)]
 [!code-vb[DLinqObjectModel#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#1)]  
  
 テーブルとして宣言されたクラスのインスタンスのみ \(つまり、エンティティ クラス\)、データベースに保存できます。  
  
 詳細については、「[Attribute\-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)」の「Table 属性」セクションを参照してください。  
  
## LINQ to SQL クラス メンバーおよびデータベース列  
 クラスとテーブルの関連付けに加えて、フィールドまたはプロパティを設定してデータベース列を表すことができます。  このためには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、次の例に示すように <xref:System.Data.Linq.Mapping.ColumnAttribute> 属性を定義します。  
  
### 例  
 [!code-csharp[DLinqObjectModel#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#2)]
 [!code-vb[DLinqObjectModel#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#2)]  
  
 列に対応付けられたフィールドおよびプロパティのみ、データベースに保持したり、データベースから取得できます。  列として宣言されていないものは、アプリケーション ロジックの一時的な部分と見なされます。  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute> 属性にはさまざまなプロパティがあり、これを使用することで、列を表すメンバーをカスタマイズできます \(たとえば、主キー列を表すメンバーを指定できます\)。  詳細については、「[Attribute\-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)」の「Column 属性」セクションを参照してください。  
  
## LINQ to SQL の関連付けおよびデータベースの外部キー リレーションシップ  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、<xref:System.Data.Linq.Mapping.AssociationAttribute> 属性を適用することによって、データベースの関連付け \(外部キーと主キーのリレーションシップなど\) を表します。  次のコード セグメントでは、`Order` クラスに `Customer` プロパティが含まれ、このプロパティが <xref:System.Data.Linq.Mapping.AssociationAttribute> 属性を持ちます。  このプロパティとその属性が、`Order` クラスおよび `Customer` クラスとのリレーションシップを提供します。  
  
 `Customer` クラスの `Order` プロパティを表示する方法を次の例に示します。  
  
### 例  
 [!code-csharp[DLinqObjectModel#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#3)]
 [!code-vb[DLinqObjectModel#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#3)]  
  
 詳細については、「[Attribute\-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)」の「Association 属性」セクションを参照してください。  
  
## LINQ to SQL メソッドおよびデータベース ストアド プロシージャ  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、ストアド プロシージャとユーザー定義関数をサポートしています。  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、これらのデータベース定義の概念をクライアント オブジェクトに対応付けることによって、クライアント コードから厳密に型指定された方法でのアクセスを実現しています。  メソッド シグネチャは、データベース内で定義されているプロシージャおよび関数のシグネチャと可能な限りよく似ています。  IntelliSense を使用して、これらのメソッドを見つけることができます。  
  
 呼び出しによって対応するプロシージャに返される結果セットは、厳密に型指定されたコレクションです。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、<xref:System.Data.Linq.Mapping.FunctionAttribute> 属性と <xref:System.Data.Linq.Mapping.ParameterAttribute> 属性を使用して、ストアド プロシージャおよび関数をメソッドに対応付けます。  ストアド プロシージャを表すメソッドは、<xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> プロパティによって、ユーザー定義関数を表すメソッドと区別されます。  このプロパティが `false` \(既定値\) に設定されている場合、メソッドはストアド プロシージャを表します。  `true` に設定されている場合、メソッドはデータベース関数を表します。  
  
> [!NOTE]
>  [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] を使用している場合は、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]を使用して、ストアド プロシージャおよびユーザー定義関数に対応付けられるメソッドを作成できます。  
  
### 例  
 [!code-csharp[DLinqObjectModel#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#4)]
 [!code-vb[DLinqObjectModel#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#4)]  
  
 詳細については、「[Attribute\-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)」 の「Function 属性」、「Stored Procedure 属性」、および「Parameter 属性」の各セクション、および「[Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)」を参照してください。  
  
## 参照  
 [Attribute\-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)   
 [Background Information](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)