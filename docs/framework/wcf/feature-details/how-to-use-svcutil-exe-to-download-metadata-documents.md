---
title: '方法 : Svcutil.exe を使用してメタデータ ドキュメントをダウンロードする'
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: a8872bbf04e688906fb0229e3d8215fb92cdbc3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492399"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a><span data-ttu-id="eb628-102">方法 : Svcutil.exe を使用してメタデータ ドキュメントをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="eb628-102">How to: Use Svcutil.exe to Download Metadata Documents</span></span>
<span data-ttu-id="eb628-103">Svcutil.exe を使用すると、実行中のサービスからメタデータをダウンロードして、ローカル ファイルに保存できます。</span><span class="sxs-lookup"><span data-stu-id="eb628-103">You can use Svcutil.exe to download metadata from running services and to save the metadata to local files.</span></span> <span data-ttu-id="eb628-104">HTTP および HTTPS の URL スキームの場合、Svcutil.exe は Ws-metadataexchange を使用してメタデータの取得を試みますと[XML Web サービス探索](http://go.microsoft.com/fwlink/?LinkId=94950)です。</span><span class="sxs-lookup"><span data-stu-id="eb628-104">For HTTP and HTTPS URL schemes, Svcutil.exe attempts to retrieve metadata using WS-MetadataExchange and [XML Web Service Discovery](http://go.microsoft.com/fwlink/?LinkId=94950).</span></span> <span data-ttu-id="eb628-105">その他の URL スキームの場合、Svcutil.exe は WS-MetadataExchange のみを使用します。</span><span class="sxs-lookup"><span data-stu-id="eb628-105">For all other URL schemes, Svcutil.exe uses only WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="eb628-106">既定で、Svcutil.exe は <xref:System.ServiceModel.Description.MetadataExchangeBindings> クラスに定義されているバインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="eb628-106">By default, Svcutil.exe uses the bindings defined in the <xref:System.ServiceModel.Description.MetadataExchangeBindings> class.</span></span> <span data-ttu-id="eb628-107">WS-MetadataExchange で使用するバインディングを構成するには、Svcutil.exe の構成ファイル (svcutil.exe.config) でクライアント エンドポイントを定義する必要があります。このとき、クライアント エンドポイントが `IMetadataExchange` コントラクトを使用し、メタデータ エンドポイントのアドレスの URI (Uniform Resource Identifier) スキームと同じ名前を持つように定義します。</span><span class="sxs-lookup"><span data-stu-id="eb628-107">To configure the binding used for WS-MetadataExchange, you must define a client endpoint in the configuration file for Svcutil.exe (svcutil.exe.config) that uses the `IMetadataExchange` contract and that has the same name as the Uniform Resource Identifier (URI) scheme of the metadata endpoint address.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="eb628-108">2 つの異なるサービスを公開するサービスのメタデータを取得する Svcutil.exe を実行しているコントラクトの同じ名前の操作が含まれていることと、Svcutil.exe では"できませんからメタデータを取得しています..."というメッセージが、エラーが表示されます。たとえばと呼ばれるサービス コントラクトを公開するサービスを使用していれば、操作を含む ICarService Get (Car c) と、同じサービスが ibookservice という get (Book b) サービス コントラクトを公開します。</span><span class="sxs-lookup"><span data-stu-id="eb628-108">When running Svcutil.exe to get metadata for a service that exposes two different service contracts that each contain an operation of the same name, Svcutil.exe displays an error saying, "Cannot obtain Metadata from ...." For example, if you have a service that exposes a service contract called ICarService that has an operation Get(Car c) and the same service exposes a service contract called IBookService that has an operation Get(Book b).</span></span> <span data-ttu-id="eb628-109">この問題を回避するには、次のいずれかの操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="eb628-109">To work around this issue, do one of the following:</span></span>  
>   
>  -   <span data-ttu-id="eb628-110">操作の名前を変更する。</span><span class="sxs-lookup"><span data-stu-id="eb628-110">Rename one of the operations</span></span>  
> -   <span data-ttu-id="eb628-111"><xref:System.ServiceModel.OperationContractAttribute.Name%2A> を別の名前に設定する。</span><span class="sxs-lookup"><span data-stu-id="eb628-111">Set the <xref:System.ServiceModel.OperationContractAttribute.Name%2A> to a different name.</span></span>  
> -   <span data-ttu-id="eb628-112"><xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> プロパティを使用して、操作の名前空間のいずれかを別の名前空間に設定する。</span><span class="sxs-lookup"><span data-stu-id="eb628-112">Set one of the operations' namespaces to a different namespace using the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
### <a name="to-download-metadata-using-svcutilexe"></a><span data-ttu-id="eb628-113">Svcutil.exe を使用してメタデータをダウンロードするには</span><span class="sxs-lookup"><span data-stu-id="eb628-113">To download metadata using Svcutil.exe</span></span>  
  
1.  <span data-ttu-id="eb628-114">次の場所で Svcutil.exe ツールを検索します。</span><span class="sxs-lookup"><span data-stu-id="eb628-114">Locate the Svcutil.exe tool at the following location:</span></span>  
  
     <span data-ttu-id="eb628-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span><span class="sxs-lookup"><span data-stu-id="eb628-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span></span>  
  
2.  <span data-ttu-id="eb628-116">コマンド プロンプトで、次の形式を使用してツールを起動します。</span><span class="sxs-lookup"><span data-stu-id="eb628-116">At the command prompt, launch the tool using the following format.</span></span>  
  
    ```  
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     <span data-ttu-id="eb628-117">メタデータをダウンロードするには `/t:metadata` オプションを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eb628-117">You must specify the `/t:metadata` option to download metadata.</span></span> <span data-ttu-id="eb628-118">このオプションを指定しないと、クライアントのコードと構成が生成されます。</span><span class="sxs-lookup"><span data-stu-id="eb628-118">Otherwise, client code and configuration are generated.</span></span>  
  
3.  <span data-ttu-id="eb628-119"><`url`> 引数は、メタデータを提供するサービス エンドポイントまたはオンラインになっているメタデータ ドキュメントの URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="eb628-119">The <`url`>argument specifies the URL to a service endpoint that provides metadata or to a metadata document hosted online.</span></span> <span data-ttu-id="eb628-120"><`epr`> 引数を WS アドレス指定を含む XML ファイルへのパスを指定する`EndpointAddress`Ws-metadataexchange をサポートするサービス エンドポイントにします。</span><span class="sxs-lookup"><span data-stu-id="eb628-120">The <`epr`> argument specifies the path to an XML file that contains a WS-Addressing `EndpointAddress` for a service endpoint that supports WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="eb628-121">メタデータのダウンロード用にこのツールを使用する方法の詳細については、次を参照してください。 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="eb628-121">For more options about using this tool for metadata download, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb628-122">例</span><span class="sxs-lookup"><span data-stu-id="eb628-122">Example</span></span>  
 <span data-ttu-id="eb628-123">次のコマンドにより、実行中のサービスからメタデータ ドキュメントがダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="eb628-123">The following command downloads metadata documents from a running service.</span></span>  
  
```  
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb628-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb628-124">See Also</span></span>  
 [<span data-ttu-id="eb628-125">ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="eb628-125">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
