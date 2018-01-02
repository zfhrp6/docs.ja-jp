---
title: "&lt;bypasslist&gt;要素 (ネットワーク設定)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 20e3676e69357dc73433876275cb2737ee235552
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltbypasslistgt-element-network-settings"></a>&lt;bypasslist&gt;要素 (ネットワーク設定)
プロキシを使用しないアドレスを記述する正規表現のセットを提供します。  
  
 \<configuration>  
\<system.net >  
\<defaultProxy >  
\<bypasslist >  
  
## <a name="syntax"></a>構文  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[add](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-bypasslist-network-settings.md)|プロキシ バイ パス一覧に IP アドレスまたは DNS 名を追加します。|  
|[clear](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-bypasslist-network-settings.md)|バイパス リストをクリアします。|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-bypasslist-network-settings.md)|プロキシ バイ パス一覧から IP アドレスまたは DNS 名を削除します。|  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[defaultProxy](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|ハイパーテキスト転送プロトコル (HTTP: Hypertext Transfer Protocol) プロキシ サーバーを構成します。|  
  
## <a name="remarks"></a>コメント  
 バイパス リストを含む Uri を表す正規表現を<xref:System.Net.WebRequest>インスタンスは、プロキシ サーバーを直接の代わりにアクセスします。  
  
 この要素に正規表現を指定する場合は、注意を使用してください。 正規表現"[a ~ z] +\\.contoso\\.com"contoso.com ドメイン内の任意のホストと一致する contoso.com.cpandl.com ドメイン内のどのホストにも一致します。 Contoso.com ドメイン内のホストのみを一致するには、アンカー (「$」) を使用します。"[a ~ z] +\\.contoso\\.com$"です。  
  
 正規表現の詳細についてを参照してください。[.NET framework 正規表現](../../../../../docs/standard/base-types/regular-expressions.md)です。  
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  
 次の例では、バイパス リストに 2 つのアドレスを追加します。 1 つ目は、contoso.com ドメイン内のすべてのサーバーでプロキシをバイパスします。2 番目は、すべてのサーバーの IP アドレスを持つ開始 192.168.*.* でプロキシをバイパスします。  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
