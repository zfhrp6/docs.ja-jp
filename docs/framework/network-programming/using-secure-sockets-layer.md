---
title: "Secure Sockets Layerの使用 | Microsoft Docs"
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
  - "SSL"
  - "Secure Sockets Layer"
  - "インターネットからのデータ要求、Secure Sockets Layer"
  - "データの送信、Secure Sockets Layer"
  - "ネットワーク リソース"
  - "データ要求、Secure Sockets Layer"
  - "データの受信、Secure Sockets Layer"
  - "インターネット、Secure Sockets Layer"
ms.assetid: 6e4289e6-d1b7-4e82-ab0d-e83e3b6063ed
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# Secure Sockets Layerの使用
<xref:System.Net> のクラスが複数のネットワーク セキュリティの接続を暗号化するには Secure Sockets Layer \(SSL\) を使用します。  
  
 http の接続の場合は、<xref:System.Net.WebRequest> と <xref:System.Net.WebResponse> のクラスが SSL をサポートする Web ホストと通信するために SSL を使用します。  SSL を使用する決定を特定 URI に基づいて <xref:System.Net.WebRequest> クラスが、行われます。  URI の「https から始まれば: 」、SSL が使用されます; URI が「http から始まれば: 」、非暗号化の接続が使用されます。  
  
 ファイル Transfer Protocol \(FTP\) で SSL を使用するには、<xref:System.Net.FtpWebRequest.GetResponse>を追加する前に調整するに <xref:System.Net.FtpWebRequest.EnableSsl> のプロパティを設定します。  同様に、Simple Mail 転送プロトコル \(SMTP\) を使用して、SSL は、電子メールを送信する前に調整するに <xref:System.Net.Mail.SmtpClient.EnableSsl> のプロパティを設定します。  
  
 <xref:System.Net.Security.SslStream> のクラスが SSL にストリーム ベースの抽象的概念を示し、SSL のハンドシェイクをコンフィギュレーションする方法を説明します。  
  
## 例  
  
### コード  
  
```vb  
Dim MyURI As String = "https://www.contoso.com/"  
Dim Wreq As WebRequest = WebRequest.Create(MyURI)  
  
Dim serverUri As String = "ftp://ftp.contoso.com/file.txt"  
Dim request As FtpWebRequest = CType(WebRequest.Create(serverUri), FtpWebRequest)  
request.Method = WebRequestMethods.Ftp.DeleteFile  
request.EnableSsl = True  
Dim response As FtpWebResponse = CType(request.GetResponse(), FtpWebResponse)  
```  
  
```csharp  
String MyURI = "https://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
  
String serverUri = "ftp://ftp.contoso.com/file.txt"  
FtpWebRequest request = (FtpWebRequest)WebRequest.Create(serverUri);  
request.EnableSsl = true;  
request.Method = WebRequestMethods.Ftp.DeleteFile;  
FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
```  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   **\[System.Net\]** の名前空間への参照。  
  
## 参照  
 [ネットワーク プログラミングにおけるセキュリティ](../../../docs/framework/network-programming/security-in-network-programming.md)   
 [.NET Framework のネットワーク プログラミング](../../../docs/framework/network-programming/index.md)   
 [証明書の選択と検証](../../../docs/framework/network-programming/certificate-selection-and-validation.md)