---
title: "LINQ to Objects アクティビティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 403c82e8-7f2b-42f6-93cd-95c35bc76ead
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ff77211000cfdda9c35e5a0dcbc69fc0eaf5c3be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="linq-to-objects-activity"></a>LINQ to Objects アクティビティ
このサンプルでは、LINQ to Objects を使用してコレクション内の要素に対してクエリを実行するアクティビティを作成する方法を示します。  
  
## <a name="activity-details-for-findincollection"></a>FindInCollection のアクティビティの詳細  
 このアクティビティでは、LINQ to Objects を使用してメモリ内のコレクションの要素に対してクエリを実行できます。 LINQ 述語をラムダ式のフォームで指定して、結果をフィルター処理する必要があります。 このアクティビティは、<xref:System.Activities.Statements.AddToCollection%601> アクティビティと組み合わせて使用することができます。  
  
 次の表で、アクティビティのプロパティと戻り値について詳しく説明します。  
  
|プロパティ値または戻り値|説明|  
|------------------------------|-----------------|  
|`Collection` プロパティ|ソース コレクションを指定する必須のプロパティ|  
|`Predicate` プロパティ|コレクションのフィルターをラムダ式のフォームで指定する必須のプロパティ|  
|戻り値|フィルター処理されたコレクション|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a>カスタム アクティビティを使用するコード サンプル  
 次のコード例では、`FindInCollection` カスタム アクティビティを使用して、`Role` プロパティと `Manager` プロパティがそれぞれ `Location` と `Redmond` に設定されている従業員のコレクションのすべての行を検索します。  
  
```csharp  
// Find all program managers in Redmond in the employees collection.  
  
Activity wf = new FindInCollection<Employee>  
{  
    Collections = new LambdaValue<IEnumerable<Employee>>(c => employees),                
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(e => e.Role.Equals("Manager") && e.Location.Equals("Redmond")))  
};  
```  
  
 次のコードでは、カスタム FindInCollection アクティビティ、<xref:System.Activities.Statements.AddToCollection%601>、および <xref:System.Activities.Statements.ForEach%601> アクティビティを使用して、コレクションに従業員を挿入し、ロールが開発者で勤務地が Redmond である従業員をすべて検索して、生成されたリストを反復処理するワークフロー プログラムを作成する方法を示します。  
  
```csharp  
// Create the Linq predicate for the find expression  
  
Func<Employee, bool> predicate = e => e.Role == "DEV" && e.Location.Equals("Redmond");  
  
// Create workflow program  
Activity sampleWorkflow = new Sequence  
{  
    Variables = { employees, devsFromRedmond },  
    Activities =  
    {  
        new Assign<IList<Employee>>  
        {  
            To = employees,  
            Value = new LambdaValue<IList<Employee>>(c => new List<Employee>())  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(1, "Employee 1", "DEV", "Redmond"))  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(2, "Employee 2", "DEV", "Redmond"))  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(3, "Employee 3", "PM", "Redmond"))  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(4, "Employee 4", "PM", "China"))  
        },  
        new FindInCollection<Employee>  
        {  
            Collections = new InArgument<IEnumerable<Employee>>(employees),  
            Predicate = new LambdaValue<Func<Employee, bool>>(c => predicate),  
            Result = new OutArgument<IList<Employee>>(devsFromRedmond)  
        },  
        new ForEach<Employee>  
        {  
            Values = new InArgument<IEnumerable<Employee>>(devsFromRedmond),  
            Body = new ActivityAction<Employee>  
            {  
                Argument = iterationVariable,  
                Handler = new WriteLine  
                {  
                    Text = new InArgument<string>(env => iterationVariable.Get(env).ToString())  
                }  
            }  
        }  
    }  
};  
```  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、LinqToObjects.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、F5 キーを押します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Linq\LinqToObjects`  
  
## <a name="see-also"></a>参照  
 [ラムダ式 (c# プログラミング ガイド)](http://go.microsoft.com/fwlink/?LinkId=150381)  
 [LINQ to Objects](http://go.microsoft.com/fwlink/?LinkID=150380)
