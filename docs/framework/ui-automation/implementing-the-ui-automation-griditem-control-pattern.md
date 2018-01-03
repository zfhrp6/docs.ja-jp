---
title: "UI オートメーション GridItem コントロール パターンの実装"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
caps.latest.revision: "15"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d234ea6f15706a47f6a758528dbe4eda0f3b778a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a>UI オートメーション GridItem コントロール パターンの実装
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。  
  
 このトピックのガイドラインと規則を実装するための導入<xref:System.Windows.Automation.Provider.IGridItemProvider>、プロパティに関する情報などです。 その他のリファレンスへのリンクは、概要の最後に記載します。  
  
 <xref:System.Windows.Automation.GridItemPattern>コントロール パターンを実装するコンテナーの各子コントロールをサポートするために使用<xref:System.Windows.Automation.Provider.IGridProvider>です。 このコントロール パターンを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)」をご覧ください。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>実装のガイドラインと規則  
 実装するときに<xref:System.Windows.Automation.Provider.IGridProvider>、次のガイドラインと規則に注意してください。  
  
-   グリッドの座標は 0 から始まり、左上のセルの座標が (0, 0) です。  
  
-   マージされたセルが報告、<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>と<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>プロパティは、UI オートメーション プロバイダーによって定義された、基になるアンカー セルに基づきます。 通常、これは、最上位の左端の行または列です。  
  
-   <xref:System.Windows.Automation.Provider.IGridItemProvider>グリッドの結合またはセルの分割などのアクティブな操作を提供しません。  
  
-   実装するコントロール<xref:System.Windows.Automation.Provider.IGridItemProvider>通常走査することができます (つまり、UI オートメーション クライアントが隣接するコントロールに移動ことができます)、キーボードを使用しています。  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a>IGridItemProvider の必須メンバー  
 <xref:System.Windows.Automation.Provider.IGridItemProvider> の実装には、次のプロパティとメソッドが必要です。  
  
|必須メンバー|メンバーの型|ノート|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|プロパティ|なし|  
  
 このコントロール パターンに関連するメソッドまたはイベントはありません。  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>例外  
 このコントロール パターンに関連付けられた例外はありません。  
  
## <a name="see-also"></a>参照  
 [UI Automation コントロール パターンの概要](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI オートメーション プロバイダーでのコントロール パターンのサポート](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [クライアントの UI オートメーション コントロール パターン](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI オートメーション Grid コントロール パターンの実装](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)  
 [UI Automation ツリーの概要](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [UI オートメーションにおけるキャッシュの使用](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
