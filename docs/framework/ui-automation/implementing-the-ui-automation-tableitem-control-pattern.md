---
title: "UI オートメーション TableItem コントロール パターンの実装"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
caps.latest.revision: "14"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 5861ab24627f9b78cd20f97fcdb1b1b3d681991a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a>UI オートメーション TableItem コントロール パターンの実装
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](http://go.microsoft.com/fwlink/?LinkID=156746)」をご覧ください。  
  
 このトピックのガイドラインと規則を実装するための導入<xref:System.Windows.Automation.Provider.ITableItemProvider>、イベントおよびプロパティに関する情報も含まれます。 その他のリファレンスへのリンクは、概要の最後に記載します。  
  
 <xref:System.Windows.Automation.TableItemPattern>コントロール パターンを実装するコンテナーの子コントロールをサポートするために使用<xref:System.Windows.Automation.Provider.ITableProvider>です。 個々 のセル機能へのアクセスが必要な同時実装によって提供される<xref:System.Windows.Automation.Provider.IGridItemProvider>です。 このコントロール パターンはに似て<xref:System.Windows.Automation.Provider.IGridItemProvider>を実装するコントロールを除いて、<xref:System.Windows.Automation.Provider.ITableItemProvider>プログラムによって、個々 のセルとその行および列情報間のリレーションシップを公開する必要があります。 このコントロール パターンを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)」をご覧ください。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>実装のガイドラインと規則  
  
-   関連するグリッド項目機能では、次を参照してください。 [UI オートメーション GridItem コントロール パターンを実装する](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)です。  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a>ITableItemProvider の必須メンバー  
  
|必須メンバー|メンバーの型|ノート|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|メソッド|なし|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|メソッド|なし|  
  
 このコントロール パターンに関連付けられるプロパティやイベントはありません。  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>例外  
 このコントロール パターンに関連付けられた例外はありません。  
  
## <a name="see-also"></a>関連項目  
 [UI オートメーション コントロール パターンの概要](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI オートメーション プロバイダーでコントロール パターンをサポートします。](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [クライアントの UI オートメーション コントロール パターン](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI オートメーション Table コントロール パターンを実装します。](../../../docs/framework/ui-automation/implementing-the-ui-automation-table-control-pattern.md)  
 [UI オートメーション GridItem コントロール パターンの実装](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)  
 [UI オートメーション ツリーの概要](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [UI オートメーションにおけるキャッシュを使用します。](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
