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
# <a name="high-dpi-support-in-windows-forms"></a>Windows フォームでの高 DPI サポート

.NET Framework 4.7 以降、Windows フォームには、共通の高 DPI と動的 DPI シナリオ用の機能強化が含まれています。 次の設定があります。 

- スケーリングとさまざまな Windows フォームのレイアウトの改善を制御するように、<xref:System.Windows.Forms.MonthCalendar>コントロールと<xref:System.Windows.Forms.CheckedListBox>コントロール。 

- シングル パスをスケーリングします。  .NET Framework 4.6 と以前のバージョンでのスケーリングが必要以上にスケールする一部のコントロールの原因となる、複数のパスを通じて実行されました。

- Windows フォーム アプリケーションの起動後、ユーザー DPI またはスケール ファクターを変更する動的の DPI シナリオをサポートします。

.NET Framework 4.7 以降の .NET Framework のバージョンでは、高 DPI サポートの強化は、オプトイン機能です。 これを活用するために、アプリケーションを構成する必要があります。

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a>高 DPI サポートについては、Windows フォーム アプリを構成します。

高 DPI 認識をサポートする新しい Windows フォームの機能は、.NET Framework 4.7 をターゲットし、Windows 10 の作成者の更新で Windows オペレーティング システムで実行されているアプリケーションでのみ使用できます。 

さらに、Windows フォーム アプリケーションで高 DPI サポートを構成するにする必要があります、次のように行います。

- Windows 10 との互換性を宣言します。

  これを行うには、マニフェスト ファイルに、次を追加します。

  ```xml
  <compatibility xmlns="urn:schemas-microsoft.com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- モニターごとの DPI 対応能力を有効にする、 *app.config*ファイル。

  Windows フォームが導入されていますが、新しい[ `<System.Windows.Forms.ApplicationConfigurationSection>` ](../../../docs/framework/configure-apps/file-schema/winforms/index.md)の新機能と .NET Framework 4.7 以降追加のカスタマイズをサポートする要素。 高 DPI をサポートする新しい機能を利用するには、アプリケーション構成ファイルに、次を追加します。   

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>      
  ```
   
  > [!IMPORTANT]
  > .NET Framework の以前のバージョンでは、マニフェストを使用して、高 DPI サポートを追加しました。 このアプローチは推奨されなく、app.config ファイルで定義された設定をオーバーライドするためです。
   
- 静的なを呼び出す<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>メソッドです。
   
  これは、アプリケーションのエントリ ポイントの最初のメソッド呼び出しでなければなりません。 例えば:
   
  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());   
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a>高 DPI 機能を個別の除外

設定、`DpiAwareness`値を`PerMonitorV2`.NET Framework 4.7 以降の .NET Framework バージョンでサポートされている、すべて高 DPI 認識の機能を有効にします。 通常、これはほとんどの Windows フォーム アプリケーションに適しています。 ただし、1 つまたは複数の個々 の機能を除外することがあります。 これを行うための最も重要な理由は、既存のアプリケーション コードは、その機能を既に処理です。  たとえば、アプリケーションでは、自動スケーリングを処理する場合に、次のように自動サイズ変更機能を無効にする可能性があります。

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" /> 
</System.Windows.Forms.ApplicationConfigurationSection>    
```

個々 のキーと値の一覧は、次を参照してください。 [Windows フォームに追加の構成要素](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)です。

## <a name="new-dpi-change-events"></a>新しい DPI の変更イベント

.NET Framework 4.7 以降では、3 つの新しいイベントを使用する動的 DPI の変更をプログラムで処理します。

- <xref:System.Windows.Forms.Control.DpiChangedAfterParent>、コントロールの DPI 設定は、親コントロールの DPI の変更イベントの後にプログラムで変更またはフォームが発生したときに発生します。
- <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>、コントロールの DPI 設定は、親コントロールの DPI の変更イベントの前にプログラムで変更またはフォームが発生したときに発生します。
- <xref:System.Windows.Forms.Form.DpiChanged>、フォームが現在表示されている、ディスプレイ デバイスに DPI 設定が変更されたときに発生します。

## <a name="new-helper-methods-and-properties"></a>新しいヘルパー メソッドとプロパティ

.NET Framework 4.7 では、さまざまな DPI スケーリングに関する情報を提供し、DPI スケールを実行できるようにする新しいヘルパー メソッドとプロパティも追加されます。 次の設定があります。

- <xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>を論理座標から値をデバイス ピクセルに変換します。

- <xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>、デバイスの論理 DPI にビットマップのスケールを設定します。

- <xref:System.Windows.Forms.Control.DeviceDpi%2A>、現在のデバイスの DPI が返されます。

## <a name="versioning-considerations"></a>バージョン管理に関する考慮事項

、.NET Framework 4.7 と Windows 10 の作成者 Update 上だけでなく、アプリケーションがない高 DPI の機能強化と互換性のある環境では実行もします。 この場合、代替のアプリケーションを開発する必要があります。 こうことを実行する[カスタム描画](./controls/user-drawn-controls.md)スケーリングを処理します。

これを行うには、アプリが実行されているオペレーティング システムを決定する必要があります。 次のようなコードを行うことができます。

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

アプリケーションが正常が認識できない Windows 10、アプリケーション マニフェストでサポートされているオペレーティング システムとして表示されていない場合に注意してください。

に対して、アプリケーションが作成されている .NET Framework のバージョンを確認することもできます。

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a>関連項目

[Windows フォームの構成要素を追加します。](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)  
[Windows フォームのサイズとスケールを調整する](../../../docs/framework/winforms/adjusting-the-size-and-scale-of-windows-forms.md)
