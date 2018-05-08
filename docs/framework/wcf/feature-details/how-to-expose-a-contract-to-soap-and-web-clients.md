---
title: '方法 : コントラクトを SOAP クライアントおよび Web クライアントに公開する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
ms.openlocfilehash: a9a730fe94d1df8c887a2eaf20c1e338bd056ed5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-expose-a-contract-to-soap-and-web-clients"></a>方法 : コントラクトを SOAP クライアントおよび Web クライアントに公開する
既定では、Windows Communication Foundation (WCF) を使用可能エンドポイント SOAP クライアントにのみです。 [する方法: 基本的な WCF Web HTTP サービスを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)エンドポイントが SOAP 以外のクライアントを使用できます。 状況によっては、同じコントラクトを Web エンドポイントと SOAP エンドポイントのどちらとしても利用できることが望ましい場合があります。 ここでは、これを実現する方法の例について示します。  
  
### <a name="to-define-the-service-contract"></a>サービス コントラクトを定義するには  
  
1.  次のコードのように、<xref:System.ServiceModel.ServiceContractAttribute>、<xref:System.ServiceModel.Web.WebInvokeAttribute> および <xref:System.ServiceModel.Web.WebGetAttribute> の各属性でマークされたインターフェイスを使用して、サービス コントラクトを定義します。  
  
     [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
     [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]  
  
    > [!NOTE]
    >  既定では、<xref:System.ServiceModel.Web.WebInvokeAttribute> は POST 呼び出しを操作にマッピングします。 ただし、"method=" パラメーターを指定することで、操作にマッピングするメソッドを指定できます。 <xref:System.ServiceModel.Web.WebGetAttribute> には "method=" パラメーターがないため、サービス操作には GET 呼び出しのみがマッピングされます。  
  
2.  次のコードに示すように、サービス コントラクトを実装します。  
  
     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]  
  
### <a name="to-host-the-service"></a>サービスをホストするには  
  
1.  次のコードに示すように、<xref:System.ServiceModel.ServiceHost> オブジェクトを作成します。  
  
     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]  
  
2.  次のコードに示すように、SOAP 以外のエンドポイント用に、<xref:System.ServiceModel.Description.ServiceEndpoint> に <xref:System.ServiceModel.BasicHttpBinding> を追加します。  
  
     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]  
  
3.  次のコードに示すように、SOAP 以外のエンドポイント用に、<xref:System.ServiceModel.Description.ServiceEndpoint> に <xref:System.ServiceModel.WebHttpBinding> を追加し、エンドポイントに <xref:System.ServiceModel.Description.WebHttpBehavior> を追加します。  
  
     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]  
  
4.  次のコードに示すように、`Open()` を <xref:System.ServiceModel.ServiceHost> インスタンスで呼び出して、サービス ホストを開きます。  
  
     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]  
  
### <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a>Internet Explorer で GET にマッピングされたサービス操作を呼び出すには  
  
1.  Internet Explorer を開き「"`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`"し、ENTER キーを押します。 URL には、サービスのベース アドレスが含まれています ("http://localhost:8000/")、エンドポイントの相対アドレス ("")、アンパサンドで区切られた名前付きパラメーターの一覧の後に、サービス操作呼び出し ("EchoWithGet")、疑問符 () (&)。  
  
### <a name="to-call-service-operations-on-the-web-endpoint-in-code"></a>コードから Web エンドポイントにあるサービス操作を呼び出すには  
  
1.  次のコードに示すように、<xref:System.ServiceModel.Web.WebChannelFactory%601> のインスタンスを `using` ブロック内に作成します。  
  
     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]  
  
> [!NOTE]
>  `Close()` は `using` ブロックの末尾のチャネルで自動的に呼び出されます。  
  
1.  次のコードに示すように、チャネルを作成してサービスを呼び出します。  
  
     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]  
  
### <a name="to-call-service-operations-on-the-soap-endpoint"></a>SOAP エンドポイントにあるサービス操作を呼び出すには  
  
1.  次のコードに示すように、<xref:System.ServiceModel.ChannelFactory> のインスタンスを `using` ブロック内に作成します。  
  
     [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
     [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]  
  
2.  次のコードに示すように、チャネルを作成してサービスを呼び出します。  
  
     [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
     [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]  
  
### <a name="to-close-the-service-host"></a>サービス ホストを閉じるは  
  
1.  次のコードに示すように、サービス ホストを閉じます。  
  
     [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
     [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]  
  
## <a name="example"></a>例  
 このトピックの完全なコードの一覧を以下に示します。  
  
 [!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
 [!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 Service.cs のコンパイル時には、System.ServiceModel.dll と System.ServiceModel.Web.dll を参照します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Web.WebServiceHost>  
 <xref:System.ServiceModel.ChannelFactory>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [WCF Web HTTP プログラミング モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
