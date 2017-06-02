---
title: "Implementing the UI Automation Window Control Pattern | Microsoft Docs"
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
  - "control patterns, Window"
  - "UI Automation, Window control pattern"
  - "Window control pattern"
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
caps.latest.revision: 21
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 20
---
# Implementing the UI Automation Window Control Pattern
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] の最新情報については、「[Windows Automation API: UI オートメーション](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。  
  
 このトピックでは、<xref:System.Windows.Automation.WindowPattern> のプロパティ、メソッド、イベントに関する情報など、<xref:System.Windows.Automation.Provider.IWindowProvider> の実装のためのガイドラインと規則について説明します。 その他のリファレンスへのリンクは、このトピックの最後に記載します。  
  
 <xref:System.Windows.Automation.WindowPattern> コントロール パターンは、従来の [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)] 内で、ウィンドウ ベースの基本的な機能を提供するコントロールをサポートするために使用されます。 このコントロール パターンを実装する必要があるコントロールの例として、最上位のアプリケーション ウィンドウ、[!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] 子ウィンドウ、サイズ変更可能な分割ウィンドウ コントロール、モーダル ダイアログ ボックス、バルーン ヘルプ ウィンドウがあります。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## 実装のガイドラインと規則  
 Window コントロール パターンを実装する場合は、次のガイドラインと規則に注意してください。  
  
-   UI オートメーションを使用してウィンドウのサイズと位置の両方を変更する機能をサポートするには、コントロールが <xref:System.Windows.Automation.Provider.IWindowProvider> に加えて <xref:System.Windows.Automation.Provider.ITransformProvider> を実装する必要があります。  
  
-   コントロールを移動、サイズ変更、最大化、最小化、および閉じられるようにするタイトル バーの要素とタイトル バーを格納するコントロールは、通常 <xref:System.Windows.Automation.Provider.IWindowProvider> を実装することが求められます。  
  
-   ツールヒントのポップアップやコンボ ボックス、またはメニューのドロップダウンなどのコントロールは、通常 <xref:System.Windows.Automation.Provider.IWindowProvider> を実装しません。  
  
-   バルーン ヘルプ ウィンドウは、ウィンドウと同様の閉じるボタンを提供することで、基本的なツールヒント ポップアップから区別されます。  
  
-   全画面表示モードは、アプリケーション固有の機能であり、通常のウィンドウの動作ではないため、IWindowProvider によってサポートされません。  
  
<a name="Required_Members_for_IWindowProvider"></a>   
## IWindowProvider の必須メンバー  
 IWindowProvider インターフェイスには、次のプロパティ、メソッド、イベントが必要です。  
  
|必須メンバー|メンバーの型|ノート|  
|------------|------------|---------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|メソッド|なし|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|メソッド|なし|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|メソッド|なし|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|Event|なし|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|Event|なし|  
|<xref:System.Windows.Automation.WindowInteractionState>|イベント|<xref:System.Windows.Automation.WindowInteractionState> であると保証されない|  
  
<a name="Exceptions"></a>   
## 例外  
 プロバイダーは、次の例外をスローする必要があります。  
  
|例外の種類|状態|  
|-----------|--------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> -   コントロールが、要求された動作をサポートしない場合。|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> -   パラメーターが、有効な値ではない場合。|  
  
## 参照  
 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)   
 [Support Control Patterns in a UI Automation Provider](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)   
 [UI Automation Control Patterns for Clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)   
 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)   
 [Use Caching in UI Automation](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)