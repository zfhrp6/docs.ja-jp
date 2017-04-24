---
title: "方法 : カスタムの信頼できるセッションによる HTTPS を使用したバインディングを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# 方法 : カスタムの信頼できるセッションによる HTTPS を使用したバインディングを作成する
ここでは、信頼できるセッションを使用した SSL \(Secure Sockets Layer\) トランスポート セキュリティの使用方法について説明します。  HTTPS 上で信頼できるセッションを使用するには、信頼できるセッションと HTTPS トランスポートを使用するカスタム バインディングを作成する必要があります。  信頼できるセッションを有効にするには、コードを使用して強制的に行うか、構成ファイルで宣言します。  この手順では、クライアントとサービスの構成ファイルを使用して、信頼できるセッションと [\<httpsTransport\>](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) 要素を有効にします。  
  
 この手順で重要なのは、`endpoint` 構成要素に "reliableSessionOverHttps" という名前のカスタム バインディング構成を参照する `bindingConfiguration` 属性が含まれていることです。  その後、[\<binding\>](../../../../docs/framework/misc/binding.md) 構成要素は、この名前を参照して、`reliableSession` 要素と `httpsTransport` 要素を含めることにより、信頼できるセッションと HTTPS トランスポートの使用を指定できます。  
  
 この例のソースのコピーについては、「[HTTPS を介したカスタム バインディングの信頼できるセッション](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md)」を参照してください。  
  
### HTTPS で信頼できるセッションを使用するためにサービスを CustomBinding で構成するには  
  
1.  サービスの種類にサービス コントラクトを定義します。  
  
     [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]  
  
2.  サービス クラスにサービス コントラクトを実装します。  アドレス情報とバインディング情報はサービスの実装内では指定されないことに注意してください。  同様に、コードは構成ファイルから情報を取得する必要はありません。  
  
     [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]  
  
3.  Web.config ファイルを作成し、信頼できるセッションと HTTPS トランスポートを使用する "reliableSessionOverHttps" というカスタムバインディングを使用して、`CalculatorService` のエンドポイントを構成します。  
  
     <!-- TODO: review snippet reference [!code[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/common/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]  -->  
  
4.  次の行を含む Service.svc ファイルを作成します。  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
5.  インターネット インフォメーション サービス \(IIS\) 仮想ディレクトリに Service.svc ファイルを配置します。  
  
### HTTPS で信頼できるセッションを使用するためにクライアントを CustomBinding で構成するには  
  
1.  コマンド ラインから [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を実行して、サービス メタデータからコードを生成します。  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  生成されたクライアントには、クライアントの実装時に満たされなければならないサービス コントラクトを定義する `ICalculator` インターフェイスが含まれます。  
  
     [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]  
  
3.  生成されたクライアント アプリケーションは `ClientCalculator` も実装します。  このサービスの実装では、アドレス情報とバインディング情報が指定されないことに注意してください。  同様に、コードは構成ファイルから情報を取得する必要はありません。  
  
     [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]  
  
4.  HTTPS トランスポートと信頼できるセッションを使用する "reliableSessionOverHttps" という名前のカスタム バインディングを構成します。  
  
     <!-- TODO: review snippet reference [!code[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/common/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]  -->  
  
5.  アプリケーションで `ClientCalculator` のインスタンスを作成し、サービス操作を呼び出します。  
  
     [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]  
  
6.  クライアントをコンパイルして実行します。  
  
## 使用例  
<!-- TODO: review snippet reference  [!CODE [Microsoft.Win32.RegistryKey#4](Microsoft.Win32.RegistryKey#4)]  -->  
  
## .NET Framework セキュリティ  
 このサンプルで使用する証明書は Makecert.exe で作成されたテスト証明書なので、ブラウザーで https:\/\/localhost\/servicemodelsamples\/service.svc のような HTTPS アドレスにアクセスしようとするとセキュリティ警告が表示されます。  
  
## 参照  
 [信頼できるセッション](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)