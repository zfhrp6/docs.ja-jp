---
title: "方法 : メタデータの取得および準拠サービスの実装をする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# 方法 : メタデータの取得および準拠サービスの実装をする
サービスのデザイン担当者と実装担当者が同じであるとは限りません。 アプリケーションの相互運用が重要な環境では、コントラクトを Web サービス記述言語 (WSDL) でデザインまたは記述した場合、開発者はそのコントラクトに準拠するサービスを実装する必要があります。 既存のサービスを [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] に移行することもできますが、その物理メッセージ フォーマットを維持しなければなりません。 さらに、双方向コントラクトでは、呼び出し元でコールバック コントラクトを実装する必要もあります。  
  
 このような場合は、使用する必要があります、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) (または同等のツール) をコントラクトの要件を満たすために実装可能なマネージ言語でサービス コントラクト インターフェイスを生成します。 通常、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)が、チャネル ファクトリを使用するサービス コントラクトを取得するために使用または[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]クライアントの種類と同様に、正しいバインディングとアドレスを設定するクライアント構成ファイルもあります。 生成された構成ファイルを使用するには、それをサービスの構成ファイルに変更する必要があります。 また、サービス コントラクトを変更する必要もあります。  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a>データを取得して準拠サービスを実装するには  
  
1.  使用して、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)メタデータ ファイルまたはコード ファイルを生成するメタデータ エンドポイントに対してです。  
  
2.  マークされている (ある場合は&1; つ以上の) で関係のあるインターフェイスが含まれる出力コード ファイルの部分の検索、 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=fullName>属性です。 次のコード例によって生成された&2; つのインターフェイスを示しています。 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)します。 最初の例 (`ISampleService`) は、準拠サービスを作成するために実装するサービス コントラクト インターフェイスです。 2 番目 (`ISampleServiceChannel`)、サービス コントラクト インターフェイスを拡張するクライアント用のヘルパー インターフェイスですし、 <xref:System.ServiceModel.IClientChannel?displayProperty=fullName>クライアント アプリケーションで使用されます。  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3.  WSDL がすべての操作に対する応答アクションを指定していない場合、生成後の操作コントラクトがあります、 <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A>プロパティがワイルドカード文字 (*) に設定します。 このプロパティの設定を削除します。 削除しない場合は、サービス コントラクト メタデータを実装するときに、それらの操作のメタデータをエクスポートできません。  
  
4.  クラスにインターフェイスを実装してサービスをホストします。 例については、次を参照してください。[方法: サービス コントラクトを実装する](../../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)、または例」のセクションの下の単純な実装を参照してください。  
  
5.  クライアント構成ファイルを[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)生成されると、変更、 [ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/client.md)構成セクションに、 [ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/services.md)構成セクション。 (生成されたクライアント アプリケーション構成ファイルの例については、次の例を参照してください)。  
  
6.  内で、 [ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/services.md)構成セクションで、作成、`name`属性、 [ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/services.md)サービス実装の構成セクション。  
  
7.  サービスの `name` 属性をユーザーのサービス実装の構成名に設定します。  
  
8.  実装するサービス コントラクトを使用するエンドポイント構成要素をサービス構成セクションに追加します。  
  
## <a name="example"></a>例  
 次のコード例を実行して、生成されたコード ファイルの大部分を示しています、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)メタデータ ファイルに対してです。  
  
 このコードには、次の項目が示されています。  
  
-   コントラクトの要件に準拠するサービス コントラクト インターフェイス (実装する場合) (`ISampleService`)。  
  
-   サービス コントラクト インターフェイスを拡張するクライアント用のヘルパー インターフェイスと<xref:System.ServiceModel.IClientChannel?displayProperty=fullName>クライアント アプリケーションで使用されます (`ISampleServiceChannel`)。  
  
-   拡張するヘルパー クラス<xref:System.ServiceModel.ClientBase%601?displayProperty=fullName>クライアント アプリケーションで使用されます (`SampleServiceClient`)。  
  
-   サービスから生成された構成ファイル。  
  
-   `ISampleService` サービスの簡単な実装。  
  
-   クライアント側の構成ファイルからサービス側バージョンへの変換。  
  
 [!code-csharp[ClientProxyCodeSample#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#1)]  
  
 [!code[ClientProxyCodeSample#10](../../../../samples/snippets/common/VS_Snippets_CFX/clientproxycodesample/common/client.exe.config#10)]
 [!code-csharp[ClientProxyCodeSample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/client.exe.config#10)]  
  
 [!code-csharp[ClientProxyCodeSample#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.cs#5)]  
  
 [!code[ClientProxyCodeSample#20](../../../../samples/snippets/common/VS_Snippets_CFX/clientproxycodesample/common/hostapplication.exe.config#20)]
 [!code-csharp[ClientProxyCodeSample#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.exe.config#20)]  
  
## <a name="see-also"></a>関連項目  
 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)