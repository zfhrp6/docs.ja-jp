---
title: .NET Framework のアクセシビリティの新機能
ms.custom: updateeachrelease
ms.date: 04/10/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fe7e15e482028b9988d7e560b98be19b6c07427
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509217"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="1d692-102">.NET Framework のアクセシビリティの新機能</span><span class="sxs-lookup"><span data-stu-id="1d692-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="1d692-103">.NET Framework では、ユーザーのためにアプリケーションのアクセシビリティ向上を目指しています。</span><span class="sxs-lookup"><span data-stu-id="1d692-103">The .NET Framework aims at making applications more accessible for your users.</span></span> <span data-ttu-id="1d692-104">ユーザー補助機能により、支援機能の利用者にとってアプリケーションがさらに使いやすくなります。</span><span class="sxs-lookup"><span data-stu-id="1d692-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="1d692-105">.NET Framework 4.7.1 以降、.NET Framework にはさまざまなアクセシビリティ拡張機能が含まれるようになりました。それを利用することで開発者はアクセシビリティを備えたアプリケーションを開発できます。</span><span class="sxs-lookup"><span data-stu-id="1d692-105">Starting with the .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span> 

## <a name="accessibility-switches"></a><span data-ttu-id="1d692-106">アクセシビリティのスイッチ</span><span class="sxs-lookup"><span data-stu-id="1d692-106">Accessibility switches</span></span>

