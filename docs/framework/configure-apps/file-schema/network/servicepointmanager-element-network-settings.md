---
title: '&lt;servicePointManager&gt;要素 (ネットワーク設定)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5903174f125938923a63fc031421a8d5a020e56d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753587"
---
# <a name="ltservicepointmanagergt-element-network-settings"></a>&lt;servicePointManager&gt;要素 (ネットワーク設定)
ネットワーク リソースへの接続を構成します。  
  
 \<configuration>  
\<system.net>  
\<settings>  
\<servicePointManager >  
  
## <a name="syntax"></a>構文  
  
```xml  
<servicePointManager  
  checkCertificateName="true|false"  
  checkCertificateRevocationList="true|false"  
  encryptionPolicy="AllowNoEncryption|NoEncryption|RequireEncryption"  
  expect100Continue="true|false"  
  useNagleAlgorithm="true|false"  
  enableDnsRoundRobin="true|false"  
  dnsRefreshTimeout="time"  
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|**属性**|**説明**|  
|-------------------|---------------------|  
|`checkCertificateName`|システムが証明書を使用する前に、証明書の名前がサーバーのホスト名と一致することを確認する必要があるかどうかを指定します。 既定値は `true` です。|  
|`checkCertificateRevocationList`|システムが証明書を使用する前に、証明書が失効したかどうかをチェックする必要があるかどうかを指定します。 既定値は `false` です。|  
|`dnsRefreshTimeout`|ミリ秒単位で、DNS ラウンド ロビン オプションと組み合わせて期間ドメイン ネーム サービス (DNS) の解像度はキャッシュを指定します。 既定値は 120,000 ミリ秒 (2 分) です。|  
|`enableDnsRoundRobin`|すべてのアドレスまたは最初の 1 つだけに、ホストの DNS 解決が戻り値の複数のインターネット プロトコル (IP) アドレスを持つ名前かどうかを指定します。 既定値は `false` です。|  
|`encryptionPolicy`|SSL/TLS セッションに適用される暗号化ポリシーを指定します、<xref:System.Net.ServicePointManager>インスタンス。 値と同じ値には、<xref:System.Net.Security.EncryptionPolicy>列挙します。 使用<xref:System.Security.Authentication.CipherAlgorithmType.Null>は、暗号化ポリシーが に設定されている場合に必要`NoEncryption`です。 既定値は `RequireEncryption` です。|  
|`expect100Continue`|POST メソッドが受信することが予想されるかどうかを指定します、`100-continue`サーバーからの応答。 既定値は `true` です。|  
|`useNagleAlgorithm`|サービス ポイントのマネージャーによって制御される接続で Nagle アルゴリズムを使用するかどうかを指定します。 既定値は `true` です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[設定](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<xref:System.Net> 名前空間の基本的なネットワーク オプションを構成します。|  
  
## <a name="remarks"></a>コメント  
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Net.ServicePointManager>  
 <xref:System.Net.Security.EncryptionPolicy>  
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
