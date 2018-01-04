---
title: "基本検証"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba1343cc-aaab-4ade-b0c0-1dd5063bf4ad
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b2712ca923d8608fe9e26dba380476993d35b6a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="basic-validation"></a>基本検証
このサンプルは、`CreateProduct` アクティビティで構成されています。このアクティビティでは、その `Cost` 引数が `Price` 引数以下であることを検証します。  
  
## <a name="sample-details"></a>サンプルの詳細  
 検証を使用する 2 人の作成者が存在します。1 人はアクティビティの検証ロジックを作成するアクティビティ作成者で、もう 1 人は、特定のワークフローで検証サービスを呼び出すワークフロー作成者です。 このシナリオでは、アクティビティ作成者はアクティビティのすべてのインスタンスで、コストが必ず価格以下になるように強制します。  
  
 アクティビティ作成者 (アクティビティ内) は、次を行う必要があります。  
  
-   制約 (`PriceGreaterThanCost`) を作成します。 ここには、すべての検証ロジックが存在します。  
  
-   `System.Activities.CodeActivity.OnGetConstraints()` をオーバーライドし、制約 (`PriceGreaterThanCost`) を制約 <xref:System.Collections.IList> に追加します。  
  
 ワークフロー作成者 (メイン プログラム) は次を実行する必要があります。  
  
-   検証するアクティビティのインスタンスを含むワークフローを作成します (`CreateProduct`)。  
  
-   <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> を呼び出すと、<xref:System.Activities.Validation.ValidationResults> の <xref:System.Activities.Validation.ValidationError> コレクションが返されます。  
  
-   (省略可能) <xref:System.Activities.Validation.ValidationError> オブジェクトを出力します。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で BasicValidation.sln サンプル ソリューションを開きます。  
  
2.  ソリューションをビルドして実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\BasicValidation`