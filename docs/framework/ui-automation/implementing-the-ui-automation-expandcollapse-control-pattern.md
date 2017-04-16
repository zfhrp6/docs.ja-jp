---
title: "Implementing the UI Automation ExpandCollapse Control Pattern | Microsoft Docs"
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
  - "UI Automation, ExpandCollapse control pattern"
  - "ExpandCollapse control pattern"
  - "control patterns, ExpandCollapse"
ms.assetid: 1dbabb8c-0d68-47c1-a35e-1c01cb01af26
caps.latest.revision: 25
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 25
---
# Implementing the UI Automation ExpandCollapse Control Pattern
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] の最新情報については、「[Windows Automation API: UI オートメーション](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。  
  
 このトピックでは、プロパティ、メソッド、イベントに関する情報など、<xref:System.Windows.Automation.Provider.IExpandCollapseProvider> の実装のためのガイドラインと規則について説明します。 その他のリファレンスへのリンクは、概要の最後に記載します。  
  
 <xref:System.Windows.Automation.ExpandCollapsePattern> コントロール パターンは、視覚的に展開してより多くのコンテンツを表示したり、折りたたんでコンテンツを非表示にしたりするコントロールをサポートするために使用します。 このコントロール パターンを実装するコントロールの例については、「[Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)」を参照してください。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## 実装のガイドラインと規則  
 ExpandCollapse コントロール パターンを実装する場合は、次のガイドラインと規則に注意してください。  
  
-   展開または折りたたみの機能を備えた UI を提供する子オブジェクトで構成された集約コントロールは、<xref:System.Windows.Automation.ExpandCollapsePattern> コントロール パターンをサポートする必要がありますが、その子要素がサポートする必要はありません。 たとえば、コンボ ボックス コントロールは、リスト ボックス、ボタン、およびエディット コントロールの組み合わせで構成されていますが、<xref:System.Windows.Automation.ExpandCollapsePattern> をサポートする必要があるのは親のコンボ ボックスのみです。  
  
    > [!NOTE]
    >  メニュー コントロールは例外であり、これは個々の MenuItem オブジェクトの集合体です。 MenuItem オブジェクトは <xref:System.Windows.Automation.ExpandCollapsePattern> コントロール パターンをサポートできますが、親の Menu コントロールはできません。 同様の例外が、Tree および Tree Item コントロールにも適用されます。  
  
-   コントロールの <xref:System.Windows.Automation.ExpandCollapseState> が <xref:System.Windows.Automation.ExpandCollapseState> に設定されている場合、コントロールに対して現在アクティブな <xref:System.Windows.Automation.ExpandCollapsePattern> 機能は存在せず、このコントロール パターンを使用して取得できる情報は <xref:System.Windows.Automation.ExpandCollapseState> だけです。 その後、子オブジェクトが追加された場合は、<xref:System.Windows.Automation.ExpandCollapseState> が変更され、<xref:System.Windows.Automation.ExpandCollapsePattern> 機能がアクティブになります。  
  
-   <xref:System.Windows.Automation.ExpandCollapseState> は、すべての子孫オブジェクトの可視性を表すのではなく、直接の子オブジェクトの可視性のみを表します。  
  
-   展開および折りたたみ機能は、コントロールに固有の機能です。 この機能の動作例を次に示します。  
  
    -   Office Personal のメニューには、3 つの状態を示す MenuItem \(<xref:System.Windows.Automation.ExpandCollapseState>、<xref:System.Windows.Automation.ExpandCollapseState>、および <xref:System.Windows.Automation.ExpandCollapseState>\) を指定できます。この場合、<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> または <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> を呼び出したときに選択される状態は、コントロールによって指定されます。  
  
    -   TreeItem で <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> を呼び出すと、すべての子孫または直接の子のみを表示できます。  
  
    -   コントロールでの <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> または <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> の呼び出しによってその子孫の状態が維持されるとき、状態の変更イベントではなく、可視性の変更イベントが送信されます。折りたたみの実行時に親コントロールが子孫の状態を維持しないときは、コントロールが表示されなくなったすべての子孫を破棄し、破棄イベントを発生させる場合と、子孫ごとに <xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A> を変更して、可視性の変更イベントを発生させる場合があります。  
  
-   ナビゲーションを確実にするには、オブジェクトを親の <xref:System.Windows.Automation.ExpandCollapseState> に関係なく、\(可視性の状態が適切な\) [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー内に配置することをお勧めします。 子孫が必要に応じて生成される場合、それらが [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーに表示されるのは、初回の表示以降か、または可視状態になっている間に限られます。  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## IExpandCollapseProvider の必須メンバー  
 <xref:System.Windows.Automation.Provider.IExpandCollapseProvider> の実装には、次のプロパティとメソッドが必要です。  
  
|必須メンバー|メンバーの型|ノート|  
|------------|------------|---------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A>|メソッド|なし|  
|<xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>|メソッド|なし|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|Event|このコントロールには関連付けられているイベントがありません。この汎用デリゲートを使用します。|  
  
<a name="Exceptions"></a>   
## 例外  
 プロバイダーは、次の例外をスローする必要があります。  
  
|例外の種類|状態|  
|-----------|--------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ExpandCollapseState> \= <xref:System.Windows.Automation.ExpandCollapseState> の場合、<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> または <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> のどちらかが呼び出されます。|  
  
## 参照  
 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)   
 [Support Control Patterns in a UI Automation Provider](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)   
 [UI Automation Control Patterns for Clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)   
 [Navigate Among UI Automation Elements with TreeWalker](../../../docs/framework/ui-automation/navigate-among-ui-automation-elements-with-treewalker.md)   
 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)   
 [Use Caching in UI Automation](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)