---
title: "方法 : 企業内のエンドポイントをロックダウンする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b7eaab7-da60-4cf7-9d6a-ec02709cf75d
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5b6fa36a269dec4a191417813ec9c4ee26b699ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-lock-down-endpoints-in-the-enterprise"></a><span data-ttu-id="0ee41-102">方法 : 企業内のエンドポイントをロックダウンする</span><span class="sxs-lookup"><span data-stu-id="0ee41-102">How to: Lock Down Endpoints in the Enterprise</span></span>
<span data-ttu-id="0ee41-103">大規模な企業では、多くの場合、企業のセキュリティ ポリシーに準拠してアプリケーションを開発する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ee41-103">Large enterprises often require that applications are developed in compliance with enterprise security policies.</span></span> <span data-ttu-id="0ee41-104">ここでは、コンピューターにインストールされているすべての [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] クライアント アプリケーションを検証できるクライアント エンドポイント検証を開発してインストールする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="0ee41-104">The following topic discusses how to develop and install a client endpoint validator that can be used to validate all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client applications installed on computers.</span></span>  
  
 <span data-ttu-id="0ee41-105">この場合、検証コントロールは、クライアント検証コントロールをクライアントにこのエンドポイントの動作が追加されるため[ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) machine.config ファイル内のセクションです。</span><span class="sxs-lookup"><span data-stu-id="0ee41-105">In this case, the validator is a client validator because this endpoint behavior is added to the client [\<commonBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) section in the machine.config file.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="0ee41-106"> は、クライアント アプリケーションだけを対象に共通のエンドポイント動作を読み込み、サービス アプリケーションだけを対象に共通のサービス動作を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="0ee41-106"> loads common endpoint behaviors only for client applications and loads common service behaviors only for service applications.</span></span> <span data-ttu-id="0ee41-107">サービス アプリケーション用のこの同じ検証コントロールをインストールするには、検証コントロールがサービス動作であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="0ee41-107">To install this same validator for service applications, the validator must be a service behavior.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="0ee41-108">[ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)セクションです。</span><span class="sxs-lookup"><span data-stu-id="0ee41-108"> the [\<commonBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) section.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0ee41-109">サービスまたはエンドポイントの動作でマークされていない、<xref:System.Security.AllowPartiallyTrustedCallersAttribute>属性 (APTCA) に追加される、 [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)部分的な信頼でアプリケーションを実行すると、構成ファイルのセクションが実行されませんこのエラーが発生、環境、および例外がスローされません。</span><span class="sxs-lookup"><span data-stu-id="0ee41-109">Service or endpoint behaviors not marked with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute (APTCA) that are added to the [\<commonBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) section of a configuration file are not run when the application runs in a partial trust environment, and no exception is thrown when this occurs.</span></span> <span data-ttu-id="0ee41-110">検証コントロールなどの共通動作を強制的に実行するには、次のいずれかを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ee41-110">To enforce the running of common behaviors such as validators, you must either:</span></span>  
