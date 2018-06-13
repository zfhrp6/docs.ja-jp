---
title: ASP.NET AJAX 用の WCF サービスの作成
ms.date: 03/30/2017
ms.assetid: 04c0402c-e617-4ba5-aedf-d17692234776
ms.openlocfilehash: c2d56380b626cd0eafc178b4db3584883b00a6bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492972"
---
# <a name="creating-wcf-services-for-aspnet-ajax"></a>ASP.NET AJAX 用の WCF サービスの作成
Microsoft ASP.NET AJAX により、応答性に優れ、使い慣れたユーザー インターフェイス要素を使用して、充実したユーザー エクスペリエンスを提供する Web ページを簡単に作成できます。 ASP.NET AJAX には、ブラウザーに依存しない ECMAScript (JavaScript) テクノロジとダイナミック HTML (DHTML) テクノロジを組み込んだクライアント スクリプト ライブラリが用意されており、これらのライブラリが ASP.NET 2.0 サーバー ベース開発プラットフォームと統合されます。 ASP.NET AJAX を使用することで、Web アプリケーションのユーザー エクスペリエンスと効率を向上させることができます。  
  
 ASP.NET AJAX は、クライアント スクリプト ライブラリとサーバー コンポーネントを統合した強固な開発フレームワークです。 ASP.NET ページからサービスにアクセスする場合、サービス URL をページ上の ASP.NET スクリプト マネージャーに追加すると、標準の JavaScript 関数の呼び出しとまったく同じに見える JavaScript コードを使い、サービス操作を呼び出すことができます。 参照してください[ASP.NET AJAX の学習](http://go.microsoft.com/fwlink/?LinkId=186475)AJAX フレームワーク内で Web サービスの使用に関するします。  
  
 ほとんどの Windows Communication Foundation (WCF) サービスは、適切な ASP.NET AJAX エンドポイントを追加することで ASP.NET AJAX と互換性のあるサービスとして公開する可能性があります。  
  
 Visual Studio を使用している場合で、AJAX 対応 WCF サービスの構築済みテンプレートを使用することがあります、**新しい項目の追加**ダイアログ ASP.NET Web サイトや Web アプリケーションを使用する場合。  
  
 Visual Studio テンプレートを使用しない場合、ASP.NET AJAX エンドポイントを作成するには次の 2 つの方法があります。  
  
-   構成を使用せずに、動的ホスト アクティブ化を使用してエンドポイントを作成する。 これは、WCF 構成システムの操作に慣れていない場合の最も簡単な方法です。 詳細については、次を参照してください。[する方法: ASP.NET AJAX エンドポイントなしを使用して構成を追加](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)です。  
  
-   構成を使用して WCF サービスに AJAX 対応エンドポイントを追加します。 詳細については、次を参照してください。[する方法: ASP.NET AJAX エンドポイントを追加する構成を使用する](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)です。  
  
 説明されている Web プログラミング モデル、 [WCF Web HTTP プログラミング モデルの概要](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)は ASP.NET AJAX サービスで使用できます。 具体的には、次のように使用します。  
  
-   <xref:System.ServiceModel.Web.WebGetAttribute> および <xref:System.ServiceModel.Web.WebInvokeAttribute> 属性を使用して、HTTP GET 動詞と HTTP POST 動詞のいずれかを選択できます。 正しく使用すれば、アプリケーションのパフォーマンスを大幅に向上させることができます。 詳細については、次を参照してください。[する方法: ASP.NET AJAX エンドポイントに対して HTTP POST または HTTP GET 要求を選択](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)です。  
  
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
  
-   ASP.NET AJAX との互換性が必要な場合、<xref:System.ServiceModel.Web.WebGetAttribute> および <xref:System.ServiceModel.Web.WebInvokeAttribute> 属性の他の属性は変更できません。 ASP.NET AJAX 呼び出し規則に違反しない限り、Web プログラミング モデルのその他の機能を使用できます。  
  
 高度なシナリオでは、WCF での AJAX サポートの追加の詳細情報が認識する必要があります。  
  
-   データの転送方法と詳細については、AJAX ページのクライアントと JavaScript を使用して WCF サービスの間で .NET Framework の型を JavaScript の型にマップする方法を理解するのを参照してください。 [JSON とその他のデータ転送形式のサポート](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)です。  
  
-   たとえば、URL ベースの認証や ASP.NET セッション情報へのアクセスなどの ASP.NET 機能を活用するには、構成で ASP.NET 互換モードを有効にします。  
  
 ASP.NET AJAX フレームワークなしで WCF AJAX エンドポイントで使用できます可能性があります。 これを行うには、WCF での AJAX サポートのサポート アーキテクチャを理解することが必要です。 このアーキテクチャの詳細については、次を参照してください。 [WCF Web HTTP プログラミング オブジェクト モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)です。 この方法を示すコード サンプルは、次を参照してください。、 [JSON と XML での AJAX サービス](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md)です。  
  
## <a name="see-also"></a>関連項目  
 [WCF Web HTTP プログラミング モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [方法 : 構成を使用せずに ASP.NET AJAX エンドポイントを追加する](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)  
 [方法 : 構成を使用して ASP.NET AJAX エンドポイントを追加する](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)  
 [方法 : ASP.NET AJAX エンドポイントのために HTTP POST または HTTP GET を選択する](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)
