---
title: "&lt;httpWebRequest&gt;要素 (ネットワーク設定)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
caps.latest.revision: "18"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: dadb2d7635f132b44d6fca8c56f53b847ffb1ff9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="lthttpwebrequestgt-element-network-settings"></a>&lt;httpWebRequest&gt;要素 (ネットワーク設定)
Web 要求のパラメーターをカスタマイズします。  
  
 \<configuration>  
\<system.net >  
\<設定 >  
\<httpWebRequest >  
  
## <a name="syntax"></a>構文  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|**属性**|**説明**|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|応答ヘッダーの最大長を指定します (キロバイト単位)。 既定値は 64 です。 値-1 は、応答ヘッダーにサイズの制限が設定されていないことを示します。|  
|`maximumErrorResponseLength`|エラー応答の最大長を指定します (キロバイト単位)。 既定値は 64 です。 値-1 は、エラー応答のサイズの制限が設定されていないことを示します。|  
|`maximumUnauthorizedUploadLength`|アップロードの最大長 (バイト単位)、承認されていないエラー コードへの応答を指定します。 既定値は -1 です。 値-1 は、アップロード時にサイズの制限が設定されていないことを示します。|  
|`useUnsafeHeaderParsing`|安全でないヘッダーの解析が有効になっているかどうかを指定します。 既定値は `false` です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[設定](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<xref:System.Net> 名前空間の基本的なネットワーク オプションを構成します。|  
  
## <a name="remarks"></a>コメント  
 既定では、.NET Framework は URI の解析の RFC 2616 を厳密には適用します。 サーバー応答の一部が原因となる、禁止されているフィールドにコントロール文字を含めることがあります、<xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType>をスローするメソッド、<xref:System.Net.WebException>です。 場合**useUnsafeHeaderParsing**に設定されている**true**、<xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType>ただしです。 この場合はスローされません、アプリケーションがいくつかの形式の URI の解析攻撃を受けやすくなります。 応答に制御文字が含まれないように、サーバーを変更することをお勧めします。  
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  
 次の例は、大きい値を指定する方法を示しています。 標準ヘッダーの最大長よりもします。  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpWebRequest  
        maximumResponseHeadersLength="128"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>  
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
