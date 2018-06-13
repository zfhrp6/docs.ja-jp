---
title: Windows フォームの構成要素を追加します。
ms.date: 04/07/2017
helpviewer_keywords:
- Windows Forms Add configuration element
- configuring Windows Forms applications
ms.assetid: 3e3e04de-99d1-4658-b716-44cb669d9589
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 529dbccd5ddb4dd1f1456fb9a6043f3c5f7b378d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759661"
---
# <a name="windows-forms-add-configuration-element"></a>Windows フォームの構成要素を追加します。

`<add>`要素は、Windows フォーム アプリが .NET Framework 4.7 以降の Windows フォーム アプリに追加された機能をサポートしているかどうかを指定する定義済みのキーを追加します。

## <a name="syntax"></a>構文

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="key-name" value="key-value" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

## <a name="attributes-and-elements"></a>属性と要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

| 属性 | 説明 |
| --------- | ----------- |
| `key`     | 必須の属性です。 特定の Windows フォームのカスタマイズ可能な機能に対応する定義済みのキー名。 |
| `value`   | 必須の属性です。 代入する値`key`です。 |

### <a name="key-attribute-names-and-associated-values"></a>`key` 属性名と関連付けられている値

| `key` 名 | 値 | 説明 |
| ---------- | ------ | ----------- |
| "AnchorLayout.DisableSinglePassControlScaling" | "true"&#124;"false" | 単一のパスで固定されたコントロールをスケーリングするかどうかを示します。 1 つを無効にするには"true"を渡すスケーリングです。それ以外の場合は false です。 「1 つは、スケーリングを渡す」のセクションを参照して、[解説](#Remarks)詳細についてはします。 |
| "DpiAwareness" | "PerMonitorV2"&#124;"false" | アプリケーションが DPI 対応かどうかを示します。 "PerMonitorV2"Dpi 認識; をサポートするためのキーを設定します。それ以外の場合、"false"に設定します。 DPI 認識は、オプトイン機能です。Windows フォームの高 DPI サポートを利用するには、"PerMonitorV2"には、その値を設定してください。 参照してください、[解説](#remarks)詳細についてはします。 |
| "CheckedListBox.DisableHighDpiImprovements" | "true"&#124;"false" | 示すかどうか、 <xref:System.Windows.Forms.CheckedListBox> .NET Framework 4.7 で導入された機能強化が対応するスケーリングとレイアウトの制御を活用します。 "true"caling とレイアウトの改善; から除外するにはそれ以外の場合、"false"です。 |
| "DataGridView.DisableHighDpiImprovements" | "true"&#124;"false" | 示すかどうか、 <xref:System.Windows.Forms.DataGridView> .NET Framework 4.7 で導入された機能強化が対応するスケーリングとレイアウトを制御します。 "true"DPI 認識; から除外するには"false"それ以外の場合。 |
| "DisableDpiChangedMessageHandling" | "true"&#124;"false" | DPI スケール変更に関連するメッセージを受信しないことを"true""false"それ以外の場合。 参照してください、[解説](#remarks)詳細についてはします。 |
| "EnableWindowsFormsHighDpiAutoResizing" | "true"&#124;"false" | Windows フォーム アプリケーションの DPI スケーリングの変更により自動的にサイズを変更するかどうかを示します。 "true"を自動サイズ変更を有効にするにはそれ以外の場合は false です。 |
| "Form.DisableSinglePassControlScaling" | "true"&#124;"false" | 示すかどうか、<xref:System.Windows.Forms.Form>単一のパスでのスケールが設定されます。 "true"を無効にするシングル パス スケーリングです。それ以外の場合は false です。 「1 つは、スケーリングを渡す」のセクションを参照して、[解説](#Remarks)詳細についてはします。 |
| "MonthCalendar.DisableSinglePassControlScaling" | "true"&#124;"false" | 示すかどうか、<xref:System.Windows.Forms.MonthCalendar>単一のパスでコントロールのスケールを設定します。 "true"を無効にするシングル パス スケーリングです。それ以外の場合は false です。 「1 つは、スケーリングを渡す」のセクションを参照して、[解説](#Remarks)詳細についてはします。 |
| "Toolstrip.DisableHighDpiImprovements" | "true"&#124;"false" | 示すかどうか、 <xref:System.Windows.Forms.ToolStrip> .NET Framework 4.7 で導入された機能強化が対応するスケーリングとレイアウトの制御を活用します。 "true"DPI 認識; から除外するには"false"それ以外の場合。 |

### <a name="child-elements"></a>子要素

なし。

### <a name="parent-elements"></a>親要素

| 要素 | 説明 |
| ------- | ----------- |
| [`<System.Windows.Forms.ApplicationConfigurationSection>`](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md) | 新しい Windows フォーム アプリケーションの機能のサポートを構成します。 |

## <a name="a-nameremarks--remarks"></a><a name="remarks" /> 「解説」