>   
>  <span data-ttu-id="0ee41-111">-- 共通動作を <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 属性でマークし、部分信頼アプリケーションとして展開したときに実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="0ee41-111">-- Mark your common behavior with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute so that it can run when deployed as a Partial Trust application.</span></span> <span data-ttu-id="0ee41-112">APTCA でマークされたアセンブリを実行できないように、コンピューターでレジストリ エントリを設定できます。</span><span class="sxs-lookup"><span data-stu-id="0ee41-112">Note that a registry entry can be set on the computer to prevent APTCA-marked assemblies from running..</span></span>  
>   
>  <span data-ttu-id="0ee41-113">-- アプリケーションが完全信頼アプリケーションとして配置されている場合に、ユーザーが部分信頼環境でアプリケーションを実行するようにコード アクセス セキュリティ設定を変更できないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="0ee41-113">-- Ensure that if the application is deployed as a fully-trusted application that users cannot modify the code-access security settings to run the application in a Partial Trust environment.</span></span> <span data-ttu-id="0ee41-114">ユーザーがこのような変更を行うことができる場合、カスタム検証コントロールは実行されず、例外もスローされません。</span><span class="sxs-lookup"><span data-stu-id="0ee41-114">If they can do so, the custom validator does not run and no exception is thrown.</span></span> <span data-ttu-id="0ee41-115">これを確認する方法の 1 つを参照してください、`levelfinal`オプションを使用して[コード アクセス セキュリティ ポリシー ツール (Caspol.exe)](http://go.microsoft.com/fwlink/?LinkId=248222)です。</span><span class="sxs-lookup"><span data-stu-id="0ee41-115">For one way to ensure this, see the `levelfinal` option using [Code Access Security Policy Tool (Caspol.exe)](http://go.microsoft.com/fwlink/?LinkId=248222).</span></span>  
>   
>  <span data-ttu-id="0ee41-116">詳細については、次を参照してください。[部分的な信頼のベスト プラクティス](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md)と[展開シナリオのサポートされている](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md)です。</span><span class="sxs-lookup"><span data-stu-id="0ee41-116">For more information, see [Partial Trust Best Practices](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md) and [Supported Deployment Scenarios](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md).</span></span>  
  
### <a name="to-create-the-endpoint-validator"></a><span data-ttu-id="0ee41-117">エンドポイント検証コントロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="0ee41-117">To create the endpoint validator</span></span>  
  
1.  <span data-ttu-id="0ee41-118"><xref:System.ServiceModel.Description.IEndpointBehavior> メソッドに、必要な検証手順を備えた <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A> を作成します。</span><span class="sxs-lookup"><span data-stu-id="0ee41-118">Create an <xref:System.ServiceModel.Description.IEndpointBehavior> with the desired validation steps in the <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A> method.</span></span> <span data-ttu-id="0ee41-119">次にコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="0ee41-119">The following code provides an example.</span></span> <span data-ttu-id="0ee41-120">(、`InternetClientValidatorBehavior`から取得した、[セキュリティ検証](../../../../docs/framework/wcf/samples/security-validation.md)サンプルです)。</span><span class="sxs-lookup"><span data-stu-id="0ee41-120">(The `InternetClientValidatorBehavior` is taken from the [Security Validation](../../../../docs/framework/wcf/samples/security-validation.md) sample.)</span></span>  
  
     [!code-csharp[LockdownValidation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorbehavior.cs#2)]  
  
2.  <span data-ttu-id="0ee41-121">手順 1. で作成したエンドポイント検証コントロールを登録する新しい <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> を作成します。</span><span class="sxs-lookup"><span data-stu-id="0ee41-121">Create new <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> that registers the endpoint validator created in step 1.</span></span> <span data-ttu-id="0ee41-122">このコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0ee41-122">The following code example shows this.</span></span> <span data-ttu-id="0ee41-123">(この例の元のコードは、[セキュリティ検証](../../../../docs/framework/wcf/samples/security-validation.md)サンプルです)。</span><span class="sxs-lookup"><span data-stu-id="0ee41-123">(The original code for this example is in the [Security Validation](../../../../docs/framework/wcf/samples/security-validation.md) sample.)</span></span>  
  
     [!code-csharp[LockdownValidation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorelement.cs#3)]  
  
3.  <span data-ttu-id="0ee41-124">コンパイル済みのアセンブリが厳密な名前で署名されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0ee41-124">Make sure the compiled assembly is signed with a strong name.</span></span> <span data-ttu-id="0ee41-125">詳細については、次を参照してください。、[厳密名ツール (SN です。EXE)](http://go.microsoft.com/fwlink/?LinkId=248217)と言語のコンパイラ コマンド。</span><span class="sxs-lookup"><span data-stu-id="0ee41-125">For details, see the [Strong Name Tool (SN.EXE)](http://go.microsoft.com/fwlink/?LinkId=248217) and the compiler commands for your language.</span></span>  
  
### <a name="to-install-the-validator-into-the-target-computer"></a><span data-ttu-id="0ee41-126">検証コントロールをターゲット コンピューターにインストールには</span><span class="sxs-lookup"><span data-stu-id="0ee41-126">To install the validator into the target computer</span></span>  
  
1.  <span data-ttu-id="0ee41-127">適切な機構を使用してエンドポイント検証をインストールします。</span><span class="sxs-lookup"><span data-stu-id="0ee41-127">Install the endpoint validator using the appropriate mechanism.</span></span> <span data-ttu-id="0ee41-128">企業では、グループ ポリシーと Systems Management Server (SMS) を使用してインストールします。</span><span class="sxs-lookup"><span data-stu-id="0ee41-128">In an enterprise, this can be using Group Policy and Systems Management Server (SMS).</span></span>  
  
2.  <span data-ttu-id="0ee41-129">厳密な名前付きアセンブリをグローバル アセンブリ キャッシュを使用して、インストール、 [Gacutil.exe (グローバル アセンブリ キャッシュ ツール)](http://msdn.microsoft.com/library/ex0ss12c\(v=vs.110\).aspx)です。</span><span class="sxs-lookup"><span data-stu-id="0ee41-129">Install the strongly-named assembly into the global assembly cache using the [Gacutil.exe (Global Assembly Cache Tool)](http://msdn.microsoft.com/library/ex0ss12c\(v=vs.110\).aspx).</span></span>  
  
3.  <span data-ttu-id="0ee41-130"><xref:System.Configuration?displayProperty=nameWithType> 名前空間の型を使用して、次の処理を行います。</span><span class="sxs-lookup"><span data-stu-id="0ee41-130">Use the <xref:System.Configuration?displayProperty=nameWithType> namespace types to:</span></span>  
  
    1.  <span data-ttu-id="0ee41-131">拡張機能を追加、 [ \<behaviorExtensions >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)セクションの完全修飾型名を使用して要素をロックします。</span><span class="sxs-lookup"><span data-stu-id="0ee41-131">Add the extension to the [\<behaviorExtensions>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md) section using a fully-qualified type name and lock the element.</span></span>  
  
         [!code-csharp[LockdownValidation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#5)]  
  
    2.  <span data-ttu-id="0ee41-132">動作要素を追加、`EndpointBehaviors`のプロパティ、 [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)セクションし、要素をロックします。</span><span class="sxs-lookup"><span data-stu-id="0ee41-132">Add the behavior element to the `EndpointBehaviors` property of the [\<commonBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) section and lock the element.</span></span> <span data-ttu-id="0ee41-133">(サービスの検証コントロールをインストールするには、検証コントロールが <xref:System.ServiceModel.Description.IServiceBehavior> であることが必要です。また、検証コントロールを `ServiceBehaviors` プロパティに追加する必要があります)。次のコード例は、手順 a.</span><span class="sxs-lookup"><span data-stu-id="0ee41-133">(To install the validator on the service, the validator must be an <xref:System.ServiceModel.Description.IServiceBehavior> and added to the `ServiceBehaviors` property.) The following code example shows the proper configuration after steps a.</span></span> <span data-ttu-id="0ee41-134">と b. の後の適切な構成を示しています。厳密な名前が存在しない点だけが異なります。</span><span class="sxs-lookup"><span data-stu-id="0ee41-134">and b., with the sole exception that there is no strong name.</span></span>  
  
         [!code-csharp[LockdownValidation#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#6)]  
  
    3.  <span data-ttu-id="0ee41-135">machine.config ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="0ee41-135">Save the machine.config file.</span></span> <span data-ttu-id="0ee41-136">次のコード例では、手順 3. にあるすべてのタスクを実行しますが、変更された machine.config ファイルのコピーはローカルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="0ee41-136">The following code example performs all the tasks in step 3 but saves a copy of the modified machine.config file locally.</span></span>  
  
         [!code-csharp[LockdownValidation#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#7)]  
  
## <a name="example"></a><span data-ttu-id="0ee41-137">例</span><span class="sxs-lookup"><span data-stu-id="0ee41-137">Example</span></span>  
 <span data-ttu-id="0ee41-138">次のコード例では、machine.config ファイルに共通の動作を追加し、そのコピーをディスクに保存する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0ee41-138">The following code example shows how to add a common behavior to the machine.config file and save a copy to the disk.</span></span> <span data-ttu-id="0ee41-139">`InternetClientValidatorBehavior`から取得した、[セキュリティ検証](../../../../docs/framework/wcf/samples/security-validation.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="0ee41-139">The `InternetClientValidatorBehavior` is taken from the [Security Validation](../../../../docs/framework/wcf/samples/security-validation.md) sample.</span></span>  
  
 [!code-csharp[LockdownValidation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="0ee41-140">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="0ee41-140">.NET Framework Security</span></span>  
 <span data-ttu-id="0ee41-141">また、構成ファイルの要素を暗号化する必要がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="0ee41-141">You may also want to encrypt the configuration file elements.</span></span> <span data-ttu-id="0ee41-142">詳細については、「参照」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ee41-142">For more information, see the See Also section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ee41-143">参照</span><span class="sxs-lookup"><span data-stu-id="0ee41-143">See Also</span></span>  
 [<span data-ttu-id="0ee41-144">DPAPI を使用する暗号化の構成ファイルの要素</span><span class="sxs-lookup"><span data-stu-id="0ee41-144">Encrypting configuration file elements using DPAPI</span></span>](http://go.microsoft.com/fwlink/?LinkId=94954)  
 [<span data-ttu-id="0ee41-145">RSA を使用して、暗号化のための構成ファイルの要素</span><span class="sxs-lookup"><span data-stu-id="0ee41-145">Encrypting configuration file elements using RSA</span></span>](http://go.microsoft.com/fwlink/?LinkId=94955)
