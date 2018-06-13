---
title: '&lt;追加&gt;NameValueSectionHandler と DictionarySectionHandler 要素'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: guardrex
ms.author: mairaw
ms.openlocfilehash: aeb3e3a4be201369ca2df8d231498dd2400d3c07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361372"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<追加 > NameValueSectionHandler と DictionarySectionHandler 要素

カスタム アプリケーションの設定を追加します。 各**\<追加 >** タグには、キー/値ペアが含まれています。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<sectionName >**](~/docs/framework/configure-apps/file-schema/custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<追加 >**

## <a name="syntax"></a>構文

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a>属性

| 属性 | 説明 |
| --------- | ----------- |
| **key**   | 必須の属性です。<br><br>設定の名前を指定します。 |
| **value** | 必須の属性です。<br><br>設定の値を指定します。 |

## <a name="parent-element"></a>親要素

| 要素 | 説明 |
| ------- | ------------|
| [**\<sectionName >** 要素](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | 使用するカスタム構成セクションの設定を定義、<xref:System.Configuration.NameValueSectionHandler>と<xref:System.Configuration.DictionarySectionHandler>クラスです。 |

## <a name="child-elements"></a>子要素

なし

## <a name="example"></a>例

次の例は、カスタム構成セクションを定義および使用する方法を示しています、 **\<追加 >** セクションに設定を追加する要素。

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
</configuration>
```

## <a name="configuration-file"></a>構成ファイル

この要素は、アプリケーション構成ファイル、マシン構成ファイルで使用できます (*Machine.config*)、および*Web.config*アプリケーション ディレクトリ レベルではないファイル。

## <a name="see-also"></a>関連項目

[.NET Framework の構成ファイル スキーマ](~/docs/framework/configure-apps/file-schema/index.md)
