---
title: 移行のガイドライン
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: 562ee0913f657b349d88fe7be1627ecd9469f317
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="migration-guidance"></a>移行のガイドライン
[!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]、2 つ目のメジャー バージョンの Windows Workflow Foundation (WF) がリリースされています。 [!INCLUDE[wf1](../../../includes/wf1-md.md)] は、[!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] (これに含まれていた System.Workflow.* 名前空間の型は現在 WF3 と呼ばれています) でリリースされ、[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] で強化されました。 WF3 もの一部、 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]、新しいワークフロー テクノロジが存在するが、(System.Activities。 内の型\*名前空間です。 WF4 と呼ばれます)。 WF4 の導入時期を検討する場合は、最初にそのタイミングの管理を認識することが重要です。  
  
-   WF3 は [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] で完全にサポートされています。  
  
-   WF3 のアプリケーションは、変更しなくても [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] で実行され、引き続き完全にサポートされます。  
  
-   新しい WF3 アプリケーションを作成することもできます。また、既存のアプリケーションを [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] で編集することも可能で、そのアプリケーションも完全にサポートされます。  
  
 したがって、.NET Framework 4 を導入するに WF4 に移行するから切り離されます (System.Activities.*) WF3 から (System.Workflow。\*)。 このトピックでは、WF の移行のガイドラインへのリンクを提供し、WF3 および WF4 での作業に関する情報を提供します。  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a>WF の移行に関するホワイト ペーパーとクックブック  
 [WF の移行の概要](http://go.microsoft.com/fwlink/?LinkId=153873)WF3 と WF4 と移行方法の間のリレーションシップの大まかな概要を説明します。 関連トピックでは、特定のトピックを掘り下げて説明します。  
  
 [WF の移行の概要](http://go.microsoft.com/fwlink/?LinkId=153873)  
 WF3 と WF4 の関係、および .NET 4 のワークフロー テクノロジのユーザーまたは潜在的なユーザーとして使用できる選択肢について説明します。  
  
 [WF の移行: WF3 を開発に関するヒント集](http://go.microsoft.com/fwlink/?LinkId=153852)  
 より簡単に WF4 に移行できるように、WF3 の成果物を設計する方法について説明します。  
  
 [WF のガイダンス: 規則](http://go.microsoft.com/fwlink/?LinkId=153854)  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] のソリューションに規則関連の投資を促進する方法について説明します。  
  
 [WF のガイダンス: ステート マシン](http://go.microsoft.com/fwlink/?LinkId=153855)  
 ステート マシンのアクティビティがない場合の WF4 の制御フロー モデリングについて説明します。  
  
 このガイダンスは、.NET Framework 4 を対象とするワークフロー プロジェクトにのみ該当することに注意してください。 ステート マシンのワークフローは、Platform Update 1 のリリースで .NET 4.0.1 に追加され、.NET Framework 4.5 の一部として含まれていました。 .NET 4.0.1 - 4.0.3 以降と .NET Framework 4.5 でのステート マシン ワークフローの詳細については、次を参照してください。 [Microsoft .NET Framework 4 の機能の更新プログラム 4.0.1](http://msdn.microsoft.com/library/de3297bd-c3e1-4126-95be-2ed7fe2a98fc)と[ステート マシン ワークフロー](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md)です。  
  
 [WF 移行のクックブック: カスタム アクティビティ](http://go.microsoft.com/fwlink/?LinkId=153856)  
 WF3 のカスタム アクティビティを WF4 で再設計する場合のサンプルと手順について説明します。  
  
 [WF 移行のクックブック: 高度なカスタム アクティビティ](http://go.microsoft.com/fwlink/?LinkId=275560)  
 WF3 キューを使用して子アクティビティを WF4 カスタム アクティビティとしてスケジュールする高度な WF3 カスタム アクティビティを再設計するための指針を示します。  
  
 [WF 移行のクックブック: ワークフロー](http://go.microsoft.com/fwlink/?LinkId=153858)  
 WF3 のワークフローを WF4 で再設計する場合のサンプルと手順について説明します。  
  
 [WF 移行のクックブック: ワークフローのホスティング](http://go.microsoft.com/fwlink/?LinkId=275561)  
 WF3 ホスティング コードを WF4 ホスティング コードとして再設計するための指針を示します。 この目的は、WF3 と WF4 のワークフロー ホスティングの主な違いを説明することです。  
  
 [WF 移行のクックブック: ワークフローの追跡](http://go.microsoft.com/fwlink/?LinkId=275562)  
 WF3 追跡コードを再設計するための指針と、同等の WF4 追跡コードと構成を使用した構成を示します。  
  
 [WF のガイダンス: ワークフロー サービス](http://go.microsoft.com/fwlink/?LinkId=275564)  
 事前定義アクティビティの一般的なシナリオ向けに、WF3 で作成した Windows Communication Foundation (WCF) Web サービス (一般にワークフロー サービスと呼ばれます) を実装するワークフローを WF4 を使用するように再設計するための詳細な手順を例を中心として示します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Activities.Statements.Interop>
