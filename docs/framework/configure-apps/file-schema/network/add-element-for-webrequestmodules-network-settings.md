---
title: '&lt;追加&gt;webRequestModules (ネットワーク設定) の要素'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 921f5f2bfda1a19d022d3f3f4131e3653fd17ea7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742791"
---
# <a name="ltaddgt-element-for-webrequestmodules-network-settings"></a>&lt;追加&gt;webRequestModules (ネットワーク設定) の要素
アプリケーションにカスタム Web 要求のモジュールを追加します。  
  
 \<configuration>  
\<system.net>  
\<webRequestModules>  
\<add>  
  
## <a name="syntax"></a>構文  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|**属性**|**説明**|  
|-------------------|---------------------|  
|`prefix`|この Web 要求モジュールによって処理される要求の URI プレフィックス。|  
|`type`|完全修飾型名 (によって示される、<xref:System.Type.FullName%2A>プロパティ) とアセンブリ名 (によって示される、<xref:System.Reflection.Assembly.FullName%2A>プロパティ)、この Web 要求のモジュールを実装する、コンマで区切って指定します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[webRequestModules](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|使用してネットワークのホストから情報を要求するモジュールを指定します。|  
  
## <a name="remarks"></a>コメント  
 `prefix`属性は、指定された Web 要求モジュールを使用する URI プレフィックスを定義します。 Web 要求のモジュールは、通常、HTTP、FTP などの特定のプロトコルを処理する登録しますが、特定のサーバーまたはサーバー上のパスに要求を処理する登録されていることができます。  
  
 URI の一致のプレフィックスに渡される Web 要求のモジュールが作成された、<xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>メソッドです。  
  
 値、`prefix`属性が有効な URI: たとえば、"http"の先頭の文字にする必要がありますか"http://www.contoso.com"です。  
  
 値、`type`属性が有効な型名と対応するアセンブリ名、コンマで区切られたにする必要があります。  
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  
 次の例では、HTTP のカスタム Web 要求のモジュールを登録します。 指定したモジュールの正しい値を持つバージョンおよび PublicKeyToken の値を置き換える必要があります。  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Net.WebRequest>  
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
