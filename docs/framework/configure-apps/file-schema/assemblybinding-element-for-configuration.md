---
title: "&lt;assemblyBinding&gt;要素&lt;構成&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 8d670c56a885a5fdae059a87f63fba9ab32f020c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="assemblybinding-element-for-configuration"></a>\<assemblyBinding > 要素を\<構成 >

構成レベルでのアセンブリ バインディング ポリシーを指定します。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;**\<assemblyBinding >**

## <a name="syntax"></a>構文

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a>属性

|           | 説明 |
| --------- | ----------- |
| **xmlns** | 必須の属性です。<br><br>アセンブリのバインディングに必要な XML 名前空間を指定します。 値として、文字列 "urn:schemas-microsoft-com:asm.v1" を使用します。 |

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ----------- |
| [**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | 共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。 |

## <a name="child-element"></a>子要素

|     | 説明 |
| --- | ----------- |
| [**\<linkedConfiguration >**](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) | インクルードする構成ファイルを指定します。 |

## <a name="remarks"></a>コメント

[  **\<LinkedConfiguration >** ](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md)要素内の構成ファイルにアセンブリを含めるアプリケーション構成ファイルを許可することで、コンポーネントのアセンブリの管理を簡略化既知の場所ではなくアセンブリ構成設定を複製します。

> [!NOTE]
>  **\<LinkedConfiguration >** Windows サイド バイ サイド マニフェストと共にアプリケーションに要素がサポートされていません。

## <a name="example"></a>例

次の例では、ローカル ハード_ディスク上の構成ファイルをインクルードする方法を示します。

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>関連項目

[.NET Framework の構成ファイル スキーマ](~/docs/framework/configure-apps/file-schema/index.md)
