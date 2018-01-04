---
title: "ロール ベース セキュリティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- role-based security, about role-based security
- user authentication, principals
- principals [.NET Framework]
- security [.NET Framework], role-based
- permissions [.NET Framework], principals
- authentication [.NET Framework], principals
- role-based security, principals
ms.assetid: 578cc32b-5654-4d8b-9d8c-ebcbc5c75390
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 18b2883fd69f5cadf2fce3dc677e5d2b79806d0b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="role-based-security"></a><span data-ttu-id="07e02-102">ロール ベース セキュリティ</span><span class="sxs-lookup"><span data-stu-id="07e02-102">Role-Based Security</span></span>
<span data-ttu-id="07e02-103">財務アプリケーションや業務アプリケーションでは、ポリシーを適用するためにロールが使用されることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="07e02-103">Roles are often used in financial or business applications to enforce policy.</span></span> <span data-ttu-id="07e02-104">たとえば、要求を出しているユーザーが指定のロールのメンバーかどうかに基づいて、処理するトランザクションのサイズにアプリケーションが制限を課すことがあります。</span><span class="sxs-lookup"><span data-stu-id="07e02-104">For example, an application might impose limits on the size of the transaction being processed depending on whether the user making the request is a member of a specified role.</span></span> <span data-ttu-id="07e02-105">たとえば、事務員には指定のしきい値よりも小さいトランザクションを処理する権限が与えられ、スーパーバイザにはより高いしきい値が与えられ、その上司にはさらに高いしきい値が与えられる (または制限がまったくない)、という場合です。</span><span class="sxs-lookup"><span data-stu-id="07e02-105">Clerks might have authorization to process transactions that are less than a specified threshold, supervisors might have a higher limit, and vice-presidents might have a still higher limit (or no limit at all).</span></span> <span data-ttu-id="07e02-106">アプリケーションで 1 つのアクションを完了するために複数の承認を必要とするときにも、ロール ベース セキュリティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="07e02-106">Role-based security can also be used when an application requires multiple approvals to complete an action.</span></span> <span data-ttu-id="07e02-107">たとえば、どの社員も購買の要求を生成できるものの、その要求を仕入先に送信できる購買発注に変換できるのは購買部門だけにする場合などが考えられます。</span><span class="sxs-lookup"><span data-stu-id="07e02-107">Such a case might be a purchasing system in which any employee can generate a purchase request, but only a purchasing agent can convert that request into a purchase order that can be sent to a supplier.</span></span>  
  
 <span data-ttu-id="07e02-108">.NET Framework のロール ベース セキュリティでは、関連付けられた ID で構築されるプリンシパルについての情報を現在のスレッドで使用できるようにすることによって、承認をサポートします。</span><span class="sxs-lookup"><span data-stu-id="07e02-108">.NET Framework role-based security supports authorization by making information about the principal, which is constructed from an associated identity, available to the current thread.</span></span> <span data-ttu-id="07e02-109">この場合の ID (および ID を利用して定義されるプリンシパル) は、Windows アカウントに基づく ID か、または Windows アカウントとは無関係のカスタム ID です。</span><span class="sxs-lookup"><span data-stu-id="07e02-109">The identity (and the principal it helps to define) can be either based on a Windows account or be a custom identity unrelated to a Windows account.</span></span> <span data-ttu-id="07e02-110">.NET Framework アプリケーションは、プリンシパルの ID、ロール メンバーシップ、またはその両方に基づいて、承認の決定を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="07e02-110">.NET Framework applications can make authorization decisions based on the principal's identity or role membership, or both.</span></span> <span data-ttu-id="07e02-111">ロールとは、セキュリティに関して同じ特権を持つプリンシパルの名前付きセット (窓口係や責任者など) です。</span><span class="sxs-lookup"><span data-stu-id="07e02-111">A role is a named set of principals that have the same privileges with respect to security (such as a teller or a manager).</span></span> <span data-ttu-id="07e02-112">プリンシパルは、1 つ以上のロールのメンバーであることができます。</span><span class="sxs-lookup"><span data-stu-id="07e02-112">A principal can be a member of one or more roles.</span></span> <span data-ttu-id="07e02-113">このため、アプリケーションはロール メンバーシップを使用して、要求されたアクションを実行する権限がプリンシパルにあるかどうかを決定できます。</span><span class="sxs-lookup"><span data-stu-id="07e02-113">Therefore, applications can use role membership to determine whether a principal is authorized to perform a requested action.</span></span>  
  
 <span data-ttu-id="07e02-114">使いやすさ、およびコード アクセス セキュリティとの一貫性を実現するため、.NET Framework のロール ベース セキュリティには <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> オブジェクトが用意されています。共通言語ランタイムは、このオブジェクトを使用することによって、コード アクセス セキュリティ チェックに似た方法で承認を実行できます。</span><span class="sxs-lookup"><span data-stu-id="07e02-114">To provide ease of use and consistency with code access security, .NET Framework role-based security provides <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> objects that enable the common language runtime to perform authorization in a way that is similar to code access security checks.</span></span> <span data-ttu-id="07e02-115"><xref:System.Security.Permissions.PrincipalPermission> クラスは、プリンシパルが一致している必要のある ID またはロールを表し、宣言セキュリティ チェックと強制セキュリティ チェックの両方と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="07e02-115">The <xref:System.Security.Permissions.PrincipalPermission> class represents the identity or role that the principal must match and is compatible with both declarative and imperative security checks.</span></span> <span data-ttu-id="07e02-116">プリンシパルの ID 情報に直接アクセスし、必要なときに、コード内でロール チェックと ID チェックを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="07e02-116">You can also access a principal's identity information directly and perform role and identity checks in your code when needed.</span></span>  
  
 <span data-ttu-id="07e02-117">.NET Framework のロール ベース セキュリティには、幅広いアプリケーションのニーズを満たせるだけの柔軟性と拡張性があります。</span><span class="sxs-lookup"><span data-stu-id="07e02-117">The .NET Framework provides role-based security support that is flexible and extensible enough to meet the needs of a wide spectrum of applications.</span></span> <span data-ttu-id="07e02-118">COM+ 1.0 Services などの既存の認証インフラストラクチャと相互運用する方法と、カスタムの認証システムを作成する方法のどちらかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="07e02-118">You can choose to interoperate with existing authentication infrastructures, such as COM+ 1.0 Services, or to create a custom authentication system.</span></span> <span data-ttu-id="07e02-119">ロール ベース セキュリティは、主にサーバー上で処理される ASP.NET Web アプリケーションでの使用に適しています。</span><span class="sxs-lookup"><span data-stu-id="07e02-119">Role-based security is particularly well-suited for use in ASP.NET Web applications, which are processed primarily on the server.</span></span> <span data-ttu-id="07e02-120">とはいえ、.NET Framework のロール ベース セキュリティは、クライアントとサーバーのどちらでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="07e02-120">However, .NET Framework role-based security can be used on either the client or the server.</span></span>  
  
 <span data-ttu-id="07e02-121">このセクションの内容を読み取る前に記載されている内容を理解することを確認してください[セキュリティの基本概念](../../../docs/standard/security/key-security-concepts.md)です。</span><span class="sxs-lookup"><span data-stu-id="07e02-121">Before reading this section, make sure that you understand the material presented in [Key Security Concepts](../../../docs/standard/security/key-security-concepts.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="07e02-122">関連トピック</span><span class="sxs-lookup"><span data-stu-id="07e02-122">Related Topics</span></span>  
  
|<span data-ttu-id="07e02-123">タイトル</span><span class="sxs-lookup"><span data-stu-id="07e02-123">Title</span></span>|<span data-ttu-id="07e02-124">説明</span><span class="sxs-lookup"><span data-stu-id="07e02-124">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="07e02-125">プリンシパル オブジェクトと ID オブジェクト</span><span class="sxs-lookup"><span data-stu-id="07e02-125">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)|<span data-ttu-id="07e02-126">Windows ID と Windows プリンシパル、汎用 ID と汎用プリンシパルの両方について、セットアップと管理方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="07e02-126">Explains how to set up and manage both Windows and generic identities and principals.</span></span>|  
|[<span data-ttu-id="07e02-127">セキュリティの基本概念</span><span class="sxs-lookup"><span data-stu-id="07e02-127">Key Security Concepts</span></span>](../../../docs/standard/security/key-security-concepts.md)|<span data-ttu-id="07e02-128">.NET Framework のセキュリティを使用する前に理解しておく必要のある、基本的な概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="07e02-128">Introduces fundamental concepts you must understand before using .NET Framework security.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="07e02-129">参照</span><span class="sxs-lookup"><span data-stu-id="07e02-129">Reference</span></span>  
 <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType>
