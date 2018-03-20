---
title: "WCF 開発ツールの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d253f38fab21496dd305cc67e7b6e84846579f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-wcf-development-tools"></a>WCF 開発ツールの使用
このセクションでは、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスの開発を支援する [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 開発ツールについて説明します。

[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] テンプレートは独自のサービスを迅速に構築するための基礎として使用することができます。これによって、サービスをデバッグし、テストするための [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス自動ホストと [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] テスト クライアントを使用できるようになります。 これらのツールによって、高速でシームレスなデバッグとテストのサイクルが実現し、初期の段階においてホスト モデルのコミットが必要なくなります。

## <a name="the-wcf-developer-tools"></a>WCF の開発者用ツール  
 [WCF Visual Studio テンプレート](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 定義済みを使用することができます[!INCLUDE[indigo2](../../../includes/indigo2-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]でプロジェクトと項目テンプレート[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]をすばやく構築[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]サービスや周辺アプリケーションです。  
  
 [WCF サービス ホスト (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスの自動ホスト (WcfSvcHost.exe) を使用すると、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] デバッガーを起動して (F5 キーを押します)、実装しているサービスを自動的にホストおよびテストすることができます。 その後、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のテスト用クライアント (wcfTestClient.exe) または独自のクライアントを使用してサービスをテストし、潜在的なエラーを見つけて修正できます。  
  
 [WCF のテスト用クライアント (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のテスト用クライアント (WcfTestClient.exe) は GUI ツールです。このツールを使用すると、任意の型のパラメーターを入力し、その入力をサービスに送信して、サービスから返される応答を表示できます。 このツールを [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスの自動ホストと組み合わせて使用すると、シームレスにサービスをテストできるようになります。  
  
 [XML からのデータ型クラスの生成](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 クリップボードに格納されている XML データは、コード ページに貼り付けることができます。 データで定義されているクラスは、コード型に変換されます。  
  
## <a name="using-the-tools-without-administrator-privilege"></a>管理特権を必要としないツールの使用  
 管理特権のないユーザーが [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスを開発できるようにするために、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] のインストール時には、名前空間 "http://+:8731/Design_Time_Addresses" に対してアクセス制御リスト (ACL: Access Control List) が作成されます。 この ACL は (UI) に設定され、コンピューターにログオンしているすべての対話ユーザーが含まれます。 管理者は、この ACL にユーザーを追加または削除したり、追加のポートを開いたりできます。この ACL によって、既定の構成で、WCF テンプレートまたは WF テンプレートでデータを送受信できるようになります。 また、ユーザーは、管理特権が付与されていなくても、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスの自動ホスト (wcfSvcHost.exe) を使用できるようになります。  
  
 システム特権のある管理者アカウントで [!INCLUDE[wv](../../../includes/wv-md.md)] の Netsh.exe ツールを使用すると、アクセスを変更できます。 Netsh.exe の使用例を次に示します。  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]Netsh.exe を参照してください[Netsh.exe ツールとコマンド ライン スイッチを使用する方法](http://go.microsoft.com/fwlink/?LinkId=97877)です。  
  
## <a name="see-also"></a>参照  
 [WCF Visual Studio テンプレート](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [WCF サービス ホスト (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [WCF のテスト用クライアント (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
