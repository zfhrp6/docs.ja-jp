---
title: "Web およびソケットのアクセス許可 | Microsoft Docs"
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
helpviewer_keywords: 
  - "ネットワーク"
  - "位置 [.NET Framework]、受け入れ"
  - "ソケット、アクセス許可"
  - "ネットワーク、アクセス許可"
  - "インターネット、アクセス許可"
  - "ネットワーク リソース"
  - "SocketPermission クラス、SocketPermission クラスについて"
  - "位置 [.NET Framework]、接続"
  - "WebPermission クラス、WebPermission クラスについて"
  - "アクセス許可 [.NET Framework]、ソケット"
  - "セキュリティ [.NET Framework]、インターネット"
  - "位置 [.NET Framework]、付与"
ms.assetid: d51ad8cb-03ae-4a51-bfcd-cfcf6b98afa9
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# Web およびソケットのアクセス許可
<xref:System.Net> の名前空間を使用してアプリケーションのインターネットのセキュリティは <xref:System.Net.WebPermission> と <xref:System.Net.SocketPermission> クラスが提供されます。  **\[WebPermission\]** のクラスが URI のデータが必要か、またはインターネットに URI に役立つアプリケーションの権限を制御します。  **\[SocketPermission\]** クラスは、ローカル ポートのデータを受け入れるか、ソケット ホストのポート番号、および転送プロトコルのような住所で転送プロトコルを使用して、リモート デバイスに連絡するに <xref:System.Net.Sockets.Socket> を使用するアプリケーションの権限を制御します。  
  
 アクセス許可、クラスを使用するかは、のアプリケ ション タイプによって。  <xref:System.Net.WebRequest> と子孫を使用するアプリケーションは、アクセス許可を管理するに **\[WebPermission\]** クラスを使用する必要があります。  ソケット レベルのアクセスを使用するアプリケーションは、アクセス許可を管理するに **\[SocketPermission\]** クラスを使用する必要があります。  
  
 **\[WebPermission\]** と **\[SocketPermission\]** は、2 種類のアクセス許可を定義します: 受け入れ、接続します。  承認はアプリケーションに別のパーティーからフォワード接続を応答権限を与えます。  接続をアプリケーションに別のパーティーへの接続を開始する権限を与えます。  
  
 **\[SocketPermission\]** のインスタンスに、承認は、アプリケーションがローカル配送先住所を接続を受け付けるできることを示します; アプリケーションがリモート \(またはローカル\) 配送先住所に接続できることを示します接続します。  
  
 **\[WebPermission\]** のインスタンスに、承認は、アプリケーションが世界に **\[WebPermission\]** によって制御される URI をエクスポートするということです; \(、またはローカルかどうか\) アプリケーションでその URI にアクセスできるようにする接続します。  
  
## 参照  
 [セキュリティ](../../../docs/standard/security/index.md)   
 [ネットワーク プログラミングにおけるセキュリティ](../../../docs/framework/network-programming/security-in-network-programming.md)