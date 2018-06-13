---
title: Windows フォームでの高 DPI サポート
ms.date: 05/16/2017
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fbf2d7b61b34a2cd4641a77ee1f2fcdff7f3c3fe
ms.sourcegitcommit: b7763f3435635850a76d4cbcf09bdce6c019208a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/25/2018
ms.locfileid: "34483542"
---
# <a name="high-dpi-support-in-windows-forms"></a><span data-ttu-id="e0d09-102">Windows フォームでの高 DPI サポート</span><span class="sxs-lookup"><span data-stu-id="e0d09-102">High DPI support in Windows Forms</span></span>

<span data-ttu-id="e0d09-103">.NET Framework 4.7 以降、Windows フォームには、共通の高 DPI と動的 DPI シナリオ用の機能強化が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e0d09-103">Starting with the .NET Framework 4.7, Windows Forms includes enhancements for common high DPI and dynamic DPI scenarios.</span></span> <span data-ttu-id="e0d09-104">次の設定があります。</span><span class="sxs-lookup"><span data-stu-id="e0d09-104">These include:</span></span> 

- <span data-ttu-id="e0d09-105">スケーリングとさまざまな Windows フォームのレイアウトの改善を制御するように、<xref:System.Windows.Forms.MonthCalendar>コントロールと<xref:System.Windows.Forms.CheckedListBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="e0d09-105">Improvements in the scaling and layout of a number of Windows Forms controls, such as the <xref:System.Windows.Forms.MonthCalendar> control and the <xref:System.Windows.Forms.CheckedListBox> control.</span></span> 

- <span data-ttu-id="e0d09-106">シングル パスをスケーリングします。</span><span class="sxs-lookup"><span data-stu-id="e0d09-106">Single-pass scaling.</span></span>  <span data-ttu-id="e0d09-107">.NET Framework 4.6 と以前のバージョンでのスケーリングが必要以上にスケールする一部のコントロールの原因となる、複数のパスを通じて実行されました。</span><span class="sxs-lookup"><span data-stu-id="e0d09-107">In the .NET Framework 4.6 and earlier versions, scaling was performed through multiple passes, which caused some controls to be scaled more than was necessary.</span></span>

- <span data-ttu-id="e0d09-108">Windows フォーム アプリケーションの起動後、ユーザー DPI またはスケール ファクターを変更する動的の DPI シナリオをサポートします。</span><span class="sxs-lookup"><span data-stu-id="e0d09-108">Support for dynamic DPI scenarios in which the user changes the DPI or scale factor after a Windows Forms application has been launched.</span></span>

<span data-ttu-id="e0d09-109">.NET Framework 4.7 以降の .NET Framework のバージョンでは、高 DPI サポートの強化は、オプトイン機能です。</span><span class="sxs-lookup"><span data-stu-id="e0d09-109">In versions of the .NET Framework starting with the .NET Framework 4.7, enhanced high DPI support is an opt-in feature.</span></span> <span data-ttu-id="e0d09-110">これを活用するために、アプリケーションを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0d09-110">You must configure your application to take advantage of it.</span></span>

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a><span data-ttu-id="e0d09-111">高 DPI サポートについては、Windows フォーム アプリを構成します。</span><span class="sxs-lookup"><span data-stu-id="e0d09-111">Configuring your Windows Forms app for high DPI support</span></span>

<span data-ttu-id="e0d09-112">高 DPI 認識をサポートする新しい Windows フォームの機能は、.NET Framework 4.7 をターゲットし、Windows 10 の作成者の更新で Windows オペレーティング システムで実行されているアプリケーションでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="e0d09-112">The new Windows Forms features that support high DPI awareness are available only in applications that target the .NET Framework 4.7 and are running on Windows operating systems starting with the Windows 10 Creators Update.</span></span> 

<span data-ttu-id="e0d09-113">さらに、Windows フォーム アプリケーションで高 DPI サポートを構成するにする必要があります、次のように行います。</span><span class="sxs-lookup"><span data-stu-id="e0d09-113">In addition, to configure high DPI support in your Windows Forms application, you must do the following:</span></span>

