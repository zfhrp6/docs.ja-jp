---
title: "3.5 ルール セットとの相互運用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 969f3295-d874-428c-a9c6-623e3d578e51
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 854aeac936d3f911f2613c6e315ab81347f64a25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="interop-with-35-rule-set"></a>3.5 ルール セットとの相互運用
このサンプルでの使用、<xref:System.Activities.Statements.Interop>アクティビティのカスタム アクティビティと統合する[!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)]を使用して<!--zz <xref:System.Workflow.Activities.Policy> -->`System.Workflow.Activities.Policy`とルール。 このサンプルでは、カスタム アクティビティで公開されている依存プロパティに [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 変数をバインドすることで、カスタム アクティビティにデータを渡します。  
  
## <a name="requirements"></a>必要条件  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
2.  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]  
  
3.  [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]  
  
## <a name="demonstrates"></a>使用例  
 <xref:System.Activities.Statements.Interop>アクティビティ、 <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy`でアクティビティ[!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)]依存関係プロパティを持つ  
  
## <a name="discussion"></a>説明  
 このサンプルでは、[!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] アクティビティと統合するための統合シナリオの 1 つを示します。 このサンプルが含まれています、[!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)]を呼び出すカスタム アクティビティ、 <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy`アクティビティ。  
  
## <a name="travelrulelibrary"></a>TravelRuleLibrary  
 デザイナーで TravelRuleSet.cs を開くと、次のようにポリシー アクティビティを含むカスタムのシーケンシャル アクティビティが示されます。  
  
 ![Interop アクティビティ](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulespolicy.jpg "InteropRulesPolicy")  
  
 ダブルクリックして、 **DiscountPolicy**ポリシー アクティビティをルールを検証します。 ルール エディターが表示され、ルールが表示されます。  
  
 ![ルール セット エディター](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesruleseteditor.jpg "InteropRulesRuleSetEditor")  
  
 右クリックし、 **DiscountPolicy**アクティビティを選択、**コードの表示**コード側 c# コードをこのアクティビティと共に使用するにはオプションです。 `DiscountLevel` の依存関係プロパティの設定を確認します。 これは、<xref:System.Activities.Argument> の [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] と同じです。  
  
```  
public static DependencyProperty DiscountLevelProperty = DependencyProperty.Register("DiscountLevel", typeof(int), typeof(TravelRuleSet));  
  
[DescriptionAttribute("DiscountLevel")]  
[CategoryAttribute("DiscountLevel Category")]  
[BrowsableAttribute(true)]  
[DesignerSerializationVisibilityAttribute(DesignerSerializationVisibility.Visible)]  
public int DiscountLevel  
{  
   get  
   {  
return ((int)base.GetValue(TravelRuleSet.DiscountLevelProperty)));  
   }  
   set  
   {  
base.SetValue(TravelRuleSet.DiscountLevelProperty, value);  
   }  
}  
```  
  
## <a name="interopwith35ruleset"></a>InteropWith35RuleSet  
 これは、[!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] アクティビティを使用して、TravelRuleLibrary プロジェクトで作成されたカスタム ルール セットと統合する <xref:System.Activities.Statements.Interop> シーケンシャル ワークフロー プロジェクトです。 変数は、次のように最上位レベルの <xref:System.Activities.Statements.Sequence> で作成されます。  
  
 ![変数](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesvariables.jpg "InteropRulesVariables")  
  
 ![ソリューション エクスプ ローラー](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulessolutionexplorer.jpg "InteropRulesSolutionExplorer")  
  
 最後に、<xref:System.Activities.Statements.Interop> アクティビティは、TravelRuleSet と統合するために使用されます。 <xref:System.Activities.Statements.Sequence> で事前に宣言された変数は、依存プロパティにバインドするために使用されます。  
  
 ![アクティビティ タイプ](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprules.jpg "InteropRules")  
  
 ![矢印](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesarrow.jpg "InteropRulesArrow")  
  
 ![プロパティ](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesproperties.jpg "InteropRulesProperties")  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`
