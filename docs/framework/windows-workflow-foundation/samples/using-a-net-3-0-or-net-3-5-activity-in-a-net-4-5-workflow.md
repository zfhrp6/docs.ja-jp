---
title: .NET Framework 4.5 ワークフローでの .NET Framework 3.0 または .NET Framework 3.5 アクティビティの使用
ms.date: 03/30/2017
ms.assetid: 6c53fd4c-5dd0-4fb4-ab6b-111302629548
ms.openlocfilehash: ab2e93918617bd1ca21fb32878d446db0dd2ef16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="using-a-net-framework-30-or-net-framework-35-activity-in-a-net-framework-45-workflow"></a>.NET Framework 4.5 ワークフローでの .NET Framework 3.0 または .NET Framework 3.5 アクティビティの使用
<xref:System.Activities.Statements.Interop>アクティビティでは、内で .NET Framework 3.0 Windows Workflow Foundation (WF) 活動を実行することができます、[!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]ワークフローです。 このサンプルでは、<xref:System.Activities.Statements.Interop> アクティビティを使用して、文字列をカスタムの [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] アクティビティに引数として渡す方法を示します。  
  
## <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、SimpleInterop.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\SimpleInterop`  
  
## <a name="see-also"></a>関連項目
