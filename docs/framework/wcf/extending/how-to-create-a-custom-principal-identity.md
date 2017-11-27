---
title: "方法 : カスタム プリンシパル ID を作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IPrincipal
- IAuthorizationPolicy
- PrincipalPermissionMode
- PrincipalPermissionAttribute
ms.assetid: c4845fca-0ed9-4adf-bbdc-10812be69b61
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 973b3ebbedf80a7c33047f74306232805989646c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-principal-identity"></a><span data-ttu-id="3396b-102">方法 : カスタム プリンシパル ID を作成する</span><span class="sxs-lookup"><span data-stu-id="3396b-102">How to: Create a Custom Principal Identity</span></span>
<span data-ttu-id="3396b-103"><xref:System.Security.Permissions.PrincipalPermissionAttribute> は、サービス メソッドへのアクセスを宣言によって制御する手段として使用できます。</span><span class="sxs-lookup"><span data-stu-id="3396b-103">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is a declarative means of controlling access to service methods.</span></span> <span data-ttu-id="3396b-104">この属性を使用する場合、承認チェックを実行するためのモードが <xref:System.ServiceModel.Description.PrincipalPermissionMode> 列挙体で指定されます。</span><span class="sxs-lookup"><span data-stu-id="3396b-104">When using this attribute, the <xref:System.ServiceModel.Description.PrincipalPermissionMode> enumeration specifies the mode for performing authorization checks.</span></span> <span data-ttu-id="3396b-105">このモードが <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> に設定されている場合、ユーザーは、<xref:System.Security.Principal.IPrincipal> プロパティから返されるカスタムの <xref:System.Threading.Thread.CurrentPrincipal%2A> クラスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="3396b-105">When this mode is set to <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, it enables the user to specify a custom <xref:System.Security.Principal.IPrincipal> class returned by the <xref:System.Threading.Thread.CurrentPrincipal%2A> property.</span></span> <span data-ttu-id="3396b-106">ここでは、<xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> を、カスタム承認ポリシーおよびカスタム プリンシパルと組み合わせて使用する場合のシナリオを説明します。</span><span class="sxs-lookup"><span data-stu-id="3396b-106">This topic illustrates the scenario when <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> is used in combination with a custom authorization policy and a custom principal.</span></span>  
  
 <span data-ttu-id="3396b-107">使用しての詳細については、<xref:System.Security.Permissions.PrincipalPermissionAttribute>を参照してください[する方法: PrincipalPermissionAttribute クラスを使用したアクセスの制限](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)です。</span><span class="sxs-lookup"><span data-stu-id="3396b-107">For more information about using the <xref:System.Security.Permissions.PrincipalPermissionAttribute>, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3396b-108">例</span><span class="sxs-lookup"><span data-stu-id="3396b-108">Example</span></span>  
 [!code-csharp[PrincipalPermissionMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/principalpermissionmode/cs/source.cs#8)]
 [!code-vb[PrincipalPermissionMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/principalpermissionmode/vb/source.vb#8)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3396b-109">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="3396b-109">Compiling the Code</span></span>  
 <span data-ttu-id="3396b-110">このコードをコンパイルするには、次の名前空間へ参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="3396b-110">References to the following namespaces are needed to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.Collections.Generic>  
  
-   <xref:System.Security.Permissions>  
  
-   <xref:System.Security.Principal>  
  
-   <xref:System.Threading>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Description>  
  
-   <xref:System.IdentityModel.Claims>  
  
-   <xref:System.IdentityModel.Policy>  
  
## <a name="see-also"></a><span data-ttu-id="3396b-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="3396b-111">See Also</span></span>  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 [<span data-ttu-id="3396b-112">方法: サービスで ASP.NET ロール プロバイダーを使用</span><span class="sxs-lookup"><span data-stu-id="3396b-112">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [<span data-ttu-id="3396b-113">方法: PrincipalPermissionAttribute クラスでアクセスを制限する</span><span class="sxs-lookup"><span data-stu-id="3396b-113">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