.NET Framework 4.7 を使用すれば、.NET Framework の最近のリリースで追加された機能が利用できる Windows フォームのアプリケーションを、`<System.Windows.Forms.ApplicationConfigurationSection>` 要素で構成できます。 

`<System.Windows.Forms.ApplicationConfigurationSection>`要素では、1 つまたは複数の子を追加することができます`<add>`要素、それぞれが特定の構成設定を定義します。  

Windows フォームの高 DPI サポートの概要については、次を参照してください。 [Windows フォームでの高 DPI サポート](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)です。

### <a name="dpiawareness"></a>DpiAwareness

以降では、.NET Framework 4.7 以降では、Windows 10 の作成者のエディションとターゲットのバージョンの .NET Framework のバージョンの Windows で動作する Windows フォーム アプリケーションは、.NET Framework で導入された高 DPI 改善に活用するために構成することができます。4.7 です。 次の設定があります。

- Windows フォーム アプリケーションの起動後、ユーザー DPI またはスケール ファクターを変更する動的の DPI シナリオをサポートします。

- スケーリングとさまざまな Windows フォームのレイアウトの改善を制御するように、<xref:System.Windows.Forms.MonthCalendar>コントロールと<xref:System.Windows.Forms.CheckedListBox>コントロール。 

高 DPI 認識は、オプトイン機能です。既定では、値`DpiAwareness`は`false`します。 DPI 認識にこのキーの値を設定して Windows フォームのサポートにオプトインできます`PerMonitorV2`アプリケーション構成ファイルにします。 DPI 認識が有効になっている場合、個々 のすべての DPI 機能も有効にします。 次の設定があります。

- DPI によって制御される、メッセージの変更、`DisableDpiChangedMessageHandling`キー。

- 動的な DPI サポートでは、によって制御されます、`EnableWindowsFormsHighDpiAutoResizing`キー。

- シングル パス コントロールがスケーリング、これは制御、`Form.DisableSinglePassControlScaling`個々 の<xref:System.Windows.Forms.Form>制御によって、 `AnchorLayout.DisableSinglePassControlScaling` 、アンカーされたコントロールに、キー、`MonthCalendar.DisableSinglePassControlScaling`のキー、<xref:System.Windows.Forms.MonthCalendar>コントロール 

- 高 DPI スケーリングとレイアウトの向上で制御されている、`CheckListBox.DisableHighDpiImprovements`のキー、<xref:System.Windows.Forms.CheckedListBox>制御によって、`DataGridView.DisableHighDpiImprovements`のキー、<xref:System.Windows.Forms.DataGridView>コントロール、および、`Toolstrip.DisableHighDpiImprovements`のキー、<xref:System.Windows.Forms.ToolStrip>コントロール。  

1 つの既定、オプトインの設定は設定によって提供される`DpiAwareness`に`PerMonitorV2`は新しい Windows フォーム アプリケーションに一般的に適してします。 ただし、し、選択を解除する個々 の高 DPI 機能強化、アプリケーション構成ファイルに対応するキーを追加することによりします。 たとえば、動的 DPI サポートを除くすべての新しい DPI featuers を利用する場合は、アプリケーション構成ファイルには、次を追加します。

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
   <add key="DpiAwareness" value="PerMonitorV2" />
   <--! Disable dynamic DPI support -->
   <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```
通常、オプト アウト、特定の機能をプログラムで処理を選択しているためです。

Windows フォーム アプリケーションで高 DPI サポートの利用の詳細については、次を参照してください。 [Windows フォームでの高 DPI サポート](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)です。
 
### <a name="disabledpichangedmessagehandling"></a>DisableDpiChangedMessageHandling

.NET Framework 4.7 以降、Windows フォーム コントロールは、DPI スケールの変更に関連するイベントの数を発生します。 ように、 <xref:System.Windows.Forms.Control.DpiChangedAfterParent>、 <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>、および<xref:System.Windows.Forms.Form.DpiChanged>イベント。 値、`DisableDpiChangedMessageHandling`キーは、Windows フォーム アプリケーションでこれらのイベントが発生したかどうかを判断します。 

### <a name="single-pass-scaling"></a>シングルパスのスケーリング

調整ので、ユーザー インターフェイスの見かけ上の応答性とユーザー インターフェイス要素の外観に影響 1 つまたは複数のパスをスケーリングします。 .NET Framework 4.7 以降、Windows フォームは、1 つのパスのスケーリングします。 .NET Framework の以前のバージョンでのスケーリングが必要以上にスケールする一部のコントロールの原因となる、複数のパスを通じて実行されました。 アプリは、従来の動作に依存する場合、単一パス scaling を無効のみ必要があります。  

## <a name="see-also"></a>関連項目
 
[Windows フォームの構成 セクション](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md)   
[Windows フォームの高 DPI サポート](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
