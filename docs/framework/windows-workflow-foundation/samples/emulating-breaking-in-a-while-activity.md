---
title: While アクティビティでの中断のエミュレート
ms.date: 03/30/2017
ms.assetid: ddff715d-d623-4b54-b841-60bacbc3ca21
ms.openlocfilehash: 37c64c2b8dc03d58f9c2802edef644fe4888e87d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="emulating-breaking-in-a-while-activity"></a>While アクティビティでの中断のエミュレート
このサンプルでは、<xref:System.Activities.Statements.DoWhile>、<xref:System.Activities.Statements.ForEach%601>、<xref:System.Activities.Statements.While>、および <xref:System.Activities.Statements.ParallelForEach%601> の各アクティビティのループ機構を中断する方法を示します。  
  
 これは、機能は、Windows Workflow Foundation (WF) にこれらのループの実行を中断するアクティビティが含まれていないため便利です。  
  
## <a name="scenario"></a>シナリオ  
 このサンプルでは、ベンダー (`Vendor` クラスのインスタンス) のリストから信頼できるベンダーを探し、最初に見つかったベンダーを取得します。 各ベンダーには、`ID`、`Name`、およびそのベンダーがどの程度信頼できるかを示す信頼度の数値があります。 このサンプルでは、`FindReliableVendor` というカスタム アクティビティを作成します。このアクティビティは、2 つの入力パラメーター (ベンダーのリストと信頼度の最小値) を受け取り、リストのベンダーのうち、指定された条件に一致する最初のベンダーを返します。  
  
## <a name="breaking-a-loop"></a>ループの中断  
 Windows Workflow Foundation (WF) では、ループを中断するアクティビティは含まれません。 コード サンプルでは、<xref:System.Activities.Statements.If> アクティビティといくつかの変数を使用してループの中断を実現します。 このサンプルでは、<xref:System.Activities.Statements.While> 変数に `reliableVendor` 以外の値が代入されると、`null` アクティビティが中断されます。  
  
 while ループを中断する方法を示すコード例を次に示します。  
  
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
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、EmulatingBreakInWhile.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\EmulatingBreakInWhile`