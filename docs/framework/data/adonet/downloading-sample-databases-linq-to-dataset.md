---
title: サンプル データベースのダウンロード (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
ms.openlocfilehash: f2488b0e1bfc578679a2a2802c332439f374a341
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763054"
---
# <a name="downloading-sample-databases-linq-to-dataset"></a><span data-ttu-id="9a0fe-102">サンプル データベースのダウンロード (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="9a0fe-102">Downloading Sample Databases (LINQ to DataSet)</span></span>
<span data-ttu-id="9a0fe-103">サンプルおよびチュートリアルでは、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]ドキュメントは、AdventureWorks サンプル データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-103">The samples and walkthroughs in the [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] documentation use the AdventureWorks sample database.</span></span> <span data-ttu-id="9a0fe-104">この製品は、Microsoft のダウンロード サイトから無償でダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-104">You can download this product free of charge from the Microsoft download site.</span></span> <span data-ttu-id="9a0fe-105">[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] のドキュメントで取り上げられているサンプルおよびチュートリアルでは、データ ストアとして SQL Server が使用されています。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-105">The samples and walkthroughs in the [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] documentation use SQL Server as the data store.</span></span> <span data-ttu-id="9a0fe-106">SQL Server の代わりに、無償で提供されている SQL Server Express Edition をデータ ストアとして使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-106">SQL Server Express Edition, which is available without charge, can also be used as the data store instead of SQL Server.</span></span>  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a><span data-ttu-id="9a0fe-107">AdventureWorks データベースのダウンロードとインストール</span><span class="sxs-lookup"><span data-stu-id="9a0fe-107">Downloading and Installing the AdventureWorks Database</span></span>  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="9a0fe-108">SQL Server の AdventureWorks サンプル データベースをダウンロードおよびインストールするには</span><span class="sxs-lookup"><span data-stu-id="9a0fe-108">To download and install the AdventureWorks sample database for SQL Server</span></span>  
  
1.  <span data-ttu-id="9a0fe-109">Internet Explorer を開きます。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-109">Open Internet Explorer.</span></span>  
  
