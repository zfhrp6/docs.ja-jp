---
title: "プラグ可能なプロトコルのプログラミング | Microsoft Docs"
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
  - "ダウンロード (インターネット リソースの)、プラグ可能なプロトコル"
  - "WebRequest クラス、プラグ可能なプロトコル"
  - "インターネット要求への応答、プラグ可能なプロトコル"
  - "WebResponse クラス、プラグ可能なプロトコル"
  - "送信 (データを)、プラグ可能なプロトコル"
  - "ネットワーク リソース、プラグ可能なプロトコル"
  - "インターネット、プラグ可能なプロトコル"
  - "プラグ可能なプロトコルのプログラミング"
  - "プラグ可能なプロトコル、プログラミング"
  - "要求 (インターネットからデータを)、プラグ可能なプロトコル"
  - "受信 (データを)、プラグ可能なプロトコル"
  - "プロトコル、プラグ可能"
ms.assetid: 66ef8456-7576-4e97-8956-959b216373db
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# プラグ可能なプロトコルのプログラミング
<xref:System.Net.WebResponse> の抽象的な <xref:System.Net.WebRequest> およびクラスはプラグイン可能なプロトコルに基準を提供します。  <xref:System.Net.WebRequest> と <xref:System.Net.WebResponse>からプロトコル対応クラスを取得すると、アプリケーションは、インターネットのリソースのデータを要求し、使用するプロトコルを指定せずに応答を読み取ることができます。  
  
 プロトコル対応する <xref:System.Net.WebRequest>を作成する前に作成されます方法を登録する必要があります。  <xref:System.Net.WebRequest> その子孫を特定のインターネット設定に、設定、サーバー、または設定、サーバーとパスに複数の要求を処理するために登録するに <xref:System.Net.WebRequest> の <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> の静的な方法を使用します。  
  
 ほとんどの場合、送れるデータを <xref:System.Net.WebRequest> 方法およびプロパティを使用して受け取るように分類します。  ただし、対応アクセス プロトコルのプロパティを必要がある場合は、特定の派生クラスのインスタンスに <xref:System.Net.WebRequest> を型にはめるできます。  
  
 プラグイン可能なプロトコルを使用するには、<xref:System.Net.WebRequest> のプロトコル子孫は対応するプロパティがある必要はありません既定の要求および応答のトランザクションを入力する必要があります。  たとえば、HTTP の <xref:System.Net.WebRequest> クラスを実行する <xref:System.Net.HttpWebRequest> のクラスが Web サーバーから返されるストリームを含む `GET` の要求を既定では提供します <xref:System.Net.HttpWebResponse> を返します。  
  
## 参照  
 [WebRequest からの派生](../../../docs/framework/network-programming/deriving-from-webrequest.md)   
 [WebResponse からの派生](../../../docs/framework/network-programming/deriving-from-webresponse.md)   
 [.NET Framework のネットワーク プログラミング](../../../docs/framework/network-programming/index.md)   
 [方法: WebRequest を型キャストしてプロトコル固有のプロパティにアクセスする](../../../docs/framework/network-programming/how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)