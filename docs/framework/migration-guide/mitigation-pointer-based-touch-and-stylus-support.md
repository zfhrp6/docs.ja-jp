---
title: "軽減策: ポインター ベースのタッチおよびスタイラスのサポート"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
caps.latest.revision: "2"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 78a7365d9bc82111ebd27f40e999c24d8f9ebfde
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="92c52-102">軽減策: ポインター ベースのタッチおよびスタイラスのサポート</span><span class="sxs-lookup"><span data-stu-id="92c52-102">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="92c52-103">.NET Framework 4.7 を対象とし、Windows 10 Creators Update 以降の Windows システムで実行されている WPF アプリケーションは、オプションの `WM_POINTER` ベースの WPF タッチ/スタイラス スタックを有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="92c52-103">WPF applications that target the .NET Framework 4.7 and are running on Windows Systems starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="92c52-104">影響</span><span class="sxs-lookup"><span data-stu-id="92c52-104">Impact</span></span>

<span data-ttu-id="92c52-105">ポインター ベースのタッチ/スタイラス サポートを明示的に有効にしていない開発者は、WPF タッチ/スタイラス動作の変更を確認できません。</span><span class="sxs-lookup"><span data-stu-id="92c52-105">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="92c52-106">オプションの `WM_POINTER` ベースのタッチ/スタイラス スタックに関する現在の既知の問題を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="92c52-106">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="92c52-107">リアルタイム インクがサポートされない。</span><span class="sxs-lookup"><span data-stu-id="92c52-107">No support for real-time inking.</span></span>

   <span data-ttu-id="92c52-108">インクとスタイラス プラグインがまだ機能している間は、UI スレッドで処理されますが、パフォーマンスの低下につながる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="92c52-108">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="92c52-109">プロモーションの変更により、タッチ/スタイラス イベントからマウス イベントに動作が変更される。</span><span class="sxs-lookup"><span data-stu-id="92c52-109">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="92c52-110">操作の動作が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="92c52-110">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="92c52-111">ドラッグ/ドロップでは、タッチ入力の適切なフィードバックが表示されません </span><span class="sxs-lookup"><span data-stu-id="92c52-111">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="92c52-112">(これはスタイラス入力には影響しません)。</span><span class="sxs-lookup"><span data-stu-id="92c52-112">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="92c52-113">ドラッグ/ドロップは、タッチ/スタイラス イベントで開始できなくなりました。</span><span class="sxs-lookup"><span data-stu-id="92c52-113">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="92c52-114">そのため、マウス入力が検出されるまで、アプリケーションがハングする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="92c52-114">This can potentially hang the application until mouse input is detected.</span></span> <span data-ttu-id="92c52-115">代わりに、開発者はマウス イベントからドラッグ アンド ドロップを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="92c52-115">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wmpointer-based-touchstylus-support"></a><span data-ttu-id="92c52-116">WM_POINTER ベースのタッチ/スタイラス サポートの有効化</span><span class="sxs-lookup"><span data-stu-id="92c52-116">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="92c52-117">このスタックを有効にする開発者は、アプリケーションの app.config ファイルに次の行を追加できます。</span><span class="sxs-lookup"><span data-stu-id="92c52-117">Developers who wish to enable this stack can add the following to their application's app.config file:</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="92c52-118">このエントリを削除するか、その値を `false` に設定すると、このオプションのスタックがオフになります。</span><span class="sxs-lookup"><span data-stu-id="92c52-118">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="92c52-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="92c52-119">See also</span></span>

[<span data-ttu-id="92c52-120">.NET Framework 4.7 における再ターゲットの変更点</span><span class="sxs-lookup"><span data-stu-id="92c52-120">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
