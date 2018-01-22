---
title: "クライアントのセキュリティ保護"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: clients [WCF], security considerations
ms.assetid: 44c8578c-9a5b-4acd-8168-1c30a027c4c5
caps.latest.revision: "22"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 611272f9d0369a89d401315e9b6379d2e8cd27c0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="securing-clients"></a><span data-ttu-id="ffc58-102">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="ffc58-102">Securing Clients</span></span>
<span data-ttu-id="ffc58-103">[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] では、サービスがクライアントのセキュリティ要件を決定します。</span><span class="sxs-lookup"><span data-stu-id="ffc58-103">In [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], the service dictates the security requirements for clients.</span></span> <span data-ttu-id="ffc58-104">つまり、使用するセキュリティ モード、およびクライアントが資格情報を提供するかどうかは、サービスによって指定されます。</span><span class="sxs-lookup"><span data-stu-id="ffc58-104">That is, the service specifies what security mode to use, and whether or not the client must provide a credential.</span></span> <span data-ttu-id="ffc58-105">そのため、クライアントをセキュリティで保護するプロセスは、サービスから取得したメタデータ (公開されている場合) を使用してクライアントを構築するという簡単なものになります。</span><span class="sxs-lookup"><span data-stu-id="ffc58-105">The process of securing a client, therefore, is simple: use the metadata obtained from the service (if it is published) and build a client.</span></span> <span data-ttu-id="ffc58-106">クライアントを構成する方法は、メタデータによって指定されます。</span><span class="sxs-lookup"><span data-stu-id="ffc58-106">The metadata specifies how to configure the client.</span></span> <span data-ttu-id="ffc58-107">クライアントが資格情報を提供することをサービスが要求する場合、要件に適した資格情報を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffc58-107">If the service requires that the client supply a credential, then you must obtain a credential that fits the requirement.</span></span> <span data-ttu-id="ffc58-108">ここでは、このプロセスについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="ffc58-108">This topic discusses the process in further detail.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="ffc58-109">セキュリティで保護されたサービスを作成するを参照してください[Services のセキュリティ保護](../../../docs/framework/wcf/securing-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="ffc58-109"> creating a secure service, see [Securing Services](../../../docs/framework/wcf/securing-services.md).</span></span>  
  
## <a name="the-service-specifies-security"></a><span data-ttu-id="ffc58-110">サービスによるセキュリティの指定</span><span class="sxs-lookup"><span data-stu-id="ffc58-110">The Service Specifies Security</span></span>  
 <span data-ttu-id="ffc58-111">既定では、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] バインディングのセキュリティ機能は有効になっています </span><span class="sxs-lookup"><span data-stu-id="ffc58-111">By default, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] bindings have security features enabled.</span></span> <span data-ttu-id="ffc58-112">(<xref:System.ServiceModel.BasicHttpBinding> を除く)。そのため、サービスが [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] を使用して作成されている場合、認証、機密性、および整合性を確実にするセキュリティが実装される可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="ffc58-112">(The exception is the <xref:System.ServiceModel.BasicHttpBinding>.) Therefore, if the service was created using [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], there is a greater chance that it will implement security to ensure authentication, confidentiality, and integrity.</span></span> <span data-ttu-id="ffc58-113">この場合、サービスが提供するメタデータによって、セキュリティで保護された通信チャネルの確立に必要なものが示されます。</span><span class="sxs-lookup"><span data-stu-id="ffc58-113">In that case, the metadata the service provides will indicate what it requires to establish a secure communication channel.</span></span> <span data-ttu-id="ffc58-114">サービス メタデータにセキュリティ要件がまったく含まれていない場合には、サービスでセキュリティ スキーム (SSL (Secure Sockets Layer) over HTTP など) を強制する方法はありません。</span><span class="sxs-lookup"><span data-stu-id="ffc58-114">If the service metadata does not include any security requirements, there is no way to impose a security scheme, such as Secure Sockets Layer (SSL) over HTTP, on a service.</span></span> <span data-ttu-id="ffc58-115">ただし、サービスがクライアントに資格情報の提供を求める場合は、クライアントの開発者、展開担当者、または管理者は、クライアントがサービスに対して認証を受けるときに実際に使用する資格情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffc58-115">If, however, the service requires the client to supply a credential, then the client developer, deployer, or administrator must supply the actual credential that the client will use to authenticate itself to the service.</span></span>  
  
