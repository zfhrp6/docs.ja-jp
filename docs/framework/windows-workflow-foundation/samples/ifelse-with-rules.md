---
title: "ルール付き IfElse"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4ad9bb2-9037-413a-8b14-59ed7b927a9e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bec818ca5492e9a49a602a4f7baef4b45cb073c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ifelse-with-rules"></a>ルール付き IfElse
このサンプルでは、ルール条件を <xref:System.Workflow.Activities.IfElseActivity> アクティビティで使用する方法を示します。  
  
 このサンプルでは、ホストから `OrderValue` パラメータが渡されます。 このパラメータの値は、<xref:System.Workflow.Activities.IfElseActivity> アクティビティの最初の分岐のルール条件で使用されます。 場合、値が 10,000 未満の場合、最初の分岐が実行され、<xref:System.Workflow.Activities.CodeActivity>最初の分岐のアクティビティの出力**マネージャーの承認を取得**コンソールにします。 値が 10,000 を超える場合、 <xref:System.Workflow.Activities.CodeActivity> 2 番目の分岐のアクティビティが実行され、印刷**取得 VP 承認**です。  
  
### <a name="to-build-the-sample"></a>サンプルをビルドするには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で、ソリューションを開きます。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
3.  Ctrl キーを押しながら F5 キーを押して、ソリューションをデバッグなしで実行します。  
  
### <a name="to-run-the-sample"></a>サンプルを実行するには  
  
-   [SDK コマンド プロンプト] ウィンドウで、IfElseWithRules\bin\debug フォルダー (Visual Basic バージョンのサンプルの場合は IfElseWithRules\bin フォルダー) にある .exe ファイルを実行します。このフォルダーは、サンプルのメイン フォルダーの下に作成されます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\IfElseWithRules`  
  
## <a name="see-also"></a>参照  
 <xref:System.Workflow.Activities.Rules>  
 <xref:System.Workflow.Activities.IfElseActivity>  
 <xref:System.Workflow.Activities.CodeActivity>  
 <xref:System.Workflow.Activities.Rules.RuleDefinitions>
