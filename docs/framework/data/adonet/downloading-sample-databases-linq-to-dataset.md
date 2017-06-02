---
title: "Downloading Sample Databases (LINQ to DataSet) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Downloading Sample Databases (LINQ to DataSet)
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] のドキュメントで取り上げられているサンプルおよびチュートリアルでは、AdventureWorks サンプル データベースが使用されています。  この製品は、Microsoft のダウンロード サイトから無償でダウンロードできます。[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] のドキュメントに記載されているサンプルおよびチュートリアルでは、データ ストアとして SQL Server が使用されています。  SQL Server の代わりに、無償で提供されている SQL Server Express Edition をデータ ストアとして使用することもできます。  
  
## AdventureWorks データベースのダウンロードとインストール  
  
#### SQL Server の AdventureWorks サンプル データベースをダウンロードおよびインストールするには  
  
1.  Internet Explorer を開きます。  
  
2.  「[SQL Server 2005 サンプルとサンプル データベース](http://go.microsoft.com/fwlink/?linkid=31046)」の Web サイトに移動します。  
  
3.  記載されている手順に従ってプロセッサの種類に応じた AdventureWorks サンプル データベース \(AdventureWorksDB.msi など\) をダウンロードし、.MSI ファイルをローカル コンピューターに保存します。  
  
4.  以前のバージョンの AdventureWorks は、単体でダウンロードしたか SQL Server のセットアップ時にインストールしたかに関係なく、AdventureWorks.msi の実行前に削除しておく必要があります。  
  
#### 単体でダウンロードした以前のバージョンの AdventureWorks サンプル データベースを削除するには  
  
1.  AdventureWorks データベースまたは AdventureWorksDW データベースを削除します。  
  
2.  **\[プログラムの追加と削除\]** で **\[AdventureWorksDB\]** または **\[AdventureWorksBI\]** を選択し、**\[削除\]** をクリックします。  
  
#### 過去にセットアップ プログラムを使用してインストールした AdventureWorks サンプル データベースを削除するには  
  
1.  AdventureWorks データベースまたは AdventureWorksDW データベースを削除します。  
  
2.  **\[プログラムの追加と削除\]** で **\[Microsoft SQL Server 2005\]** を選択し、**\[変更\]** をクリックします。  
  
3.  **\[コンポーネントの選択\]** で **\[ワークステーション コンポーネント\]** を選択し、**\[次へ\]** をクリックします。  
  
4.  **\[Microsoft SQL Server インストール ウィザードへようこそ\]** で、**\[次へ\]** をクリックします。  
  
5.  **\[システム構成チェック\]** で、**\[次へ\]** をクリックします。  
  
6.  **\[インスタンスの変更または削除\]** で、**\[インストール済みコンポーネントの変更\]** をクリックします。  
  
7.  **\[機能の選択\]** をクリックし、**\[ドキュメント、サンプル、およびサンプル データベース\]** ノードを展開します。  
  
8.  **\[サンプル コードとアプリケーション\]** を選択します。  **\[サンプル データベース\]** を展開し、削除するサンプル データベースを選択して、**\[インストールしない\]** を選択します。  **\[次へ\]** をクリックします。  
  
9. **\[インストール\]** をクリックしてインストール ウィザードを完了します。  
  
#### AdventureWorks サンプル データベース ファイルを SQL Server のインスタンスにアタッチするには  
  
1.  サンプル データベースのインストーラー ファイルをダウンロードしたら、ダウンロードしたファイル \(**AdventureWorksDB.msi** など\) をダブルクリックして、データベースをインストールします。  既定では、データベースは c:\\Program Files\\Microsoft SQL Server\\MSSQL.1\\MSSQL\\Data にインストールされます。  
  
2.  SQLCMD または SQL Server Management Studio で次のスクリプトを実行し、AdventureWorks データベース ファイルを SQL Server のインスタンスにアタッチします。  
  
    ```  
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     これらのファイルが異なるドライブまたはディレクトリにインストールされている場合は、パスを適宜修正してから、`sp_attach_db` ストアド プロシージャを実行してください。  
  
## SQL Server Express Edition のダウンロード  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] セクションで取り上げられているサンプルおよびチュートリアルには、データ ストアとして SQL Server 2005 が使用されていますが、代わりに SQL Server Express Edition を使用するように修正することもできます。  SQL Server Express Edition は無料で入手でき、アプリケーションと共に再配布できます。  Professional Edition 以上の [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] には、SQL Server Express Edition が付属しています。  
  
#### SQL Server Express Edition をダウンロードおよびインストールするには  
  
1.  Internet Explorer を開始します。  
  
2.  [Microsoft SQL Server 2005 Express Edition](http://go.microsoft.com/fwlink/?LinkID=31070) のダウンロード ページに移動します。  
  
3.  Web サイトに記載されているインストールの指示に従います。  
  
## 参照  
 [Getting Started](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)