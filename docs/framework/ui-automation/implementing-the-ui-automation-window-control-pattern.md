---
title: UI オートメーション Window コントロール パターンの実装
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 73a484ea6165b4e38901630730c7ba985a5608ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408022"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a><span data-ttu-id="52af5-102">UI オートメーション Window コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="52af5-102">Implementing the UI Automation Window Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="52af5-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="52af5-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="52af5-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52af5-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="52af5-105">このトピックでは、 <xref:System.Windows.Automation.Provider.IWindowProvider>のプロパティ、メソッド、イベントに関する情報など、 <xref:System.Windows.Automation.WindowPattern> の実装のためのガイドラインと規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="52af5-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IWindowProvider>, including information about <xref:System.Windows.Automation.WindowPattern> properties, methods, and events.</span></span> <span data-ttu-id="52af5-106">その他のリファレンスへのリンクは、このトピックの最後に記載します。</span><span class="sxs-lookup"><span data-stu-id="52af5-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="52af5-107"><xref:System.Windows.Automation.WindowPattern> コントロール パターンは、従来の [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)]内で、ウィンドウ ベースの基本的な機能を提供するコントロールをサポートするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="52af5-107">The <xref:System.Windows.Automation.WindowPattern> control pattern is used to support controls that provide fundamental window-based functionality within a traditional [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)].</span></span> <span data-ttu-id="52af5-108">このコントロール パターンを実装する必要があるコントロールの例として、最上位のアプリケーション ウィンドウ、 [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] 子ウィンドウ、サイズ変更可能な分割ウィンドウ コントロール、モーダル ダイアログ ボックス、バルーン ヘルプ ウィンドウがあります。</span><span class="sxs-lookup"><span data-stu-id="52af5-108">Examples of controls that must implement this control pattern include top-level application windows, [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] child windows, resizable split pane controls, modal dialogs and balloon help windows.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="52af5-109">実装のガイドラインと規則</span><span class="sxs-lookup"><span data-stu-id="52af5-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="52af5-110">Window コントロール パターンを実装する場合は、次のガイドラインと規則に注意してください。</span><span class="sxs-lookup"><span data-stu-id="52af5-110">When implementing the Window control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="52af5-111">UI オートメーションを使用してウィンドウのサイズと位置の両方を変更する機能をサポートするには、コントロールが <xref:System.Windows.Automation.Provider.ITransformProvider> に加えて <xref:System.Windows.Automation.Provider.IWindowProvider>を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52af5-111">To support the ability to modify both window size and screen position using UI Automation, a control must implement <xref:System.Windows.Automation.Provider.ITransformProvider> in addition to <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
-   <span data-ttu-id="52af5-112">コントロールを移動、サイズ変更、最大化、最小化、および閉じられるようにするタイトル バーの要素とタイトル バーを格納するコントロールは、通常 <xref:System.Windows.Automation.Provider.IWindowProvider>を実装することが求められます。</span><span class="sxs-lookup"><span data-stu-id="52af5-112">Controls that contain title bars and title bar elements that enable the control to be moved, resized, maximized, minimized, or closed are typically required to implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
-   <span data-ttu-id="52af5-113">ツールヒントのポップアップやコンボ ボックス、またはメニューのドロップダウンなどのコントロールは、通常 <xref:System.Windows.Automation.Provider.IWindowProvider>を実装しません。</span><span class="sxs-lookup"><span data-stu-id="52af5-113">Controls such as tooltip pop-ups and combo box or menu drop-downs do not typically implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
-   <span data-ttu-id="52af5-114">バルーン ヘルプ ウィンドウは、ウィンドウと同様の閉じるボタンを提供することで、基本的なツールヒント ポップアップから区別されます。</span><span class="sxs-lookup"><span data-stu-id="52af5-114">Balloon help windows are differentiated from basic tooltip pop-ups by the provision of a window-like Close button.</span></span>  
  
-   <span data-ttu-id="52af5-115">全画面表示モードは、アプリケーション固有の機能であり、通常のウィンドウの動作ではないため、IWindowProvider によってサポートされません。</span><span class="sxs-lookup"><span data-stu-id="52af5-115">Full-screen mode is not supported by IWindowProvider as it is feature-specific to an application and is not typical window behavior.</span></span>  
  
<a name="Required_Members_for_IWindowProvider"></a>   
## <a name="required-members-for-iwindowprovider"></a><span data-ttu-id="52af5-116">IWindowProvider の必須メンバー</span><span class="sxs-lookup"><span data-stu-id="52af5-116">Required Members for IWindowProvider</span></span>  
 <span data-ttu-id="52af5-117">IWindowProvider インターフェイスには、次のプロパティ、メソッド、イベントが必要です。</span><span class="sxs-lookup"><span data-stu-id="52af5-117">The following properties, methods, and events are required for the IWindowProvider interface.</span></span>  
  
