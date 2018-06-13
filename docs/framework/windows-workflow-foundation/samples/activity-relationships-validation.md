---
title: アクティビティの関係の検証
ms.date: 03/30/2017
ms.assetid: 6f11a34e-ed67-4bce-88ce-7e96bbb4d052
ms.openlocfilehash: e6dd0e6a7b48444073ebae378e21c1b45977a1f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515109"
---
# <a name="activity-relationships-validation"></a>アクティビティの関係の検証
このサンプルには 3 つのアクティビティ `CreateCity`、`CreateState`、および `CreateCountry` が含まれます。 `CreateCity` は `CreateState` アクティビティ内にあり、`CreateState` は `CreateCountry` アクティビティ内にある必要があります。 このサンプルの目的から、検証ロジックは、`CreateState` アクティビティについてはコードで記述され、`CreateCity` アクティビティについては XAML で記述されます。 制約の動作は両方とも同じです。  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] には、アクティビティ間の関係を検証するために使用できる次の 3 つのヘルパー アクティビティが用意されています。  
  
 <xref:System.Activities.Validation.GetParentChain>  
 現在のノードの親に属しているすべてのアクティビティのコレクションを提供します。  
  
 <xref:System.Activities.Validation.GetChildSubtree>  
 現在のノードのサブツリーに属しているすべてのアクティビティのコレクションを提供します (現在のノードを除く)。  
  
 <xref:System.Activities.Validation.GetWorkflowTree>  
 現在のノードと同じツリーにあるすべてのアクティビティのコレクションを提供します。  
  
 このサンプルでは、<xref:System.Activities.Statements.ForEach%601> アクティビティを使用して、<xref:System.Activities.Validation.GetParentChain> から返されたコレクション内のすべての要素を処理します。 コレクション内の要素ごとに、その型が `CreateCountry` (`CreateState` を検証する場合は `CreateCity`) と比較され、一致が見つかると、結果フラグが `true` に設定されます。 最後に、結果フラグが <xref:System.Activities.Validation.AssertValidation> に設定される場合は、`false` を使用して検証エラーが生成されます。  
  
### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で ContainmentValidation.sln サンプル ソリューションを開きます。  
  
2.  ソリューションをビルドします。  
  
3.  Ctrl キーを押しながら F5 キーを押して、プログラムを起動します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ActivityRelationships`
