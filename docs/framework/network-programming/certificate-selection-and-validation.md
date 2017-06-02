---
title: "証明書の選択と検証 | Microsoft Docs"
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
ms.assetid: c933aca2-4cd0-4ff1-9df9-267143f25a6f
caps.latest.revision: 15
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 15
---
# 証明書の選択と検証
<xref:System.Net> クラスを選択する方法がサポートされ、<xref:System.Security.Cryptography.X509Certificates> の検証するには、Secure Socket Layer \(SSL\) 接続の。  クライアントとサーバーにはなくを認証する一つ以上の証明書を選択できます。  サーバーは、クライアントに認証証明書の一つ以上の特定の属性を持つように要求することもできます。  
  
## 定義  
 証明書は公開キー \(属性、バージョン番号、シリアル番号、有効期限など\) および証明機関からのデジタル署名を含む ASCII のバイト ストリームです。  証明書の暗号化された接続を設定またはサーバーにクライアントを認証するために使用されます。  
  
## クライアント証明書の選択と検証  
 クライアント接続で SSL は、特定の一つ以上の証明書を選択できます。  クライアント証明書は Web サーバーまたは SMTP メール サーバーへの接続 SSL に関連付けることができます。  クライアントが <xref:System.Security.Cryptography.X509Certificates.X509Certificate> または <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> クラス オブジェクト コレクションに資格を追加します。  、例として、電子メールを使用して、証明書の集合 <xref:System.Net.Mail.SmtpClient> クラスの <xref:System.Net.Mail.SmtpClient.ClientCertificates%2A> のプロパティに関連付けられている <xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection>のインスタンスです\)。  <xref:System.Net.HttpWebRequest> クラスに <xref:System.Net.HttpWebRequest.ClientCertificates%2A> の同様のプロパティがあります。  
  
 <xref:System.Security.Cryptography.X509Certificates.X509Certificate> と <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> クラス間の主な違いは秘密キーが <xref:System.Security.Cryptography.X509Certificates.X509Certificate> クラスの証明書ストアに存在する必要があります。  
  
 証明書のグループに追加され、SSL が特定の接続に関連付けられている、証明書がサーバーにサーバーがその要求を送信する。  複数のクライアント接続証明書がに設定されている場合、最適な 1 がサーバーによって提供される証明書のフィールドの一覧とクライアント証明書のフィールドの名前との一致を考慮するアルゴリズムに基づいて使用されます。  
  
 <xref:System.Net.Security.SslStream> のクラスが SSL のハンドシェイクの設定をさらに詳細提供します。  クライアントは、ピッキングに使用するクライアント証明書委任を指定できます。  
  
 リモート サーバーは、クライアント、証明書が有効期限、適切な証明機関によって署名できることを確認できます。  委任は <xref:System.Net.ServicePointManager.ServerCertificateValidationCallback%2A> に証明書の検証を適用するに追加できます。  
  
## クライアント証明書の選択  
 .NET Framework サーバーには次のように表示するクライアント証明書を選択します:  
  
1.  クライアント証明書がサーバーに指定された場合、証明書が最初に指定されたときにキャッシュされ、それ以降のクライアント証明書の要求に再利用されます。  
  
2.  必須の場合は、選択するにはクライアント証明書として必須の結果を常に使用します。  委任が null 値を返品した証明書のコレクションが空白でない可能な月にキャッシュされた証明書を使用するとしますが、キャッシュされた匿名認証情報を使用しないでください。  
  
3.  これがクライアント証明書の最初の課題の場合、フレームワークは <xref:System.Security.Cryptography.X509Certificates.X509Certificate> の証明書またはサーバーで提供される証明書のフィールドの一覧とクライアント証明書のフィールドの名前との一致を検索する接続に関連付けられている <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> オブジェクト クラスを列挙。  一致する最初の証明書はサーバーに送信されます。  証明書が一致していないか、証明書のコレクションが空の場合、匿名信任状はサーバーに送信されます。  
  
## 証明書のコンフィギュレーションのツール  
 いくつかのツールはクライアントとサーバー証明書の構成に使用できます。  
  
 *\[Winhttpcertcfg.exe\]* のツールがクライアント証明書をコンフィギュレーションすることもできます。  *\[Winhttpcertcfg.exe\]* のツールは、Windows Server 2003 のリソース キットをツールの 1 種類として指定します。  このツールは www.microsoft.com に Windows Server 2003 のリソースのキットのツールの一部としてダウンロードとしても使用できます。  
  
 *HttpCfg.exe* のツールが <xref:System.Net.HttpListener> クラスの証明書サーバーをコンフィギュレーションすることもできます。  *\[HttpCfg.exe\]* のツールは、Windows Server 2003 および Windows XP Service Pack 2 のサポート ツールの 1 種類として入力されます。  *\[HttpCfg.exe\]* サポートなどのツールは、Windows Server 2003 または Windows XP に既定では、インストール。  Windows Server 2003。  サポート ツールは、以下のフォルダとは別に、インストール、Windows Server 2003 のファイル CD\-ROM にします:  
  
 \\Support\\Tools\\Suptools.msi  
  
 Windows XP Service Pack 2 の使用については、Windows XP サポート ツールは www.microsoft.com からダウンロードとして使用できます。  
  
 *\[HttpCfg.exe\]* ツールのバージョンのソース・コードは、Windows Server の SDK としてサンプルを指定します。  *\[HttpCfg.exe\]* のサンプルのソース・コードが次のフォルダの下の Windows SDK の一部としてネットワーキングのサンプルなど既定では、インストール:  
  
 *C:\\Program Files\\Microsoft SDKs\\Windows\\v1.0\\Samples\\NetDS\\http\\serviceconfig*  
  
 これらのツールに加えて、<xref:System.Security.Cryptography.X509Certificates.X509Certificate> と <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> クラス、ファイル システムから証明書を読み込むする方法を提供します。  
  
## 参照  
 [ネットワーク プログラミングにおけるセキュリティ](../../../docs/framework/network-programming/security-in-network-programming.md)   
 [.NET Framework のネットワーク プログラミング](../../../docs/framework/network-programming/index.md)