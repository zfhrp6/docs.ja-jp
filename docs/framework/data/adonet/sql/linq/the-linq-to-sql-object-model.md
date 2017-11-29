---
title: "LINQ to SQL オブジェクト モデル"
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
ms.assetid: 81dd0c37-e2a4-4694-83b0-f2e49e693810
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 30231ea756e80ddeac087fa8b3e46664860c26a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="the-linq-to-sql-object-model"></a><span data-ttu-id="435f7-102">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="435f7-102">The LINQ to SQL Object Model</span></span>
<span data-ttu-id="435f7-103">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]開発者のプログラミング言語で表されるオブジェクト モデルは、リレーショナル データベースのデータ モデルにマップします。</span><span class="sxs-lookup"><span data-stu-id="435f7-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model expressed in the programming language of the developer is mapped to the data model of a relational database.</span></span> <span data-ttu-id="435f7-104">データ操作はオブジェクト モデルに従って行われます。</span><span class="sxs-lookup"><span data-stu-id="435f7-104">Operations on the data are then conducted according to the object model.</span></span>  
  
 <span data-ttu-id="435f7-105">このシナリオでは、データベースに対してデータベース コマンド (`INSERT` など) を実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="435f7-105">In this scenario, you do not issue database commands (for example, `INSERT`) to the database.</span></span> <span data-ttu-id="435f7-106">代わりに、オブジェクト モデル内で値を変更し、メソッドを実行します。</span><span class="sxs-lookup"><span data-stu-id="435f7-106">Instead, you change values and execute methods within your object model.</span></span> <span data-ttu-id="435f7-107">データベースに対してクエリを実行したり、変更を送信する必要がある場合、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、要求を正しい SQL コマンドに変換し、そのコマンドをデータベースに送信します。</span><span class="sxs-lookup"><span data-stu-id="435f7-107">When you want to query the database or send it changes, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates your requests into the correct SQL commands and sends those commands to the database.</span></span>  
  
 <span data-ttu-id="435f7-108">![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")</span><span class="sxs-lookup"><span data-stu-id="435f7-108">![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")</span></span>  
  
 <span data-ttu-id="435f7-109">内の最も基本的な要素、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]オブジェクト モデルとリレーショナル データ モデル内の要素との関係は次の表に概要を示します。</span><span class="sxs-lookup"><span data-stu-id="435f7-109">The most fundamental elements in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model and their relationship to elements in the relational data model are summarized in the following table:</span></span>  
  
|<span data-ttu-id="435f7-110">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="435f7-110">LINQ to SQL Object Model</span></span>|<span data-ttu-id="435f7-111">リレーショナル データ モデル</span><span class="sxs-lookup"><span data-stu-id="435f7-111">Relational Data Model</span></span>|  
|------------------------------|---------------------------|  
|<span data-ttu-id="435f7-112">エンティティ クラス</span><span class="sxs-lookup"><span data-stu-id="435f7-112">Entity class</span></span>|<span data-ttu-id="435f7-113">テーブル</span><span class="sxs-lookup"><span data-stu-id="435f7-113">Table</span></span>|  
|<span data-ttu-id="435f7-114">クラス メンバー</span><span class="sxs-lookup"><span data-stu-id="435f7-114">Class member</span></span>|<span data-ttu-id="435f7-115">Column</span><span class="sxs-lookup"><span data-stu-id="435f7-115">Column</span></span>|  
|<span data-ttu-id="435f7-116">関連付け</span><span class="sxs-lookup"><span data-stu-id="435f7-116">Association</span></span>|<span data-ttu-id="435f7-117">外部キー リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="435f7-117">Foreign-key relationship</span></span>|  
|<span data-ttu-id="435f7-118">メソッド</span><span class="sxs-lookup"><span data-stu-id="435f7-118">Method</span></span>|<span data-ttu-id="435f7-119">ストアド プロシージャまたは関数</span><span class="sxs-lookup"><span data-stu-id="435f7-119">Stored Procedure or Function</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="435f7-120">次の説明は、リレーショナル データ モデルと規則に関する基本的な知識があることが前提です。</span><span class="sxs-lookup"><span data-stu-id="435f7-120">The following descriptions assume that you have a basic knowledge of the relational data model and rules.</span></span>  
  
## <a name="linq-to-sql-entity-classes-and-database-tables"></a><span data-ttu-id="435f7-121">LINQ to SQL エンティティ クラスおよびデータベース テーブル</span><span class="sxs-lookup"><span data-stu-id="435f7-121">LINQ to SQL Entity Classes and Database Tables</span></span>  
 <span data-ttu-id="435f7-122">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、データベース テーブルで表現され、*エンティティ クラス*です。</span><span class="sxs-lookup"><span data-stu-id="435f7-122">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a database table is represented by an *entity class*.</span></span> <span data-ttu-id="435f7-123">エンティティ クラスは、作成する他のクラスに似ていますが、クラスをデータベース テーブルに関連付ける特別な情報を使用して、クラスに注釈を付ける点が異なります。</span><span class="sxs-lookup"><span data-stu-id="435f7-123">An entity class is like any other class you might create except that you annotate the class by using special information that associates the class with a database table.</span></span> <span data-ttu-id="435f7-124">次の例に示すように、クラス宣言にカスタム属性 (<xref:System.Data.Linq.Mapping.TableAttribute>) を追加することによって、この注釈を付けます。</span><span class="sxs-lookup"><span data-stu-id="435f7-124">You make this annotation by adding a custom attribute (<xref:System.Data.Linq.Mapping.TableAttribute>) to your class declaration, as in the following example:</span></span>  
  
