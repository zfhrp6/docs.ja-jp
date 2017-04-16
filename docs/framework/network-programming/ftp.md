---
title: "FTP | Microsoft Docs"
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
  - "FTP"
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# FTP
.NET Framework は <xref:System.Net.FtpWebRequest> と <xref:System.Net.FtpWebResponse> クラスを FTP プロトコルに対する総合的なサポートを提供します。  これらのクラスが <xref:System.Net.WebRequest> と <xref:System.Net.WebResponse>から取得されます。  プロパティとして公開される FTP 特定の機能へのアクセスを必要に応じて要求をする必要がある <xref:System.Net.FtpWebRequest> または <xref:System.Net.FtpWebResponse>にこれらのクラスのタイプにはめるできます。ほとんどの場合、<xref:System.Net.WebResponse> の <xref:System.Net.WebRequest> およびクラスはすべてを提供します。  
  
## 例  
 詳細については、次のトピックを参照してください: [方法: FTP を使用してファイルをダウンロードする](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md)、[方法: FTP を使用してファイルをアップロードする](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md)と [方法: FTP でディレクトリの内容を一覧表示する](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md)。  
  
## プロキシと FTP  
 プロキシは \(<xref:System.Net.FtpWebRequest.Proxy%2A> のプロパティで指定された\) の HTTP プロキシの場合、<xref:System.Net.WebRequestMethods.Ftp.DownloadFile>、<xref:System.Net.WebRequestMethods.Ftp.ListDirectory>と <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> のコマンドのみがサポートされます。  
  
## 参照  
 [プロキシを介したインターネットへのアクセス](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)   
 [ネットワーク プログラミングのサンプル](../../../docs/framework/network-programming/network-programming-samples.md)   
 [クライアントの FTP テクノロジのサンプル](http://go.microsoft.com/fwlink/?LinkID=179557)   
 [FTP の自宅の技術サンプルの参照](http://go.microsoft.com/fwlink/?LinkID=179569)   
 [アプリケーション プロトコルの使用](../../../docs/framework/network-programming/using-application-protocols.md)