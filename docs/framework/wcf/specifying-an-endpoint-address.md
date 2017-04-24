---
title: "エンドポイント アドレスの指定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "アドレス指定のエンドポイント [WCF]"
ms.assetid: ac24f5ad-9558-4298-b168-c473c68e819b
caps.latest.revision: 41
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 41
---
# エンドポイント アドレスの指定
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービスを使用して行われるすべての通信では、エンドポイントが使用されます。 各<xref:System.ServiceModel.Description.ServiceEndpoint>が含まれています、<xref:System.ServiceModel.Description.ServiceEndpoint.Address%2A>、<xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A>、および<xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A>します。 コントラクトでは、使用できる操作を指定します。 バインディングでは、サービスとの通信方法を指定し、アドレスでは、サービスの場所を指定します。 各エンドポイントには、一意のアドレスを設定する必要があります。 エンドポイント アドレスがによって表される、 <xref:System.ServiceModel.EndpointAddress> 、識別子 URI (Uniform Resource) を表すサービスのアドレスを保持しているクラス、 <xref:System.ServiceModel.EndpointAddress.Identity%2A>、サービスのセキュリティ id とオプションのコレクションを表します<xref:System.ServiceModel.EndpointAddress.Headers%2A>します。 オプション ヘッダーは、エンドポイントの識別または対話のために、より詳細なアドレス指定情報を提供します。 たとえば、ヘッダーを使用して、受信メッセージの処理方法や、エンドポイントからの応答メッセージの送信先を指定できるほか、複数のサービス インスタンスが使用できる場合に、特定ユーザーからの受信メッセージの処理に使用するインスタンスを指定できます。  
  
## <a name="definition-of-an-endpoint-address"></a>エンドポイント アドレスの定義  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]、 <xref:System.ServiceModel.EndpointAddress> Ws-addressing 仕様で定義されているエンドポイント参照 (EPR) をモデル化します。  
  
 ほとんどのトランスポートの URI アドレスは、4 つの部分から構成されます。 たとえば、"http://www.fabrikam.com:322/mathservice.svc/secureEndpoint" という URI は、次の&4; つの部分から構成されます。  
  
-   スキーム : http:  
  
-   コンピューター : www.fabrikam.com  
  
-   (省略可能) ポート: 322  
  
-   パス : /mathservice.svc/secureEndpoint  
  
 EPR モデルの一部では、各エンドポイント参照は、追加の識別情報を追加する複数の参照パラメーターを伝達できます。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]、これらの参照パラメーターは、のインスタンスとしてモデル化、 <xref:System.ServiceModel.Channels.AddressHeader>クラスです。  
  
 サービスのエンドポイント アドレスはコードを使用して強制的に指定するか、構成を介して宣言として指定できます。 設置済みサービスのバインドおよびアドレスは一般的に、サービスの開発中に使用されるものとは異なるので、コード内でエンドポイントを定義することは通常、実用的ではありません。 一般に、サービス エンドポイントの定義にはコードではなく、構成を使用する方がより実用的です。 バインディング情報とアドレス情報をコードに含めないことで、変更時にアプリケーションの再コンパイルや再展開を行う必要がなくなります。 エンドポイントがコードまたは構成で指定されていない場合、ランタイムは、サービスで実装されたコントラクトごとに、1 つの既定のエンドポイントを各ベース アドレスに追加します。  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] でサービスのエンドポイント アドレスを指定するには&2; つの方法があります。 サービスに関連付けられている各エンドポイントの絶対アドレスを指定することものベース アドレスを指定することができます、 <xref:System.ServiceModel.ServiceHost>サービスのこのベース アドレスに対して相対的に定義されているこのサービスに関連付けられた各エンドポイントのアドレスを指定します。 サービスのエンドポイント アドレスを指定するには、構成とコードのいずれかで、これらの各方法を使用します。 相対アドレスを指定しない場合、サービスはベース アドレスを使用します。 サービスに対して複数のベース アドレスを設定することもできますが、サービスが各トランスポートに対して設定できるベース アドレスは&1; つに限られます。 複数のエンドポイントがある場合、各エンドポイントには異なるバインディングで構成されるため、それぞれのアドレスは一意になります。 異なるコントラクトで同じバインディングを使用するエンドポイントは同じアドレスを使用できます。  
  
 IIS でホストする場合を管理しないと、 <xref:System.ServiceModel.ServiceHost>自分をインスタンス化します。 IIS でホストしているサービスでは、サービスの .svc ファイルで指定されているアドレスが常にベース アドレスになります。 そのため、IIS でホストされるサービスのエンドポイントでは、相対エンドポイント アドレスを使用する必要があります。 完全修飾されたエンドポイント アドレスを指定すると、サービスの展開時にエラーとなる可能性があります。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][インターネット インフォメーション サービスでホストされる WCF サービスの配置](../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)します。  
  
