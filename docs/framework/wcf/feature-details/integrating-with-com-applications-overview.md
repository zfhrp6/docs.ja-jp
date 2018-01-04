---
title: "COM アプリケーションとの統合の概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5b20ae5329f08e9391fd7b93218c44c3c1978a48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="integrating-with-com-applications-overview"></a><span data-ttu-id="135ca-102">COM アプリケーションとの統合の概要</span><span class="sxs-lookup"><span data-stu-id="135ca-102">Integrating with COM Applications Overview</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="135ca-103"> では、マネージ コード開発者は、接続されたアプリケーションを作成するための多彩な環境を使用できます。</span><span class="sxs-lookup"><span data-stu-id="135ca-103"> provides the managed code developer with a rich environment for creating connected applications.</span></span> <span data-ttu-id="135ca-104">ただし、COM ベースのアンマネージ コードにかなりの投資を行っており移行を望まない場合でも、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス モニカーを使用することで、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web サービスを既存のコードに直接統合できます。</span><span class="sxs-lookup"><span data-stu-id="135ca-104">However, if you have a substantial investment in unmanaged COM-based code and do not want to migrate, you can still integrate [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web services directly into your existing code by using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker.</span></span> <span data-ttu-id="135ca-105">サービス モニカーは Office VBA、Visual Basic 6.0、または Visual C++ 6.0 などの幅広い COM ベースの開発環境で使用可能です。</span><span class="sxs-lookup"><span data-stu-id="135ca-105">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="135ca-106">サービス モニカーは、すべての通信に [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の通信チャネルを使用します。</span><span class="sxs-lookup"><span data-stu-id="135ca-106">The service moniker uses a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] communication channel for all communication.</span></span> <span data-ttu-id="135ca-107">このチャネルのセキュリティ メカニズムと識別メカニズムは、標準の COM および DCOM プロキシで使用されるものとは異なります。</span><span class="sxs-lookup"><span data-stu-id="135ca-107">The security and identity mechanisms for that channel differ from those used in standard COM and DCOM proxies.</span></span> <span data-ttu-id="135ca-108">また、サービス モニカーでは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の通信チャネルを使用するため、すべての呼び出しの既定のタイムアウト時間が 1 分になります。</span><span class="sxs-lookup"><span data-stu-id="135ca-108">In addition, because the service moniker uses a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] communication channel the default timeout period is one minute for all calls.</span></span>  
  
 <span data-ttu-id="135ca-109">サービス モニカーを `GetObject` 関数と共に使用することで、アンマネージ開発者は、厳密に型指定された COM 固有の方法を使用して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web サービスを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="135ca-109">The service moniker is used with the `GetObject` function to provide the unmanaged developer with a strongly-typed, COM-specific approach for calling [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web services.</span></span> <span data-ttu-id="135ca-110">そのためには、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web サービス コントラクトの定義と、使用されるバインディングが、ローカル COM から参照できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="135ca-110">This requires a local, COM-visible definition of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web service contract and the binding that is to be used.</span></span> <span data-ttu-id="135ca-111">他の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントの場合と同様に、サービス モニカーではサービスへの型指定されたチャネルを構築する必要がありますが、このチャネルは、最初のメソッド呼び出し時に COM プログラマには透過的に構築されます。</span><span class="sxs-lookup"><span data-stu-id="135ca-111">Like other [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients, the service moniker must construct a typed channel to the service, though this channel construction occurs transparently to the COM programmer on the first method call.</span></span>  
  
 <span data-ttu-id="135ca-112">他の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントと同じように、アプリケーションはモニカーを使用する際に、サービスとの通信に使用するアドレス、バインディング、およびコントラクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="135ca-112">In common with other [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients, when using the moniker, applications specify the address, binding and contract to communicate with a service.</span></span> <span data-ttu-id="135ca-113">コントラクトは、次のいずれかの方法で指定できます。</span><span class="sxs-lookup"><span data-stu-id="135ca-113">The contract can be specified in one of the following ways:</span></span>  
  
-   <span data-ttu-id="135ca-114">型指定のあるコントラクト - クライアント コンピューターで COM から参照できる型として登録されます。</span><span class="sxs-lookup"><span data-stu-id="135ca-114">Typed contract – the contract is registered as a COM visible type on the client machine.</span></span>  
  
-   <span data-ttu-id="135ca-115">WSDL コントラクト - WSDL ドキュメントという形で供給されます。</span><span class="sxs-lookup"><span data-stu-id="135ca-115">WSDL contract – the contract is supplied in the form of a WSDL document.</span></span>  
  
-   <span data-ttu-id="135ca-116">MEX コントラクト - 実行時に Metadata Exchange (MEX) エンドポイントから取得されます。</span><span class="sxs-lookup"><span data-stu-id="135ca-116">MEX contract – the contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="parameters-supported-by-the-service-moniker"></a><span data-ttu-id="135ca-117">サービス モニカーでサポートされるパラメーター</span><span class="sxs-lookup"><span data-stu-id="135ca-117">Parameters Supported by the Service Moniker</span></span>  
 <span data-ttu-id="135ca-118">サービス モニカーでサポートされるパラメーターを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="135ca-118">The following table shows the parameters that are supported by the service moniker.</span></span>  
  
|<span data-ttu-id="135ca-119">パラメーター</span><span class="sxs-lookup"><span data-stu-id="135ca-119">Parameter</span></span>|<span data-ttu-id="135ca-120">説明</span><span class="sxs-lookup"><span data-stu-id="135ca-120">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="135ca-121">サービスの URL 位置。</span><span class="sxs-lookup"><span data-stu-id="135ca-121">URL location of the service.</span></span>|  
|`binding`|<span data-ttu-id="135ca-122">アプリケーション構成のバインディング セクションの名前。</span><span class="sxs-lookup"><span data-stu-id="135ca-122">Binding section name from the application configuration.</span></span>|  
|`bindingConfiguration`|<span data-ttu-id="135ca-123">名前付きバインディング セクション内の名前付きバインディング インスタンス。</span><span class="sxs-lookup"><span data-stu-id="135ca-123">Named binding instance from within the named binding section.</span></span>|  
|`contract`|<span data-ttu-id="135ca-124">サービス コントラクトまたは (MEX の) コントラクト名を表すインターフェイス識別子 (IID)。</span><span class="sxs-lookup"><span data-stu-id="135ca-124">Interface identifier (IID) that represents the service contract or the contract name (from MEX).</span></span>|  
|`wsdl`|<span data-ttu-id="135ca-125">代替形式のコントラクト定義を提供する WSDL ドキュメント。</span><span class="sxs-lookup"><span data-stu-id="135ca-125">WSDL document that provides an alternative form of contract definition.</span></span>|  
|`spnIdentity`|<span data-ttu-id="135ca-126">サービスとの通信に使用するサーバー プリンシパル名 (SPN) ID。</span><span class="sxs-lookup"><span data-stu-id="135ca-126">Server principal name (SPN) identity to be used to communicate with the service.</span></span>|  
|`upnIdentity`|<span data-ttu-id="135ca-127">サービスとの通信に使用するユーザー プリンシパル名 (UPN) ID。</span><span class="sxs-lookup"><span data-stu-id="135ca-127">User principal name (UPN) identity to be used to communicate with the service.</span></span>|  
|`dnsIdentity`|<span data-ttu-id="135ca-128">サービスとの通信に使用する DNS ID。</span><span class="sxs-lookup"><span data-stu-id="135ca-128">DNS identity to be used to communicate with the service.</span></span>|  
|`mexAddress`|<span data-ttu-id="135ca-129">サービスの Metadata Exchange (MEX) エンドポイントの URL 位置。</span><span class="sxs-lookup"><span data-stu-id="135ca-129">URL location of the Metadata Exchange (MEX) endpoint of the service.</span></span>|  
|`mexBinding`|<span data-ttu-id="135ca-130">MEX エンドポイントと接続するための、アプリケーション構成のバインディング セクションの名前。</span><span class="sxs-lookup"><span data-stu-id="135ca-130">Binding section name from the application configuration to connect with the MEX endpoint.</span></span>|  
|`mexBindingConfiguration`|<span data-ttu-id="135ca-131">MEX エンドポイントと接続する名前付きバインディング セクション内の名前付きバインディング インスタンス。</span><span class="sxs-lookup"><span data-stu-id="135ca-131">Named binding instance from within the named binding section to connect with the MEX endpoint.</span></span>|  
|`bindingNamespace`|<span data-ttu-id="135ca-132">取得する MEX のバインディング セクション名の名前空間。</span><span class="sxs-lookup"><span data-stu-id="135ca-132">Namespace of the binding section name from the retrieved MEX.</span></span>|  
|`contractNamespace`|<span data-ttu-id="135ca-133">取得する MEX のコントラクトの名前空間。</span><span class="sxs-lookup"><span data-stu-id="135ca-133">Namespace of the contract from the retrieved MEX.</span></span>|  
|`mexSpnIdentity`|<span data-ttu-id="135ca-134">MEX エンドポイントとの通信に使用するサーバー プリンシパル名 (SPN) ID。</span><span class="sxs-lookup"><span data-stu-id="135ca-134">Server principal name (SPN) identity to be used to communicate with the MEX endpoint.</span></span>|  
|`mexUpnIdentity`|<span data-ttu-id="135ca-135">MEX エンドポイントとの通信に使用するユーザー プリンシパル名 (UPN) ID。</span><span class="sxs-lookup"><span data-stu-id="135ca-135">User principal name (UPN) identity to be used to communicate with the MEX endpoint.</span></span>|  
|`mexDnsIdentity`|<span data-ttu-id="135ca-136">MEX エンドポイントとの通信に使用する DNS ID。</span><span class="sxs-lookup"><span data-stu-id="135ca-136">DNS identity to be used to communicate with the MEX endpoint.</span></span>|  
|`serializer`|<span data-ttu-id="135ca-137">"XML" シリアライザーと "datacontract" シリアライザーのいずれを使用するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="135ca-137">Specify the use of either the "xml" or "datacontract" serializer.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="135ca-138">完全に COM ベースのクライアントと共にサービス モニカーを使用する場合でも、クライアント コンピューターには [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] とこれをサポートする .NET Framework 2.0 がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="135ca-138">Even when used with entirely COM-based clients, the service moniker requires [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and the supporting .NET Framework 2.0 to be installed on the client computer.</span></span> <span data-ttu-id="135ca-139">また、サービス モニカーを使用するクライアント アプリケーションには、適切なバージョンの .NET Framework ランタイムが読み込まれていることが重要です。</span><span class="sxs-lookup"><span data-stu-id="135ca-139">It is also critical that client applications that use the service moniker load the appropriate version of the .NET Framework runtime.</span></span> <span data-ttu-id="135ca-140">Office アプリケーション内でモニカーを使用する場合、構成ファイルに、正しいフレームワーク バージョンが読み込まれていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="135ca-140">When using the moniker within Office applications, a configuration file may be required to ensure that the correct framework version is loaded.</span></span> <span data-ttu-id="135ca-141">たとえば Excel の場合、Excel.exe ファイルと同じディレクトリにある Excel.exe.config というファイルに、次のテキストが記述されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="135ca-141">For example, with Excel, the following text should be placed in a file called Excel.exe.config in the same directory as the Excel.exe file:</span></span>  
>   
>  `<?xml version="1.0" encoding="utf-8"?>`  
>   
>  <span data-ttu-id="135ca-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span><span class="sxs-lookup"><span data-stu-id="135ca-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span></span>  
>   
>  `<startup>`  
>   
>  `<requiredRuntime version="v2.0.50727" />`  
>   
>  `</startup>`  
>   
>  `</configuration>`  
  
## <a name="see-also"></a><span data-ttu-id="135ca-143">参照</span><span class="sxs-lookup"><span data-stu-id="135ca-143">See Also</span></span>  
 [<span data-ttu-id="135ca-144">方法 : サービス モニカーを登録および構成する</span><span class="sxs-lookup"><span data-stu-id="135ca-144">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
