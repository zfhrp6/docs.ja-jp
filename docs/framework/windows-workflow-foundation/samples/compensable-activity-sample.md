---
title: "補正可能なアクティビティのサンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58f4898c-b2b8-44a4-9a73-3bef4da6d5ba
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8b6b8eff89ebded7681a88cc4b1aee877828e021
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="compensable-activity-sample"></a>補正可能なアクティビティのサンプル
このサンプルでは、`CompensableActivity` アクティビティを使用して、通常の実行中に特定のアクションに対して実行される作業、および必要に応じて後からアクションを補正するために実行する必要がある作業を定義する方法を示します。  サンプルの最初の部分では、[!INCLUDE[wf](../../../../includes/wf-md.md)] アクティビティを使用して `CompensableActivity` で補正可能な作業の単位を定義する方法と、これらの作業を正常に実行する方法を示します。  サンプルの 2 つ目の部分では、予期しないイベントが発生してワークフロー インスタンスがキャンセルされたときに、同じ単位の補正可能な作業が自動的に補正を引き継ぐ方法を示します。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  Visual Studio 2010 を使用して、CompensableActivity.sln を開きます。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
3.  F5 キーを押してアプリケーションを実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\BasicCompensableActivity`