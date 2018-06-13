---
title: SingleTagSectionHandler のカスタム要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 07bc0d9560546f4946d34413697fb0adcf84c58d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743278"
---
# <a name="custom-element-for-singletagsectionhandler"></a>SingleTagSectionHandler のカスタム要素

定義されているカスタム構成セクションの設定を定義します。 <section> 要素と使用、<xref:System.Configuration.SingleTagSectionHandler>クラスです。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;*\<sectionName>*

## <a name="syntax"></a>構文

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a>属性

属性および属性値は、ユーザー定義を示します。

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ----------- |
| [**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | 共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。 |

## <a name="child-elements"></a>子要素

なし

## <a name="remarks"></a>コメント

**\<SectionName >** 要素は、カスタムの要素によって定義された、 [ **\<セクション >** ](~/docs/framework/configure-apps/file-schema/section-element.md)にタグを付ける、 [ **\<configSections >** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)要素。 構成システムを返します、<xref:System.Collections.IDictionary>オブジェクトを呼び出すとき<xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>です。

## <a name="example"></a>例

次の例と呼ばれるカスタム要素の宣言 **\<sampleSection >** によって読み取られた設定を格納している、<xref:System.Configuration.SingleTagSectionHandler>クラス。

```xml
<configuration>
  <configSections>
    <section name="sampleSection" 
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>構成ファイル

この要素は、アプリケーション構成ファイル、マシン構成ファイルで使用できます (*Machine.config*)、および*Web.config*アプリケーション ディレクトリ レベルではないファイル。

## <a name="see-also"></a>関連項目

[.NET Framework の構成ファイル スキーマ](~/docs/framework/configure-apps/file-schema/index.md)
