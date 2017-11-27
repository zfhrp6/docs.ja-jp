---
title: "&lt;追加&gt;bypasslist (ネットワーク設定) の要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <bypasslist>, add element
- bypasslist, add element
- <add> element, bypasslist
- add element, bypasslist
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: eae909e2f70cfa045dd9a5c6b7496f112a59dc45
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-element-for-bypasslist-network-settings"></a>&lt;追加&gt;bypasslist (ネットワーク設定) の要素
プロキシ バイ パス一覧に IP アドレスまたは DNS 名を追加します。  
  
 \<configuration>  
\<system.net >  
\<defaultProxy >  
\<bypasslist >  
\<add>  
  
## <a name="syntax"></a>構文  
  
```xml  
<add   
  address="regular expression"   
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|**属性**|**説明**|  
|-------------------|---------------------|  
|**address**|IP アドレスまたは DNS 名を記述する正規表現。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[bypasslist](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|プロキシを使用しないアドレスを記述する正規表現のセットを提供します。|  
  
## <a name="remarks"></a>コメント  
 `add`要素は、IP アドレスやプロキシ サーバーをバイパスするアドレスのリストに DNS サーバー名を記述する正規表現を挿入します。  
  
 値、`address`属性は、一連の IP アドレスまたはホスト名を記述する正規表現をする必要があります。  
  
 この要素に正規表現を指定する場合は、注意を使用してください。 正規表現"[a ~ z] +\\.contoso\\.com"contoso.com ドメイン内の任意のホストと一致する contoso.com.cpandl.com ドメイン内のどのホストにも一致します。 Contoso.com ドメイン内のホストのみを一致するには、アンカー (「$」) を使用します。"[a ~ z] +\\.contoso\\.com$"です。  
  
 正規表現の詳細についてを参照してください。[.NET framework 正規表現](../../../../../docs/standard/base-types/regular-expressions.md)です。  
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  
 次の例では、バイパス リストに 2 つのアドレスを追加します。 1 つ目は、contoso.com ドメイン内のすべてのサーバーでプロキシをバイパスします。2 番目は、すべてのサーバーの IP アドレスが始まる 192.168.*.* でプロキシをバイパスします。  
  
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
  
## <a name="see-also"></a>関連項目  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
