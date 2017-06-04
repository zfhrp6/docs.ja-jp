---
title: "Implementing the UI Automation SelectionItem Control Pattern | Microsoft Docs"
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
  - "Selection Item control pattern"
  - "UI Automation, Selection Item control pattern"
  - "control patterns, Selection Item"
ms.assetid: 76b0949a-5b23-4cfc-84cc-154f713e2e12
caps.latest.revision: 22
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 22
---
# Implementing the UI Automation SelectionItem Control Pattern
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] の最新情報については、「[Windows Automation API: UI オートメーション](http://go.microsoft.com/fwlink/?LinkID=156746)」をご覧ください。  
  
 このトピックでは、プロパティ、メソッド、イベントに関する情報など、<xref:System.Windows.Automation.Provider.ISelectionItemProvider> の実装のためのガイドラインと規則について説明します。 その他のリファレンスへのリンクは、概要の最後に記載します。  
  
 <xref:System.Windows.Automation.SelectionItemPattern> コントロール パターンは、<xref:System.Windows.Automation.Provider.ISelectionProvider> を実装するコンテナー コントロールの個別の選択可能な子項目として機能するコントロールをサポートするために使用します。 SelectionItem コントロール パターンを実装するコントロールの例については、「[Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)」を参照してください。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## 実装のガイドラインと規則  
 Selection Item コントロール パターンを実装する場合は、次のガイドラインと規則に留意してください。  
  
-   **\[画面のプロパティ\]** ダイアログ ボックスの **\[画面解像度\]** スライダーなどの <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot> を実装する子コントロールを管理する単一選択コントロールは <xref:System.Windows.Automation.Provider.ISelectionProvider> を実装する必要があり、その子は <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> と <xref:System.Windows.Automation.Provider.ISelectionItemProvider> の両方を実装する必要があります。  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## ISelectionItemProvider の必須メンバー  
 <xref:System.Windows.Automation.Provider.ISelectionItemProvider> の実装には、次のプロパティ、メソッド、およびイベントが必要です。  
  
|必須メンバー|メンバーの型|ノート|  
|------------|------------|---------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|メソッド|なし|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|イベント|コンテナー内の選択が大幅に変更され、<xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> 定数で許可されたよりも多くの <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> イベントと <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> イベントを送信する必要がある場合に発生します。|  
  
-   <xref:System.Windows.Automation.SelectionItemPattern.Select%2A>、<xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A>、または <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> の結果が単一選択項目の場合は、<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> が発生するはずです。それ以外の場合は、必要に応じて、<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>\/<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> が送信されます。  
  
<a name="Exceptions"></a>   
## 例外  
 プロバイダーは、次の例外をスローする必要があります。  
  
|例外の種類|状態|  
|-----------|--------|  
|<xref:System.InvalidOperationException>|次のいずれが試行された場合:<br /><br /> -   <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty> \= `true` で、既に 1 つの要素が選択されている単一選択コンテナーで <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> が呼び出された場合。<br />-   <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty> \= `true` で、1 つの要素だけが選択されている複数選択コンテナーで <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> が呼び出された場合。<br />-   <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty> \= `false` で、既に別の要素が選択されている単一選択コンテナーで <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A> が呼び出された場合。|  
  
## 参照  
 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)   
 [Support Control Patterns in a UI Automation Provider](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)   
 [UI Automation Control Patterns for Clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)   
 [Implementing the UI Automation Selection Control Pattern](../../../docs/framework/ui-automation/implementing-the-ui-automation-selection-control-pattern.md)   
 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)   
 [Use Caching in UI Automation](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)   
 [Fragment Provider Sample](http://msdn.microsoft.com/ja-jp/778ef1bc-8610-4bc9-886e-aeff94a8a13e)