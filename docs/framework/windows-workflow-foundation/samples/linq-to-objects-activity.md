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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9f34189c8f9911b09017056b22611d27df25c10e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-objects-activity"></a><span data-ttu-id="5fbdd-102">LINQ to Objects アクティビティ</span><span class="sxs-lookup"><span data-stu-id="5fbdd-102">LINQ to Objects Activity</span></span>
<span data-ttu-id="5fbdd-103">このサンプルでは、LINQ to Objects を使用してコレクション内の要素に対してクエリを実行するアクティビティを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5fbdd-103">This sample demonstrates how to create an activity to use LINQ to Objects to query elements in a collection.</span></span>  
  
## <a name="activity-details-for-findincollection"></a><span data-ttu-id="5fbdd-104">FindInCollection のアクティビティの詳細</span><span class="sxs-lookup"><span data-stu-id="5fbdd-104">Activity Details for FindInCollection</span></span>  
 <span data-ttu-id="5fbdd-105">このアクティビティでは、LINQ to Objects を使用してメモリ内のコレクションの要素に対してクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="5fbdd-105">This activity allows users to query elements from collections in memory using LINQ to Objects.</span></span> <span data-ttu-id="5fbdd-106">LINQ 述語をラムダ式のフォームで指定して、結果をフィルター処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5fbdd-106">You must provide a LINQ predicate in the form of a lambda expression to filter the results.</span></span> <span data-ttu-id="5fbdd-107">このアクティビティは、<xref:System.Activities.Statements.AddToCollection%601> アクティビティと組み合わせて使用することができます。</span><span class="sxs-lookup"><span data-stu-id="5fbdd-107">This activity can be used in conjunction with <xref:System.Activities.Statements.AddToCollection%601> activities.</span></span>  
  
 <span data-ttu-id="5fbdd-108">次の表で、アクティビティのプロパティと戻り値について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="5fbdd-108">The following table details the property and return values for the activity.</span></span>  
  
|<span data-ttu-id="5fbdd-109">プロパティ値または戻り値</span><span class="sxs-lookup"><span data-stu-id="5fbdd-109">Property or Return Value</span></span>|<span data-ttu-id="5fbdd-110">説明</span><span class="sxs-lookup"><span data-stu-id="5fbdd-110">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="5fbdd-111">`Collection` プロパティ</span><span class="sxs-lookup"><span data-stu-id="5fbdd-111">`Collection` property</span></span>|<span data-ttu-id="5fbdd-112">ソース コレクションを指定する必須のプロパティ</span><span class="sxs-lookup"><span data-stu-id="5fbdd-112">A required property that specifies the source collection.</span></span>|  
|<span data-ttu-id="5fbdd-113">`Predicate` プロパティ</span><span class="sxs-lookup"><span data-stu-id="5fbdd-113">`Predicate` property</span></span>|<span data-ttu-id="5fbdd-114">コレクションのフィルターをラムダ式のフォームで指定する必須のプロパティ</span><span class="sxs-lookup"><span data-stu-id="5fbdd-114">A required property that specifies the filter for the collection in the form of a lambda expression.</span></span>|  
|<span data-ttu-id="5fbdd-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="5fbdd-115">Return Value</span></span>|<span data-ttu-id="5fbdd-116">フィルター処理されたコレクション</span><span class="sxs-lookup"><span data-stu-id="5fbdd-116">The filtered collection.</span></span>|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a><span data-ttu-id="5fbdd-117">カスタム アクティビティを使用するコード サンプル</span><span class="sxs-lookup"><span data-stu-id="5fbdd-117">Code Sample that uses the Custom Activity</span></span>  
 <span data-ttu-id="5fbdd-118">次のコード例では、`FindInCollection` カスタム アクティビティを使用して、`Role` プロパティと `Manager` プロパティがそれぞれ `Location` と `Redmond` に設定されている従業員のコレクションのすべての行を検索します。</span><span class="sxs-lookup"><span data-stu-id="5fbdd-118">The following code example uses the `FindInCollection` custom activity to find all rows in a collection of employees that have a `Role` property set to `Manager` and the `Location` property set to `Redmond`.</span></span>  
  
```csharp  
// Find all program managers in Redmond in the employees collection.  
  
Activity wf = new FindInCollection<Employee>  
{  
    Collections = new LambdaValue<IEnumerable<Employee>>(c => employees),                
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(e => e.Role.Equals("Manager") && e.Location.Equals("Redmond")))  
};  
```  
  
 <span data-ttu-id="5fbdd-119">次のコードでは、カスタム FindInCollection アクティビティ、<xref:System.Activities.Statements.AddToCollection%601>、および <xref:System.Activities.Statements.ForEach%601> アクティビティを使用して、コレクションに従業員を挿入し、ロールが開発者で勤務地が Redmond である従業員をすべて検索して、生成されたリストを反復処理するワークフロー プログラムを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5fbdd-119">The following code shows how to create a workflow program that uses the custom FindInCollection activity, <xref:System.Activities.Statements.AddToCollection%601>, and <xref:System.Activities.Statements.ForEach%601> activities to populate a collection with employees, find all the employees that have developer roles and are located in Redmond, and then iterate through the resulting list.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="5fbdd-120">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="5fbdd-120">To use this sample</span></span>  
  
1.  <span data-ttu-id="5fbdd-121">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、LinqToObjects.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="5fbdd-121">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the LinqToObjects.sln solution file.</span></span>  
  
2.  <span data-ttu-id="5fbdd-122">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="5fbdd-122">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="5fbdd-123">ソリューションを実行するには、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="5fbdd-123">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5fbdd-124">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="5fbdd-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5fbdd-125">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="5fbdd-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5fbdd-126">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="5fbdd-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5fbdd-127">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="5fbdd-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Linq\LinqToObjects`  
  
## <a name="see-also"></a><span data-ttu-id="5fbdd-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="5fbdd-128">See Also</span></span>  
 [<span data-ttu-id="5fbdd-129">ラムダ式 (c# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="5fbdd-129">Lambda Expressions (C# Programming Guide)</span></span>](http://go.microsoft.com/fwlink/?LinkId=150381)  
 [<span data-ttu-id="5fbdd-130">LINQ to Objects</span><span class="sxs-lookup"><span data-stu-id="5fbdd-130">LINQ to Objects</span></span>](http://go.microsoft.com/fwlink/?LinkID=150380)
