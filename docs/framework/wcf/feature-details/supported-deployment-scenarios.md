---
title: "サポートされている配置シナリオ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5886b327f1ea6d2866b9fc76bb29031ee870934e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="supported-deployment-scenarios"></a>サポートされている配置シナリオ
部分的に信頼されたアプリケーションでの使用のために用意されている [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 機能のサブセットは、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]を使用するための一部のシナリオ (全部ではありません) の要件を満たすように作成されています。 サーバーでは、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、セキュリティの理由により [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] の中程度の信頼アクセス許可セットでサードパーティ製アプリケーションを実行するインターネット規模の共有ホスティング プロバイダーの要件を満たします。 クライアントでは、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の部分信頼サポート機能は、 [ClickOnce 展開](http://go.microsoft.com/fwlink/?LinkId=83712) または [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]の XAML ブラウザー アプリケーション (XBAP) テクノロジなどの展開技術の要件を満たすように設計されています。これらの技術は、信頼できないサイトからシームレスかつ安全にデスクトップ アプリケーションを展開できるようにするためのものです。  
  
## <a name="minimum-permission-requirements"></a>最小のアクセス許可の要件  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、次の標準の名前付きアクセス許可セットのいずれかで実行されるアプリケーションの機能のサブセットをサポートします。  
  
-   中程度の信頼アクセス許可  
  
-   インターネット ゾーン アクセス許可  
  
 これよりも制限の厳しいアクセス許可が設定された部分信頼アプリケーションで [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用すると、実行時にセキュリティ例外が発生することがあります。  
  
 このようなアクセス許可セットでサポートされる機能の詳細については、「 [Partial Trust Feature Compatibility](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md)」を参照してください。  
  
## <a name="partial-trust-on-the-server"></a>サーバーでの部分信頼  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web アプリケーション ホスティング サービスのプロバイダー事業者の多くは、それぞれのサーバーで動作するアプリケーションが [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] の中程度の信頼アクセス許可セットを使用して実行されることを義務付けています。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]サービスを使用するような環境で実行できます、 <xref:System.ServiceModel.BasicHttpBinding>、 <xref:System.ServiceModel.WebHttpBinding>、または <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> トランスポート レベルのセキュリティとします。  
  
 信頼レベルが中程度のホスティング環境で動作する[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、クライアント要求に応じて他のサーバーにメッセージを送信することによって、中間層サービスとして動作することもできます。 ホスティング環境が適切な <xref:System.Net.WebPermission> をアプリケーションに与えて、目的のサーバーに送信要求を行うようにする場合は、サーバーでの中間層のシナリオがサポートされます。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、サポートされる SOAP バインディングのいずれか 1 つを使用する SOAP メッセージングの他にも、部分的に信頼されたアプリケーションで Web スタイルのサービスを構築するための <xref:System.ServiceModel.WebHttpBinding> をサポートします。 [WCF Web HTTP プログラミング モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)、 [WCF 配信](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)、および[AJAX の統合と JSON サポート](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)の機能[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]がすべて部分的な信頼でサポートします。  
  
 ワークフロー サービスは完全信頼のアクセス許可を必要とし、部分的に信頼されたアプリケーションでは使用できません。  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][する方法: ASP.NET 2.0 で中程度の信頼を使用して](http://go.microsoft.com/fwlink/?LinkId=84603)です。  
  
## <a name="partial-trust-on-the-client"></a>クライアントでの部分信頼  
 信頼されていないインターネット サイトからコードをダウンロードして実行する場合、ある程度のセキュリティ対策が必要です。 [ClickOnce 展開](http://go.microsoft.com/fwlink/?LinkId=83712) と [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]の XBAP テクノロジでは共に、部分信頼を利用して信頼できないコードに制限付きのアクセス許可 (インターネット ゾーン) を与えます。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、 [ClickOnce 展開](http://go.microsoft.com/fwlink/?LinkId=83712) または XBAP によって展開された部分信頼のアプリケーション内からリモート サーバーと通信するときに使用できます。 インターネット ゾーン アクセス許可セットには、元のホスト用の <xref:System.Net.WebPermission> が含まれます。これにより、このようなアプリケーションは、サポートされる [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] バインディングのいずれかを使用してそれぞれの元のサーバーと通信できます (「 [Partial Trust Feature Compatibility](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md)を使用するための一部のシナリオ (全部ではありません) の要件を満たすように作成されています。  
  
## <a name="see-also"></a>関連項目  
 [コード アクセス セキュリティ](http://go.microsoft.com/fwlink/?LinkId=83717)  
 [Windows Presentation Foundation ブラウザーによってホストされるアプリケーションの概要](http://go.microsoft.com/fwlink/?LinkId=98397)  
 [部分信頼](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 [ASP.Net の中程度の信頼](http://go.microsoft.com/fwlink/?LinkId=69328)
