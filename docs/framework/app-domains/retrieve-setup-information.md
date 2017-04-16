---
title: "アプリケーション ドメインからのセットアップ情報の取得 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "AppDomainSetup オブジェクト"
  - "アプリケーション ドメイン, 取得 (セットアップ情報を)"
  - "取得 (セットアップ情報を)"
ms.assetid: 5cdb12ae-1e37-4a62-8ec7-93d6dcc6e8d9
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# アプリケーション ドメインからのセットアップ情報の取得
アプリケーション ドメインの各インスタンスは、プロパティと <xref:System.AppDomainSetup> 情報で構成されます。  <xref:System.AppDomain?displayProperty=fullName> クラスを使用して、アプリケーション ドメインからセットアップ情報を取得できます。  このクラスは、アプリケーション ドメインについての構成情報を取得するいくつかのメンバーを提供します。  
  
 アプリケーション ドメインの **AppDomainSetup** オブジェクトを問い合わせて、アプリケーション ドメインの作成時に渡されたセットアップ情報を取得することもできます。  
  
 新しいアプリケーション ドメインを作成し、いくつかのメンバー値をコンソールに出力する例を次に示します。  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 アプリケーション ドメインのセットアップ情報を設定してから取得する例を次に示します。  `AppDomain.SetupInformation.ApplicationBase` は構成情報を取得します。  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## 参照  
 [Hosting Overview](http://msdn.microsoft.com/ja-jp/ea527626-99e3-4995-81c4-c8f3e60eb6d5)   
 [Programming with Application Domains](http://msdn.microsoft.com/ja-jp/bd36055b-56bd-43eb-b4d8-820c37172131)   
 [アプリケーション ドメインの使用](../../../docs/framework/app-domains/use.md)