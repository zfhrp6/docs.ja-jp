---
title: ".NET Framework 3.5 ルールセットでの変数の使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 27b56249-22fe-4252-840f-74c0d6c7a6b3
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# .NET Framework 3.5 ルールセットでの変数の使用
このサンプルでは、<xref:System.Activities.Statements.Interop> アクティビティを使用するワークフローを作成し、ポリシーとルールを使用する、[!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] で記述されたカスタム アクティビティを統合する方法を示します。このワークフローでは、カスタム アクティビティで公開されている依存プロパティに変数をバインドすることで、カスタム アクティビティにデータを渡します。  
  
## サンプルのチュートリアル  
  
#### TravelRuleLibrary を検証するには  
  
1.  [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] を使用して、InteropWith35RuleSet.sln ソリューション ファイルを開きます。  
  
2.  ワークフロー デザイナーで TravelRuleSet.cs を開きます。  
  
     <xref:System.Workflow.Activities.PolicyActivity> を含むカスタム シーケンシャル アクティビティが表示されます。  
  
3.  ルールを検証するには、DiscountPolicy ポリシー アクティビティをダブルクリックします。  
  
     ルール エディターがポップアップで開き、ルールが表示されます。  
  
4.  アクティビティのコード側 C\# コードを検証するには、`DiscountPolicy` を右クリックして **\[コードの表示\]** をクリックします。  
  
     `DiscountLevel` の依存関係プロパティの設定を確認します。これは [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] の引数と同じです。引数 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[変数と引数](../../../../docs/framework/windows-workflow-foundation//variables-and-arguments.md)」を参照してください。  
  
## InteropWith35RuleSet  
 これは、<xref:System.Activities.Statements.Interop> アクティビティを使用して、`TravelRuleLibrary` プロジェクトで作成されたカスタム ルール セットと統合するシーケンシャル ワークフロー プロジェクトです。変数は、最上位レベルの <xref:System.Activities.Statements.Sequence> アクティビティで作成されます。<xref:System.Activities.Statements.Interop> アクティビティは、`TravelRuleSet` アクティビティと統合するために使用されます。<xref:System.Activities.Statements.Sequence> で宣言された変数は、依存プロパティにバインドするために使用されます。  
  
## このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、InteropWith35RuleSet.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`  
  
## 参照