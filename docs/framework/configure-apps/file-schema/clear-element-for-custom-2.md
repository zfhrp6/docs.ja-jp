---
title: "&lt;オフ&gt;NameValueSectionHandler と DictionarySectionHandler 要素"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57ee634c987d344d81f1ca099fe55e633bfbf659
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<オフ > NameValueSectionHandler と DictionarySectionHandler 要素

セクション内のすべての以前に定義された設定を消去します。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<sectionName >**](~/docs/framework/configure-apps/file-schema/custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<オフ >**

## <a name="syntax"></a>構文

```xml
<clear />
```

## <a name="attributes"></a>属性

なし

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ------------|
| [**\<sectionName >**要素](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | 使用するカスタム構成セクションの設定を定義、<xref:System.Configuration.NameValueSectionHandler>と<xref:System.Configuration.DictionarySectionHandler>クラスです。 |

## <a name="child-elements"></a>子要素

なし

## <a name="remarks"></a>コメント

使用することができます、 **\<オフ >**構成ファイルの階層内の上位レベルで定義されているアプリケーションからのすべての設定を削除する要素。

## <a name="example"></a>例

この例は、マシン構成ファイルとアプリケーション構成ファイルを定義し、使用する方法を示しています、 **\<オフ >**で以前に定義されたセクションをオフにするアプリケーション構成ファイル内の要素、マシン構成ファイルです。

マシン構成ファイルのコードは、次のセクションを宣言して **\<mySection >**:

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

次のアプリケーション構成ファイルのコードからすべての設定を削除する **\<mySection >**です。 アプリケーションを取得できませんで宣言されていた設定のいずれかで、  **\<mySection >**マシン構成ファイルのセクションです。

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>構成ファイル

この要素は、アプリケーション構成ファイル、マシン構成ファイルで使用できます (*Machine.config*)、および*Web.config*アプリケーション ディレクトリ レベルではないファイル。

## <a name="see-also"></a>関連項目

[.NET Framework の構成ファイル スキーマ](~/docs/framework/configure-apps/file-schema/index.md)
