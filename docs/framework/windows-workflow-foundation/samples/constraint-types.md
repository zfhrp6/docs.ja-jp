---
title: "制約の種類"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6b246e6-1130-4698-9625-c5c42abcbfed
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 516733490dba459f452727d29320a366208b55fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="constraint-types"></a>制約の種類
このサンプルでは、ワークフローに制約を適用する 2 種類の方法を示します。1 つはアクティビティの内部 (ビルド) から適用する方法で、もう 1 つはアクティビティの外部 (ポリシー) から適用する方法です。 このシナリオでは、(サードパーティのソフトウェア会社の) アクティビティ作成者が 2 つの引数間のリレーションシップを検証します。 ここでは、コストが価格以下になるようにする必要があります。 これは、一般的な検証ビルド制約です。  
  
 次に、ショップ オーナーがこの一般的なアクティビティに検証を追加します。 ここでは、製品のほとんどを $9.99 以下にします。 したがって、`CreateProduct` アクティビティに基づくポリシー制約を使用します。  
  
 このサンプルでは、次の操作を行います。  
  
 アクティビティ作成者 (ビルド) は、次を行う必要があります。  
  
-   制約 (`PriceGreaterThanCost`) を作成します。 ここには、すべての検証ロジックが存在します。  
  
-   `System.Activities.CodeActivity.OnGetConstraints()` をオーバーライドし、制約 (`PriceGreaterThanCost`) を制約 <xref:System.Collections.IList> に追加します。  
  
 ワークフロー作成者 (ポリシー) は、次を行う必要があります。  
  
-   検証するアクティビティのインスタンスを含むワークフローを作成します (`CreateProduct`)。  
  
-   制約 (`MaxPrice`) を作成します。  
  
-   <xref:System.Activities.Validation.ValidationSettings> インスタンス (`validationSettings`) を作成し、制約 (`MaxPrice`) をコレクション `AdditionalConstraints` に追加します。 ここで、ワークフロー作成者は、シーケンスや並列などのアクティビティにポリシー制約を追加できます。  
  
-   <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> を呼び出すと、<xref:System.Activities.Validation.ValidationResults> オブジェクトの <xref:System.Activities.Validation.ValidationError> コレクションが返されます。  
  
-   (省略可能) <xref:System.Activities.Validation.ValidationError> オブジェクトを出力します。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で ConstraintTypes.sln サンプル ソリューションを開きます。  
  
2.  ソリューションをビルドして実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Validation\ConstraintLibrary`