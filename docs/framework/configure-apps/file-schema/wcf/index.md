---
title: WCF 構成スキーマ
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: 147df2200017224bd20ad7eaca283f4dbcd08fb2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="wcf-configuration-schema"></a><span data-ttu-id="ea2a9-102">WCF 構成スキーマ</span><span class="sxs-lookup"><span data-stu-id="ea2a9-102">WCF Configuration Schema</span></span>
<span data-ttu-id="ea2a9-103">Windows Communication Foundation (WCF) 構成要素を使用して構成[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]サービスおよびクライアント アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="ea2a9-103">Windows Communication Foundation (WCF) configuration elements enable you to configure [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service and client applications.</span></span> <span data-ttu-id="ea2a9-104">[ 構成エディター ツール (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) を使用して、クライアントとサービスの構成ファイルを作成および変更できます。</span><span class="sxs-lookup"><span data-stu-id="ea2a9-104">You can use the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) to create and modify configuration files for clients and services.</span></span> <span data-ttu-id="ea2a9-105">構成ファイルは XML として書式設定されているので、テキスト エディターを使用して手動で編集する場合は、XML について理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea2a9-105">Since the configuration files are formatted as XML, you must be familiar with XML if you want to manually edit them using a text editor.</span></span> <span data-ttu-id="ea2a9-106">理解しないで編集すると、XML 要素タグや属性が見つからないなどの問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ea2a9-106">Otherwise, you may run into issues such as an unfound XML element tag or attribute.</span></span> <span data-ttu-id="ea2a9-107">問題の原因は、XML 要素タグと属性が大文字と小文字を区別することによります。</span><span class="sxs-lookup"><span data-stu-id="ea2a9-107">This is because XML element tags and attributes are case-sensitive.</span></span>  
  
 <span data-ttu-id="ea2a9-108">[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 構成システムは、<xref:System.Configuration> 名前空間に基づいています。</span><span class="sxs-lookup"><span data-stu-id="ea2a9-108">The [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] configuration system is based on the <xref:System.Configuration> namespace.</span></span> <span data-ttu-id="ea2a9-109">したがって、<xref:System.Configuration> 名前空間によって提供される、構成ロック、暗号化、マージなどのすべての標準機能を使用して、アプリケーションとその構成のセキュリティを強化できます。</span><span class="sxs-lookup"><span data-stu-id="ea2a9-109">Therefore, you can use all the standard features provided by the <xref:System.Configuration> namespace, such as configuration locking, encryption and merging to increase the security of your application and its configuration.</span></span> <span data-ttu-id="ea2a9-110">これらの概念の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea2a9-110">For more information on these concepts, see the following topics.</span></span>  
  
 [<span data-ttu-id="ea2a9-111">保護された構成を使用した構成情報の暗号化</span><span class="sxs-lookup"><span data-stu-id="ea2a9-111">Encrypting Configuration Information</span></span>](http://go.microsoft.com/fwlink/?LinkId=95337)  
  
 [<span data-ttu-id="ea2a9-112">構成設定のロック</span><span class="sxs-lookup"><span data-stu-id="ea2a9-112">Locking Configuration Settings</span></span>](http://go.microsoft.com/fwlink/?LinkId=95338)  
  
 <span data-ttu-id="ea2a9-113">このセクションでは、各構成項目のすべての可能な値についてと各構成項目が他の WCF 構成要素とやり取りする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ea2a9-113">This section describes all possible values of each configuration item, and how it interacts with other WCF configuration elements.</span></span> <span data-ttu-id="ea2a9-114">次のマップは、WCF 構成スキーマを示します。</span><span class="sxs-lookup"><span data-stu-id="ea2a9-114">The following map illustrates the WCF configuration schema.</span></span>  
  
 <span data-ttu-id="ea2a9-115">![WCF 構成スキーマ](../../../../../docs/framework/configure-apps/file-schema/wcf/media/orcasconfigschema.gif "OrcasConfigSchema")</span><span class="sxs-lookup"><span data-stu-id="ea2a9-115">![WCF Configuration Schema](../../../../../docs/framework/configure-apps/file-schema/wcf/media/orcasconfigschema.gif "OrcasConfigSchema")</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="ea2a9-116">潜在的なセキュリティ上の脅威を避けるために、アプリケーション構成ファイル (app.config) の [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 構成セクションは、適切なアクセス制御リスト (ACL) を使用して保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea2a9-116">You should protect [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] configuration sections in your application configuration files (app.config) with appropriate Access Control Lists (ACL) to prevent any potential security threats.</span></span>  <span data-ttu-id="ea2a9-117">たとえば、適切なユーザーだけが、アプリケーション バインドのセキュリティ設定、またはサービスの構成ファイルのサービス モデル セクションにアクセスまたは変更できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea2a9-117">For example, you should make sure that only the appropriate people can access or modify the security settings on application bindings, or the service model section of the configuration file for a service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ea2a9-118">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ea2a9-118">In This Section</span></span>  
 [<span data-ttu-id="ea2a9-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ea2a9-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
 <span data-ttu-id="ea2a9-120">`ServiceModel` 要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ea2a9-120">Describes the `ServiceModel` element.</span></span>  
  
 [<span data-ttu-id="ea2a9-121">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="ea2a9-121">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)  
 <span data-ttu-id="ea2a9-122">SMSvcHost.exe ツールを構成します。</span><span class="sxs-lookup"><span data-stu-id="ea2a9-122">Configures the SMSvcHost.exe tool.</span></span>  
  
 [<span data-ttu-id="ea2a9-123">\<system.runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="ea2a9-123">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
 <span data-ttu-id="ea2a9-124"><xref:System.Runtime.Serialization.DataContractSerializer> などのシリアライザーの使用時にオプションを設定するための最上位の要素。</span><span class="sxs-lookup"><span data-stu-id="ea2a9-124">The top-level element for setting options when using serializers such as the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ea2a9-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea2a9-125">Related Sections</span></span>  
 [<span data-ttu-id="ea2a9-126">Windows Communication Foundation アプリケーションの構成</span><span class="sxs-lookup"><span data-stu-id="ea2a9-126">Configuring Windows Communication Foundation Applications</span></span>](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 <span data-ttu-id="ea2a9-127">[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] のサービスとクライアントを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ea2a9-127">Describes how to configure [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services and clients.</span></span>
