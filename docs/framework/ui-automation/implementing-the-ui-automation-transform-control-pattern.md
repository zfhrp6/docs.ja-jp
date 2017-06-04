---
title: "Implementing the UI Automation Transform Control Pattern | Microsoft Docs"
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
  - "control patterns, Transform"
  - "Transform control pattern"
  - "UI Automation, Transform control pattern"
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
caps.latest.revision: 14
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 14
---
# Implementing the UI Automation Transform Control Pattern
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] の最新情報については、「[Windows Automation API: UI オートメーション](http://go.microsoft.com/fwlink/?LinkID=156746)」をご覧ください。  
  
 このトピックでは、プロパティ、メソッド、イベントに関する情報など、<xref:System.Windows.Automation.Provider.ITransformProvider> の実装のためのガイドラインと規則について説明します。 その他のリファレンスへのリンクは、トピックの最後に記載します。  
  
 <xref:System.Windows.Automation.TransformPattern> コントロール パターンは、2 次元空間で移動、サイズ変更、または回転できるコントロールをサポートするために使用されます。 このコントロール パターンを実装するコントロールの例については、「[Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)」をご覧ください。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## 実装のガイドラインと規則  
 Transform コントロール パターンを実装する場合は、次のガイドラインと規則にご留意ください。  
  
-   このコントロール パターンのサポートは、デスクトップ上のオブジェクトに制限されません。 コンテナーの境界内で子が自由に移動、サイズ変更、または回転できるようにする場合は、そのコンテナー オブジェクトの子もこのコントロール パターンをサポートしている必要があります。  
  
-   操作後の画面位置が完全にそのコンテナーの座標外となり、キーボードやマウスからアクセスできなくなる場合 \(たとえば、トップレベルのウィンドウが画面外に移動したり、子オブジェクトがコンテナーのビューポートの境界外へ移動したりする場合\) は、オブジェクトの移動、サイズ変更、および回転はできません。 このような場合、上辺または左辺の座標をコンテナーの境界内にオーバーライドして、要求された画面座標のできるだけ近くにオブジェクトが配置されます。  
  
-   マルチモニター システムでは、結合したデスクトップ画面座標の完全に外へオブジェクトを移動、サイズ変更、または回転した場合、プライマリ モニター上の、要求された画面座標のできるだけ近くにオブジェクトが配置されます。  
  
-   すべてのパラメーターとプロパティの値は絶対値で、ロケールには依存しません。  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## ITransformProvider の必須メンバー  
 <xref:System.Windows.Automation.Provider.ITransformProvider> の実装には、次のプロパティとメソッドが必要です。  
  
|必須メンバー|メンバーの型|ノート|  
|------------|------------|---------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|メソッド|なし|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|メソッド|なし|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|メソッド|なし|  
  
 このコントロール パターンに関連付けられたイベントはありません。  
  
<a name="Exceptions"></a>   
## 例外  
 プロバイダーは、次の例外をスローする必要があります。  
  
|例外の種類|状態|  
|-----------|--------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> -   <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> が false の場合。|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> -   <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> が false の場合。|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> -   <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> が false の場合。|  
  
## 参照  
 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)   
 [Support Control Patterns in a UI Automation Provider](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)   
 [UI Automation Control Patterns for Clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)   
 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)   
 [Use Caching in UI Automation](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)