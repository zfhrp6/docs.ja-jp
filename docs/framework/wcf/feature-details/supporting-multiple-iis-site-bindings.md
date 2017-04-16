---
title: "複数の IIS サイト バインディングのサポート | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 複数の IIS サイト バインディングのサポート
インターネット インフォメーション サービス \(IIS: Internet Information Services\) 7.0 で [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスをホストする場合は、同じサイトで同じプロトコルを使用する、複数のベース アドレスを提供できます。これにより、同じサービスで多数の異なる URI に応答できます。http:\/\/www.contoso.com および http:\/\/contoso.com でリッスンするサービスをホストするときには、これが役立ちます。また、内部ユーザー用に 1 つのベース アドレスを持ち、外部ユーザー用に別のベース アドレスを持つサービスを作成するのにも役立ちます。たとえば、http:\/\/internal.contoso.com および http:\/\/www.contoso.com というベース アドレスを持つ場合があります。  
  
> [!NOTE]
>  この機能は、HTTP プロトコルを使用してのみ、使用可能です。  
  
## 複数のベース アドレス  
 この機能は、IIS でホストされている [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスでのみ使用可能です。この機能は、既定では有効にされません。有効にするには、次の例に示すように、Web.config ファイルで `multipleSiteBindingsEnabled` 属性を \<`serviceHostingEnvironment`\> 要素に追加し、`true` に設定します。  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled=”true”/>  
```  
  
 IIS で [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスをホストする場合、IIS では、アプリケーションを格納している仮想ディレクトリへの URI に基づいて、1 つのベース アドレスが作成されます。インターネット インフォメーション サービス マネージャーを使用して、同じプロトコルを使用するベース アドレスを追加し、1 つ以上のバインディングを Web サイトに追加できます。それぞれのバインディングに対して、プロトコル \(HTTP または HTTPS\)、IP アドレス、ポート、およびホスト名を指定します。インターネット インフォメーション サービス マネージャーの使用[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[IIS マネージャー \(IIS 7\)](http://go.microsoft.com/fwlink/?LinkId=164057)」を参照してください。サイトへのバインディングの追加[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[Web サイトを作成する \(IIS 7\)](http://go.microsoft.com/fwlink/?LinkId=164060)」を参照してください。  
  
 同じサイトに複数のベース アドレスを指定すると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のヘルプ ページ、スキーマのインポート、サービスによって生成される WSDL\/MEX 情報に影響が生じます。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のヘルプ ページには、サービスと通信できる [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントの生成に使用する、コマンド ラインが表示されます。このコマンド ラインには、その Web サイト用の IIS バインディングで指定された最初のアドレスだけが含まれています。同様に、スキーマをインポートするときには、IIS バインディングで指定された最初のベース アドレスだけが使用されます。WSDL および MEX データには、IIS バインディングで指定されたすべてのベース アドレスが含まれています。  
  
> [!WARNING]
>  つまり、サービスに 2 つのベース アドレス \(1 つは内部ユーザー用、もう 1 つは外部ユーザー用\) がある場合、サービスによって生成される WSDL\/MEX 情報では、両方のベース アドレスが指定されます。