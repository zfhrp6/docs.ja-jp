---
title: "発行者名レジストリの検証"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4644dd1-dead-48ff-abeb-7bffae69a6ac
caps.latest.revision: "4"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d131a032aa2747bda83874e8dd744588dfe07dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="validating-issuer-name-registry"></a><span data-ttu-id="32474-102">発行者名レジストリの検証</span><span class="sxs-lookup"><span data-stu-id="32474-102">Validating Issuer Name Registry</span></span>
<span data-ttu-id="32474-103">Windows Identity Foundation の Validating Issuer Name Registry (VINR) 拡張機能を使用すると、受信トークンが信頼できるテナントおよび ID プロバイダーから発行されたことをマルチテナント アプリケーションが確認できます。</span><span class="sxs-lookup"><span data-stu-id="32474-103">The Validating Issuer Name Registry (VINR) for Windows Identity Foundation enables multi-tenant applications to ensure that an incoming token has been issued by a trusted tenant and identity provider.</span></span> <span data-ttu-id="32474-104">Microsoft Azure AD によって発行されるすべてのトークンは同じ証明書を使用して署名されているため、この機能は Microsoft Azure Active Directory を使用するマルチテナント アプリケーションに特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="32474-104">This functionality is particularly useful for multi-tenant applications that use Windows Azure Active Directory because all tokens issued by Windows Azure AD are signed using the same certificate.</span></span> <span data-ttu-id="32474-105">同じ証明書を使用する (つまり、母音が同じ) 複数のテナントからの要求を区別するため、アプリケーションはテナントごとに発行者名を維持して検証ロジックを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32474-105">In order to differentiate between requests from multiple tenants that use the same certificate – and consequently have the same thumbprint – your application must persist the issuer name for each tenant to perform validation logic.</span></span> <span data-ttu-id="32474-106">VINR にはこの機能が備わっており、カスタム検証ロジックを追加したり、構成ファイル以外の場所に発行者のレジストリ データを格納したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="32474-106">The VINR provides this functionality, and it also enables you to add custom validation logic or to store the issuer registry data in locations other than a configuration file.</span></span> <span data-ttu-id="32474-107">この拡張機能は、アプリケーションの WIF パイプラインに追加したり、別個に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="32474-107">The extension can be added to your application’s WIF pipeline or it can be used independently.</span></span>  
  
 <span data-ttu-id="32474-108">VINR は NuGet パッケージとして入手できます。</span><span class="sxs-lookup"><span data-stu-id="32474-108">The VINR is available as a NuGet package.</span></span> <span data-ttu-id="32474-109">詳細については、「[Downloading the Validating Issuer Name Registry Package](../../../docs/framework/security/downloading-the-validating-issuer-name-registry-package.md)」(発行者名レジストリの検証パッケージのダウンロード) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32474-109">See [Downloading the Validating Issuer Name Registry Package](../../../docs/framework/security/downloading-the-validating-issuer-name-registry-package.md) for more information.</span></span>  
  
## <a name="scenarios"></a><span data-ttu-id="32474-110">シナリオ</span><span class="sxs-lookup"><span data-stu-id="32474-110">Scenarios</span></span>  
 <span data-ttu-id="32474-111">VINR により、次の主要なシナリオが可能になります。</span><span class="sxs-lookup"><span data-stu-id="32474-111">The VINR enables the following key scenario:</span></span>  
  
-   <span data-ttu-id="32474-112">**マルチテナント アプリケーションのトークンを検証する**: このシナリオでは、Litware という会社が Windows Azure AD として ID プロバイダーを使用するマルチテナント アプリケーションを開発しました。</span><span class="sxs-lookup"><span data-stu-id="32474-112">**Validate a Token in a Multi-Tenant Application**: In this scenario, a company named Litware has developed a multi-tenant application that uses an identity provider such as Windows Azure AD.</span></span> <span data-ttu-id="32474-113">このアプリケーションは、2 つの顧客 (Contoso および Fabrikam) にサービスを提供しています。</span><span class="sxs-lookup"><span data-stu-id="32474-113">This application serves two customers: Contoso and Fabrikam.</span></span> <span data-ttu-id="32474-114">Fabrikam のユーザーが Litware のアプリケーションで認証を行うと、Microsoft Azure AD から生成されるトークンは標準の証明書を使用して署名され、要求は Fabrikam により発行されます。</span><span class="sxs-lookup"><span data-stu-id="32474-114">When a user from Fabrikam authenticates to Litware’s application, the resulting token from Windows Azure AD is signed using its standard certificate and the request is issued by Fabrikam.</span></span> <span data-ttu-id="32474-115">アプリケーションは発行者名とトークンの両方が有効であることを検証し、Windows Azure AD の同じ証明書を使用して署名された Contoso からの要求を区別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32474-115">The application needs to verify that both the issuer name and the token is valid, and needs to differentiate requests from Contoso that are signed using the same certificate from Windows Azure AD.</span></span> <span data-ttu-id="32474-116">VINR を使用すると、Litware アプリケーションが Contoso や Fabrikam などのマルチテナントからの要求を簡単に区別できるようになります。</span><span class="sxs-lookup"><span data-stu-id="32474-116">The VINR makes it easy for Litware’s application to differentiate and validate requests from multiple tenants such as Contoso and Fabrikam.</span></span>  
  
## <a name="features"></a><span data-ttu-id="32474-117">機能</span><span class="sxs-lookup"><span data-stu-id="32474-117">Features</span></span>  
 <span data-ttu-id="32474-118">VINR には次の機能があります。</span><span class="sxs-lookup"><span data-stu-id="32474-118">The VINR offers the following features:</span></span>  
  
-   <span data-ttu-id="32474-119">**マルチテナント アプリケーションの発行者名とトークンの検証**: 発行者名 (テナント) と、トークンが ID プロバイダーの有効な証明書を使用して署名されたかどうかを確認することで、受信トークンを検証します。</span><span class="sxs-lookup"><span data-stu-id="32474-119">**Issuer Name and Token Validation for Multi-Tenant Applications**: Validates the incoming token by verifying the issuer name (tenant) and whether the token was signed using a valid certificate from the identity provider.</span></span>  
  
-   <span data-ttu-id="32474-120">**カスタム検証ロジックとデータ ストアの機能拡張**: 独自の検証ロジックを挿入し、既定の構成ファイル以外のデータ ストアを指定するための機能拡張を提供します。</span><span class="sxs-lookup"><span data-stu-id="32474-120">**Extensibility for Custom Validation Logic and Data Stores**: Provides extensibility to inject your own validation logic and to specify a data store other than the default configuration file.</span></span>
