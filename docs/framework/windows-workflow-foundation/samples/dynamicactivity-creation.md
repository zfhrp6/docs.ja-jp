---
title: DynamicActivity の作成
ms.date: 03/30/2017
ms.assetid: d8ebe82f-98c8-4452-aed7-2c60a512b097
ms.openlocfilehash: 93435be69f90ca0b74dae6b934cb145fabb7afff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518104"
---
# <a name="dynamicactivity-creation"></a><span data-ttu-id="a0768-102">DynamicActivity の作成</span><span class="sxs-lookup"><span data-stu-id="a0768-102">DynamicActivity Creation</span></span>
<span data-ttu-id="a0768-103">このサンプルでは、<xref:System.Activities.DynamicActivity> アクティビティを使用して実行時にアクティビティを作成する 2 つの異なる方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a0768-103">This sample demonstrates two different ways to create an activity at runtime using the <xref:System.Activities.DynamicActivity> activity.</span></span>  
  
 <span data-ttu-id="a0768-104">このサンプルでは、<xref:System.Activities.Statements.Sequence> アクティビティと <xref:System.Activities.Statements.ForEach%601> アクティビティを含む <xref:System.Activities.Statements.Assign%601> アクティビティが本体に含まれたアクティビティを実行時に作成します。</span><span class="sxs-lookup"><span data-stu-id="a0768-104">In this sample, an activity is created at runtime with a body that contains a <xref:System.Activities.Statements.Sequence> activity that contains <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.Assign%601> activities.</span></span> <span data-ttu-id="a0768-105">整数の入力リストがこのアクティビティに渡され、プロパティとして設定されます。</span><span class="sxs-lookup"><span data-stu-id="a0768-105">An input list of integers is passed into the activity and set as a property.</span></span> <span data-ttu-id="a0768-106">次に、<xref:System.Activities.Statements.ForEach%601> アクティビティは値のリストを反復処理し、累計します。</span><span class="sxs-lookup"><span data-stu-id="a0768-106">The <xref:System.Activities.Statements.ForEach%601> activity then iterates over the list of values and accumulates it.</span></span> <span data-ttu-id="a0768-107"><xref:System.Activities.Statements.Assign%601> アクティビティでは、累計値をリスト内の要素数で除算して平均値を計算し、その値を平均に代入します。</span><span class="sxs-lookup"><span data-stu-id="a0768-107">In the <xref:System.Activities.Statements.Assign%601> activity, the average value is calculated by dividing the accumulator by the number of elements in the list and assign it to the average.</span></span>  
  
 <span data-ttu-id="a0768-108">このサンプルでは、入力引数として変数に設定され、出力引数として戻り値に設定される <xref:System.Activities.DynamicActivity> アクティビティを使用します。</span><span class="sxs-lookup"><span data-stu-id="a0768-108">The sample demonstrates the usage of a <xref:System.Activities.DynamicActivity> activity that flows in variables as input arguments and returning values as output arguments.</span></span> <span data-ttu-id="a0768-109">このアクティビティには、整数のリストである `Numbers` という名前の 1 つの入力引数があります。</span><span class="sxs-lookup"><span data-stu-id="a0768-109">The activity has one input argument named `Numbers` that is a list of integers.</span></span> <span data-ttu-id="a0768-110"><xref:System.Activities.Statements.ForEach%601> アクティビティは値のリストを反復処理し、累計します。</span><span class="sxs-lookup"><span data-stu-id="a0768-110">The <xref:System.Activities.Statements.ForEach%601> activity iterates over the list of values and accumulates it.</span></span> <span data-ttu-id="a0768-111"><xref:System.Activities.Statements.Assign%601> アクティビティでは、累計値をリスト内の要素数で除算して平均値を計算し、その値を平均に代入します。</span><span class="sxs-lookup"><span data-stu-id="a0768-111">In the <xref:System.Activities.Statements.Assign%601> activity, the average value is calculated by dividing the accumulator by the number of elements in the list and assigning it to the average.</span></span> <span data-ttu-id="a0768-112">平均は、`Average` という名前の出力引数として返されます。</span><span class="sxs-lookup"><span data-stu-id="a0768-112">The average is returned as an output argument named `Average`.</span></span>  
  
 <span data-ttu-id="a0768-113">動的アクティビティをプログラムで作成する場合は、次のコード例に示すように入力と出力を宣言します。</span><span class="sxs-lookup"><span data-stu-id="a0768-113">When the dynamic activity is created programmatically, the input and output are declared as shown in the following code example.</span></span>  
  
```csharp  
DynamicActivity act = new DynamicActivity()  
{  
    DisplayName = "Find average",  
    Properties =   
    {  
        // Input argument  
        new DynamicActivityProperty  
        {  
            Name = "Numbers",  
            Type = typeof(InArgument<List<int>>),  
            Value = numbers  
        },  
        // Output argument  
        new DynamicActivityProperty  
        {  
            Name = "Average",  
            Type = typeof(OutArgument<double>),  
            Value = average  
        }  
    },  
};  
```  
  
 <span data-ttu-id="a0768-114">リスト内の値の平均を計算する `DynamicActivity` の完全な定義を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="a0768-114">The following code example shows the complete definition of the `DynamicActivity` that computes the average of the values in a list.</span></span>  
  
