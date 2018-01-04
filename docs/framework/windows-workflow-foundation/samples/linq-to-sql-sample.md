---
title: "LINQ to SQL のサンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f39db9e-0e62-42c9-8c98-bb8b54cec98c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 06273f3ac7dd159adac4c058a23c187f44417d94
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="linq-to-sql-sample"></a><span data-ttu-id="51126-102">LINQ to SQL のサンプル</span><span class="sxs-lookup"><span data-stu-id="51126-102">LINQ to SQL Sample</span></span>
<span data-ttu-id="51126-103">このサンプルでは、SQL Server データベース内のテーブルの LINQ to SQL クエリ エンティティを使用するアクティビティを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="51126-103">This sample demonstrates how to create an activity to use LINQ to SQL query entities from tables in SQL Server databases.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="51126-104">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="51126-104">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples may already be installed on your machine.</span></span> <span data-ttu-id="51126-105">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="51126-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\Samples\WCFWFCardspace`  
>   
>  <span data-ttu-id="51126-106">このディレクトリが存在しない場合は、このページの上部にあるサンプルのダウンロードのリンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="51126-106">If this directory does not exist, click the download sample link at the top of this page.</span></span> <span data-ttu-id="51126-107">このリンクをクリックすると、[!INCLUDE[wf1](../../../../includes/wf1-md.md)]、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]、および [!INCLUDE[infocard](../../../../includes/infocard-md.md)] のサンプルがすべてダウンロードおよびインストールされます。</span><span class="sxs-lookup"><span data-stu-id="51126-107">Note that this link downloads and installs all of the [!INCLUDE[wf1](../../../../includes/wf1-md.md)], [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], and [!INCLUDE[infocard](../../../../includes/infocard-md.md)] samples.</span></span> <span data-ttu-id="51126-108">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="51126-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\Samples\WCFWFCardSpace\WF\Scenario\ActivityLibrary\Linq\LinqToSql`  
  
## <a name="activity-details-for-findinsqltable"></a><span data-ttu-id="51126-109">FindInSqlTable のアクティビティの詳細</span><span class="sxs-lookup"><span data-stu-id="51126-109">Activity details for FindInSqlTable</span></span>  
 <span data-ttu-id="51126-110">このアクティビティでは、LINQ to SQL を使用してデータベース内のテーブルのエンティティに対してクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="51126-110">This activity allows users to query entities from tables in a database using LINQ to SQL.</span></span> <span data-ttu-id="51126-111">アクティビティのユーザーは、LINQ 述語をラムダ式のフォームで指定して、結果をフィルター処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="51126-111">Users of the activity can also provide a LINQ predicate in the form of a lambda expression to filter the results.</span></span> <span data-ttu-id="51126-112">述語を指定しない場合、テーブル全体が返されます。</span><span class="sxs-lookup"><span data-stu-id="51126-112">If no predicate is provided, the entire table is returned.</span></span> <span data-ttu-id="51126-113">次の表で、アクティビティのプロパティと戻り値について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="51126-113">The following table details the property and return values for the activity.</span></span>  
  
|<span data-ttu-id="51126-114">プロパティ値または戻り値</span><span class="sxs-lookup"><span data-stu-id="51126-114">Property or Return Value</span></span>|<span data-ttu-id="51126-115">説明</span><span class="sxs-lookup"><span data-stu-id="51126-115">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="51126-116">`Collection` プロパティ</span><span class="sxs-lookup"><span data-stu-id="51126-116">`Collection` property</span></span>|<span data-ttu-id="51126-117">ソース コレクションを指定する必須のプロパティ</span><span class="sxs-lookup"><span data-stu-id="51126-117">A required property that specifies the source collection.</span></span>|  
|<span data-ttu-id="51126-118">`Predicate` プロパティ</span><span class="sxs-lookup"><span data-stu-id="51126-118">`Predicate` property</span></span>|<span data-ttu-id="51126-119">コレクションのフィルターをラムダ式のフォームで指定する必須のプロパティ</span><span class="sxs-lookup"><span data-stu-id="51126-119">A required property that specifies the filter for the collection in the form of a lambda expression.</span></span>|  
|<span data-ttu-id="51126-120">戻り値</span><span class="sxs-lookup"><span data-stu-id="51126-120">Return Value</span></span>|<span data-ttu-id="51126-121">フィルター処理されたコレクション</span><span class="sxs-lookup"><span data-stu-id="51126-121">The filtered collection.</span></span>|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a><span data-ttu-id="51126-122">カスタム アクティビティを使用するコード サンプル</span><span class="sxs-lookup"><span data-stu-id="51126-122">Code Sample that uses the Custom Activity</span></span>  
 <span data-ttu-id="51126-123">`FindInSqlTable` カスタム アクティビティを使用して、`Employee` という名前の SQL Server テーブルで `Role` 列が `SDE` になっている行をすべて検索するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="51126-123">The following code example uses the `FindInSqlTable` custom activity to find all rows in a SQL Server table named `Employee` where the `Role` column is equal to `SDE`.</span></span>  
  
