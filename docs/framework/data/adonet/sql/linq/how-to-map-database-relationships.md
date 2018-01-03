---
title: "方法 : データベース リレーションシップを割り当てる"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 235c02d4f0030a6a5ecc22c83d6bcb24f32ccccf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-map-database-relationships"></a><span data-ttu-id="83a82-102">方法 : データベース リレーションシップを割り当てる</span><span class="sxs-lookup"><span data-stu-id="83a82-102">How to: Map Database Relationships</span></span>
<span data-ttu-id="83a82-103">データ リレーションシップが常に同じ場合は、これをエンティティ クラス内のプロパティ参照としてエンコードできます。</span><span class="sxs-lookup"><span data-stu-id="83a82-103">You can encode as property references in your entity class any data relationships that will always be the same.</span></span> <span data-ttu-id="83a82-104">たとえば、Northwind サンプル データベースでは、通常は顧客が注文を発注するため、モデルには、顧客と注文のリレーションシップが常に存在します。</span><span class="sxs-lookup"><span data-stu-id="83a82-104">In the Northwind sample database, for example, because customers typically place orders, there is always a relationship in the model between customers and their orders.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="83a82-105">定義、<xref:System.Data.Linq.Mapping.AssociationAttribute>のため、このようなリレーションシップを表す属性です。</span><span class="sxs-lookup"><span data-stu-id="83a82-105"> defines an <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute to help represent such relationships.</span></span> <span data-ttu-id="83a82-106">この属性を、<xref:System.Data.Linq.EntitySet%601> 型および <xref:System.Data.Linq.EntityRef%601> 型と共に使用することで、データベース内の外部キー リレーションシップが表されます。</span><span class="sxs-lookup"><span data-stu-id="83a82-106">This attribute is used together with the <xref:System.Data.Linq.EntitySet%601> and <xref:System.Data.Linq.EntityRef%601> types to represent what would be a foreign key relationship in a database.</span></span> <span data-ttu-id="83a82-107">詳細については、の「Association 属性」セクションを参照してください。[属性ベースの対応付け](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)です。</span><span class="sxs-lookup"><span data-stu-id="83a82-107">For more information, see the Association Attribute section of [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83a82-108">AssociationAttribute プロパティ値と ColumnAttribute Storage プロパティ値では大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="83a82-108">AssociationAttribute and ColumnAttribute Storage property values are case sensitive.</span></span> <span data-ttu-id="83a82-109">たとえば、AssociationAttribute.Storage  プロパティの属性に使用されている値は、コード内の別の場所で使用されている対応するプロパティ名と、大文字と小文字が一致するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="83a82-109">For example, ensure that values used in the attribute for the AssociationAttribute.Storage property match the case for the corresponding property names used elsewhere in the code.</span></span> <span data-ttu-id="83a82-110">これは、[!INCLUDE[vb_current_short](../../../../../../includes/vb-current-short-md.md)] など、通常は大文字と小文字が区別されない言語を含むすべての .NET プログラミング言語に適用されます。</span><span class="sxs-lookup"><span data-stu-id="83a82-110">This applies to all .NET programming languages, even those which are not typically case sensitive, including [!INCLUDE[vb_current_short](../../../../../../includes/vb-current-short-md.md)].</span></span> <span data-ttu-id="83a82-111">Storage プロパティの詳細については、「<xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83a82-111">For more information about the Storage property, see <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="83a82-112">ほとんどのリレーションシップは、このトピックの例のように、一対多のリレーションシップです。</span><span class="sxs-lookup"><span data-stu-id="83a82-112">Most relationships are one-to-many, as in the example later in this topic.</span></span> <span data-ttu-id="83a82-113">次に示すように、一対一および多対多のリレーションシップも表すことができます。</span><span class="sxs-lookup"><span data-stu-id="83a82-113">You can also represent one-to-one and many-to-many relationships as follows:</span></span>  
  
-   <span data-ttu-id="83a82-114">一対一 : 両側に <xref:System.Data.Linq.EntitySet%601> を指定することによって、この種類のリレーションシップを表します。</span><span class="sxs-lookup"><span data-stu-id="83a82-114">One-to-one: Represent this kind of relationship by including <xref:System.Data.Linq.EntitySet%601> on both sides.</span></span>  
  
     <span data-ttu-id="83a82-115">たとえば、 `Customer` - `SecurityCode`リレーションシップを作成できるように、お客様のセキュリティ コードは含まれない、`Customer`の表に、承認されたユーザーのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="83a82-115">For example, consider a `Customer`-`SecurityCode` relationship, created so that the customer's security code will not be found in the `Customer` table and can be accessed only by authorized persons.</span></span>  
  
-   <span data-ttu-id="83a82-116">多対多: 多対多リレーションシップのリンク テーブルの主キーで (とも呼ばれます、*分岐点*テーブル) の他の 2 つのテーブルから外部キーによって形成が多くの場合。</span><span class="sxs-lookup"><span data-stu-id="83a82-116">Many-to-many: In many-to-many relationships, the primary key of the link table (also named the *junction* table) is often formed by a composite of the foreign keys from the other two tables.</span></span>  
  
     <span data-ttu-id="83a82-117">たとえば、 `Employee` - `Project`リンク テーブルを使用して、多対多のリレーションシップが形成される`EmployeeProject`です。</span><span class="sxs-lookup"><span data-stu-id="83a82-117">For example, consider an `Employee`-`Project` many-to-many relationship formed by using link table `EmployeeProject`.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="83a82-118"> では、このようなリレーションシップを、`Employee`、`Project`、および `EmployeeProject` という 3 つのクラスを使用してモデル化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83a82-118"> requires that such a relationship be modeled by using three classes: `Employee`, `Project`, and `EmployeeProject`.</span></span> <span data-ttu-id="83a82-119">この場合、`Employee` と `Project` の間のリレーションシップを変更すると、主キーの `EmployeeProject` の更新が必要であるように見える可能性がありす。</span><span class="sxs-lookup"><span data-stu-id="83a82-119">In this case, changing the relationship between an `Employee` and a `Project` can appear to require an update of the primary key `EmployeeProject`.</span></span> <span data-ttu-id="83a82-120">ただし、この状態は、既存の `EmployeeProject` の削除、および新しい `EmployeeProject` の作成として適切にモデル化されます。</span><span class="sxs-lookup"><span data-stu-id="83a82-120">However, this situation is best modeled as deleting an existing `EmployeeProject` and the creating a new `EmployeeProject`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="83a82-121">リレーショナル データベース内のリレーションシップは、通常、他のテーブルの主キーを参照する外部キー値としてモデル化されます。</span><span class="sxs-lookup"><span data-stu-id="83a82-121">Relationships in relational databases are typically modeled as foreign key values that refer to primary keys in other tables.</span></span> <span data-ttu-id="83a82-122">それらの間を移動するを明示的に 2 つのテーブルを使用して関連付けるリレーショナル*結合*操作します。</span><span class="sxs-lookup"><span data-stu-id="83a82-122">To navigate between them you explicitly associate the two tables by using a relational *join* operation.</span></span>  
    >   
    >  <span data-ttu-id="83a82-123">内のオブジェクト[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、別のに対して、プロパティ参照または参照を使用して移動のコレクションを使用して相互に参照*ドット*表記します。</span><span class="sxs-lookup"><span data-stu-id="83a82-123">Objects in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], on the other hand, refer to each other by using property references or collections of references that you navigate by using *dot* notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83a82-124">例</span><span class="sxs-lookup"><span data-stu-id="83a82-124">Example</span></span>  
 <span data-ttu-id="83a82-125">次の一対多の例では、`Customer` クラスは、顧客とその注文のリレーションシップを宣言するプロパティを持ちます。</span><span class="sxs-lookup"><span data-stu-id="83a82-125">In the following one-to-many example, the `Customer` class has a property that declares the relationship between customers and their orders.</span></span>  <span data-ttu-id="83a82-126">`Orders` プロパティは <xref:System.Data.Linq.EntitySet%601> 型です。</span><span class="sxs-lookup"><span data-stu-id="83a82-126">The `Orders` property is of type <xref:System.Data.Linq.EntitySet%601>.</span></span> <span data-ttu-id="83a82-127">この型は、このリレーションシップが一対多 (1 人の顧客対多くの注文) であることを意味します。</span><span class="sxs-lookup"><span data-stu-id="83a82-127">This type signifies that this relationship is one-to-many (one customer to many orders).</span></span> <span data-ttu-id="83a82-128"><xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> プロパティを使用して、この関連付けを実現する方法を記述します。つまり、これと比較する、関連クラス内のプロパティの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="83a82-128">The <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> property is used to describe how this association is accomplished, namely, by specifying the name of the property in the related class to be compared with this one.</span></span> <span data-ttu-id="83a82-129">この例では、`CustomerID`データベースと同様、プロパティが比較*結合*その列の値を比較します。</span><span class="sxs-lookup"><span data-stu-id="83a82-129">In this example, the `CustomerID` property is compared, just as a database *join* would compare that column value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83a82-130">[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] を使用している場合は、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]を使用してクラス間の関連付けを作成できます。</span><span class="sxs-lookup"><span data-stu-id="83a82-130">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create an association between classes.</span></span>  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="83a82-131">例</span><span class="sxs-lookup"><span data-stu-id="83a82-131">Example</span></span>  
 <span data-ttu-id="83a82-132">逆の場合も可能です。</span><span class="sxs-lookup"><span data-stu-id="83a82-132">You can also reverse the situation.</span></span> <span data-ttu-id="83a82-133">`Customer` クラスを使用して顧客と注文の関連付けを記述するのではなく、`Order` クラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="83a82-133">Instead of using the `Customer` class to describe the association between customers and orders, you can use the `Order` class.</span></span> <span data-ttu-id="83a82-134">`Order` クラスは、<xref:System.Data.Linq.EntityRef%601> 型を使用して、次のコード例に示すように、顧客へのリレーションシップを記述できます。</span><span class="sxs-lookup"><span data-stu-id="83a82-134">The `Order` class uses the <xref:System.Data.Linq.EntityRef%601> type to describe the relationship back to the customer, as in the following code example.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83a82-135"><xref:System.Data.Linq.EntityRef%601>クラスでサポート*遅延読み込み*です。</span><span class="sxs-lookup"><span data-stu-id="83a82-135">The <xref:System.Data.Linq.EntityRef%601> class supports *deferred loading*.</span></span> <span data-ttu-id="83a82-136">詳細については、*を参照してください*[遅延実行と即時読み込み](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)です。</span><span class="sxs-lookup"><span data-stu-id="83a82-136">For more information, *see* [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="83a82-137">参照</span><span class="sxs-lookup"><span data-stu-id="83a82-137">See Also</span></span>  
 [<span data-ttu-id="83a82-138">方法 : コード エディターを使用してエンティティ クラスをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="83a82-138">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 [<span data-ttu-id="83a82-139">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="83a82-139">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
