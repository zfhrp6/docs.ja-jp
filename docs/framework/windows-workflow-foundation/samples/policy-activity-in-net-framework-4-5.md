---
title: ".NET Framework 4.5 のポリシー アクティビティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e375e0c-d7c1-4d69-88ab-36d52db0aa7e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 68c81b81ac8070cff539b52c75e1cd7ffb3e54b5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="policy-activity-in-net-framework-45"></a>.NET Framework 4.5 のポリシー アクティビティ
Policy4 アクティビティは、[!INCLUDE[wf2](../../../../includes/wf2-md.md)] (WF 3.5) [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] オブジェクト内の <xref:System.Workflow.Activities.Rules.RuleSet> を、WF 3.5 に付属しているルール エンジンを使用して [!INCLUDE[wf2](../../../../includes/wf2-md.md)] (WF 4.5) の [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] で直接使用できるようにします。 このアクティビティを使用すると、WF 3.5 <xref:System.Workflow.Activities.Rules.RuleSet> を作成して実行できます。 Windows Workflow Foundation の一部として用意されている WF 3.5 ルール エンジンの[!INCLUDE[crabout](../../../../includes/crabout-md.md)]については、「Windows Workflow Foundation ルール エンジンの紹介」を参照してください。 移行の詳細についての WF ルール[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]をお読みください[移行のガイダンス](../../../../docs/framework/windows-workflow-foundation/migration-guidance.md)です。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-Policy4`  
  
## <a name="projects-in-this-sample"></a>このサンプルのプロジェクト  
  
|プロジェクト名|説明|メイン ファイル|  
|------------------|-----------------|----------------|  
|Policy4|Policy4 アクティビティとその [!INCLUDE[wf1](../../../../includes/wf1-md.md)] デザイナーが含まれます。|**Policy4.cs**: Policy4 アクティビティ定義。<br /><br /> **PolicyDesigner.xaml**: Policy4 アクティビティのカスタム デザイナーです。 ルール エディターを使用して ([RuleSetDialog クラス](http://go.microsoft.com/fwlink/?LinkId=150378)) から[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ルール エンジン。|  
|ImperativeCodeClientSample|命令型 C# コードで、Policy4 アプリケーションを使用してワークフローを構成および実行するサンプル クライアント アプリケーションです ([!INCLUDE[wf1](../../../../includes/wf1-md.md)] デザイナーは不使用)。|**ApplyDiscount.rules**: ファイルと[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ルール定義。<br /><br /> **Order.cs**: 顧客の注文を表す型。 ルールはこの型のオブジェクトに適用されます。<br /><br /> **Program.cs**: を構成し、ワークフローを Order オブジェクトのインスタンスにして、ApplyDiscount.rules で定義されたルールを適用する Policy4 アクティビティを実行します。<br /><br /> **App.config**: ルール ファイルのパスを持つ構成ファイル。|  
|DesignerClientSample|[!INCLUDE[wf1](../../../../includes/wf1-md.md)] デザイナーで、Policy4 アプリケーションを使用してワークフローを構成および実行するサンプル クライアント アプリケーションです。|**Sequence1.xaml**: Policy4 アクティビティを使用してルール評価を実行するシーケンシャル ワークフローです。<br /><br /> `Program.cs`: Sequence1.xaml で定義されているワークフローのインスタンスを実行します。|  
  
## <a name="the-policy4-activity"></a>Policy4 アクティビティ  
 Policy4 アクティビティは、ワークフローで <xref:System.Activities.NativeActivity%601> RuleSet を実行できるようにする [!INCLUDE[wf1](../../../../includes/wf1-md.md)] の派生クラスです。 次のコード例は、このアクティビティのパブリック OM の簡略化された定義です。  
  
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
|--------------|-----------------|  
|RuleSet|WF [RuleSet クラス](http://go.microsoft.com/fwlink/?LinkId=150379)アクティビティが実行されるときに評価される .NET Framework 3.5 用です。|  
|TargetObject|対象となるオブジェクト内のルール、 [RuleSet クラス](http://go.microsoft.com/fwlink/?LinkId=150379)が評価されます。|  
|ValidationError|によって返される検証エラーの一覧、[!INCLUDE[wf1](../../../../includes/wf1-md.md)]を検証するときに、.NET Framework 3.5 用のルール エンジン、 [RuleSet クラス](http://go.microsoft.com/fwlink/?LinkId=150379)に対して実行する前に、ターゲット オブジェクト。|  
  
## <a name="policy4-activity-designer"></a>Policy4 アクティビティ デザイナー  
 Policy4 デザイナーを使用すると、コードを記述することなく Policy4 アクティビティを構成できます。 ソリューションを構築した後にあります、ツールボックスのセクションで**Microsoft.Samples.Activities.Rules**です。  
  
 WF デザイナーでは、対象オブジェクトや RuleSet を構成できます。 ときに、 **Edit RuleSet**ボタンをクリックして、WF [RuleSetDialog クラス](http://go.microsoft.com/fwlink/?LinkId=150378)の[!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)]が表示されます。 このダイアログは、ホストを変更した [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] ルール エディターです。 このエディターを使用して、Policy4 アクティビティで実行するルールを作成および編集します。  
  
## <a name="using-this-sample"></a>このサンプルの使用  
 このサンプルを実行するのに特別な設定は必要ありません。 Visual Studio でソリューションを開き、F5 キーを押してアプリケーションを実行するだけです。  
  
 このサンプルには、ImperativeCodeClientSample と DesignerClientSample の 2 つのクライアント アプリケーションがあります。 ImperativeCodeClientSample クライアントは、C# 命令型コードを使用して Policy4 アクティビティを構成および実行する方法を示します。 DesignerClientSample は、デザイナーを使用して Policy4 アクティビティを構成および実行する方法を示します。  
  
#### <a name="to-run-the-imperativecodeclientsample-client-application"></a>ImperativeCodeClientSample クライアント アプリケーションを実行するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、Policy4Sample.sln ソリューション ファイルを開きます。  
  
2.  **ソリューション エクスプ ローラー**を右クリックし、 **ImperativeCodeClientSample**プロジェクトを選択し、**スタートアップ プロジェクトとして設定**です。  
  
3.  プロジェクトを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
#### <a name="to-run-the-imperativecodeclientsample-client-application"></a>ImperativeCodeClientSample クライアント アプリケーションを実行するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、Policy4Sample.sln ソリューション ファイルを開きます。  
  
2.  **ソリューション エクスプ ローラー**を右クリックし、 **DesignerClientSample**プロジェクト。  
  
    -   選択**スタートアップ プロジェクトとして設定**です。  
  
3.  プロジェクトをコンパイルするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
4.  プロジェクトを実行するには、Ctrl キーを押しながら F5 キーを押します。