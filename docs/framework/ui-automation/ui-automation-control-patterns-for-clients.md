---
title: "UI Automation Control Patterns for Clients | Microsoft Docs"
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
  - "UI Automation, control patterns for clients"
  - "control patterns, UI Automation clients"
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
caps.latest.revision: 24
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 24
---
# UI Automation Control Patterns for Clients
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] の最新情報については、「[Windows Automation API: UI オートメーション](http://go.microsoft.com/fwlink/?LinkID=156746)」をご覧ください。  
  
 この概要では、UI オートメーション クライアントのコントロール パターンについて説明します。 また、UI オートメーション クライアントがコントロール パターンを使用して、[!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] の情報にアクセスするしくみについても説明します。  
  
 コントロール パターンは、コントロール型や外観に関係なく、コントロールの機能を分類したり公開したりするための手段です。 UI オートメーション クライアントは、<xref:System.Windows.Automation.AutomationElement> を調べてどのコントロール パターンがサポートされているかを特定し、そのコントロールの動作を確実に実行することができます。  
  
 コントロール パターンの完全なリストについては、「[UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)」をご覧ください。  
  
<a name="uiautomation_getting_control_patterns"></a>   
## コントロール パターンの取得  
 クライアントは、<xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=fullName> または <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=fullName> を呼び出して、<xref:System.Windows.Automation.AutomationElement> からコントロール パターンを取得します。  
  
 クライアントは、<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> メソッドまたは個別の `IsPatternAvailable` プロパティ \(<xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty> など\) を使用して、パターンまたはパターンのグループが <xref:System.Windows.Automation.AutomationElement> でサポートされているかどうかを特定できます。 ただし、サポートされているプロパティを確認してコントロール パターンを取得するよりも、コントロール パターンを取得して `null` 参照に対するテストを試行する方が、プロセス間呼び出しが少なくなるため効率的です。  
  
 <xref:System.Windows.Automation.AutomationElement> から <xref:System.Windows.Automation.TextPattern> コントロール パターンを取得する方法を次の例に示します。  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>   
## コントロール パターンのプロパティの取得  
 クライアントは、<xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=fullName> または <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=fullName> を呼び出し、返されたオブジェクトを適切な型にキャストすることで、コントロール パターンのプロパティ値を取得できます。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティについて詳しくは、「[UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)」をご覧ください。  
  
 `GetPropertyValue` メソッドに加え、[!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] アクセサーを介してパターンの[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティにアクセスすることで、プロパティ値を取得することもできます。  
  
<a name="uiautomation_with_variable_patterns"></a>   
## 変数パターンを持つコントロール  
 一部のコントロール型は、状態やコントロールの使用方法に応じた複数のパターンをサポートしています。 変数パターンを持つコントロールの例としては、リスト ビュー \(サムネイル、タイル、アイコン、リスト、詳細\)、[!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] グラフ \(円、線、横棒、式を使用するセル値\)、[!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] のドキュメント領域 \(標準、Web レイアウト、アウトライン、印刷レイアウト、印刷プレビュー\)、[!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] スキンなどがあります。  
  
 カスタム コントロール型を実装するコントロールは、機能を表すために必要なコントロール パターンの任意のセットを持つことができます。  
  
## 参照  
 [UI Automation Control Patterns](../../../docs/framework/ui-automation/ui-automation-control-patterns.md)   
 [UI Automation Text Pattern](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)   
 [Invoke a Control Using UI Automation](../../../docs/framework/ui-automation/invoke-a-control-using-ui-automation.md)   
 [Get the Toggle State of a Check Box Using UI Automation](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)   
 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)   
 [TextPattern Insert Text Sample](http://msdn.microsoft.com/ja-jp/67353f93-7ee2-42f2-ab76-5c078cf6ca16)   
 [TextPattern Search and Selection Sample](http://msdn.microsoft.com/ja-jp/0a3bca57-8b72-489d-a57c-da85b7a22c7f)   
 [InvokePattern and ExpandCollapsePattern Menu Item Sample](http://msdn.microsoft.com/ja-jp/b7fa141c-e2d1-4da2-a27f-81a7d1172210)