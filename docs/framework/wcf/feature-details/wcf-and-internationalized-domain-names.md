---
title: "WCF と国際化ドメイン名 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# WCF と国際化ドメイン名
国際化ドメイン名 \(IDN\) を持つ WCF サービスを許可するためのサポートが追加されました。  国際化ドメイン名とは、非 ASCII 文字を含むドメイン名です。  このサポートには、IDN 名を持つ WCF サービスをホストする機能と、IDN 名を持つ Web サービスとの通信を行う WCF クライアントをホストする機能の両方が含まれます。  
  
## System.Uri と IDN  
 <xref:System.Uri> には、<xref:System.Uri.Host%2A> および <xref:System.Uri.DnsSafeHost%2A> という 2 つのプロパティがあります。  これらのプロパティには、IDN 構成設定に応じて Unicode 値または Punycode 値が格納されます。  
  
 IDN をアプリケーションの構成ファイルで有効にするには、次の XML を使用します。  
  
```  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
  
```  
  
 \<idn\> 要素の enabled 属性は、次のいずれかの値に設定できます。  
  
1.  "None"  
  
2.  "AllExceptIntranet"  
  
3.  "All"  
  
 IDN 設定を "None" に設定した場合、Uri.Host または Uri.DnsSafeHost による変換は実行されません。  IDN 設定を "All" に設定した場合、uri.Host は Unicode のまま、uri.DnsSafeHost が Punycode に変換されます。  IDN 設定を "AllExceptIntranet" に設定すると、インターネット アドレスについては uri.DnsSafeHost が Punycode に変換され、イントラネット アドレスについては Unicode のままとなります。  この設定は、正しい DNS 名解決にとって重要です。  Windows 8 以降のバージョンでは、この設定を構成する必要はありません。  
  
> [!WARNING]
>  Punycode を使用してアドレスをハードコーディングしないようにしてください。  アドレスは、適用した構成設定に基づき、WCF によって自動的に変換されます。  
  
> [!WARNING]
>  Unicode 文字を applicationHost.exe.config に追加する場合は、UTF\-8 エンコードを使用してファイルを保存してください。  
  
## 参照  
 [System.Uri](http://msdn.microsoft.com/library/system.uri.aspx)