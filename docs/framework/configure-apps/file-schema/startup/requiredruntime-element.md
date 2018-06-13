---
title: '&lt;requiredRuntime&gt;要素'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 184547dd47e728f17f28105e74b2ca67c1436efc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749983"
---
# <a name="ltrequiredruntimegt-element"></a>&lt;requiredRuntime&gt;要素
バージョン 1.0 の共通言語ランタイムのみがアプリケーションでサポートされることを指定します。 この要素は推奨されておらず、使用できなくする必要があります。 [ `supportedRuntime` ](supportedruntime-element.md)要素を使用してください。
  
 \<configuration>  
\<startup>  
\<requiredRuntime>  
  
## <a name="syntax"></a>構文  
  
```xml  
   <requiredRuntime    
version="runtime version"  
safemode="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`version`|省略可能な属性です。<br /><br /> このアプリケーションをサポートする .NET Framework のバージョンを指定する文字列値。 文字列値は、.NET Framework のインストールのルート ディレクトリ名と一致する必要があります。 文字列値の内容は解析されません。|  
|`safemode`|省略可能な属性です。<br /><br /> ランタイム スタートアップ コードがランタイムのバージョンを確認するためのレジストリを検索するかどうかを指定します。|  
  
## <a name="safemode-attribute"></a>セーフ モード属性  
  
|[値]|説明|  
|-----------|-----------------|  
|`false`|ランタイム スタートアップ コードは、レジストリを検索します。 これが既定値です。|  
|`true`|ランタイム スタートアップ コードは、レジストリでは検索しません。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`startup`|含まれています、`<requiredRuntime>`要素。|  
  
## <a name="remarks"></a>コメント  
 ランタイムのバージョン 1.0 をサポートするために構築されたアプリケーションを使用する必要があります、`<requiredRuntime>`要素。 1.1 以降、ランタイムのバージョンを使用して構築されたアプリケーションを使用する必要があります、`<supportedRuntime>`要素。  
  
> [!NOTE]
>  使用する場合、 [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)構成ファイルを指定する関数を使用する必要があります、`<requiredRuntime>`ランタイムのすべてのバージョンの要素。 `<supportedRuntime>`を使用するときに、要素は無視されます[CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)です。  
  
 `version`属性文字列は指定されたバージョンの .NET Framework のインストール フォルダーの名前と一致する必要があります。 この文字列は解釈されません。 ランタイム スタートアップ コードが一致するフォルダーを見つけられない場合、ランタイムが読み込まれていません。スタートアップ コードは、エラー メッセージが表示され、終了します。  
  
> [!NOTE]
>  Microsoft Internet Explorer でホストされているアプリケーションのスタートアップ コードは無視されます、`<requiredRuntime>`要素。  
  
## <a name="example"></a>例  
 次の例では、構成ファイルでランタイムのバージョンを指定する方法を示します。  
  
```xml  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 [スタートアップ設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver> 使用するランタイム バージョンの指定](http://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
