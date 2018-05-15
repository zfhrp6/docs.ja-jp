---
title: プリンシパル オブジェクトの置き換え
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- principal objects, replacing
- security [.NET Framework], replacing principal objects
- security [.NET Framework], principals
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 94391471fecd92aeadec4da39cdd5b6f80bb6949
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="replacing-a-principal-object"></a><span data-ttu-id="7bf4c-102">プリンシパル オブジェクトの置き換え</span><span class="sxs-lookup"><span data-stu-id="7bf4c-102">Replacing a Principal Object</span></span>
<span data-ttu-id="7bf4c-103">認証サービスを提供するアプリケーションでは、特定のスレッドの **プリンシパル** オブジェクト (<xref:System.Security.Principal.IPrincipal>) を置換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7bf4c-103">Applications that provide authentication services must be able to replace the **Principal** object (<xref:System.Security.Principal.IPrincipal>) for a given thread.</span></span> <span data-ttu-id="7bf4c-104">さらに、虚偽の ID やロールを要求することにより、悪意をもってアタッチされた不適切な **プリンシパル** がアプリケーションのセキュリティに問題を生じさせるため、セキュリティ システムを活用して **プリンシパル** オブジェクトを置き換える機能を保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7bf4c-104">Furthermore, the security system must help protect the ability to replace **Principal** objects because a maliciously attached, incorrect **Principal** compromises the security of your application by claiming an untrue identity or role.</span></span> <span data-ttu-id="7bf4c-105">そのため、アプリケーションを必要とするを置き換える機能**プリンシパル**オブジェクトを付与する必要があります、<xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>プリンシパル コントロールのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7bf4c-105">Therefore, applications that require the ability to replace **Principal** objects must be granted the <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> object for principal control.</span></span> <span data-ttu-id="7bf4c-106">(ロール ベースのセキュリティ チェックを実行する、または **プリンシパル** オブジェクトを作成するために、このアクセス許可は必要がないことに注意してください。)</span><span class="sxs-lookup"><span data-stu-id="7bf4c-106">(Note that this permission is not required for performing role-based security checks or for creating **Principal** objects.)</span></span>  
  
 <span data-ttu-id="7bf4c-107">次のタスクを実行することによって、現在の **プリンシパル** オブジェクトを置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="7bf4c-107">The current **Principal** object can be replaced by performing the following tasks:</span></span>  
  
1.  <span data-ttu-id="7bf4c-108">置き換える **プリンシパル** オブジェクトと関連付けられている **ID** オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="7bf4c-108">Create the replacement **Principal** object and associated **Identity** object.</span></span>  
  
2.  <span data-ttu-id="7bf4c-109">新しい **プリンシパル** オブジェクトを呼び出しコンテキストにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="7bf4c-109">Attach the new **Principal** object to the call context.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bf4c-110">例</span><span class="sxs-lookup"><span data-stu-id="7bf4c-110">Example</span></span>  
 <span data-ttu-id="7bf4c-111">次の例では、汎用プリンシパル オブジェクトを作成し、それを使用してスレッドのプリンシパルを設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7bf4c-111">The following example shows how to create a generic principal object and use it to set the principal of a thread.</span></span>  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7bf4c-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="7bf4c-112">See Also</span></span>  
 <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>  
 [<span data-ttu-id="7bf4c-113">プリンシパル オブジェクトと ID オブジェクト</span><span class="sxs-lookup"><span data-stu-id="7bf4c-113">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
