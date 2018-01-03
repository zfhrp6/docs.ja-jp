---
title: "危険なアクセス許可とポリシー管理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 471570aec43398b05b8678bdcf74a3ef2494e289
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="7a573-102">危険なアクセス許可とポリシー管理</span><span class="sxs-lookup"><span data-stu-id="7a573-102">Dangerous Permissions and Policy Administration</span></span>
<span data-ttu-id="7a573-103">.NET Framework がアクセス許可を提供する保護された操作のいくつかで、セキュリティ システムが回避されてしまう可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7a573-103">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="7a573-104">これらの危険なアクセス許可は信頼できるコードにのみ付与し、その付与は必要な場合に限る必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a573-104">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="7a573-105">これらのアクセス許可が付与されると、通常、悪意のあるコードに対する防御策はありません。</span><span class="sxs-lookup"><span data-stu-id="7a573-105">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a573-106">[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]では、.NET Framework のセキュリティ モデルと用語に重要な変更が加えられています。</span><span class="sxs-lookup"><span data-stu-id="7a573-106">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="7a573-107">これらの変更の詳細については、次を参照してください。[セキュリティの変更点](../../../docs/framework/security/security-changes.md)です。</span><span class="sxs-lookup"><span data-stu-id="7a573-107">For more information about these changes, see [Security Changes](../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="7a573-108">危険なアクセス許可については、次の表で説明します。</span><span class="sxs-lookup"><span data-stu-id="7a573-108">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="7a573-109">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="7a573-109">Permission</span></span>|<span data-ttu-id="7a573-110">潜在的なリスク</span><span class="sxs-lookup"><span data-stu-id="7a573-110">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="7a573-111">マネージ コードからアンマネージ コードを呼び出せるようにしますが、これは大抵リスクを伴います。</span><span class="sxs-lookup"><span data-stu-id="7a573-111">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="7a573-112">検証なしで、コードは何でも実行できます。</span><span class="sxs-lookup"><span data-stu-id="7a573-112">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="7a573-113">無効な証拠でセキュリティ ポリシーをかいくぐることができます。</span><span class="sxs-lookup"><span data-stu-id="7a573-113">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="7a573-114">セキュリティ ポリシーを変更する機能によって、セキュリティを無効にできます。</span><span class="sxs-lookup"><span data-stu-id="7a573-114">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="7a573-115">シリアル化を使用して、ユーザー補助機能のメカニズムを回避できます。</span><span class="sxs-lookup"><span data-stu-id="7a573-115">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="7a573-116">詳細については、「 [セキュリティとシリアル化](../../../docs/framework/misc/security-and-serialization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a573-116">For details, see [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="7a573-117">現行プリンシパルを設定する機能によって、ロール ベースのセキュリティを欺くことができます。</span><span class="sxs-lookup"><span data-stu-id="7a573-117">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="7a573-118">スレッドにはセキュリティ状態が関連付けられているため、スレッドの操作は危険です。</span><span class="sxs-lookup"><span data-stu-id="7a573-118">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="7a573-119">プライベート メンバーを使用して、ユーザー補助機能のメカニズムを無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="7a573-119">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7a573-120">参照</span><span class="sxs-lookup"><span data-stu-id="7a573-120">See Also</span></span>  
 [<span data-ttu-id="7a573-121">安全なコーディングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="7a573-121">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
