---
title: "ホスティング例外 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# ホスティング例外
ここでは、ホスティングによって生成されるすべての例外を示します。  
  
## 例外の一覧  
  
|リソース コード|リソースの文字列|  
|--------------|--------------|  
|Hosting\_AddressIsAbsoluteUri|完全 URI は許可されていません。完全 URI は、ServiceHostingEnvironment.EnsureServiceAvailable API に対しては許可されていません。対応するサービスの仮想パスを使用してください。|  
|Hosting\_BuildProviderCouldNotCreateType|指定した CLR 型をサービスのコンパイル中に読み込むことができません。この型が、アプリケーションの \\\\App\_Code ディレクトリに配置されているソース ファイルで定義されているか、アプリケーションの \\\\bin ディレクトリに配置されているコンパイル済みアセンブリ内、もしくはグローバル アセンブリ キャッシュにインストールされているアセンブリ内にあるか確認してください。型名では、大文字と小文字が区別されます。\\\\App\_Code、\\\\bin などのディレクトリは、アプリケーションのルート ディレクトリに配置する必要があります。\\\\App\_Code ディレクトリと \\\\bin ディレクトリは、サブディレクトリで入れ子にはできません。|