---
title: ".NET Framework のアクセシビリティの新機能"
ms.custom: updateeachrelease
ms.date: 10/13/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6a6759ae285f2dd101bddf71ea8e5ca792e87df
ms.sourcegitcommit: 957c696f25e39f923a827fc3ad5e8ab72768838c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="83874-102">.NET Framework のアクセシビリティの新機能</span><span class="sxs-lookup"><span data-stu-id="83874-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="83874-103">.NET Framework では、ユーザーのためにアプリケーションのアクセシビリティ向上を目指しています。</span><span class="sxs-lookup"><span data-stu-id="83874-103">The .NET Framework aims at making applications more accessibile for your users.</span></span> <span data-ttu-id="83874-104">ユーザー補助機能により、支援機能の利用者にとってアプリケーションがさらに使いやすくなります。</span><span class="sxs-lookup"><span data-stu-id="83874-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="83874-105">.NET Framework 4.7.1 以降、.NET Framework にはさまざまなアクセシビリティ拡張機能が含まれるようになりました。それを利用することで開発者はアクセシビリティを備えたアプリケーションを開発できます。</span><span class="sxs-lookup"><span data-stu-id="83874-105">Starting with the .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span> 

<span data-ttu-id="83874-106">.NET Framework 4.7.1 以降を対象とするアプリケーションでは、この新しいユーザー補助機能が既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="83874-106">The new accessibility features are enabled by default for applications that target the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="83874-107">また、初期の .NET Framework を対象としているが、.NET Framework 4.7.1 以降で実行されているアプリケーションの場合、古いアクセシビリティ動作を利用しないことを選択できます (.NET Framework 4.7.1 のアクセシビリティ拡張機能の利用を選択します)。その場合、アプリケーションの設定ファイルの [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) セクションで次のスイッチを [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 要素に追加してください。</span><span class="sxs-lookup"><span data-stu-id="83874-107">In addition, applications that target an earlier version of the .NET Framework but are running on the .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby opt in to the accessibility improvements in the .NET Framework 4.7.1) by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="83874-108">同様に、4.7.1 以降の .NET Framework を対象にしているアプリケーションではアクセシビリティ機能を無効にできます。その場合、アプリケーションの設定ファイルの [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) セクションで次のスイッチを [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 要素に追加してください。</span><span class="sxs-lookup"><span data-stu-id="83874-108">Similarly, applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a><span data-ttu-id="83874-109">.NET Framework 4.7.1 のアクセシビリティの新機能</span><span class="sxs-lookup"><span data-stu-id="83874-109">What's new in accessibility in the .NET Framework 4.7.1</span></span>

<span data-ttu-id="83874-110">.NET Framework 4.7.1 には、次の領域の新しいアクセシビリティ機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="83874-110">The .NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="83874-111">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="83874-111">Windows Presentation Foundation (WPF)</span></span>](#windows-presentation-foundation-wpf)

- [<span data-ttu-id="83874-112">Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="83874-112">Windows Forms</span></span>](#windows-forms-accessibility-improvements)

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="83874-113">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="83874-113">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="83874-114">**スクリーン リーダーの機能強化**</span><span class="sxs-lookup"><span data-stu-id="83874-114">**Screen reader improvements**</span></span>

<span data-ttu-id="83874-115">アクセシビリティ拡張機能を有効にすると、.NET Framework 4.7.1 は次の面でスクリーン リーダーの機能を強化します。</span><span class="sxs-lookup"><span data-stu-id="83874-115">If accessibility improvements are enabled, the .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="83874-116">.NET Framework 4.7 以前のバージョンでは、スクリーン リーダーが <xref:System.Windows.Controls.Expander> コントロールをボタンとして読み上げました。</span><span class="sxs-lookup"><span data-stu-id="83874-116">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="83874-117">.NET Framework 4.7.1 以降では、展開と折りたたみが可能なグループとして正しく読み上げられます。</span><span class="sxs-lookup"><span data-stu-id="83874-117">Starting with the .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="83874-118">.NET Framework 4.7 以前のバージョンの場合、スクリーン リーダーが <xref:System.Windows.Controls.DataGridCell> コントロールを “カスタム” として読み上げました。</span><span class="sxs-lookup"><span data-stu-id="83874-118">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="83874-119">.NET Framework 4.7.1 以降では、データ グリッド セル (ローカライズされます) として正しく読み上げられます。</span><span class="sxs-lookup"><span data-stu-id="83874-119">Starting with the .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>
 
- <span data-ttu-id="83874-120">.NET Framework 4.7.1 以降、スクリーン リーダーは編集可能な <xref:System.Windows.Controls.ComboBox> の名前を読み上げます。</span><span class="sxs-lookup"><span data-stu-id="83874-120">Starting with the .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="83874-121">.NET Framework 4.7 以前のバージョンの場合、<xref:System.Windows.Controls.PasswordBox> コントロールが “ビューに項目がありません” として読み上げられたか、他の誤動作が発生しました。</span><span class="sxs-lookup"><span data-stu-id="83874-121">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="83874-122">この問題は .NET Framework 4.7.1 以降で修正されています。</span><span class="sxs-lookup"><span data-stu-id="83874-122">This issue is fixed starting with the .NET Framework 4.7.1.</span></span>     

<span data-ttu-id="83874-123">**UIAutomation LiveRegion サポート**</span><span class="sxs-lookup"><span data-stu-id="83874-123">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="83874-124">ナレーターなどのスクリーン リーダーはアプリケーションの UI コンテンツをユーザーのために読み上げます。通常、フォーカスを合わせた UI コンテンツのテキストが読み上げられます。</span><span class="sxs-lookup"><span data-stu-id="83874-124">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="83874-125">ただし、UI 要素が変わり、フォーカスがなくなったとき、ユーザーに通知されず、重要な情報を逃すことがあります。</span><span class="sxs-lookup"><span data-stu-id="83874-125">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="83874-126">ライブ領域は、この問題の解決を目指しています。</span><span class="sxs-lookup"><span data-stu-id="83874-126">Live regions aim at solving this problem.</span></span> <span data-ttu-id="83874-127">開発者はこれを利用し、UI 要素が大幅に変更されたことをスクリーン リーダーやその他の UIAutomation クライアントに指示できます。</span><span class="sxs-lookup"><span data-stu-id="83874-127">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="83874-128">指示後、スクリーン リーダーでは、その変更をユーザーに通知する方法とタイミングが決定されます。</span><span class="sxs-lookup"><span data-stu-id="83874-128">The screen reader can then decide how and when to inform the user of this change.</span></span> 

<span data-ttu-id="83874-129">ライブ領域をサポートするために、次の API が WPF に追加されました。</span><span class="sxs-lookup"><span data-stu-id="83874-129">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="83874-130"><xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> フィールドと <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> フィールド。**LiveSetting** プロパティと **LiveRegionChanged** イベントを識別します。</span><span class="sxs-lookup"><span data-stu-id="83874-130">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="83874-131">XAML を利用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="83874-131">They can be set by using XAML.</span></span>

- <span data-ttu-id="83874-132">**AutomationProperties.LiveSetting** 添付プロパティ。UI の変化がユーザーにとって重要であることをスクリーン リーダーに伝えます。</span><span class="sxs-lookup"><span data-stu-id="83874-132">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="83874-133"><xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> プロパティ。**AutomationProperties.LiveSetting** 添付プロパティを識別します。</span><span class="sxs-lookup"><span data-stu-id="83874-133">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>
 
- <span data-ttu-id="83874-134"><xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> メソッド。**LiveSetting** 値を提供するようにオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="83874-134">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="83874-135"><xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> メソッドと <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> メソッド。**LiveSetting** 値を取得し、設定します。</span><span class="sxs-lookup"><span data-stu-id="83874-135">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>
 
- <span data-ttu-id="83874-136"><xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> 列挙。次の指定可能 **LiveSetting** 値を定義します。</span><span class="sxs-lookup"><span data-stu-id="83874-136">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

   - <span data-ttu-id="83874-137"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="83874-137"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="83874-138">ライブ領域の内容が変更された場合でも、要素が通知を送信することはありません。</span><span class="sxs-lookup"><span data-stu-id="83874-138">The element does not send notifications if the content of the live region has changed.</span></span>   
   - <span data-ttu-id="83874-139"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="83874-139"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="83874-140">ライブ領域の内容が変更された場合、要素は非割り込み型の通知を送信します。</span><span class="sxs-lookup"><span data-stu-id="83874-140">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>   

  - <span data-ttu-id="83874-141"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="83874-141"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="83874-142">ライブ領域の内容が変更された場合、要素により割り込み通知が送信されます。</span><span class="sxs-lookup"><span data-stu-id="83874-142">The element sends interruptive notifications if the content of the live region has changed.</span></span>   

<span data-ttu-id="83874-143">関心のある要素で **AutomationProperties.LiveSetting** プロパティを作成できます。次の例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="83874-143">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="83874-144">ライブ領域のデータが変化し、スクリーン リーダーに通知する必要があれば、次のサンプルのように、明示的にイベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="83874-144">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="83874-145">**ハイ コントラスト**</span><span class="sxs-lookup"><span data-stu-id="83874-145">**High contrast**</span></span>

<span data-ttu-id="83874-146">.NET Framework 4.7.1 以降、さまざまな WPF コントロールでハイ コントラストが強化されました。</span><span class="sxs-lookup"><span data-stu-id="83874-146">Starting with the .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="83874-147"><xref:System.Windows.SystemParameters.HighContrast%2A> テーマが設定されているときにこれを確認できます。</span><span class="sxs-lookup"><span data-stu-id="83874-147">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="83874-148">次の設定があります。</span><span class="sxs-lookup"><span data-stu-id="83874-148">These include:</span></span>

- <span data-ttu-id="83874-149"><xref:System.Windows.Controls.Expander> コントロール</span><span class="sxs-lookup"><span data-stu-id="83874-149"><xref:System.Windows.Controls.Expander> control</span></span>

    <span data-ttu-id="83874-150">フォーカスを合わせたとき、<xref:System.Windows.Controls.Expander> コントロールが見やすくなりました。</span><span class="sxs-lookup"><span data-stu-id="83874-150">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="83874-151"><xref:System.Windows.Controls.ComboBox>、<xref:System.Windows.Controls.ListBox>、<xref:System.Windows.Controls.RadioButton> コントロールのキーボードも見やすくなりました。</span><span class="sxs-lookup"><span data-stu-id="83874-151">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="83874-152">例:</span><span class="sxs-lookup"><span data-stu-id="83874-152">For example:</span></span>

    <span data-ttu-id="83874-153">前:</span><span class="sxs-lookup"><span data-stu-id="83874-153">Before:</span></span> 
    
    ![フォーカスを合わせた Expander コントロール (アクセシビリティ機能改善前)](media/expander-before.png)

    <span data-ttu-id="83874-155">後:</span><span class="sxs-lookup"><span data-stu-id="83874-155">After:</span></span> 

    ![フォーカスを合わせた Expander コントロール (アクセシビリティ機能改善後)](media/expander-after.png)

- <span data-ttu-id="83874-157"><xref:System.Windows.Controls.CheckBox> コントロールと <xref:System.Windows.Controls.RadioButton> コントロール</span><span class="sxs-lookup"><span data-stu-id="83874-157"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>
 
    <span data-ttu-id="83874-158"><xref:System.Windows.Controls.CheckBox> コントロールと <xref:System.Windows.Controls.RadioButton> コントロールのテキストは、ハイ コントラスト テーマで選択されているとき、見やすくなりました。</span><span class="sxs-lookup"><span data-stu-id="83874-158">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="83874-159">例:</span><span class="sxs-lookup"><span data-stu-id="83874-159">For example:</span></span>

    <span data-ttu-id="83874-160">前:</span><span class="sxs-lookup"><span data-stu-id="83874-160">Before:</span></span> 

    ![フォーカスを合わせたハイ コントラストのラジオ ボタン (アクセシビリティ機能改善前)](media/radio-button-before.png)
    
    <span data-ttu-id="83874-162">後:</span><span class="sxs-lookup"><span data-stu-id="83874-162">After:</span></span> 

    ![フォーカスを合わせたハイ コントラストのラジオ ボタン (アクセシビリティ機能改善後)](media/radio-button-after.png)

- <span data-ttu-id="83874-164"><xref:System.Windows.Controls.ComboBox> コントロール</span><span class="sxs-lookup"><span data-stu-id="83874-164"><xref:System.Windows.Controls.ComboBox> control</span></span>
 
    <span data-ttu-id="83874-165">.NET Framework 4.7.1 以降、無効にした <xref:System.Windows.Controls.ComboBox> コントロールの枠線が無効にしたテキストと同じ色になります。</span><span class="sxs-lookup"><span data-stu-id="83874-165">Starting with the .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="83874-166">例:</span><span class="sxs-lookup"><span data-stu-id="83874-166">For example:</span></span>
    
    <span data-ttu-id="83874-167">前:</span><span class="sxs-lookup"><span data-stu-id="83874-167">Before:</span></span> 

     ![無効にした ComboBox の枠線とテキスト (アクセシビリティ機能改善前)](media/combo-disabled-before.png)

    <span data-ttu-id="83874-169">後:</span><span class="sxs-lookup"><span data-stu-id="83874-169">After:</span></span>   

     ![無効にした ComboBox の枠線とテキスト (アクセシビリティ機能改善後)](media/combo-disabled-after.png)

    <span data-ttu-id="83874-171">また、無効にしているボタンにフォーカスを合わせたとき、正しいテーマ色が使用されます。</span><span class="sxs-lookup"><span data-stu-id="83874-171">In addition, disabled and focused buttons use the correct theme color.</span></span>

    <span data-ttu-id="83874-172">前:</span><span class="sxs-lookup"><span data-stu-id="83874-172">Before:</span></span>

    ![ボタンのテーマ色 (アクセシビリティ機能改善前)](media/button-themes-before.png) 
    
    <span data-ttu-id="83874-174">後:</span><span class="sxs-lookup"><span data-stu-id="83874-174">After:</span></span> 

    ![ボタンのテーマ色 (アクセシビリティ機能改善後)](media/button-themes-after.png) 

    <span data-ttu-id="83874-176">最後になりますが、.NET Framework 4.7 以前のバージョンでは、<xref:System.Windows.Controls.ComboBox> コントロールのスタイルを `Toolbar.ComboBoxStyleKey` に設定すると、ドロップダウンの矢印が見えなくなりました。</span><span class="sxs-lookup"><span data-stu-id="83874-176">Finally, in the .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="83874-177">この問題は .NET Framework 4.7.1 以降で修正されています。</span><span class="sxs-lookup"><span data-stu-id="83874-177">This issue is fixed starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="83874-178">例:</span><span class="sxs-lookup"><span data-stu-id="83874-178">For example:</span></span>

    <span data-ttu-id="83874-179">前:</span><span class="sxs-lookup"><span data-stu-id="83874-179">Before:</span></span> 

    ![Toolbar.ComboBoxStyleKey (アクセシビリティ機能改善前)](media/comboboxstylekey-before.png) 
    
    <span data-ttu-id="83874-181">後:</span><span class="sxs-lookup"><span data-stu-id="83874-181">After:</span></span> 

    ![Toolbar.ComboBoxStyleKey (アクセシビリティ機能改善後)](media/comboboxstylekey-after.png) 

- <span data-ttu-id="83874-183"><xref:System.Windows.Controls.DataGrid> コントロール</span><span class="sxs-lookup"><span data-stu-id="83874-183"><xref:System.Windows.Controls.DataGrid> control</span></span>

    <span data-ttu-id="83874-184">.NET Framework 4.7.1 以降、<xref:System.Windows.Controls.DataGrid> コントロールの並べ替えインジケーターで正しいテーマ色が使われるようになりました。</span><span class="sxs-lookup"><span data-stu-id="83874-184">Starting with the .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="83874-185">例:</span><span class="sxs-lookup"><span data-stu-id="83874-185">For example:</span></span>

    <span data-ttu-id="83874-186">前:</span><span class="sxs-lookup"><span data-stu-id="83874-186">Before:</span></span> 

    ![並べ替えインジケーターの矢印 (アクセシビリティ機能改善前)](media/sort-indicator-before.png) 
    
    <span data-ttu-id="83874-188">後:</span><span class="sxs-lookup"><span data-stu-id="83874-188">After:</span></span>   
 
    ![並べ替えインジケーターの矢印 (アクセシビリティ機能改善後)](media/sort-indicator-after.png) 
    
    <span data-ttu-id="83874-190">また、.NET Framework 4.7 以前のバージョンでは、ハイ コントラスト モードでカーソルを合わせたとき、既定のリンク スタイルが正しくない色に変化しました。</span><span class="sxs-lookup"><span data-stu-id="83874-190">In addition, in the .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="83874-191">これは .NET Framework 4.7.1 以降で修正されています。</span><span class="sxs-lookup"><span data-stu-id="83874-191">This is resolved starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="83874-192">同様に、.NET Framework 4.7.1 以降、<xref:System.Windows.Controls.DataGrid> チェックボックス列でキーボード フォーカス フィードバックに既定の色が使用されます。</span><span class="sxs-lookup"><span data-stu-id="83874-192">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with the .NET Framework 4.7.1.</span></span>

    <span data-ttu-id="83874-193">前:</span><span class="sxs-lookup"><span data-stu-id="83874-193">Before:</span></span> 

    ![DataGrid の既定のリンク スタイル (アクセシビリティ機能改善前)](media/default-link-style-before.png) 
 
    <span data-ttu-id="83874-195">後:</span><span class="sxs-lookup"><span data-stu-id="83874-195">After:</span></span>    
  
    ![DataGrid の既定のリンク スタイル (アクセシビリティ機能改善後)](media/default-link-style-after.png)  

<span data-ttu-id="83874-197">.NET Framework 4.7.1 のアクセシビリティ機能の改善の詳細については、「[Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf)」 (WPF のアクセシビリティ機能改善) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83874-197">For more information on WPF accessibility improvements in the .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

## <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="83874-198">Windows フォームのアクセシビリティ機能改善</span><span class="sxs-lookup"><span data-stu-id="83874-198">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="83874-199">.NET Framework 4.7.1 では、Windows フォーム (WinForms) のアクセシビリティが次の領域で変更されました。</span><span class="sxs-lookup"><span data-stu-id="83874-199">In the .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="83874-200">**ハイ コントラスト モードの表示が改善されました**</span><span class="sxs-lookup"><span data-stu-id="83874-200">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="83874-201">.NET Framework 4.7.1 以降では、オペレーティング システムで利用できるハイ コントラスト モードを選択したとき、さまざまな WinForms コントロールの表示が改善されました。</span><span class="sxs-lookup"><span data-stu-id="83874-201">Starting with the .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="83874-202">Windows 10 では、ハイ コントラストのシステム色の一部で値が変わりました。Windows フォームは Windows 10 Win32 フレームワークに基づきます。</span><span class="sxs-lookup"><span data-stu-id="83874-202">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="83874-203">最も快適に利用するためには、最新版の Windows で実行し、テスト アプリケーションに app.manifest ファイルを追加して最新の OS 変更を選択し、次の画像のように Windows 10 対応 OS 行のコメントを解除します。</span><span class="sxs-lookup"><span data-stu-id="83874-203">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!– Windows 10 –>
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
<span data-ttu-id="83874-204">ハイ コントラストの変更例:</span><span class="sxs-lookup"><span data-stu-id="83874-204">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="83874-205"><xref:System.Windows.Forms.MenuStrip> 項目のチェックマークが見やすくなりました。</span><span class="sxs-lookup"><span data-stu-id="83874-205">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="83874-206">選択したとき、無効になっている <xref:System.Windows.Forms.MenuStrip> 項目が見やすくなりました。</span><span class="sxs-lookup"><span data-stu-id="83874-206">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="83874-207">選択した <xref:System.Windows.Forms.Button> コントロールのテキストが背景色に対して際立ち、見やすくなりました。</span><span class="sxs-lookup"><span data-stu-id="83874-207">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="83874-208">無効になっているテキストが読みやすくなりました。</span><span class="sxs-lookup"><span data-stu-id="83874-208">Disabled text is easier to read.</span></span> <span data-ttu-id="83874-209">例:</span><span class="sxs-lookup"><span data-stu-id="83874-209">For example:</span></span>

    <span data-ttu-id="83874-210">前:</span><span class="sxs-lookup"><span data-stu-id="83874-210">Before:</span></span>

    ![無効にしたテキスト (アクセシビリティ機能改善前)](media/wf-disabled-before.png) 

    <span data-ttu-id="83874-212">後:</span><span class="sxs-lookup"><span data-stu-id="83874-212">After:</span></span>

    ![無効にしたテキスト (アクセシビリティ機能改善後)](media/wf-disabled-after.png) 

- <span data-ttu-id="83874-214">スレッド例外ダイアログのハイ コントラストが改善されました。</span><span class="sxs-lookup"><span data-stu-id="83874-214">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="83874-215">**ナレーター サポートが改善されました**</span><span class="sxs-lookup"><span data-stu-id="83874-215">**Improved Narrator support**</span></span>

<span data-ttu-id="83874-216">.NET Framework 4.7.1 の Windows フォームでは、ナレーターのアクセシビリティが次の面で改善されました。</span><span class="sxs-lookup"><span data-stu-id="83874-216">Windows Forms in the .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="83874-217"><xref:System.Windows.Forms.MonthCalendar> コントロールに、他の UI 自動化ツールと同様に、ナレーターからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="83874-217">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="83874-218"><xref:System.Windows.Forms.CheckedListBox> コントロールは、項目のチェック状態が変わったとき、ナレーターに通知します。その結果、リスト アイテムの値を変えたことがユーザーに通知されます。</span><span class="sxs-lookup"><span data-stu-id="83874-218">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>
 
- <span data-ttu-id="83874-219"><xref:System.Windows.Forms.DataGridViewCell> コントロールは正しい読み取り専用状態をナレーターに報告します。</span><span class="sxs-lookup"><span data-stu-id="83874-219">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>
 
- <span data-ttu-id="83874-220">ナレーターが無効になっている <xref:System.Windows.Forms.ToolStripMenuItem> テキストを読み上げるようになりました。以前は、無効になっているメニュー項目はスキップされました。</span><span class="sxs-lookup"><span data-stu-id="83874-220">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="83874-221">**UIAutomation アクセシビリティ パターンのサポートが強化されました**</span><span class="sxs-lookup"><span data-stu-id="83874-221">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="83874-222">.NET Framework 4.7.1 以降、アクセシビリティ技術ツールの開発者は、一部の WinForms コントロールについて、API アクセシビリティの共通のパターンとプロパティを活用できます。</span><span class="sxs-lookup"><span data-stu-id="83874-222">Starting with the .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="83874-223">アクセシビリティ機能改善の例:</span><span class="sxs-lookup"><span data-stu-id="83874-223">These accessibility improvements include:</span></span>

- <span data-ttu-id="83874-224"><xref:System.Windows.Forms.ComboBox> と <xref:System.Windows.Forms.ToolStripSplitButton> が[展開/折りたたみパターン](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)対応になりました。</span><span class="sxs-lookup"><span data-stu-id="83874-224">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>
 
- <span data-ttu-id="83874-225"><xref:System.Windows.Forms.DataGridViewCheckBoxCell> が[切り替えパターン](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md)対応になりました。</span><span class="sxs-lookup"><span data-stu-id="83874-225">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>
 
- <span data-ttu-id="83874-226"><xref:System.Windows.Forms.ToolStripItem> コントロールが <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> プロパティと[展開/折りたたみパターン](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)対応になりました。</span><span class="sxs-lookup"><span data-stu-id="83874-226">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="83874-227"><xref:System.Windows.Forms.NumericUpDown> コントロールと <xref:System.Windows.Forms.DomainUpDown> コントロールが <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> プロパティ対応になりました。</span><span class="sxs-lookup"><span data-stu-id="83874-227">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="83874-228">**プロパティ ブラウザーが使いやすくなりました**</span><span class="sxs-lookup"><span data-stu-id="83874-228">**Improved property browser experience**</span></span>

<span data-ttu-id="83874-229">.NET Framework 4.7.1 以降、Windows フォームは次の点で改善されました。</span><span class="sxs-lookup"><span data-stu-id="83874-229">Starting with the .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="83874-230">さまざまなドロップダウン選択ウィンドウを利用することでキーボード操作が便利になりました。</span><span class="sxs-lookup"><span data-stu-id="83874-230">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="83874-231">不要なタブ ストップが減りました。</span><span class="sxs-lookup"><span data-stu-id="83874-231">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="83874-232">コントロールの種類の報告機能が改善されました。</span><span class="sxs-lookup"><span data-stu-id="83874-232">Better reporting of control types.</span></span>
- <span data-ttu-id="83874-233">ナレーターの動作が改善されました。</span><span class="sxs-lookup"><span data-stu-id="83874-233">Improved narrator behavior.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="83874-234">参照</span><span class="sxs-lookup"><span data-stu-id="83874-234">See Also</span></span>
[<span data-ttu-id="83874-235">.NET Framework の新機能</span><span class="sxs-lookup"><span data-stu-id="83874-235">What's new in the .NET Framework</span></span>](whats-new.md)   
 