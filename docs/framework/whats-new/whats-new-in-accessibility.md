---
title: ".NET Framework のユーザー補助機能の新機能"
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
ms.openlocfilehash: 4886dad94d3a67e78525241a1538c06b9fe4b0be
ms.sourcegitcommit: 6f49c973f62855ffd6c4a322903e7dd50c5c1b50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2017
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="e162e-102">.NET Framework のユーザー補助機能の新機能</span><span class="sxs-lookup"><span data-stu-id="e162e-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="e162e-103">.NET Framework の目的のユーザー用の複数の補助アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="e162e-103">The .NET Framework aims at making applications more accessibile for your users.</span></span> <span data-ttu-id="e162e-104">ユーザー補助機能は、支援技術のユーザーに適切なエクスペリエンスを提供するアプリケーションを許可します。</span><span class="sxs-lookup"><span data-stu-id="e162e-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="e162e-105">以降、.NET Framework 4.7.1 では、.NET Framework には、多数ユーザー補助アプリケーションを作成するためのアクセシビリティの機能強化にはが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e162e-105">Starting with the .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span> 

<span data-ttu-id="e162e-106">新しいユーザー補助機能は、既定では、.NET Framework 4.7.1 を対象とするアプリケーションを有効になっている以降です。</span><span class="sxs-lookup"><span data-stu-id="e162e-106">The new accessibility features are enabled by default for applications that target the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="e162e-107">さらに、アプリケーション、.NET Framework の以前のバージョンをターゲットが .NET Framework 4.7.1 で実行されているまたは後で選択できますレガシ ユーザー補助機能の動作の出力 (およびこれにより、.NET Framework 4.7.1 のユーザー補助機能強化にオプトイン) によって次のスイッチを追加する、 [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)内の要素、 [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md)アプリケーションの構成ファイルのセクションです。</span><span class="sxs-lookup"><span data-stu-id="e162e-107">In addition, applications that target an earlier version of the .NET Framework but are running on the .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby opt in to the accessibility improvements in the .NET Framework 4.7.1) by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="e162e-108">以降 4.7.1 で .NET Framework のバージョンを対象とするアプリケーションがユーザー補助機能を無効にする次のスイッチを追加することで同様に、 [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)内の要素、 [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md)アプリケーションの構成ファイルのセクションです。</span><span class="sxs-lookup"><span data-stu-id="e162e-108">Similarly, applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a><span data-ttu-id="e162e-109">.NET Framework 4.7.1 のユーザー補助機能の新機能</span><span class="sxs-lookup"><span data-stu-id="e162e-109">What's new in accessibility in the .NET Framework 4.7.1</span></span>

