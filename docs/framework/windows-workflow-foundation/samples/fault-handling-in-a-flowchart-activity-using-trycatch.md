---
title: "TryCatch を使用した Flowchart アクティビティでのエラー処理 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# TryCatch を使用した Flowchart アクティビティでのエラー処理
このサンプルでは、複雑な制御フロー アクティビティ内で <xref:System.Activities.Statements.TryCatch> アクティビティを使用する方法を示します。  
  
 このサンプルでは、販売促進コードに対応する式に基づいて割引率を計算する <xref:System.Activities.Statements.Flowchart> アクティビティに、販売促進コードと子供の数が変数として渡されます。このサンプルには、命令型コードとワークフロー デザイナー バージョンのサンプルが含まれています。  
  
 次の表で、`CreateFlowchartWithFaults` アクティビティの変数の詳細を説明します。  
  
|パラメーター|説明|  
|------------|--------|  
|promoCode|販売促進コード。型: String<br /><br /> 使用できる値は次のとおりです \(かっこ内は値の説明\)。<br /><br /> -   Single \(独身\)<br />-   MNK \(子供のいない既婚者\)<br />-   MWK \(子供のいる既婚者\)|  
|numKids|子供の数。型: int|  
  
 `CreateFlowchartWithFaults` アクティビティでは、`promoCode` 引数を有効にする <xref:System.Activities.Statements.FlowSwitch%601> アクティビティを使用し、次の式を使って割引率を計算します。  
  
|`promoCode` の値|割引率 \(%\)|  
|--------------------|---------------|  
|Single|10|  
|MNK|15|  
|MWK|15 \+ \(1 – 1\/`numberOfKids`\)\*10 **Note:**  この計算では、<xref:System.DivideByZeroException> がスローされる可能性があります。そのため、割引率の計算は、<xref:System.DivideByZeroException> 例外をキャッチして割引率をゼロに設定する <xref:System.Activities.Statements.TryCatch> アクティビティでラップされます。|  
  
#### このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、FlowchartWithFaultHandling.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、F5 キーを押します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`  
  
## 参照  
 [Flowchart のワークフロー](../../../../docs/framework/windows-workflow-foundation//flowchart-workflows.md)   
 [例外](../../../../docs/framework/windows-workflow-foundation//exceptions.md)