|<span data-ttu-id="52af5-118">必須メンバー</span><span class="sxs-lookup"><span data-stu-id="52af5-118">Required member</span></span>|<span data-ttu-id="52af5-119">メンバーの型</span><span class="sxs-lookup"><span data-stu-id="52af5-119">Member type</span></span>|<span data-ttu-id="52af5-120">メモ</span><span class="sxs-lookup"><span data-stu-id="52af5-120">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|<span data-ttu-id="52af5-121">プロパティ</span><span class="sxs-lookup"><span data-stu-id="52af5-121">Property</span></span>|<span data-ttu-id="52af5-122">なし</span><span class="sxs-lookup"><span data-stu-id="52af5-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|<span data-ttu-id="52af5-123">プロパティ</span><span class="sxs-lookup"><span data-stu-id="52af5-123">Property</span></span>|<span data-ttu-id="52af5-124">なし</span><span class="sxs-lookup"><span data-stu-id="52af5-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|<span data-ttu-id="52af5-125">プロパティ</span><span class="sxs-lookup"><span data-stu-id="52af5-125">Property</span></span>|<span data-ttu-id="52af5-126">なし</span><span class="sxs-lookup"><span data-stu-id="52af5-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|<span data-ttu-id="52af5-127">プロパティ</span><span class="sxs-lookup"><span data-stu-id="52af5-127">Property</span></span>|<span data-ttu-id="52af5-128">なし</span><span class="sxs-lookup"><span data-stu-id="52af5-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|<span data-ttu-id="52af5-129">プロパティ</span><span class="sxs-lookup"><span data-stu-id="52af5-129">Property</span></span>|<span data-ttu-id="52af5-130">なし</span><span class="sxs-lookup"><span data-stu-id="52af5-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|<span data-ttu-id="52af5-131">プロパティ</span><span class="sxs-lookup"><span data-stu-id="52af5-131">Property</span></span>|<span data-ttu-id="52af5-132">なし</span><span class="sxs-lookup"><span data-stu-id="52af5-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|<span data-ttu-id="52af5-133">メソッド</span><span class="sxs-lookup"><span data-stu-id="52af5-133">Method</span></span>|<span data-ttu-id="52af5-134">なし</span><span class="sxs-lookup"><span data-stu-id="52af5-134">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|<span data-ttu-id="52af5-135">メソッド</span><span class="sxs-lookup"><span data-stu-id="52af5-135">Method</span></span>|<span data-ttu-id="52af5-136">なし</span><span class="sxs-lookup"><span data-stu-id="52af5-136">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|<span data-ttu-id="52af5-137">メソッド</span><span class="sxs-lookup"><span data-stu-id="52af5-137">Method</span></span>|<span data-ttu-id="52af5-138">なし</span><span class="sxs-lookup"><span data-stu-id="52af5-138">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|<span data-ttu-id="52af5-139">event</span><span class="sxs-lookup"><span data-stu-id="52af5-139">Event</span></span>|<span data-ttu-id="52af5-140">なし</span><span class="sxs-lookup"><span data-stu-id="52af5-140">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|<span data-ttu-id="52af5-141">event</span><span class="sxs-lookup"><span data-stu-id="52af5-141">Event</span></span>|<span data-ttu-id="52af5-142">なし</span><span class="sxs-lookup"><span data-stu-id="52af5-142">None</span></span>|  
|<xref:System.Windows.Automation.WindowInteractionState>|<span data-ttu-id="52af5-143">event</span><span class="sxs-lookup"><span data-stu-id="52af5-143">Event</span></span>|<span data-ttu-id="52af5-144"><xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span><span class="sxs-lookup"><span data-stu-id="52af5-144">Is not guaranteed to be <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span></span>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="52af5-145">例外</span><span class="sxs-lookup"><span data-stu-id="52af5-145">Exceptions</span></span>  
 <span data-ttu-id="52af5-146">プロバイダーは、次の例外をスローする必要があります。</span><span class="sxs-lookup"><span data-stu-id="52af5-146">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="52af5-147">例外の種類</span><span class="sxs-lookup"><span data-stu-id="52af5-147">Exception type</span></span>|<span data-ttu-id="52af5-148">条件</span><span class="sxs-lookup"><span data-stu-id="52af5-148">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> <span data-ttu-id="52af5-149">-コントロールでは、要求された動作をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="52af5-149">-   When a control does not support a requested behavior.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> <span data-ttu-id="52af5-150">場合、パラメーターは、有効な数値ではありません。</span><span class="sxs-lookup"><span data-stu-id="52af5-150">-   When the parameter is not a valid number.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="52af5-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="52af5-151">See Also</span></span>  
 [<span data-ttu-id="52af5-152">UI Automation コントロール パターンの概要</span><span class="sxs-lookup"><span data-stu-id="52af5-152">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="52af5-153">UI オートメーション プロバイダーでのコントロール パターンのサポート</span><span class="sxs-lookup"><span data-stu-id="52af5-153">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="52af5-154">クライアントの UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="52af5-154">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="52af5-155">UI Automation ツリーの概要</span><span class="sxs-lookup"><span data-stu-id="52af5-155">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="52af5-156">UI オートメーションにおけるキャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="52af5-156">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
