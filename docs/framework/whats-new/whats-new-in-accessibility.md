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
# <a name="whats-new-in-accessibility-in-the-net-framework"></a>.NET Framework のアクセシビリティの新機能

.NET Framework では、ユーザーのためにアプリケーションのアクセシビリティ向上を目指しています。 ユーザー補助機能により、支援機能の利用者にとってアプリケーションがさらに使いやすくなります。 .NET Framework 4.7.1 以降、.NET Framework にはさまざまなアクセシビリティ拡張機能が含まれるようになりました。それを利用することで開発者はアクセシビリティを備えたアプリケーションを開発できます。 

.NET Framework 4.7.1 以降を対象とするアプリケーションでは、この新しいユーザー補助機能が既定で有効になっています。 また、初期の .NET Framework を対象としているが、.NET Framework 4.7.1 以降で実行されているアプリケーションの場合、古いアクセシビリティ動作を利用しないことを選択できます (.NET Framework 4.7.1 のアクセシビリティ拡張機能の利用を選択します)。その場合、アプリケーションの設定ファイルの [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) セクションで次のスイッチを [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 要素に追加してください。 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

同様に、4.7.1 以降の .NET Framework を対象にしているアプリケーションではアクセシビリティ機能を無効にできます。その場合、アプリケーションの設定ファイルの [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) セクションで次のスイッチを [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 要素に追加してください。 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a>.NET Framework 4.7.1 のアクセシビリティの新機能

.NET Framework 4.7.1 には、次の領域の新しいアクセシビリティ機能が含まれています。

- [Windows Presentation Foundation (WPF)](#windows-presentation-foundation-wpf)

- [Windows フォーム](#windows-forms-accessibility-improvements)

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**スクリーン リーダーの機能強化**

アクセシビリティ拡張機能を有効にすると、.NET Framework 4.7.1 は次の面でスクリーン リーダーの機能を強化します。

- .NET Framework 4.7 以前のバージョンでは、スクリーン リーダーが <xref:System.Windows.Controls.Expander> コントロールをボタンとして読み上げました。 .NET Framework 4.7.1 以降では、展開と折りたたみが可能なグループとして正しく読み上げられます。

- .NET Framework 4.7 以前のバージョンの場合、スクリーン リーダーが <xref:System.Windows.Controls.DataGridCell> コントロールを “カスタム” として読み上げました。 .NET Framework 4.7.1 以降では、データ グリッド セル (ローカライズされます) として正しく読み上げられます。
 
- .NET Framework 4.7.1 以降、スクリーン リーダーは編集可能な <xref:System.Windows.Controls.ComboBox> の名前を読み上げます。

- .NET Framework 4.7 以前のバージョンの場合、<xref:System.Windows.Controls.PasswordBox> コントロールが “ビューに項目がありません” として読み上げられたか、他の誤動作が発生しました。 この問題は .NET Framework 4.7.1 以降で修正されています。     

**UIAutomation LiveRegion サポート**

ナレーターなどのスクリーン リーダーはアプリケーションの UI コンテンツをユーザーのために読み上げます。通常、フォーカスを合わせた UI コンテンツのテキストが読み上げられます。 ただし、UI 要素が変わり、フォーカスがなくなったとき、ユーザーに通知されず、重要な情報を逃すことがあります。 ライブ領域は、この問題の解決を目指しています。 開発者はこれを利用し、UI 要素が大幅に変更されたことをスクリーン リーダーやその他の UIAutomation クライアントに指示できます。 指示後、スクリーン リーダーでは、その変更をユーザーに通知する方法とタイミングが決定されます。 

ライブ領域をサポートするために、次の API が WPF に追加されました。

- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> フィールドと <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> フィールド。**LiveSetting** プロパティと **LiveRegionChanged** イベントを識別します。 XAML を利用して設定できます。

- **AutomationProperties.LiveSetting** 添付プロパティ。UI の変化がユーザーにとって重要であることをスクリーン リーダーに伝えます。

- <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> プロパティ。**AutomationProperties.LiveSetting** 添付プロパティを識別します。
 
- <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> メソッド。**LiveSetting** 値を提供するようにオーバーライドできます。

- <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> メソッドと <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> メソッド。**LiveSetting** 値を取得し、設定します。
 
- <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> 列挙。次の指定可能 **LiveSetting** 値を定義します。

   - <xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>。 ライブ領域の内容が変更された場合でも、要素が通知を送信することはありません。   
   - <xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>。 ライブ領域の内容が変更された場合、要素は非割り込み型の通知を送信します。   

  - <xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>。 ライブ領域の内容が変更された場合、要素により割り込み通知が送信されます。   

関心のある要素で **AutomationProperties.LiveSetting** プロパティを作成できます。次の例をご覧ください。   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

ライブ領域のデータが変化し、スクリーン リーダーに通知する必要があれば、次のサンプルのように、明示的にイベントを発生させます。

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

**ハイ コントラスト**

.NET Framework 4.7.1 以降、さまざまな WPF コントロールでハイ コントラストが強化されました。 <xref:System.Windows.SystemParameters.HighContrast%2A> テーマが設定されているときにこれを確認できます。 次の設定があります。

- <xref:System.Windows.Controls.Expander> コントロール

    フォーカスを合わせたとき、<xref:System.Windows.Controls.Expander> コントロールが見やすくなりました。 <xref:System.Windows.Controls.ComboBox>、<xref:System.Windows.Controls.ListBox>、<xref:System.Windows.Controls.RadioButton> コントロールのキーボードも見やすくなりました。 例:

    前: 
    
    ![フォーカスを合わせた Expander コントロール (アクセシビリティ機能改善前)](media/expander-before.png)

    後: 

    ![フォーカスを合わせた Expander コントロール (アクセシビリティ機能改善後)](media/expander-after.png)

- <xref:System.Windows.Controls.CheckBox> コントロールと <xref:System.Windows.Controls.RadioButton> コントロール
 
    <xref:System.Windows.Controls.CheckBox> コントロールと <xref:System.Windows.Controls.RadioButton> コントロールのテキストは、ハイ コントラスト テーマで選択されているとき、見やすくなりました。 例:

    前: 

    ![フォーカスを合わせたハイ コントラストのラジオ ボタン (アクセシビリティ機能改善前)](media/radio-button-before.png)
    
    後: 

    ![フォーカスを合わせたハイ コントラストのラジオ ボタン (アクセシビリティ機能改善後)](media/radio-button-after.png)

- <xref:System.Windows.Controls.ComboBox> コントロール
 
    .NET Framework 4.7.1 以降、無効にした <xref:System.Windows.Controls.ComboBox> コントロールの枠線が無効にしたテキストと同じ色になります。 例:
    
    前: 

     ![無効にした ComboBox の枠線とテキスト (アクセシビリティ機能改善前)](media/combo-disabled-before.png)

    後:   

     ![無効にした ComboBox の枠線とテキスト (アクセシビリティ機能改善後)](media/combo-disabled-after.png)

    また、無効にしているボタンにフォーカスを合わせたとき、正しいテーマ色が使用されます。

    前:

    ![ボタンのテーマ色 (アクセシビリティ機能改善前)](media/button-themes-before.png) 
    
    後: 

    ![ボタンのテーマ色 (アクセシビリティ機能改善後)](media/button-themes-after.png) 

    最後になりますが、.NET Framework 4.7 以前のバージョンでは、<xref:System.Windows.Controls.ComboBox> コントロールのスタイルを `Toolbar.ComboBoxStyleKey` に設定すると、ドロップダウンの矢印が見えなくなりました。 この問題は .NET Framework 4.7.1 以降で修正されています。 例:

    前: 

    ![Toolbar.ComboBoxStyleKey (アクセシビリティ機能改善前)](media/comboboxstylekey-before.png) 
    
    後: 

    ![Toolbar.ComboBoxStyleKey (アクセシビリティ機能改善後)](media/comboboxstylekey-after.png) 

- <xref:System.Windows.Controls.DataGrid> コントロール

    .NET Framework 4.7.1 以降、<xref:System.Windows.Controls.DataGrid> コントロールの並べ替えインジケーターで正しいテーマ色が使われるようになりました。 例:

    前: 

    ![並べ替えインジケーターの矢印 (アクセシビリティ機能改善前)](media/sort-indicator-before.png) 
    
    後:   
 
    ![並べ替えインジケーターの矢印 (アクセシビリティ機能改善後)](media/sort-indicator-after.png) 
    
    また、.NET Framework 4.7 以前のバージョンでは、ハイ コントラスト モードでカーソルを合わせたとき、既定のリンク スタイルが正しくない色に変化しました。 これは .NET Framework 4.7.1 以降で修正されています。 同様に、.NET Framework 4.7.1 以降、<xref:System.Windows.Controls.DataGrid> チェックボックス列でキーボード フォーカス フィードバックに既定の色が使用されます。

    前: 

    ![DataGrid の既定のリンク スタイル (アクセシビリティ機能改善前)](media/default-link-style-before.png) 
 
    後:    
  
    ![DataGrid の既定のリンク スタイル (アクセシビリティ機能改善後)](media/default-link-style-after.png)  

.NET Framework 4.7.1 のアクセシビリティ機能の改善の詳細については、「[Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf)」 (WPF のアクセシビリティ機能改善) を参照してください。

## <a name="windows-forms-accessibility-improvements"></a>Windows フォームのアクセシビリティ機能改善

.NET Framework 4.7.1 では、Windows フォーム (WinForms) のアクセシビリティが次の領域で変更されました。

**ハイ コントラスト モードの表示が改善されました**

.NET Framework 4.7.1 以降では、オペレーティング システムで利用できるハイ コントラスト モードを選択したとき、さまざまな WinForms コントロールの表示が改善されました。 Windows 10 では、ハイ コントラストのシステム色の一部で値が変わりました。Windows フォームは Windows 10 Win32 フレームワークに基づきます。 最も快適に利用するためには、最新版の Windows で実行し、テスト アプリケーションに app.manifest ファイルを追加して最新の OS 変更を選択し、次の画像のように Windows 10 対応 OS 行のコメントを解除します。

```xml
<!– Windows 10 –>
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
ハイ コントラストの変更例:

- <xref:System.Windows.Forms.MenuStrip> 項目のチェックマークが見やすくなりました。

- 選択したとき、無効になっている <xref:System.Windows.Forms.MenuStrip> 項目が見やすくなりました。

- 選択した <xref:System.Windows.Forms.Button> コントロールのテキストが背景色に対して際立ち、見やすくなりました。

- 無効になっているテキストが読みやすくなりました。 例:

    前:

    ![無効にしたテキスト (アクセシビリティ機能改善前)](media/wf-disabled-before.png) 

    後:

    ![無効にしたテキスト (アクセシビリティ機能改善後)](media/wf-disabled-after.png) 

- スレッド例外ダイアログのハイ コントラストが改善されました。

**ナレーター サポートが改善されました**

.NET Framework 4.7.1 の Windows フォームでは、ナレーターのアクセシビリティが次の面で改善されました。

- <xref:System.Windows.Forms.MonthCalendar> コントロールに、他の UI 自動化ツールと同様に、ナレーターからアクセスできます。

- <xref:System.Windows.Forms.CheckedListBox> コントロールは、項目のチェック状態が変わったとき、ナレーターに通知します。その結果、リスト アイテムの値を変えたことがユーザーに通知されます。
 
- <xref:System.Windows.Forms.DataGridViewCell> コントロールは正しい読み取り専用状態をナレーターに報告します。
 
- ナレーターが無効になっている <xref:System.Windows.Forms.ToolStripMenuItem> テキストを読み上げるようになりました。以前は、無効になっているメニュー項目はスキップされました。

**UIAutomation アクセシビリティ パターンのサポートが強化されました**

.NET Framework 4.7.1 以降、アクセシビリティ技術ツールの開発者は、一部の WinForms コントロールについて、API アクセシビリティの共通のパターンとプロパティを活用できます。 アクセシビリティ機能改善の例:

- <xref:System.Windows.Forms.ComboBox> と <xref:System.Windows.Forms.ToolStripSplitButton> が[展開/折りたたみパターン](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)対応になりました。
 
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell> が[切り替えパターン](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md)対応になりました。
 
- <xref:System.Windows.Forms.ToolStripItem> コントロールが <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> プロパティと[展開/折りたたみパターン](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)対応になりました。

- <xref:System.Windows.Forms.NumericUpDown> コントロールと <xref:System.Windows.Forms.DomainUpDown> コントロールが <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> プロパティ対応になりました。

**プロパティ ブラウザーが使いやすくなりました**

.NET Framework 4.7.1 以降、Windows フォームは次の点で改善されました。

- さまざまなドロップダウン選択ウィンドウを利用することでキーボード操作が便利になりました。
- 不要なタブ ストップが減りました。
- コントロールの種類の報告機能が改善されました。
- ナレーターの動作が改善されました。
 
## <a name="see-also"></a>参照
[.NET Framework の新機能](whats-new.md)   
 