2.  <span data-ttu-id="9a0fe-110">移動して、 [SQL Server 2005 サンプルとサンプル データベース](http://go.microsoft.com/fwlink/?linkid=31046)Web サイトです。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-110">Go to the [SQL Server 2005 Samples and Sample Databases](http://go.microsoft.com/fwlink/?linkid=31046) Web site.</span></span>  
  
3.  <span data-ttu-id="9a0fe-111">記載されている手順に従ってプロセッサの種類に応じた AdventureWorks サンプル データベース (AdventureWorksDB.msi など) をダウンロードし、.MSI ファイルをローカル コンピューターに保存します。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-111">Follow the instructions for downloading the AdventureWorks sample database for your processor type (such as AdventureWorksDB.msi), and save the .MSI file to your local computer.</span></span>  
  
4.  <span data-ttu-id="9a0fe-112">以前のバージョンの AdventureWorks は、単体でダウンロードしたか SQL Server のセットアップ時にインストールしたかに関係なく、AdventureWorks.msi の実行前に削除しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-112">If you have a previous version of AdventureWorks installed from the download or during the SQL Server setup, you must remove it before running AdventureWorks.msi.</span></span>  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a><span data-ttu-id="9a0fe-113">単体でダウンロードした以前のバージョンの AdventureWorks サンプル データベースを削除するには</span><span class="sxs-lookup"><span data-stu-id="9a0fe-113">To remove a previous download of an AdventureWorks sample database</span></span>  
  
1.  <span data-ttu-id="9a0fe-114">AdventureWorks データベースまたは AdventureWorksDW データベースを削除します。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-114">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2.  <span data-ttu-id="9a0fe-115">**プログラム追加と削除**[ **AdventureWorksDB**または **[adventureworksbi]** ] をクリック**削除**です。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-115">From **Add or Remove Programs**, select **AdventureWorksDB** or **AdventureWorksBI** and click **Remove**.</span></span>  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a><span data-ttu-id="9a0fe-116">過去にセットアップ プログラムを使用してインストールした AdventureWorks サンプル データベースを削除するには</span><span class="sxs-lookup"><span data-stu-id="9a0fe-116">To remove an AdventureWorks sample database previously installed using Setup</span></span>  
  
1.  <span data-ttu-id="9a0fe-117">AdventureWorks データベースまたは AdventureWorksDW データベースを削除します。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-117">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2.  <span data-ttu-id="9a0fe-118">**プログラム追加と削除****[Microsoft SQL Server 2005]** をクリック**変更**です。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-118">From **Add or Remove Programs**, select **Microsoft SQL Server 2005** and click **Change**.</span></span>  
  
3.  <span data-ttu-id="9a0fe-119">**コンポーネントの選択****[ワークステーション コンポーネント]** をクリックし、 **[次へ]** です。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-119">From **Component Selection**, select **Workstation Components** and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="9a0fe-120">**、SQL Server インストール ウィザードへようこそ**をクリックして**次**です。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-120">From **Welcome to the SQL Server Installation Wizard**, click **Next**.</span></span>  
  
5.  <span data-ttu-id="9a0fe-121">**システム構成チェック**をクリックして**次**です。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-121">From **System Configuration Check**, click **Next**.</span></span>  
  
6.  <span data-ttu-id="9a0fe-122">**インスタンスの削除の変更または**をクリックして**インストール済みコンポーネントの変更**です。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-122">From **Change or Remove Instance**, click **Change Installed Components**.</span></span>  
  
7.  <span data-ttu-id="9a0fe-123">**機能の選択**、展開、**マニュアル、サンプル、およびサンプル データベース**ノード。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-123">From **Feature Selection**, expand the **Documentation, Samples, and Sample Databases** node.</span></span>  
  
8.  <span data-ttu-id="9a0fe-124">選択**サンプル コードおよびアプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-124">Select **Sample Code and Applications**.</span></span> <span data-ttu-id="9a0fe-125">展開**サンプル データベース**、削除して、選択するには、サンプル データベースを選択して**全体の機能は使用できません**です。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-125">Expand **Sample Databases**, select the sample database to be removed, and select **Entire feature will be unavailable**.</span></span> <span data-ttu-id="9a0fe-126">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-126">Click **Next**.</span></span>  
  
9. <span data-ttu-id="9a0fe-127">をクリックして**インストール**と、インストール ウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-127">Click **Install** and finish the installation wizard.</span></span>  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a><span data-ttu-id="9a0fe-128">AdventureWorks サンプル データベース ファイルを SQL Server のインスタンスにアタッチするには</span><span class="sxs-lookup"><span data-stu-id="9a0fe-128">To attach the AdventureWorks sample database files to an instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="9a0fe-129">ファイルのサンプル データベースのインストーラー ファイルをダウンロード後をダブルクリックして、 **AdventureWorksDB.msi**ファイル (またはダウンロードしたファイル)、データベースをインストールします。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-129">After the file sample database installer file has downloaded, double-click the **AdventureWorksDB.msi** file (or the file you downloaded) to install the database.</span></span> <span data-ttu-id="9a0fe-130">既定では、データベースは c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-130">By default, the database is installed at c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.</span></span>  
  
2.  <span data-ttu-id="9a0fe-131">SQLCMD または SQL Server Management Studio で次のスクリプトを実行し、AdventureWorks データベース ファイルを SQL Server のインスタンスにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-131">Attach the AdventureWorks database files to an instance of SQL Server by executing the following script SQLCMD or SQL Server Management Studio:</span></span>  
  
    ```  
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     <span data-ttu-id="9a0fe-132">これらのファイルが異なるドライブまたはディレクトリにインストールされている場合は、パスを適宜修正してから、`sp_attach_db` ストアド プロシージャを実行してください。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-132">If you have installed these files to a different drive or directory, you must revise the paths appropriately before you execute the `sp_attach_db` stored procedure.</span></span>  
  
## <a name="downloading-sql-server-express-edition"></a><span data-ttu-id="9a0fe-133">SQL Server Express Edition のダウンロード</span><span class="sxs-lookup"><span data-stu-id="9a0fe-133">Downloading SQL Server Express Edition</span></span>  
 <span data-ttu-id="9a0fe-134">サンプルおよびチュートリアルでは、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]セクションはデータ ストアとして SQL Server 2005 を使用しますが、代わりに SQL Server Express Edition を使用するように変更できます。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-134">The samples and walkthroughs in the [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] section use SQL Server 2005 as the data store but can be modified to use SQL Server Express Edition, instead.</span></span> <span data-ttu-id="9a0fe-135">SQL Server Express Edition は無料で入手でき、アプリケーションと共に再配布できます。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-135">SQL Server Express Edition is available without charge, and you can redistribute it with applications.</span></span> <span data-ttu-id="9a0fe-136">Visual Studio を使用している場合は、Pro 以上のエディションの SQL Server Express Edition が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-136">If you are using Visual Studio, SQL Server Express Edition is included in the Pro and higher editions.</span></span>  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a><span data-ttu-id="9a0fe-137">SQL Server Express Edition をダウンロードおよびインストールするには</span><span class="sxs-lookup"><span data-stu-id="9a0fe-137">To download and install SQL Server Express Edition</span></span>  
  
1.  <span data-ttu-id="9a0fe-138">Internet Explorer を開始します。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-138">Start Internet Explorer.</span></span>  
  
2.  <span data-ttu-id="9a0fe-139">移動して、 [Microsoft SQL Server 2005 Express Edition](http://go.microsoft.com/fwlink/?LinkID=31070)ページをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-139">Go to the  [Microsoft SQL Server 2005 Express Edition](http://go.microsoft.com/fwlink/?LinkID=31070) download page.</span></span>  
  
3.  <span data-ttu-id="9a0fe-140">Web サイトに記載されているインストールの指示に従います。</span><span class="sxs-lookup"><span data-stu-id="9a0fe-140">Follow the installation instructions on the Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a0fe-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a0fe-141">See Also</span></span>  
 [<span data-ttu-id="9a0fe-142">はじめに</span><span class="sxs-lookup"><span data-stu-id="9a0fe-142">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
