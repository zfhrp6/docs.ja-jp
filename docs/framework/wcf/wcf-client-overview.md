---
title: "WCF クライアントの概要 | Microsoft Docs"
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
  - "クライアント [WCF], アーキテクチャ"
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
caps.latest.revision: 17
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# WCF クライアントの概要
このセクションでは、クライアント アプリケーションの処理、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] クライアントの構成方法、作成方法、使用方法、およびクライアント アプリケーションをセキュリティで保護する方法について説明します。  
  
## <a name="using-wcf-client-objects"></a>WCF クライアント オブジェクトの使用  
 クライアント アプリケーションは、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアントを使用して別のアプリケーションと通信するマネージ アプリケーションです。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスのクライアント アプリケーションを作成するには、次の手順に従います。  
  
1.  サービス エンドポイントのサービス コントラクト、バインディング、およびアドレス情報を取得します。  
  
2.  その情報を使用して [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアントを作成します。  
  
3.  操作を呼び出します。  
  
4.  [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアント オブジェクトを閉じます。  
  
 この後の各セクションでは、これらの手順について詳しく説明します。また、次の内容についても簡単に説明します。  
  
-   エラー処理  
  
-   クライアントの構成とセキュリティ保護  
  
-   双方向サービスのコールバック オブジェクトの作成  
  
-   サービスの非同期呼び出し  
  
-   クライアント チャネルを使用したサービスの呼び出し  
  
## <a name="obtain-the-service-contract-bindings-and-addresses"></a>サービス コントラクト、バインディング、およびアドレスを取得する  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] では、サービスとクライアントは、マネージ属性、マネージ インターフェイス、およびマネージ メソッドを使用してコントラクトをモデル化します。 クライアント アプリケーションからサービスに接続するには、そのサービス コントラクトの型情報を取得する必要があります。 通常、これを行うを使用して、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)、サービスからメタデータをダウンロード、変換のファイルは、任意の言語でマネージ ソース コードに、クライアント アプリケーションの構成ファイルを作成し、構成する使用することができます、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]クライアント オブジェクトです。 たとえば、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] を呼び出す `MyCalculatorService` クライアント オブジェクトを作成するときに、そのサービスのメタデータが `http://computerName/MyCalculatorService/Service.svc?wsdl` で公開されていることがわかっている場合に、Svcutil.exe を使用してマネージ コードにサービス コントラクトが含まれている `ClientCode.vb` ファイルを取得するコード例を次に示します。  
  
```  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 このコントラクト コードをクライアント アプリケーションまたは別のアセンブリにコンパイルし、クライアント アプリケーションでそれを使用して [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアント オブジェクトを作成できます。 構成ファイルを使用してサービスに正しく接続するクライアント オブジェクトを構成できます。  
  
 このプロセスの例は、次を参照してください。[方法: クライアントを作成する](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)です。 コントラクトの詳細については、次を参照してください。[コントラクト](../../../docs/framework/wcf/feature-details/contracts.md)します。  
  
## <a name="create-a-wcf-client-object"></a>WCF クライアント オブジェクトを作成する  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアントとは、クライアントがリモート サービスとの通信に使用できる形式で [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスを表すローカル オブジェクトです。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアント型は、ターゲットのサービス コントラクトを実装します。そのため、サービス コントラクトを作成して構成すると、クライアント オブジェクトを直接使用して、サービス操作を呼び出すことができます。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]ランタイムは、メソッド呼び出しをメッセージに、サービスに送信、応答をリッスンおよびそれらの値を返します変換、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]戻り値としてクライアント オブジェクトまたは`out`または`ref`パラメーター。  
  
 また、サービスとの通信やサービスの使用に [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアント チャネル オブジェクトも使用できます。 詳細については、「 [WCF クライアント アーキテクチャ](../../../docs/framework/wcf/feature-details/client-architecture.md)します。  
  
#### <a name="creating-a-new-wcf-object"></a>新しい WCF オブジェクトの作成  
 使用方法を示す、 <xref:System.ServiceModel.ClientBase%601>クラス、サービス アプリケーションから次の単純なサービス コントラクトが生成されていると仮定します。  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] を使用して [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアントを作成する場合、サービス参照をプロジェクトに追加すると、オブジェクトはオブジェクト ブラウザーに自動的に読み込まれます。  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 使用していない場合[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]、拡張する型を検索する生成されるコントラクト コードを調べる<xref:System.ServiceModel.ClientBase%601>とサービス コントラクト インターフェイス`ISampleService`します。 この場合、この型は次のようなコードになります。  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 このクラスを、コンストラクターの&1; つを使用してローカル オブジェクトとして作成し、構成して、型 `ISampleService` のサービスへの接続に使用できます。  
  
 まず [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアント オブジェクトを作成し、それを&1; つの try/catch ブロック内で使用して閉じることをお勧めします。 特定のエラー モードで例外をマスクする場合があるため、`using` ステートメント (`Using` では [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) を使用しないでください。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]以降のセクションでも、[を使用してステートメントを使用して問題を回避する](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)です。  
  
### <a name="contracts-bindings-and-addresses"></a>コントラクト、バインディング、およびアドレス  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアント オブジェクトを作成するには、クライアント オブジェクトを構成する必要があります。 具体的には、サービスが必要*エンドポイント*を使用します。 エンドポイントは、サービス コントラクト、バインディング、およびアドレスの組み合わせです  ([!INCLUDE[crabout](../../../includes/crabout-md.md)]エンドポイントは、[エンドポイント: アドレス、バインディング、およびコントラクト](../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md))。通常、この情報に記載されて、 [ <> \> ](../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md) Svcutil.exe ツールによって生成されると、クライアント オブジェクトを作成するときに自動的に読み込まれますのものなど、クライアントのアプリケーション構成ファイル内の要素。 両方の [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアント型には、この情報をプログラムで指定できるオーバーロードもあります。  
  
 たとえば、上記の例で使用した `ISampleService` 用に生成された構成ファイルには、次のエンドポイント情報が含まれます。  
  
 [!code[C_GeneratedCodeFiles#19](../../../samples/snippets/common/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 この構成ファイルの `<client>` 要素には、ターゲット エンドポイントが指定されます。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]複数のターゲット エンドポイントを使用して表示、 <xref:System.ServiceModel.ClientBase%601.%23ctor%2A?displayProperty=fullName>または<xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A?displayProperty=fullName>コンス トラクターです。  
  
## <a name="calling-operations"></a>操作の呼び出し  
 クライアント オブジェクトを作成し構成したら、try/catch ブロックを作成し、ローカルのオブジェクトの場合と同じ方法で操作を呼び出して、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアント オブジェクトを閉じます。 クライアント アプリケーションが最初の操作を呼び出すときに、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] は、基になるチャネルを自動的に開きます。基になるチャネルはオブジェクトが再利用されるときに閉じられます  (また、他の操作を呼び出す前後にチャネルを明示的に開いたり閉じたりすることもできます)。  
  
 たとえば、次のようなサービス コントラクトを使用する場合があります。  
  
```csharp  
namespace Microsoft.ServiceModel.Samples  
{  
    using System;  
    using System.ServiceModel;  
  
    [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
    public interface ICalculator  
   {  
        [OperationContract]  
        double Add(double n1, double n2);  
        [OperationContract]  
        double Subtract(double n1, double n2);  
        [OperationContract]  
        double Multiply(double n1, double n2);  
        [OperationContract]  
        double Divide(double n1, double n2);  
    }  
}  
```  
  
```vb  
Namespace Microsoft.ServiceModel.Samples  
  
    Imports System  
    Imports System.ServiceModel  
  
    <ServiceContract(Namespace:= _  
    "http://Microsoft.ServiceModel.Samples")> _   
   Public Interface ICalculator  
        <OperationContract> _   
        Function Add(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
        Function Subtract(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
        Function Multiply(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
     Function Divide(n1 As Double, n2 As Double) As Double  
End Interface  
```  
  
 次のコード例で示すように、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアント オブジェクトを作成し、そのメソッドを呼び出すことで操作を呼び出すことができます。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアント オブジェクトのオープン、呼び出し、クローズは、1 つの try/catch ブロック内で行われます。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][WCF クライアントを使用してサービスにアクセスする](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)と[Using ステートメントに関する問題を回避する](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)です。  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a>エラー処理  
 基になるクライアント チャネルを開いたとき (明示的に開いた場合、または操作を呼び出すことによって自動的に開いた場合)、クライアントまたはチャネル オブジェクトを使用して操作を呼び出したとき、基になるクライアント チャネルを閉じたときときに、クライアント アプリケーションで例外が発生する可能性があります。 お勧め最低限のアプリケーションが可能な限りの処理を想定している<xref:System.TimeoutException?displayProperty=fullName>と<xref:System.ServiceModel.CommunicationException?displayProperty=fullName>他にも、例外<xref:System.ServiceModel.FaultException?displayProperty=fullName>操作によって返される SOAP エラーの結果としてスローされるオブジェクト。 としてクライアント アプリケーションに、操作コントラクトで指定された SOAP エラーが発生した、 <xref:System.ServiceModel.FaultException%601?displayProperty=fullName>型パラメーターが SOAP エラーの詳細型であります。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]クライアント アプリケーションでのエラー状況を処理するを参照してください[送信と受信エラー](../../../docs/framework/wcf/sending-and-receiving-faults.md)します。 完全なサンプルに示すクライアントでのエラーを処理する方法を参照してください[予想例外](../../../docs/framework/wcf/samples/expected-exceptions.md)します。  
  
## <a name="configuring-and-securing-clients"></a>クライアントの構成とセキュリティ保護  
 クライアントを構成するには、まず、そのクライアントまたはチャネル オブジェクトに必要なターゲット エンドポイント情報を読み込みます。通常は構成ファイルから読み込みますが、クライアント コンストラクターとプロパティを使用してプログラムで読み込むこともできます。 ただし、特定のクライアントの動作を有効にし、多くのセキュリティ シナリオに対応するには、追加の構成手順が必要です。  
  
 たとえば、サービス コントラクトのセキュリティ要件はサービス コントラクト インターフェイスに宣言します。Svcutil.exe で構成ファイルを作成した場合、通常そのファイルにはサービスのセキュリティ要件に対応できるバインディングが含まれています。 ただし、クライアント資格情報の構成など、さらに多くのセキュリティ構成が必要な場合もあります。 詳細については、セキュリティ構成の[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]クライアントを参照してください[クライアントのセキュリティで保護する](../../../docs/framework/wcf/securing-clients.md)です。  
  
 また、カスタム ランタイム動作など、クライアント アプリケーションでいくつかのカスタム変更を有効にすることもできます。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]カスタム クライアント動作を構成する方法[クライアントの動作の構成](../../../docs/framework/wcf/configuring-client-behaviors.md)します。  
  
## <a name="creating-callback-objects-for-duplex-services"></a>双方向サービスのコールバック オブジェクトの作成  
 双方向サービスには、コントラクトの要件に従って呼び出すサービスのコールバック オブジェクトを提供するために、クライアント アプリケーションが実装する必要のあるコールバック コントラクトを指定します。 コールバック オブジェクトは完全なサービスではありません (たとえば、コールバック オブジェクトを使用してチャネルを初期化できません) が、実装と構成という目的においては、一種のサービスとして考えることができます。  
  
 双方向サービスのクライアントでは、以下の処理を行う必要があります。  
  
-   コールバック コントラクト クラスを実装します。  
  
-   コールバック コントラクト実装クラスのインスタンスを作成し、使用して作成する、 <xref:System.ServiceModel.InstanceContext?displayProperty=fullName>に渡されたオブジェクト、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]クライアント コンス トラクターです。  
  
-   操作を呼び出し、操作のコールバックを処理します。  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] の双方向クライアント オブジェクトは、対応する非双方向クライアント オブジェクトと同じように機能します。ただし、双方向クライアント オブジェクトは、コールバック サービスの構成など、コールバックのサポートに必要な機能を公開します。  
  
 たとえば、コールバック オブジェクトのランタイム動作のさまざまな側面を制御のプロパティを使用して、 <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=fullName>コールバック クラスの属性です。 別の例は、の使用、 <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=fullName>コールバック オブジェクトを呼び出したサービスに例外情報を返すようにするクラス。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][双方向サービス](../../../docs/framework/wcf/feature-details/duplex-services.md)します。 完全なサンプルを参照してください。[双方向](../../../docs/framework/wcf/samples/duplex.md)します。  
  
 クライアントのベース アドレスを使用して、Windows XP コンピューターのインターネット インフォメーション サービス (IIS) 5.1 を実行している場合に双方向クライアントが指定する必要があります、 <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=fullName>クラス、または例外がスローされます。 次のコード例は、コードでこれを指定する方法を示します。  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 次のコードは、構成ファイルでこれを指定する方法を示します。  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a>サービスの非同期呼び出し  
 操作の呼び出し方法は、クライアント開発者に完全に依存します。 これは、操作を構成するメッセージは、マネージ コードで表現するときに同期メソッドまたは非同期メソッドのどちらかにマップできるためです。 したがって、操作を非同期に呼び出すクライアントを作成する場合、Svcutil.exe の `/async` オプションを使用して非同期クライアント コードを生成できます。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][方法: サービス操作を非同期的に呼び出す](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)します。  
  
## <a name="calling-services-using-wcf-client-channels"></a>WCF クライアント チャネルを使用したサービスの呼び出し  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]クライアント型を拡張する<xref:System.ServiceModel.ClientBase%601>から派生した<xref:System.ServiceModel.IClientChannel?displayProperty=fullName>基になるチャネル システムを公開するインターフェイスです。 サービスを起動するには、ターゲット サービス コントラクトを使用して、 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=fullName>クラスです。 詳細については、「 [WCF クライアント アーキテクチャ](../../../docs/framework/wcf/feature-details/client-architecture.md)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.ClientBase%601?displayProperty=fullName>   
 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=fullName>