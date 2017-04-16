---
title: "方法 : Windows 資格情報でサービスをセキュリティで保護する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF, セキュリティ"
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
caps.latest.revision: 26
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 26
---
# 方法 : Windows 資格情報でサービスをセキュリティで保護する
ここでは、Windows ドメイン内に存在し、同じドメイン内のクライアントから呼び出される [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービスで転送セキュリティを有効にする方法について説明します。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]このシナリオを参照してください[トランスポート セキュリティと Windows 認証](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md)します。 サンプル アプリケーションについては、次を参照してください。、 [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md)サンプルです。  
  
 このトピックでは、定義済みのコントラクト インターフェイスと実装が既に存在するものとして、それに機能を追加していきます。 既存のサービスとクライアントを変更することもできます。  
  
 Windows 資格情報によるサービスのセキュリティ保護は、完全にコードで実現できます。 または、構成ファイルを使用して、一部のコードを省略することもできます。 このトピックでは両方の方法について説明します。 ただし、どちらか&1; つの方法だけを使うようにして、両方は使用しないでください。  
  
 最初の&3; つの手順は、コードを使用してサービスをセキュリティで保護する方法について示しています。 4 番目と&5; 番目の手順は、構成ファイルを使用して同様の操作を行う方法について示しています。  
  
## <a name="using-code"></a>コードの使用  
 サービスとクライアントの完全なコードは、このトピックの最後にある「使用例」のセクションに記載されています。  
  
 作成して構成する最初の手順では、説明、 <xref:System.ServiceModel.WSHttpBinding>コード内のクラスです。 バインディングでは HTTP トランスポートを使用します。 同じバインディングがクライアント上で使用されます。  
  
#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a>Windows 資格情報とメッセージ セキュリティを使用する WSHttpBinding を作成するには  
  
1.  この手順のコードは、「使用例」のセクションに記載されたサービス コードの `Run` クラスの `Test` メソッドの先頭に挿入されています。  
  
2.  インスタンスを作成、 <xref:System.ServiceModel.WSHttpBinding>クラスです。  
  
3.  設定、 <xref:System.ServiceModel.WsHttpSecurity.Mode%2A>のプロパティ、 <xref:System.ServiceModel.WsHttpSecurity>クラスを<xref:System.ServiceModel.SecurityMode>します。  
  
4.  設定、 <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A>のプロパティ、 <xref:System.ServiceModel.MessageSecurityOverHttp>クラスを<xref:System.ServiceModel.MessageCredentialType>します。  
  
5.  この手順で使用するコードは、次のようになります。  
  
     [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
     [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]  
  
### <a name="using-the-binding-in-a-service"></a>サービスでのバインディングの使用  
 この&2; 番目の手順では、自己ホスト型サービスでバインディングを使用する方法を示します。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]ホスティング サービスを参照してください[ホスティング サービス](../../../docs/framework/wcf/hosting-services.md)します。  
  
##### <a name="to-use-a-binding-in-a-service"></a>サービスでバインディングを使用するには  
  
1.  前の手順のコードの後に、この手順のコードを挿入します。  
  
2.  作成、<xref:System.Type>という名前の変数`contractType`インターフェイスの型を割り当てると (`ICalculator`)。 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] を使用している場合は、`GetType` 演算子を使用し、C# を使用している場合は、`typeof` キーワードを使用します。  
  
3.  `Type` という名前の&2; つ目の `serviceType` 変数を作成し、その変数に実装されたコントラクトの型 (`Calculator`) を割り当てます。  
  
4.  インスタンスを作成、 <xref:System.Uri>という名前のクラス`baseAddress`サービスのベース アドレスを使用します。 ベース アドレスには、トランスポートに一致するスキームを指定する必要があります。 この場合、トランスポート スキームは HTTP であり、アドレスは、特別な URI (Uniform Resource Identifier) の "localhost"、ポート番号 (8036)、およびベース エンドポイント アドレス ("serviceModelSamples/) で構成されます。つまり、http://localhost:8036/serviceModelSamples/ になります。  
  
5.  インスタンスを作成、 <xref:System.ServiceModel.ServiceHost>クラス、`serviceType`と`baseAddress`変数です。  
  
6.  `contractType`、バインディング、およびエンドポイント名 (secureCalculator) を使用して、サービスにエンドポイントを追加します。 クライアントは、サービスへの呼び出しを開始するときに、ベース アドレスとエンドポイント名を連結する必要があります。  
  
7.  呼び出す、<xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>サービスを開始するメソッドです。 この手順で使用するコードは次のとおりです。  
  
     [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
     [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]  
  
### <a name="using-the-binding-in-a-client"></a>クライアントでのバインディングの使用  
 この手順では、サービスと通信するプロキシの生成方法を示します。 プロキシが生成、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)サービス メタデータを使用してプロキシを作成します。  
  
 このプロシージャのインスタンスの作成も、 <xref:System.ServiceModel.WSHttpBinding>サービスと通信するクラスし、サービスが呼び出されます。  
  
 この例では、コードだけを使用してクライアントを作成します。 この手順の後のセクションに示す構成ファイルを使用することもできます。  
  
##### <a name="to-use-a-binding-in-a-client-with-code"></a>コードによってクライアントでバインディングを使用するには  
  
1.  SvcUtil.exe ツールを使用して、サービスのメタデータからプロキシ コードを生成します。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][方法: クライアントを作成する](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)です。 生成されたプロキシ コードが継承、 <xref:System.ServiceModel.ClientBase%601>クラスで、必要なコンス トラクター、メソッド、およびプロパティと通信するすべてのクライアントがあることを確認、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]サービスです。 この例では、生成されたコードに、`CalculatorClient` インターフェイスを実装した `ICalculator` クラスが追加されるので、サービス コードとの互換が可能になります。  
  
