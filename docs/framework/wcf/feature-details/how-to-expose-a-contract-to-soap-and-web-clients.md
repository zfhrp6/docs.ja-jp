---
title: "方法 : コントラクトを SOAP クライアントおよび Web クライアントに公開する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
caps.latest.revision: 21
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 21
---
# 方法 : コントラクトを SOAP クライアントおよび Web クライアントに公開する
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、既定でエンドポイントは SOAP クライアントでのみ利用できます。  SOAP 以外のクライアントでもエンドポイントを利用できるようにする方法については、「[方法 : 基本的な WCF Web HTTP サービスを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)」を参照してください。  状況によっては、同じコントラクトを Web エンドポイントと SOAP エンドポイントのどちらとしても利用できることが望ましい場合があります。  ここでは、これを実現する方法の例について示します。  
  
### サービス コントラクトを定義するには  
  
1.  次のコードのように、<xref:System.ServiceModel.ServiceContractAttribute>、<xref:System.ServiceModel.Web.WebInvokeAttribute> および <xref:System.ServiceModel.Web.WebGetAttribute> の各属性でマークされたインターフェイスを使用して、サービス コントラクトを定義します。  
  
     [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
     [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]  
  
    > [!NOTE]
    >  既定では、<xref:System.ServiceModel.Web.WebInvokeAttribute> は POST 呼び出しを操作にマッピングします。  ただし、"method\=" パラメーターを指定することで、操作にマッピングするメソッドを指定できます。  <xref:System.ServiceModel.Web.WebGetAttribute> には "method\=" パラメーターがないため、サービス操作には GET 呼び出しのみがマッピングされます。  
  
2.  次のコードに示すように、サービス コントラクトを実装します。  
  
     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]  
  
### サービスをホストするには  
  
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
  
### Internet Explorer で GET にマッピングされたサービス操作を呼び出すには  
  
1.  Internet Explorer を開いて「`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`」と入力し、Enter キーを押します。  この URL には、サービスのベース アドレス \("http:\/\/localhost:8000\/"\) が含まれており、エンドポイントの相対アドレス \(""\)、呼び出すサービス操作 \("EchoWithGet"\)、疑問符の後にアンパサンド \(&\) で区切られた名前付きパラメーターのリストが続きます。  
  
### コードから Web エンドポイントにあるサービス操作を呼び出すには  
  
1.  次のコードに示すように、<xref:System.ServiceModel.Web.WebChannelFactory%601> のインスタンスを `using` ブロック内に作成します。  
  
     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]  
  
> [!NOTE]
>  `Close()` は `using` ブロックの末尾のチャネルで自動的に呼び出されます。  
  
1.  次のコードに示すように、チャネルを作成してサービスを呼び出します。  
  
     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]  
  
### SOAP エンドポイントにあるサービス操作を呼び出すには  
  
1.  次のコードに示すように、<xref:System.ServiceModel.ChannelFactory> のインスタンスを `using` ブロック内に作成します。  
  
     [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
     [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]  
  
2.  次のコードに示すように、チャネルを作成してサービスを呼び出します。  
  
     [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
     [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]  
  
### サービス ホストを閉じるは  
  
1.  次のコードに示すように、サービス ホストを閉じます。  
  
     [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
     [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]  
  
## 使用例  
 このトピックの完全なコードの一覧を以下に示します。  
  
 [!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
 [!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]  
  
## コードのコンパイル  
 Service.cs のコンパイル時には、System.ServiceModel.dll と System.ServiceModel.Web.dll を参照します。  
  
## 参照  
 <xref:System.ServiceModel.WebHttpBinding>   
 <xref:System.ServiceModel.Web.WebGetAttribute>   
 <xref:System.ServiceModel.Web.WebInvokeAttribute>   
 <xref:System.ServiceModel.Web.WebServiceHost>   
 <xref:System.ServiceModel.ChannelFactory>   
 <xref:System.ServiceModel.Description.WebHttpBehavior>   
 [WCF Web HTTP プログラミング モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)