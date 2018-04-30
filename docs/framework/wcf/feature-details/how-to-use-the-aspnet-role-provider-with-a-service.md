---
title: '方法 : ASP.NET のロール プロバイダーとサービスを使用する'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9180ebe687d61315a66160a6fc95569a0e6b8e72
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a><span data-ttu-id="259a5-102">方法 : ASP.NET のロール プロバイダーとサービスを使用する</span><span class="sxs-lookup"><span data-stu-id="259a5-102">How to: Use the ASP.NET Role Provider with a Service</span></span>
<span data-ttu-id="259a5-103">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロール プロバイダーを [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] メンバーシップ プロバイダーと共に使用すると、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 開発者は、サイトで使用するアカウントをユーザーが作成し、承認のためにユーザーにロールを割り当てることができる Web サイトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="259a5-103">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider (in conjunction with the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider) is a feature that enables [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] developers to create Web sites that allow users to create an account with a site and to be assigned roles for authorization purposes.</span></span> <span data-ttu-id="259a5-104">この機能を使用すれば、ユーザーはだれでもサイトでアカウントを作成し、そのサイトにログインしてサービスに排他的にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="259a5-104">With this feature, any user can establish an account with the site, and log in for exclusive access to the site and its services.</span></span> <span data-ttu-id="259a5-105">これは、ユーザーが Windows ドメイン内にアカウントを持っていることが必要な Windows セキュリティとは対照的です。</span><span class="sxs-lookup"><span data-stu-id="259a5-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="259a5-106">自分の資格情報 (ユーザー名とパスワードの組み合わせ) を提示したユーザーは、だれでもサイトとそのサービスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="259a5-106">Instead, any user who supplies his or her credentials (the user name/password combination) can use the site and its services.</span></span>  
  
 <span data-ttu-id="259a5-107">サンプル アプリケーションについては「[メンバーシップとロール プロバイダー](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="259a5-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="259a5-108">詳細については、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]メンバーシップ プロバイダーの機能を参照してください[する方法: ASP.NET メンバーシップ プロバイダーを使用して](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)です。</span><span class="sxs-lookup"><span data-stu-id="259a5-108">For more information about the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider feature, see [How to: Use the ASP.NET Membership Provider](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span></span>  
  
 <span data-ttu-id="259a5-109">ロール プロバイダー機能では、SQL Server データベースを使用してユーザー情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="259a5-109">The role provider feature uses a SQL Server database to store user information.</span></span> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="259a5-110"> 開発者は、セキュリティを向上させるためにこれらの機能を利用できます。</span><span class="sxs-lookup"><span data-stu-id="259a5-110"> developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="259a5-111">この機能を [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションに統合した場合、ユーザーはユーザー名とパスワードの組み合わせを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント アプリケーションに提示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="259a5-111">When integrated into a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, users must supply a user name/password combination to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application.</span></span> <span data-ttu-id="259a5-112">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でデータベースを使用できるようにするには、<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> クラスのインスタンスを作成し、その <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> プロパティを <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> に設定してから、サービスをホストしている <xref:System.ServiceModel.ServiceHost> に対する動作のコレクションにそのインスタンスを追加します。</span><span class="sxs-lookup"><span data-stu-id="259a5-112">To enable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to use the database, you must create an instance of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> class, set its <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, and add the instance to the collection of behaviors to the <xref:System.ServiceModel.ServiceHost> that is hosting the service.</span></span>  
  
### <a name="to-configure-the-role-provider"></a><span data-ttu-id="259a5-113">ロール プロバイダーを構成するには</span><span class="sxs-lookup"><span data-stu-id="259a5-113">To configure the role provider</span></span>  
  
1.  <span data-ttu-id="259a5-114">Web.config ファイルで下にある、<`system.web`> 要素を追加、<`roleManager`> 要素の`enabled`属性を`true`です。</span><span class="sxs-lookup"><span data-stu-id="259a5-114">In the Web.config file, under the <`system.web`> element, add a <`roleManager`> element and set its `enabled` attribute to `true`.</span></span>  
  
2.  <span data-ttu-id="259a5-115">`defaultProvider` 属性を `SqlRoleProvider` に設定します。</span><span class="sxs-lookup"><span data-stu-id="259a5-115">Set the `defaultProvider` attribute to `SqlRoleProvider`.</span></span>  
  
3.  <span data-ttu-id="259a5-116">子として、<`roleManager`> 要素を追加、<`providers`> 要素。</span><span class="sxs-lookup"><span data-stu-id="259a5-116">As a child to the <`roleManager`> element, add a <`providers`> element.</span></span>  
  
4.  <span data-ttu-id="259a5-117">子として、<`providers`> 要素を追加、<`add`> 次の属性を持つ要素が適切な値に設定: `name`、 `type`、 `connectionStringName`、および`applicationName`次の例で示すように、します。</span><span class="sxs-lookup"><span data-stu-id="259a5-117">As a child to the <`providers`> element, add an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, and `applicationName`, as shown in the following example.</span></span>  
  
    ```xml  
    <!-- Configure the Sql Role Provider. -->  
    <roleManager enabled ="true"   
     defaultProvider ="SqlRoleProvider" >  
       <providers>  
         <add name ="SqlRoleProvider"   
           type="System.Web.Security.SqlRoleProvider"   
           connectionStringName="SqlConn"   
           applicationName="MembershipAndRoleProviderSample"/>  
       </providers>  
    </roleManager>  
    ```  
  
### <a name="to-configure-the-service-to-use-the-role-provider"></a><span data-ttu-id="259a5-118">ロール プロバイダーを使用するようにサービスを構成するには</span><span class="sxs-lookup"><span data-stu-id="259a5-118">To configure the service to use the role provider</span></span>  
  
1.  <span data-ttu-id="259a5-119">Web.config ファイルで追加、 [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)要素。</span><span class="sxs-lookup"><span data-stu-id="259a5-119">In the Web.config file, add a [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2.  <span data-ttu-id="259a5-120">追加、 [\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)要素を <`system.ServiceModel`> 要素。</span><span class="sxs-lookup"><span data-stu-id="259a5-120">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the <`system.ServiceModel`> element.</span></span>  
  
3.  <span data-ttu-id="259a5-121">追加、 [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)に、<`behaviors`> 要素。</span><span class="sxs-lookup"><span data-stu-id="259a5-121">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
4.  <span data-ttu-id="259a5-122">追加、 [\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)要素、`name`属性を適切な値にします。</span><span class="sxs-lookup"><span data-stu-id="259a5-122">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
5.  <span data-ttu-id="259a5-123">追加、 [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)に、<`behavior`> 要素。</span><span class="sxs-lookup"><span data-stu-id="259a5-123">Add a [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to the <`behavior`> element.</span></span>  
  
6.  <span data-ttu-id="259a5-124">`principalPermissionMode` 属性を `UseAspNetRoles` に設定します。</span><span class="sxs-lookup"><span data-stu-id="259a5-124">Set the `principalPermissionMode` attribute to `UseAspNetRoles`.</span></span>  
  
7.  <span data-ttu-id="259a5-125">`roleProviderName` 属性を `SqlRoleProvider` に設定します。</span><span class="sxs-lookup"><span data-stu-id="259a5-125">Set the `roleProviderName` attribute to `SqlRoleProvider`.</span></span> <span data-ttu-id="259a5-126">この構成の一部を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="259a5-126">The following example shows a fragment of the configuration.</span></span>  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
       <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                             roleProviderName ="SqlRoleProvider" />  
      </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="259a5-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="259a5-127">See Also</span></span>  
 [<span data-ttu-id="259a5-128">メンバーシップとロール プロバイダー</span><span class="sxs-lookup"><span data-stu-id="259a5-128">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)  
 [<span data-ttu-id="259a5-129">方法 : ASP.NET メンバーシップ プロバイダーを使用する</span><span class="sxs-lookup"><span data-stu-id="259a5-129">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
