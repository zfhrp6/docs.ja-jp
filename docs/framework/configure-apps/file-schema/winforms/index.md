---
title: "Windows フォームの構成セクション"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
ms.workload: dotnet
ms.openlocfilehash: f2d83f5dcf6fa93ceba4d670470bd768a2ee1f88
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-configuration-section"></a>Windows フォームの構成セクション
Windows フォームの構成設定により、カスタマイズされたアプリケーション設定に関する情報 (マルチ モニターや高 DPI のサポート、その他の定義済みの構成設定など) を Windows フォームのアプリで格納したり、取得したりできます。

Windows フォームのアプリケーション構成設定は、アプリケーション構成ファイルの `System.Windows.Forms.ApplicationConfigurationSection` 要素に格納されます。

## <a name="syntax"></a>構文

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a>属性と要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

なし。

### <a name="child-elements"></a>子要素

要素  |説明 |
---------|---------|
[`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) | 指定した値を持つ構成設定キーを追加します |

### <a name="parent-elements"></a>親要素

要素  |説明 |
---------|---------|
[\<configuration>](../configuration-element.md) | 共通言語ランタイムと Windows フォームのアプリケーションで使用されるすべての構成ファイルのルート要素です |

## <a name="remarks"></a>コメント

.NET Framework 4.7 を使用すれば、.NET Framework の最近のリリースで追加された機能が利用できる Windows フォームのアプリケーションを、`<System.Windows.Forms.ApplicationConfigurationSection>` 要素で構成できます。 

`<System.Windows.Forms.ApplicationConfigurationSection>` 要素には 1 つまたは複数の子の [`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) 要素を含めることができ、各要素には特定の構成設定が定義されます。

## <a name="see-also"></a>関連項目

[構成ファイル スキーマ](../index.md)   
[Windows フォームの高 DPI サポート](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
