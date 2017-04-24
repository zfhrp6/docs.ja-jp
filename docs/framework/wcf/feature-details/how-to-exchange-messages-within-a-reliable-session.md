---
title: "方法 : 信頼されたセッション内のメッセージを変換する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# 方法 : 信頼されたセッション内のメッセージを変換する
このトピックでは、信頼できるセッションを有効にするために必要な手順について説明します。ここでは、信頼できるセッションを \(既定ではなく\) オプションでサポートするシステム指定のバインディングを使用します。信頼できるセッションはコードを使用して強制的に有効にするか、構成ファイルで宣言して有効にします。この手順では、クライアントとサービスの構成ファイルを使用して、信頼できるセッションを有効にし、送信された順序でメッセージが受信されるように指定します。  
  
 この手順で重要なのは、エンドポイント構成要素に "Binding1" という名前のバインディング構成を参照する `bindingConfiguration` 属性が含まれていることです。[\<binding\>](../../../../docs/framework/misc/binding.md) 構成要素は、この名前を参照して、[reliableSession](http://msdn.microsoft.com/ja-jp/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) 要素の `enabled` 属性を `true` に設定することで信頼できるセッションを有効にします。信頼できるセッションで順序付き配信の保証を指定するには、`ordered` 属性を `true` に設定します。  
  
 この例のソースのコピーについては、「[WS 信頼できるセッション](../../../../docs/framework/wcf/samples/ws-reliable-session.md)」を参照してください。  
  
### 信頼できるセッションを使用するためにサービスを WSHttpBinding で構成するには  
  
1.  サービスの種類にサービス コントラクトを定義します。  
  
     [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]  
  
2.  サービス クラスにサービス コントラクトを実装します。アドレス情報とバインディング情報はサービスの実装内では指定されないことに注意してください。同様に、コードは構成ファイルから情報を取得する必要はありません。  
  
     [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]  
  
3.  Web.config ファイルを作成し、信頼できるセッションが有効で、メッセージの順序付き配信を要求する <xref:System.ServiceModel.WSHttpBinding> を使用する `CalculatorService` のエンドポイントを構成します。  
  
     <!-- TODO: review snippet reference [!code[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/common/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]  -->  
  
4.  次の行を含む Service.svc ファイルを作成します。  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
5.  インターネット インフォメーション サービス \(IIS\) 仮想ディレクトリに Service.svc ファイルを配置します。  
  
### 信頼できるセッションを使用するためにクライアントを WSHttpBinding で構成するには  
  
1.  コマンド ラインから [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を実行して、サービス メタデータからコードを生成します。  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  生成されたクライアントには、クライアントの実装時に満たされなければならないサービス コントラクトを定義する `ICalculator` インターフェイスが含まれます。  
  
     [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]  
  
3.  生成されたクライアント アプリケーションは `ClientCalculator` も実装します。このサービスの実装では、アドレス情報とバインディング情報が指定されないことに注意してください。同様に、コードは構成ファイルから情報を取得する必要はありません。  
  
     [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]  
  
4.  <xref:System.ServiceModel.WSHttpBinding> クラスを使用するクライアントの構成も、Svcutil.exe により生成されます。[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] を使用する場合、このファイルには App.config という名前を付ける必要があります。  
  
     <!-- TODO: review snippet reference [!code[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/common/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]  -->  
  
5.  アプリケーションで `ClientCalculator` のインスタンスを作成し、サービス操作を呼び出します。  
  
     [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]  
  
6.  クライアントをコンパイルして実行します。  
  
## 使用例  
<!-- TODO: review snippet reference  [!CODE [Microsoft.Win32.RegistryKey#4](Microsoft.Win32.RegistryKey#4)]  -->  
  
 システム指定のバインディングの中には、信頼できるセッションを既定でサポートするものがあります。具体的には、次のようなバインディングです。  
  
-   <xref:System.ServiceModel.WSDualHttpBinding>  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>  
  
-   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>  
  
 信頼できるセッションをサポートするカスタム バインディングを作成する方法の例については、「[方法 : カスタムの信頼できるセッションによる HTTPS を使用したバインディングを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)」を参照してください。  
  
## 参照  
 [信頼できるセッション](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)