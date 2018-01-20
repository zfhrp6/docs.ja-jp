---
title: "データ定義言語の操作"
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
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: dc2642df7cfe0f0a4b56537d0b2ebeae34304145
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="working-with-data-definition-language"></a><span data-ttu-id="30706-102">データ定義言語の操作</span><span class="sxs-lookup"><span data-stu-id="30706-102">Working with Data Definition Language</span></span>
<span data-ttu-id="30706-103">以降で、[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]バージョン 4、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]データ定義言語 (DDL) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="30706-103">Starting with the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] version 4, the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] supports data definition language (DDL).</span></span> <span data-ttu-id="30706-104">これにより、接続文字列、およびストレージ (SSDL) モデルのメターデータに基づいて、データベース インスタンスを作成または削除できます。</span><span class="sxs-lookup"><span data-stu-id="30706-104">This allows you to create or delete a database instance based on the connection string and the metadata of the storage (SSDL) model.</span></span>  
  
 <span data-ttu-id="30706-105"><xref:System.Data.Objects.ObjectContext> の次のメソッドでは、接続文字列と SSDL の内容を使用して、データベースの作成と削除、データベースが存在するかどうかの確認、生成された DDL スクリプトの表示を実行します。</span><span class="sxs-lookup"><span data-stu-id="30706-105">The following methods on the <xref:System.Data.Objects.ObjectContext> use the connection string and the SSDL content to accomplish the following: create or delete the database, check whether the database exists, and view the generated DDL script:</span></span>  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
>  <span data-ttu-id="30706-106">DDL コマンドを実行するには、十分なアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="30706-106">Executing the DDL commands assumes sufficient permissions.</span></span>  
  
 <span data-ttu-id="30706-107">上記に示したメソッドは、ほとんどの作業を基になる ADO.NET データ プロバイダーに委任します。</span><span class="sxs-lookup"><span data-stu-id="30706-107">The methods previously listed delegate most of the work to the underlying ADO.NET data provider.</span></span> <span data-ttu-id="30706-108">データベース オブジェクトの生成に使用される名前付け規則が、照会および更新に使用される規則と一致していることは、プロバイダーによって保証されています。</span><span class="sxs-lookup"><span data-stu-id="30706-108">It is the provider’s responsibility to ensure that the naming convention used to generate database objects is consistent with conventions used for querying and updates.</span></span>  
  
 <span data-ttu-id="30706-109">次の例は、既存のモデルを基にデータベースを生成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="30706-109">The following example shows you how to generate the database based on the existing model.</span></span> <span data-ttu-id="30706-110">また、新しいエンティティ オブジェクトはオブジェクト コンテキストに追加され、データベースに保存されます。</span><span class="sxs-lookup"><span data-stu-id="30706-110">It also adds a new entity object to the object context and then saves it to the database.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="30706-111">手順</span><span class="sxs-lookup"><span data-stu-id="30706-111">Procedures</span></span>  
  
#### <a name="to-define-a-database-based-on-the-existing-model"></a><span data-ttu-id="30706-112">既存のモデルに基づいてデータベースを定義するには</span><span class="sxs-lookup"><span data-stu-id="30706-112">To define a database based on the existing model</span></span>  
  
1.  <span data-ttu-id="30706-113">コンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="30706-113">Create a console application.</span></span>  
  
2.  <span data-ttu-id="30706-114">既存のモデルをアプリケーションに追加します。</span><span class="sxs-lookup"><span data-stu-id="30706-114">Add an existing model to your application.</span></span>  
  
    1.  <span data-ttu-id="30706-115">空のモデル名を追加`SchoolModel`です。</span><span class="sxs-lookup"><span data-stu-id="30706-115">Add an empty model named `SchoolModel`.</span></span> <span data-ttu-id="30706-116">空のモデルを作成するを参照してください。、[する方法: 新しい .edmx ファイルを作成する](http://msdn.microsoft.com/library/beb8189e-e51c-4051-839c-9902c224abf2)トピックです。</span><span class="sxs-lookup"><span data-stu-id="30706-116">To create an empty model, see the [How to: Create a New .edmx File](http://msdn.microsoft.com/library/beb8189e-e51c-4051-839c-9902c224abf2) topic.</span></span>  
  
     <span data-ttu-id="30706-117">SchoolModel.edmx ファイルがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="30706-117">The SchoolModel.edmx file is added to your project.</span></span>  
  
    1.  <span data-ttu-id="30706-118">概念、記憶域をコピーしてから School モデルのコンテンツのマッピング、 [School モデル](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac)トピックです。</span><span class="sxs-lookup"><span data-stu-id="30706-118">Copy the conceptual, storage, and mapping content for the School model from the [School Model](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) topic.</span></span>  
  
    2.  <span data-ttu-id="30706-119">SchoolModel.edmx ファイルを開き、`edmx:Runtime` タグ内にその内容を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="30706-119">Open the SchoolModel.edmx file and paste the content within the `edmx:Runtime` tags.</span></span>  
  
3.  <span data-ttu-id="30706-120">main 関数に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="30706-120">Add the following code to your main function.</span></span> <span data-ttu-id="30706-121">このコードでは、データベース サーバーへの接続文字列を初期化し、DDL スクリプトを表示して、データベースを作成します。さらに、コンテキストに新しいエンティティを追加して、データベースに変更内容を保存します。</span><span class="sxs-lookup"><span data-stu-id="30706-121">The code initializes the connection string to your database server, views the DDL script, creates the database, adds a new entity to the context, and saves the changes to the database.</span></span>  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
