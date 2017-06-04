---
title: "How to: Map Database Relationships | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# How to: Map Database Relationships
データ リレーションシップが常に同じ場合は、これをエンティティ クラス内のプロパティ参照としてエンコードできます。  たとえば、Northwind サンプル データベースでは、通常は顧客が注文を発注するため、モデルには、顧客と注文のリレーションシップが常に存在します。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、<xref:System.Data.Linq.Mapping.AssociationAttribute> 属性を定義して、このようなリレーションシップを表します。  この属性を、<xref:System.Data.Linq.EntitySet%601> 型および <xref:System.Data.Linq.EntityRef%601> 型と共に使用することで、データベース内の外部キー リレーションシップが表されます。詳細については、「[Attribute\-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)」の「Association 属性」セクションを参照してください。  
  
> [!NOTE]
>  AssociationAttribute プロパティ値と ColumnAttribute Storage プロパティ値では大文字と小文字が区別されます。  たとえば、AssociationAttribute.Storage  プロパティの属性に使用されている値は、コード内の別の場所で使用されている対応するプロパティ名と、大文字と小文字が一致するようにしてください。  これは、[!INCLUDE[vb_current_short](../../../../../../includes/vb-current-short-md.md)] など、通常は大文字と小文字が区別されない言語を含むすべての .NET プログラミング言語に適用されます。  Storage プロパティの詳細については、「<xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=fullName>」を参照してください。  
  
 ほとんどのリレーションシップは、このトピックの例のように、一対多のリレーションシップです。  次に示すように、一対一および多対多のリレーションシップも表すことができます。  
  
-   一対一 : 両側に <xref:System.Data.Linq.EntitySet%601> を指定することによって、この種類のリレーションシップを表します。  
  
     たとえば、顧客のセキュリティ コードが `Customer` テーブルには表示されず、承認されたユーザーのみがアクセスできるようにするために作成された、`SecurityCode`\-`Customer` リレーションシップがその例です。  
  
-   多対多 : 多対多リレーションシップでは、リンク テーブル \(*結合*テーブルともいいます\) の主キーは、多くの場合、他の 2 つのテーブルの外部キーが結合して作成されます。  
  
     たとえば、リンク テーブル `Employee` を使用して作成される `Project`\-`EmployeeProject` という多対多リレーションシップがあるとします。  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、このようなリレーションシップを、`Employee`、`Project`、および `EmployeeProject` という 3 つのクラスを使用してモデル化する必要があります。  この場合、`Employee` と `Project` の間のリレーションシップを変更すると、主キーの `EmployeeProject` の更新が必要であるように見える可能性がありす。  ただし、この状態は、既存の `EmployeeProject` の削除、および新しい `EmployeeProject` の作成として適切にモデル化されます。  
  
    > [!NOTE]
    >  リレーショナル データベース内のリレーションシップは、通常、他のテーブルの主キーを参照する外部キー値としてモデル化されます。  それらの間を移動するには、リレーショナル*結合*演算を使用して、2 つのテーブルを明示的に関連付けます。  
    >   
    >  これに対して、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 内のオブジェクトは、*ドット*表記を使用して移動するプロパティ参照または参照のコレクションを使用して、互いを参照します。  
  
## 使用例  
 次の一対多の例では、`Customer` クラスは、顧客とその注文のリレーションシップを宣言するプロパティを持ちます。  `Orders` プロパティは <xref:System.Data.Linq.EntitySet%601> 型です。  この型は、このリレーションシップが一対多 \(1 人の顧客対多くの注文\) であることを意味します。  <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> プロパティを使用して、この関連付けを実現する方法を記述します。つまり、これと比較する、関連クラス内のプロパティの名前を指定します。  この例では、データベース`CustomerID`結合がその列値を比較するときに、 *プロパティが比較されます。*  
  
> [!NOTE]
>  [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] を使用している場合は、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]を使用してクラス間の関連付けを作成できます。  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## 使用例  
 逆の場合も可能です。  `Customer` クラスを使用して顧客と注文の関連付けを記述するのではなく、`Order` クラスを使用できます。  `Order` クラスは、<xref:System.Data.Linq.EntityRef%601> 型を使用して、次のコード例に示すように、顧客へのリレーションシップを記述できます。  
  
> [!NOTE]
>  <xref:System.Data.Linq.EntityRef%601> クラスは、*遅延読み込み*をサポートします。  詳細については、*「*[Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)」を参照してください。  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## 参照  
 [How to: Customize Entity Classes by Using the Code Editor](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)   
 [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)