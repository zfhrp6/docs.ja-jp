---
title: UI オートメーション コントロール型の概要
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: c8ca0934e724c4035fb24b9cb246b0b2f41eea3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399731"
---
# <a name="ui-automation-control-types-overview"></a><span data-ttu-id="74bb4-102">UI オートメーション コントロール型の概要</span><span class="sxs-lookup"><span data-stu-id="74bb4-102">UI Automation Control Types Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="74bb4-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="74bb4-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="74bb4-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74bb4-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="74bb4-105"> コントロール型は、コンボ ボックスやボタンなど、特定の要素が表すコントロールの種類を示すのに使用できる既知の識別子です。</span><span class="sxs-lookup"><span data-stu-id="74bb4-105"> control types are well-known identifiers that can be used to indicate what kind of control a particular element represents, such as a combo box or a button.</span></span>  
  
 <span data-ttu-id="74bb4-106">既知の識別子を使用すると、支援テクノロジ デバイスで、 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] で使用できるコントロール型およびコントロールとの対話方法を簡単に確認できるようになります。</span><span class="sxs-lookup"><span data-stu-id="74bb4-106">Having a well-known identifier makes it easier for assistive technology devices to determine what types of controls are available in the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] and how to interact with the controls.</span></span>  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a><span data-ttu-id="74bb4-107">UI オートメーション コントロール型の要件</span><span class="sxs-lookup"><span data-stu-id="74bb4-107">UI Automation Control Type Requisites</span></span>  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="74bb4-108"> コントロール型は、プロバイダーが満たす必要のある一連の条件を提供します。</span><span class="sxs-lookup"><span data-stu-id="74bb4-108"> control types provide a set of conditions that providers must meet.</span></span> <span data-ttu-id="74bb4-109">これらの条件が満たされると、コントロールは特定のコントロール型名を使用できます。</span><span class="sxs-lookup"><span data-stu-id="74bb4-109">When these conditions are met, the control can use the specific control type name.</span></span> <span data-ttu-id="74bb4-110">コントロール型にはそれぞれ、次のような条件があります。</span><span class="sxs-lookup"><span data-stu-id="74bb4-110">Each control type has conditions for the following:</span></span>  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="74bb4-111"> コントロール パターン - サポートする必要があるコントロール パター、省略可能なコントロール パターン、およびコントロールでサポートする必要がないコントロール パターン。</span><span class="sxs-lookup"><span data-stu-id="74bb4-111"> control patterns—which control patterns must be supported, which control patterns are optional, and which control patterns must not be supported by the control.</span></span>  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="74bb4-112"> プロパティ値 - サポートされるプロパティ値。</span><span class="sxs-lookup"><span data-stu-id="74bb4-112"> property values—which property values are supported.</span></span>  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="74bb4-113"> ツリー構造 - コントロールに必要な [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー構造。</span><span class="sxs-lookup"><span data-stu-id="74bb4-113"> tree structure—the required [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure for the control.</span></span>  
  
 <span data-ttu-id="74bb4-114">コントロールが特定のコントロール型の条件を満たす場合、 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> プロパティの値がそのコントロール型を示します。</span><span class="sxs-lookup"><span data-stu-id="74bb4-114">When a control meets the conditions for a particular control type, the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> property value will indicate that control type.</span></span>  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a><span data-ttu-id="74bb4-115">現在の UI オートメーション コントロール型</span><span class="sxs-lookup"><span data-stu-id="74bb4-115">Current UI Automation Control Types</span></span>  
 <span data-ttu-id="74bb4-116">現在の [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] コントロール型の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="74bb4-116">The following list contains the current set of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] control types:</span></span>  
  
-   [<span data-ttu-id="74bb4-117">UI オートメーションによる Button コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-117">UI Automation Support for the Button Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-button-control-type.md)  
  
-   [<span data-ttu-id="74bb4-118">UI オートメーションによる Calendar コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-118">UI Automation Support for the Calendar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-calendar-control-type.md)  
  
-   [<span data-ttu-id="74bb4-119">UI オートメーションによる CheckBox コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-119">UI Automation Support for the CheckBox Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-checkbox-control-type.md)  
  
-   [<span data-ttu-id="74bb4-120">UI オートメーションによる ComboBox コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-120">UI Automation Support for the ComboBox Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-combobox-control-type.md)  
  
-   [<span data-ttu-id="74bb4-121">UI オートメーションによる DataGrid コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-121">UI Automation Support for the DataGrid Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-datagrid-control-type.md)  
  
-   [<span data-ttu-id="74bb4-122">UI オートメーションによる DataItem コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-122">UI Automation Support for the DataItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)  
  
-   [<span data-ttu-id="74bb4-123">UI オートメーションによる Document コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-123">UI Automation Support for the Document Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-document-control-type.md)  
  
-   [<span data-ttu-id="74bb4-124">UI オートメーションによる Edit コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-124">UI Automation Support for the Edit Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-edit-control-type.md)  
  
-   [<span data-ttu-id="74bb4-125">UI オートメーションによる Group コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-125">UI Automation Support for the Group Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-group-control-type.md)  
  
-   [<span data-ttu-id="74bb4-126">UI オートメーションによる Header コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-126">UI Automation Support for the Header Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-header-control-type.md)  
  
-   [<span data-ttu-id="74bb4-127">UI オートメーションによる HeaderItem コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-127">UI Automation Support for the HeaderItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-headeritem-control-type.md)  
  
-   [<span data-ttu-id="74bb4-128">UI オートメーションによる Hyperlink コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-128">UI Automation Support for the Hyperlink Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-hyperlink-control-type.md)  
  
-   [<span data-ttu-id="74bb4-129">UI オートメーションによる Image コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-129">UI Automation Support for the Image Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-image-control-type.md)  
  
-   [<span data-ttu-id="74bb4-130">UI オートメーションによる List コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-130">UI Automation Support for the List Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-list-control-type.md)  
  
-   [<span data-ttu-id="74bb4-131">UI オートメーションによる ListItem コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-131">UI Automation Support for the ListItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)  
  
-   [<span data-ttu-id="74bb4-132">UI オートメーションによる Menu コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-132">UI Automation Support for the Menu Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menu-control-type.md)  
  
-   [<span data-ttu-id="74bb4-133">UI オートメーションによる MenuBar コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-133">UI Automation Support for the MenuBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md)  
  
-   [<span data-ttu-id="74bb4-134">UI オートメーションによる MenuItem コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-134">UI Automation Support for the MenuItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menuitem-control-type.md)  
  
-   [<span data-ttu-id="74bb4-135">UI オートメーションによる Pane コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-135">UI Automation Support for the Pane Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-pane-control-type.md)  
  
-   [<span data-ttu-id="74bb4-136">UI オートメーションによる ProgressBar コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-136">UI Automation Support for the ProgressBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-progressbar-control-type.md)  
  
-   [<span data-ttu-id="74bb4-137">UI オートメーションによる RadioButton コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-137">UI Automation Support for the RadioButton Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-radiobutton-control-type.md)  
  
-   [<span data-ttu-id="74bb4-138">UI オートメーションによる ScrollBar コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-138">UI Automation Support for the ScrollBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-scrollbar-control-type.md)  
  
-   [<span data-ttu-id="74bb4-139">UI オートメーションによる Separator コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-139">UI Automation Support for the Separator Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-separator-control-type.md)  
  
-   [<span data-ttu-id="74bb4-140">UI オートメーションによる Slider コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-140">UI Automation Support for the Slider Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-slider-control-type.md)  
  
-   [<span data-ttu-id="74bb4-141">UI オートメーションによる Spinner コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-141">UI Automation Support for the Spinner Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)  
  
-   [<span data-ttu-id="74bb4-142">UI オートメーションによる SplitButton コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-142">UI Automation Support for the SplitButton Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-splitbutton-control-type.md)  
  
-   [<span data-ttu-id="74bb4-143">UI オートメーションによる StatusBar コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-143">UI Automation Support for the StatusBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-statusbar-control-type.md)  
  
-   [<span data-ttu-id="74bb4-144">UI オートメーションによる Tab コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-144">UI Automation Support for the Tab Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tab-control-type.md)  
  
-   [<span data-ttu-id="74bb4-145">UI オートメーションでの TabItem コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-145">UI Automation Support for the TabItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tabitem-control-type.md)  
  
-   [<span data-ttu-id="74bb4-146">UI オートメーションによる Table コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-146">UI Automation Support for the Table Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-table-control-type.md)  
  
-   [<span data-ttu-id="74bb4-147">UI オートメーションによる Text コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-147">UI Automation Support for the Text Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-text-control-type.md)  
  
-   [<span data-ttu-id="74bb4-148">UI オートメーションによる Thumb コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-148">UI Automation Support for the Thumb Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-thumb-control-type.md)  
  
-   [<span data-ttu-id="74bb4-149">UI オートメーションによる TitleBar コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-149">UI Automation Support for the TitleBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-titlebar-control-type.md)  
  
-   [<span data-ttu-id="74bb4-150">UI オートメーションによる ToolBar コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-150">UI Automation Support for the ToolBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-toolbar-control-type.md)  
  
-   [<span data-ttu-id="74bb4-151">UI オートメーションによる ToolTip コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-151">UI Automation Support for the ToolTip Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tooltip-control-type.md)  
  
-   [<span data-ttu-id="74bb4-152">UI オートメーションによる Tree コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-152">UI Automation Support for the Tree Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tree-control-type.md)  
  
-   [<span data-ttu-id="74bb4-153">UI オートメーションによる TreeItem コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-153">UI Automation Support for the TreeItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)  
  
-   [<span data-ttu-id="74bb4-154">UI オートメーションによる Window コントロール型のサポート</span><span class="sxs-lookup"><span data-stu-id="74bb4-154">UI Automation Support for the Window Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a><span data-ttu-id="74bb4-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="74bb4-155">See Also</span></span>  
 <xref:System.Windows.Automation.ControlType>
