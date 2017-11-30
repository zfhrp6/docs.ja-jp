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
# <a name="whats-new-in-accessibility-in-the-net-framework"></a>.NET Framework のユーザー補助機能の新機能

.NET Framework の目的のユーザー用の複数の補助アプリケーションを作成します。 ユーザー補助機能は、支援技術のユーザーに適切なエクスペリエンスを提供するアプリケーションを許可します。 以降、.NET Framework 4.7.1 では、.NET Framework には、多数ユーザー補助アプリケーションを作成するためのアクセシビリティの機能強化にはが含まれています。 

新しいユーザー補助機能は、既定では、.NET Framework 4.7.1 を対象とするアプリケーションを有効になっている以降です。 さらに、アプリケーション、.NET Framework の以前のバージョンをターゲットが .NET Framework 4.7.1 で実行されているまたは後で選択できますレガシ ユーザー補助機能の動作の出力 (およびこれにより、.NET Framework 4.7.1 のユーザー補助機能強化にオプトイン) によって次のスイッチを追加する、 [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)内の要素、 [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md)アプリケーションの構成ファイルのセクションです。 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

以降 4.7.1 で .NET Framework のバージョンを対象とするアプリケーションがユーザー補助機能を無効にする次のスイッチを追加することで同様に、 [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)内の要素、 [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md)アプリケーションの構成ファイルのセクションです。 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a>.NET Framework 4.7.1 のユーザー補助機能の新機能

.NET Framework 4.7.1 には、次の領域の新しいユーザー補助機能が含まれます。

