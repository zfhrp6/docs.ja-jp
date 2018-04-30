---
title: 生成されたクライアント コードの理解
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8cd3e7f5ac8f129e29ed080cbf510dfe106edfb7
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="understanding-generated-client-code"></a>生成されたクライアント コードの理解
[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) は、クライアント アプリケーションの構築時に使用するクライアント コードとクライアント アプリケーション構成ファイルを生成します。 このトピックでは、標準サービス コントラクトのシナリオ向けに生成されたコード例について説明します。 生成されたコードを使用してクライアント アプリケーションの作成の詳細については、次を参照してください。 [WCF クライアントの概要](../../../../docs/framework/wcf/wcf-client-overview.md)です。  
  
## <a name="overview"></a>概要  
 Visual Studio を使用して生成する場合[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]クライアント プロジェクトの種類に、通常必要はありません、生成されたクライアント コードを調べる。 同じサービスを実行する開発環境を使用していない場合は、Svcutil.exe のようなツールを使用してクライアント コードを生成し、そのコードでクライアント アプリケーションを開発します。  
  
 Svcutil.exe には、生成された型情報を変更する多くのオプションがあるため、ここですべてのシナリオを説明することはできません。 ここでは、生成されたコードの検索に関する標準的な作業の例を紹介します。  
  
-   サービス コントラクト インターフェイスの識別  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント クラスの識別  
  
-   データ型の識別  
  
-   双方向サービスのコールバック コントラクトの識別  
  
-   ヘルパーのサービス コントラクトのチャネル インターフェイスの識別  
  
### <a name="finding-service-contract-interfaces"></a>サービス コントラクト インターフェイスの検索  
 サービス コントラクトをモデル化するインターフェイスを検索するには、<xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> 属性でマークされたインターフェイスを検索します。 多くの場合、属性自体に設定された他の属性や明示的なプロパティが存在するため、この属性をすばやく読み取って見つけることは簡単ではありません。 サービス コントラクト インターフェイスとクライアント コントラクト インターフェイスは 2 つの別の種類だという点に注意してください。 次のコード例は、元のサービス コントラクトを示しています。  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 次のコード例は、Svcutil.exe で生成された同じサービス コントラクトを示しています。  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 生成されたサービス コントラクト インターフェイスと <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> クラスを使用して、サービス操作の呼び出しに使用する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] チャネル オブジェクトを作成できます。 詳細については、次を参照してください。[する方法: ChannelFactory を使用して](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)です。  
  
### <a name="finding-wcf-client-classes"></a>WCF クライアント クラスの検索  
 使用するサービス コントラクトを実装する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント クラスを検索するには、<xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> の拡張を検索します。ここで、型パラメーターは、以前に検索され、自身を拡張するサービス コントラクト インターフェイスです。 次のコード例は、 <xref:System.ServiceModel.ClientBase%601> 型の `ISampleService`クラスを示しています。  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 この [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント クラスを使用するには、新しいインスタンスを作成し、このクラスに実装されているメソッドを呼び出します。 これらのメソッドは、対応しているサービス操作を呼び出し、やり取りを行うように構成されています。 詳細については、次を参照してください。 [WCF クライアントの概要](../../../../docs/framework/wcf/wcf-client-overview.md)です。  
  
> [!NOTE]
>  SvcUtil.exe で WCF クライアント クラスが生成されるとき、 <xref:System.Diagnostics.DebuggerStepThroughAttribute> がクライアント クラスに追加されるため、デバッガーで WCF クライアント クラスをステップ実行できなくなります。  
  
### <a name="finding-data-types"></a>データ型の検索  
 生成されたコード内でデータ型を検索する最も基本的な方法は、コントラクトに指定された型名を識別し、その型宣言のコードを検索することです。 たとえば、次のコントラクトには、 `SampleMethod` が型 `microsoft.wcf.documentation.SampleFault`の SOAP エラーを返せることが指定されています。  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 `SampleFault` を検索すると、次の型宣言が見つかります。  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 この場合、このデータ型は、クライアントの特定の例外 ( <xref:System.ServiceModel.FaultException%601> ) によりスローされる詳細な型です。詳細な型のパラメーターは、 `microsoft.wcf.documentation.SampleFault`です。 データ型の詳細については、次を参照してください。[サービス コントラクトのデータ転送を指定する](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)です。 クライアントでの例外処理の詳細については、次を参照してください。[送信と受信エラー](../../../../docs/framework/wcf/sending-and-receiving-faults.md)です。  
  
### <a name="finding-callback-contracts-for-duplex-services"></a>双方向サービスのコールバック コントラクトの検索  
 コントラクト インターフェイスにより <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> プロパティの値が指定されているサービス コントラクトを検索すると、そのコントラクトには双方向コントラクトが指定されていることがわかります。 二重のコントラクトを使用した場合、クライアント アプリケーションは、コールバック コントラクトを実装するコールバック クラスを作成し、そのクラスのインスタンスを、サービスとの通信に使用する <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> または <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> に渡す必要があります。 双方向クライアントの詳細については、次を参照してください。[する方法: 双方向コントラクトでサービスをアクセス](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)です。  
  
 次のコントラクトは、型 `SampleDuplexHelloCallback`のコールバック コントラクトを指定しています。  
  
 [!code-csharp[C_GeneratedCodeFiles#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#2)]
 [!code-vb[C_GeneratedCodeFiles#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#2)]  
  
 このコールバック コントラクトを検索すると、クライアント アプリケーションが実装する必要のある次のインターフェイスが見つかります。  
  
 [!code-csharp[C_GeneratedCodeFiles#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#4)]
 [!code-vb[C_GeneratedCodeFiles#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#4)]  
  
### <a name="finding-service-contract-channel-interfaces"></a>サービス コントラクト チャネル インターフェイスの検索  
 サービス コントラクト インターフェイスで <xref:System.ServiceModel.ChannelFactory> クラスを使用する場合、明示的にチャネルを開いたり、閉じたり、中止したりするには、<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> インターフェイスにキャストする必要があります。 処理を容易にするために、Svcutil.exe ツールでは、サービス コントラクト インターフェイスと <xref:System.ServiceModel.IClientChannel> の両方を実装するヘルパー インターフェイスも生成されます。これにより、キャストを行わずにクライアント チャネル インフラストラクチャとのやりとりを実現できます。 上記のサービス コントラクトを実装するヘルパー クライアント チャネルの定義を、次のコード例に示します。  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
## <a name="see-also"></a>関連項目  
 [WCF クライアントの概要](../../../../docs/framework/wcf/wcf-client-overview.md)
