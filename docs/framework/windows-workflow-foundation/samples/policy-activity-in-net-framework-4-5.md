---
title: ".NET Framework 4.5 のポリシー アクティビティ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8e375e0c-d7c1-4d69-88ab-36d52db0aa7e
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# .NET Framework 4.5 のポリシー アクティビティ
Policy4 アクティビティは、[!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] \(WF 3.5\) <xref:System.Workflow.Activities.Rules.RuleSet> オブジェクト内の [!INCLUDE[wf2](../../../../includes/wf2-md.md)] を、WF 3.5 に付属しているルール エンジンを使用して [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] \(WF 4.5\) の [!INCLUDE[wf2](../../../../includes/wf2-md.md)] で直接使用できるようにします。このアクティビティを使用すると、WF 3.5 <xref:System.Workflow.Activities.Rules.RuleSet> を作成して実行できます。Windows Workflow Foundation の一部として用意されている WF 3.5 ルール エンジン[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「Windows Workflow Foundation ルール エンジンの紹介」を参照してください。[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] へのルール移行の詳細については、「[移行のガイドライン](../../../../docs/framework/windows-workflow-foundation//migration-guidance.md)」を参照してください。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-Policy4`  
  
## このサンプルのプロジェクト  
  
|プロジェクト名|説明|メイン ファイル|  
|-------------|--------|--------------|  
|Policy4|Policy4 アクティビティとその [!INCLUDE[wf1](../../../../includes/wf1-md.md)] デザイナーが含まれます。|**Policy4.cs**: Policy4 アクティビティ定義です。<br /><br /> **PolicyDesigner.xaml**: Policy4 アクティビティのカスタム デザイナーです。[!INCLUDE[wf1](../../../../includes/wf1-md.md)] ルール エンジンからルール エディター \([RuleSetDialog クラス](http://go.microsoft.com/fwlink/?LinkId=150378)\) を使用します。|  
|ImperativeCodeClientSample|命令型 C\# コードで、Policy4 アプリケーションを使用してワークフローを構成および実行するサンプル クライアント アプリケーションです \([!INCLUDE[wf1](../../../../includes/wf1-md.md)] デザイナーは不使用\)。|**ApplyDiscount.rules**: [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ルール定義が記述されたファイルです。<br /><br /> **Order.cs**: 顧客の注文を表す型です。ルールはこの型のオブジェクトに適用されます。<br /><br /> **Program.cs**: Policy4 アクティビティを使用するワークフローを構成および実行して、ApplyDiscount.rules で定義されているルールを Order オブジェクトのインスタンスに適用します。<br /><br /> **App.config**: ルール ファイルのパスが記述された構成ファイルです。|  
|DesignerClientSample|[!INCLUDE[wf1](../../../../includes/wf1-md.md)] デザイナーで、Policy4 アプリケーションを使用してワークフローを構成および実行するサンプル クライアント アプリケーションです。|**Sequence1.xaml**: Policy4 アクティビティを使用してルール評価を実行するシーケンシャル ワークフローです。<br /><br /> `Program.cs`: Sequence1.xaml で定義されているワークフローのインスタンスを実行します。|  
  
## Policy4 アクティビティ  
 Policy4 アクティビティは、ワークフローで [!INCLUDE[wf1](../../../../includes/wf1-md.md)] RuleSet を実行できるようにする <xref:System.Activities.NativeActivity%601> の派生クラスです。次のコード例は、このアクティビティのパブリック OM の簡略化された定義です。  
  
```csharp  
  
public class Policy4Activity<TResult>: NativeActivity<TResult>  
{  
    public RuleSet RuleSet  
  
    [IsRequired]  
    public InArgument Input  
  
    public OutArgument<ValidationErrorCollection> ValidationErrors  
}  
```  
  
|プロパティ|説明|  
|-----------|--------|  
|RuleSet|アクティビティが実行されるときに評価される、.NET Framework 3.5 の WF [RuleSet クラス](http://go.microsoft.com/fwlink/?LinkId=150379)です。|  
|TargetObject|[RuleSet クラス](http://go.microsoft.com/fwlink/?LinkId=150379)の Rules を評価する対象のオブジェクトです。|  
|ValidationError|実行前に対象オブジェクトに対して [RuleSet クラス](http://go.microsoft.com/fwlink/?LinkId=150379)を検証するときに、.NET Framework 3.5 の [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ルール エンジンから返される検証エラーのリストです。|  
  
## Policy4 アクティビティ デザイナー  
 Policy4 デザイナーを使用すると、コードを記述することなく Policy4 アクティビティを構成できます。ソリューションをビルドすると、**Microsoft.Samples.Activities.Rules** セクションのツールボックス内からこのデザイナーを使用できるようになります。  
  
 WF デザイナーでは、対象オブジェクトや RuleSet を構成できます。**\[Edit RuleSet\]** ボタンをクリックすると、[!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] の WF [RuleSetDialog クラス](http://go.microsoft.com/fwlink/?LinkId=150378)が表示されます。このダイアログは、ホストを変更した [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] ルール エディターです。このエディターを使用して、Policy4 アクティビティで実行するルールを作成および編集します。  
  
## このサンプルの使用  
 このサンプルを実行するのに特別な設定は必要ありません。Visual Studio でソリューションを開き、F5 キーを押してアプリケーションを実行するだけです。  
  
 このサンプルには、ImperativeCodeClientSample と DesignerClientSample の 2 つのクライアント アプリケーションがあります。ImperativeCodeClientSample クライアントは、C\# 命令型コードを使用して Policy4 アクティビティを構成および実行する方法を示します。DesignerClientSample は、デザイナーを使用して Policy4 アクティビティを構成および実行する方法を示します。  
  
#### ImperativeCodeClientSample クライアント アプリケーションを実行するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、Policy4Sample.sln ソリューション ファイルを開きます。  
  
2.  **ソリューション エクスプローラー**で、**ImperativeCodeClientSample** プロジェクトを右クリックし、**\[スタートアップ プロジェクトに設定\]** をクリックします。  
  
3.  プロジェクトを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
#### ImperativeCodeClientSample クライアント アプリケーションを実行するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、Policy4Sample.sln ソリューション ファイルを開きます。  
  
2.  **ソリューション エクスプローラー**で、**DesignerClientSample** プロジェクトを右クリックします。  
  
    -   **\[スタートアップ プロジェクトに設定\]** をクリックします。  
  
3.  プロジェクトをコンパイルするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
4.  プロジェクトを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
## 参照