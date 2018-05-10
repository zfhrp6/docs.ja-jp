---
title: LINQ to SQL のサンプル
ms.date: 03/30/2017
ms.assetid: 5f39db9e-0e62-42c9-8c98-bb8b54cec98c
ms.openlocfilehash: 3cfcaf3de1a22b8bb5505083f127a9888b99dbd8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="linq-to-sql-sample"></a>LINQ to SQL のサンプル
このサンプルでは、SQL Server データベース内のテーブルの LINQ to SQL クエリ エンティティを使用するアクティビティを作成する方法を示します。  
  
> [!IMPORTANT]
>  WCF サンプルは、既にコンピューターにインストールできます。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\Samples\WCFWFCardspace`  
>   
>  このディレクトリが存在しない場合は、このページの上部にあるサンプルのダウンロードのリンクをクリックします。 このリンクがダウンロードしのすべてをインストールすることに注意してください、 [!INCLUDE[wf1](../../../../includes/wf1-md.md)]、WCF、および[!INCLUDE[infocard](../../../../includes/infocard-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\Samples\WCFWFCardSpace\WF\Scenario\ActivityLibrary\Linq\LinqToSql`  
  
## <a name="activity-details-for-findinsqltable"></a>FindInSqlTable のアクティビティの詳細  
 このアクティビティでは、LINQ to SQL を使用してデータベース内のテーブルのエンティティに対してクエリを実行できます。 アクティビティのユーザーは、LINQ 述語をラムダ式のフォームで指定して、結果をフィルター処理することもできます。 述語を指定しない場合、テーブル全体が返されます。 次の表で、アクティビティのプロパティと戻り値について詳しく説明します。  
  
|プロパティ値または戻り値|説明|  
|------------------------------|-----------------|  
|`Collection` プロパティ|ソース コレクションを指定する必須のプロパティ|  
|`Predicate` プロパティ|コレクションのフィルターをラムダ式のフォームで指定する必須のプロパティ|  
|戻り値|フィルター処理されたコレクション|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a>カスタム アクティビティを使用するコード サンプル  
 `FindInSqlTable` カスタム アクティビティを使用して、`Employee` という名前の SQL Server テーブルで `Role` 列が `SDE` になっている行をすべて検索するコード例を次に示します。  
  
```csharp  
new FindInSqlTable<Employee>   
{  
    ConnectionString = @"Data Source=.\SQLExpress;Initial Catalog=LinqToSqlSample;Integrated Security=True",                          
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(emp => emp.Role.Equals("SDE"))),  
    Result = new OutArgument<IList<Employee>>(employees)  
},  
```  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  コマンド プロンプトを開きます。  
  
2.  このサンプルが含まれるフォルダーに移動します。  
  
3.  Setup.cmd コマンド ファイルを実行します。  
  
    > [!NOTE]
    >  Setup.cmd スクリプトは、ローカル コンピューターに SQL Server Express のサンプル データベースをインストールしようとします。 他の SQL Server インスタンスにインストールする場合は、Setup.cmd を編集します。  
  
     Setup.cmd スクリプトでは、次の操作を実行します。  
  
    -   LinqToSqlSample という名前のデータベースを作成します。  
  
    -   Roles テーブルを作成します。  
  
    -   Employees テーブルを作成します。  
  
    -   3 個のレコードを Roles テーブルに挿入します。  
  
    -   12 個のレコードを Employees テーブルに挿入します。  
  
4.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、LinqToSQL.sln ソリューション ファイルを開きます。  
  
5.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
6.  ソリューションを実行するには、F5 キーを押します。  
  
#### <a name="to-uninstall-the-linqtosql-sample-database"></a>LinqToSql サンプル データベースをアンインストールするには  
  
1.  コマンド プロンプトを開きます。  
  
2.  このサンプルが含まれるフォルダーに移動します。  
  
3.  Cleanup.cmd コマンド ファイルを実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Liiinq\LinqToSql`  
  
## <a name="see-also"></a>関連項目  
 [LINQ to SQL](http://go.microsoft.com/fwlink/?LinkId=150376)  
 [はじめに (LINQ to SQL)](http://go.microsoft.com/fwlink/?LinkId=150377)