## <a name="defining-endpoint-addresses-in-configuration"></a>構成によるエンドポイント アドレスの定義  
 構成ファイルでエンドポイントを定義するには、使用、 [ <> \> ](http://msdn.microsoft.com/ja-jp/13aa23b7-2f08-4add-8dbf-a99f8127c017)要素。  
  
 <!-- TODO: review snippet reference [!code[S_UEHelloWorld#5](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp2.config#5)]  -->  
  
 ときに、<xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>メソッドが呼び出されます (つまり、ホスト アプリケーションでは、サービスを開始しようとして)、システムは、 [ <> \> ](../../../docs/framework/configure-apps/file-schema/wcf/service.md) "UE を指定する name 属性を持つ要素。Samples.HelloService"です。 場合、 [ <> \> ](../../../docs/framework/configure-apps/file-schema/wcf/service.md)要素が見つかると、システムが、指定したクラスに読み込んで、構成ファイルで提供されるエンドポイントの定義を使用してエンドポイントを作成します。 このしくみによって、2 行のコードでサービスを読み込んで開始でき、バインディングとアドレス指定情報をコード外に維持することができます。 この方法の利点は、アプリケーションを再度コンパイルしたり、展開したりすることなく、この&2; つの情報を変更できる点です。  
  
 省略可能なヘッダーがで宣言されている、 [ <> \</> \>](../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)します。 次に示す例では、構成ファイルでサービスのエンドポイントを指定するための要素で、2 つのヘッダー (http://tempuri1.org/ からの "Gold" クライアントと http://tempuri2.org/ からの "Standard" クライアント) を識別しています。 このサービスを呼び出すクライアントが、適切な必要[ <> \> ](../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)構成ファイルにします。  
  
 <!-- TODO: review snippet reference [!code[S_UEHelloWorld#1](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp.config#1)]  -->  
  
 ヘッダーは、(上記のように) エンドポイントのすべてのメッセージに対してではなく、個別のメッセージに設定できます。 使用してこれは、 <xref:System.ServiceModel.OperationContextScope>を次の例で示すように、送信メッセージにカスタム ヘッダーを追加するクライアント アプリケーションで新しいコンテキストを作成します。  
  
 [!code-csharp[OperationContextScope#4](../../../samples/snippets/csharp/VS_Snippets_CFX/operationcontextscope/cs/client.cs#4)]
 [!code-vb[OperationContextScope#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationcontextscope/vb/client.vb#4)]  
  
## <a name="endpoint-address-in-metadata"></a>メタデータ内のエンドポイント アドレス  
 Web サービス記述言語 (WSDL) では、エンドポイント アドレスは、対応するエンドポイントの `EndpointReference` 要素内で WS-Addressing の `wsdl:port` (EPR) 要素として表されます。 EPR には、エンドポイントのアドレスのほかに、アドレスのすべてのプロパティが含まれます。 `wsdl:port` 内にある EPR では、次の例に示すように `soap:Address` を置き換えるので注意してください。  
  
  
  
## <a name="defining-endpoint-addresses-in-code"></a>コードによるエンドポイント アドレスの定義  
 コードで作成できるエンドポイント アドレス、 <xref:System.ServiceModel.EndpointAddress>クラスです。 エンドポイント アドレスに指定する URI は、完全修飾パスまたはサービスのベース アドレスを基準にしたパスです。 次のコード例のインスタンスを作成する方法、 <xref:System.ServiceModel.EndpointAddress>し、クラスに追加、 <xref:System.ServiceModel.ServiceHost>サービスをホストしているインスタンス。  
  
 次の例は、コードで完全なエンドポイント アドレスを指定する方法を示しています。  
  
 [!code-csharp[S_UEHelloWorld#2](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#2)]  
  
 次の例は、サービス ホストのベース アドレスに相対アドレス ("MyService") を追加する方法を示しています。  
  
 [!code-csharp[S_UEHelloWorld#3](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#3)]  
  
> [!NOTE]
>  プロパティ、 <xref:System.ServiceModel.Description.ServiceDescription>サービスでアプリケーションを変更しないでください以降に、 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A>メソッドを<xref:System.ServiceModel.ServiceHostBase>します。 一部のメンバーなど、<xref:System.ServiceModel.ServiceHostBase.Credentials%2A>プロパティおよび`AddServiceEndpoint`メソッド<xref:System.ServiceModel.ServiceHostBase>と<xref:System.ServiceModel.ServiceHost>、その時点以降後に変更された場合に例外をスローします。 変更を許可するメンバーもありますが、結果は未定義の状態になります。  
>   
>  同様に、クライアントで、 <xref:System.ServiceModel.Description.ServiceEndpoint>呼び出しの後に、値を変更しないでください<xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A>上、 <xref:System.ServiceModel.ChannelFactory>します。 <xref:System.ServiceModel.ChannelFactory.Credentials%2A>プロパティは、その時点以降後に変更された場合に例外をスローします。 その他のクライアント記述値は、エラーを発生させずに変更できますが、結果は未定義の状態になります。  
>   
>  かどうか、サービスまたはクライアントは勧め呼び出しの前に説明を変更すること<xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>します。  
  
## <a name="using-default-endpoints"></a>既定のエンドポイントの使用  
 エンドポイントがコードまたは構成で指定されていない場合、ランタイムは、サービスで実装されたサービス コントラクトごとに、1 つの既定のエンドポイントを各ベース アドレスに追加することで、既定のエンドポイントを提供します。 コードまたは構成では、ベース アドレスを指定することができ、既定のエンドポイントが追加されたときに<xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>で呼び出される、 <xref:System.ServiceModel.ServiceHost>します。  
  
 既定のエンドポイントは呼び出すことによって引き続き追加できますエンドポイントを明示的に指定しない場合<xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A>上、 <xref:System.ServiceModel.ServiceHost>呼び出す前に<xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>します。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]既定のエンドポイント、バインディング、および動作を参照してください[簡略化された構成](../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.EndpointAddress>   
 [サービス Id と認証](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)   
 [エンドポイントの作成の概要](../../../docs/framework/wcf/endpoint-creation-overview.md)   
 [ホストしています。](../../../docs/framework/wcf/feature-details/hosting.md)