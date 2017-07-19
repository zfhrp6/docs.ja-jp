---
title: "基本認証とダイジェスト認証 | Microsoft Docs"
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
  - "認証 [.NET Framework]、クラス"
  - "基本認証"
  - "認証 [.NET Framework]、基本"
  - "クライアント認証、基本"
  - "ユーザー認証、基本"
  - "認証 [.NET Framework]、ダイジェスト"
  - "受信 (データの)、認証"
  - "クライアント認証、ダイジェスト"
  - "インターネット、認証"
  - "ダイジェスト認証"
  - "送信 (データの)、認証"
  - "ネットワーク リソース、認証"
  - "ユーザー認証、ダイジェスト"
ms.assetid: 8cce2742-8d52-4643-9dd2-64ddf38aa878
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# 基本認証とダイジェスト認証
基本とダイジェストの認証を <xref:System.Net> の実装に RFC2617 – HTTP 認証に従います。: \(www.w3.org から World Wide Web コンソーシアム Web サイトで使用可能\) 基本およびダイジェスト認証。  
  
 基本とダイジェスト認証を使用するには、アプリケーションは次の例で示すように、インターネットからデータを要求する <xref:System.Net.WebRequest> のオブジェクトの <xref:System.Net.WebRequest.Credentials%2A> のプロパティのユーザー名とパスワードを指定する必要があります。  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword)  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
WReq.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword);  
```  
  
> [!CAUTION]
>  基本認証およびダイジェストに送信されるデータを暗号化いないため、データは敵対者で表示できます。  また、基本認証の資格情報は、ユーザー名とパスワード\) 明確に送信され、横取りできます。  
  
## 参照  
 [NTLM 認証および Kerberos 認証](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)   
 [インターネット認証](../../../docs/framework/network-programming/internet-authentication.md)