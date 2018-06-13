---
title: .NET Framework 3.5 ルールセットでの変数の使用
ms.date: 03/30/2017
ms.assetid: 27b56249-22fe-4252-840f-74c0d6c7a6b3
ms.openlocfilehash: 9fa6eaf58aaddc4673f08ec9a9001647a494877d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516857"
---
# <a name="using-variables-with-a-net-framework-35-ruleset"></a>.NET Framework 3.5 ルールセットでの変数の使用
このサンプルでは、<xref:System.Activities.Statements.Interop> アクティビティを使用するワークフローを作成し、ポリシーとルールを使用する、[!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] で記述されたカスタム アクティビティを統合する方法を示します。 このワークフローでは、カスタム アクティビティで公開されている依存プロパティに変数をバインドすることで、カスタム アクティビティにデータを渡します。  
  
## <a name="sample-walkthrough"></a>サンプルのチュートリアル  
  
#### <a name="to-examine-travelrulelibrary"></a>TravelRuleLibrary を検証するには  
  
1.  Visual Studio を使用して、InteropWith35RuleSet.sln ソリューション ファイルを開きます。  
  
2.  ワークフロー デザイナーで TravelRuleSet.cs を開きます。  
  
     <xref:System.Workflow.Activities.PolicyActivity> を含むカスタム シーケンシャル アクティビティが表示されます。  
  
3.  ルールを検証するには、DiscountPolicy ポリシー アクティビティをダブルクリックします。  
  
     ルール エディターがポップアップで開き、ルールが表示されます。  
  
4.  右クリックして、`DiscountPolicy`を選択し、**コードの表示**アクティビティの c# コードの横にあるコードをチェックするオプションです。  
  
     `DiscountLevel` の依存関係プロパティの設定を確認します。 これは [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] の引数と同じです。 引数の詳細については、次を参照してください。[変数と引数](../../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md)です。  
  
## <a name="interopwith35ruleset"></a>InteropWith35RuleSet  
 これは、<xref:System.Activities.Statements.Interop> アクティビティを使用して、`TravelRuleLibrary` プロジェクトで作成されたカスタム ルール セットと統合するシーケンシャル ワークフロー プロジェクトです。 変数は、最上位レベルの <xref:System.Activities.Statements.Sequence> アクティビティで作成されます。 <xref:System.Activities.Statements.Interop> アクティビティは、`TravelRuleSet` アクティビティと統合するために使用されます。 <xref:System.Activities.Statements.Sequence> で宣言された変数は、依存プロパティにバインドするために使用されます。  
  
## <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、InteropWith35RuleSet.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`