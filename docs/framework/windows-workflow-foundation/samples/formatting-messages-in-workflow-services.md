---
title: "ワークフロー サービスでのメッセージの書式設定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d15d44b-20f8-4cb7-bd4f-598c32781ebc
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 726ce98f3fe11bbc3cd13d90cdae335c0741efe6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="formatting-messages-in-workflow-services"></a>ワークフロー サービスでのメッセージの書式設定
このサンプルでは、メッセージング アクティビティ (WF サービス) で使用できるユーザーの種類を示します。 サンプルのサービスは、簡単な費用承認サービスで、3 つの操作を公開します。 `ApproveExpense` はデータ コントラクト型を受け取り、既知の型を使用する方法を示します。 この操作では、費用の金額に基づいて `true` または `false` を返します。 `ApprovePO`XmlSerializer 型を受け取り、返します`true`または`false`費用の金額に基づいて。`ApprovedVendor` メッセージ コントラクト型を受け取り、返します`true`または`false`仕入先が承認された販売元の一覧にある場合、または、要求の送信元、財務部門 (経理部はどの販売元を使用できます)。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] でプロジェクト ソリューションを読み込み、プロジェクトをビルドします。  
  
2.  最初に、[ソリューションの基本ディレクトリ]\FormatterService\bin\debug\ に生成されたサービスを実行します。  
  
3.  2 番目に、[ソリューションの基本ディレクトリ]\FormatterClient\bin\debug に生成されたクライアント アプリケーションを実行します。  
  
4.  クライアントは、サービスで 3 つの操作を呼び出し、結果を出力します。 完了したら、Enter キーを押してクライアントを終了し、サービスを終了します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Formatter`