---
title: "HTTP | Microsoft Docs"
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
  - "プロトコル、HTTP"
  - "送信 (データを)、HTTP"
  - "HttpWebResponse クラス、送受信 (データを)"
  - "HTTP"
  - "受信 (データを)、HTTP"
  - "アプリケーション プロトコル、HTTP"
  - "インターネット、HTTP"
  - "ネットワーク リソース、HTTP"
  - "HTTP、HTTP の概要"
  - "HttpWebRequest クラス、送受信 (データを)"
ms.assetid: 985fe5d8-eb71-4024-b361-41fbdc1618d8
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# HTTP
.NET Framework は<xref:System.Net.HttpWebRequest> と <xref:System.Net.HttpWebResponse> クラスを使用するすべてのインターネットのトラフィックより大多数を構成する HTTP プロトコルに詳細なサポートを提供します。  <xref:System.Net.WebRequest> と <xref:System.Net.WebResponse>から派生したこれらのクラスは、静的方法 <xref:System.Net.WebRequest.Create%2A?displayProperty=fullName> が http https 「」または「」に従って URI に発生するときに、既定では戻されます。  プロパティとして公開される Http 特定の機能へのアクセスを必要に応じて要求をする必要がある **HttpWebRequest** または **HttpWebResponse**にこれらのクラスのタイプにはめるできます。ほとんどの場合、**WebResponse** の **\[WebRequest\]** およびクラスはすべてを提供します。  
  
 **HttpWebRequest** と **HttpWebResponse** は、標準の HTTP の要求および応答のトランザクションをカプセル化、共通の HTTP ヘッダーにアクセスできます。  これらのクラスは、ほとんどの HTTP 1.1 の機能を、チャンク、認証、preauthentication、暗号化、プロキシ サーバーでは、証明書の検証および接続管理のデータを送受信するパイプライニングがサポートされます。  プロパティを使用して提供されていないカスタム ヘッダーとヘッダーには格納され、**\[ヘッダー\]** のプロパティを使用してアクセスできます。  
  
 **HttpWebRequest** は **\[WebRequest.Create\]** 方法に URI に合格する前に **\[WebRequest\]** で使用される既定のクラスで、登録する必要はありません。  
  
 自分のアプリケーションに **true**  \(既定値\) に <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> のプロパティを設定して HTTP のリダイレクトに自動的に続かせますできます。  アプリケーションは要求の方向を変更および **HttpWebResponse** の [&#91;ResponseURI&#93;](frlrfsystemnethttpwebresponseclassresponseuritopic) のプロパティは要求にな Web 応募した実際のリソースが含まれます。  **false**に設定 **\[AllowAutoRedirect\]**、アプリケーションの HTTP プロトコルのエラーとしてリダイレクトを扱えれば必要がある場合。  
  
 アプリケーションは [WebExceptionStatus.ProtocolError](frlrfsystemnetwebexceptionstatusclasstopic)に設定 <xref:System.Net.WebException.Status%2A> の <xref:System.Net.WebException> をつかまえるして HTTP プロトコルのエラーが表示されます。  <xref:System.Net.WebException.Response%2A> のプロパティはサーバーが送信 **WebResponse** を含み、ある実際の HTTP なエラーを表示します。  
  
## 参照  
 [プロキシを介したインターネットへのアクセス](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)   
 [アプリケーション プロトコルの使用](../../../docs/framework/network-programming/using-application-protocols.md)   
 [方法: HTTP 固有のプロパティにアクセスする](../../../docs/framework/network-programming/how-to-access-http-specific-properties.md)