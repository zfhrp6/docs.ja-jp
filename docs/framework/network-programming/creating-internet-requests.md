---
title: "インターネット要求の作成 | Microsoft Docs"
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
  - "WebRequest クラス、送受信 (データを)"
  - "ネットワーク"
  - "HttpWebResponse クラス、送受信 (データを)"
  - "要求 (インターネットからデータを)、作成 (要求を)"
  - "ネットワーク リソース"
  - "インターネット、要求 (データを)"
  - "データの要求、作成 (要求を)"
ms.assetid: faab683e-3f1e-4eee-b5e9-59f7245033d5
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# インターネット要求の作成
アプリケーションは <xref:System.Net.WebRequest.Create%2A?displayProperty=fullName> 方法で <xref:System.Net.WebRequest> のインスタンスを作成します。  これに渡される URI の設定に **\[WebRequest\]** から派生クラスを基づいてを作成する方法です。  
  
## Web、ファイルと FTP の要求  
 .NET Framework は処理の HTTP と HTTPS の要求に対する **\[WebRequest\]**から、派生 <xref:System.Net.HttpWebRequest> クラスを説明します。  ほとんどの場合、**\[WebRequest\]** クラスは、要求をする必要があるすべてのプロパティを提供します; 必要に応じて、ことが要求の Http 固有のプロパティにアクセスするに **\[WebRequest.Create\]** 方法によって作成された **HttpWebRequest** タイプに **\[WebRequest\]** のオブジェクトをキャストことが可能です。  同様に、**HttpWebResponse** のオブジェクトは、HTTP と HTTPS の要求からの応答を処理します。  **HttpWebResponse** への Http 固有のプロパティにアクセスするには、**HttpWebResponse** タイプに **WebResponse** のオブジェクトをキャスト必要があります。逆します。  
  
 .NET Framework は、「ファイルを使用するリソースに要求の処理に <xref:System.Net.FileWebRequest> と <xref:System.Net.FileWebResponse> クラスを提供します: 」URI の設定。  同様に、<xref:System.Net.FtpWebResponse> の <xref:System.Net.FtpWebRequest> およびクラスは、「ftp を使用するリソースに要求の処理に用意されています: 」設定。  、要求の設定が使用するリソースがである場合、要求をされるオブジェクトを取得するに **\[WebRequest.Create\]** 方法を使用できます。  
  
 へ他のアプリケーション レベルのセキュリティを使用する要求を処理するために、**\[WebRequest\]** と **WebResponse**から派生したプロトコル対応クラスを実行する必要があります。  詳細については、[プログラミング プラグインの可能なセキュリティ](../../../docs/framework/network-programming/programming-pluggable-protocols.md)を参照してください。  
  
## 参照  
 [方法: WebRequest クラスを使用してデータを要求する](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)   
 [データの要求](../../../docs/framework/network-programming/requesting-data.md)