2.  この手順のコードは、クライアント プログラムの `Main` メソッドの先頭に挿入します。  
  
3.  インスタンスを作成、 <xref:System.ServiceModel.WSHttpBinding>クラスし、そのセキュリティ モードを設定`Message`とそのクライアントの資格情報の種類`Windows`します。 この例では、変数に `clientBinding` という名前を付けます。  
  
4.  インスタンスを作成、 <xref:System.ServiceModel.EndpointAddress>という名前のクラス`serviceAddress`します。 エンドポイント名が連結されたベース アドレスでインスタンスを初期化します。  
  
5.  `serviceAddress` 変数と `clientBinding` 変数を指定して、生成されたクライアント クラスのインスタンスを作成します。  
  
6.  呼び出す、<xref:System.ServiceModel.ClientBase%601.Open%2A>メソッドを次のコードに示すようにします。  
  
7.  サービスを呼び出し、結果を表示します。  
  
     [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
     [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]  
  
## <a name="using-the-configuration-file"></a>構成ファイルの使用  
 手順コードを使用してバインディングを作成する代わりに、構成ファイルのバインディング セクションに次のコードを記述することもできます。  
  
 定義されているサービスがあるない場合は、次を参照してください。[を設計および実装するサービス](../../../docs/framework/wcf/designing-and-implementing-services.md)、および[サービスを構成する](../../../docs/framework/wcf/configuring-services.md)です。  
  
 **注**サービスとクライアントの両方の構成ファイルでこの構成コードを使用します。  
  
#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a>構成を使用して Windows ドメインのサービスで転送セキュリティを有効にするには  
  
1.  追加、 [ <> \> ](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)要素を[ <> \> ](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)構成ファイルの要素のセクションです。  
  
2.  <`binding`> 要素に <`WSHttpBinding`> 要素を追加し、`configurationName` 属性をアプリケーションに適した値に設定します。  
  
3.  <`security`> 要素を追加し、`mode` 属性を Message に設定します。  
  
4.  <`message`> 要素を追加し、`clientCredentialType` 属性を Windows に設定します。  
  
5.  サービスの構成ファイルで、`<bindings>` セクションを次のコードに置き換えます。 サービス構成ファイルがあるない場合は、次を参照してください。[を使用してサービスを構成すると、クライアントのバインド](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)します。  
  
    ```  
    <bindings>  
      <wsHttpBinding>  
       <binding name = "wsHttpBinding_Calculator">  
         <security mode="Message">  
           <message clientCredentialType="Windows"/>  
         </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    ```  
  
### <a name="using-the-binding-in-a-client"></a>クライアントでのバインディングの使用  
 この手順では、サービスと通信するプロキシと構成ファイルの&2; つのファイルの生成方法を示します。 また、クライアント上で使用される&3; つ目のファイルであるクライアント プログラムへの変更点についても説明します。  
  
##### <a name="to-use-a-binding-in-a-client-with-configuration"></a>構成によってクライアントでバインディングを使用するには  
  
1.  SvcUtil.exe ツールを使用して、サービスのメタデータからプロキシ コードと構成ファイルを生成します。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][方法: クライアントを作成する](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)です。  
  
2.  置き換える、 [ <> \> ](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)の構成コードは、前のセクションを生成された構成ファイルのセクションです。  
  
3.  手順コードは、クライアント プログラムの `Main` メソッドの先頭に挿入します。  
  
4.  生成されたクライアント クラスのインスタンスを作成します。このとき、構成ファイルのバインディングの名前を入力パラメーターとして渡します。  
  
5.  呼び出す、<xref:System.ServiceModel.ClientBase%601.Open%2A>メソッドを次のコードに示すようにします。  
  
6.  サービスを呼び出し、結果を表示します。  
  
     [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]  
  
## <a name="example"></a>例  
 [!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]  
  
 [!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)]
 [!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.WSHttpBinding>   
 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)   
 [方法: クライアントを作成します。](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)   
 [サービスのセキュリティ保護](../../../docs/framework/wcf/securing-services.md)   
 [セキュリティの概要](../../../docs/framework/wcf/feature-details/security-overview.md)