- <span data-ttu-id="e0d09-114">Windows 10 との互換性を宣言します。</span><span class="sxs-lookup"><span data-stu-id="e0d09-114">Declare compatibility with Windows 10.</span></span>

  <span data-ttu-id="e0d09-115">これを行うには、マニフェスト ファイルに、次を追加します。</span><span class="sxs-lookup"><span data-stu-id="e0d09-115">To do this, add the following to your manifest file:</span></span>

  ```xml
  <compatibility xmlns="urn:schemas-microsoft.com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- <span data-ttu-id="e0d09-116">モニターごとの DPI 対応能力を有効にする、 *app.config*ファイル。</span><span class="sxs-lookup"><span data-stu-id="e0d09-116">Enable per-monitor DPI awareness in the *app.config* file.</span></span>

  <span data-ttu-id="e0d09-117">Windows フォームが導入されていますが、新しい[ `<System.Windows.Forms.ApplicationConfigurationSection>` ](../../../docs/framework/configure-apps/file-schema/winforms/index.md)の新機能と .NET Framework 4.7 以降追加のカスタマイズをサポートする要素。</span><span class="sxs-lookup"><span data-stu-id="e0d09-117">Windows Forms introduces a new [`<System.Windows.Forms.ApplicationConfigurationSection>`](../../../docs/framework/configure-apps/file-schema/winforms/index.md) element to support new features and customizations added starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="e0d09-118">高 DPI をサポートする新しい機能を利用するには、アプリケーション構成ファイルに、次を追加します。</span><span class="sxs-lookup"><span data-stu-id="e0d09-118">To take advantage of the new features that support high DPI, add the following to your application configuration file.</span></span>   

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>      
  ```
   
  > [!IMPORTANT]
  > <span data-ttu-id="e0d09-119">.NET Framework の以前のバージョンでは、マニフェストを使用して、高 DPI サポートを追加しました。</span><span class="sxs-lookup"><span data-stu-id="e0d09-119">In previous versions of the .NET Framework, you used the manifest to add high DPI support.</span></span> <span data-ttu-id="e0d09-120">このアプローチは推奨されなく、app.config ファイルで定義された設定をオーバーライドするためです。</span><span class="sxs-lookup"><span data-stu-id="e0d09-120">This approach is no longer recommended, since it overrides settings defined on the app.config file.</span></span>
   
- <span data-ttu-id="e0d09-121">静的なを呼び出す<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e0d09-121">Call the static <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>
   
  <span data-ttu-id="e0d09-122">これは、アプリケーションのエントリ ポイントの最初のメソッド呼び出しでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="e0d09-122">This should be the first method call in your application entry point.</span></span> <span data-ttu-id="e0d09-123">例えば:</span><span class="sxs-lookup"><span data-stu-id="e0d09-123">For example:</span></span>
   
  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());   
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a><span data-ttu-id="e0d09-124">高 DPI 機能を個別の除外</span><span class="sxs-lookup"><span data-stu-id="e0d09-124">Opting out of individual high DPI features</span></span>

