---
title: UI オートメーションによる標準コントロールのサポート
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 3ccd6e1348125f5d901e0f093d2b5483b818719f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="791cb-102">UI オートメーションによる標準コントロールのサポート</span><span class="sxs-lookup"><span data-stu-id="791cb-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="791cb-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="791cb-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="791cb-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="791cb-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="791cb-105">このトピックでは、 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 、 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]、および [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]フレームワーク向けに開発されたアプリケーションの標準コントロールに対する [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] サポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="791cb-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="791cb-106">Windows Presentation Foundation コントロール</span><span class="sxs-lookup"><span data-stu-id="791cb-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="791cb-107">ユーザー操作に関する情報やサポートを提供するすべての [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] コントロール要素は、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を全面的にネイティブ サポートしています。</span><span class="sxs-lookup"><span data-stu-id="791cb-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="791cb-108">パネルなどのその他の要素は、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]からは認識できません。</span><span class="sxs-lookup"><span data-stu-id="791cb-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="791cb-109">Win32 コントロール</span><span class="sxs-lookup"><span data-stu-id="791cb-109">Win32 Controls</span></span>  
 <span data-ttu-id="791cb-110">ほとんどの [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] コントロールは、UIAutomationClientsideProviders.dll のクライアント側プロバイダーによって [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] に公開されています。</span><span class="sxs-lookup"><span data-stu-id="791cb-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="791cb-111">このアセンブリは、UI オートメーション クライアント アプリケーションで使用するために、自動的に登録されます。</span><span class="sxs-lookup"><span data-stu-id="791cb-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="791cb-112">完全なサポートは、ComCtrl32.dll のバージョン 6 ( [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] 以降で使用可能) のコントロールに対してのみ提供されています。</span><span class="sxs-lookup"><span data-stu-id="791cb-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="791cb-113">次のコントロールがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="791cb-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="791cb-114">クラス名</span><span class="sxs-lookup"><span data-stu-id="791cb-114">Class name</span></span>|<span data-ttu-id="791cb-115">コントロール型</span><span class="sxs-lookup"><span data-stu-id="791cb-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="791cb-116">ボタン</span><span class="sxs-lookup"><span data-stu-id="791cb-116">Button</span></span>|<span data-ttu-id="791cb-117">ボタン</span><span class="sxs-lookup"><span data-stu-id="791cb-117">Button</span></span>|  
