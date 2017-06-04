---
title: "コア通信 : Webhost サポート | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 034c501f-96f9-4ef7-9602-3ac21788fd3e
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# コア通信 : Webhost サポート
ここでは、Webhost サポートによって生成されるすべての例外を示します。  
  
## 例外の一覧  
  
|リソース コード|リソースの文字列|  
|--------------|--------------|  
|Hosting\_CompatibilityServiceNotHosted|このサービスでは、ASP.NET 互換性が必要です。また、IIS でホストする必要もあります。Web.config で ASP.NET 互換性を有効にして IIS でサービスをホストするか、または AspNetCompatibilityRequirementsAttribute.AspNetCompatibilityRequirementsMode プロパティを Required 以外の値に設定します。|  
|Hosting\_ListenerNotFoundForActivationInRecycling|指定されたアドレスをアクティブにリッスンしているチャネルはありません。アプリケーションがリサイクルされる場合、サービスは閉じられます。|  
|Hosting\_NonHTTPInCompatibilityMode|ASP.NET 互換性でサポートされるプロトコルは HTTP と HTTPS のみです。指定されたエンドポイントを削除するか、アプリケーションに対して ASP.NET 互換性を無効にします。|  
|Hosting\_ProcessNotExecutingUnderHostedContext|指定されたホスト プロセスは、現在のホスト環境内で呼び出すことができません。この API では、アプリケーションの呼び出しがインターネット インフォメーション サービスまたは Windows プロセス アクティブ化サービス内で干すとされている必要があります。|  
|Hosting\_ServiceCompatibilityRequire|このサービスは ASP.NET 互換性を必要とするため、アクティブにできません。このアプリケーションに対して、ASP.NET 互換性が有効になっていません。Web.config ファイルで ASP.NET 互換性を有効にするか、AspNetCompatibilityRequirementsAttribute.AspNetCompatibilit を設定します。|