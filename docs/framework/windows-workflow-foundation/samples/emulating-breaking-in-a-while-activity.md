---
title: "While アクティビティでの中断のエミュレート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ddff715d-d623-4b54-b841-60bacbc3ca21
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8d2d1a0686b96d74bc39a654ee5c9b6f0972a12b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="emulating-breaking-in-a-while-activity"></a><span data-ttu-id="f5191-102">While アクティビティでの中断のエミュレート</span><span class="sxs-lookup"><span data-stu-id="f5191-102">Emulating breaking in a While activity</span></span>
<span data-ttu-id="f5191-103">このサンプルでは、<xref:System.Activities.Statements.DoWhile>、<xref:System.Activities.Statements.ForEach%601>、<xref:System.Activities.Statements.While>、および <xref:System.Activities.Statements.ParallelForEach%601> の各アクティビティのループ機構を中断する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f5191-103">This sample demonstrates how to break the looping mechanism of the following activities: <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.While>, and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span>  
  
 <span data-ttu-id="f5191-104">[!INCLUDE[wf](../../../../includes/wf-md.md)] にはこれらのループの実行を中断するアクティビティは用意されていないので、この方法が役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f5191-104">This is useful because [!INCLUDE[wf](../../../../includes/wf-md.md)] does not include any activity to break the execution of these loops.</span></span>  
  
## <a name="scenario"></a><span data-ttu-id="f5191-105">シナリオ</span><span class="sxs-lookup"><span data-stu-id="f5191-105">Scenario</span></span>  
 <span data-ttu-id="f5191-106">このサンプルでは、ベンダー (`Vendor` クラスのインスタンス) のリストから信頼できるベンダーを探し、最初に見つかったベンダーを取得します。</span><span class="sxs-lookup"><span data-stu-id="f5191-106">The sample finds the first reliable vendor from a list of vendors (instances of the `Vendor` class).</span></span> <span data-ttu-id="f5191-107">各ベンダーには、`ID`、`Name`、およびそのベンダーがどの程度信頼できるかを示す信頼度の数値があります。</span><span class="sxs-lookup"><span data-stu-id="f5191-107">Each vendor has an `ID`, a `Name` and a numeric reliability value that determines how dependable the vendor is.</span></span> <span data-ttu-id="f5191-108">このサンプルでは、`FindReliableVendor` というカスタム アクティビティを作成します。このアクティビティは、2 つの入力パラメーター (ベンダーのリストと信頼度の最小値) を受け取り、リストのベンダーのうち、指定された条件に一致する最初のベンダーを返します。</span><span class="sxs-lookup"><span data-stu-id="f5191-108">The sample creates a custom activity called `FindReliableVendor` that receives two input parameters (a list of vendors and a minimum reliability value) and returns the first vendor of the list that matches the supplied criteria.</span></span>  
  
## <a name="breaking-a-loop"></a><span data-ttu-id="f5191-109">ループの中断</span><span class="sxs-lookup"><span data-stu-id="f5191-109">Breaking a Loop</span></span>  
 [!INCLUDE[wf](../../../../includes/wf-md.md)]<span data-ttu-id="f5191-110"> にはループを中断するアクティビティは用意されていません。</span><span class="sxs-lookup"><span data-stu-id="f5191-110"> does not include an activity to break a loop.</span></span> <span data-ttu-id="f5191-111">コード サンプルでは、<xref:System.Activities.Statements.If> アクティビティといくつかの変数を使用してループの中断を実現します。</span><span class="sxs-lookup"><span data-stu-id="f5191-111">The code sample accomplishes breaking a loop by using an <xref:System.Activities.Statements.If> activity and several variables.</span></span> <span data-ttu-id="f5191-112">このサンプルでは、<xref:System.Activities.Statements.While> 変数に `reliableVendor` 以外の値が代入されると、`null` アクティビティが中断されます。</span><span class="sxs-lookup"><span data-stu-id="f5191-112">In the sample, the <xref:System.Activities.Statements.While> activity is broken once the `reliableVendor` variable is assigned a value other than `null`.</span></span>  
  
 <span data-ttu-id="f5191-113">while ループを中断する方法を示すコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f5191-113">The following code example demonstrates how the sample breaks a while loop.</span></span>  
  
```csharp  
// Iterates while the "i" variable is lower than the size of the list   
// and any reliable Vendor is found.        
new While(env => i.Get(env) < this.Vendors.Get(env).Count && reliableVendor.Get(env) == null)  
{  
    DisplayName = "Main loop. Breaks when a reliable vendor is found",  
    Body = new Sequence  
    {                              
        Activities =  
        {  
            // This is the if used for setting the value of the break value…  
            new If  
            {  
                DisplayName = "Check for a reliable vendor",  
  
                //  If a vendor satisfies the reliability level…  
                Condition = new InArgument<bool>(env =>   
                           this.Vendors.Get(env)[i.Get(env)].Reliability >   
                           this.MinimumReliability.Get(env)),  
  
                // then assign that vendor to the reliable vendor variable and   
                // the while condition becomes false (exit the loop).  
                Then = new Assign<Vendor>  
                {  
                    To = reliableVendor,  
                    Value = new InArgument<Vendor>(env =>   
                                  this.Vendors.Get(env)[i.Get(env)])  
                }  
            },  
  
            // Increment the iteration variable.   
            new Assign<int>  
            {  
                DisplayName = "Increment iteration variable",  
                To = i,  
                Value = new InArgument<int>(env => i.Get(env) + 1)  
            }   
        }  
    }  
}  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="f5191-114">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="f5191-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="f5191-115">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、EmulatingBreakInWhile.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="f5191-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the EmulatingBreakInWhile.sln solution file.</span></span>  
  
2.  <span data-ttu-id="f5191-116">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="f5191-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="f5191-117">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="f5191-117">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f5191-118">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="f5191-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f5191-119">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f5191-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f5191-120">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="f5191-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f5191-121">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="f5191-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\EmulatingBreakInWhile`