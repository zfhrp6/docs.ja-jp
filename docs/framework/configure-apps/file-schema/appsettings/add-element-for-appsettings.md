---
title: "&lt;追加&gt;要素&lt;appSettings&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d080a7c63ddda0577e66d2e7ddd433c7fd5fdbd1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="add-element-for-appsettings"></a>\<追加 > 要素を\<appSettings >

カスタム アプリケーション設定を追加します。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<追加 >**

## <a name="syntax"></a>構文

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a>属性

|           | 説明 |
| --------- | ----------- |
| **key**   | 必須の属性です。<br><br>追加するキーの名前を指定します。 |
| **value** | 必須の属性です。<br><br>追加するキーの値を指定します。 |

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ----------- |
| [**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | ファイル パス、XML Web サービス URL、またはアプリケーションのその他のカスタム構成情報など、カスタム アプリケーションの設定が含まれています。 |

## <a name="child-elements"></a>子要素

なし

## <a name="example"></a>例

次の例では、アプリケーションの名前のカスタム構成設定を追加する方法を示します。

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

## <a name="see-also"></a>関連項目

[.NET Framework の構成ファイル スキーマ](~/docs/framework/configure-apps/file-schema/index.md)