## <a name="obtaining-metadata"></a><span data-ttu-id="ffc58-116">メタデータの取得</span><span class="sxs-lookup"><span data-stu-id="ffc58-116">Obtaining Metadata</span></span>  
 <span data-ttu-id="ffc58-117">クライアントを作成する場合、最初の手順はクライアントが通信を行うサービスからメタデータを取得することです。</span><span class="sxs-lookup"><span data-stu-id="ffc58-117">When creating a client, the first step is to obtain the metadata for the service that the client will communicate with.</span></span> <span data-ttu-id="ffc58-118">これは、次の 2 つの方法で行うことができます。</span><span class="sxs-lookup"><span data-stu-id="ffc58-118">This can be done in two ways.</span></span> <span data-ttu-id="ffc58-119">最初に場合、サービス メタデータ交換 (MEX) エンドポイントを公開するか HTTP または HTTPS 経由でそのメタデータを利用をダウンロードできますを使用して、メタデータ、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)、両方を生成します。構成ファイルと同様に、クライアントは、コード ファイル。</span><span class="sxs-lookup"><span data-stu-id="ffc58-119">First, if the service publishes a metadata exchange (MEX) endpoint or makes its metadata available over HTTP or HTTPS, you can download the metadata using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), which generates both code files for a client as well as a configuration file.</span></span> <span data-ttu-id="ffc58-120">([!INCLUDE[crabout](../../../includes/crabout-md.md)]ツールを使用して、参照してください[へのアクセスを WCF クライアントを使用してサービス](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md))。サービスにより MEX エンドポイントが公開されておらず、かつ HTTP または HTTPS 上でメタデータが使用可能になっていない場合は、サービス作成者に連絡して、セキュリティ要件とメタデータについて記述したドキュメントを入手する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffc58-120">([!INCLUDE[crabout](../../../includes/crabout-md.md)] using the tool, see [Accessing Services Using a WCF Client](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).) If the service does not publish a MEX endpoint and also does not make its metadata available over HTTP or HTTPS, you must contact the service creator for documentation that describes the security requirements and the metadata.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ffc58-121">メタデータが信頼されたソースのものであり、改ざんされていないことを確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ffc58-121">It is recommended that the metadata come from a trusted source and that it not be tampered with.</span></span> <span data-ttu-id="ffc58-122">HTTP プロトコルを使用して取得したメタデータはクリア テキストで送信されるため、改ざんされるおそれがあります。</span><span class="sxs-lookup"><span data-stu-id="ffc58-122">Metadata retrieved using the HTTP protocol is sent in clear text and can be tampered with.</span></span> <span data-ttu-id="ffc58-123">サービスで <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> プロパティおよび <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> プロパティを使用している場合は、サービス作成者から提供された URL で、HTTPS プロトコルを使用してデータをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="ffc58-123">If the service uses the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> and <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> properties, use the URL the service creator supplied to download the data using the HTTPS protocol.</span></span>  
  
## <a name="validating-security"></a><span data-ttu-id="ffc58-124">セキュリティの検証</span><span class="sxs-lookup"><span data-stu-id="ffc58-124">Validating Security</span></span>  
 <span data-ttu-id="ffc58-125">メタデータのソースは、信頼されたソースと信頼関係のないソースの 2 つに大きく分けられます。</span><span class="sxs-lookup"><span data-stu-id="ffc58-125">Metadata sources can be divided into two broad categories: trust sources and untrusted sources.</span></span> <span data-ttu-id="ffc58-126">ソースを信頼しており、そのソースのセキュリティで保護された MEX エンドポイントからクライアント コードとその他のメタデータをダウンロードしている場合、何の懸念もなく、クライアントをビルドし、適切な資格情報を提供して実行できます。</span><span class="sxs-lookup"><span data-stu-id="ffc58-126">If you trust a source and have downloaded the client code and other metadata from that source's secure MEX endpoint, then you can build the client, supply it with the right credentials, and run it with no other concerns.</span></span>  
  
 <span data-ttu-id="ffc58-127">ただし、ほとんど未知のソースからクライアントとメタデータをダウンロードする場合は、コードで使用しているセキュリティ対策を検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffc58-127">However, if you elect to download a client and metadata from a source that you know little about, be sure to validate the security measures the code uses.</span></span> <span data-ttu-id="ffc58-128">たとえば、サービスにより (最低でも) 機密性と整合性とが要求されていない場合は、個人情報や財務情報を送信するクライアントを作成するようなことは絶対に避けてください。</span><span class="sxs-lookup"><span data-stu-id="ffc58-128">For example, you must not simply create a client that sends your personal or financial information to a service unless the service demands confidentiality and integrity (at the very least).</span></span> <span data-ttu-id="ffc58-129">この種の情報はサービスの所有者から見ることが可能なので、この種の情報の開示を行ってもよいと判断できる程度にはサービスの所有者を信頼できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffc58-129">You should trust the owner of the service to the extent that you are willing to disclose such information because such information will be visible to him or her.</span></span>  
  
 <span data-ttu-id="ffc58-130">したがって、信頼できないソースから受け取ったコードとメタデータを使用する場合には、それがこちらの必要とするセキュリティ レベルを満たしていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffc58-130">As a rule, therefore, when using code and metadata from an untrusted source, check the code and metadata to ensure that it meets the security level that you require.</span></span>  
  
