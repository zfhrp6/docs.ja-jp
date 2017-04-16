---
title: "ネットワーク設定スキーマ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "構成の設定 [.NET Framework], ネットワーク"
  - "接続 [.NET Framework], ネットワーク構成要素"
  - "要素 [.NET Framework], ネットワーク構成要素"
  - "インターネット, ネットワーク構成要素"
  - "ネットワーク構成要素"
  - "ネットワーク リソース, ネットワーク構成要素"
  - "ネットワーク設定"
  - "受信 (データを), ネットワーク構成要素"
  - "送信 (データを), ネットワーク構成要素"
ms.assetid: f1de5a0f-76c5-4833-819f-5222b8146340
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# ネットワーク設定スキーマ
ネットワーク設定は、.NET Framework がインターネットに接続する方法を指定します。  [\<system.Net\> 要素 \(ネットワーク設定\)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) 下の各子構成要素の機能を説明する表を次に示します。  
  
|要素|説明|  
|--------|--------|  
|[\<authenticationModules\> 要素 \(ネットワーク設定\)](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|インターネット要求を認証するために使用するモジュールを指定します。|  
|[\<connectionManagement\> 要素 \(ネットワーク設定\)](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|インターネット ホストへの接続の最大数を指定します。|  
|[\<defaultProxy\> 要素 \(ネットワーク設定\)](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|インターネットへの HTTP 要求のために使用するプロキシ サーバーを指定します。|  
|[\<mailSettings\> 要素 \(ネットワーク設定\)](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|メール送信オプションの設定を格納します。|  
|[\<requestCaching\> 要素 \(ネットワーク設定\)](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|インターネット ホストからの情報を要求するために使用するモジュールを指定します。|  
|[\<requestCaching\> 要素 \(ネットワーク設定\)](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<xref:System.Net?displayProperty=fullName> 名前空間の基本的なネットワーク オプションを構成します。|  
|[\<webRequestModules\> 要素 \(ネットワーク設定\)](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|インターネット ホストからの情報を要求するために使用するモジュールを指定します。|  
  
 Uri の設定は、.NET Framework は URI \(Uniform Resource Identifiers \(URIs\) を使用\) で表現された Web アドレスがどのように処理するかを指定します。  [\<Uri\> 要素 \(Uri 設定\)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md) 下の各子構成要素の機能を説明する表を次に示します。  
  
|要素|説明|  
|--------|--------|  
|[\<idn\> 要素 \(Uri 設定\)](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|国際化ドメイン名 \(IDN: Internationalized Domain Name\) による解析をドメイン名に適用するかどうかを指定します。|  
|[\<iriParsing\> 要素 \(Uri 設定\)](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|IRI \(International Resource Identifier\) 解析を <xref:System.Uri> に適用するかどうか、および IRI の解析規則を適用するかどうかを指定します。|  
|[\<schemeSettings\> 要素 \(Uri 設定\)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<xref:System.Uri> が特定のスキーマに対して解析される方法を指定します。|  
  
## 参照  
 [構成 \(インターネット アプリケーションを\)](../../../../../docs/framework/network-programming/configuring-internet-applications.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)