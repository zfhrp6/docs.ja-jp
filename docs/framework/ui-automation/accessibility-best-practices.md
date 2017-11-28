---
title: "ユーザー補助のベスト プラクティス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
caps.latest.revision: "16"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: d8714bb211c649d783cb1cfc46058e3b097def26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="accessibility-best-practices"></a><span data-ttu-id="8c47f-102">ユーザー補助のベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="8c47f-102">Accessibility Best Practices</span></span>
> [!NOTE]
>  <span data-ttu-id="8c47f-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="8c47f-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8c47f-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c47f-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="8c47f-105">コントロールやアプリケーションで以下のベスト プラクティスを実行すると、 [!INCLUDE[TLA#tla_at](../../../includes/tlasharptla-at-md.md)] デバイスを使用するユーザーのアクセシビリティ が向上します。</span><span class="sxs-lookup"><span data-stu-id="8c47f-105">Implementing the following best practices in controls or applications will improve their accessibility for people who use [!INCLUDE[TLA#tla_at](../../../includes/tlasharptla-at-md.md)] devices.</span></span> <span data-ttu-id="8c47f-106">これらのベスト プラクティスの多くは [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] に適した設計を中心としています。</span><span class="sxs-lookup"><span data-stu-id="8c47f-106">Many of these best practices focus on good [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] design.</span></span> <span data-ttu-id="8c47f-107">各ベスト プラクティスには、 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] コントロールまたはアプリケーションの実装の情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8c47f-107">Each best practice includes implementation information for [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] controls or applications.</span></span> <span data-ttu-id="8c47f-108">多くの場合、これらのベスト プラクティスに対応する作業は既に [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] コントロールに含まれています。</span><span class="sxs-lookup"><span data-stu-id="8c47f-108">In many cases, the work to meet these best practices is already included in [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] controls.</span></span>  
  
<a name="Programmatic_Access"></a>   
## <a name="programmatic-access"></a><span data-ttu-id="8c47f-109">プログラムによるアクセス</span><span class="sxs-lookup"><span data-stu-id="8c47f-109">Programmatic Access</span></span>  
 <span data-ttu-id="8c47f-110">プログラムによるアクセスにより、すべての [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 要素にラベルが付き、プロパティの値が公開され、適切なイベントが発生するようになります。</span><span class="sxs-lookup"><span data-stu-id="8c47f-110">Programmatic access involves ensuring that all [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elements are labeled, property values are exposed, and appropriate events are raised.</span></span> <span data-ttu-id="8c47f-111">標準の [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] コントロールでは、この作業の大部分が <xref:System.Windows.Automation.Peers.AutomationPeer>を介して既に実行されています。</span><span class="sxs-lookup"><span data-stu-id="8c47f-111">For standard [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] controls, most of this work is already done through <xref:System.Windows.Automation.Peers.AutomationPeer>.</span></span> <span data-ttu-id="8c47f-112">カスタム コントロールでは、プログラムによるアクセスが正しく実装されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c47f-112">Custom controls require additional work to ensure that programmatic access is correctly implemented.</span></span>  
  
<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>   
### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a><span data-ttu-id="8c47f-113">すべての UI 要素とテキストでのプログラムによるアクセスの有効化</span><span class="sxs-lookup"><span data-stu-id="8c47f-113">Enable Programmatic Access to all UI Elements and Text</span></span>  
 [!INCLUDE[TLA#tla_ui#initcap](../../../includes/tlasharptla-uisharpinitcap-md.md)]<span data-ttu-id="8c47f-114"> 要素では、プログラムによるアクセスを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c47f-114"> elements should enable programmatic access.</span></span> <span data-ttu-id="8c47f-115">[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] が標準的な [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] コントロールである場合、プログラムによるアクセスのサポートがコントロールに含まれます。</span><span class="sxs-lookup"><span data-stu-id="8c47f-115">If the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] is a standard [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control, support for programmatic access is included in the control.</span></span> <span data-ttu-id="8c47f-116">コントロールがカスタム コントロール (コモン コントロールのサブクラスに指定されているコントロール、またはコントロールからサブクラスに指定されたコントロール) である場合、変更が必要な領域に対する <xref:System.Windows.Automation.Peers.AutomationPeer> の実装を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c47f-116">If the control is a custom control – a control that has been subclassed from a common control or a control that has been subclassed from Control – then you must check the <xref:System.Windows.Automation.Peers.AutomationPeer> implementation for areas that may need modification.</span></span>  
  
 <span data-ttu-id="8c47f-117">このベスト プラクティスに従うことで [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] ベンダーは、製品の [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]の要素を特定および操作することができます。</span><span class="sxs-lookup"><span data-stu-id="8c47f-117">Following this best practice allows [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] vendors to identify and manipulate elements of your product's [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].</span></span>  
  
<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>   
### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a><span data-ttu-id="8c47f-118">UI オブジェクト、フレーム、およびページにおける、場所の名前、タイトル、説明</span><span class="sxs-lookup"><span data-stu-id="8c47f-118">Place Names, Titles, and Descriptions on UI Objects, Frames, and Pages</span></span>  
 <span data-ttu-id="8c47f-119">スクリーン リーダーなどの支援のテクノロジでは、ナビゲーション スキーム内のフレーム、オブジェクト、またはページの場所を理解するためにタイトルを使用します。</span><span class="sxs-lookup"><span data-stu-id="8c47f-119">Assistive technologies, especially screen readers, use the title to understand the location of the frame, object, or page in the navigation scheme.</span></span> <span data-ttu-id="8c47f-120">そのため、タイトルは非常にわかりやすくする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c47f-120">Therefore, the title must be very descriptive.</span></span> <span data-ttu-id="8c47f-121">たとえば、「Microsoft Web ページ」といった Web ページのタイトルでは、ユーザーはいくつかの特定の領域に深く入っていった場合に役に立ちません。</span><span class="sxs-lookup"><span data-stu-id="8c47f-121">For example, a Web page title of "Microsoft Web Page" is useless if the user has navigated deeply into some particular area.</span></span> <span data-ttu-id="8c47f-122">わかりやすいタイトルは、スクリーン リーダーに依存する視覚障がい者にとって重要です。</span><span class="sxs-lookup"><span data-stu-id="8c47f-122">A descriptive title is critical for users who are blind and depend on screen readers.</span></span> <span data-ttu-id="8c47f-123">同様に、 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] コントロールでも、 <xref:System.Windows.Automation.AutomationProperties.NameProperty> と <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> は [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] デバイスにとって重要です。</span><span class="sxs-lookup"><span data-stu-id="8c47f-123">Similarly, for [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] controls, <xref:System.Windows.Automation.AutomationProperties.NameProperty> and <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> are important for [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] devices.</span></span>  
  
 <span data-ttu-id="8c47f-124">このベスト プラクティスに従うことにより、 [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)]はサンプル コントロールとアプリケーションの [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] を特定および操作できるようになります。</span><span class="sxs-lookup"><span data-stu-id="8c47f-124">Following this best practice allows [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)]s to identify and manipulate [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] in sample controls and applications.</span></span>  
  
<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>   
### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a><span data-ttu-id="8c47f-125">プログラムによるイベントが、すべての UI 操作によってトリガーされることを確認する</span><span class="sxs-lookup"><span data-stu-id="8c47f-125">Ensure Programmatic Events Are Triggered by All UI Activities</span></span>  
 <span data-ttu-id="8c47f-126">このベスト プラクティスに従うことにより、 [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)]は [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] の変化をリッスンし、変化についてユーザーに通知できるようになります。</span><span class="sxs-lookup"><span data-stu-id="8c47f-126">Following this best practice allows [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)]s to listen for changes in the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] and notify the user about these changes.</span></span>  
  
<a name="User_Settings"></a>   
## <a name="user-settings"></a><span data-ttu-id="8c47f-127">ユーザー設定</span><span class="sxs-lookup"><span data-stu-id="8c47f-127">User Settings</span></span>  
 <span data-ttu-id="8c47f-128">このセクションのベスト プラクティスでは、コントロールやアプリケーションはユーザー設定をオーバーライドしないようにします。</span><span class="sxs-lookup"><span data-stu-id="8c47f-128">The best practice in this section ensures that controls or applications do not override user settings.</span></span>  
  
<a name="Respect_all_System_Wide_Settings_and_do_not_Interfere"></a>   
### <a name="respect-all-system-wide-settings-and-do-not-interfere-with-accessibility-functions"></a><span data-ttu-id="8c47f-129">すべてのシステム全体の設定を尊重し、ユーザー補助機能に干渉しない</span><span class="sxs-lookup"><span data-stu-id="8c47f-129">Respect All System-Wide Settings and Do Not Interfere with Accessibility Functions</span></span>  
 <span data-ttu-id="8c47f-130">ユーザーは、コントロール パネルを使用して、システム全体のフラグを設定できます。その他のフラグはプログラムで設定できます。</span><span class="sxs-lookup"><span data-stu-id="8c47f-130">Users can use the Control Panel to set some system-wide flags; other flags can be set programmatically.</span></span> <span data-ttu-id="8c47f-131">これらの設定は、コントロールやアプリケーションで変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="8c47f-131">These settings should not be changed by controls or applications.</span></span> <span data-ttu-id="8c47f-132">また、アプリケーションは、ホスト オペレーティング システムのユーザー補助の設定をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c47f-132">Also, applications must support the accessibility settings of their host operating system.</span></span>  
  
 <span data-ttu-id="8c47f-133">このベスト プラクティスに従うことにより、ユーザーはユーザー補助の設定を行えるとともに、これらの設定がアプリケーションによって変更されないことを認識できます。</span><span class="sxs-lookup"><span data-stu-id="8c47f-133">Following this best practice allows users to set accessibility settings and know that those settings will not be changed by applications.</span></span>  
  
<a name="Visual_UI_Design"></a>   
## <a name="visual-ui-design"></a><span data-ttu-id="8c47f-134">UI のビジュアル デザイン</span><span class="sxs-lookup"><span data-stu-id="8c47f-134">Visual UI Design</span></span>  
 <span data-ttu-id="8c47f-135">このセクションのベスト プラクティスでは、コントロールまたはアプリケーションが色と画像を効果的に使用するとともに、 [!INCLUDE[TLA2#tla_at#plural](../../../includes/tla2sharptla-atsharpplural-md.md)]によって使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="8c47f-135">Best Practices in this section ensure that controls or applications use color and images effectively and are able to be used by [!INCLUDE[TLA2#tla_at#plural](../../../includes/tla2sharptla-atsharpplural-md.md)].</span></span>  
  
<a name="Don_t_Hard_Code_Colors"></a>   
### <a name="dont-hard-code-colors"></a><span data-ttu-id="8c47f-136">色をハードコーディングしない</span><span class="sxs-lookup"><span data-stu-id="8c47f-136">Don't Hard-Code Colors</span></span>  
 <span data-ttu-id="8c47f-137">色覚に障がいがあるユーザー、弱視のユーザー、または白黒の画面を使用するユーザーは、ハード コーディングされた色を持つアプリケーションを使用できません。</span><span class="sxs-lookup"><span data-stu-id="8c47f-137">People who are color blind, have low vision, or are using a black and white screen might not be able to use applications with hard-coded colors.</span></span>  
  
 <span data-ttu-id="8c47f-138">このベスト プラクティスに従うことにより、ユーザーは、個人のニーズに基づいて色の組み合わせを調整できるようになります。</span><span class="sxs-lookup"><span data-stu-id="8c47f-138">Following this best practice allows users to adjust color combinations based on individual needs.</span></span>  
  
<a name="Support_High_Contrast_and_all_System_Display_Attributes"></a>   
### <a name="support-high-contrast-and-all-system-display-attributes"></a><span data-ttu-id="8c47f-139">ハイ コントラストとすべてのシステム表示属性をサポートする</span><span class="sxs-lookup"><span data-stu-id="8c47f-139">Support High Contrast and all System Display Attributes</span></span>  
 <span data-ttu-id="8c47f-140">アプリケーションは、ユーザーが選択したシステム全体のコントラスト設定、色の選択、またはその他のシステム全体のディスプレイの設定と属性を中断または無効にしてはなりません。</span><span class="sxs-lookup"><span data-stu-id="8c47f-140">Applications should not disrupt or disable user-selected, system-wide contrast settings, color selections, or other system-wide display settings and attributes.</span></span> <span data-ttu-id="8c47f-141">ユーザーが採用しているシステム全体の設定は、アプリケーションのユーザー補助機能を強化します。そのため、これをアプリケーションによって無効にしたり、無視したりしないでください。</span><span class="sxs-lookup"><span data-stu-id="8c47f-141">System-wide settings adopted by a user enhance the accessibility of applications, so they should not be disabled or disregarded by applications.</span></span> <span data-ttu-id="8c47f-142">色は、正しいコントラストを提供するため、正しい前景色と背景色の組み合わせで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c47f-142">Color should be used in their correct foreground-on-background combination to provide proper contrast.</span></span> <span data-ttu-id="8c47f-143">関係のない色を混在させないでください。また、色を反転させないでください。</span><span class="sxs-lookup"><span data-stu-id="8c47f-143">Unrelated colors should not be mixed, and colors should not be reversed.</span></span>  
  
 <span data-ttu-id="8c47f-144">黒の背景に白いテキストなど、特定のハイ コントラストの組み合わせが必要なユーザーは多数います。</span><span class="sxs-lookup"><span data-stu-id="8c47f-144">Many users require specific high-contrast combinations, such as white text on a black background.</span></span> <span data-ttu-id="8c47f-145">それらを反転させて、白地に黒のテキストとして描画すると、前景色の上に背景色がにじみ、一部のユーザーには読みづらくなります。</span><span class="sxs-lookup"><span data-stu-id="8c47f-145">Drawing these reversed, as black text on a white background causes the background to bleed over the foreground and can make reading difficult for some users.</span></span>  
  
<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>   
### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a><span data-ttu-id="8c47f-146">すべての DPI 設定によってすべての UI を正しく拡大/縮小する</span><span class="sxs-lookup"><span data-stu-id="8c47f-146">Ensure All UI Correctly Scales by Any DPI Setting</span></span>  
 <span data-ttu-id="8c47f-147">すべての [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 設定によってすべての [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)] が正しく拡大/縮小されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8c47f-147">Ensure that all [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] can correctly scale by any [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)] setting.</span></span> <span data-ttu-id="8c47f-148">また、 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 要素が  1024 x 768、120 [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)]の画面に合っていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8c47f-148">Also, ensure that [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elements fit in a screen of 1024 x 768 with 120 [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)].</span></span>  
  
<a name="Navigation"></a>   
## <a name="navigation"></a><span data-ttu-id="8c47f-149">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="8c47f-149">Navigation</span></span>  
 <span data-ttu-id="8c47f-150">このセクションのベスト プラクティスでは、ナビゲーションがコントロールとアプリケーションで対処されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8c47f-150">Best Practices in this section ensure that navigation has been addressed for controls and applications.</span></span>  
  
<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>   
### <a name="provide-keyboard-interface-for-all-ui-elements"></a><span data-ttu-id="8c47f-151">すべての UI 要素にキーボード インターフェイスを指定する</span><span class="sxs-lookup"><span data-stu-id="8c47f-151">Provide Keyboard Interface for All UI Elements</span></span>  
 <span data-ttu-id="8c47f-152">タブ ストップは、特に慎重に計画された場合は、ユーザーが [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]をナビゲートする別の方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="8c47f-152">Tab stops, especially when carefully planned, give users another way to navigate the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="8c47f-153">アプリケーションは、次のキーボード インターフェイスを備えている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c47f-153">Applications should provide the following keyboard interfaces:</span></span>  
  
-   <span data-ttu-id="8c47f-154">ボタン、リンク、またはリスト ボックスなど、ユーザーが操作できるすべてのコントロールのタブ ストップ</span><span class="sxs-lookup"><span data-stu-id="8c47f-154">tab stops for all controls that the user can interact with, such as buttons, links, or list boxes</span></span>  
  
-   <span data-ttu-id="8c47f-155">論理的なタブの順序</span><span class="sxs-lookup"><span data-stu-id="8c47f-155">logical tab order</span></span>  
  
<a name="Show_the_Keyboard_Focus"></a>   
### <a name="show-the-keyboard-focus"></a><span data-ttu-id="8c47f-156">キーボード フォーカスの表示</span><span class="sxs-lookup"><span data-stu-id="8c47f-156">Show the Keyboard Focus</span></span>  
 <span data-ttu-id="8c47f-157">ユーザーがキーストロークの効果を予測できるように、ユーザーはどのオブジェクトにキーボード フォーカスがあるかを認識しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c47f-157">Users need to know which object has the keyboard focus so that they can anticipate the effect of their keystrokes.</span></span> <span data-ttu-id="8c47f-158">キーボード フォーカスを強調表示するには、色、フォント、または四角形や拡大などのグラフィックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="8c47f-158">To highlight the keyboard focus, use colors, fonts, or graphics such as rectangles or magnification.</span></span> <span data-ttu-id="8c47f-159">キーボード フォーカスを音声で強調表示するには、音量、音の高さ、または音質を変更します。</span><span class="sxs-lookup"><span data-stu-id="8c47f-159">To audibly highlight the keyboard focus, change the volume, pitch or tonal quality.</span></span>  
  
 <span data-ttu-id="8c47f-160">混乱を回避するには、アプリケーションはビジュアル フォーカス インジケーターをすべて非表示にし、非アクティブなウィンドウ (またはペイン) にある選択項目を暗くする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c47f-160">To avoid confusion, applications should hide all visual focus indicators and dim selections that are located in inactive windows (or panes).</span></span>  
  
 <span data-ttu-id="8c47f-161">アプリケーションは、キーボード フォーカスで以下を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c47f-161">Applications should do the following with keyboard focus:</span></span>  
  
-   <span data-ttu-id="8c47f-162">1 つの項目が常にキーボード フォーカスされている必要がある</span><span class="sxs-lookup"><span data-stu-id="8c47f-162">one item should always have keyboard focus</span></span>  
  
-   <span data-ttu-id="8c47f-163">キーボード フォーカスは明確に表示されている必要がある</span><span class="sxs-lookup"><span data-stu-id="8c47f-163">keyboard focus should be visible and obvious</span></span>  
  
-   <span data-ttu-id="8c47f-164">選択項目またはフォーカスされた項目は視覚的に強調表示されている必要がある</span><span class="sxs-lookup"><span data-stu-id="8c47f-164">selections and/or focused items should be visually highlighted</span></span>  
  
<a name="Support_Navigation_Standards_and_Powerful_Navigation"></a>   
### <a name="support-navigation-standards-and-powerful-navigation-schemes"></a><span data-ttu-id="8c47f-165">ナビゲーションの標準と強力なナビゲーション スキームをサポートする</span><span class="sxs-lookup"><span data-stu-id="8c47f-165">Support Navigation Standards and Powerful Navigation Schemes</span></span>  
 <span data-ttu-id="8c47f-166">さまざまなキーボード ナビゲーションの側面で、ユーザーが [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]をナビゲートするさまざまな方法が提供されています。</span><span class="sxs-lookup"><span data-stu-id="8c47f-166">Different aspects of keyboard navigation provide different ways for users to navigate the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="8c47f-167">アプリケーションは、次のキーボード インターフェイスを備えている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c47f-167">Applications should provide the following keyboard interfaces:</span></span>  
  
-   <span data-ttu-id="8c47f-168">すべてのコマンド、メニュー、およびコントロール用のショートカット キーと下線付きのアクセス キー</span><span class="sxs-lookup"><span data-stu-id="8c47f-168">shortcut keys and underlined access keys for all commands, menus and controls</span></span>  
  
-   <span data-ttu-id="8c47f-169">重要なリンクへのキーボード ショートカット</span><span class="sxs-lookup"><span data-stu-id="8c47f-169">keyboard shortcuts to important links</span></span>  
  
-   <span data-ttu-id="8c47f-170">すべてのメニュー項目にアクセス キーがあり、すべてのボタンにアクセラレータ キーがあり、すべてのコマンドにアクセラレータ キーがある</span><span class="sxs-lookup"><span data-stu-id="8c47f-170">all menu items have an access key; all buttons have accelerator keys, all commands have an accelerator key.</span></span>  
  
<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>   
### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a><span data-ttu-id="8c47f-171">マウスの位置がキーボード ナビゲーションと干渉しないようにする</span><span class="sxs-lookup"><span data-stu-id="8c47f-171">Do Not Let Mouse Location Interfere with Keyboard Navigation</span></span>  
 <span data-ttu-id="8c47f-172">マウスの位置は、キーボードのナビゲーションと干渉しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="8c47f-172">Mouse location should not interfere with keyboard navigation.</span></span> <span data-ttu-id="8c47f-173">たとえば、マウスが別の場所に位置し、ユーザーがキーボードでナビゲートする場合、マウスのクリックは、ユーザーが開始するまで発生しないようにします。</span><span class="sxs-lookup"><span data-stu-id="8c47f-173">For example, if the mouse is positioned someplace and the user is navigating with the keyboard, a mouse click should not happen unless initiated by the user.</span></span>  
  
<a name="Multimodal_Interface"></a>   
## <a name="multimodal-interface"></a><span data-ttu-id="8c47f-174">マルチモーダル インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c47f-174">Multimodal Interface</span></span>  
 <span data-ttu-id="8c47f-175">このセクションのベスト プラクティスでは、アプリケーション [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] にはビジュアル要素の代替案が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8c47f-175">Best Practices in this section ensure that application [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] includes alternatives for visual elements.</span></span>  
  
<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>   
### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a><span data-ttu-id="8c47f-176">テキスト以外の要素に相当する、ユーザーが選択可能な項目を提供する</span><span class="sxs-lookup"><span data-stu-id="8c47f-176">Provide User-Selectable Equivalents for Non-Text Elements</span></span>  
 <span data-ttu-id="8c47f-177">テキスト以外の各要素について、テキスト、チャット内容、または音声による説明 (代替テキスト、キャプション、視覚的なフィードバックなど) に相当する、ユーザーが選択可能な項目を提供します。</span><span class="sxs-lookup"><span data-stu-id="8c47f-177">For each non-text element, provide a user-selectable equivalent for text, transcripts, or audio descriptions, such as alt text, captions, or visual feedback.</span></span>  
  
 <span data-ttu-id="8c47f-178">テキスト以外の要素には、幅広い範囲の [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 要素 (画像、画像マップ領域、アニメーション、アプレット、フレーム、スクリプト、グラフィカルなボタン、サウンド、スタンドアロンのオーディオ ファイル、およびビデオなど) があります。</span><span class="sxs-lookup"><span data-stu-id="8c47f-178">Non-text elements cover a wide range of [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elements including: images, image map regions, animations, applets, frames, scripts, graphical buttons, sounds, stand-alone audio files and video.</span></span> <span data-ttu-id="8c47f-179">テキスト以外の要素は、 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]のコンテンツを理解するためにユーザーがアクセスを必要とする視覚的な情報、音声、または通常のオーディオ情報が含まれる場合は重要になります。</span><span class="sxs-lookup"><span data-stu-id="8c47f-179">Non-text elements are important when they contain visual information, speech, or general audio information that the user needs access to in order to understand the content of the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].</span></span>  
  
<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>   
### <a name="use-color-but-also-provide-alternatives-to-color"></a><span data-ttu-id="8c47f-180">色を使用するだけでなく、色の代替手段を提供する</span><span class="sxs-lookup"><span data-stu-id="8c47f-180">Use Color but Also Provide Alternatives to Color</span></span>  
 <span data-ttu-id="8c47f-181">色を使用して、他の手段によって示される情報を強化、強調、または再反復処理します。ただし、色単独を使用して情報を伝達しないでください。</span><span class="sxs-lookup"><span data-stu-id="8c47f-181">Use color to enhance, emphasize, or reiterate information shown by other means, but do not communicate information by using color alone.</span></span> <span data-ttu-id="8c47f-182">色覚に障がいがあるユーザーまたは白黒表示のディスプレイを持つユーザーには、色の代替手段が必要です。</span><span class="sxs-lookup"><span data-stu-id="8c47f-182">Users who are color blind or have a monochrome display need alternatives to color.</span></span>  
  
<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>   
### <a name="use-standard-input-apis-with-device-independent-calls"></a><span data-ttu-id="8c47f-183">デバイスに依存しない呼び出しで標準の入力 API を使用する</span><span class="sxs-lookup"><span data-stu-id="8c47f-183">Use Standard Input APIs with Device-Independent Calls</span></span>  
 <span data-ttu-id="8c47f-184">デバイスに依存しない呼び出しは、キーボードとマウスの機能が同等であることを保証する一方、 [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] に関する必要な情報を [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]に提供します。</span><span class="sxs-lookup"><span data-stu-id="8c47f-184">Device-independent calls ensure keyboard and mouse feature equality, while providing [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] with needed information about the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c47f-185">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c47f-185">See Also</span></span>  
 <xref:System.Windows.Automation.Peers>  
 [<span data-ttu-id="8c47f-186">NumericUpDown カスタム コントロールのテーマと UI オートメーションのサポートのサンプル</span><span class="sxs-lookup"><span data-stu-id="8c47f-186">NumericUpDown Custom Control with Theme and UI Automation Support Sample</span></span>](http://msdn.microsoft.com/en-us/9aed3c10-68eb-419e-a57f-1d2af15a8253)  
 [<span data-ttu-id="8c47f-187">キーボード ユーザー インターフェイス設計のガイドライン</span><span class="sxs-lookup"><span data-stu-id="8c47f-187">Guidelines for Keyboard User Interface Design</span></span>](http://msdn2.microsoft.com/library/ms971323.aspx)