- [Windows Presentation Foundation (WPF)](#windows-presentation-foundation-wpf)

- [Windows フォーム](#windows-forms-accessibility-improvements)

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**スクリーン リーダーの強化**

ユーザー補助機能強化が有効な場合、.NET Framework 4.7.1 には、スクリーン リーダーに影響する次の機能強化が含まれています。

- .NET Framework 4.7 と以前のバージョンで<xref:System.Windows.Controls.Expander>ボタンとして画面リーダーによってコントロールが発表されました。 .NET Framework 4.7.1 から始めて、展開/折りたたみ可能なグループとして正しく読み上げられます。

- .NET Framework 4.7 と以前のバージョンで<xref:System.Windows.Controls.DataGridCell>コントロールがスクリーン リーダーで"custom"に発表されました。 .NET Framework 4.7.1 から始めて、今すぐ正しく読み上げられます (ローカライズされた) データ グリッドのセルとして。
 
- .NET Framework 4.7.1 から始めて、スクリーン リーダー アナウンスの編集可能な名前<xref:System.Windows.Controls.ComboBox>です。

- .NET Framework 4.7 と以前のバージョンで<xref:System.Windows.Controls.PasswordBox>コントロール「ビューのアイテムがありません」として発表されたがそれ以外の場合に不適切な動作です。 この問題は、.NET Framework 4.7.1 以降では固定です。     

**UIAutomation LiveRegion サポート**

ナレーター ヘルプ人などのスクリーン リーダーは、フォーカスのある UI コンテンツの音声合成の出力で通常、アプリケーションの UI の内容を読み取る。 ただし、UI 要素が変更が、フォーカスされていない場合、ユーザーは通知されない場合があり、重要な情報を見逃す可能性があります。 この問題の解決を目的としてライブ領域。 開発者は、スクリーン リーダーや UI 要素に重要な変更が行われたその他の任意の UIAutomation クライアントを通知するためにそれらを使用できます。 スクリーン リーダー方法とタイミングを決定できますし、この変更のユーザーに通知します。 

領域をサポートするライブ、WPF に次の Api が追加されました。

- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType>と<xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType>、識別フィールド、 **LiveSetting**プロパティおよび**LiveRegionChanged**イベント。 これらは、XAML を使用して設定できます。

- **AutomationProperties.LiveSetting**添付プロパティで、ユーザーに、UI の変更の重要度のスクリーン リーダーに通知します。

- <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType>プロパティを識別する、 **AutomationProperties.LiveSetting**添付プロパティ。
 
- <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType>できますをオーバーライドするメソッド、 **LiveSetting**値。

- <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType>と<xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType>get し、set メソッド、 **LiveSetting**値。
 
- <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>列挙体は、次の考えられる定義**LiveSetting**値。

   - <xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>。 要素は、ライブの領域の内容が変更された場合、通知を送信しません。   
   - <xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>。 ライブ領域の内容が変更された場合、要素は非割り込み型の通知を送信します。   

  - <xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>。 ライブ領域の内容が変更された場合、要素により割り込み通知が送信されます。   

設定して、LiveRegion を作成することができます、 **AutomationProperties.LiveSetting**次の例で示すように、目的の要素のプロパティ。   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

ライブ領域内のデータを変更すると、スクリーン リーダーに通知する必要がありますを明示的にイベントを発生させる、次の例に示すようにします。

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

**ハイ コントラスト**

.NET Framework 4.7.1 から始めて、ハイ コントラストの機能強化に加えられたさまざまな WPF コントロールです。 これは表示されているときに、<xref:System.Windows.SystemParameters.HighContrast%2A>テーマを設定します。 以下に例を示します。

- <xref:System.Windows.Controls.Expander> コントロール

    ビジュアルをフォーカス、<xref:System.Windows.Controls.Expander>コントロールが表示されるようになりました。 キーボードのビジュアルの<xref:System.Windows.Controls.ComboBox>、<xref:System.Windows.Controls.ListBox>、および<xref:System.Windows.Controls.RadioButton>コントロールがも表示されます。 例:

    前: 
    
    ![ユーザー補助機能を強化する前にフォーカスを持つ expander コントロール](media/expander-before.png)

    後。 

    ![ユーザー補助機能強化の後にフォーカスを持つ expander コントロール](media/expander-after.png)

- <xref:System.Windows.Controls.CheckBox>および<xref:System.Windows.Controls.RadioButton>コントロール
 
    内のテキスト、<xref:System.Windows.Controls.CheckBox>と<xref:System.Windows.Controls.RadioButton>コントロールは、ハイ コントラスト テーマで選択するとわかりやすくようになりました。 例:

    前: 

    ![ユーザー補助機能を強化する前にフォーカスがあるハイ コントラストのラジオ ボタン](media/radio-button-before.png)
    
    後。 

    ![ユーザー補助機能強化の後にフォーカスがあるハイ コントラストのラジオ ボタン](media/radio-button-after.png)

- <xref:System.Windows.Controls.ComboBox> コントロール
 
    .NET Framework 4.7.1、無効なの枠線で始まる<xref:System.Windows.Controls.ComboBox>コントロールが無効なテキストと同じ色。 例:
    
    前: 

     ![コンボ ボックスには、罫線とユーザー補助機能を強化する前にテキストが無効になっています](media/combo-disabled-before.png)

    後。   

     ![コンボ ボックスはユーザー補助機能強化の後に罫線とテキストを無効にします。](media/combo-disabled-after.png)

    さらに、無効になっており、フォーカスされたボタンは、適切なテーマの色を使用します。

    前:

    ![ユーザー補助機能を強化する前にボタンのテーマの色](media/button-themes-before.png) 
    
    後。 

    ![ユーザー補助機能強化の後にボタンのテーマの色](media/button-themes-after.png) 

    .NET Framework 4.7 と設定、以前のバージョンで最後に、<xref:System.Windows.Controls.ComboBox>コントロールのスタイルを`Toolbar.ComboBoxStyleKey`ドロップダウン矢印を表示しない原因となった。 この問題は、.NET Framework 4.7.1 以降では固定です。 例:

    前: 

    ![ユーザー補助機能を強化する前に Toolbar.ComboBoxStyleKey](media/comboboxstylekey-before.png) 
    
    後。 

    ![ユーザー補助機能強化後 Toolbar.ComboBoxStyleKey](media/comboboxstylekey-after.png) 

- <xref:System.Windows.Controls.DataGrid> コントロール

    .NET Framework 4.7.1、並べ替えのインジケーターの矢印で始まる<xref:System.Windows.Controls.DataGrid>これで、使用して解決テーマの色を制御します。 例:

    前: 

    ![ユーザー補助機能を強化する前に並べ替えインジケーターの矢印](media/sort-indicator-before.png) 
    
    後。   
 
    ![ユーザー補助機能強化の後に並べ替えインジケーターの矢印](media/sort-indicator-after.png) 
    
    さらに、.NET Framework 4.7 以前のバージョンで、リンクの既定のスタイル内に変更マウス上の正しくない色経由でハイ コントラスト モード。 これは、.NET Framework 4.7.1 以降の解決。 同様に、 <xref:System.Windows.Controls.DataGrid>  チェック ボックス列がキーボード フォーカス フィードバックについては、.NET Framework 4.7.1 以降の色を使用します。

    前: 

    ![ユーザー補助機能を強化する前に既定のリンクのスタイルを DataGrid](media/default-link-style-before.png) 
 
    後。    
  
    ![ユーザー補助機能強化の後に既定のリンクのスタイルを DataGrid](media/default-link-style-after.png)  

.NET Framework 4.7.1 の WPF ユーザー補助機能強化の詳細については、次を参照してください。 [WPF のユーザー補助機能の強化](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf)です。

## <a name="windows-forms-accessibility-improvements"></a>Windows フォームのユーザー補助機能強化

.NET framework 4.7.1 では、Windows フォーム (WinForms) には、次の領域でユーザー補助機能の変更が含まれています。

**ハイ コントラスト モードで表示を改善しました**

以降、.NET Framework 4.7.1 では、さまざまな WinForms コントロールは、オペレーティング システムで使用できるハイコントラスト モードで向上のレンダリングを提供します。 Windows 10 には、ハイ コントラスト システムの一部の色の値が変更されており、Windows フォームは、Windows 10 の Win32 framework に基づいています。 最良の結果は、最新バージョンの Windows で実行し、テスト アプリケーションとコメントを解除して Windows 10 で、アプリケーション マニフェスト ファイルに OS 行がサポートされている場合に、次を追加して、OS の最新の変更を有効します。

```xml
<!– Windows 10 –>
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
ハイ コントラストの変更の例をいくつかは次のとおりです。

- チェック マーク<xref:System.Windows.Forms.MenuStrip>項目は簡単に表示します。

- 選択した場合は、次の無効になっています。<xref:System.Windows.Forms.MenuStrip>項目は簡単に表示します。

- 選択したテキスト<xref:System.Windows.Forms.Button>選択範囲の色とコントラストを制御します。

- 無効な文字が読みやすくします。 例:

    前:

    ![ユーザー補助機能を強化する前に無効なテキスト](media/wf-disabled-before.png) 

    後。

    ![ユーザー補助機能強化の後に無効なテキスト](media/wf-disabled-after.png) 

- スレッドの例外ダイアログ ボックスでハイ コントラストの向上。

**ナレーターのサポートの強化**

.NET Framework 4.7.1 での Windows フォームには、ナレーターの次のユーザー補助機能強化が含まれています。

- <xref:System.Windows.Forms.MonthCalendar>コントロールは、ナレーターおよび他の UI オートメーション ツールでアクセスできます。

- <xref:System.Windows.Forms.CheckedListBox>コントロールがユーザーに通知するリスト項目の値を変更したこと、アイテムのチェック状態が変化したときに、ナレーターを通知します。
 
- <xref:System.Windows.Forms.DataGridViewCell>コントロールは、ナレーターに正しい読み取り専用ステータスをレポートします。
 
- ナレーターは、無効を読み取ることができるようになりました<xref:System.Windows.Forms.ToolStripMenuItem>テキスト、無効なメニュー項目をスキップは、以前はします。

**UIAutomation アクセシビリティ パターンのサポートの強化**

.NET Framework 4.7.1 から始めて、API ユーザー補助機能の一般的なパターンといくつかの WinForms コントロールのプロパティをユーザー補助テクノロジのツールの開発者は利用できます。 これらのユーザー補助機能強化は次のとおりです。

- <xref:System.Windows.Forms.ComboBox>と<xref:System.Windows.Forms.ToolStripSplitButton>ようになりました、[展開/折りたたみパターン](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)です。
 
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell>ようになりました、[トグル パターン](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md)です。
 
- <xref:System.Windows.Forms.ToolStripItem>サポート、<xref:System.Windows.Automation.AutomationElement.Name>プロパティおよび[展開/折りたたみパターン](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)です。

- <xref:System.Windows.Forms.NumericUpDown>と<xref:System.Windows.Forms.DomainUpDown>のサポートを制御、<xref:System.Windows.Automation.automationElement.Name>プロパティです。

**ブラウザー エクスペリエンスの向上プロパティ**

以降、.NET Framework 4.7.1 では、Windows フォームが含まれています。

- さまざまなドロップダウン選択ウィンドウをキーボード ナビゲーション機能が向上します。
- 不要なタブの削減を停止します。
- コントロールの種類の報告が改善します。
- ナレーターの強化された動作です。
 
## <a name="see-also"></a>関連項目
[.NET Framework の新機能](whats-new.md)   
 