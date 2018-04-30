---
title: 複数の IIS サイト バインディングのサポート
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a4b586b4d5c3c37355bf7b05a8a0227565a5b5e5
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="supporting-multiple-iis-site-bindings"></a>複数の IIS サイト バインディングのサポート
インターネット インフォメーション サービス (IIS: Internet Information Services) 7.0 で [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスをホストする場合は、同じサイトで同じプロトコルを使用する、複数のベース アドレスを提供できます。 これにより、同じサービスで多数の異なる URI に応答できます。 リッスンするサービスをホストする場合に便利ですがhttp://www.contoso.comとhttp://contoso.comです。また、内部ユーザー用に 1 つのベース アドレスを持ち、外部ユーザー用に別のベース アドレスを持つサービスを作成するのにも役立ちます。 例:http://internal.contoso.comとhttp://www.contoso.comです。  
  
> [!NOTE]
>  この機能は、HTTP プロトコルを使用してのみ、使用可能です。  
  
## <a name="multiple-base-addresses"></a>複数のベース アドレス  
 この機能は、IIS でホストされている [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスでのみ使用可能です。 この機能は、既定では有効にされません。 有効にする必要がありますを追加する、`multipleSiteBindingsEnabled`属性を <`serviceHostingEnvironment`> Web.config 内の要素に設定し、ファイル`true`次の例で示すように、します。  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 IIS で [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスをホストする場合、IIS では、アプリケーションを格納している仮想ディレクトリへの URI に基づいて、1 つのベース アドレスが作成されます。 インターネット インフォメーション サービス マネージャーを使用して、同じプロトコルを使用するベース アドレスを追加し、1 つ以上のバインディングを Web サイトに追加できます。 それぞれのバインディングに対して、プロトコル (HTTP または HTTPS)、IP アドレス、ポート、およびホスト名を指定します。 詳細については、インターネット インフォメーション サービス マネージャーを使用して、次を参照してください。 [IIS マネージャー (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164057)です。 サイトへのバインドの追加に関する詳細については、次を参照してください[Web サイト (IIS 7) を作成する。](http://go.microsoft.com/fwlink/?LinkId=164060)  
  
 同じサイトに複数のベース アドレスを指定すると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のヘルプ ページ、スキーマのインポート、サービスによって生成される WSDL/MEX 情報に影響が生じます。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のヘルプ ページには、サービスと通信できる [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントの生成に使用する、コマンド ラインが表示されます。 このコマンド ラインには、その Web サイト用の IIS バインディングで指定された最初のアドレスだけが含まれています。 同様に、スキーマをインポートするときには、IIS バインディングで指定された最初のベース アドレスだけが使用されます。 WSDL および MEX データには、IIS バインディングで指定されたすべてのベース アドレスが含まれています。  
  
> [!WARNING]
>  つまり、サービスに 2 つのベース アドレス (1 つは内部ユーザー用、もう 1 つは外部ユーザー用) がある場合、サービスによって生成される WSDL/MEX 情報では、両方のベース アドレスが指定されます。
