---
title: 補正可能なアクティビティでのキャンセル ハンドラー
ms.date: 03/30/2017
ms.assetid: afd98bee-eccf-47e9-99c9-27cea84ce5ce
ms.openlocfilehash: ce4d67b26a2b4c6a9b507715b48e75e328c5b100
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515002"
---
# <a name="cancellation-handler-on-compensable-activity"></a>補正可能なアクティビティでのキャンセル ハンドラー
このサンプルでは、<xref:System.Activities.Statements.CompensableActivity> でキャンセル ハンドラーを使用する例を示します。  
  
 このサンプルには、<xref:System.Activities.Statements.CompensableActivity> キャンセルの使用法を示す 2 つのシナリオが含まれています。最初のシナリオには、3 つの補正可能な子アクティビティを含む補正可能なルート アクティビティが含まれます。 2 つの子アクティビティは、アクティビティ本体の実行を正常に終了します。 3 つ目の子アクティビティ本体が実行されると、3 つ目のアクティビティ処理をキャンセルすることで処理される例外が発生し、その後ルート アクティビティのキャンセルがトリガーされます。 この例のルート アクティビティのロジックでは、先に完了している他の 2 つの子アクティビティが補正されます。  
  
```  
Try  
{  
    CA   
    {  
        CA1   
        {  
        }  
        CA2  
        {  
        }  
        CA3  
        {  
            //Exception here  
            // Then this will get cancelled  
        }  
  
       // Cancellation for the root activity automatically gets called, which, in turn, adds some logic to revert what was done (Or can decide to actually confirm CA1 & CA2 if the user so desires).  
    }  
}  
Catches {  
// Can do more stuff...  
}  
```  
  
 2 つ目のシナリオでは、<xref:System.Activities.Statements.TryCatch> 分岐の前に終了する <xref:System.Activities.Statements.Delay> と平行して、<xref:System.Activities.Statements.TryCatch> を実行する方法を示します。 最初の分岐が終了したときに完了条件が `true` に設定されて、他の分岐がキャンセルされます。  
  
```  
Parallel   
{  
    Branch1   
    {  
        // Small Delay that times out (timeout1) before branch2.  
    }  
    Branch2   
    {  
        CA   
        {  
            CA1   
            {  
            }  
            CA2   
            {  
            }  
            CA3   
            {  
            }  
            If (timeout1)    
            {  
                call Cancel CA  
            }  
        }  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して CompensationCancellation.sln を開きます。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押すか、[ビルド] メニューの [ソリューションのビルド] をクリックして、サンプルをビルドします。  
  
3.  F5 キーを押すか、[デバッグ] メニューの [デバッグ開始] をクリックしてサンプルを実行します。 または、Ctrl キーを押しながら F5 キーを押すか、[デバッグ] メニューの [デバッグなしで開始] をクリックすることもできます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CompensationCancellation`