## <a name="setting-a-client-credential"></a><span data-ttu-id="ffc58-131">クライアント資格情報の設定</span><span class="sxs-lookup"><span data-stu-id="ffc58-131">Setting a Client Credential</span></span>  
 <span data-ttu-id="ffc58-132">クライアントへの資格情報の設定には、次の 2 つの手順があります。</span><span class="sxs-lookup"><span data-stu-id="ffc58-132">Setting a client credential on a client consists of two steps:</span></span>  
  
1.  <span data-ttu-id="ffc58-133">確認、*クライアント資格情報の種類*サービスが必要です。</span><span class="sxs-lookup"><span data-stu-id="ffc58-133">Determine the *client credential type* the service requires.</span></span> <span data-ttu-id="ffc58-134">これは、2 つある方法のどちらかによって行います。</span><span class="sxs-lookup"><span data-stu-id="ffc58-134">This is accomplished by one of two methods.</span></span> <span data-ttu-id="ffc58-135">1 つ目の方法として、サービス作成者からドキュメントを入手している場合は、このドキュメントにサービスが要求するクライアント資格情報の種類が示されています (クライアント資格情報の種類が指定されている場合)。</span><span class="sxs-lookup"><span data-stu-id="ffc58-135">First, if you have documentation from the service creator, it should specify the client credential type (if any) the service requires.</span></span> <span data-ttu-id="ffc58-136">2 番目の方法は Svcutil.exe ツールによって作成された構成ファイルしかない場合で、個々のバインディングを調べることで必要な資格情報の種類を特定できます。</span><span class="sxs-lookup"><span data-stu-id="ffc58-136">Second, if you have only a configuration file generated by the Svcutil.exe tool, you can examine the individual bindings to determine what credential type is required.</span></span>  
  
2.  <span data-ttu-id="ffc58-137">実際のクライアント資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="ffc58-137">Specify an actual client credential.</span></span> <span data-ttu-id="ffc58-138">実際のクライアント資格情報が呼び出された、*クライアント資格情報の値*型から区別するためにします。</span><span class="sxs-lookup"><span data-stu-id="ffc58-138">The actual client credential is called a *client credential value* to distinguish it from the type.</span></span> <span data-ttu-id="ffc58-139">たとえば、クライアント資格情報の種類として証明書が指定されている場合、サービスが信頼する証明機関によって発行された X.509 証明書を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffc58-139">For example, if the client credential type specifies a certificate, you must supply an X.509 certificate that is issued by a certification authority the service trusts.</span></span>  
  
