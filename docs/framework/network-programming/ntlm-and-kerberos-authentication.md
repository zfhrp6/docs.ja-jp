---
title: "NTLM 認証および Kerberos 認証 | Microsoft Docs"
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
  - "認証 [.NET Framework]、NTLM"
  - "認証 [.NET Framework]、Kerberos"
  - "ユーザー認証、Kerberos"
  - "ユーザー認証、NTLM"
  - "Kerberos 認証"
  - "受信 (データの)、認証"
  - "NTLM 認証"
  - "インターネット、認証"
  - "クライアント認証、Kerberos"
  - "送信 (データの)、認証"
  - "ネットワーク リソース、認証"
  - "クラス [.NET Framework]、認証"
  - "クライアント認証、NTLM"
ms.assetid: 9ef65560-f596-4469-bcce-f4d5407b55cd
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# NTLM 認証および Kerberos 認証
既定の NTLM 認証および認証を Kerberos サーバーと認証との間のアプリケーションに関連付けられている Microsoft Windows NT のユーザーの資格情報を使用します。  既定以外 NTLM 認証を使用すると、アプリケーションには NTLM 認証の型を設定し、次の例で示すようにホストにユーザー名、パスワード、およびドメインを渡すために <xref:System.Net.NetworkCredential> のオブジェクトを使用します。  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = _  
    New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create (MyURI);  
WReq.Credentials =   
    new NetworkCredential(UserName, SecurelyStoredPassword, Domain);  
```  
  
 アプリケーションのユーザーの資格情報を使用してインターネット サービスに接続する必要があるアプリケーションは、次の例で示すように、ユーザーの既定の資格情報を、実行できます。  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = CredentialCache.DefaultCredentials  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create (MyURI);  
WReq.Credentials = CredentialCache.DefaultCredentials;  
```  
  
 交渉認証のモジュールがリモート サーバーが NTLM または Kerberos 認証を使用する確認し、適切な応答かどうかを送信します。  
  
> [!NOTE]
>  NTLM 認証がプロキシ サーバーを使用して。  
  
## 参照  
 [基本認証とダイジェスト認証](../../../docs/framework/network-programming/basic-and-digest-authentication.md)   
 [インターネット認証](../../../docs/framework/network-programming/internet-authentication.md)