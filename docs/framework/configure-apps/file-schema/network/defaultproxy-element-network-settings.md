---
title: '&lt;defaultProxy&gt;要素 (ネットワーク設定)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a91775ff9f46eba772a959cfac3115c9720ac5ab
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742719"
---
# <a name="ltdefaultproxygt-element-network-settings"></a>&lt;defaultProxy&gt;要素 (ネットワーク設定)
ハイパーテキスト転送プロトコル (HTTP: Hypertext Transfer Protocol) プロキシ サーバーを構成します。  
  
 \<configuration>  
\<system.net>  
\<defaultProxy >  
  
## <a name="syntax"></a>構文  
  
```xml  
      <defaultProxy  
        enabled="true|false"  
        useDefaultCredentials="true|false">  
           <bypasslist> … </bypasslist>  
           <proxy> … </proxy>  
           <module> … </module>  
      </defaultProxy>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|`enabled`|Web プロキシが使用されているかどうかを指定します。 既定値は `true` です。|  
|`useDefaultCredentials`|このホストに対する既定の資格情報が Web プロキシにアクセスするために使用されるかどうかを指定します。 既定値は `false` です。|  
  
### <a name="child-elements"></a>子要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[bypasslist](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|プロキシを使用しないアドレスを記述する一連の正規表現を提供します。|  
|[モジュール](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md)|新しいプロキシ モジュールをアプリケーションに追加します。|  
|[プロキシ](../../../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md)|プロキシ サーバーを定義します。|  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[system.net](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|.NET Framework がネットワークに接続する方法を指定するための設定が含まれています。|  
  
## <a name="remarks"></a>コメント  
 defaultProxy 要素が空の場合、Internet Explorer のプロキシ設定が使用されます。 この動作は、.NET Framework Version 1.1 とは異なります。  
  
 場合、例外がスローされます、[モジュール](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md)要素が非パブリックの種類を指定、種類がから派生していない、<xref:System.Net.IWebProxy>クラス、このオブジェクトの既定のコンス トラクターから例外が発生したか、例外が発生しました中システム指定の既定のプロキシを取得しています。 例外の <xref:System.Exception.InnerException%2A> プロパティに、このエラーの根本的な原因に関する詳細情報が含まれています。  
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  
 次の例は、Internet Explorer のプロキシで既定値を使用して、プロキシ アドレスを指定し、ローカル アクセスおよび contoso.com のプロキシをバイパスします。  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
