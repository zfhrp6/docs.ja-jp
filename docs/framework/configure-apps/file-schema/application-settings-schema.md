---
title: アプリケーション設定スキーマ
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7af6342e9c05fc4e6c1bf4daac59db14ccdf22c7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="application-settings-schema"></a>アプリケーション設定スキーマ

アプリケーションの設定を保存し、アプリケーション スコープ設定し、ユーザー スコープ設定を取得する Windows フォームまたは ASP.NET アプリケーションを許可します。 このコンテキストで、*設定*のアプリケーション固有または現在のユーザーに特定できる情報は、-ユーザーにデータベース接続文字列から何かの既定のウィンドウ サイズを優先します。

既定では、Windows フォーム アプリケーションにおけるアプリケーションの設定を使用して、<xref:System.Configuration.LocalFileSettingsProvider>クラスは、.NET 構成システムを使用して、XML 構成ファイルに設定を格納します。 アプリケーションの設定で使用されるファイルの詳細については、次を参照してください。[アプリケーション設定アーキテクチャ](~/docs/framework/winforms/advanced/application-settings-architecture.md)です。

アプリケーションの設定は、使用して、構成ファイルの一部として、次の要素を定義します。

| 要素                    | 説明                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings >** | すべてを含む**\<設定 >** タグはアプリケーションに固有です。                         |
| **\<ユーザー >**        | すべてが含まれます**\<設定 >** タグは、現在のユーザーを特定します。                        |
| **\<設定 >**             | 設定を定義します。 いずれかの子 **\<applicationSettings >** または**\<ユーザー >** です。 |
| **\<value>**               | 設定の値を定義します。 子**\<設定 >** です。                                   |

## <a name="applicationsettings-element"></a>\<applicationSettings > 要素

この要素には、すべてが含まれています**\<設定 >** タグは、クライアント コンピューターにアプリケーションのインスタンスに固有です。 属性は定義されません。

## <a name="usersettings-element"></a>\<ユーザー > 要素

この要素には、すべてが含まれています**\<設定 >** アプリケーションが現在使用しているユーザーに固有のタグ。 属性は定義されません。

## <a name="setting-element"></a>\<設定 > 要素

この要素は、設定を定義します。 次の属性があります。

| 属性        | 説明 |
| ---------------- | ----------- |
| **name**         | 必須。 設定の一意の ID。 Visual Studio で作成した設定は、名前で保存`ProjectName.Properties.Settings`です。 |
| **serializedAs** | 必須。 テキスト値をシリアル化するために使用する形式。 次の値を指定できます。<br><br>- `string`. 使用して文字列として値がシリアル化、<xref:System.ComponentModel.TypeConverter>です。<br>- `xml`. XML シリアル化を使用して、値がシリアル化されます。<br>- `binary`. 値は、バイナリのシリアル化を使用して、テキスト エンコードされたバイナリとしてシリアル化します。<br />- `custom`. 設定プロバイダーは、この設定の固有の情報しシリアル化し、逆シリアル化されます。 |

## <a name="value-element"></a>\<値 > 要素

この要素には、設定の値が含まれています。

## <a name="example"></a>例

次の例では、2 つのアプリケーション スコープ設定と 2 つのユーザー スコープ設定を定義するアプリケーションの設定ファイルを示します。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
    </sectionGroup>
    <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
    </sectionGroup>
  </configSections>
  <applicationSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="Cursor" serializeAs="String">
        <value>Default</value>
      </setting>
      <setting name="DoubleBuffering" serializeAs="String">
        <value>False</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </applicationSettings>
  <userSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="FormTitle" serializeAs="String">
        <value>Form1</value>
      </setting>
      <setting name="FormSize" serializeAs="String">
        <value>595, 536</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </userSettings>
</configuration>
```

## <a name="see-also"></a>関連項目

[アプリケーション設定の概要](~/docs/framework/winforms/advanced/application-settings-overview.md)   
[アプリケーション設定アーキテクチャ](~/docs/framework/winforms/advanced/application-settings-architecture.md)