<span data-ttu-id="e0d09-125">設定、`DpiAwareness`値を`PerMonitorV2`.NET Framework 4.7 以降の .NET Framework バージョンでサポートされている、すべて高 DPI 認識の機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="e0d09-125">Setting the `DpiAwareness` value to `PerMonitorV2` enables all high DPI awareness features supported by .NET Framework versions starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="e0d09-126">通常、これはほとんどの Windows フォーム アプリケーションに適しています。</span><span class="sxs-lookup"><span data-stu-id="e0d09-126">Typically, this is adequate for most Windows Forms applications.</span></span> <span data-ttu-id="e0d09-127">ただし、1 つまたは複数の個々 の機能を除外することがあります。</span><span class="sxs-lookup"><span data-stu-id="e0d09-127">However, you may want to opt out of one or more individual features.</span></span> <span data-ttu-id="e0d09-128">これを行うための最も重要な理由は、既存のアプリケーション コードは、その機能を既に処理です。</span><span class="sxs-lookup"><span data-stu-id="e0d09-128">The most important reason for doing this is that your existing application code already handles that feature.</span></span>  <span data-ttu-id="e0d09-129">たとえば、アプリケーションでは、自動スケーリングを処理する場合に、次のように自動サイズ変更機能を無効にする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e0d09-129">For example, if your application handles auto scaling, you might want to disable the auto-resizing feature as follows:</span></span>

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" /> 
</System.Windows.Forms.ApplicationConfigurationSection>    
```

<span data-ttu-id="e0d09-130">個々 のキーと値の一覧は、次を参照してください。 [Windows フォームに追加の構成要素](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)です。</span><span class="sxs-lookup"><span data-stu-id="e0d09-130">For a list of individual keys and their values, see [Windows Forms Add Configuration Element](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span></span>

## <a name="new-dpi-change-events"></a><span data-ttu-id="e0d09-131">新しい DPI の変更イベント</span><span class="sxs-lookup"><span data-stu-id="e0d09-131">New DPI change events</span></span>

<span data-ttu-id="e0d09-132">.NET Framework 4.7 以降では、3 つの新しいイベントを使用する動的 DPI の変更をプログラムで処理します。</span><span class="sxs-lookup"><span data-stu-id="e0d09-132">Starting with the .NET Framework 4.7, three new events allow you to programmatically handle dynamic DPI changes:</span></span>

- <span data-ttu-id="e0d09-133"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>、コントロールの DPI 設定は、親コントロールの DPI の変更イベントの後にプログラムで変更またはフォームが発生したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="e0d09-133"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, which is fired when the DPI setting for a control is changed programmatically after a DPI change event for it's parent control or form has occurred.</span></span>
- <span data-ttu-id="e0d09-134"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>、コントロールの DPI 設定は、親コントロールの DPI の変更イベントの前にプログラムで変更またはフォームが発生したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="e0d09-134"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, which is fired when the DPI setting for a control is changed programmatically before a DPI change event for its parent control or form has occurred.</span></span>
- <span data-ttu-id="e0d09-135"><xref:System.Windows.Forms.Form.DpiChanged>、フォームが現在表示されている、ディスプレイ デバイスに DPI 設定が変更されたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="e0d09-135"><xref:System.Windows.Forms.Form.DpiChanged>, which is fired when the DPI setting changes on the display device where the form is currently displayed.</span></span>

## <a name="new-helper-methods-and-properties"></a><span data-ttu-id="e0d09-136">新しいヘルパー メソッドとプロパティ</span><span class="sxs-lookup"><span data-stu-id="e0d09-136">New helper methods and properties</span></span>

<span data-ttu-id="e0d09-137">.NET Framework 4.7 では、さまざまな DPI スケーリングに関する情報を提供し、DPI スケールを実行できるようにする新しいヘルパー メソッドとプロパティも追加されます。</span><span class="sxs-lookup"><span data-stu-id="e0d09-137">The .NET Framework 4.7 also adds a number of new helper methods and properties that provide information about DPI scaling and allow you to perform DPI scaling.</span></span> <span data-ttu-id="e0d09-138">次の設定があります。</span><span class="sxs-lookup"><span data-stu-id="e0d09-138">These include:</span></span>

- <span data-ttu-id="e0d09-139"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>を論理座標から値をデバイス ピクセルに変換します。</span><span class="sxs-lookup"><span data-stu-id="e0d09-139"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, which converts a value from logical to device pixels.</span></span>

- <span data-ttu-id="e0d09-140"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>、デバイスの論理 DPI にビットマップのスケールを設定します。</span><span class="sxs-lookup"><span data-stu-id="e0d09-140"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, which scales a bitmap image to the logical DPI for a device.</span></span>

- <span data-ttu-id="e0d09-141"><xref:System.Windows.Forms.Control.DeviceDpi%2A>、現在のデバイスの DPI が返されます。</span><span class="sxs-lookup"><span data-stu-id="e0d09-141"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, which returns the DPI for the current device.</span></span>

## <a name="versioning-considerations"></a><span data-ttu-id="e0d09-142">バージョン管理に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="e0d09-142">Versioning considerations</span></span>

<span data-ttu-id="e0d09-143">、.NET Framework 4.7 と Windows 10 の作成者 Update 上だけでなく、アプリケーションがない高 DPI の機能強化と互換性のある環境では実行もします。</span><span class="sxs-lookup"><span data-stu-id="e0d09-143">In addition to running on .NET Framework 4.7 and Windows 10 Creators Update, your application may also run in an environment in which it isn't compatible with high DPI improvements.</span></span> <span data-ttu-id="e0d09-144">この場合、代替のアプリケーションを開発する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0d09-144">In this case, you'll need to develop a fallback for your application.</span></span> <span data-ttu-id="e0d09-145">こうことを実行する[カスタム描画](./controls/user-drawn-controls.md)スケーリングを処理します。</span><span class="sxs-lookup"><span data-stu-id="e0d09-145">You can do this to perform [custom drawing](./controls/user-drawn-controls.md) to handle scaling.</span></span>

<span data-ttu-id="e0d09-146">これを行うには、アプリが実行されているオペレーティング システムを決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0d09-146">To do this, you also need to determine the operating system on which your app is running.</span></span> <span data-ttu-id="e0d09-147">次のようなコードを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="e0d09-147">You can do that with code like the following:</span></span>

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

<span data-ttu-id="e0d09-148">アプリケーションが正常が認識できない Windows 10、アプリケーション マニフェストでサポートされているオペレーティング システムとして表示されていない場合に注意してください。</span><span class="sxs-lookup"><span data-stu-id="e0d09-148">Note that your application won't successfully detect Windows 10 if it wasn't listed as a supported operating system in the application manifest.</span></span>

<span data-ttu-id="e0d09-149">に対して、アプリケーションが作成されている .NET Framework のバージョンを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="e0d09-149">You can also check the version of the .NET Framework that the application was built against:</span></span>

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a><span data-ttu-id="e0d09-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0d09-150">See also</span></span>

[<span data-ttu-id="e0d09-151">Windows フォームの構成要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="e0d09-151">Windows Forms Add Configuration Element</span></span>](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)  
[<span data-ttu-id="e0d09-152">Windows フォームのサイズとスケールを調整する</span><span class="sxs-lookup"><span data-stu-id="e0d09-152">Adjusting the Size and Scale of Windows Forms</span></span>](../../../docs/framework/winforms/adjusting-the-size-and-scale-of-windows-forms.md)
