---
title: "DynamicActivity の作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8ebe82f-98c8-4452-aed7-2c60a512b097
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1760324fc7911ebe9b3139f79c65222b54a329d0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="dynamicactivity-creation"></a>DynamicActivity の作成
このサンプルでは、<xref:System.Activities.DynamicActivity> アクティビティを使用して実行時にアクティビティを作成する 2 つの異なる方法を示します。  
  
 このサンプルでは、<xref:System.Activities.Statements.Sequence> アクティビティと <xref:System.Activities.Statements.ForEach%601> アクティビティを含む <xref:System.Activities.Statements.Assign%601> アクティビティが本体に含まれたアクティビティを実行時に作成します。 整数の入力リストがこのアクティビティに渡され、プロパティとして設定されます。 次に、<xref:System.Activities.Statements.ForEach%601> アクティビティは値のリストを反復処理し、累計します。 <xref:System.Activities.Statements.Assign%601> アクティビティでは、累計値をリスト内の要素数で除算して平均値を計算し、その値を平均に代入します。  
  
 このサンプルでは、入力引数として変数に設定され、出力引数として戻り値に設定される <xref:System.Activities.DynamicActivity> アクティビティを使用します。 このアクティビティには、整数のリストである `Numbers` という名前の 1 つの入力引数があります。 <xref:System.Activities.Statements.ForEach%601> アクティビティは値のリストを反復処理し、累計します。 <xref:System.Activities.Statements.Assign%601> アクティビティでは、累計値をリスト内の要素数で除算して平均値を計算し、その値を平均に代入します。 平均は、`Average` という名前の出力引数として返されます。  
  
 動的アクティビティをプログラムで作成する場合は、次のコード例に示すように入力と出力を宣言します。  
  
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
  
 リスト内の値の平均を計算する `DynamicActivity` の完全な定義を次のコード例に示します。  
  
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
  
 XAML で作成する場合は、次の例に示すように入力と出力を宣言します。  
  
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
  
 XAML は、[!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] を使用して視覚的に作成できます。 Visual Studio プロジェクトに含まれている場合は、「ビルド アクション」を"None"にコンパイルされないように設定することを確認します。 その後、XAML は、次の呼び出しを使用して動的に読み込むことができます。  
  
```  
Activity act2 = ActivityXamlServices.Load(@"FindAverage.xaml");  
```  
  
 プログラムによって、または XAML ワークフローを読み込むことによって作成された <xref:System.Activities.DynamicActivity> インスタンスは、次のコード例に示すように使用できます。 「機能」に渡されることに注意してください、 `WorkflowInvoker.Invoke` "act"は、<xref:System.Activities.Activity>最初のコード例で定義されています。  
  
```  
IDictionary<string, object> results = WorkflowInvoker.Invoke(act, new Dictionary<string, object> { { "Numbers", numbers } });  
  
Console.WriteLine("The average calculated using the code activity is = " + results["Average"]);  
```  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、DynamicActivityCreation.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
## <a name="command-line-arguments"></a>[コマンド ライン引数]  
 このサンプルでは、コマンド ライン引数を受け取ります。 ユーザーは、アクティビティで平均を計算する対象となる数値のリストを指定できます。 使用する数値のリストは、スペースで区切られた数値のリストとして渡します。 たとえば、5、10、および 32 の平均を計算するには、次のコマンド ラインを使用してこのサンプルを呼び出します。  
  
 **DynamicActivityCreation 5 10 32**  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\DynamicActivityCreation`