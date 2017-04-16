---
title: "UI オートメーション GridItem コントロール パターンの実装 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GridItem コントロール パターン"
  - "UI オートメーション GridItem コントロール パターン"
  - "GridItem コントロール パターン"
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
caps.latest.revision: 15
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 15
---
# UI オートメーション GridItem コントロール パターンの実装
> [!NOTE]
>  このドキュメントが目的とする、管理を使用する .NET Framework 開発者[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]で定義されたクラス、 <xref:System.Windows.Automation>名前空間。 最新情報について[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API: UI 自動化](http://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 このトピックでは、実装するため<xref:System.Windows.Automation.Provider.IGridItemProvider>、プロパティに関する情報などです。 その他のリファレンスへのリンクは、概要の最後に記載します。  
  
 <xref:System.Windows.Automation.GridItemPattern>コントロール パターンが実装したコンテナーの個々 の子コントロールをサポートするために使用される<xref:System.Windows.Automation.Provider.IGridProvider>します。 このコントロール パターンを実装するコントロールの例については、次を参照してください。 [UI オートメーション クライアントのコントロール パターン マッピング](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)します。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>実装のガイドラインと規則  
 実装するときに<xref:System.Windows.Automation.Provider.IGridProvider>、次のガイドラインと規則に注意してください。  
  
-   グリッドの座標は 0 から始まり、左上のセルの座標が (0, 0) です。  
  
-   結合されたセルが報告されます、<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>と<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>プロパティは、UI オートメーション プロバイダーで定義されている、基になるアンカー セルに基づいています。 通常、これは、最上位の左端の行または列です。  
  
-   <xref:System.Windows.Automation.Provider.IGridItemProvider>は、グリッドの結合またはセルの分割などのアクティブな操作を提供しません。  
  
-   実装するコントロール<xref:System.Windows.Automation.Provider.IGridItemProvider>走査できる通常 (つまり、UI オートメーション クライアントが隣接するコントロールに移動できる)、キーボードを使用しています。  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a>IGridItemProvider の必須メンバー  
 次のプロパティとメソッドを実装するために必要な<xref:System.Windows.Automation.Provider.IGridItemProvider>します。  
  
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
 このコントロール パターンに関連付けられる例外はありません。  
  
## <a name="see-also"></a>関連項目  
 [UI オートメーション コントロール パターンの概要](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)   
 [UI オートメーション プロバイダーでコントロール パターンをサポートします。](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)   
 [クライアントの UI オートメーション コントロール パターン](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)   
 [UI オートメーション Grid コントロール パターンの実装](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)   
 [UI オートメーション ツリーの概要](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)   
 [UI オートメーションにおけるキャッシュを使用します。](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)