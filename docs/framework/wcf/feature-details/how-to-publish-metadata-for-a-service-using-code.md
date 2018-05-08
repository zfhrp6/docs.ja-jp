---
title: '方法: コードを使用してサービスのメタデータを公開する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
ms.openlocfilehash: bef5421d377bcae6e8c56b0117ebbe22a861de86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a>方法: コードを使用してサービスのメタデータを公開する
これは、Windows Communication Foundation (WCF) サービスのメタデータの公開の方法を説明している 2 つの操作方法に関するトピックのいずれかです。 構成ファイルとコードを使用して、サービスがメタデータを公開する手段を指定する方法は 2 つあります。 このトピックでは、コードを使用してサービスのメタデータを公開する方法について説明します。  
  
> [!CAUTION]
>  このトピックでは、セキュリティで保護されていない方法でメタデータを公開する方法について説明します。 クライアントは、サービスからメタデータを取得できます。 セキュリティで保護された方法でメタデータを公開するサービスが必要な場合は、 参照してください[カスタム セキュリティで保護されたメタデータ エンドポイント](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)です。  
  
 構成ファイルのメタデータの公開の詳細については、次を参照してください。[する方法: 構成ファイルを使用して、サービスのメタデータを公開](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)です。 メタデータを公開すると、クライアントが `?wsdl` クエリ文字列を使用した WS-Transfer GET 要求または HTTP/GET 要求によりメタデータを取得できるようになります。 コードを機能させるには、基本的な WCF サービスを作成する必要があります。 次のコードは基本的な自己ホスト型サービスの例です。  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a>コードでメタデータを公開するには  
  
1.  コンソール アプリケーションのメイン メソッド内で、サービス型とベース アドレスを渡して <xref:System.ServiceModel.ServiceHost> オブジェクトをインスタンス化します。  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2.  手順 1. のコードのすぐ下に try ブロックを作成します。これにより、サービスの実行中にスローされる例外がすべてキャッチされます。  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3.  サービス ホストに <xref:System.ServiceModel.Description.ServiceMetadataBehavior> が含まれているかどうかを確認し、含まれていない場合は、新しい <xref:System.ServiceModel.Description.ServiceMetadataBehavior> インスタンスを作成します。  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4.  <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> プロパティを `true.` に設定します。  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5.  <xref:System.ServiceModel.Description.ServiceMetadataBehavior> には <xref:System.ServiceModel.Description.MetadataExporter> プロパティが含まれています。 <xref:System.ServiceModel.Description.MetadataExporter> には <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> プロパティが含まれています。 <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> プロパティの値を <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> に設定します。 <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> プロパティを <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> に設定することもできます。 設定すると<xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>メタデータ エクスポーターがメタデータとポリシー情報を生成する"Ws-policy 1.5 に準拠しています。 <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> に設定すると、WS-Policy 1.2 に準拠したポリシー情報がメタデータ エクスポーターによって生成されます。  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6.  <xref:System.ServiceModel.Description.ServiceMetadataBehavior> インスタンスをサービス ホストの動作コレクションに追加します。  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7.  メタデータ交換エンドポイントをサービス ホストに追加します。  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8.  アプリケーション エンドポイントをサービス ホストに追加します。  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    >  エンドポイントをサービスに追加しない場合、ランタイムによって既定のエンドポイントが追加されます。 この例では、サービスには <xref:System.ServiceModel.Description.ServiceMetadataBehavior> に設定された `true` があるので、サービスで公開メタデータも有効化されています。 既定のエンドポイントの詳細については、次を参照してください。[簡略化された構成](../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。  
  
9. サービス ホストを開き、受信呼び出しを待ちます。 ユーザーが Enter キーを押すと、サービス ホストが終了します。  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. コンソール アプリケーションのビルドと実行  
  
11. Internet Explorer を使用して、サービスのベース アドレスを参照 (http://localhost:8001/MetadataSampleこのサンプルでは) し、メタデータの公開の電源が入っていることを確認します。 上部の "サービスを作成しました" のすぐ下に "Simple Service" と表示された Web ページが表示されます。 有効になっていない場合は、"このサービスのメタデータ公開は現在は無効になっています。" というメッセージが結果ページの上部に表示されます。  
  
## <a name="example"></a>例  
 次のコード例は、コードのサービスのメタデータを公開する基本的な WCF サービスの実装を示しています。  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a>関連項目  
 [方法: マネージ アプリケーションで WCF サービスをホストする](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [自己ホスト](../../../../docs/framework/wcf/samples/self-host.md)  
 [メタデータ アーキテクチャの概要](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [メタデータを使用する](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [方法 : 構成ファイルを使用してサービスのメタデータを公開する](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
