---
title: "式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 43a85905-77b5-4893-bb38-1cb9b293d69d
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# 式
このサンプルでは、基本的な式をワークフローで使用する方法を示します。このサンプルは、架空の会社の 2 人の従業員の基本給を計算するワークフローで構成されます。`Employee` および `SalaryStats` という 2 つのクラスが Employee.cs と SalaryStats.cs で定義されています。これらのクラスをワークフローで使用して、複合型の変数のプロパティに対する単純な数値演算と文字列操作を実行する方法を示します。  
  
 給与計算ワークフローは、2 つの作成スタイルを示すために XAML と C\# の両方で定義されています。XAML バージョンは SalaryCalculation.xaml にあり、ワークフロー デザイナーで表示および編集できます。C\# バージョンは Program.cs にあります。XAML で使用されている式は Visual Basic 構文に準拠しており、<xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> 式アクティビティと <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> 式アクティビティを使用して実行されます。Visual Basic の式[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[式](http://go.microsoft.com/fwlink/?LinkId=165912)」を参照してください。一方、C\# の式はラムダ式で記述されており、<xref:System.Activities.Expressions.LambdaValue%601> 式アクティビティと <xref:System.Activities.Expressions.LambdaReference%601> 式アクティビティが使用されます。ラムダ式で記述されているため、C\# コンパイラで構文の強調表示や静的な検証を行うことができます。C\# のラムダ式 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]、[ラムダ式 \(C\# プログラミング ガイド\)](http://go.microsoft.com/fwlink/?LinkId=182082) を参照してください。ワーク フローで Visual Basic を使用してコードで書かれれば、Visual Basic ラムダ式が使用されます。Visual Basic のラムダ式 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[ラムダ式 \(Visual Basic\)](http://go.microsoft.com/fwlink/?LinkId=152437)」を参照してください。命令型コードを使用してワークフローを作成する方法 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[命令型コードを使用してワークフロー、アクティビティ、および式を作成する方法](../../../../docs/framework/windows-workflow-foundation//authoring-workflows-activities-and-expressions-using-imperative-code.md)」を参照してください。  
  
#### サンプルを実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で Expressions.sln ソリューションを開きます。  
  
2.  CTRL キーと SHIFT キーを押したまま B キーを押してソリューションをビルドするか、**\[ビルド\]** メニューの **\[ソリューションのビルド\]** を選択します。  
  
    > [!NOTE]
    >  Visual Studio デザイナーで SalaryCalculation.xaml を開くには、先にプロジェクトをコンパイルして、`Employee` クラスと `SalaryStats` クラスをデザイナーで使用できるようにする必要があります。  
  
3.  ビルドが完了したら、F5 キーを押すか、**\[デバッグ\]** メニューの **\[デバッグ開始\]** をクリックします。または、Ctrl キーを押しながら F5 キーを押すか、**\[デバッグ\]** メニューの **\[デバッグなしで開始\]** をクリックして、デバッグ機能なしで実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Expressions`  
  
## 参照