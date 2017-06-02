---
title: "方法: IPv6 のサポートを有効にするようにコンピューター構成ファイルを変更する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
caps.latest.revision: 18
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 18
---
# 方法: IPv6 のサポートを有効にするようにコンピューター構成ファイルを変更する
次のコード例に示します。コンピュータのコンフィギュレーション ファイル、*machine.config*を IPv6 のサポートを有効にする方法を変更する。  *machine.config* ファイルを Windows がインストール ディレクトリの *%Windir%\\Microsoft.NET\\Framework* のフォルダに保存されます。  .NET Framework コンピュータにインストールされている \(たとえば、*C:\\WINDOWS\\Microsoft.NET\\Framework\\v2.0.50727\\machine.config*\) 各バージョンの *%Windir%\\Microsoft.NET\\Framework* の下に *machine.config* のフォルダに固有のファイル。  
  
 これらの設定は、コンフィギュレーション ファイルのコンピュータ上の優先順位があるアプリケーションのコンフィギュレーション ファイルで作成できます。  
  
 .NET Framework Version 1.1 が、以前の **ipv6 enabled**、コンポーネントの Switch の値はかどうか <xref:System.Net.Dns?displayProperty=fullName> クラスの返品 IPv6 の住所のメンバ指定します。  
  
 .NET Framework Version 2.0 と後で、<xref:System.Net.Dns?displayProperty=fullName> クラスのすべてのメンバーに Windows が IPv6 をサポート \(たとえば、<xref:System.Net.Dns.GetHostEntry%2A?displayProperty=fullName> 方法\)、1 種類の制限の IPv6 の住所を返します。  <xref:System.Net.Dns?displayProperty=fullName> クラスによって不要のメンバは、\(たとえば、<xref:System.Net.Dns.Resolve%2A?displayProperty=fullName> 方法\) コンフィギュレーション ファイルの値を読み、確認します。  
  
> [!NOTE]
>  .NET Framework Version 2.0 が、後で、IPv6 は、既定で有効になります。  .NET Framework Version 1.1 には、以前の IPv6 は既定で無効になります。  
  
## 使用例  
  
```  
<system.net>  
    …………  
    <settings>  
        …………  
        <ipv6 enabled="true"/>   
    ……………  
    </settings>  
    ………………  
<system.net>  
```  
  
## 参照  
 [IPv6 アドレス指定](../../../docs/framework/network-programming/ipv6-addressing.md)   
 [ネットワーク設定スキーマ](../../../docs/framework/configure-apps/file-schema/network/index.md)   
 [\<ipv6\> 要素 \(ネットワーク設定\)](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)