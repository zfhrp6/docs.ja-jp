---
title: "ASP.NET AJAX 用の WCF サービスの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04c0402c-e617-4ba5-aedf-d17692234776
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9f13fffcfb6094b56f1cbfdffca52a1b24f437b4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="creating-wcf-services-for-aspnet-ajax"></a>ASP.NET AJAX 用の WCF サービスの作成
Microsoft ASP.NET AJAX により、応答性に優れ、使い慣れたユーザー インターフェイス要素を使用して、充実したユーザー エクスペリエンスを提供する Web ページを簡単に作成できます。 ASP.NET AJAX には、ブラウザーに依存しない ECMAScript (JavaScript) テクノロジとダイナミック HTML (DHTML) テクノロジを組み込んだクライアント スクリプト ライブラリが用意されており、これらのライブラリが ASP.NET 2.0 サーバー ベース開発プラットフォームと統合されます。 ASP.NET AJAX を使用することで、Web アプリケーションのユーザー エクスペリエンスと効率を向上させることができます。  
  
 ASP.NET AJAX は、クライアント スクリプト ライブラリとサーバー コンポーネントを統合した強固な開発フレームワークです。 ASP.NET ページからサービスにアクセスする場合、サービス URL をページ上の ASP.NET スクリプト マネージャーに追加すると、標準の JavaScript 関数の呼び出しとまったく同じに見える JavaScript コードを使い、サービス操作を呼び出すことができます。 参照してください[ASP.NET AJAX の学習](http://go.microsoft.com/fwlink/?LinkId=186475)AJAX フレームワーク内で Web サービスの使用に関するします。  
  
 適切な ASP.NET AJAX エンドポイントを追加すると、ほとんどの [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスを、ASP.NET AJAX 互換のサービスとして公開できます。  
  
 Visual Studio を使用している場合で、AJAX 対応 WCF サービスの構築済みテンプレートを使用することがあります、**新しい項目の追加**ダイアログ ASP.NET Web サイトや Web アプリケーションを使用する場合。  
  
 Visual Studio テンプレートを使用しない場合、ASP.NET AJAX エンドポイントを作成するには次の 2 つの方法があります。  
  
-   構成を使用せずに、動的ホスト アクティブ化を使用してエンドポイントを作成する。 これは、WCF 構成システムの操作に慣れていない場合の最も簡単な方法です。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][する方法: 構成を使用せずに ASP.NET AJAX エンドポイントを追加](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)です。  
  
-   構成を使用して、AJAX 対応のエンドポイントを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスに追加する。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][する方法: ASP.NET AJAX エンドポイントを追加する構成を使用して](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)です。  
  
 説明されている Web プログラミング モデル、 [WCF Web HTTP プログラミング モデルの概要](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)は ASP.NET AJAX サービスで使用できます。 具体的には、次のように使用します。  
  
-   <xref:System.ServiceModel.Web.WebGetAttribute> および <xref:System.ServiceModel.Web.WebInvokeAttribute> 属性を使用して、HTTP GET 動詞と HTTP POST 動詞のいずれかを選択できます。 正しく使用すれば、アプリケーションのパフォーマンスを大幅に向上させることができます。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][する方法: ASP.NET AJAX エンドポイントに対して HTTP POST または HTTP GET 要求を選択](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)です。  
  
-   <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> および <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> プロパティを使用して、サービスが返すデータを、既定の JSON (JavaScript Object Notation) ではなく XML データにすることができます。 これを ASP.NET AJAX フレームワークで行うと、JavaScript クライアントは XML DOM オブジェクトを受け取ります。  
  
    > [!WARNING]
    >  この動作を機能させるには、コンテンツ タイプを text/xml に設定する必要があります。 設定しない場合、JavaScript クライアントは XML DOM オブジェクトではなく XML を含む文字列を受け取ります。  
  
     コンテンツ タイプが適切に設定された XML データを返す操作の例を次に示します。  
  
    ```  
    [OperationContract, WebGet(ResponseFormat=WebMessageFormat.Xml)]  
    public XElement GetData()  
    {  
    XElement x;  
    //Get some data here...  
  
    WebOperationContext.Current.OutgoingResponse.ContentType = "text/xml";      
    return x;  
    }  
    ```  
  
-   ASP.NET AJAX との互換性が必要な場合、<xref:System.ServiceModel.Web.WebGetAttribute> および <xref:System.ServiceModel.Web.WebInvokeAttribute> 属性の他の属性は変更できません。 ASP.NET AJAX 呼び出し規約に違反しない限り、Web プログラミング モデルのその他の機能を使用できます。  
  
 より高度なシナリオでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] での AJAX サポートについて、他にいくつかの詳細な事項を理解する必要があります。  
  
-   AJAX ページのクライアントの間でデータを転送する方法を理解しておくと、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] JavaScript を使用してサービスを提供し、.NET Framework の型を JavaScript の型にマップする方法の詳細については、「 [JSON とその他のデータ転送形式のサポート](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md).  
  
-   たとえば、URL ベースの認証や ASP.NET セッション情報へのアクセスなどの ASP.NET 機能を活用するには、構成で ASP.NET 互換モードを有効にします。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の AJAX エンドポイントは、ASP.NET AJAX フレームワークなしで使用できます。 これを行うには、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] での AJAX サポートのサポート アーキテクチャに関する知識が必要です。 このアーキテクチャの詳細については、次を参照してください。 [WCF Web HTTP プログラミング オブジェクト モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)です。 この方法を示すコード サンプルは、次を参照してください。、 [JSON と XML での AJAX サービス](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md)です。  
  
## <a name="see-also"></a>関連項目  
 [WCF Web HTTP プログラミング モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [方法: 構成を使用せずに ASP.NET AJAX エンドポイントを追加](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)  
 [方法: 構成を使用して ASP.NET AJAX エンドポイントを追加するには](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)  
 [方法: ASP.NET AJAX エンドポイントに対して HTTP POST または HTTP GET 要求を選択](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)
