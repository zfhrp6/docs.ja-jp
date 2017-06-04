---
title: "UI Automation Support for the ToolTip Control Type | Microsoft Docs"
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
  - "UI Automation, ToolTip control type"
  - "ToolTip control type"
  - "control types, ToolTip"
ms.assetid: c3779d78-3164-43ae-8dae-bfaeafffdd65
caps.latest.revision: 22
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 22
---
# UI Automation Support for the ToolTip Control Type
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] の最新情報については、「[Windows Automation API: UI オートメーション](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。  
  
 このトピックでは、ToolTip コントロール型に対する [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] のサポートについて説明します。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] でのコントロール型とは、コントロールが <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> プロパティを使用するために満たす必要がある一連の条件のことです。 条件には、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー構造、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティの値、およびコントロール パターンに関する特定のガイドラインが含まれます。  
  
 ツール ヒント コントロールは、テキストを含むポップアップ ウィンドウです。  
  
 以下の各セクションで、ToolTip コントロール型に必要な [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー構造、プロパティ、コントロール パターン、およびイベントを定義します。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] の要件は、[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]、[!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]、[!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] のいずれの場合でも、すべてのツール ヒント コントロールに適用されます。  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## 必須の UI オートメーション ツリー構造  
 次の表に、ツール ヒント コントロールに関連する [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコントロール ビューとコンテンツ ビューを示し、それぞれのビューに含めることができる内容について説明します。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーの詳細については、「[UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)」を参照してください。  
  
|コントロール ビュー|コンテンツ ビュー|  
|----------------|---------------|  
|ヒント<br /><br /> -   テキスト \(0 個以上\)<br />-   イメージ \(0 個以上\)|ヒント|  
  
 ツール ヒント コントロールは、キーボード フォーカスを受け取ることができる場合は、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコンテンツ ビューにのみ表示されます。 それ以外の場合、ツール ヒントの情報はすべて、ツール ヒントが参照している [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 要素の `HelpTextProperty` から取得できます。  
  
 ツール ヒントは、その情報が参照しているコントロールの下に表示されます。 クライアントは、ツール ヒントに含まれる情報を常に取得できるよう、`ToolTipOpenedEvent` をリッスンする必要があります。  
  
<a name="Required_UI_Automation_Properties"></a>   
## 必須の UI オートメーション プロパティ  
 次の表に、ツール ヒント コントロールに特に関連する値または定義を持つ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティを示します。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティの詳細については、「[UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)」を参照してください。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティ|値|ノート|  
|---------------------------------------------------------------------------------|-------|---------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|「ノート」を参照してください。|このプロパティの値は、アプリケーションのすべてのコントロールにおいて一意である必要があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|「ノート」を参照してください。|コントロール全体を格納する最も外側の四角形。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|「ノート」を参照してください。|クリック可能なポイントは、コントロールを閉じるツール ヒントの部分である必要があります。 一部のツール ヒントには、この機能がありません。その場合、クリック可能なポイントを持ちません。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|「ノート」を参照してください。|コントロールがキーボード フォーカスを受け取ることができる場合は、このプロパティをサポートする必要があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|「ノート」を参照してください。|ツール ヒント内に表示されるテキストがツール ヒント コントロールの名前になります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|ツール ヒント コントロールは、常にそのコンテンツで自己ラベル付けを行います。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ヒント|この値は、すべての UI フレームワークで同じです。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"ツール ヒント"|ToolTip コントロール型に対応する、ローカライズされた文字列。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|状況に依存|ツール ヒント コントロールがキーボード フォーカスを受け取ることができる場合、ツリーのコンテンツ ビューにのみ表示される必要があります。 テキストのみである場合は、生成元のコントロールの HelpTextProperty として取得できます。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|ツール ヒント コントロールは、常にコントロールである必要があります。|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## 必須の UI オートメーション コントロール パターン  
 次の表に、ツール ヒント コントロールでサポートされなければならない [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] コントロール パターンを示します。 コントロール パターンの詳細については、「[UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)」を参照してください。  
  
|コントロール パターン|Support|ノート|  
|-----------------|-------------|---------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider>|状況に依存|UI 項目をクリックして閉じることができるツール ヒントは、自動的に閉じるように、WindowPattern をサポートする必要があります。|  
|<xref:System.Windows.Automation.Provider.ITextProvider>|状況に依存|アクセシビリティを向上させるために、ツール ヒント コントロールでは Text コントロール パターンをサポートできますが、必須ではありません。 テキストにさまざまなスタイルや属性 \(たとえば、色、太字、斜体など\) がある場合、Text コントロール パターンの使用をお勧めします。|  
  
<a name="Required_UI_Automation_Events"></a>   
## 必須の UI オートメーション イベント  
 ツール ヒント コントロールは、画面に表示された場合に `ToolTipOpenedEvent` を生成する必要があります。 イベントにツール ヒント自体の [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 要素への参照が組み込まれます。  
  
 次の表に、すべてのツール ヒント コントロールでサポートされなければならない [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] イベントを示します。 イベントの詳細については、「[UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md)」を参照してください。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] イベント|Support|ノート|  
|--------------------------------------------------------------------------------|-------------|---------|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|状況に依存|なし|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|状況に依存|なし|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent>|状況に依存|なし|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent>|状況に依存|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipOpenedEvent>|必要|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipClosedEvent>|必要|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> プロパティ変更イベント。|必須|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> プロパティ変更イベント。|必須|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> プロパティ変更イベント。|必須|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> プロパティ変更イベント。|必須|なし|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowVisualStateProperty> プロパティ変更イベント。|状況に依存|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|必要|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|必要|なし|  
  
## 参照  
 <xref:System.Windows.Automation.ControlType.ToolTip>   
 [UI Automation Control Types Overview](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)   
 [UI Automation Overview](../../../docs/framework/ui-automation/ui-automation-overview.md)