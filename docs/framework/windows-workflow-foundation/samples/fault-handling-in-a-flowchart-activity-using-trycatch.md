---
title: TryCatch を使用した Flowchart アクティビティでのエラー処理
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: cc7630be868a5bdc1a07e8d935e5dd3269b4ae22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a>TryCatch を使用した Flowchart アクティビティでのエラー処理
このサンプルでは、複雑な制御フロー アクティビティ内で <xref:System.Activities.Statements.TryCatch> アクティビティを使用する方法を示します。  
  
 このサンプルでは、販売促進コードに対応する式に基づいて割引率を計算する <xref:System.Activities.Statements.Flowchart> アクティビティに、販売促進コードと子供の数が変数として渡されます。 このサンプルには、命令型コードとワークフロー デザイナー バージョンのサンプルが含まれています。  
  
 次の表で、`CreateFlowchartWithFaults` アクティビティの変数の詳細を説明します。  
  
|パラメーター|説明|  
|----------------|-----------------|  
|promoCode|販売促進コード。 型: String<br /><br /> 使用できる値は次のとおりです (かっこ内は値の説明)。<br /><br /> 単一 (単一)<br />MNK (子供のいないで既婚。)<br />MWK (子供の既婚。)|  
|numKids|子供の数。 型: int|  
  
 `CreateFlowchartWithFaults` アクティビティでは、<xref:System.Activities.Statements.FlowSwitch%601> 引数を有効にする `promoCode` アクティビティを使用し、次の式を使って割引率を計算します。  
  
|`promoCode` の値|割引率 (%)|  
|--------------------------|--------------------|  
|Single|10|  
|MNK|16|  
|MWK|15 + (1 – 1/`numberOfKids`)\*10**注:** 可能性のある、この計算がスローすることが、<xref:System.DivideByZeroException>です。 そのため、割引率の計算は、<xref:System.Activities.Statements.TryCatch> 例外をキャッチして割引率をゼロに設定する <xref:System.DivideByZeroException> アクティビティでラップされます。|  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、FlowchartWithFaultHandling.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、F5 キーを押します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`  
  
## <a name="see-also"></a>関連項目  
 [Flowchart のワークフロー](../../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)  
 [例外](../../../../docs/framework/windows-workflow-foundation/exceptions.md)
