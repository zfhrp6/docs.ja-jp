---
title: '方法 : メタデータの取得および準拠サービスの実装をする'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ac7654fa041688bbd703d564f6703df9671fbaea
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2018
---
# <a name="how-to-retrieve-metadata-and-implement-a-compliant-service"></a><span data-ttu-id="0bfb1-102">方法 : メタデータの取得および準拠サービスの実装をする</span><span class="sxs-lookup"><span data-stu-id="0bfb1-102">How to: Retrieve Metadata and Implement a Compliant Service</span></span>
<span data-ttu-id="0bfb1-103">サービスのデザイン担当者と実装担当者が同じであるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-103">Often, the same person does not design and implement services.</span></span> <span data-ttu-id="0bfb1-104">アプリケーションの相互運用が重要な環境では、コントラクトを Web サービス記述言語 (WSDL) でデザインまたは記述した場合、開発者はそのコントラクトに準拠するサービスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-104">In environments where interoperating applications are important, contracts can be designed or described in Web Services Description Language (WSDL) and a developer must implement a service that complies with the provided contract.</span></span> <span data-ttu-id="0bfb1-105">既存のサービスを [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] に移行することもできますが、その物理メッセージ フォーマットを維持しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-105">You may also want to migrate an existing service to [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] but preserve the wire format.</span></span> <span data-ttu-id="0bfb1-106">さらに、双方向コントラクトでは、呼び出し元でコールバック コントラクトを実装する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-106">In addition, duplex contracts require callers to implement a callback contract as well.</span></span>  
  
 <span data-ttu-id="0bfb1-107">このようなケースにおいて、コントラクトの要件を満たしうる言語で サービス コントラクト インターフェイスを生成するためには、[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) (または同等のツール) を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-107">In these cases, you must use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) (or an equivalent tool) to generate a service contract interface in a managed language that you can implement to fulfill the requirements of the contract.</span></span> <span data-ttu-id="0bfb1-108">通常、[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) は、チャネル ファクトリを使用するサービス コントラクトを、または、正しいバインドとアドレスを設定するクライアント構成ファイルと同様に [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のクライアントの種類を取得するために使用されます。生成された構成ファイルを使用するには、それをサービスの構成ファイルに変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-108">Typically the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) is used to acquire a service contract that is used with a channel factory or a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client type as well as with a client configuration file that sets up the correct binding and address.</span></span> <span data-ttu-id="0bfb1-109">また、サービス コントラクトを変更する必要がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-109">To use the generated configuration file, you must change it into a service configuration file.</span></span> <span data-ttu-id="0bfb1-110">また、サービス コントラクトを変更する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-110">You may also need to modify the service contract.</span></span>  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a><span data-ttu-id="0bfb1-111">データを取得して準拠サービスを実装するには</span><span class="sxs-lookup"><span data-stu-id="0bfb1-111">To retrieve data and implement a compliant service</span></span>  
  