<span data-ttu-id="1d692-107">アプリのターゲットが .NET Framework 4.7 である場合、またはそれより前のバージョンがターゲットであっても実行環境が .NET Framework 4.7.1 以降である場合は、ユーザー補助機能を使用するようにアプリを構成できます。</span><span class="sxs-lookup"><span data-stu-id="1d692-107">You can configure your app to opt into accessibility features if it targets the .NET Framework 4.7 or an earlier version but is running on the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="1d692-108">また、アプリのターゲットが 4.7.1 .NET Framework 以降である場合は、従来の機能を使用するように (そして、ユーザー補助機能を利用しないように) アプリを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="1d692-108">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="1d692-109">ユーザー補助機能が含まれる .NET Framework の各バージョンには、バージョン固有のアクセシビリティ スイッチがあります。これを、アプリケーションの構成ファイルの [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) セクションの [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 要素に追加します。</span><span class="sxs-lookup"><span data-stu-id="1d692-109">Each version of the .NET Framework that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> <span data-ttu-id="1d692-110">サポートされているスイッチは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1d692-110">The following are the supported switches:</span></span>

|<span data-ttu-id="1d692-111">Version</span><span class="sxs-lookup"><span data-stu-id="1d692-111">Version</span></span>|<span data-ttu-id="1d692-112">切り替え</span><span class="sxs-lookup"><span data-stu-id="1d692-112">Switch</span></span>|
|---|---|
|<span data-ttu-id="1d692-113">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="1d692-113">.NET Framework 4.7.1</span></span>|<span data-ttu-id="1d692-114">"Switch.UseLegacyAccessibilityFeatures"</span><span class="sxs-lookup"><span data-stu-id="1d692-114">"Switch.UseLegacyAccessibilityFeatures"</span></span>|
|<span data-ttu-id="1d692-115">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="1d692-115">.NET Framework 4.7.2</span></span>|<span data-ttu-id="1d692-116">"Switch.UseLegacyAccessibilityFeatures.2"</span><span class="sxs-lookup"><span data-stu-id="1d692-116">"Switch.UseLegacyAccessibilityFeatures.2"</span></span>|

### <a name="taking-advantage-of-accessibility-enhancements"></a><span data-ttu-id="1d692-117">アクセシビリティ拡張機能の利用</span><span class="sxs-lookup"><span data-stu-id="1d692-117">Taking advantage of accessibility enhancements</span></span>

<span data-ttu-id="1d692-118">.NET Framework 4.7.1 以降を対象とするアプリケーションでは、この新しいユーザー補助機能が既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="1d692-118">The new accessibility features are enabled by default for applications that target the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="1d692-119">また、それより前のバージョンの .NET Framework がターゲットであっても、実行環境が .NET Framework 4.7.1 以降であるアプリケーションの場合は、アプリケーションの構成ファイルの [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) セクションの [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 要素にスイッチを追加し、値を `false` に設定することで、古いアクセシビリティ動作を利用しないことを (そして、それにより向上したアクセシビリティ拡張機能を利用することを) 選択できます。</span><span class="sxs-lookup"><span data-stu-id="1d692-119">In addition, applications that target an earlier version of the .NET Framework but are running on the .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span></span> <span data-ttu-id="1d692-120">.NET Framework 4.7.1 で導入されたアクセシビリティの機能強化を有効にする方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1d692-120">The following shows how to opt in to accessibility enhancements introduced in the .NET Framework 4.7.1:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="1d692-121">新しいバージョンの .NET Framework のユーザー補助機能を選択する場合は、古いバージョンの .NET Framework の機能も明示的に選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d692-121">If you choose to opt in to accessibility features in a later version of the .NET Framework, you must also explicitly opt in to the features from earlier versions of the .NET Framework.</span></span> <span data-ttu-id="1d692-122">.NET Framework 4.7.1 と 4.7.2 両方のアクセシビリティ強化機能を利用するようにアプリを構成するには、次の [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 要素が必要です。</span><span class="sxs-lookup"><span data-stu-id="1d692-122">Configuring your app to take advantage of accessibility improvements in both the .NET Framework 4.7.1 and 4.7.2 requires the following [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a><span data-ttu-id="1d692-123">従来の動作に戻す</span><span class="sxs-lookup"><span data-stu-id="1d692-123">Restoring legacy behavior</span></span>

<span data-ttu-id="1d692-124">アプリケーションがバージョン 4.7.1 以降の .NET Framework をターゲットにしている場合、アプリケーションの構成ファイルの [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) セクションの [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 要素にスイッチを追加し、値を `true` に設定することで、アクセシビリティ機能を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="1d692-124">Applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span></span> <span data-ttu-id="1d692-125">たとえば、次の構成は、.NET Framework 4.7.2 で導入されたユーザー補助機能を無効にします。</span><span class="sxs-lookup"><span data-stu-id="1d692-125">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span></span>  

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-472"></a><span data-ttu-id="1d692-126">.NET Framework 4.7.2 のアクセシビリティの新機能</span><span class="sxs-lookup"><span data-stu-id="1d692-126">What's new in accessibility in the .NET Framework 4.7.2</span></span>

<span data-ttu-id="1d692-127">.NET Framework 4.7.2 には、次の領域の新しいアクセシビリティ機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="1d692-127">The .NET Framework 4.7.2 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="1d692-128">Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="1d692-128">Windows Forms</span></span>](#winforms472)

- [<span data-ttu-id="1d692-129">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="1d692-129">Windows Presentation Foundation (WPF)</span></span>](#wpf472)

<a name="winforms472"></a>
### <a name="windows-forms"></a><span data-ttu-id="1d692-130">Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="1d692-130">Windows Forms</span></span>

<span data-ttu-id="1d692-131">**ハイ コントラスト テーマでの OS で定義された色**</span><span class="sxs-lookup"><span data-stu-id="1d692-131">**OS-defined colors in High Contrast themes**</span></span>

<span data-ttu-id="1d692-132">.NET Framework 4.7.2 以降、Windows フォームは、オペレーティング システムで定義されている色をハイ コントラスト テーマで使用します。</span><span class="sxs-lookup"><span data-stu-id="1d692-132">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span></span> <span data-ttu-id="1d692-133">これは、次のコントロールに影響します。</span><span class="sxs-lookup"><span data-stu-id="1d692-133">This affects the following controls:</span></span>

- <span data-ttu-id="1d692-134"><xref:System.Windows.Forms.ToolStripDropDownButton> コントロールのドロップダウン矢印。</span><span class="sxs-lookup"><span data-stu-id="1d692-134">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span></span>

- <span data-ttu-id="1d692-135"><xref:System.Windows.Forms.ButtonBase.FlatStyle> が <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> または <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType> に設定された、<xref:System.Windows.Forms.Button>、<xref:System.Windows.Forms.RadioButton>、および <xref:System.Windows.Forms.CheckBox> コントロール。</span><span class="sxs-lookup"><span data-stu-id="1d692-135">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1d692-136">以前は、選択されたテキストと背景の色のコントラストが同じで、見分けるのが困難でした。</span><span class="sxs-lookup"><span data-stu-id="1d692-136">Previously, selected text and background colors were not contrasting and were hard to read.</span></span>

- <span data-ttu-id="1d692-137"><xref:System.Windows.Forms.Control.Enabled> プロパティが `false` に設定されている <xref:System.Windows.Forms.GroupBox> に含まれるコントロール。</span><span class="sxs-lookup"><span data-stu-id="1d692-137">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>
 
- <span data-ttu-id="1d692-138"><xref:System.Windows.Forms.ToolStripButton>、<xref:System.Windows.Forms.ToolStripComboBox>、<xref:System.Windows.Forms.ToolStripDropDownButton> コントロール。これらは、ハイ コントラスト モードでの明度コントラストの比率が高くなりました。</span><span class="sxs-lookup"><span data-stu-id="1d692-138">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span></span>

- <span data-ttu-id="1d692-139"><xref:System.Windows.Forms.DataGridViewLinkCell> の <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> プロパティ。</span><span class="sxs-lookup"><span data-stu-id="1d692-139">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span></span>

<span data-ttu-id="1d692-140">**ナレーターの機能強化**</span><span class="sxs-lookup"><span data-stu-id="1d692-140">**Narrator improvements**</span></span>

<span data-ttu-id="1d692-141">.NET Framework 4.7.2 以降では、ナレーターのサポートが次のように強化されました。</span><span class="sxs-lookup"><span data-stu-id="1d692-141">Starting with the .NET Framework 4.7.2, Narrator support is enhanced as follows:</span></span>

- <span data-ttu-id="1d692-142"><xref:System.Windows.Forms.ToolStripMenuItem> のテキストを読み上げるときに、<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> プロパティの値を読み上げます。</span><span class="sxs-lookup"><span data-stu-id="1d692-142">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span> 

- <span data-ttu-id="1d692-143"><xref:System.Windows.Forms.ToolStripMenuItem> の <xref:System.Windows.Forms.Control.Enabled> プロパティが `false` に設定されている場合、それを示します。</span><span class="sxs-lookup"><span data-stu-id="1d692-143">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="1d692-144"><xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> プロパティが `true` に設定されているとき、チェック ボックスの状態に関するフィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="1d692-144">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>

- <span data-ttu-id="1d692-145">ナレーター スキャン モードのフォーカス順序が、ClickOnce ダウンロード ダイアログ ウィンドウでのコントロールの視覚的な順序と一致します。</span><span class="sxs-lookup"><span data-stu-id="1d692-145">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="1d692-146">**DataGridView の機能強化**</span><span class="sxs-lookup"><span data-stu-id="1d692-146">**DataGridView improvements**</span></span>

<span data-ttu-id="1d692-147">.NET Framework 4.7.2 以降、<xref:System.Windows.Forms.DataGridView> コントロールには次のアクセシビリティの機能強化が導入されました。</span><span class="sxs-lookup"><span data-stu-id="1d692-147">Starting with the .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span></span>

- <span data-ttu-id="1d692-148">キーボードを使って行を並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="1d692-148">Rows can be sorted using the keyboard.</span></span> <span data-ttu-id="1d692-149">ユーザーは、F3 キーを使って現在の列で並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="1d692-149">A user can use the F3 key in order to sort by the current column.</span></span>

- <span data-ttu-id="1d692-150"><xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> が <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> に設定されていると、ユーザーが現在の行のセルを Tab で移動するとき、列ヘッダーの色が変わって現在の列を示します。</span><span class="sxs-lookup"><span data-stu-id="1d692-150">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span></span>

- <span data-ttu-id="1d692-151"><xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> の <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> プロパティは、正しい親コントロールを返します。</span><span class="sxs-lookup"><span data-stu-id="1d692-151">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span></span>

<span data-ttu-id="1d692-152">**視覚的な手掛かりの向上**</span><span class="sxs-lookup"><span data-stu-id="1d692-152">**Improved visual cues**</span></span>

- <span data-ttu-id="1d692-153"><xref:System.Windows.Forms.ButtonBase.Text> プロパティが空の <xref:System.Windows.Forms.RadioButton> および <xref:System.Windows.Forms.CheckBox> コントロールは、フォーカスを受け取るとフォーカス インジケーターを表示します。</span><span class="sxs-lookup"><span data-stu-id="1d692-153">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span></span>

<span data-ttu-id="1d692-154">**強化されたプロパティ グリッドのサポート**</span><span class="sxs-lookup"><span data-stu-id="1d692-154">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="1d692-155"><xref:System.Windows.Forms.PropertyGrid> コントロールの子要素は、PropertyGrid 要素が有効になっている場合にのみ、<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> プロパティに対して `true` を返すようになりました。</span><span class="sxs-lookup"><span data-stu-id="1d692-155">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>

- <span data-ttu-id="1d692-156"><xref:System.Windows.Forms.PropertyGrid> コントロールの子要素は、PropertyGrid 要素をユーザーが変更できる場合にのみ、<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> プロパティに対して `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="1d692-156">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>

<span data-ttu-id="1d692-157">**キーボード ナビゲーションの向上**</span><span class="sxs-lookup"><span data-stu-id="1d692-157">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="1d692-158"><xref:System.Windows.Forms.ToolStripButton> コントロールは、<xref:System.Windows.Forms.ToolStripPanel.TabStop> プロパティが `true` に設定された <xref:System.Windows.Forms.ToolStripPanel> 内に含まれているときにフォーカスできます</span><span class="sxs-lookup"><span data-stu-id="1d692-158">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span></span>

<a name="wpf472"></a>
### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="1d692-159">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="1d692-159">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="1d692-160">**CheckBox および RadioButton コントロールに対する変更**</span><span class="sxs-lookup"><span data-stu-id="1d692-160">**Changes to the CheckBox and RadioButton controls**</span></span>

<span data-ttu-id="1d692-161">.NET Framework 4.7.1 およびそれより前のバージョンでは、WPF の <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> および <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> コントロールのフォーカス ビジュアルに整合性がなく、クラシック テーマとハイ コントラスト テーマでは正しくありません。</span><span class="sxs-lookup"><span data-stu-id="1d692-161">In the .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="1d692-162">これらの問題は、コントロールに内容が何も設定されていない場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="1d692-162">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="1d692-163">これにより、テーマ間の遷移が混乱し、フォーカス ビジュアルが見にくくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="1d692-163">This can make the transition between themes confusing and the focus visual hard to see.</span></span>

<span data-ttu-id="1d692-164">.NET Framework 4.7.2 では、これらのビジュアルのテーマ間の整合性が向上し、クラシック モードとハイ コントラスト テーマでの視認性がよくなっています。</span><span class="sxs-lookup"><span data-stu-id="1d692-164">In the .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

<span data-ttu-id="1d692-165">**WPF アプリケーションでホストされる WinForms コントロール**</span><span class="sxs-lookup"><span data-stu-id="1d692-165">**WinForms controls hosted in a WPF application**</span></span>

<span data-ttu-id="1d692-166">.NET Framework 4.7.1 以前のバージョンの WPF アプリケーションでホストされている WinForms コントロールでは、そのレイヤーの最初または最後のコントロールが WPF <xref:System.Windows.Forms.Integration.ElementHost> コントロールの場合、ユーザーは Tab キーで WinForms レイヤーから外に移動できませんでした。</span><span class="sxs-lookup"><span data-stu-id="1d692-166">For WinForms control hosted in a WPF application in the .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span> <span data-ttu-id="1d692-167">.NET Framework 4.7.2 では、ユーザーは Tab キーで WinForms レイヤーから外に移動できます。</span><span class="sxs-lookup"><span data-stu-id="1d692-167">In the .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span></span>

<span data-ttu-id="1d692-168">ただし、WinForms レイヤーをエスケープしないフォーカスに依存する自動化アプリケーションは、意図したように機能しなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1d692-168">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a><span data-ttu-id="1d692-169">.NET Framework 4.7.1 のアクセシビリティの新機能</span><span class="sxs-lookup"><span data-stu-id="1d692-169">What's new in accessibility in the .NET Framework 4.7.1</span></span>

<span data-ttu-id="1d692-170">.NET Framework 4.7.1 には、次の領域の新しいアクセシビリティ機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="1d692-170">The .NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="1d692-171">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="1d692-171">Windows Presentation Foundation (WPF)</span></span>](#wpf471)

- [<span data-ttu-id="1d692-172">Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="1d692-172">Windows Forms</span></span>](#winforms471)

- [<span data-ttu-id="1d692-173">ASP.NET Web コントロール</span><span class="sxs-lookup"><span data-stu-id="1d692-173">ASP.NET web controls</span></span>](#aspnet471)

- [<span data-ttu-id="1d692-174">.NET SDK Tools</span><span class="sxs-lookup"><span data-stu-id="1d692-174">.NET SDK Tools</span></span>](#tools471)

- [<span data-ttu-id="1d692-175">Windows Workflow Foundation (WF) ワークフロー デザイナー</span><span class="sxs-lookup"><span data-stu-id="1d692-175">Windows Workflow Foundation (WF) Workflow Designer</span></span>](#wf471)

<a name="wpf471"></a>
### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="1d692-176">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="1d692-176">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="1d692-177">**スクリーン リーダーの機能強化**</span><span class="sxs-lookup"><span data-stu-id="1d692-177">**Screen reader improvements**</span></span>

<span data-ttu-id="1d692-178">アクセシビリティ拡張機能を有効にすると、.NET Framework 4.7.1 は次の面でスクリーン リーダーの機能を強化します。</span><span class="sxs-lookup"><span data-stu-id="1d692-178">If accessibility improvements are enabled, the .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="1d692-179">.NET Framework 4.7 以前のバージョンでは、スクリーン リーダーが <xref:System.Windows.Controls.Expander> コントロールをボタンとして読み上げました。</span><span class="sxs-lookup"><span data-stu-id="1d692-179">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="1d692-180">.NET Framework 4.7.1 以降では、展開と折りたたみが可能なグループとして正しく読み上げられます。</span><span class="sxs-lookup"><span data-stu-id="1d692-180">Starting with the .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="1d692-181">.NET Framework 4.7 以前のバージョンの場合、スクリーン リーダーが <xref:System.Windows.Controls.DataGridCell> コントロールを “カスタム” として読み上げました。</span><span class="sxs-lookup"><span data-stu-id="1d692-181">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="1d692-182">.NET Framework 4.7.1 以降では、データ グリッド セル (ローカライズされます) として正しく読み上げられます。</span><span class="sxs-lookup"><span data-stu-id="1d692-182">Starting with the .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>
 
- <span data-ttu-id="1d692-183">.NET Framework 4.7.1 以降、スクリーン リーダーは編集可能な <xref:System.Windows.Controls.ComboBox> の名前を読み上げます。</span><span class="sxs-lookup"><span data-stu-id="1d692-183">Starting with the .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="1d692-184">.NET Framework 4.7 以前のバージョンの場合、<xref:System.Windows.Controls.PasswordBox> コントロールが “ビューに項目がありません” として読み上げられたか、他の誤動作が発生しました。</span><span class="sxs-lookup"><span data-stu-id="1d692-184">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="1d692-185">この問題は .NET Framework 4.7.1 以降で修正されています。</span><span class="sxs-lookup"><span data-stu-id="1d692-185">This issue is fixed starting with the .NET Framework 4.7.1.</span></span>

<span data-ttu-id="1d692-186">**UIAutomation LiveRegion サポート**</span><span class="sxs-lookup"><span data-stu-id="1d692-186">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="1d692-187">ナレーターなどのスクリーン リーダーはアプリケーションの UI コンテンツをユーザーのために読み上げます。通常、フォーカスを合わせた UI コンテンツのテキストが読み上げられます。</span><span class="sxs-lookup"><span data-stu-id="1d692-187">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="1d692-188">ただし、UI 要素が変わり、フォーカスがなくなったとき、ユーザーに通知されず、重要な情報を逃すことがあります。</span><span class="sxs-lookup"><span data-stu-id="1d692-188">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="1d692-189">ライブ領域は、この問題の解決を目指しています。</span><span class="sxs-lookup"><span data-stu-id="1d692-189">Live regions aim at solving this problem.</span></span> <span data-ttu-id="1d692-190">開発者はこれを利用し、UI 要素が大幅に変更されたことをスクリーン リーダーやその他の UIAutomation クライアントに指示できます。</span><span class="sxs-lookup"><span data-stu-id="1d692-190">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="1d692-191">指示後、スクリーン リーダーでは、その変更をユーザーに通知する方法とタイミングが決定されます。</span><span class="sxs-lookup"><span data-stu-id="1d692-191">The screen reader can then decide how and when to inform the user of this change.</span></span> 

<span data-ttu-id="1d692-192">ライブ領域をサポートするために、次の API が WPF に追加されました。</span><span class="sxs-lookup"><span data-stu-id="1d692-192">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="1d692-193"><xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> フィールドと <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> フィールド。**LiveSetting** プロパティと **LiveRegionChanged** イベントを識別します。</span><span class="sxs-lookup"><span data-stu-id="1d692-193">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="1d692-194">XAML を利用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="1d692-194">They can be set by using XAML.</span></span>

- <span data-ttu-id="1d692-195">**AutomationProperties.LiveSetting** 添付プロパティ。UI の変化がユーザーにとって重要であることをスクリーン リーダーに伝えます。</span><span class="sxs-lookup"><span data-stu-id="1d692-195">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="1d692-196"><xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> プロパティ。**AutomationProperties.LiveSetting** 添付プロパティを識別します。</span><span class="sxs-lookup"><span data-stu-id="1d692-196">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>
 
- <span data-ttu-id="1d692-197"><xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> メソッド。**LiveSetting** 値を提供するようにオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="1d692-197">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="1d692-198"><xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> メソッドと <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> メソッド。**LiveSetting** 値を取得し、設定します。</span><span class="sxs-lookup"><span data-stu-id="1d692-198">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>
 
- <span data-ttu-id="1d692-199"><xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> 列挙。次の指定可能 **LiveSetting** 値を定義します。</span><span class="sxs-lookup"><span data-stu-id="1d692-199">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

   - <span data-ttu-id="1d692-200"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="1d692-200"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1d692-201">ライブ領域の内容が変更された場合でも、要素が通知を送信することはありません。</span><span class="sxs-lookup"><span data-stu-id="1d692-201">The element does not send notifications if the content of the live region has changed.</span></span>   
   - <span data-ttu-id="1d692-202"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="1d692-202"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1d692-203">ライブ領域の内容が変更された場合、要素は非割り込み型の通知を送信します。</span><span class="sxs-lookup"><span data-stu-id="1d692-203">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>   

  - <span data-ttu-id="1d692-204"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="1d692-204"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1d692-205">ライブ領域の内容が変更された場合、要素により割り込み通知が送信されます。</span><span class="sxs-lookup"><span data-stu-id="1d692-205">The element sends interruptive notifications if the content of the live region has changed.</span></span>   

<span data-ttu-id="1d692-206">関心のある要素で **AutomationProperties.LiveSetting** プロパティを作成できます。次の例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1d692-206">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="1d692-207">ライブ領域のデータが変化し、スクリーン リーダーに通知する必要があれば、次のサンプルのように、明示的にイベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="1d692-207">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="1d692-208">**ハイ コントラスト**</span><span class="sxs-lookup"><span data-stu-id="1d692-208">**High contrast**</span></span>

<span data-ttu-id="1d692-209">.NET Framework 4.7.1 以降、さまざまな WPF コントロールでハイ コントラストが強化されました。</span><span class="sxs-lookup"><span data-stu-id="1d692-209">Starting with the .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="1d692-210"><xref:System.Windows.SystemParameters.HighContrast%2A> テーマが設定されているときにこれを確認できます。</span><span class="sxs-lookup"><span data-stu-id="1d692-210">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="1d692-211">次の設定があります。</span><span class="sxs-lookup"><span data-stu-id="1d692-211">These include:</span></span>

- <span data-ttu-id="1d692-212"><xref:System.Windows.Controls.Expander> コントロール</span><span class="sxs-lookup"><span data-stu-id="1d692-212"><xref:System.Windows.Controls.Expander> control</span></span>

    <span data-ttu-id="1d692-213">フォーカスを合わせたとき、<xref:System.Windows.Controls.Expander> コントロールが見やすくなりました。</span><span class="sxs-lookup"><span data-stu-id="1d692-213">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="1d692-214"><xref:System.Windows.Controls.ComboBox>、<xref:System.Windows.Controls.ListBox>、<xref:System.Windows.Controls.RadioButton> コントロールのキーボードも見やすくなりました。</span><span class="sxs-lookup"><span data-stu-id="1d692-214">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="1d692-215">例:</span><span class="sxs-lookup"><span data-stu-id="1d692-215">For example:</span></span>

    <span data-ttu-id="1d692-216">前:</span><span class="sxs-lookup"><span data-stu-id="1d692-216">Before:</span></span> 
    
    ![フォーカスを合わせた Expander コントロール (アクセシビリティ機能改善前)](media/expander-before.png)

    <span data-ttu-id="1d692-218">後:</span><span class="sxs-lookup"><span data-stu-id="1d692-218">After:</span></span> 

    ![フォーカスを合わせた Expander コントロール (アクセシビリティ機能改善後)](media/expander-after.png)

- <span data-ttu-id="1d692-220"><xref:System.Windows.Controls.CheckBox> コントロールと <xref:System.Windows.Controls.RadioButton> コントロール</span><span class="sxs-lookup"><span data-stu-id="1d692-220"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>
 
    <span data-ttu-id="1d692-221"><xref:System.Windows.Controls.CheckBox> コントロールと <xref:System.Windows.Controls.RadioButton> コントロールのテキストは、ハイ コントラスト テーマで選択されているとき、見やすくなりました。</span><span class="sxs-lookup"><span data-stu-id="1d692-221">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="1d692-222">例:</span><span class="sxs-lookup"><span data-stu-id="1d692-222">For example:</span></span>

    <span data-ttu-id="1d692-223">前:</span><span class="sxs-lookup"><span data-stu-id="1d692-223">Before:</span></span> 

    ![フォーカスを合わせたハイ コントラストのラジオ ボタン (アクセシビリティ機能改善前)](media/radio-button-before.png)
    
    <span data-ttu-id="1d692-225">後:</span><span class="sxs-lookup"><span data-stu-id="1d692-225">After:</span></span> 

    ![フォーカスを合わせたハイ コントラストのラジオ ボタン (アクセシビリティ機能改善後)](media/radio-button-after.png)

- <span data-ttu-id="1d692-227"><xref:System.Windows.Controls.ComboBox> コントロール</span><span class="sxs-lookup"><span data-stu-id="1d692-227"><xref:System.Windows.Controls.ComboBox> control</span></span>
 
    <span data-ttu-id="1d692-228">.NET Framework 4.7.1 以降、無効にした <xref:System.Windows.Controls.ComboBox> コントロールの枠線が無効にしたテキストと同じ色になります。</span><span class="sxs-lookup"><span data-stu-id="1d692-228">Starting with the .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="1d692-229">例:</span><span class="sxs-lookup"><span data-stu-id="1d692-229">For example:</span></span>
    
    <span data-ttu-id="1d692-230">前:</span><span class="sxs-lookup"><span data-stu-id="1d692-230">Before:</span></span> 

     ![無効にした ComboBox の枠線とテキスト (アクセシビリティ機能改善前)](media/combo-disabled-before.png)

    <span data-ttu-id="1d692-232">後:</span><span class="sxs-lookup"><span data-stu-id="1d692-232">After:</span></span>   

     ![無効にした ComboBox の枠線とテキスト (アクセシビリティ機能改善後)](media/combo-disabled-after.png)

    <span data-ttu-id="1d692-234">また、無効にしているボタンにフォーカスを合わせたとき、正しいテーマ色が使用されます。</span><span class="sxs-lookup"><span data-stu-id="1d692-234">In addition, disabled and focused buttons use the correct theme color.</span></span>

    <span data-ttu-id="1d692-235">前:</span><span class="sxs-lookup"><span data-stu-id="1d692-235">Before:</span></span>

    ![ボタンのテーマ色 (アクセシビリティ機能改善前)](media/button-themes-before.png) 
    
    <span data-ttu-id="1d692-237">後:</span><span class="sxs-lookup"><span data-stu-id="1d692-237">After:</span></span> 

    ![ボタンのテーマ色 (アクセシビリティ機能改善後)](media/button-themes-after.png) 

    <span data-ttu-id="1d692-239">最後になりますが、.NET Framework 4.7 以前のバージョンでは、<xref:System.Windows.Controls.ComboBox> コントロールのスタイルを `Toolbar.ComboBoxStyleKey` に設定すると、ドロップダウンの矢印が見えなくなりました。</span><span class="sxs-lookup"><span data-stu-id="1d692-239">Finally, in the .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="1d692-240">この問題は .NET Framework 4.7.1 以降で修正されています。</span><span class="sxs-lookup"><span data-stu-id="1d692-240">This issue is fixed starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="1d692-241">例:</span><span class="sxs-lookup"><span data-stu-id="1d692-241">For example:</span></span>

    <span data-ttu-id="1d692-242">前:</span><span class="sxs-lookup"><span data-stu-id="1d692-242">Before:</span></span> 

    ![Toolbar.ComboBoxStyleKey (アクセシビリティ機能改善前)](media/comboboxstylekey-before.png) 
    
    <span data-ttu-id="1d692-244">後:</span><span class="sxs-lookup"><span data-stu-id="1d692-244">After:</span></span> 

    ![Toolbar.ComboBoxStyleKey (アクセシビリティ機能改善後)](media/comboboxstylekey-after.png) 

- <span data-ttu-id="1d692-246"><xref:System.Windows.Controls.DataGrid> コントロール</span><span class="sxs-lookup"><span data-stu-id="1d692-246"><xref:System.Windows.Controls.DataGrid> control</span></span>

    <span data-ttu-id="1d692-247">.NET Framework 4.7.1 以降、<xref:System.Windows.Controls.DataGrid> コントロールの並べ替えインジケーターで正しいテーマ色が使われるようになりました。</span><span class="sxs-lookup"><span data-stu-id="1d692-247">Starting with the .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="1d692-248">例:</span><span class="sxs-lookup"><span data-stu-id="1d692-248">For example:</span></span>

    <span data-ttu-id="1d692-249">前:</span><span class="sxs-lookup"><span data-stu-id="1d692-249">Before:</span></span> 

    ![並べ替えインジケーターの矢印 (アクセシビリティ機能改善前)](media/sort-indicator-before.png) 
    
    <span data-ttu-id="1d692-251">後:</span><span class="sxs-lookup"><span data-stu-id="1d692-251">After:</span></span>   
 
    ![並べ替えインジケーターの矢印 (アクセシビリティ機能改善後)](media/sort-indicator-after.png) 
    
    <span data-ttu-id="1d692-253">また、.NET Framework 4.7 以前のバージョンでは、ハイ コントラスト モードでカーソルを合わせたとき、既定のリンク スタイルが正しくない色に変化しました。</span><span class="sxs-lookup"><span data-stu-id="1d692-253">In addition, in the .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="1d692-254">これは .NET Framework 4.7.1 以降で修正されています。</span><span class="sxs-lookup"><span data-stu-id="1d692-254">This is resolved starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="1d692-255">同様に、.NET Framework 4.7.1 以降、<xref:System.Windows.Controls.DataGrid> チェックボックス列でキーボード フォーカス フィードバックに既定の色が使用されます。</span><span class="sxs-lookup"><span data-stu-id="1d692-255">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with the .NET Framework 4.7.1.</span></span>

    <span data-ttu-id="1d692-256">前:</span><span class="sxs-lookup"><span data-stu-id="1d692-256">Before:</span></span> 

    ![DataGrid の既定のリンク スタイル (アクセシビリティ機能改善前)](media/default-link-style-before.png) 
 
    <span data-ttu-id="1d692-258">後:</span><span class="sxs-lookup"><span data-stu-id="1d692-258">After:</span></span>    
  
    ![DataGrid の既定のリンク スタイル (アクセシビリティ機能改善後)](media/default-link-style-after.png)  

<span data-ttu-id="1d692-260">.NET Framework 4.7.1 のアクセシビリティ機能の改善の詳細については、「[Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf)」 (WPF のアクセシビリティ機能改善) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d692-260">For more information on WPF accessibility improvements in the .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

<a name="winforms471"></a>
## <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="1d692-261">Windows フォームのアクセシビリティ機能改善</span><span class="sxs-lookup"><span data-stu-id="1d692-261">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="1d692-262">.NET Framework 4.7.1 では、Windows フォーム (WinForms) のアクセシビリティが次の領域で変更されました。</span><span class="sxs-lookup"><span data-stu-id="1d692-262">In the .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="1d692-263">**ハイ コントラスト モードの表示が改善されました**</span><span class="sxs-lookup"><span data-stu-id="1d692-263">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="1d692-264">.NET Framework 4.7.1 以降では、オペレーティング システムで利用できるハイ コントラスト モードを選択したとき、さまざまな WinForms コントロールの表示が改善されました。</span><span class="sxs-lookup"><span data-stu-id="1d692-264">Starting with the .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="1d692-265">Windows 10 では、ハイ コントラストのシステム色の一部で値が変わりました。Windows フォームは Windows 10 Win32 フレームワークに基づきます。</span><span class="sxs-lookup"><span data-stu-id="1d692-265">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="1d692-266">最も快適に利用するためには、最新版の Windows で実行し、テスト アプリケーションに app.manifest ファイルを追加して最新の OS 変更を選択し、次の画像のように Windows 10 対応 OS 行のコメントを解除します。</span><span class="sxs-lookup"><span data-stu-id="1d692-266">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
<span data-ttu-id="1d692-267">ハイ コントラストの変更例:</span><span class="sxs-lookup"><span data-stu-id="1d692-267">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="1d692-268"><xref:System.Windows.Forms.MenuStrip> 項目のチェックマークが見やすくなりました。</span><span class="sxs-lookup"><span data-stu-id="1d692-268">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="1d692-269">選択したとき、無効になっている <xref:System.Windows.Forms.MenuStrip> 項目が見やすくなりました。</span><span class="sxs-lookup"><span data-stu-id="1d692-269">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="1d692-270">選択した <xref:System.Windows.Forms.Button> コントロールのテキストが背景色に対して際立ち、見やすくなりました。</span><span class="sxs-lookup"><span data-stu-id="1d692-270">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="1d692-271">無効になっているテキストが読みやすくなりました。</span><span class="sxs-lookup"><span data-stu-id="1d692-271">Disabled text is easier to read.</span></span> <span data-ttu-id="1d692-272">例:</span><span class="sxs-lookup"><span data-stu-id="1d692-272">For example:</span></span>

    <span data-ttu-id="1d692-273">前:</span><span class="sxs-lookup"><span data-stu-id="1d692-273">Before:</span></span>

    ![無効にしたテキスト (アクセシビリティ機能改善前)](media/wf-disabled-before.png) 

    <span data-ttu-id="1d692-275">後:</span><span class="sxs-lookup"><span data-stu-id="1d692-275">After:</span></span>

    ![無効にしたテキスト (アクセシビリティ機能改善後)](media/wf-disabled-after.png) 

- <span data-ttu-id="1d692-277">スレッド例外ダイアログのハイ コントラストが改善されました。</span><span class="sxs-lookup"><span data-stu-id="1d692-277">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="1d692-278">**ナレーター サポートが改善されました**</span><span class="sxs-lookup"><span data-stu-id="1d692-278">**Improved Narrator support**</span></span>

<span data-ttu-id="1d692-279">.NET Framework 4.7.1 の Windows フォームでは、ナレーターのアクセシビリティが次の面で改善されました。</span><span class="sxs-lookup"><span data-stu-id="1d692-279">Windows Forms in the .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="1d692-280"><xref:System.Windows.Forms.MonthCalendar> コントロールに、他の UI 自動化ツールと同様に、ナレーターからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1d692-280">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="1d692-281"><xref:System.Windows.Forms.CheckedListBox> コントロールは、項目のチェック状態が変わったとき、ナレーターに通知します。その結果、リスト アイテムの値を変えたことがユーザーに通知されます。</span><span class="sxs-lookup"><span data-stu-id="1d692-281">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>
 
- <span data-ttu-id="1d692-282"><xref:System.Windows.Forms.DataGridViewCell> コントロールは正しい読み取り専用状態をナレーターに報告します。</span><span class="sxs-lookup"><span data-stu-id="1d692-282">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>
 
- <span data-ttu-id="1d692-283">ナレーターが無効になっている <xref:System.Windows.Forms.ToolStripMenuItem> テキストを読み上げるようになりました。以前は、無効になっているメニュー項目はスキップされました。</span><span class="sxs-lookup"><span data-stu-id="1d692-283">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="1d692-284">**UIAutomation アクセシビリティ パターンのサポートが強化されました**</span><span class="sxs-lookup"><span data-stu-id="1d692-284">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="1d692-285">.NET Framework 4.7.1 以降、アクセシビリティ技術ツールの開発者は、一部の WinForms コントロールについて、API アクセシビリティの共通のパターンとプロパティを活用できます。</span><span class="sxs-lookup"><span data-stu-id="1d692-285">Starting with the .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="1d692-286">アクセシビリティ機能改善の例:</span><span class="sxs-lookup"><span data-stu-id="1d692-286">These accessibility improvements include:</span></span>

- <span data-ttu-id="1d692-287"><xref:System.Windows.Forms.ComboBox> と <xref:System.Windows.Forms.ToolStripSplitButton> が[展開/折りたたみパターン](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)対応になりました。</span><span class="sxs-lookup"><span data-stu-id="1d692-287">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>
 
- <span data-ttu-id="1d692-288"><xref:System.Windows.Forms.DataGridViewCheckBoxCell> が[切り替えパターン](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md)対応になりました。</span><span class="sxs-lookup"><span data-stu-id="1d692-288">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>
 
- <span data-ttu-id="1d692-289"><xref:System.Windows.Forms.ToolStripItem> コントロールが <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> プロパティと[展開/折りたたみパターン](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)対応になりました。</span><span class="sxs-lookup"><span data-stu-id="1d692-289">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="1d692-290"><xref:System.Windows.Forms.NumericUpDown> コントロールと <xref:System.Windows.Forms.DomainUpDown> コントロールが <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> プロパティ対応になりました。</span><span class="sxs-lookup"><span data-stu-id="1d692-290">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="1d692-291">**プロパティ ブラウザーが使いやすくなりました**</span><span class="sxs-lookup"><span data-stu-id="1d692-291">**Improved property browser experience**</span></span>

<span data-ttu-id="1d692-292">.NET Framework 4.7.1 以降、Windows フォームは次の点で改善されました。</span><span class="sxs-lookup"><span data-stu-id="1d692-292">Starting with the .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="1d692-293">さまざまなドロップダウン選択ウィンドウを利用することでキーボード操作が便利になりました。</span><span class="sxs-lookup"><span data-stu-id="1d692-293">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="1d692-294">不要なタブ ストップが減りました。</span><span class="sxs-lookup"><span data-stu-id="1d692-294">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="1d692-295">コントロールの種類の報告機能が改善されました。</span><span class="sxs-lookup"><span data-stu-id="1d692-295">Better reporting of control types.</span></span>
- <span data-ttu-id="1d692-296">ナレーターの動作が改善されました。</span><span class="sxs-lookup"><span data-stu-id="1d692-296">Improved narrator behavior.</span></span>
 
<a name="aspnet471"></a>
## <a name="aspnet-web-controls"></a><span data-ttu-id="1d692-297">ASP.NET Web コントロール</span><span class="sxs-lookup"><span data-stu-id="1d692-297">ASP.NET web controls</span></span>

<span data-ttu-id="1d692-298">.NET Framework 4.7.1 および Visual Studio 2017 15.3 以降では、ASP.NET Web コントロールによる Visual Studio のアクセシビリティ テクノロジの処理方法が向上しています。</span><span class="sxs-lookup"><span data-stu-id="1d692-298">Starting with the .NET Framework 4.7.1 and Visual Studio 2017 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span></span> <span data-ttu-id="1d692-299">主な変更点は以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1d692-299">Changes include the following:</span></span>

- <span data-ttu-id="1d692-300">**[詳細の表示]** ウィザードの **[フィールドの追加]** ダイアログや **ListView** ウィザードの **[ListView の構成]** ダイアログなど、コントロールで不足していた UI アクセシビリティ パターンを実装するための変更。</span><span class="sxs-lookup"><span data-stu-id="1d692-300">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span></span>

- <span data-ttu-id="1d692-301">**データ ページャー フィールド エディター**など、ハイ コントラスト モードでの表示を改善するための変更。</span><span class="sxs-lookup"><span data-stu-id="1d692-301">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span></span>

- <span data-ttu-id="1d692-302">DataPager コントロールの **[ページャーのフィールドを編集]** ウィザードの **[フィールド]** ダイアログ、**[ObjectContext の構成]** ダイアログ、**[データ ソースの構成]** ウィザードの **[データの選択の構成]** ダイアログなど、キーボードの操作性を改善するための変更。</span><span class="sxs-lookup"><span data-stu-id="1d692-302">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span></span>

<a name="tools471"></a>
## <a name="net-sdk-tools"></a><span data-ttu-id="1d692-303">.NET SDK Tools</span><span class="sxs-lookup"><span data-stu-id="1d692-303">.NET SDK Tools</span></span>

<span data-ttu-id="1d692-304">[構成エディター ツール (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) および[サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) が、さまざまなアクセシビリティの問題を修正して改善されています。</span><span class="sxs-lookup"><span data-stu-id="1d692-304">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="1d692-305">その問題のほとんどは、名前の未定義や、特定の UI の自動化パターンが正しく実装されていないといった軽微なものです。</span><span class="sxs-lookup"><span data-stu-id="1d692-305">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="1d692-306">このような問題は、多くのユーザーが認識しないものですが、スクリーン リーダーのような支援技術を使用するお客様はこれらの SDK ツールのアクセシビリティの強化を実感されるでしょう。</span><span class="sxs-lookup"><span data-stu-id="1d692-306">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span> 

<span data-ttu-id="1d692-307">これらの機能強化により、キーボード フォーカスの順序など、以前のいくつかの動作が変更されます。</span><span class="sxs-lookup"><span data-stu-id="1d692-307">These enhancements change some previous behaviors, such as keyboard focus order.</span></span>

<a name="wf471"></a>
## <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="1d692-308">Windows Workflow Foundation (WF) ワークフロー デザイナー</span><span class="sxs-lookup"><span data-stu-id="1d692-308">Windows Workflow Foundation (WF) Workflow Designer</span></span>

<span data-ttu-id="1d692-309">ワークフロー デザイナーでのアクセシビリティに関する変更は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1d692-309">Accessibility changes in the Workflow Designer include the following:</span></span>

- <span data-ttu-id="1d692-310">一部のコントロールで、タブ オーダーが左から右、上から下に変更されます。</span><span class="sxs-lookup"><span data-stu-id="1d692-310">The tab order changes to left to right and top to bottom in some controls:</span></span>

  - <span data-ttu-id="1d692-311"><xref:System.ServiceModel.Activities.InitializeCorrelation> アクティビティの関連付けデータを設定するための関連付けの初期化ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="1d692-311">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span></span>

  - <span data-ttu-id="1d692-312"><xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.SendReply>、および <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティのコンテンツ定義ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="1d692-312">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span></span>

- <span data-ttu-id="1d692-313">キーボードで利用できる機能が増えます:</span><span class="sxs-lookup"><span data-stu-id="1d692-313">More functions are available via the keyboard:</span></span>

  - <span data-ttu-id="1d692-314">アクティビティのプロパティを編集する際、プロパティ グループに初めてフォーカスを設定したときに、プロパティ グループをキーボードで折りたたむことができます。</span><span class="sxs-lookup"><span data-stu-id="1d692-314">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>

  - <span data-ttu-id="1d692-315">警告アイコンにキーボードでアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1d692-315">Warning icons are accessible by keyboard.</span></span>

  - <span data-ttu-id="1d692-316">**[プロパティ]** ウィンドウの **[その他のプロパティ]** ボタンに、キーボードでアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1d692-316">The **More Properties** button in the **Properties** window is accessible by keyboard.</span></span>

  - <span data-ttu-id="1d692-317">キーボードを使って、ワークフロー デザイナーの **[引数]** および **[変数]** ウィンドウのヘッダー項目にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1d692-317">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span></span>

- <span data-ttu-id="1d692-318">次のような場合に、フォーカスのある項目の可視性が向上しました:</span><span class="sxs-lookup"><span data-stu-id="1d692-318">Improved visibility of items with focus, such as when:</span></span>

  - <span data-ttu-id="1d692-319">ワークフロー デザイナーおよびアクティビティ デザイナーで使われているデータ グリッドへの行の追加。</span><span class="sxs-lookup"><span data-stu-id="1d692-319">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>

  - <span data-ttu-id="1d692-320"><xref:System.ServiceModel.Activities.ReceiveReply> および <xref:System.ServiceModel.Activities.SendReply> アクティビティ内のフィールド間の Tab 移動。</span><span class="sxs-lookup"><span data-stu-id="1d692-320">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>

  - <span data-ttu-id="1d692-321">変数または引数の既定値の設定</span><span class="sxs-lookup"><span data-stu-id="1d692-321">Setting default values for variables or arguments</span></span>

- <span data-ttu-id="1d692-322">スクリーン リーダーが正しく認識できるようになりました:</span><span class="sxs-lookup"><span data-stu-id="1d692-322">Screen readers can now correctly recognize:</span></span>

  - <span data-ttu-id="1d692-323">ワークフロー デザイナーで設定されたブレークポイント。</span><span class="sxs-lookup"><span data-stu-id="1d692-323">Breakpoints set in the workflow designer.</span></span>

  - <span data-ttu-id="1d692-324"><xref:System.Activities.Statements.FlowSwitch%601>、<xref:System.Activities.Statements.FlowDecision>、<xref:System.ServiceModel.Activities.CorrelationScope> アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="1d692-324">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
  - <span data-ttu-id="1d692-325"><xref:System.ServiceModel.Activities.Receive> アクティビティの内容。</span><span class="sxs-lookup"><span data-stu-id="1d692-325">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

  - <span data-ttu-id="1d692-326"><xref:System.Activities.Statements.InvokeMethod> アクティビティのターゲットの種類。</span><span class="sxs-lookup"><span data-stu-id="1d692-326">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>

  - <span data-ttu-id="1d692-327"><xref:System.Activities.Statements.TryCatch> アクティビティの [例外] コンボ ボックスと [Finally] セクション。</span><span class="sxs-lookup"><span data-stu-id="1d692-327">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>

  - <span data-ttu-id="1d692-328">メッセージング アクティビティの [メッセージの種類] コンボ ボックス、[関連付け初期化子の追加] ウィンドウのスプリッター、[コンテンツ定義] ウィンドウで、および [CorrelatesOn の定義] ウィンドウ (<xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.SendReply>、および <xref:System.ServiceModel.Activities.ReceiveReply>)。</span><span class="sxs-lookup"><span data-stu-id="1d692-328">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>

  - <span data-ttu-id="1d692-329">ステート マシンの遷移と遷移先。</span><span class="sxs-lookup"><span data-stu-id="1d692-329">State machine transitions and transitions destinations.</span></span>

  - <span data-ttu-id="1d692-330"><xref:System.Activities.Statements.FlowDecision> アクティビティの注釈とコネクタ。</span><span class="sxs-lookup"><span data-stu-id="1d692-330">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>

  - <span data-ttu-id="1d692-331">アクティビティのコンテキスト (右クリック) メニュー。</span><span class="sxs-lookup"><span data-stu-id="1d692-331">The context (right-click) menus for activities.</span></span>

  - <span data-ttu-id="1d692-332">プロパティ グリッドの、プロパティ値エディター、[検索のクリア] ボタン、[カテゴリ別] および [アルファベット順] の並べ替えボタン、[式エディター] ダイアログ。</span><span class="sxs-lookup"><span data-stu-id="1d692-332">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>

  - <span data-ttu-id="1d692-333">ワークフロー デザイナーのズーム パーセンテージ。</span><span class="sxs-lookup"><span data-stu-id="1d692-333">The zoom percentage in the Workflow Designer.</span></span>

  - <span data-ttu-id="1d692-334"><xref:System.Activities.Statements.Parallel> および <xref:System.Activities.Statements.Pick> アクティビティの区切り記号。</span><span class="sxs-lookup"><span data-stu-id="1d692-334">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>

  - <span data-ttu-id="1d692-335"><xref:System.Activities.Statements.InvokeDelegate> アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="1d692-335">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>

  - <span data-ttu-id="1d692-336">ディクショナリ アクティビティの [型の選択] ウィンドウ (`Microsoft.Activities.AddToDictionary<TKey,TValue>`、`Microsoft.Activities.RemoveFromDictionary<TKey,TValue>` など)。</span><span class="sxs-lookup"><span data-stu-id="1d692-336">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span></span>

  - <span data-ttu-id="1d692-337">[.NET 型の参照と選択] ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="1d692-337">The Browse and Select .NET Type window.</span></span>

  - <span data-ttu-id="1d692-338">ワークフロー デザイナーでの階層リンク。</span><span class="sxs-lookup"><span data-stu-id="1d692-338">Breadcrumbs in the Workflow Designer.</span></span>

- <span data-ttu-id="1d692-339">ハイ コントラスト テーマを選ぶと、要素間のコントラスト比の向上や、フォーカス要素に使われる選択ボックスの認識性の向上など、ワークフロー デザイナーとそのコントロールの表示について多くの点が向上していることがわかります。</span><span class="sxs-lookup"><span data-stu-id="1d692-339">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d692-340">参照</span><span class="sxs-lookup"><span data-stu-id="1d692-340">See Also</span></span>

[<span data-ttu-id="1d692-341">.NET Framework の新機能</span><span class="sxs-lookup"><span data-stu-id="1d692-341">What's new in the .NET Framework</span></span>](whats-new.md)
 