|<span data-ttu-id="791cb-118">ボタン</span><span class="sxs-lookup"><span data-stu-id="791cb-118">Button</span></span>|<span data-ttu-id="791cb-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="791cb-119">RadioButton</span></span>|  
|<span data-ttu-id="791cb-120">ボタン</span><span class="sxs-lookup"><span data-stu-id="791cb-120">Button</span></span>|<span data-ttu-id="791cb-121">グループ化</span><span class="sxs-lookup"><span data-stu-id="791cb-121">Group</span></span>|  
|<span data-ttu-id="791cb-122">ボタン</span><span class="sxs-lookup"><span data-stu-id="791cb-122">Button</span></span>|<span data-ttu-id="791cb-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="791cb-123">CheckBox</span></span>|  
|<span data-ttu-id="791cb-124">ボタン</span><span class="sxs-lookup"><span data-stu-id="791cb-124">Button</span></span>|<span data-ttu-id="791cb-125">ハイパーリンク</span><span class="sxs-lookup"><span data-stu-id="791cb-125">Hyperlink</span></span>|  
|<span data-ttu-id="791cb-126">ボタン</span><span class="sxs-lookup"><span data-stu-id="791cb-126">Button</span></span>|<span data-ttu-id="791cb-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="791cb-127">SplitButton</span></span>|  
|<span data-ttu-id="791cb-128">ボタン</span><span class="sxs-lookup"><span data-stu-id="791cb-128">Button</span></span>|<span data-ttu-id="791cb-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="791cb-129">CheckBox</span></span>|  
|<span data-ttu-id="791cb-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="791cb-130">ComboBoxEx32</span></span>|<span data-ttu-id="791cb-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="791cb-131">ComboBox</span></span>|  
|<span data-ttu-id="791cb-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="791cb-132">ComboBox</span></span>|<span data-ttu-id="791cb-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="791cb-133">ComboBox</span></span>|  
|<span data-ttu-id="791cb-134">編集</span><span class="sxs-lookup"><span data-stu-id="791cb-134">Edit</span></span>|<span data-ttu-id="791cb-135">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="791cb-135">Document</span></span>|  
|<span data-ttu-id="791cb-136">編集</span><span class="sxs-lookup"><span data-stu-id="791cb-136">Edit</span></span>|<span data-ttu-id="791cb-137">編集</span><span class="sxs-lookup"><span data-stu-id="791cb-137">Edit</span></span>|  
|<span data-ttu-id="791cb-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="791cb-138">SysLink</span></span>|<span data-ttu-id="791cb-139">ハイパーリンク</span><span class="sxs-lookup"><span data-stu-id="791cb-139">Hyperlink</span></span>|  
|<span data-ttu-id="791cb-140">スタティック</span><span class="sxs-lookup"><span data-stu-id="791cb-140">Static</span></span>|<span data-ttu-id="791cb-141">テキスト</span><span class="sxs-lookup"><span data-stu-id="791cb-141">Text</span></span>|  
|<span data-ttu-id="791cb-142">スタティック</span><span class="sxs-lookup"><span data-stu-id="791cb-142">Static</span></span>|<span data-ttu-id="791cb-143">イメージ</span><span class="sxs-lookup"><span data-stu-id="791cb-143">Image</span></span>|  
|<span data-ttu-id="791cb-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="791cb-144">SysIPAddress32</span></span>|<span data-ttu-id="791cb-145">カスタム</span><span class="sxs-lookup"><span data-stu-id="791cb-145">Custom</span></span>|  
|<span data-ttu-id="791cb-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="791cb-146">SysHeader32</span></span>|<span data-ttu-id="791cb-147">Header/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="791cb-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="791cb-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="791cb-148">SysListView32</span></span>|<span data-ttu-id="791cb-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="791cb-149">DataGrid</span></span>|  
|<span data-ttu-id="791cb-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="791cb-150">SysListView32</span></span>|<span data-ttu-id="791cb-151">リスト</span><span class="sxs-lookup"><span data-stu-id="791cb-151">List</span></span>|  
|<span data-ttu-id="791cb-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="791cb-152">ListBox</span></span>|<span data-ttu-id="791cb-153">リスト</span><span class="sxs-lookup"><span data-stu-id="791cb-153">List</span></span>|  
|<span data-ttu-id="791cb-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="791cb-154">ListBox</span></span>|<span data-ttu-id="791cb-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="791cb-155">ListItem</span></span>|  
|<span data-ttu-id="791cb-156">#32768</span><span class="sxs-lookup"><span data-stu-id="791cb-156">#32768</span></span>|<span data-ttu-id="791cb-157">メニュー</span><span class="sxs-lookup"><span data-stu-id="791cb-157">Menu</span></span>|  
|<span data-ttu-id="791cb-158">#32768</span><span class="sxs-lookup"><span data-stu-id="791cb-158">#32768</span></span>|<span data-ttu-id="791cb-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="791cb-159">MenuItem</span></span>|  
|<span data-ttu-id="791cb-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="791cb-160">msctls_progress32</span></span>|<span data-ttu-id="791cb-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="791cb-161">ProgressBar</span></span>|  
|<span data-ttu-id="791cb-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="791cb-162">RichEdit</span></span>|<span data-ttu-id="791cb-163">ドキュメント。</span><span class="sxs-lookup"><span data-stu-id="791cb-163">Document.</span></span> <span data-ttu-id="791cb-164">注を参照。</span><span class="sxs-lookup"><span data-stu-id="791cb-164">See note.</span></span>|  
|<span data-ttu-id="791cb-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="791cb-165">RichEdit20A</span></span>|<span data-ttu-id="791cb-166">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="791cb-166">Document</span></span>|  
|<span data-ttu-id="791cb-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="791cb-167">RichEdit20W</span></span>|<span data-ttu-id="791cb-168">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="791cb-168">Document</span></span>|  
|<span data-ttu-id="791cb-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="791cb-169">RichEdit50W</span></span>|<span data-ttu-id="791cb-170">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="791cb-170">Document</span></span>|  
|<span data-ttu-id="791cb-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="791cb-171">ScrollBar</span></span>|<span data-ttu-id="791cb-172">スライダー</span><span class="sxs-lookup"><span data-stu-id="791cb-172">Slider</span></span>|  
|<span data-ttu-id="791cb-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="791cb-173">msctls_trackbar32</span></span>|<span data-ttu-id="791cb-174">スライダー</span><span class="sxs-lookup"><span data-stu-id="791cb-174">Slider</span></span>|  
|<span data-ttu-id="791cb-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="791cb-175">msctls_updown32</span></span>|<span data-ttu-id="791cb-176">Spinner</span><span class="sxs-lookup"><span data-stu-id="791cb-176">Spinner</span></span>|  
|<span data-ttu-id="791cb-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="791cb-177">msctls_statusbar32</span></span>|<span data-ttu-id="791cb-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="791cb-178">StatusBar</span></span>|  
|<span data-ttu-id="791cb-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="791cb-179">SysTabControl32</span></span>|<span data-ttu-id="791cb-180">タブ</span><span class="sxs-lookup"><span data-stu-id="791cb-180">Tab</span></span>|  
|<span data-ttu-id="791cb-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="791cb-181">SysTabControl32</span></span>|<span data-ttu-id="791cb-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="791cb-182">TabItem</span></span>|  
|<span data-ttu-id="791cb-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="791cb-183">ToolbarWindow32</span></span>|<span data-ttu-id="791cb-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="791cb-184">ToolBar</span></span>|  
|<span data-ttu-id="791cb-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="791cb-185">ToolbarWindow32</span></span>|<span data-ttu-id="791cb-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="791cb-186">MenuItem</span></span>|  
|<span data-ttu-id="791cb-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="791cb-187">ToolbarWindow32</span></span>|<span data-ttu-id="791cb-188">ボタン</span><span class="sxs-lookup"><span data-stu-id="791cb-188">Button</span></span>|  
|<span data-ttu-id="791cb-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="791cb-189">ToolbarWindow32</span></span>|<span data-ttu-id="791cb-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="791cb-190">CheckBox</span></span>|  
|<span data-ttu-id="791cb-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="791cb-191">ToolbarWindow32</span></span>|<span data-ttu-id="791cb-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="791cb-192">RadioButton</span></span>|  
|<span data-ttu-id="791cb-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="791cb-193">ToolbarWindow32</span></span>|<span data-ttu-id="791cb-194">区切り記号</span><span class="sxs-lookup"><span data-stu-id="791cb-194">Separator</span></span>|  
|<span data-ttu-id="791cb-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="791cb-195">tooltips_class32</span></span>|<span data-ttu-id="791cb-196">ヒント</span><span class="sxs-lookup"><span data-stu-id="791cb-196">ToolTip</span></span>|  
|<span data-ttu-id="791cb-197">#32774</span><span class="sxs-lookup"><span data-stu-id="791cb-197">#32774</span></span>|<span data-ttu-id="791cb-198">ヒント</span><span class="sxs-lookup"><span data-stu-id="791cb-198">ToolTip</span></span>|  
|<span data-ttu-id="791cb-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="791cb-199">ReBarWindow32</span></span>|<span data-ttu-id="791cb-200">ツール バー</span><span class="sxs-lookup"><span data-stu-id="791cb-200">Toolbar</span></span>|  
|<span data-ttu-id="791cb-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="791cb-201">SysTreeView32</span></span>|<span data-ttu-id="791cb-202">ツリー</span><span class="sxs-lookup"><span data-stu-id="791cb-202">Tree</span></span>|  
|<span data-ttu-id="791cb-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="791cb-203">SysTreeView32</span></span>|<span data-ttu-id="791cb-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="791cb-204">TreeItem</span></span>|  
  
 <span data-ttu-id="791cb-205">**注** RichEdit コントロールは、 [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] に付属するバージョン (RichEd20.dll バージョン 3.1 以降、および MsftEdit.dll バージョン 4.1 以降) に対してのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="791cb-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="791cb-206">次のコントロールはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="791cb-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="791cb-207">クラス名</span><span class="sxs-lookup"><span data-stu-id="791cb-207">Class name</span></span>|<span data-ttu-id="791cb-208">コントロール型</span><span class="sxs-lookup"><span data-stu-id="791cb-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="791cb-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="791cb-209">SysAnimate32</span></span>|<span data-ttu-id="791cb-210">イメージ</span><span class="sxs-lookup"><span data-stu-id="791cb-210">Image</span></span>|  