1.  <span data-ttu-id="0bfb1-112">メタデータ ファイルまたはコード ファイルを生成するメタデータ エンドポイントに対して [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-112">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) against metadata files or a metadata endpoint to generate a code file.</span></span>  
  
2.  <span data-ttu-id="0bfb1-113">出力コード ファイルを検索し、<xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> 属性でマークされた対象のインターフェイス (複数ある場合) 部分を見つけます。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-113">Search for the portion of the output code file that contains the interface of interest (in case there is more than one) that is marked with the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="0bfb1-114">次のコード例は、によって生成された 2 つのインターフェイスを示しています。 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-114">The following code example shows the two interfaces generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="0bfb1-115">最初の例 (`ISampleService`) は、準拠サービスを作成するために実装するサービス コントラクト インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-115">The first (`ISampleService`) is the service contract interface that you implement to create a compliant service.</span></span> <span data-ttu-id="0bfb1-116">2 番目の例 (`ISampleServiceChannel`) は、サービス コントラクト インターフェイスと <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> の両方を拡張するクライアント用のヘルパー インターフェイスです。これはクライアント アプリケーションでも使用されます。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-116">The second (`ISampleServiceChannel`) is a helper interface for client use that extends both the service contract interface and <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> and is for use in a client application.</span></span>  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3.  <span data-ttu-id="0bfb1-117">すべての操作に対する応答アクションを WSDL で指定していない場合、生成後の操作コントラクトでは、<xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> プロパティがワイルドカード文字 (\*) に設定される場合があります。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-117">If the WSDL does not specify a reply action for all of the operations, the generated operation contracts may have the <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> property set to the wildcard character (\*).</span></span> <span data-ttu-id="0bfb1-118">このプロパティの設定を削除します。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-118">Remove this property setting.</span></span> <span data-ttu-id="0bfb1-119">削除しない場合は、サービス コントラクト メタデータを実装するときに、それらの操作のメタデータをエクスポートできません。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-119">Otherwise, when you implement the service contract metadata, the metadata cannot be exported for those operations.</span></span>  
  
4.  <span data-ttu-id="0bfb1-120">クラスにインターフェイスを実装してサービスをホストします。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-120">Implement the interface on a class and host the service.</span></span> <span data-ttu-id="0bfb1-121">例については、[サービス コントラクトを実装する方法](../../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md) に関する記事、または下記の例のセクションにあるシンプルな実装を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-121">For an example, see [How to: Implement a Service Contract](../../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md), or see a simple implementation below in the Example section.</span></span>  
  
5.  <span data-ttu-id="0bfb1-122">[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) が生成したクライアント構成ファイルで、[\<client>](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) 構成セクションを[\<services>](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) 構成セクションへ変更します。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-122">In the client configuration file that the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generates, change the [\<client>](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) configuration section to a [\<services>](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) configuration section.</span></span> <span data-ttu-id="0bfb1-123">(生成されたクライアント アプリケーション構成ファイルの例は、次の「例」セクションを参照してください)。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-123">(For an example of a generated client application configuration file, see the following "Example" section.)</span></span>  
  
6.  <span data-ttu-id="0bfb1-124">[\<services >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) 構成セクションの中で、サービス実装の`name`属性を[\<services >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md)構成セクションに作成します。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-124">Within the [\<services>](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) configuration section, create a `name` attribute in the [\<services>](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) configuration section for your service implementation.</span></span>  
  
7.  <span data-ttu-id="0bfb1-125">サービスの `name` 属性をユーザーのサービス実装の構成名に設定します。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-125">Set the service `name` attribute to the configuration name for your service implementation.</span></span>  
  
8.  <span data-ttu-id="0bfb1-126">実装するサービス コントラクトを使用するエンドポイント構成要素をサービス構成セクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-126">Add the endpoint configuration elements that use the implemented service contract to the service configuration section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bfb1-127">例</span><span class="sxs-lookup"><span data-stu-id="0bfb1-127">Example</span></span>  
 <span data-ttu-id="0bfb1-128">次のコード例を実行して生成されたコード ファイルの大部分を示しています、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)メタデータ ファイルに対してです。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-128">The following code example shows the majority of a code file generated by running the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) against metadata files.</span></span>  
  
 <span data-ttu-id="0bfb1-129">このコードには、次の項目が示されています。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-129">The following code shows:</span></span>  
  
-   <span data-ttu-id="0bfb1-130">コントラクトの要件に準拠するサービス コントラクト インターフェイス (実装する場合) (`ISampleService`)。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-130">The service contract interface that, when implemented, complies with the contract requirements (`ISampleService`).</span></span>  
  
-   <span data-ttu-id="0bfb1-131">サービス コントラクト インターフェイスと <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> の両方を拡張するクライアント用のヘルパー インターフェイス。これはクライアント アプリケーションでも使用されます(`ISampleServiceChannel`)。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-131">The helper interface for client use that extends both the service contract interface and <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> and is for use in a client application (`ISampleServiceChannel`).</span></span>  
  
-   <span data-ttu-id="0bfb1-132"><xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> を拡張するヘルパー クラス。クライアント アプリケーションで使用されます。(`SampleServiceClient`)</span><span class="sxs-lookup"><span data-stu-id="0bfb1-132">The helper class that extends <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> and is for use in a client application (`SampleServiceClient`).</span></span>  
  
-   <span data-ttu-id="0bfb1-133">サービスから生成された構成ファイル。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-133">The configuration file generated from the service.</span></span>  
  
-   <span data-ttu-id="0bfb1-134">`ISampleService` サービスの簡単な実装。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-134">A simple `ISampleService` service implementation.</span></span>  
  
-   <span data-ttu-id="0bfb1-135">クライアント側の構成ファイルからサービス側バージョンへの変換。</span><span class="sxs-lookup"><span data-stu-id="0bfb1-135">A conversion of the client-side configuration file to a service-side version.</span></span>  
  
 [!code-csharp[ClientProxyCodeSample#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#1)]    
 [!code-xml[ClientProxyCodeSample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/client.exe.config#10)]     
 [!code-csharp[ClientProxyCodeSample#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.cs#5)]    
 [!code-xml[ClientProxyCodeSample#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.exe.config#20)]    
  
## <a name="see-also"></a><span data-ttu-id="0bfb1-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="0bfb1-136">See Also</span></span>  
 [<span data-ttu-id="0bfb1-137">ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="0bfb1-137">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
