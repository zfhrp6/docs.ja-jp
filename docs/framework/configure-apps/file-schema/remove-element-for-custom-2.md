---
title: '&lt;削除&gt;NameValueSectionHandler と DictionarySectionHandler 要素'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 61f1c98d3f12b5aa1d25595ca28328602683b073
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742914"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<削除 > NameValueSectionHandler と DictionarySectionHandler 要素

以前に定義された設定を削除します。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<sectionName >**](~/docs/framework/configure-apps/file-schema/custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<削除 >**

## <a name="syntax"></a>構文

```xml
<add remove="key" />
```

## <a name="attribute"></a>属性

|           | 説明 |
| --------- | ----------- |
| **key**   | 必須の属性です。<br><br>削除する設定の名前を指定します。 |

## <a name="parent-element"></a>親要素

| 要素 | 説明 |
| ------- | ------------|
| [**\<sectionName >** 要素](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | 使用するカスタム構成セクションの設定を定義、<xref:System.Configuration.NameValueSectionHandler>と<xref:System.Configuration.DictionarySectionHandler>クラスです。 |

## <a name="child-elements"></a>子要素

なし

## <a name="remarks"></a>コメント

使用することができます、 **\<削除 >** 構成ファイルの階層内の上位レベルで定義されているアプリケーションから設定を削除する要素。

## <a name="example"></a>例

次の例を使用する方法を示しています、 **\<削除 >** マシン構成ファイルで定義済みの設定を削除するアプリケーション構成ファイル内の要素。

マシン構成ファイルのコードは、次のセクションを宣言して **\<mySection >** し、2 つの設定を追加`key1`と`key2`に。

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

アプリケーション構成ファイルのコードは、次の削除、`key2`設定から **\<mySection >**:

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>構成ファイル

この要素は、アプリケーション構成ファイル、マシン構成ファイルで使用できます (*Machine.config*)、および*Web.config*アプリケーション ディレクトリ レベルではないファイル。

## <a name="see-also"></a>関連項目

[.NET Framework の構成ファイル スキーマ](~/docs/framework/configure-apps/file-schema/index.md)