### <a name="example"></a><span data-ttu-id="435f7-125">例</span><span class="sxs-lookup"><span data-stu-id="435f7-125">Example</span></span>  
 [!code-csharp[DLinqObjectModel#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#1)]
 [!code-vb[DLinqObjectModel#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#1)]  
  
 <span data-ttu-id="435f7-126">テーブルとして宣言されたクラスのインスタンスのみ (つまり、エンティティ クラス)、データベースに保存できます。</span><span class="sxs-lookup"><span data-stu-id="435f7-126">Only instances of classes declared as tables (that is, entity classes) can be saved to the database.</span></span>  
  
 <span data-ttu-id="435f7-127">詳細については、テーブルの属性の参照[属性ベースの対応付け](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)です。</span><span class="sxs-lookup"><span data-stu-id="435f7-127">For more information, see the Table Attribute section of [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
## <a name="linq-to-sql-class-members-and-database-columns"></a><span data-ttu-id="435f7-128">LINQ to SQL クラス メンバーおよびデータベース列</span><span class="sxs-lookup"><span data-stu-id="435f7-128">LINQ to SQL Class Members and Database Columns</span></span>  
 <span data-ttu-id="435f7-129">クラスとテーブルの関連付けに加えて、フィールドまたはプロパティを設定してデータベース列を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="435f7-129">In addition to associating classes with tables, you designate fields or properties to represent database columns.</span></span> <span data-ttu-id="435f7-130">このためには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、次の例に示すように <xref:System.Data.Linq.Mapping.ColumnAttribute> 属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="435f7-130">For this purpose, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] defines the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute, as in the following example:</span></span>  
  
### <a name="example"></a><span data-ttu-id="435f7-131">例</span><span class="sxs-lookup"><span data-stu-id="435f7-131">Example</span></span>  
 [!code-csharp[DLinqObjectModel#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#2)]
 [!code-vb[DLinqObjectModel#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#2)]  
  
 <span data-ttu-id="435f7-132">列に対応付けられたフィールドおよびプロパティのみ、データベースに保持したり、データベースから取得できます。</span><span class="sxs-lookup"><span data-stu-id="435f7-132">Only fields and properties mapped to columns are persisted to or retrieved from the database.</span></span> <span data-ttu-id="435f7-133">列として宣言されていないものは、アプリケーション ロジックの一時的な部分と見なされます。</span><span class="sxs-lookup"><span data-stu-id="435f7-133">Those not declared as columns are considered as transient parts of your application logic.</span></span>  
  
 <span data-ttu-id="435f7-134"><xref:System.Data.Linq.Mapping.ColumnAttribute> 属性にはさまざまなプロパティがあり、これを使用することで、列を表すメンバーをカスタマイズできます (たとえば、主キー列を表すメンバーを指定できます)。</span><span class="sxs-lookup"><span data-stu-id="435f7-134">The <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute has a variety of properties that you can use to customize these members that represent columns (for example, designating a member as representing a primary key column).</span></span> <span data-ttu-id="435f7-135">詳細についてを参照してください、列の属性の[属性ベースの対応付け](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)です。</span><span class="sxs-lookup"><span data-stu-id="435f7-135">For more information, see the Column Attribute section of [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
## <a name="linq-to-sql-associations-and-database-foreign-key-relationships"></a><span data-ttu-id="435f7-136">LINQ to SQL の関連付けおよびデータベースの外部キー リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="435f7-136">LINQ to SQL Associations and Database Foreign-key Relationships</span></span>  
 <span data-ttu-id="435f7-137">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、適用することによってデータベースの関連付け (外部キーと主キーのリレーションシップ) などを表す、<xref:System.Data.Linq.Mapping.AssociationAttribute>属性。</span><span class="sxs-lookup"><span data-stu-id="435f7-137">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you represent database associations (such as foreign-key to primary-key relationships) by applying the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span> <span data-ttu-id="435f7-138">次のコードのセグメントで、`Order`クラスが含まれています、`Customer`プロパティを持つ、<xref:System.Data.Linq.Mapping.AssociationAttribute>属性。</span><span class="sxs-lookup"><span data-stu-id="435f7-138">In the following segment of code, the `Order` class contains a `Customer` property that has an <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span> <span data-ttu-id="435f7-139">このプロパティとその属性が、`Order` クラスおよび `Customer` クラスとのリレーションシップを提供します。</span><span class="sxs-lookup"><span data-stu-id="435f7-139">This property and its attribute provide the `Order` class with a relationship to the `Customer` class.</span></span>  
  
 <span data-ttu-id="435f7-140">`Customer` クラスの `Order` プロパティを表示する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="435f7-140">The following code example shows the `Customer` property from the `Order` class.</span></span>  
  
### <a name="example"></a><span data-ttu-id="435f7-141">例</span><span class="sxs-lookup"><span data-stu-id="435f7-141">Example</span></span>  
 [!code-csharp[DLinqObjectModel#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#3)]
 [!code-vb[DLinqObjectModel#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#3)]  
  
 <span data-ttu-id="435f7-142">詳細については、の「Association 属性」セクションを参照してください。[属性ベースの対応付け](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)です。</span><span class="sxs-lookup"><span data-stu-id="435f7-142">For more information, see the Association Attribute section of [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
## <a name="linq-to-sql-methods-and-database-stored-procedures"></a><span data-ttu-id="435f7-143">LINQ to SQL メソッドおよびデータベース ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="435f7-143">LINQ to SQL Methods and Database Stored Procedures</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="435f7-144"> は、ストアド プロシージャとユーザー定義関数をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="435f7-144"> supports stored procedures and user-defined functions.</span></span> <span data-ttu-id="435f7-145">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、それらをクライアント コードから厳密に型指定された方法でアクセスできるようにするクライアント オブジェクトにこれらのデータベースの定義済みの抽象化をマップします。</span><span class="sxs-lookup"><span data-stu-id="435f7-145">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you map these database-defined abstractions to client objects so that you can access them in a strongly typed manner from client code.</span></span> <span data-ttu-id="435f7-146">メソッド シグネチャは、データベース内で定義されているプロシージャおよび関数のシグネチャと可能な限りよく似ています。</span><span class="sxs-lookup"><span data-stu-id="435f7-146">The method signatures resemble as closely as possible the signatures of the procedures and functions defined in the database.</span></span> <span data-ttu-id="435f7-147">IntelliSense を使用して、これらのメソッドを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="435f7-147">You can use IntelliSense to discover these methods.</span></span>  
  
 <span data-ttu-id="435f7-148">呼び出しによって対応するプロシージャに返される結果セットは、厳密に型指定されたコレクションです。</span><span class="sxs-lookup"><span data-stu-id="435f7-148">A result set that is returned by a call to a mapped procedure is a strongly typed collection.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="435f7-149"> は、<xref:System.Data.Linq.Mapping.FunctionAttribute> 属性と <xref:System.Data.Linq.Mapping.ParameterAttribute> 属性を使用して、ストアド プロシージャおよび関数をメソッドに対応付けます。</span><span class="sxs-lookup"><span data-stu-id="435f7-149"> maps stored procedures and functions to methods by using the <xref:System.Data.Linq.Mapping.FunctionAttribute> and <xref:System.Data.Linq.Mapping.ParameterAttribute> attributes.</span></span> <span data-ttu-id="435f7-150">ストアド プロシージャを表すメソッドは、<xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> プロパティによって、ユーザー定義関数を表すメソッドと区別されます。</span><span class="sxs-lookup"><span data-stu-id="435f7-150">Methods representing stored procedures are distinguished from those representing user-defined functions by the <xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> property.</span></span> <span data-ttu-id="435f7-151">このプロパティが `false` (既定値) に設定されている場合、メソッドはストアド プロシージャを表します。</span><span class="sxs-lookup"><span data-stu-id="435f7-151">If this property is set to `false` (the default), the method represents a stored procedure.</span></span> <span data-ttu-id="435f7-152">`true` に設定されている場合、メソッドはデータベース関数を表します。</span><span class="sxs-lookup"><span data-stu-id="435f7-152">If it is set to `true`, the method represents a database function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="435f7-153">[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] を使用している場合は、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]を使用して、ストアド プロシージャおよびユーザー定義関数に対応付けられるメソッドを作成できます。</span><span class="sxs-lookup"><span data-stu-id="435f7-153">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create methods mapped to stored procedures and user-defined functions.</span></span>  
  
### <a name="example"></a><span data-ttu-id="435f7-154">例</span><span class="sxs-lookup"><span data-stu-id="435f7-154">Example</span></span>  
 [!code-csharp[DLinqObjectModel#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#4)]
 [!code-vb[DLinqObjectModel#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#4)]  
  
 <span data-ttu-id="435f7-155">詳細については、の関数の属性、Stored Procedure 属性およびパラメーターの属性のセクションを参照してください。[属性ベースの対応付け](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)と[Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="435f7-155">For more information, see the Function Attribute, Stored Procedure Attribute, and Parameter Attribute sections of [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md) and [Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="435f7-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="435f7-156">See Also</span></span>  
 [<span data-ttu-id="435f7-157">属性ベースのマッピング</span><span class="sxs-lookup"><span data-stu-id="435f7-157">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [<span data-ttu-id="435f7-158">背景情報</span><span class="sxs-lookup"><span data-stu-id="435f7-158">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
