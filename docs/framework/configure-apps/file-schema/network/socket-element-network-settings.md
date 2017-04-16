---
title: "&lt;socket&gt; 要素 (ネットワーク設定) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#socket"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<socket> 要素"
  - "socket 要素"
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
caps.latest.revision: 21
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 21
---
# &lt;socket&gt; 要素 (ネットワーク設定)
ソケット処理で完了ポートを使用するかどうかを指定します。  
  
## 構文  
  
```  
  
      <socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel ="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/socket>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|**Attribute**|**説明**|  
|-------------------|------------|  
|`alwaysUseCompletionPortsForAccept`|Accept メソッドの呼び出しを行う場合、ソケットで常に完了ポートを使用するかどうかを示します。  既定値は `false` です。|  
|`alwaysUseCompletionPortsForConnect`|Connect メソッドの呼び出しを行う場合、ソケットで常に完了ポートを使用するかどうかを示します。  既定値は `false` です。|  
|`ipProtectionLevel`|ソケットに使用する既定の <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=fullName> を指定します。  既定値は、Windows のバージョンによって異なります。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|**要素**|**説明**|  
|------------|------------|  
|[設定](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<xref:System.Net> 名前空間の基本的なネットワーク オプションを構成します。|  
  
## 解説  
 クラスによって `alwaysUseCompletionPortsForAccept` と `alwaysUseCompletionPortsForConnect` 属性が <xref:System.Net.Sockets?displayProperty=fullName>.namespace で完了ポートの使用に関する既定の動作を指定するために使用されます。  完了ポートは、高性能なサーバー アプリケーションに推奨されます。  
  
 `alwaysUseCompletionPortsForAccept` 属性および `alwaysUseCompletionPortsForConnect` 属性の既定値は **false** です。  
  
 <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> を使用して、適用可能な構成ファイルから `alwaysUseCompletionPortsForAccept` 属性の現在の値を取得できます。  <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> を使用して、適用可能な構成ファイルから `alwaysUseCompletionPortsForConnect` 属性の現在の値を取得できます。  
  
 `ipProtectionLevel` 属性は、ソケットに使用する既定の <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=fullName> を指定します。  <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> プロパティを使用すると、IPv6 ソケットの制限を指定したスコープ \(同じリンク ローカルまたはサイト ローカル プレフィックスを持つアドレスなど\) に構成できます。  このオプションによって、アプリケーションは IPv6 ソケットにアクセス制限を設定できます。  この制限により、プライベート LAN で実行されるアプリケーションを外部からの攻撃に対して簡単、堅牢に強化できます。  このオプションで待機中のソケットのスコープを変更して、適切な場合はパブリック ユーザーおよびプライベート ユーザーからの無制限のアクセスを許可したり、必要に応じて同じサイトへのアクセスのみに制限したりできます。  
  
 この `ipProtectionLevel` 属性設定は、最初の受信トラフィックにだけ影響します。  
  
-   ソケットで受信接続を待機する TCP サーバー。  
  
-   ソケットでパケットを受信する UDP アプリケーション。  
  
 この構成設定は、既に確立されている TCP 接続には影響しません \(トラフィックはいずれの方向でも制限されません\)。また、アプリケーションが送信する UDP パケットにも影響しません。  
  
 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=fullName> 列挙体で定義されている保護レベルに対応する `ipProtectionLevel` 属性設定には、次の値を指定できます。  
  
|||  
|-|-|  
|**属性値**|**説明**|  
|EdgeRestricted|IP 保護レベルはエッジ制限付きです。  この値は、インターネット経由で動作するように設計されているアプリケーションによって使用されます。  この設定を使用する場合、Windows Teredo 実装を使用したネットワーク アドレス変換 \(NAT: Network Address Translation\) トラバーサルは使用できません。  これらのアプリケーションは、IPv4 のファイアウォールをバイパスすることがあるため、開いているポートを対象としたインターネットからの攻撃に対して堅牢である必要があります。  Windows Server 2003 と Windows XP では、ソケットの IP 保護レベルの既定値はエッジ制限付きです。|  
|Restricted|IP 保護レベルは制限付きです。  この値は、インターネットのシナリオを実装しないイントラネット アプリケーションによって使用されます。  これらのアプリケーションは、一般的に、インターネット型の攻撃に対してテストが行われていなかったり堅牢ではなかったりします。  この設定を使用する場合、受信トラフィックはリンクローカルのみに制限されます。|  
|制限なし|IP 保護レベルは無制限です。  この値は、Windows に組み込まれている IPv6 NAT Traversal 機能 \(たとえば、Teredo\) を使用するアプリケーションを含む、インターネット経由で動作するように設計されているアプリケーションによって使用されます。  これらのアプリケーションは、IPv4 のファイアウォールをバイパスすることがあるため、開いているポートを対象としたインターネットからの攻撃に対して堅牢である必要があります。  Windows Server 2008 R2 と Windows Vista では、ソケットの IP 保護レベルの既定値は無制限です。|  
|Unspecified|IP 保護レベルは未指定です。  Windows 7 と Windows Server 2008 R2 では、ソケットの IP 保護レベルの既定値は未指定です。|  
  
 `ipProtectionLevel` 属性の既定値は **Unspecified** です。  
  
 <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> プロパティを使用して、適用可能な構成ファイルから `ipProtectionLevel` 属性の現在の値を取得できます。  
  
## 構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル \(Machine.config\) で使用できます。  
  
## 使用例  
 完了ポートが使用される必要があることと、既定の <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=fullName> が Unrestricted である必要があることを指定する方法を、次のコード例に示します。  
  
```  
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
  
## 参照  
 <xref:System.Net?displayProperty=fullName>   
 <xref:System.Net.Configuration.SocketElement?displayProperty=fullName>   
 <xref:System.Net.Sockets?displayProperty=fullName>   
 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=fullName>   
 <xref:System.Net.Sockets.SocketOptionName?displayProperty=fullName>   
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)