|<span data-ttu-id="791cb-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="791cb-211">SysPager</span></span>|<span data-ttu-id="791cb-212">Spinner</span><span class="sxs-lookup"><span data-stu-id="791cb-212">Spinner</span></span>|  
|<span data-ttu-id="791cb-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="791cb-213">SysDateTimePick32</span></span>|<span data-ttu-id="791cb-214">カスタム</span><span class="sxs-lookup"><span data-stu-id="791cb-214">Custom</span></span>|  
|<span data-ttu-id="791cb-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="791cb-215">SysMonthCal32</span></span>|<span data-ttu-id="791cb-216">予定表</span><span class="sxs-lookup"><span data-stu-id="791cb-216">Calendar</span></span>|  
|<span data-ttu-id="791cb-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="791cb-217">MS_WINNOTE</span></span>|<span data-ttu-id="791cb-218">ヒント</span><span class="sxs-lookup"><span data-stu-id="791cb-218">Tooltip</span></span>|  
|<span data-ttu-id="791cb-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="791cb-219">VBBubble</span></span>|<span data-ttu-id="791cb-220">ヒント</span><span class="sxs-lookup"><span data-stu-id="791cb-220">Tooltip</span></span>|  
|<span data-ttu-id="791cb-221">ScrollBar (スタンドアロン コントロールとして使用される場合)</span><span class="sxs-lookup"><span data-stu-id="791cb-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="791cb-222">スライダー</span><span class="sxs-lookup"><span data-stu-id="791cb-222">Slider</span></span>|  
|<span data-ttu-id="791cb-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="791cb-223">SuperGrid</span></span>|<span data-ttu-id="791cb-224">カスタム</span><span class="sxs-lookup"><span data-stu-id="791cb-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="791cb-225">Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="791cb-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="791cb-226">Windows フォーム コントロールに公開される[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]UIAutomationClientsideProviders.dll のクライアント側プロバイダーによってです。</span><span class="sxs-lookup"><span data-stu-id="791cb-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="791cb-227">このアセンブリは、UI オートメーション クライアント アプリケーションで使用するために、自動的に登録されます。</span><span class="sxs-lookup"><span data-stu-id="791cb-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="791cb-228">通常、Windows フォーム コントロールのマネージ ラッパー[!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]コモン コントロールでサポートされる[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="791cb-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="791cb-229">次のコントロールがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="791cb-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="791cb-230">クラス名</span><span class="sxs-lookup"><span data-stu-id="791cb-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="791cb-231">ボタン</span><span class="sxs-lookup"><span data-stu-id="791cb-231">Button</span></span>|  
|<span data-ttu-id="791cb-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="791cb-232">CheckBox</span></span>|  
|<span data-ttu-id="791cb-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="791cb-233">CheckedListBox</span></span>|  
|<span data-ttu-id="791cb-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="791cb-234">ColorDialog</span></span>|  
|<span data-ttu-id="791cb-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="791cb-235">ComboBox</span></span>|  
|<span data-ttu-id="791cb-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="791cb-236">FolderBrowser</span></span>|  
|<span data-ttu-id="791cb-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="791cb-237">FontDialog</span></span>|  
|<span data-ttu-id="791cb-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="791cb-238">GroupBox</span></span>|  
|<span data-ttu-id="791cb-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="791cb-239">HscrollBar</span></span>|  
|<span data-ttu-id="791cb-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="791cb-240">ImageList</span></span>|  
|<span data-ttu-id="791cb-241">group1</span><span class="sxs-lookup"><span data-stu-id="791cb-241">Label</span></span>|  
|<span data-ttu-id="791cb-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="791cb-242">ListBox</span></span>|  
|<span data-ttu-id="791cb-243">ListView</span><span class="sxs-lookup"><span data-stu-id="791cb-243">ListView</span></span>|  
|<span data-ttu-id="791cb-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="791cb-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="791cb-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="791cb-245">MonthCalendar</span></span>|  
|<span data-ttu-id="791cb-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="791cb-246">NotifyIcon</span></span>|  
|<span data-ttu-id="791cb-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="791cb-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="791cb-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="791cb-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="791cb-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="791cb-249">PrintDialog</span></span>|  
|<span data-ttu-id="791cb-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="791cb-250">ProgressBar</span></span>|  
|<span data-ttu-id="791cb-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="791cb-251">RadioButton</span></span>|  
|<span data-ttu-id="791cb-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="791cb-252">RichTextBox</span></span>|  
|<span data-ttu-id="791cb-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="791cb-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="791cb-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="791cb-254">ScrollableControl</span></span>|  
|<span data-ttu-id="791cb-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="791cb-255">SoundPlayer</span></span>|  
|<span data-ttu-id="791cb-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="791cb-256">StatusBar</span></span>|  
|<span data-ttu-id="791cb-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="791cb-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="791cb-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="791cb-258">TextBox</span></span>|  
|<span data-ttu-id="791cb-259">タイマー</span><span class="sxs-lookup"><span data-stu-id="791cb-259">Timer</span></span>|  
|<span data-ttu-id="791cb-260">ToolBar</span><span class="sxs-lookup"><span data-stu-id="791cb-260">Toolbar</span></span>|  
|<span data-ttu-id="791cb-261">ヒント</span><span class="sxs-lookup"><span data-stu-id="791cb-261">ToolTip</span></span>|  
|<span data-ttu-id="791cb-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="791cb-262">TrackBar</span></span>|  
|<span data-ttu-id="791cb-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="791cb-263">TreeView</span></span>|  
|<span data-ttu-id="791cb-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="791cb-264">VscrollBar</span></span>|  
|<span data-ttu-id="791cb-265">Web ブラウザー</span><span class="sxs-lookup"><span data-stu-id="791cb-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="791cb-266">次に示すコントロールは、 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] のサポートによってのみ、 [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)]に公開されています。</span><span class="sxs-lookup"><span data-stu-id="791cb-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="791cb-267">一部の機能が使用できないことがあります。</span><span class="sxs-lookup"><span data-stu-id="791cb-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="791cb-268">コントロール名</span><span class="sxs-lookup"><span data-stu-id="791cb-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="791cb-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="791cb-269">BindingSource</span></span>|  
|<span data-ttu-id="791cb-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="791cb-270">DataGrid</span></span>|  
|<span data-ttu-id="791cb-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="791cb-271">DataGridView</span></span>|  
|<span data-ttu-id="791cb-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="791cb-272">DataNavigator</span></span>|  
|<span data-ttu-id="791cb-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="791cb-273">DomainUpDown</span></span>|  
|<span data-ttu-id="791cb-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="791cb-274">ErrorProvider</span></span>|  
|<span data-ttu-id="791cb-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="791cb-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="791cb-276">フォーム</span><span class="sxs-lookup"><span data-stu-id="791cb-276">Form</span></span>|  
|<span data-ttu-id="791cb-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="791cb-277">LinkLabel</span></span>|  
|<span data-ttu-id="791cb-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="791cb-278">HelpProvider</span></span>|  
|<span data-ttu-id="791cb-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="791cb-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="791cb-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="791cb-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="791cb-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="791cb-281">NumericUpDown</span></span>|  
|<span data-ttu-id="791cb-282">パネル</span><span class="sxs-lookup"><span data-stu-id="791cb-282">Panel</span></span>|  
|<span data-ttu-id="791cb-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="791cb-283">PictureBox</span></span>|  
|<span data-ttu-id="791cb-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="791cb-284">PrintDocument</span></span>|  
|<span data-ttu-id="791cb-285">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="791cb-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="791cb-286">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="791cb-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="791cb-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="791cb-287">PropertyGrid</span></span>|  
|<span data-ttu-id="791cb-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="791cb-288">UserControl</span></span>|  
|<span data-ttu-id="791cb-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="791cb-289">ToolStrip</span></span>|  
|<span data-ttu-id="791cb-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="791cb-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="791cb-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="791cb-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="791cb-292">スプリッター</span><span class="sxs-lookup"><span data-stu-id="791cb-292">Splitter</span></span>|  
|<span data-ttu-id="791cb-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="791cb-293">RaftingContainer</span></span>|  
|<span data-ttu-id="791cb-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="791cb-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="791cb-295">関連項目</span><span class="sxs-lookup"><span data-stu-id="791cb-295">See Also</span></span>  
 [<span data-ttu-id="791cb-296">UI オートメーション コントロール型</span><span class="sxs-lookup"><span data-stu-id="791cb-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