### <a name="determining-the-client-credential-type"></a><span data-ttu-id="ffc58-140">クライアント資格情報の種類の特定</span><span class="sxs-lookup"><span data-stu-id="ffc58-140">Determining the Client Credential Type</span></span>  
 <span data-ttu-id="ffc58-141">構成を確認して、Svcutil.exe ツールで生成されたファイルがある場合、 [\<バインド >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)セクションで必要なクライアント資格情報の種類を判断します。</span><span class="sxs-lookup"><span data-stu-id="ffc58-141">If you have the configuration file the Svcutil.exe tool generated, examine the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) section to determine what client credential type is required.</span></span> <span data-ttu-id="ffc58-142">このセクション内には、セキュリティ要件を指定するバインド要素があります。</span><span class="sxs-lookup"><span data-stu-id="ffc58-142">Within the section are binding elements that specify the security requirements.</span></span> <span data-ttu-id="ffc58-143">具体的には、確認、\<セキュリティ > の各バインド要素。</span><span class="sxs-lookup"><span data-stu-id="ffc58-143">Specifically, examine the \<security> Element of each binding.</span></span> <span data-ttu-id="ffc58-144">この要素には `mode` 属性が含まれており、3 つの値のいずれか (`Message`、`Transport`、または `TransportWithMessageCredential`) に設定できます。</span><span class="sxs-lookup"><span data-stu-id="ffc58-144">That element includes the `mode` attribute, which you can set to one of three possible values (`Message`, `Transport`, or `TransportWithMessageCredential`).</span></span> <span data-ttu-id="ffc58-145">この属性の値によってモードが決定され、このモードによってどの子要素が有効なのかが決定されます。</span><span class="sxs-lookup"><span data-stu-id="ffc58-145">The value of the attribute determines the mode, and the mode determines which of the child elements is significant.</span></span>  
  
 <span data-ttu-id="ffc58-146">`<security>`要素は、いずれかを含めることができます、`<transport>`または`<message>`要素、またはその両方です。</span><span class="sxs-lookup"><span data-stu-id="ffc58-146">The `<security>` element can contain either a `<transport>` or `<message>` element, or both.</span></span> <span data-ttu-id="ffc58-147">セキュリティ モードと一致する要素が有効な要素です。</span><span class="sxs-lookup"><span data-stu-id="ffc58-147">The significant element is the one that matches the security mode.</span></span> <span data-ttu-id="ffc58-148">たとえば、次のコードでは、セキュリティ モードを `"Message"`、`<message>` 要素のクライアント資格情報の種類を `"Certificate"` に指定しています。</span><span class="sxs-lookup"><span data-stu-id="ffc58-148">For example, the following code specifies that the security mode is `"Message"`, and the client credential type for the `<message>` element is `"Certificate"`.</span></span> <span data-ttu-id="ffc58-149">この場合、`<transport>` 要素は無視できます。</span><span class="sxs-lookup"><span data-stu-id="ffc58-149">In this case, the `<transport>` element can be ignored.</span></span> <span data-ttu-id="ffc58-150">ただし、`<message>` 要素で X.509 証明書を提示する必要があることが指定されています。</span><span class="sxs-lookup"><span data-stu-id="ffc58-150">However, the `<message>` element specifies that an X.509 certificate must be supplied.</span></span>  
  
```xml  
<wsHttpBinding>  
    <binding name="WSHttpBinding_ICalculator">  
       <security mode="Message">  
           <transport clientCredentialType="Windows"   
                      realm="" />  
           <message clientCredentialType="Certificate"   
                    negotiateServiceCredential="true"  
                    algorithmSuite="Default"   
                    establishSecurityContext="true" />  
       </security>  
    </binding>  
</wsHttpBinding>  
```  
  
 <span data-ttu-id="ffc58-151">次の例に示すように、`clientCredentialType` 属性が `"Windows"` に設定されている場合は、実際の資格情報の値を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ffc58-151">Note that if the `clientCredentialType` attribute is set to `"Windows"`, as shown in the following example, you do not need to supply an actual credential value.</span></span> <span data-ttu-id="ffc58-152">これは、Windows 統合セキュリティでは、クライアントを実行しているユーザーの実際の資格情報 (Kerberos トークン) が提供されるためです。</span><span class="sxs-lookup"><span data-stu-id="ffc58-152">This is because the Windows integrated security provides the actual credential (a Kerberos token) of the person who is running the client.</span></span>  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows "   
        realm="" />  
