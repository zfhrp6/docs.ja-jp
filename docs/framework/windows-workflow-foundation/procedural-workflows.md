---
title: 手続き型ワークフロー
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: 5cd97c8ccaae74e4275f809502ac0a4d3c2f042a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515230"
---
# <a name="procedural-workflows"></a>手続き型ワークフロー
手続き型ワークフローでは、手続き型言語と似たフロー制御方法を使用します。 これらの構造には `While` と `If` が含まれます。 これらのワークフローは、<xref:System.Activities.Statements.Flowchart> や <xref:System.Activities.Statements.Sequence> など、他のフロー制御アクティビティを使用して自由に構成できます。  
  
## <a name="controlling-execution-flow"></a>実行フローの制御  
 ワークフロー アクティビティ ライブラリには、手続き型言語で使用されるほとんどのフロー制御方法をモデル化するアクティビティがあります。 次の設定があります。  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.DoWhile>  
  
-   <xref:System.Activities.Statements.ForEach%601>  
  
-   <xref:System.Activities.Statements.Parallel>  
  
-   <xref:System.Activities.Statements.ParallelForEach%601>  
  
-   <xref:System.Activities.Statements.If>  
  
-   <xref:System.Activities.Statements.Switch%601>  
  
-   <xref:System.Activities.Statements.Pick>  
  
 フロー制御アクティビティを使用するドラッグ アンド ドロップしてから、**アクティビティ**ツールボックス、デザイナー ウィンドウ内の複合アクティビティにします。  
  
> [!NOTE]
>  [!INCLUDE[dublin](../../../includes/dublin-md.md)] を使用して Web ファーム上でワークフローをホストすると、AppFabric のインスタンスは複数の AppFabric サーバー間を移動します。 この機能を利用するには、リソースがすべてのノード間で共有可能になっている必要があります。  既定の NET 4 ワークフロー アクティビティには、ローカル リソースにアクセスする操作は含まれていません。 AppFabric には特定のワークフローを不変に設定するメカニズムがないため、ワークフローが移動されるとエラーが発生するようなカスタム アクティビティは絶対に作成しないでください。  
  
## <a name="see-also"></a>関連項目  
 [Flowchart のワークフロー](../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)
