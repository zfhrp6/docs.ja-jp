---
title: "&lt;ソケット&gt;要素 (ネットワーク設定)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
caps.latest.revision: "21"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: fefb8e119d428d86501e1c8cdd5eec5ef0809cbd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltsocketgt-element-network-settings"></a>&lt;ソケット&gt;要素 (ネットワーク設定)
ソケット操作が完了ポートを使用するかどうかを指定します。  
  
 \<configuration>  
\<system.net >  
\<設定 >  
\<ソケット >  
  
## <a name="syntax"></a>構文  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|**属性**|**説明**|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|受け入れメソッド呼び出しの場合、ソケットで常に完了ポートを使用するかどうかを示します。 既定値は `false` です。|  
|`alwaysUseCompletionPortsForConnect`|Connect メソッドの呼び出しの場合、ソケットで常に完了ポートを使用するかどうかを示します。 既定値は `false` です。|  
|`ipProtectionLevel`|既定値を指定<xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>ソケットを使用します。 既定値は、Windows のバージョンによって異なります。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[設定](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<xref:System.Net> 名前空間の基本的なネットワーク オプションを構成します。|  
  
## <a name="remarks"></a>コメント  
 `alwaysUseCompletionPortsForAccept`と`alwaysUseCompletionPortsForConnect`にあるクラスで属性を使用して、完了ポートの使用に関する既定の動作を指定、 <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace です。 完了ポートは、高パフォーマンス サーバー アプリケーションに適しています。  
  
 既定値、`alwaysUseCompletionPortsForAccept`と`alwaysUseCompletionPortsForConnect`属性は**false**です。  
  
 <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A>の現在の値を取得するために使用する、`alwaysUseCompletionPortsForAccept`該当する構成ファイルからの属性です。 <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A>の現在の値を取得するために使用する、`alwaysUseCompletionPortsForConnect`該当する構成ファイルからの属性です。  
  
 `ipProtectionLevel`属性は、既定値を指定します。<xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>ソケットを使用します。 <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>プロパティなど、ローカル リンクまたはサイト ローカル プレフィックスを同じアドレスを特定のスコープ、IPv6 ソケットの制限の構成を有効にします。 このオプションにより、IPv6 ソケットに対するアクセス制限を設定できます。 この制限により、プライベート LAN で実行されるアプリケーションを外部からの攻撃に対して簡単かつ堅牢に強化できます。 このオプションは、拡大変換か、適切な場合は、パブリックおよびプライベートのユーザーまたは必要に応じて同じサイトにのみアクセスを制限することから無制限のアクセスを有効にすると、待機中のソケットのスコープを絞り込みます。  
  
 これは、`ipProtectionLevel`初期着信トラフィックのみに影響を与える属性の設定。  
  
-   ソケットの受信接続のリッスン TCP サーバー。  
  
-   ソケットでパケットを受信する UDP アプリケーション。  
  
 この構成設定では既に確立されている TCP 接続が (トラフィックは双方向に無制限) には影響しません UDP パケットを送信するアプリケーションには影響しません。  
  
 できる値、`ipProtectionLevel`属性の設定が指定された定義済みの保護レベルに対応して、<xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>次のように列挙します。  
  
|**属性値**|**説明**|  
|-|-|  
|EdgeRestricted|IP 保護レベルは、エッジ制限付きです。 この値が、インターネット経由で動作するアプリケーションで使用されます。 この設定は、Windows Teredo の実装を使用したネットワーク アドレス変換 (NAT) トラバーサルを許可されません。 これらのアプリケーションは、開かれたポートに送信するインターネット攻撃からアプリケーションを強化する必要がありますので、IPv4 のファイアウォールをバイパスする可能性があります。 Windows Server 2003 および Windows XP の場合は、ソケットで IP 保護レベルの既定値はエッジ制限付きです。|  
|Restricted|IP 保護レベルは制限されます。 この値は、イントラネットのシナリオを実装していないイントラネット アプリケーションで使用されます。 これらのアプリケーションは通常、テストもインターネット スタイルの攻撃に対して強化します。 この設定では、リンク ローカルのみを受信したトラフィックを制限します。|  
|無制限|IP 保護レベルは制限されません。 この値は組み込まれている IPv6 NAT トラバーサル機能を活用するアプリケーションなど、インターネット経由で動作するよう設計されています。 アプリケーションによって使用されます (たとえば Teredo) を Windows にします。 これらのアプリケーションは、開かれたポートに送信するインターネット攻撃からアプリケーションを強化する必要がありますので、IPv4 のファイアウォールをバイパスする可能性があります。 Windows Server 2008 R2 および Windows Vista では、ソケットで IP 保護レベルの既定値は制限されません。|  
|指定されていません。|IP 保護レベルが指定されていません。 Windows 7 および Windows Server 2008 R2 でのソケットで IP 保護レベルの既定値は指定されません。|  
  
 既定値、`ipProtectionLevel`属性は**未指定**です。  
  
 <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>プロパティを使用しての現在の値を取得すること、`ipProtectionLevel`該当する構成ファイルからの属性です。  
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  
 次の例は、完了ポートを使用することを指定する方法と、既定<xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>限定してください。  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <socket  
        alwaysUseCompletionPortsForAccept="true"  
        alwaysUseCompletionPortsForConnect="true"  
        ipProtectionLevel="Unrestricted"  
       />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.Net?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>  
 <xref:System.Net.Sockets?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>  
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
