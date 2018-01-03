---
title: "方法 : データベースを動的に作成する"
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
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 27986236c6b693b2c89157229cd79f0de64266e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-dynamically-create-a-database"></a><span data-ttu-id="46bae-102">方法 : データベースを動的に作成する</span><span class="sxs-lookup"><span data-stu-id="46bae-102">How to: Dynamically Create a Database</span></span>
<span data-ttu-id="46bae-103">LINQ to SQL では、オブジェクト モデルをリレーショナル データベースに対応付けます。</span><span class="sxs-lookup"><span data-stu-id="46bae-103">In LINQ to SQL, an object model is mapped to a relational database.</span></span> <span data-ttu-id="46bae-104">マッピングを有効化するには、属性ベースの対応付けか、リレーショナル データベースの構造を記述した外部マッピング ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="46bae-104">Mapping is enabled by using attribute-based mapping or an external mapping file to describe the structure of the relational database.</span></span> <span data-ttu-id="46bae-105">いずれの場合も、<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> メソッドを使用してデータベースの新しいインスタンスを作成するために必要な、リレーショナル データベースに関する十分な情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="46bae-105">In both scenarios, there is enough information about the relational database that you can create a new instance of the database using the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="46bae-106"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> メソッドで作成されるデータベースのレプリカには、オブジェクト モデル内でエンコードされる情報だけが格納されます。</span><span class="sxs-lookup"><span data-stu-id="46bae-106">The <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method creates a replica of the database only to the extent of the information encoded in the object model.</span></span> <span data-ttu-id="46bae-107">マッピング ファイルおよびオブジェクト モデルの属性では、既存のデータベースの構造のすべてがエンコードされるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="46bae-107">Mapping files and attributes from your object model might not encode everything about the structure of an existing database.</span></span> <span data-ttu-id="46bae-108">ユーザー定義関数、ストアド プロシージャ、トリガー、または CHECK 制約の内容は、マッピング ファイルでは表現されません。</span><span class="sxs-lookup"><span data-stu-id="46bae-108">Mapping information does not represent the contents of user-defined functions, stored procedures, triggers, or check constraints.</span></span> <span data-ttu-id="46bae-109">これは多くのデータベースにとって十分な動作です。</span><span class="sxs-lookup"><span data-stu-id="46bae-109">This behavior is sufficient for a variety of databases.</span></span>  
  
 <span data-ttu-id="46bae-110"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> メソッドはさまざまなシナリオで使用できますが、特に、Microsoft SQL Server 2008 などの既知のデータ プロバイダーを利用できる場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="46bae-110">You can use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method in any number of scenarios, especially if a known data provider like Microsoft SQL Server 2008 is available.</span></span> <span data-ttu-id="46bae-111">一般的なシナリオとして、次のようなものが考えられます。</span><span class="sxs-lookup"><span data-stu-id="46bae-111">Typical scenarios include the following:</span></span>  
  
-   <span data-ttu-id="46bae-112">顧客のシステムに自動的に自身をインストールするアプリケーションを作成している場合</span><span class="sxs-lookup"><span data-stu-id="46bae-112">You are building an application that automatically installs itself on a customer system.</span></span>  
  
-   <span data-ttu-id="46bae-113">オフライン状態を保存するためにローカル データベースを必要とするクライアント アプリケーションを作成している場合</span><span class="sxs-lookup"><span data-stu-id="46bae-113">You are building a client application that needs a local database to save its offline state.</span></span>  
  
 <span data-ttu-id="46bae-114">接続文字列で .mdf ファイルまたは単にカタログ名を使用することにより、SQL Server でも <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="46bae-114">You can also use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method with SQL Server by using an .mdf file or a catalog name, depending on your connection string.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="46bae-115"> は、接続文字列を使用して、作成するデータベースおよびデータベースの作成先となるサーバーを定義します。</span><span class="sxs-lookup"><span data-stu-id="46bae-115"> uses the connection string to define the database to be created and on which server the database is to be created.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46bae-116">可能な限り、データベースへの接続には Windows 統合セキュリティを使用してください。これにより、接続文字列にパスワードを含める必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="46bae-116">Whenever possible, use Windows Integrated Security to connect to the database so that passwords are not required in the connection string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46bae-117">例</span><span class="sxs-lookup"><span data-stu-id="46bae-117">Example</span></span>  
 <span data-ttu-id="46bae-118">次のコードは、MyDVDs.mdf という名前の新しいデータベースを作成する例です。</span><span class="sxs-lookup"><span data-stu-id="46bae-118">The following code provides an example of how to create a new database named MyDVDs.mdf.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="46bae-119">例</span><span class="sxs-lookup"><span data-stu-id="46bae-119">Example</span></span>  
 <span data-ttu-id="46bae-120">次のようにすると、オブジェクト モデルを使用してデータベースを作成できます。</span><span class="sxs-lookup"><span data-stu-id="46bae-120">You can use the object model to create a database by doing the following:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="46bae-121">例</span><span class="sxs-lookup"><span data-stu-id="46bae-121">Example</span></span>  
 <span data-ttu-id="46bae-122">顧客のシステムに自動的に自身をインストールするアプリケーションを作成している場合、新しいデータベースを作成する前に既存のデータベースがあるかどうかを確認して削除します。</span><span class="sxs-lookup"><span data-stu-id="46bae-122">When building an application that automatically installs itself on a  customer system, see if the database already exists and drop it before creating a new one.</span></span> <span data-ttu-id="46bae-123"><xref:System.Data.Linq.DataContext> クラスには、このプロセスに役立つ <xref:System.Data.Linq.DataContext.DatabaseExists%2A> メソッドと <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> メソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="46bae-123">The <xref:System.Data.Linq.DataContext> class provides the <xref:System.Data.Linq.DataContext.DatabaseExists%2A> and <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> methods to help you with this process.</span></span>  
  
 <span data-ttu-id="46bae-124">次の例は、これらのメソッドを使用してこの方法を実装する 1 つの方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="46bae-124">The following example shows one way these methods can be used to implement this approach:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="46bae-125">参照</span><span class="sxs-lookup"><span data-stu-id="46bae-125">See Also</span></span>  
 [<span data-ttu-id="46bae-126">属性ベースの対応付け</span><span class="sxs-lookup"><span data-stu-id="46bae-126">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [<span data-ttu-id="46bae-127">外部マップ</span><span class="sxs-lookup"><span data-stu-id="46bae-127">External Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [<span data-ttu-id="46bae-128">SQL と CLR の型マッピング</span><span class="sxs-lookup"><span data-stu-id="46bae-128">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [<span data-ttu-id="46bae-129">背景情報</span><span class="sxs-lookup"><span data-stu-id="46bae-129">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="46bae-130">データの変更と変更の送信</span><span class="sxs-lookup"><span data-stu-id="46bae-130">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
