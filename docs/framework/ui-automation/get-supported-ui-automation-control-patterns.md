---
title: "サポートされている UI オートメーション コントロール パターンの取得 | Microsoft Docs"
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
  - "取得するコントロール パターン"
  - "UI オートメーション、コントロール パターンの取得"
  - "コントロール パターンを取得します。"
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
caps.latest.revision: 10
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 10
---
# サポートされている UI オートメーション コントロール パターンの取得
> [!NOTE]
>  このドキュメントが目的とする、管理を使用する .NET Framework 開発者[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]で定義されたクラス、 <xref:System.Windows.Automation>名前空間。 最新情報について[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API: UI 自動化](http://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 このトピックからのコントロール パターンのオブジェクトを取得する方法を示しています。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]要素。  
  
### <a name="obtain-all-control-patterns"></a>すべてのコントロール パターンの取得  
  
1.  取得、 <xref:System.Windows.Automation.AutomationElement>関心のあるパターンを制御します。  
  
2.  呼び出す<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>要素からすべてのコントロール パターンを取得します。  
  
> [!CAUTION]
>  クライアントが使用しないことを強くお勧め<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>します。 パフォーマンスにこのメソッドは、深刻な影響<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>の各既存のコントロール パターンを内部的にします。 可能であれば、クライアントが呼び出す必要があります<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>の関心のある主要なパターンです。  
  
### <a name="obtain-a-specific-control-pattern"></a>特定のコントロール パターンの取得  
  
1.  取得、 <xref:System.Windows.Automation.AutomationElement>関心のあるパターンを制御します。  
  
2.  呼び出す<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>または<xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>の特定のパターンを照会します。 これらのメソッドは、のようなパターンが見つからない場合は<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>で例外が発生し、 <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>を返します`false`します。  
  
## <a name="example"></a>例  
 次の例では取得、 <xref:System.Windows.Automation.AutomationElement>リスト項目の取得と、 <xref:System.Windows.Automation.SelectionItemPattern>その要素から。  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a>関連項目  
 [クライアントの UI オートメーション コントロール パターン](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)