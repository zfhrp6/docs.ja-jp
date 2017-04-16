---
title: "方法 : 構成でクライアント バインディングを指定する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# 方法 : 構成でクライアント バインディングを指定する
この例では、電卓サービスを使用するためのクライアント コンソール アプリケーションを作成し、そのクライアントのバインディングを構成で宣言によって指定します。 クライアントがアクセスする、`CalculatorService`を実装する、`ICalculator`インターフェイス、およびサービスとを使用してクライアントの両方、 <xref:System.ServiceModel.BasicHttpBinding>クラスです。  
  
 ここで説明する手順は、電卓サービスが実行されていることを前提とします。 サービスを構築する方法については、次を参照してください。[方法: 構成では、サービス バインドを指定](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)します。 使用して、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)を[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]クライアント コンポーネントを自動的に生成を提供します。 このツールにより、サービスにアクセスするためのクライアント コードと構成が生成されます。  
  
 クライアントは&2; つの部分で構成されます。 Svcutil.exe によって、`ClientCalculator` インターフェイスを実装する `ICalculator` が生成されます。 次に、`ClientCalculator` のインスタンスを作成することで、クライアント アプリケーションを作成します。  
  
 通常、ベスト プラクティスは、コードで命令として記述するよりも、構成でバインディングを指定して情報を明示的にアドレス指定することです。 設置済みサービスのバインドおよびアドレスは一般的に、サービスの開発中に使用されるものとは異なるので、コード内でエンドポイントを定義することは通常、実用的ではありません。 一般的に、バインディング情報とアドレス情報をコードに含めないことで、変更時にアプリケーションの再コンパイルや再展開を行う必要がなくなります。  
  
 次の構成手順のすべてを実行するにを使用して、[構成エディター ツール (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)します。  
  
 この例のソースのコピー、表示、 [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md)サンプルです。  
  
### <a name="specifying-a-client-binding-in-configuration"></a>構成を使用したクライアント バインディングの指定  
  
1.  コマンド ラインから Svcutil.exe を実行して、サービス メタデータからコードを生成します。  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  生成されたクライアントには、クライアントの実装時に満たされなければならないサービス コントラクトを定義する `ICalculator` インターフェイスが含まれます。  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3.  生成されたクライアントは `ClientCalculator` も実装します。  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4.  Svcutil.exe を使用するクライアントの構成を生成も、 <xref:System.ServiceModel.BasicHttpBinding>クラスです。 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] を使用する場合、このファイルに App.config という名前を付けます。 このサービスの実装では、アドレス情報とバインディング情報が指定されないことに注意してください。 同様に、コードは構成ファイルから情報を取得する必要はありません。  
  
     [!code[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/common/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]  
  
5.  アプリケーションで `ClientCalculator` のインスタンスを作成し、サービス操作を呼び出します。  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6.  クライアントをコンパイルして実行します。  
  
## <a name="see-also"></a>関連項目  
 [バインドを使用してサービスとクライアントを構成するには](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)