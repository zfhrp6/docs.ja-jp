---
title: "ASP.NET AJAX 用の WCF サービスの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 04c0402c-e617-4ba5-aedf-d17692234776
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# ASP.NET AJAX 用の WCF サービスの作成
Microsoft ASP.NET AJAX により、応答性に優れ、使い慣れたユーザー インターフェイス要素を使用して、充実したユーザー エクスペリエンスを提供する Web ページを簡単に作成できます。ASP.NET AJAX には、ブラウザーに依存しない ECMAScript \(JavaScript\) テクノロジとダイナミック HTML \(DHTML\) テクノロジを組み込んだクライアント スクリプト ライブラリが用意されており、これらのライブラリが ASP.NET 2.0 サーバー ベース開発プラットフォームと統合されます。ASP.NET AJAX を使用することで、Web アプリケーションのユーザー エクスペリエンスと効率を向上させることができます。  
  
 ASP.NET AJAX は、クライアント スクリプト ライブラリとサーバー コンポーネントを統合した強固な開発フレームワークです。ASP.NET ページからサービスにアクセスする場合、サービス URL をページ上の ASP.NET スクリプト マネージャーに追加すると、標準の JavaScript 関数の呼び出しとまったく同じに見える JavaScript コードを使い、サービス操作を呼び出すことができます。AJAX フレームワーク内での Web サービスの使用については、「[ASP.NET AJAX について](http://go.microsoft.com/fwlink/?LinkId=186475)」を参照してください。  
  
 適切な ASP.NET AJAX エンドポイントを追加すると、ほとんどの [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスを、ASP.NET AJAX 互換のサービスとして公開できます。  
  
 Visual Studio を使用する場合は、AJAX 対応 WCF サービス用のビルド済みテンプレートを使用できます。このテンプレートは、ASP.NET Web サイトまたは Web アプリケーションでの作業中に **\[新しい項目の追加\]** ダイアログ ボックスで選択できます。  
  
 Visual Studio テンプレートを使用しない場合、ASP.NET AJAX エンドポイントを作成するには次の 2 つの方法があります。  
  
-   構成を使用せずに、動的ホスト アクティブ化を使用してエンドポイントを作成する。これは、WCF 構成システムの操作に慣れていない場合の最も簡単な方法です。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][方法 : 構成を使用せずに ASP.NET AJAX エンドポイントを追加する](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
-   構成を使用して、AJAX 対応のエンドポイントを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスに追加する。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][方法 : 構成を使用して ASP.NET AJAX エンドポイントを追加する](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
 「[WCF Web HTTP プログラミング モデルの概要](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)」で説明されている Web プログラミング モデルは、ASP.NET AJAX サービスと共に使うことができます。具体的には、次のように使用します。  
  
-   <xref:System.ServiceModel.Web.WebGetAttribute> および <xref:System.ServiceModel.Web.WebInvokeAttribute> 属性を使用して、HTTP GET 動詞と HTTP POST 動詞のいずれかを選択できます。正しく使用すれば、アプリケーションのパフォーマンスを大幅に向上させることができます。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][方法 : ASP.NET AJAX エンドポイントのために HTTP POST または HTTP GET を選択する](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md).  
  
-   <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> および <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> プロパティを使用して、サービスが返すデータを、既定の JSON \(JavaScript Object Notation\) ではなく XML データにすることができます。これを ASP.NET AJAX フレームワークで行うと、JavaScript クライアントは XML DOM オブジェクトを受け取ります。  
  
    > [!WARNING]
    >  この動作を機能させるには、コンテンツ タイプを text\/xml に設定する必要があります。設定しない場合、JavaScript クライアントは XML DOM オブジェクトではなく XML を含む文字列を受け取ります。  
  
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
  
-   ASP.NET AJAX との互換性が必要な場合、<xref:System.ServiceModel.Web.WebGetAttribute> および <xref:System.ServiceModel.Web.WebInvokeAttribute> 属性の他の属性は変更できません。ASP.NET AJAX 呼び出し規約に違反しない限り、Web プログラミング モデルのその他の機能を使用できます。  
  
 より高度なシナリオでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] での AJAX サポートについて、他にいくつかの詳細な事項を理解する必要があります。  
  
-   JavaScript を使用して AJAX ページ クライアントと [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス間でデータを転送する方法と、.NET Framework の型を JavaScript の型に割り当てる方法の詳細については、「[JSON などのデータ転送形式のサポート](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)」を参照してください。  
  
-   たとえば、URL ベースの認証や ASP.NET セッション情報へのアクセスなどの ASP.NET 機能を活用するには、構成で ASP.NET 互換モードを有効にします。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の AJAX エンドポイントは、ASP.NET AJAX フレームワークなしで使用できます。これを行うには、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] での AJAX サポートのサポート アーキテクチャに関する知識が必要です。このアーキテクチャについては、「[WCF Web HTTP プログラミング オブジェクト モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)」を参照してください。この方法を実行するコード例については、「[JSON および XML 形式の AJAX サービス](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md)」を参照してください。  
  
## 参照  
 [WCF Web HTTP プログラミング モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)   
 [方法 : 構成を使用せずに ASP.NET AJAX エンドポイントを追加する](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)   
 [方法 : 構成を使用して ASP.NET AJAX エンドポイントを追加する](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)   
 [方法 : ASP.NET AJAX エンドポイントのために HTTP POST または HTTP GET を選択する](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)