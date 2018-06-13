---
title: '&lt;削除&gt;要素&lt;configSections&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 6555981edeb6f7f088fb12c710d0146cf58d5be1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752417"
---
# <a name="remove-element-for-configsections"></a>\<削除 > 要素を\<configSections >

定義済みのセクション、またはセクション グループを削除します。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<削除 >**

## <a name="syntax"></a>構文

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a>属性

|           | 説明 |
| --------- | ----------- |
| **name**  | 必須の属性です。<br><br>セクション、または削除するセクション グループの名前を指定します。 |

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ----------- |
| [**\<configSections >** 要素](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | 構成セクションと名前空間宣言が含まれています。 |

# <a name="child-elements"></a>子要素

なし

## <a name="remarks"></a>コメント

使用することができます、 **\<削除 >** セクションおよびセクション グループを構成ファイルの階層内の上位レベルで定義されているアプリケーションから削除する要素。

## <a name="example"></a>例

次の例を使用する方法を示しています、 **\<削除 >** マシン構成ファイルで定義されたセクションを削除するアプリケーション構成ファイル内の要素。

マシン構成ファイルのコードは、次のセクションを宣言して **\<sampleSection >**:

```xml
<!-- Machine.config file -->
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

アプリケーション構成ファイルのコードは、次の削除、  **\<sampleSection >** セクションです。 削除した後、アプリケーションがの設定を取得できません **\<sampleSection >** です。

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a>構成ファイル

この要素は、アプリケーション構成ファイル、マシン構成ファイルで使用できます (*Machine.config*)、および*Web.config*アプリケーション ディレクトリ レベルではないファイル。

## <a name="see-also"></a>関連項目

[.NET Framework の構成ファイル スキーマ](~/docs/framework/configure-apps/file-schema/index.md)
