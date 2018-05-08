---
title: サポートされている配置シナリオ
ms.date: 03/30/2017
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
ms.openlocfilehash: d0afd12b1c17f9356146aa13c90f8db65ed9ec0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="supported-deployment-scenarios"></a>サポートされている配置シナリオ
部分的に信頼されたアプリケーションで使用できるサポートされる Windows Communication Foundation (WCF) 機能のサブセットは、WCF を使用するためのすべてではなく、一部のシナリオの要件を満たす設計されています。 WCF がインターネット規模の要件を満たしているサーバーで、サード パーティ製のアプリケーションを実行しているホスティング プロバイダーが共有に、[!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)]中程度の信頼アクセス許可がセキュリティ上の理由を設定します。 クライアントでは、WCF 部分信頼サポートするものではなどの配置テクノロジの要件を満たす[ClickOnce 配置](http://go.microsoft.com/fwlink/?LinkId=83712)または[!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]の XAML ブラウザー アプリケーション テクノロジは、シームレスかつ安全に許可します。信頼されていないサイトからのデスクトップ アプリケーションを展開します。  
  
## <a name="minimum-permission-requirements"></a>最小のアクセス許可の要件  
 WCF では、次の標準的な名前付き権限セットのいずれかで実行されるアプリケーションの機能のサブセットをサポートしています。  
  
-   中程度の信頼アクセス許可  
  
-   インターネット ゾーン アクセス許可  
  
 制限の厳しいアクセス許可を持つ部分信頼アプリケーションで WCF を使用すると、実行時にセキュリティ例外が発生する可能性があります。  
  
 このようなアクセス許可セットでサポートされる機能の詳細については、「 [Partial Trust Feature Compatibility](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md)」を参照してください。  
  
## <a name="partial-trust-on-the-server"></a>サーバーでの部分信頼  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web アプリケーション ホスティング サービスのプロバイダー事業者の多くは、それぞれのサーバーで動作するアプリケーションが [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] の中程度の信頼アクセス許可セットを使用して実行されることを義務付けています。 WCF サービスを使用するような環境で実行できます、 <xref:System.ServiceModel.BasicHttpBinding>、 <xref:System.ServiceModel.WebHttpBinding>、または <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> トランスポート レベルのセキュリティとします。  
  
 中程度の信頼ホスティング環境で実行されている WCF サービスは、クライアントの要求に応答の他のサーバーにメッセージを送信して中間層サービスとしても機能ことができます。 ホスティング環境が適切な <xref:System.Net.WebPermission> をアプリケーションに与えて、目的のサーバーに送信要求を行うようにする場合は、サーバーでの中間層のシナリオがサポートされます。  
  
 WCF でサポートされる SOAP メッセージングを使用して、サポートされる SOAP バインディングの 1 つだけでなく、<xref:System.ServiceModel.WebHttpBinding>部分的に信頼されたアプリケーションで Web スタイル サービスを構築するためです。 [WCF Web HTTP プログラミング モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)、 [WCF 配信](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)、および[AJAX の統合と JSON のサポート](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)WCF の機能はすべて、部分的な信頼でサポートするようにされています。  
  
 ワークフロー サービスは完全信頼のアクセス許可を必要とし、部分的に信頼されたアプリケーションでは使用できません。  
  
 詳細については、次を参照してください。[する方法: ASP.NET 2.0 で使用する中程度の信頼](http://go.microsoft.com/fwlink/?LinkId=84603)です。  
  
## <a name="partial-trust-on-the-client"></a>クライアントでの部分信頼  
 信頼されていないインターネット サイトからコードをダウンロードして実行する場合、ある程度のセキュリティ対策が必要です。 [ClickOnce 展開](http://go.microsoft.com/fwlink/?LinkId=83712) と [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]の XBAP テクノロジでは共に、部分信頼を利用して信頼できないコードに制限付きのアクセス許可 (インターネット ゾーン) を与えます。  
  
 WCF は、いずれかで展開されている部分的に信頼されたアプリケーション内からリモート サーバーと通信するために使用できます[ClickOnce 配置](http://go.microsoft.com/fwlink/?LinkId=83712)または XBAP です。 インターネット ゾーン アクセス許可セットが含まれる<xref:System.Net.WebPermission>元のホスト用で説明されている、サポートされる WCF バインディングのいずれかを使用して、配信元サーバーと通信するためにこれらのアプリケーションにより[部分信頼機能の互換性](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md).  
  
## <a name="see-also"></a>関連項目  
 [コード アクセス セキュリティ](http://go.microsoft.com/fwlink/?LinkId=83717)  
 [Windows Presentation Foundation ブラウザーによってホストされるアプリケーションの概要](http://go.microsoft.com/fwlink/?LinkId=98397)  
 [部分信頼](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 [ASP.Net の中程度の信頼](http://go.microsoft.com/fwlink/?LinkId=69328)
