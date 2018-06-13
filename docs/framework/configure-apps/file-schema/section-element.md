---
title: '&lt;セクション&gt;要素'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 17b44ca93efc26f4732f5fe2926f894257d8f984
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746437"
---
# <a name="section-element"></a>\<セクション > 要素

構成セクションの宣言が含まれています。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<セクション >**

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup >**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<セクション >**

## <a name="syntax"></a>構文

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a>必要な属性

|           | 説明 |
| --------- | ----------- |
| **name**  | 構成セクションの名前を指定します。 |
| **type**  | 構成ファイルからセクションを読み取る構成セクション ハンドラー クラスの名前を指定します。 型の値には、"fully-qualified-section-handler-class-name、単純なアセンブリ名"の構文があります。 単純なアセンブリ名がなく、ルート ファイル名、 *.dll*ファイル拡張子。 |

## <a name="optional-attributes"></a>省略可能な属性

次の属性は、ASP.NET アプリケーションにのみ適用されます。 構成システムには、その他のアプリケーションの種類のこれらの属性が無視されます。

|                     | 説明 |
| ------------------- | ----------- |
| **仮想ディレクトリ** | セクションを使用できる構成ファイルを指定します。 次のいずれかの値を使用します。<br><br>**すべての場所**<br>すべての構成ファイルで使用するのには、セクションを使用できます。 既定値です。<br>**MachineOnly**<br>により、マシン構成ファイルでのみ使用するセクション (*Machine.config*)。<br>**MachineToApplication**<br>マシン構成ファイルまたはアプリケーション構成ファイルで使用するのには、セクションを使用できます。 |
| **allowLocation**   | セクション内で使用できるかどうか決定、 **\<場所 >** 要素。 次のいずれかの値を使用します。<br><br>**true**<br>セクションは内で使用される、 **\<場所 >** 要素。 既定値です。<br>**false**<br>内で使用するのには、セクションを許可しない、 **\<場所 >** 要素。 |

## <a name="parent-elements"></a>親要素

|     | 説明 |
| --- | ----------- |
| [**\<configSections >** 要素](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | 構成セクションと名前空間宣言が含まれています。 |
| [**\<sectionGroup >** 要素](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | 構成セクションの名前空間を定義します。 |

> [!NOTE]
> A **\<セクション >** 要素はいずれかの子要素 **\<configSections >** または **\<sectionGroup >** は対象外両方とも。

## <a name="child-elements"></a>子要素

なし

## <a name="remarks"></a>コメント

構成セクションを本質的に宣言するには、構成ファイルの新しい要素を定義します。 新しい要素には、構成セクション ハンドラーを設定が含まれています (実装するクラスは、<xref:System.Configuration.IConfigurationSectionHandler>インターフェイス) を読み取ります。 属性と子要素を定義するセクションの設定の読み取りに使用するセクション ハンドラーに依存します。

構成セクション ハンドラーを宣言すること、 *Machine.config*ファイルを使用すると、そのコンピューター上のすべてのアプリケーション構成ファイルで構成セクションを使用する場合を除き、 **allowDefinition**属性がそれ以外の場合を指定します。

## <a name="example"></a>例

次の例では、構成セクションを定義してそのセクションの設定を定義する方法を示します。

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" 
             allowLocation="false" />
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
