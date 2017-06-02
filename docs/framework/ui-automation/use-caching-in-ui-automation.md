---
title: "Use Caching in UI Automation | Microsoft Docs"
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
  - "caching, UI Automation"
  - "UI Automation, caching"
ms.assetid: ec722dff-6009-4279-b86a-e18d3fa94ebf
caps.latest.revision: 14
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 14
---
# Use Caching in UI Automation
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] の最新情報については、「[Windows Automation API: UI オートメーション](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。  
  
 ここでは、<xref:System.Windows.Automation.AutomationElement> プロパティとコントロール パターンのキャッシュを実装する方法について説明します。  
  
### キャッシュ要求のアクティブ化  
  
1.  <xref:System.Windows.Automation.CacheRequest> を作成します。  
  
2.  <xref:System.Windows.Automation.CacheRequest.Add%2A> を使用して、キャッシュするプロパティとパターンを指定します。  
  
3.  <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> プロパティを設定することにより、キャッシュのスコープを指定します。  
  
4.  <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> プロパティを設定することにより、サブツリーのビューを指定します。  
  
5.  オブジェクトへの完全な参照を取得しないようにして効率化を図りたい場合は、<xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> プロパティを <xref:System.Windows.Automation.AutomationElementMode> に設定します。 \(このようにすると、これらのオブジェクトから現在の値を取得できなくなります。\)  
  
6.  `using` ブロック内 \([!INCLUDE[TLA#tla_visualbnet](../../../includes/tlasharptla-visualbnet-md.md)] 内の `Using`\) で <xref:System.Windows.Automation.CacheRequest.Activate%2A> を使用して、要求をアクティブ化します。  
  
 <xref:System.Windows.Automation.AutomationElement> オブジェクトの取得後、またはイベントのサブスクライブ後に、<xref:System.Windows.Automation.CacheRequest.Pop%2A> を使用するか \(<xref:System.Windows.Automation.CacheRequest.Push%2A> を使用した場合\)、または <xref:System.Windows.Automation.CacheRequest.Activate%2A> で作成したオブジェクトを破棄することにより、要求を非アクティブ化します。 \(<xref:System.Windows.Automation.CacheRequest.Activate%2A> は `using` ブロック内 \([!INCLUDE[TLA#tla_visualbnet](../../../includes/tlasharptla-visualbnet-md.md)] 内の `Using`\) で使用してください。\)  
  
### AutomationElement プロパティのキャッシュ  
  
1.  <xref:System.Windows.Automation.CacheRequest> がアクティブな間に、<xref:System.Windows.Automation.AutomationElement.FindFirst%2A> または <xref:System.Windows.Automation.AutomationElement.FindAll%2A> を使用して、<xref:System.Windows.Automation.AutomationElement> オブジェクトを取得します。あるいは、<xref:System.Windows.Automation.CacheRequest> がアクティブな間に登録したイベントのソースとして <xref:System.Windows.Automation.AutomationElement> を取得します  \(GetUpdatedCache またはいずれかの <xref:System.Windows.Automation.TreeWalker> メソッドに <xref:System.Windows.Automation.CacheRequest> を渡すことにより、キャッシュを作成することも可能です\)。  
  
2.  <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> を使用するか、または <xref:System.Windows.Automation.AutomationElement> の <xref:System.Windows.Automation.AutomationElement.Cached%2A> プロパティからプロパティを取得します。  
  
### キャッシュされたパターンとプロパティの取得  
  
1.  <xref:System.Windows.Automation.CacheRequest> がアクティブな間に、<xref:System.Windows.Automation.AutomationElement.FindFirst%2A> または <xref:System.Windows.Automation.AutomationElement.FindAll%2A> を使用して、<xref:System.Windows.Automation.AutomationElement> オブジェクトを取得します。あるいは、<xref:System.Windows.Automation.CacheRequest> がアクティブな間に登録したイベントのソースとして <xref:System.Windows.Automation.AutomationElement> を取得します  \(GetUpdatedCache またはいずれかの <xref:System.Windows.Automation.TreeWalker> メソッドに <xref:System.Windows.Automation.CacheRequest> を渡すことにより、キャッシュを作成することも可能です\)。  
  
2.  キャッシュされたパターンを取得するために、<xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> または <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> を使用します。  
  
3.  コントロール パターンの `Cached` プロパティからプロパティ値を取得します。  
  
## 使用例  
 次のコード例は、キャッシュのさまざまな側面を示し、<xref:System.Windows.Automation.CacheRequest.Activate%2A> を使用して <xref:System.Windows.Automation.CacheRequest> をアクティブ化しています。  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## 使用例  
 次のコード例は、キャッシュのさまざまな側面を示し、<xref:System.Windows.Automation.CacheRequest.Push%2A> を使用して <xref:System.Windows.Automation.CacheRequest> をアクティブ化しています。 キャッシュ要求を入れ子にする場合を除き、<xref:System.Windows.Automation.CacheRequest.Activate%2A> を使用する方法をお勧めします。  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## 参照  
 [Caching in UI Automation Clients](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)