</security>  
```  
  
### <a name="setting-the-client-credential-value"></a><span data-ttu-id="ffc58-153">クライアント資格情報の値の設定</span><span class="sxs-lookup"><span data-stu-id="ffc58-153">Setting the Client Credential Value</span></span>  
 <span data-ttu-id="ffc58-154">クライアントが資格情報を提供する必要があると特定された場合は、クライアントを構成する適切なメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="ffc58-154">If it is determined that the client must supply a credential, use the appropriate method to configure the client.</span></span> <span data-ttu-id="ffc58-155">たとえば、クライアント証明書を設定するには、<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="ffc58-155">For example, to set a client certificate, use the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method.</span></span>  
  
 <span data-ttu-id="ffc58-156">X.509 証明書は広く使用されている資格情報の形式です。</span><span class="sxs-lookup"><span data-stu-id="ffc58-156">A common form of credential is the X.509 certificate.</span></span> <span data-ttu-id="ffc58-157">資格情報は次の 2 つの方法で提供できます。</span><span class="sxs-lookup"><span data-stu-id="ffc58-157">You can supply the credential in two ways:</span></span>  
  
-   <span data-ttu-id="ffc58-158">クライアント コードで (`SetCertificate` メソッドを使用して) プログラミングする方法。</span><span class="sxs-lookup"><span data-stu-id="ffc58-158">By programming it in your client code (using the `SetCertificate` method).</span></span>  
  
 <span data-ttu-id="ffc58-159">追加することによって、 [\<動作 >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)クライアントの構成ファイルのセクションを使用して、`clientCredentials`要素 (下図参照)。</span><span class="sxs-lookup"><span data-stu-id="ffc58-159">By adding a [\<behaviors>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) section of the configuration file for the client and using the `clientCredentials` element (shown below).</span></span>  
  
#### <a name="setting-a-clientcredentials-value-in-code"></a><span data-ttu-id="ffc58-160">設定、 \<clientCredentials > コード値</span><span class="sxs-lookup"><span data-stu-id="ffc58-160">Setting a \<clientCredentials> Value in Code</span></span>  
 <span data-ttu-id="ffc58-161">設定する、 [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)値コードでは、アクセスする必要があります、<xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>のプロパティ、<xref:System.ServiceModel.ClientBase%601>クラスです。</span><span class="sxs-lookup"><span data-stu-id="ffc58-161">To set a [\<clientCredentials>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) value in code, you must access the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class.</span></span> <span data-ttu-id="ffc58-162">このプロパティは、次の表に示すように、各種の資格情報の種類にアクセスできる <xref:System.ServiceModel.Description.ClientCredentials> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="ffc58-162">The property returns a <xref:System.ServiceModel.Description.ClientCredentials> object that allows access to various credential types, as shown in the following table.</span></span>  
  
|<span data-ttu-id="ffc58-163">ClientCredential プロパティ</span><span class="sxs-lookup"><span data-stu-id="ffc58-163">ClientCredential Property</span></span>|<span data-ttu-id="ffc58-164">説明</span><span class="sxs-lookup"><span data-stu-id="ffc58-164">Description</span></span>|<span data-ttu-id="ffc58-165">メモ</span><span class="sxs-lookup"><span data-stu-id="ffc58-165">Notes</span></span>|  
|-------------------------------|-----------------|-----------|  
|<xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>|<span data-ttu-id="ffc58-166"><xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> を返します</span><span class="sxs-lookup"><span data-stu-id="ffc58-166">Returns an <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential></span></span>|<span data-ttu-id="ffc58-167">クライアントがサービスに対して自身を認証するために提供する X.509 証明書を表します。</span><span class="sxs-lookup"><span data-stu-id="ffc58-167">Represents an X.509 certificate provided by the client to authenticate itself to the service.</span></span>|  
|<xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>|<span data-ttu-id="ffc58-168"><xref:System.ServiceModel.Security.HttpDigestClientCredential> を返します</span><span class="sxs-lookup"><span data-stu-id="ffc58-168">Returns an <xref:System.ServiceModel.Security.HttpDigestClientCredential></span></span>|<span data-ttu-id="ffc58-169">HTTP ダイジェスト資格情報を表します。</span><span class="sxs-lookup"><span data-stu-id="ffc58-169">Represents an HTTP digest credential.</span></span> <span data-ttu-id="ffc58-170">この資格情報は、ユーザー名とパスワードのハッシュです。</span><span class="sxs-lookup"><span data-stu-id="ffc58-170">The credential is a hash of the user name and password.</span></span>|  
|<xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>|<span data-ttu-id="ffc58-171"><xref:System.ServiceModel.Security.IssuedTokenClientCredential> を返します</span><span class="sxs-lookup"><span data-stu-id="ffc58-171">Returns an <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span></span>|<span data-ttu-id="ffc58-172">フェデレーション シナリオで通常使用される、セキュリティ トークン サービスによって発行されるカスタム セキュリティ トークンを表します。</span><span class="sxs-lookup"><span data-stu-id="ffc58-172">Represents a custom security token issued by a Security Token Service, commonly used in federation scenarios.</span></span>|  
|<xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>|<span data-ttu-id="ffc58-173"><xref:System.ServiceModel.Security.PeerCredential> を返します</span><span class="sxs-lookup"><span data-stu-id="ffc58-173">Returns a <xref:System.ServiceModel.Security.PeerCredential></span></span>|<span data-ttu-id="ffc58-174">Windows ドメインのピア メッシュに参加するためのピア資格情報を表します。</span><span class="sxs-lookup"><span data-stu-id="ffc58-174">Represents a Peer credential for participation in a Peer mesh on a Windows domain.</span></span>|  
|<xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>|<span data-ttu-id="ffc58-175"><xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> を返します</span><span class="sxs-lookup"><span data-stu-id="ffc58-175">Returns an <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential></span></span>|<span data-ttu-id="ffc58-176">帯域外ネゴシエーションでサービスによって提供される X.509 証明書を表します。</span><span class="sxs-lookup"><span data-stu-id="ffc58-176">Represents an X.509 certificate provided by the service in an out-of-band negotiation.</span></span>|  
|<xref:System.ServiceModel.Description.ClientCredentials.UserName%2A>|<span data-ttu-id="ffc58-177"><xref:System.ServiceModel.Security.UserNamePasswordClientCredential> を返します</span><span class="sxs-lookup"><span data-stu-id="ffc58-177">Returns a <xref:System.ServiceModel.Security.UserNamePasswordClientCredential></span></span>|<span data-ttu-id="ffc58-178">ユーザー名とパスワードのペアを表します。</span><span class="sxs-lookup"><span data-stu-id="ffc58-178">Represents a user name and password pair.</span></span>|  
|<xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>|<span data-ttu-id="ffc58-179"><xref:System.ServiceModel.Security.WindowsClientCredential> を返します</span><span class="sxs-lookup"><span data-stu-id="ffc58-179">Returns a <xref:System.ServiceModel.Security.WindowsClientCredential></span></span>|<span data-ttu-id="ffc58-180">Windows クライアントの資格情報 (Kerberos 資格情報) を表します。</span><span class="sxs-lookup"><span data-stu-id="ffc58-180">Represents a Windows client credential (a Kerberos credential).</span></span> <span data-ttu-id="ffc58-181">このクラスのプロパティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="ffc58-181">The properties of the class are read-only.</span></span>|  
  
#### <a name="setting-a-clientcredentials-value-in-configuration"></a><span data-ttu-id="ffc58-182">設定、 \<clientCredentials > 構成内の値</span><span class="sxs-lookup"><span data-stu-id="ffc58-182">Setting a \<clientCredentials> Value in Configuration</span></span>  
 <span data-ttu-id="ffc58-183">子要素として、エンドポイントの動作を使用して、資格情報の値が指定されて、 [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)要素。</span><span class="sxs-lookup"><span data-stu-id="ffc58-183">Credential values are specified by using an endpoint behavior as child elements of the [\<clientCredentials>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span> <span data-ttu-id="ffc58-184">使用される要素は、クライアントの資格情報の種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="ffc58-184">The element used depends on the client credential type.</span></span> <span data-ttu-id="ffc58-185">たとえば、次の例は、X.509 証明書を使用して設定する構成を示しています。、<[\<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)です。</span><span class="sxs-lookup"><span data-stu-id="ffc58-185">For example, the following example shows the configuration to set an X.509 certificate using the <[\<clientCertificate>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myEndpointBehavior">  
          <clientCredentials>  
            <clientCertificate findvalue="myMachineName"   
            storeLocation="Current" X509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>              
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="ffc58-186">構成でクライアント資格情報を設定するには追加、 [ \<endpointBehaviors >](../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)要素を構成ファイル。</span><span class="sxs-lookup"><span data-stu-id="ffc58-186">To set the client credential in configuration, add an [\<endpointBehaviors>](../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) element to the configuration file.</span></span> <span data-ttu-id="ffc58-187">さらに、追加の動作の要素は、サービスのエンドポイントにリンクする必要がありますを使用して、`behaviorConfiguration`の属性、 [\<エンドポイント >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)要素の次の例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="ffc58-187">Additionally, the added behavior element must be linked to the service's endpoint using the `behaviorConfiguration` attribute of the [\<endpoint>](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element as shown in the following example.</span></span> <span data-ttu-id="ffc58-188">`behaviorConfiguration` 属性の値は、動作の `name` 属性の値と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffc58-188">The value of the `behaviorConfiguration` attribute must match the value of the behavior `name` attribute.</span></span>  
  
 `<configuration>`  
  
 `<system.serviceModel>`  
  
 `<client>`  
  
 `<endpoint address="http://localhost/servicemodelsamples/service.svc"`  
  
 `binding="wsHttpBinding"`  
  
 `bindingConfiguration="Binding1"`  
  
 `behaviorConfiguration="myEndpointBehavior"`  
  
 `contract="Microsoft.ServiceModel.Samples.ICalculator" />`  
  
 `</client>`  
  
 `</system.serviceModel>`  
  
 `</configuration>`  
  
> [!NOTE]
>  <span data-ttu-id="ffc58-189">クライアント資格情報の値の中には、アプリケーション構成ファイルを使用して設定できないものがあります (ユーザー名とパスワードや、Windows ユーザーとパスワードの値など)。</span><span class="sxs-lookup"><span data-stu-id="ffc58-189">Some of the client credential values cannot be set using application configuration files, for example, user name and password, or Windows user and password values.</span></span> <span data-ttu-id="ffc58-190">このような資格情報の値は、コードでのみ指定できます。</span><span class="sxs-lookup"><span data-stu-id="ffc58-190">Such credential values can be specified only in code.</span></span>  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="ffc58-191">クライアントの資格情報を設定するには、表示[する方法: クライアントの資格情報の値を指定](../../../docs/framework/wcf/how-to-specify-client-credential-values.md)です。</span><span class="sxs-lookup"><span data-stu-id="ffc58-191"> setting the client credential, see [How to: Specify Client Credential Values](../../../docs/framework/wcf/how-to-specify-client-credential-values.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ffc58-192">次の構成例に示すように、`ClientCredentialType` が `SecurityMode` に設定されている場合、`"TransportWithMessageCredential",` は無視されます。</span><span class="sxs-lookup"><span data-stu-id="ffc58-192">`ClientCredentialType` is ignored when `SecurityMode` is set to `"TransportWithMessageCredential",` as shown in the following sample configuration.</span></span>  
  
```xml  
<wsHttpBinding>  
    <binding name="PingBinding">  
        <security mode="TransportWithMessageCredential"  >  
           <message  clientCredentialType="UserName"   
               establishSecurityContext="false"    
               negotiateServiceCredential="false" />  
           <transport clientCredentialType="Certificate"  />  
         </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ffc58-193">参照</span><span class="sxs-lookup"><span data-stu-id="ffc58-193">See Also</span></span>  
 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>  
 <xref:System.ServiceModel.ClientBase%601>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>  
 [<span data-ttu-id="ffc58-194">\<bindings></span><span class="sxs-lookup"><span data-stu-id="ffc58-194">\<bindings></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
 [<span data-ttu-id="ffc58-195">構成エディター ツール (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="ffc58-195">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [<span data-ttu-id="ffc58-196">サービスのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="ffc58-196">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="ffc58-197">WCF クライアントを使用したサービスへのアクセス</span><span class="sxs-lookup"><span data-stu-id="ffc58-197">Accessing Services Using a WCF Client</span></span>](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)  
 [<span data-ttu-id="ffc58-198">方法: クライアントの資格情報の値を指定する</span><span class="sxs-lookup"><span data-stu-id="ffc58-198">How to: Specify Client Credential Values</span></span>](../../../docs/framework/wcf/how-to-specify-client-credential-values.md)  
 [<span data-ttu-id="ffc58-199">ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="ffc58-199">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="ffc58-200">方法: クライアントの資格情報の種類を指定する</span><span class="sxs-lookup"><span data-stu-id="ffc58-200">How to: Specify the Client Credential Type</span></span>](../../../docs/framework/wcf/how-to-specify-the-client-credential-type.md)