<span data-ttu-id="e162e-110">.NET Framework 4.7.1 には、次の領域の新しいユーザー補助機能が含まれます。</span><span class="sxs-lookup"><span data-stu-id="e162e-110">The .NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="e162e-111">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="e162e-111">Windows Presentation Foundation (WPF)</span></span>](#windows-presentation-foundation-wpf)

- [<span data-ttu-id="e162e-112">Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="e162e-112">Windows Forms</span></span>](#windows-forms-accessibility-improvements)

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="e162e-113">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="e162e-113">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="e162e-114">**スクリーン リーダーの強化**</span><span class="sxs-lookup"><span data-stu-id="e162e-114">**Screen reader improvements**</span></span>

<span data-ttu-id="e162e-115">ユーザー補助機能強化が有効な場合、.NET Framework 4.7.1 には、スクリーン リーダーに影響する次の機能強化が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e162e-115">If accessibility improvements are enabled, the .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="e162e-116">.NET Framework 4.7 と以前のバージョンで<xref:System.Windows.Controls.Expander>ボタンとして画面リーダーによってコントロールが発表されました。</span><span class="sxs-lookup"><span data-stu-id="e162e-116">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="e162e-117">.NET Framework 4.7.1 から始めて、展開/折りたたみ可能なグループとして正しく読み上げられます。</span><span class="sxs-lookup"><span data-stu-id="e162e-117">Starting with the .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="e162e-118">.NET Framework 4.7 と以前のバージョンで<xref:System.Windows.Controls.DataGridCell>コントロールがスクリーン リーダーで"custom"に発表されました。</span><span class="sxs-lookup"><span data-stu-id="e162e-118">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="e162e-119">.NET Framework 4.7.1 から始めて、今すぐ正しく読み上げられます (ローカライズされた) データ グリッドのセルとして。</span><span class="sxs-lookup"><span data-stu-id="e162e-119">Starting with the .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>
 
- <span data-ttu-id="e162e-120">.NET Framework 4.7.1 から始めて、スクリーン リーダー アナウンスの編集可能な名前<xref:System.Windows.Controls.ComboBox>です。</span><span class="sxs-lookup"><span data-stu-id="e162e-120">Starting with the .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="e162e-121">.NET Framework 4.7 と以前のバージョンで<xref:System.Windows.Controls.PasswordBox>コントロール「ビューのアイテムがありません」として発表されたがそれ以外の場合に不適切な動作です。</span><span class="sxs-lookup"><span data-stu-id="e162e-121">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="e162e-122">この問題は、.NET Framework 4.7.1 以降では固定です。</span><span class="sxs-lookup"><span data-stu-id="e162e-122">This issue is fixed starting with the .NET Framework 4.7.1.</span></span>     

<span data-ttu-id="e162e-123">**UIAutomation LiveRegion サポート**</span><span class="sxs-lookup"><span data-stu-id="e162e-123">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="e162e-124">ナレーター ヘルプ人などのスクリーン リーダーは、フォーカスのある UI コンテンツの音声合成の出力で通常、アプリケーションの UI の内容を読み取る。</span><span class="sxs-lookup"><span data-stu-id="e162e-124">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="e162e-125">ただし、UI 要素が変更が、フォーカスされていない場合、ユーザーは通知されない場合があり、重要な情報を見逃す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e162e-125">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="e162e-126">この問題の解決を目的としてライブ領域。</span><span class="sxs-lookup"><span data-stu-id="e162e-126">Live regions aim at solving this problem.</span></span> <span data-ttu-id="e162e-127">開発者は、スクリーン リーダーや UI 要素に重要な変更が行われたその他の任意の UIAutomation クライアントを通知するためにそれらを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e162e-127">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="e162e-128">スクリーン リーダー方法とタイミングを決定できますし、この変更のユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e162e-128">The screen reader can then decide how and when to inform the user of this change.</span></span> 

<span data-ttu-id="e162e-129">領域をサポートするライブ、WPF に次の Api が追加されました。</span><span class="sxs-lookup"><span data-stu-id="e162e-129">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="e162e-130"><xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType>と<xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType>、識別フィールド、 **LiveSetting**プロパティおよび**LiveRegionChanged**イベント。</span><span class="sxs-lookup"><span data-stu-id="e162e-130">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="e162e-131">これらは、XAML を使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="e162e-131">They can be set by using XAML.</span></span>

- <span data-ttu-id="e162e-132">**AutomationProperties.LiveSetting**添付プロパティで、ユーザーに、UI の変更の重要度のスクリーン リーダーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e162e-132">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="e162e-133"><xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType>プロパティを識別する、 **AutomationProperties.LiveSetting**添付プロパティ。</span><span class="sxs-lookup"><span data-stu-id="e162e-133">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>
 
- <span data-ttu-id="e162e-134"><xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType>できますをオーバーライドするメソッド、 **LiveSetting**値。</span><span class="sxs-lookup"><span data-stu-id="e162e-134">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="e162e-135"><xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType>と<xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType>get し、set メソッド、 **LiveSetting**値。</span><span class="sxs-lookup"><span data-stu-id="e162e-135">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>
 
- <span data-ttu-id="e162e-136"><xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>列挙体は、次の考えられる定義**LiveSetting**値。</span><span class="sxs-lookup"><span data-stu-id="e162e-136">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

   - <span data-ttu-id="e162e-137"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="e162e-137"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e162e-138">要素は、ライブの領域の内容が変更された場合、通知を送信しません。</span><span class="sxs-lookup"><span data-stu-id="e162e-138">The element does not send notifications if the content of the live region has changed.</span></span>   
   - <span data-ttu-id="e162e-139"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="e162e-139"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e162e-140">ライブ領域の内容が変更された場合、要素は非割り込み型の通知を送信します。</span><span class="sxs-lookup"><span data-stu-id="e162e-140">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>   

  - <span data-ttu-id="e162e-141"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="e162e-141"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e162e-142">ライブ領域の内容が変更された場合、要素により割り込み通知が送信されます。</span><span class="sxs-lookup"><span data-stu-id="e162e-142">The element sends interruptive notifications if the content of the live region has changed.</span></span>   

<span data-ttu-id="e162e-143">設定して、LiveRegion を作成することができます、 **AutomationProperties.LiveSetting**次の例で示すように、目的の要素のプロパティ。</span><span class="sxs-lookup"><span data-stu-id="e162e-143">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="e162e-144">ライブ領域内のデータを変更すると、スクリーン リーダーに通知する必要がありますを明示的にイベントを発生させる、次の例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="e162e-144">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="e162e-145">**ハイ コントラスト**</span><span class="sxs-lookup"><span data-stu-id="e162e-145">**High contrast**</span></span>

<span data-ttu-id="e162e-146">.NET Framework 4.7.1 から始めて、ハイ コントラストの機能強化に加えられたさまざまな WPF コントロールです。</span><span class="sxs-lookup"><span data-stu-id="e162e-146">Starting with the .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="e162e-147">これは表示されているときに、<xref:System.Windows.SystemParameters.HighContrast%2A>テーマを設定します。</span><span class="sxs-lookup"><span data-stu-id="e162e-147">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="e162e-148">以下に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e162e-148">These include:</span></span>

- <span data-ttu-id="e162e-149"><xref:System.Windows.Controls.Expander> コントロール</span><span class="sxs-lookup"><span data-stu-id="e162e-149"><xref:System.Windows.Controls.Expander> control</span></span>

    <span data-ttu-id="e162e-150">ビジュアルをフォーカス、<xref:System.Windows.Controls.Expander>コントロールが表示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="e162e-150">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="e162e-151">キーボードのビジュアルの<xref:System.Windows.Controls.ComboBox>、<xref:System.Windows.Controls.ListBox>、および<xref:System.Windows.Controls.RadioButton>コントロールがも表示されます。</span><span class="sxs-lookup"><span data-stu-id="e162e-151">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="e162e-152">例:</span><span class="sxs-lookup"><span data-stu-id="e162e-152">For example:</span></span>

    <span data-ttu-id="e162e-153">前:</span><span class="sxs-lookup"><span data-stu-id="e162e-153">Before:</span></span> 
    
    ![ユーザー補助機能を強化する前にフォーカスを持つ expander コントロール](media/expander-before.png)

    <span data-ttu-id="e162e-155">後。</span><span class="sxs-lookup"><span data-stu-id="e162e-155">After:</span></span> 

    ![ユーザー補助機能強化の後にフォーカスを持つ expander コントロール](media/expander-after.png)

- <span data-ttu-id="e162e-157"><xref:System.Windows.Controls.CheckBox>および<xref:System.Windows.Controls.RadioButton>コントロール</span><span class="sxs-lookup"><span data-stu-id="e162e-157"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>
 
    <span data-ttu-id="e162e-158">内のテキスト、<xref:System.Windows.Controls.CheckBox>と<xref:System.Windows.Controls.RadioButton>コントロールは、ハイ コントラスト テーマで選択するとわかりやすくようになりました。</span><span class="sxs-lookup"><span data-stu-id="e162e-158">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="e162e-159">例:</span><span class="sxs-lookup"><span data-stu-id="e162e-159">For example:</span></span>

    <span data-ttu-id="e162e-160">前:</span><span class="sxs-lookup"><span data-stu-id="e162e-160">Before:</span></span> 

    ![ユーザー補助機能を強化する前にフォーカスがあるハイ コントラストのラジオ ボタン](media/radio-button-before.png)
    
    <span data-ttu-id="e162e-162">後。</span><span class="sxs-lookup"><span data-stu-id="e162e-162">After:</span></span> 

    ![ユーザー補助機能強化の後にフォーカスがあるハイ コントラストのラジオ ボタン](media/radio-button-after.png)

- <span data-ttu-id="e162e-164"><xref:System.Windows.Controls.ComboBox> コントロール</span><span class="sxs-lookup"><span data-stu-id="e162e-164"><xref:System.Windows.Controls.ComboBox> control</span></span>
 
    <span data-ttu-id="e162e-165">.NET Framework 4.7.1、無効なの枠線で始まる<xref:System.Windows.Controls.ComboBox>コントロールが無効なテキストと同じ色。</span><span class="sxs-lookup"><span data-stu-id="e162e-165">Starting with the .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="e162e-166">例:</span><span class="sxs-lookup"><span data-stu-id="e162e-166">For example:</span></span>
    
    <span data-ttu-id="e162e-167">前:</span><span class="sxs-lookup"><span data-stu-id="e162e-167">Before:</span></span> 

     ![コンボ ボックスには、罫線とユーザー補助機能を強化する前にテキストが無効になっています](media/combo-disabled-before.png)

    <span data-ttu-id="e162e-169">後。</span><span class="sxs-lookup"><span data-stu-id="e162e-169">After:</span></span>   

     ![コンボ ボックスはユーザー補助機能強化の後に罫線とテキストを無効にします。](media/combo-disabled-after.png)

    <span data-ttu-id="e162e-171">さらに、無効になっており、フォーカスされたボタンは、適切なテーマの色を使用します。</span><span class="sxs-lookup"><span data-stu-id="e162e-171">In addition, disabled and focused buttons use the correct theme color.</span></span>

    <span data-ttu-id="e162e-172">前:</span><span class="sxs-lookup"><span data-stu-id="e162e-172">Before:</span></span>

    ![ユーザー補助機能を強化する前にボタンのテーマの色](media/button-themes-before.png) 
    
    <span data-ttu-id="e162e-174">後。</span><span class="sxs-lookup"><span data-stu-id="e162e-174">After:</span></span> 

    ![ユーザー補助機能強化の後にボタンのテーマの色](media/button-themes-after.png) 

    <span data-ttu-id="e162e-176">.NET Framework 4.7 と設定、以前のバージョンで最後に、<xref:System.Windows.Controls.ComboBox>コントロールのスタイルを`Toolbar.ComboBoxStyleKey`ドロップダウン矢印を表示しない原因となった。</span><span class="sxs-lookup"><span data-stu-id="e162e-176">Finally, in the .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="e162e-177">この問題は、.NET Framework 4.7.1 以降では固定です。</span><span class="sxs-lookup"><span data-stu-id="e162e-177">This issue is fixed starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="e162e-178">例:</span><span class="sxs-lookup"><span data-stu-id="e162e-178">For example:</span></span>

    <span data-ttu-id="e162e-179">前:</span><span class="sxs-lookup"><span data-stu-id="e162e-179">Before:</span></span> 

    ![ユーザー補助機能を強化する前に Toolbar.ComboBoxStyleKey](media/comboboxstylekey-before.png) 
    
    <span data-ttu-id="e162e-181">後。</span><span class="sxs-lookup"><span data-stu-id="e162e-181">After:</span></span> 

    ![ユーザー補助機能強化後 Toolbar.ComboBoxStyleKey](media/comboboxstylekey-after.png) 

- <span data-ttu-id="e162e-183"><xref:System.Windows.Controls.DataGrid> コントロール</span><span class="sxs-lookup"><span data-stu-id="e162e-183"><xref:System.Windows.Controls.DataGrid> control</span></span>

    <span data-ttu-id="e162e-184">.NET Framework 4.7.1、並べ替えのインジケーターの矢印で始まる<xref:System.Windows.Controls.DataGrid>これで、使用して解決テーマの色を制御します。</span><span class="sxs-lookup"><span data-stu-id="e162e-184">Starting with the .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="e162e-185">例:</span><span class="sxs-lookup"><span data-stu-id="e162e-185">For example:</span></span>

    <span data-ttu-id="e162e-186">前:</span><span class="sxs-lookup"><span data-stu-id="e162e-186">Before:</span></span> 

    ![ユーザー補助機能を強化する前に並べ替えインジケーターの矢印](media/sort-indicator-before.png) 
    
    <span data-ttu-id="e162e-188">後。</span><span class="sxs-lookup"><span data-stu-id="e162e-188">After:</span></span>   
 
    ![ユーザー補助機能強化の後に並べ替えインジケーターの矢印](media/sort-indicator-after.png) 
    
    <span data-ttu-id="e162e-190">さらに、.NET Framework 4.7 以前のバージョンで、リンクの既定のスタイル内に変更マウス上の正しくない色経由でハイ コントラスト モード。</span><span class="sxs-lookup"><span data-stu-id="e162e-190">In addition, in the .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="e162e-191">これは、.NET Framework 4.7.1 以降の解決。</span><span class="sxs-lookup"><span data-stu-id="e162e-191">This is resolved starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="e162e-192">同様に、 <xref:System.Windows.Controls.DataGrid>  チェック ボックス列がキーボード フォーカス フィードバックについては、.NET Framework 4.7.1 以降の色を使用します。</span><span class="sxs-lookup"><span data-stu-id="e162e-192">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with the .NET Framework 4.7.1.</span></span>

    <span data-ttu-id="e162e-193">前:</span><span class="sxs-lookup"><span data-stu-id="e162e-193">Before:</span></span> 

    ![ユーザー補助機能を強化する前に既定のリンクのスタイルを DataGrid](media/default-link-style-before.png) 
 
    <span data-ttu-id="e162e-195">後。</span><span class="sxs-lookup"><span data-stu-id="e162e-195">After:</span></span>    
  
    ![ユーザー補助機能強化の後に既定のリンクのスタイルを DataGrid](media/default-link-style-after.png)  

<span data-ttu-id="e162e-197">.NET Framework 4.7.1 の WPF ユーザー補助機能強化の詳細については、次を参照してください。 [WPF のユーザー補助機能の強化](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf)です。</span><span class="sxs-lookup"><span data-stu-id="e162e-197">For more information on WPF accessibility improvements in the .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

## <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="e162e-198">Windows フォームのユーザー補助機能強化</span><span class="sxs-lookup"><span data-stu-id="e162e-198">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="e162e-199">.NET framework 4.7.1 では、Windows フォーム (WinForms) には、次の領域でユーザー補助機能の変更が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e162e-199">In the .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="e162e-200">**ハイ コントラスト モードで表示を改善しました**</span><span class="sxs-lookup"><span data-stu-id="e162e-200">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="e162e-201">以降、.NET Framework 4.7.1 では、さまざまな WinForms コントロールは、オペレーティング システムで使用できるハイコントラスト モードで向上のレンダリングを提供します。</span><span class="sxs-lookup"><span data-stu-id="e162e-201">Starting with the .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="e162e-202">Windows 10 には、ハイ コントラスト システムの一部の色の値が変更されており、Windows フォームは、Windows 10 の Win32 framework に基づいています。</span><span class="sxs-lookup"><span data-stu-id="e162e-202">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="e162e-203">最良の結果は、最新バージョンの Windows で実行し、テスト アプリケーションとコメントを解除して Windows 10 で、アプリケーション マニフェスト ファイルに OS 行がサポートされている場合に、次を追加して、OS の最新の変更を有効します。</span><span class="sxs-lookup"><span data-stu-id="e162e-203">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!– Windows 10 –>
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
<span data-ttu-id="e162e-204">ハイ コントラストの変更の例をいくつかは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e162e-204">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="e162e-205">チェック マーク<xref:System.Windows.Forms.MenuStrip>項目は簡単に表示します。</span><span class="sxs-lookup"><span data-stu-id="e162e-205">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="e162e-206">選択した場合は、次の無効になっています。<xref:System.Windows.Forms.MenuStrip>項目は簡単に表示します。</span><span class="sxs-lookup"><span data-stu-id="e162e-206">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="e162e-207">選択したテキスト<xref:System.Windows.Forms.Button>選択範囲の色とコントラストを制御します。</span><span class="sxs-lookup"><span data-stu-id="e162e-207">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="e162e-208">無効な文字が読みやすくします。</span><span class="sxs-lookup"><span data-stu-id="e162e-208">Disabled text is easier to read.</span></span> <span data-ttu-id="e162e-209">例:</span><span class="sxs-lookup"><span data-stu-id="e162e-209">For example:</span></span>

    <span data-ttu-id="e162e-210">前:</span><span class="sxs-lookup"><span data-stu-id="e162e-210">Before:</span></span>

    ![ユーザー補助機能を強化する前に無効なテキスト](media/wf-disabled-before.png) 

    <span data-ttu-id="e162e-212">後。</span><span class="sxs-lookup"><span data-stu-id="e162e-212">After:</span></span>

    ![ユーザー補助機能強化の後に無効なテキスト](media/wf-disabled-after.png) 

- <span data-ttu-id="e162e-214">スレッドの例外ダイアログ ボックスでハイ コントラストの向上。</span><span class="sxs-lookup"><span data-stu-id="e162e-214">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="e162e-215">**ナレーターのサポートの強化**</span><span class="sxs-lookup"><span data-stu-id="e162e-215">**Improved Narrator support**</span></span>

<span data-ttu-id="e162e-216">.NET Framework 4.7.1 での Windows フォームには、ナレーターの次のユーザー補助機能強化が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e162e-216">Windows Forms in the .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="e162e-217"><xref:System.Windows.Forms.MonthCalendar>コントロールは、ナレーターおよび他の UI オートメーション ツールでアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e162e-217">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="e162e-218"><xref:System.Windows.Forms.CheckedListBox>コントロールがユーザーに通知するリスト項目の値を変更したこと、アイテムのチェック状態が変化したときに、ナレーターを通知します。</span><span class="sxs-lookup"><span data-stu-id="e162e-218">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>
 
- <span data-ttu-id="e162e-219"><xref:System.Windows.Forms.DataGridViewCell>コントロールは、ナレーターに正しい読み取り専用ステータスをレポートします。</span><span class="sxs-lookup"><span data-stu-id="e162e-219">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>
 
- <span data-ttu-id="e162e-220">ナレーターは、無効を読み取ることができるようになりました<xref:System.Windows.Forms.ToolStripMenuItem>テキスト、無効なメニュー項目をスキップは、以前はします。</span><span class="sxs-lookup"><span data-stu-id="e162e-220">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="e162e-221">**UIAutomation アクセシビリティ パターンのサポートの強化**</span><span class="sxs-lookup"><span data-stu-id="e162e-221">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="e162e-222">.NET Framework 4.7.1 から始めて、API ユーザー補助機能の一般的なパターンといくつかの WinForms コントロールのプロパティをユーザー補助テクノロジのツールの開発者は利用できます。</span><span class="sxs-lookup"><span data-stu-id="e162e-222">Starting with the .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="e162e-223">これらのユーザー補助機能強化は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e162e-223">These accessibility improvements include:</span></span>

- <span data-ttu-id="e162e-224"><xref:System.Windows.Forms.ComboBox>と<xref:System.Windows.Forms.ToolStripSplitButton>ようになりました、[展開/折りたたみパターン](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)です。</span><span class="sxs-lookup"><span data-stu-id="e162e-224">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>
 
- <span data-ttu-id="e162e-225"><xref:System.Windows.Forms.DataGridViewCheckBoxCell>ようになりました、[トグル パターン](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md)です。</span><span class="sxs-lookup"><span data-stu-id="e162e-225">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>
 
- <span data-ttu-id="e162e-226"><xref:System.Windows.Forms.ToolStripItem>サポート、<xref:System.Windows.Automation.AutomationElement.Name>プロパティおよび[展開/折りたたみパターン](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)です。</span><span class="sxs-lookup"><span data-stu-id="e162e-226">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="e162e-227"><xref:System.Windows.Forms.NumericUpDown>と<xref:System.Windows.Forms.DomainUpDown>のサポートを制御、<xref:System.Windows.Automation.automationElement.Name>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="e162e-227">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.automationElement.Name> property.</span></span>

<span data-ttu-id="e162e-228">**ブラウザー エクスペリエンスの向上プロパティ**</span><span class="sxs-lookup"><span data-stu-id="e162e-228">**Improved property browser experience**</span></span>

<span data-ttu-id="e162e-229">以降、.NET Framework 4.7.1 では、Windows フォームが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e162e-229">Starting with the .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="e162e-230">さまざまなドロップダウン選択ウィンドウをキーボード ナビゲーション機能が向上します。</span><span class="sxs-lookup"><span data-stu-id="e162e-230">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="e162e-231">不要なタブの削減を停止します。</span><span class="sxs-lookup"><span data-stu-id="e162e-231">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="e162e-232">コントロールの種類の報告が改善します。</span><span class="sxs-lookup"><span data-stu-id="e162e-232">Better reporting of control types.</span></span>
- <span data-ttu-id="e162e-233">ナレーターの強化された動作です。</span><span class="sxs-lookup"><span data-stu-id="e162e-233">Improved narrator behavior.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="e162e-234">関連項目</span><span class="sxs-lookup"><span data-stu-id="e162e-234">See Also</span></span>
[<span data-ttu-id="e162e-235">.NET Framework の新機能</span><span class="sxs-lookup"><span data-stu-id="e162e-235">What's new in the .NET Framework</span></span>](whats-new.md)   
 