```  
DynamicActivity act = new DynamicActivity()  
{  
    DisplayName = "Find average",  
    Properties =   
    {  
        // Input argument  
        new DynamicActivityProperty  
        {  
            Name = "Numbers",  
            Type = typeof(InArgument<List<int>>),  
            Value = numbers  
        },  
        // Output argument  
        new DynamicActivityProperty  
        {  
            Name = "Average",  
            Type = typeof(OutArgument<double>),  
            Value = average  
        }  
    },  
    Implementation = () =>  
        new Sequence  
        {  
            Variables = { result, accumulator },  
            Activities =  
            {  
                new ForEach<int>  
                {  
                    Values =  new ArgumentValue<IEnumerable<int>> { ArgumentName = "Numbers" },                                  
                    Body = new ActivityAction<int>  
                    {  
                        Argument = iterationVariable,  
                        Handler = new Assign<int>  
                        {  
                            To = accumulator,  
                            Value = new InArgument<int>(env => iterationVariable.Get(env) +  accumulator.Get(env))  
                        }  
                    }  
                },  
  
                // Calculate the average and assign to the output argument.  
                new Assign<double>  
                {  
                    To = new ArgumentReference<double> { ArgumentName = "Average" },  
                    Value = new InArgument<double>(env => accumulator.Get(env) / numbers.Get(env).Count<int>())  
                },  
            }  
        }  
};  
```  
  
 <span data-ttu-id="a0768-115">XAML で作成する場合は、次の例に示すように入力と出力を宣言します。</span><span class="sxs-lookup"><span data-stu-id="a0768-115">When created in XAML, the input and output are declared as shown in the following example.</span></span>  
  
```xml  
<Activity x:Class="Microsoft.Samples.DynamicActivityCreation.FindAverage"  
          xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
          xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <x:Members>  
    <x:Property Name="Numbers" Type="InArgument(scg:List(x:Int32))" />  
    <x:Property Name="Average" Type="OutArgument(x:Double)" />  
  </x:Members>  
    ...  
    ...  
</Activity>  
```  
  
 <span data-ttu-id="a0768-116">XAML は、[!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] を使用して視覚的に作成できます。</span><span class="sxs-lookup"><span data-stu-id="a0768-116">The XAML can be created visually using the [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)].</span></span> <span data-ttu-id="a0768-117">Visual Studio プロジェクトに含まれている場合は、「ビルド アクション」を"None"にコンパイルされないように設定することを確認します。</span><span class="sxs-lookup"><span data-stu-id="a0768-117">If it is included in a Visual Studio project, be sure to set its "Build Action" to "None" to prevent it from being compiled.</span></span> <span data-ttu-id="a0768-118">その後、XAML は、次の呼び出しを使用して動的に読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="a0768-118">The XAML can then be loaded dynamically using the following call.</span></span>  
  
```  
Activity act2 = ActivityXamlServices.Load(@"FindAverage.xaml");  
```  
  
 <span data-ttu-id="a0768-119">プログラムによって、または XAML ワークフローを読み込むことによって作成された <xref:System.Activities.DynamicActivity> インスタンスは、次のコード例に示すように使用できます。</span><span class="sxs-lookup"><span data-stu-id="a0768-119">The <xref:System.Activities.DynamicActivity> instance created programmatically or through loading a XAML workflow can be used as shown in the following code example.</span></span> <span data-ttu-id="a0768-120">「機能」に渡されることに注意してください、 `WorkflowInvoker.Invoke` "act"は、<xref:System.Activities.Activity>最初のコード例で定義されています。</span><span class="sxs-lookup"><span data-stu-id="a0768-120">Please note that "act" passed to the `WorkflowInvoker.Invoke` is the "act" <xref:System.Activities.Activity> defined in the first code example.</span></span>  
  
```  
IDictionary<string, object> results = WorkflowInvoker.Invoke(act, new Dictionary<string, object> { { "Numbers", numbers } });  
  
Console.WriteLine("The average calculated using the code activity is = " + results["Average"]);  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a0768-121">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="a0768-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="a0768-122">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、DynamicActivityCreation.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="a0768-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the DynamicActivityCreation.sln solution file.</span></span>  
  
2.  <span data-ttu-id="a0768-123">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a0768-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="a0768-124">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a0768-124">To run the solution, press CTRL+F5.</span></span>  
  
## <a name="command-line-arguments"></a><span data-ttu-id="a0768-125">[コマンド ライン引数]</span><span class="sxs-lookup"><span data-stu-id="a0768-125">Command line arguments</span></span>  
 <span data-ttu-id="a0768-126">このサンプルでは、コマンド ライン引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="a0768-126">This sample accepts command line arguments.</span></span> <span data-ttu-id="a0768-127">ユーザーは、アクティビティで平均を計算する対象となる数値のリストを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a0768-127">Users can provide a list of numbers for the activity to calculate their average.</span></span> <span data-ttu-id="a0768-128">使用する数値のリストは、スペースで区切られた数値のリストとして渡します。</span><span class="sxs-lookup"><span data-stu-id="a0768-128">The list of numbers to be used is passed as a list of numbers separated by a space.</span></span> <span data-ttu-id="a0768-129">たとえば、5、10、および 32 の平均を計算するには、次のコマンド ラインを使用してこのサンプルを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a0768-129">For example, to calculate the average of 5, 10, and 32 invoke the sample using the following command line.</span></span>  
  
 <span data-ttu-id="a0768-130">**DynamicActivityCreation 5 10 32**</span><span class="sxs-lookup"><span data-stu-id="a0768-130">**DynamicActivityCreation 5 10 32**</span></span>  
> [!IMPORTANT]
>  <span data-ttu-id="a0768-131">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="a0768-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a0768-132">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a0768-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a0768-133">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="a0768-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a0768-134">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="a0768-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\DynamicActivityCreation`