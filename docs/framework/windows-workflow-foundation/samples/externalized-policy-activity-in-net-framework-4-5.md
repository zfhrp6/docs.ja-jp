---
title: ".NET Framework 4.5 の外部化されたポリシー アクティビティ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 92fd6f92-23a1-4adf-b96a-2754ea93ad3e
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# .NET Framework 4.5 の外部化されたポリシー アクティビティ
このサンプルでは、ExternalizedPolicy4 アクティビティによって既存の [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] [!INCLUDE[wf2](../../../../includes/wf2-md.md)] \(WF 3.5\) <xref:System.Workflow.Activities.Rules.RuleSet> オブジェクトを、WF 3.5 に付属しているルール エンジンを使用して [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] [!INCLUDE[wf2](../../../../includes/wf2-md.md)] \(WF 4.5\) で直接実行できるようにする方法を示します。このアクティビティを使用すると、既存の WF 3.5 <xref:System.Workflow.Activities.Rules.RuleSet> を開いて実行できます。[!INCLUDE[crabout](../../../../includes/crabout-md.md)] Windows Workflow Foundation の一部として用意されている WF 3.5 ルール エンジンについては、[「Windows Workflow Foundation ルール エンジンの紹介」](http://go.microsoft.com/fwlink/?LinkId=166079) を参照してください。[!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] の [!INCLUDE[wf1](../../../../includes/wf1-md.md)] へのルール移行については、[移行のガイドライン](../../../../docs/framework/windows-workflow-foundation//migration-guidance.md) にあるガイドラインを参照してください。  
  
## このサンプルのプロジェクト  
  
||||  
|-|-|-|  
|プロジェクト名|説明|メイン ファイル|  
|ExternalizedPolicy4|ExternalizedPolicy4 アクティビティとその WF 4.5 デザイナーが含まれます。|**ExternalizedPolicy4.cs**: アクティビティ定義です。<br /><br /> **ExternalizedPolicy4Designer.xaml**: ExternalizedPolicy4 アクティビティのカスタム デザイナーです。WF 3.5 ルール エンジンからルール エディター \(<xref:System.Workflow.Activities.Rules.Design.RuleSetDialog>\) を使用します。|  
|ImperativeCodeClientSample|命令型 C\# コードで、ExternalizedPolicy4 アプリケーションを使用してワークフローを構成および実行するサンプル クライアント アプリケーションです \(デザイナーは不使用\)。|**ApplyDiscount.rules**: [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ルール定義が記述されたファイルです。<br /><br /> **Order.cs**: 顧客の注文を表す型です。ルールはこの型のオブジェクトに適用されます。<br /><br /> **Program.cs**: Policy4 アクティビティを使用するワークフローを構成および実行して、ApplyDiscount.rules で定義されているルールを Order オブジェクトのインスタンスに適用します。<br /><br /> App.config: ルール ファイルのパスが記述された構成ファイルです。|  
|DesignerClientSample|[!INCLUDE[wf1](../../../../includes/wf1-md.md)] デザイナーで、ExternalPolicy4 アプリケーションを使用してワークフローを構成および実行するサンプル クライアント アプリケーションです。|**Sequence1.xaml**: Policy4 アクティビティを使用してルール評価を実行するシーケンシャル ワークフローです。<br /><br /> **Program.cs**: Sequence1.xaml で定義されているワークフローのインスタンスを実行します。|  
  
## ExternalizedPolicy4 アクティビティ  
 ExternalizedPolicy4 アクティビティは、WF 4.5 のワークフロー内で WF 3.5 <xref:System.Workflow.Activities.Rules.RuleSet> オブジェクトを実行できるようにする <xref:System.Activities.NativeActivity> です。次のコード例は、このアクティビティのパブリック オブジェクト モデルの簡略化された定義です。  
  
```  
public class ExternalizedPolicy4Activity<TResult>: CodeActivity  
{  
    public string RulesFilePath   
  
    public string RuleSetName           
  
    [RequiredArgument]  
    public InArgument<T> TargetObject   
  
    [RequiredArgument]  
    public OutArgument<T> ResultObject   
  
    public OutArgument<ValidationErrorCollection> ValidationErrors   
}  
```  
  
|||  
|-|-|  
|プロパティ|説明|  
|RuleSetFilePath|アクティビティが実行されるときに評価される .NET Framework 3.5 <xref:System.Workflow.Activities.Rules.RuleSet> ファイルのパスです。|  
|RuleSetName|.rules ファイル内で使用される <xref:System.Workflow.Activities.Rules.RuleSet> の名前です。|  
|TargetObject|<xref:System.Workflow.Activities.Rules.RuleSet> の <xref:System.Workflow.Activities.Rules.Rule> オブジェクトを評価する対象のオブジェクトです。|  
|ResultObject|ルールが適用された後の結果として得られるオブジェクトです \(たとえば、ルールが Input 引数に対して適用され、結果が Result 引数に格納されます\)。|  
|ValidationError|実行前に対象オブジェクトに対して <xref:System.Workflow.Activities.Rules.RuleSet> を検証するときに、WF 3.5 ルール エンジンから返される検証エラーのリストです。|  
  
## ExternalizedPolicy4 アクティビティ デザイナー  
 ExternalizedPolicy4 デザイナーを使用すると、コードを記述せずに、既存の RuleSet を使用するようにアクティビティを構成できます。.rules ファイルのパスを設定し、使用する <xref:System.Workflow.Activities.Rules.RuleSet> の名前を指定するだけです。また、<xref:System.Workflow.Activities.Rules.RuleSet> を変更することもできます。ソリューションをビルドすると、Microsoft.Samples.Activities.Rules セクションのツールボックス内からこのデザイナーを使用できるようになります。このデザイナーでは、.rules ファイルと <xref:System.Workflow.Activities.Rules.RuleSet> を選択できます。**\[Edit RuleSet\]** ボタンをクリックすると、WF 3.5 <xref:System.Workflow.Activities.Rules.Design.RuleSetDialog> が表示されます。このダイアログはホストを変更した WF 3.5 ルール エディターであり、ExternalizedPolicy4 アクティビティで実行するルールを表示および編集するために使用します。  
  
## Policy4 と ExternalPolicy4  
 [.NET Framework 4.5 のポリシー アクティビティ](../../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md)を使用すると、WF 4.5 のワークフロー内で .NET Framework 3.5 RuleSet を作成して実行できます。<xref:System.Workflow.Activities.Rules.RuleSet> は、Policy4 アクティビティの XAML 定義でインラインでシリアル化されます。ExternalizedPolicy4 サンプルでは、既存の外部 <xref:System.Workflow.Activities.Rules.RuleSet> \(.rules ファイル内に格納\) を使用する方法を示します。  
  
## このサンプルの使用  
 このサンプルを実行するのに特別な設定は必要ありません。[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] でソリューションを開き、F5 キーを押してアプリケーションを実行します。  
  
 このサンプルには、ImperativeCodeClientSample と DesignerClientSample の 2 つのクライアント アプリケーションがあります。ImperativeCodeClientSample クライアントは、C\# 命令型コードを使用して ExternalizedPolicy4 アクティビティを構成および実行する方法を示します。DesignerClientSample は、デザイナーを使用して ExternalizedPolicy4 アクティビティを構成および実行する方法を示します。  
  
#### ImperativeCodeClientSample アプリケーションを実行するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、Policy4sample.sln ソリューション ファイルを開きます。  
  
2.  **ソリューション エクスプローラー**で、**ImperativeCodeClientSample** プロジェクトを右クリックし、**\[スタートアップ プロジェクトに設定\]** をクリックします。  
  
3.  プロジェクトを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
#### DesignerClientSample アプリケーションを実行するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、Policy4sample.sln ソリューション ファイルを開きます。  
  
2.  **ソリューション エクスプローラー**で、**DesignerClientSample** プロジェクトを右クリックし、**\[スタートアップ プロジェクトに設定\]** をクリックします。  
  
3.  Ctrl キーと Shift キーを押しながら B キーを押して、プロジェクトをコンパイルします。  
  
4.  プロジェクトを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-ExternalizedPolicy4`