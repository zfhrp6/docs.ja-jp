---
title: "制限された並列 ForEach | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 制限された並列 ForEach
`ThrottleParallelForEach` アクティビティは、実行する同時分岐の数を制限するための同時実行要因を設定できるという 1 つの例外を除き、<xref:System.Activities.Statements.ParallelForEach> アクティビティと似ていることについて示します。`ThrottleParallelForEach` アクティビティは、<xref:System.Activities.NativeActivityContext> クラスを介してのみアクセスできる他のアクティビティ \(子アクティビティ\) をスケジュールする必要があるため、<xref:System.Activities.NativeActivity> クラスから派生します。  
  
## プロジェクト  
  
||||  
|-|-|-|  
|**プロジェクト名**|**説明**|**メイン ファイル**|  
|ThrottledParallelForEach|`ThrottledParallelForEach` アクティビティとそのデザイナーが含まれます。|ThrottledParallelForEach.cs<br /><br /> `ThrottledParallelForEach` アクティビティ定義。|  
|CodeTestClient|命令型コードを使用して、`ThrottledParallelForEach` を含むワークフローを構成および実行するサンプル クライアント アプリケーション。|Program.cs<br /><br /> サンプル ワークフローのインスタンスを定義および実行します。|  
  
#### このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、ThrottledParallelForEach.sln ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、F5 キーを押します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`  
  
## 参照