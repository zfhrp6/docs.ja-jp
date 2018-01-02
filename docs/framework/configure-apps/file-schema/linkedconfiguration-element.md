---
title: "&lt;linkedConfiguration&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding/linkedConfiguration
- http://schemas.microsoft.com/.NetConfiguration/v2.0#linkedConfiguration
helpviewer_keywords:
- configuration files [.NET Framework],linked configuration files
- <linkedConfiguration> element
- including configuration files
- linked configuration files
- linkedConfiguration Element
ms.assetid: 8eb34f3b-427e-4288-a7ff-c73f489deb45
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: dffff7fefa80f420e61045b21b0e0c1a170e2911
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="linkedconfiguration-element"></a>\<linkedConfiguration > 要素

インクルードする構成ファイルを指定します。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<assemblyBinding >**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration >**

## <a name="syntax"></a>構文

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a>属性

|           | 説明 |
| --------- | ----------- |
| **href**  | 必須の属性です。<br><br>含める構成ファイルの URL です。 サポートされている唯一の形式、 **href**属性は`file://`します。 ローカル ファイルと UNC ファイルがサポートされています。 |

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ----------- |
| [**\<assemblyBinding >**要素](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | 構成レベルでのアセンブリ バインディング ポリシーを指定します。 |

## <a name="child-elements"></a>子要素

なし

## <a name="remarks"></a>コメント

 **\<LinkedConfiguration >**要素は、サービス コンポーネントのアセンブリの簡略化します。 アセンブリを使用するアプリケーションの構成ファイルを使用できる 1 つまたは複数のアプリケーションでは、既知の場所に存在する構成ファイルがあるアセンブリを使用する場合、  **\<linkedConfiguration >**構成情報を直接含むのではなく、アセンブリの構成ファイルを含める要素。 コンポーネント アセンブリが処理された場合は、アセンブリを使用するすべてのアプリケーションに更新された構成情報を提供一般的な構成ファイルを更新します。

> [!NOTE]
>  **\<LinkedConfiguration >** Windows サイド バイ サイド マニフェストと共にアプリケーションに要素がサポートされていません。

次の規則は、リンクされた構成ファイルの使用を制御します。

- インクルードされる構成ファイルの設定はのみローダー バインド ポリシーには影響され、ローダーによってのみ使用されます。 インクルードされる構成ファイルではバインディング ポリシー以外の設定を使用できますが、これらの設定は何も影響がありません。

- サポートされている唯一の形式、`href`属性は`file://`します。 ローカル ファイルと UNC ファイルがサポートされています。

- 構成ファイルごとにリンクされている構成の数に制約はありません。

- すべてのリンクされた構成ファイルを結合し、1 つのファイルの動作と同様に、 `#include` C/C++ のディレクティブ。

-  **\<LinkedConfiguration >**要素がアプリケーション構成ファイルでのみ使用できます。 では無視されます*Machine.config*です。

- 循環参照が検出され、終了します。 つまり場合、  **\<linkedConfiguration >**ループを形成する一連の構成ファイルの要素、ループが検出され、停止します。

## <a name="example"></a>例

次の例では、ローカル ハード_ディスクからの構成ファイルをインクルードする方法を示します。

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>関連項目

[**\<assemblyBinding >**要素](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)   
[.NET Framework の構成ファイル スキーマ](~/docs/framework/configure-apps/file-schema/index.md)