```csharp  
new FindInSqlTable<Employee>   
{  
    ConnectionString = @"Data Source=.\SQLExpress;Initial Catalog=LinqToSqlSample;Integrated Security=True",                          
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(emp => emp.Role.Equals("SDE"))),  
    Result = new OutArgument<IList<Employee>>(employees)  
},  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="51126-124">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="51126-124">To use this sample</span></span>  
  
1.  <span data-ttu-id="51126-125">コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="51126-125">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="51126-126">このサンプルが含まれるフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="51126-126">Navigate to the folder that contains this sample.</span></span>  
  
3.  <span data-ttu-id="51126-127">Setup.cmd コマンド ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="51126-127">Run the Setup.cmd command file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="51126-128">Setup.cmd スクリプトは、ローカル コンピューターに SQL Server Express のサンプル データベースをインストールしようとします。</span><span class="sxs-lookup"><span data-stu-id="51126-128">The Setup.cmd script attempts to install the sample database in your local machine SQL Server Express.</span></span> <span data-ttu-id="51126-129">他の SQL Server インスタンスにインストールする場合は、Setup.cmd を編集します。</span><span class="sxs-lookup"><span data-stu-id="51126-129">If you want to install it in other SQL server instance, edit Setup.cmd.</span></span>  
  
     <span data-ttu-id="51126-130">Setup.cmd スクリプトでは、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="51126-130">The Setup.cmd script does the following actions.:</span></span>  
  
    -   <span data-ttu-id="51126-131">LinqToSqlSample という名前のデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="51126-131">Creates a database called LinqToSqlSample.</span></span>  
  
    -   <span data-ttu-id="51126-132">Roles テーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="51126-132">Creates a Roles table.</span></span>  
  
    -   <span data-ttu-id="51126-133">Employees テーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="51126-133">Creates an Employees table.</span></span>  
  
    -   <span data-ttu-id="51126-134">3 個のレコードを Roles テーブルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="51126-134">Inserts 3 records into the Roles table.</span></span>  
  
    -   <span data-ttu-id="51126-135">12 個のレコードを Employees テーブルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="51126-135">Inserts 12 records into the Employees table.</span></span>  
  
4.  <span data-ttu-id="51126-136">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、LinqToSQL.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="51126-136">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the LinqToSQL.sln solution file.</span></span>  
  
5.  <span data-ttu-id="51126-137">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="51126-137">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
6.  <span data-ttu-id="51126-138">ソリューションを実行するには、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="51126-138">To run the solution, press F5.</span></span>  
  
#### <a name="to-uninstall-the-linqtosql-sample-database"></a><span data-ttu-id="51126-139">LinqToSql サンプル データベースをアンインストールするには</span><span class="sxs-lookup"><span data-stu-id="51126-139">To uninstall the LinqToSql sample database</span></span>  
  
1.  <span data-ttu-id="51126-140">コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="51126-140">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="51126-141">このサンプルが含まれるフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="51126-141">Navigate to the folder that contains this sample.</span></span>  
  
3.  <span data-ttu-id="51126-142">Cleanup.cmd コマンド ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="51126-142">Run the Cleanup.cmd command file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="51126-143">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="51126-143">The samples may already be installed on your machine.</span></span> <span data-ttu-id="51126-144">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="51126-144">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="51126-145">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="51126-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="51126-146">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="51126-146">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Liiinq\LinqToSql`  
  
## <a name="see-also"></a><span data-ttu-id="51126-147">参照</span><span class="sxs-lookup"><span data-stu-id="51126-147">See Also</span></span>  
 [<span data-ttu-id="51126-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="51126-148">LINQ to SQL</span></span>](http://go.microsoft.com/fwlink/?LinkId=150376)  
 [<span data-ttu-id="51126-149">はじめに (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="51126-149">Getting Started (LINQ to SQL)</span></span>](http://go.microsoft.com/fwlink/?LinkId=150377)
