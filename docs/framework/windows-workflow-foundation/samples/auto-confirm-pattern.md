---
title: "自動確認パターン | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 668aec65-78d3-4636-9c7b-deed643a18f9
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 自動確認パターン
このサンプルは、カスタム `AutoConfirmScope` アクティビティを示す 3 つのシナリオで構成されます。1 つ目のサンプルでは、2 番目と 3 番目の補正可能なアクティビティが `AutoConfirmScope` で入れ子になっている 4 つの補正可能なアクティビティのシーケンスが正常に実行された場合を示します。2 つ目のサンプルでは、同じシーケンスを示しますが、4 番目の <xref:System.Activities.Statements.CompensableActivity> の実行後に例外が発生します。3 つ目のシナリオでは、同じシーケンスを示しますが、2 番目の <xref:System.Activities.Statements.CompensableActivity> の完了後に `AutoConfirmScope` で例外が発生します。  
  
 このサンプルでは、スコープが正常に完了したときにすべての補正可能な子アクティビティが確認される自動確認パターンを示します。このパターンでは、すべての補正可能な子アクティビティの有効期間が定義され、この期間を過ぎるとこれらのアクティビティは補正または確認できなくなります。  
  
 スコープは、<xref:System.Activities.Statements.TryCatch.Try%2A> が内部 <xref:System.Activities.Statements.CompensableActivity> である <xref:System.Activities.Statements.TryCatch> で構成されます。`AutoConfirmScope` のユーザー指定の本文は、内部 <xref:System.Activities.Statements.CompensableActivity> の本文です。この内部 <xref:System.Activities.Statements.CompensableActivity> が完了すると、<xref:System.Activities.Statements.CompensationToken> が out 引数として生成されます。`AutoConfirmScope` は、<xref:System.Activities.Statements.TryCatch.Finally%2A> を使用してトークンが生成されているかどうかをチェックし、生成されている場合は内部 <xref:System.Activities.Statements.CompensableActivity> を確認します。内部 <xref:System.Activities.Statements.CompensableActivity> は、本文に存在する補正可能なアクティビティの既定の補正を呼び出します。  
  
 1 つ目のシナリオでは、ワークフローが正常に実行された場合を示します。ワークフローが完了して 1 番目と 4 番目の補正可能なアクティビティが確認されるときには、2 番目と 3 番目の補正可能なアクティビティは既に確認されています。ここでは、確認順序は 3、2、4、1 となります。  
  
 2 つ目のシナリオでは、4 つの補正可能なアクティビティの完了後に例外が発生した場合を示します。補正可能なアクティビティ 2 および 3 は既に確認されているので影響を受けませんが、1 および 4 は補正されます。ここでは、3 が確認され、2 が確認され、4 が補正されて 1 が補正されます。  
  
 最後のシナリオでは、`AutoConfirmScope` が正常に実行されなかった場合を示します。このシナリオでは、2 番目の <xref:System.Activities.Statements.CompensableActivity> の完了後に例外が発生します。3 番目と 4 番目の補正可能なアクティビティは実行されていないので影響を受けません。スコープが正常に完了しなかったので、2 番目の <xref:System.Activities.Statements.CompensableActivity> は確認されません。ここでは、補正順序は 2、1 となります。  
  
#### このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、AutoConfirmSample.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Compensation\AutoConfirm`  
  
## 参照