---
title: "部分信頼コードからのライブラリの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [.NET Framework], partially trusted code
- partially trusted code
- partial trust
- AllowPartiallyTrustedCallersAttribute attribute
- code access security, partially trusted code
- APTCA
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
caps.latest.revision: "25"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7a452370df7c18f3e3f0190a14979099152485f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="using-libraries-from-partially-trusted-code"></a><span data-ttu-id="c2900-102">部分信頼コードからのライブラリの使用</span><span class="sxs-lookup"><span data-stu-id="c2900-102">Using Libraries from Partially Trusted Code</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
>  <span data-ttu-id="c2900-103">このトピックではアセンブリの厳密な名前の動作に対処し、のみ適用されます[レベル 1](../../../docs/framework/misc/security-transparent-code-level-1.md)アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="c2900-103">This topic addresses the behavior of strong-named assemblies and applies only to [Level 1](../../../docs/framework/misc/security-transparent-code-level-1.md) assemblies.</span></span> <span data-ttu-id="c2900-104">[セキュリティ透過的なコード、レベル 2](../../../docs/framework/misc/security-transparent-code-level-2.md)内のアセンブリ、[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]または後に影響ありません厳密な名前です。</span><span class="sxs-lookup"><span data-stu-id="c2900-104">[Security-Transparent Code, Level 2](../../../docs/framework/misc/security-transparent-code-level-2.md) assemblies in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] or later are not affected by strong names.</span></span> <span data-ttu-id="c2900-105">セキュリティ システムへの変更の詳細については、次を参照してください。[セキュリティの変更点](../../../docs/framework/security/security-changes.md)です。</span><span class="sxs-lookup"><span data-stu-id="c2900-105">For more information about changes to the security system, see [Security Changes](../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="c2900-106">呼び出して、共有ホストまたはサンド ボックスから完全な信頼は許可されませんよりも小さいを受信するアプリケーション マネージ ライブラリ、ライブラリの作成者具体的に許可を使用しない限り、<xref:System.Security.AllowPartiallyTrustedCallersAttribute>属性。</span><span class="sxs-lookup"><span data-stu-id="c2900-106">Applications that receive less than full trust from their host or sandbox are not allowed to call shared managed libraries unless the library writer specifically allows them to through the use of the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="c2900-107">そのため、アプリケーションの作成者は、ライブラリによっては部分的に信頼されたコンテキストから使用できないことを認識する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2900-107">Therefore, application writers must be aware that some libraries will not be available to them from a partially trusted context.</span></span> <span data-ttu-id="c2900-108">既定では、すべてのコードを実行する部分信頼で[サンド ボックス](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)ではありません。 完全信頼アセンブリの一覧が部分的に信頼されているとします。</span><span class="sxs-lookup"><span data-stu-id="c2900-108">By default, all code that executes in a partial-trust [sandbox](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md) and is not in the list of full-trust assemblies is partially trusted.</span></span> <span data-ttu-id="c2900-109">部分的に信頼されたコンテキストからコードを実行する、または部分的に信頼されたコードによってコードが呼び出されることはないと考えられる場合は、このセクションの情報を考慮する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c2900-109">If you do not expect your code to be executed from a partially trusted context or to be called by partially trusted code, you do not have to be concerned about the information in this section.</span></span> <span data-ttu-id="c2900-110">ただし、部分的に信頼されたコードと対話する必要があるコード、または部分的に信頼されたコンテキストから操作するコードを記述する場合は、次の要因を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2900-110">However, if you write code that must interact with partially trusted code or operate from a partially trusted context, you should consider the following factors:</span></span>  
  
-   <span data-ttu-id="c2900-111">ライブラリは、複数のアプリケーションで共有するために、厳密な名前で署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2900-111">Libraries must be signed with a strong name in order to be shared by multiple applications.</span></span> <span data-ttu-id="c2900-112">厳密な名前を使用すると、コードをグローバル アセンブリ キャッシュに配置したり、サンドボックス化する <xref:System.AppDomain> の完全信頼一覧に追加したりできます。また、コンシューマーは、実際にあなたが発信する特定のモバイル コードを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="c2900-112">Strong names allow your code to be placed in the global assembly cache or added to the full-trust list of a sandboxing <xref:System.AppDomain>, and allow consumers to verify that a particular piece of mobile code actually originates from you.</span></span>  
  
-   <span data-ttu-id="c2900-113">既定では、厳密な名前[レベル 1](../../../docs/framework/misc/security-transparent-code-level-1.md)共有ライブラリを暗黙的な実行[LinkDemand](../../../docs/framework/misc/link-demands.md)完全信頼に自動的には、ライブラリの作成者が何もする必要なし。</span><span class="sxs-lookup"><span data-stu-id="c2900-113">By default, strong-named [Level 1](../../../docs/framework/misc/security-transparent-code-level-1.md) shared libraries perform an implicit [LinkDemand](../../../docs/framework/misc/link-demands.md) for full trust automatically, without the library writer having to do anything.</span></span>  
  
-   <span data-ttu-id="c2900-114">呼び出し元に完全な信頼がないにもかかわらず、このようなライブラリを呼び出そうとする場合、ランタイムは <xref:System.Security.SecurityException> をスローします。これにより、呼び出し元はライブラリにリンクできなくなります。</span><span class="sxs-lookup"><span data-stu-id="c2900-114">If a caller does not have full trust but still tries to call such a library, the runtime throws a <xref:System.Security.SecurityException> and the caller is not allowed to link to the library.</span></span>  
  
-   <span data-ttu-id="c2900-115">自動を無効にするために**LinkDemand**と、例外がスローされないように、配置することができます、 **AllowPartiallyTrustedCallersAttribute**属性の共有アセンブリ スコープにライブラリです。</span><span class="sxs-lookup"><span data-stu-id="c2900-115">In order to disable the automatic **LinkDemand** and prevent the exception from being thrown, you can place the **AllowPartiallyTrustedCallersAttribute** attribute on the assembly scope of a shared library.</span></span> <span data-ttu-id="c2900-116">この属性により、部分的に信頼されたマネージ コードからライブラリを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="c2900-116">This attribute allows your libraries to be called from partially trusted managed code.</span></span>  
  
-   <span data-ttu-id="c2900-117">それでも、この属性を持つライブラリへのアクセスが許可されている部分的に信頼されたコードは、<xref:System.AppDomain> が定義する追加の制約を受けます。</span><span class="sxs-lookup"><span data-stu-id="c2900-117">Partially trusted code that is granted access to a library with this attribute is still subject to further restrictions defined by the <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="c2900-118">プログラムによる方法部分的に信頼されたコードを持たないライブラリを呼び出すことはありません、 **AllowPartiallyTrustedCallersAttribute**属性。</span><span class="sxs-lookup"><span data-stu-id="c2900-118">There is no programmatic way for partially trusted code to call a library that does not have the **AllowPartiallyTrustedCallersAttribute** attribute.</span></span>  
  
 <span data-ttu-id="c2900-119">特定のアプリケーションにとってプライベートなライブラリには、厳密な名前が不要または**AllowPartiallyTrustedCallersAttribute**属性し、アプリケーションの外部の悪意のあるコードによって参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="c2900-119">Libraries that are private to a specific application do not require a strong name or the **AllowPartiallyTrustedCallersAttribute** attribute and cannot be referenced by potentially malicious code outside the application.</span></span> <span data-ttu-id="c2900-120">このようなコードは、部分的に信頼されたモバイル コードの意図的または意図的でない誤使用から保護されています。開発者は追加で何かをする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c2900-120">Such code is protected against intentional or unintentional misuse by partially trusted mobile code without the developer having to do anything extra.</span></span>  
  
 <span data-ttu-id="c2900-121">次の種類のコードについて、部分的に信頼されたコードによる使用を明示的に有効にすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="c2900-121">You should consider explicitly enabling use by partially trusted code for the following types of code:</span></span>  
  
-   <span data-ttu-id="c2900-122">セキュリティの脆弱性を入念にテストされているし、で説明するガイドラインに準拠しているコード[安全なコーディングのガイドライン](../../../docs/standard/security/secure-coding-guidelines.md)です。</span><span class="sxs-lookup"><span data-stu-id="c2900-122">Code that has been diligently tested for security vulnerabilities and is in compliance with the guidelines described in [Secure Coding Guidelines](../../../docs/standard/security/secure-coding-guidelines.md).</span></span>  
  
-   <span data-ttu-id="c2900-123">部分的に信頼されたシナリオ用に特に記述された厳密な名前のコード ライブラリ。</span><span class="sxs-lookup"><span data-stu-id="c2900-123">Strong-named code libraries that are specifically written for partially trusted scenarios.</span></span>  
  
-   <span data-ttu-id="c2900-124">インターネットからダウンロードしたコードによって呼び出される、厳密な名前で署名された (部分的に信頼された、または完全に信頼された) すべてのコンポーネント。 </span><span class="sxs-lookup"><span data-stu-id="c2900-124">Any components (whether partially or fully trusted) signed with a strong name that will be called by code that is downloaded from the Internet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2900-125">.NET Framework クラス ライブラリの一部のクラスはありません、 **AllowPartiallyTrustedCallersAttribute**属性で、部分的に信頼されたコードから呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="c2900-125">Some classes in the .NET Framework class library do not have the **AllowPartiallyTrustedCallersAttribute** attribute and cannot be called by partially trusted code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2900-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2900-126">See Also</span></span>  
 [<span data-ttu-id="c2900-127">コード アクセス セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c2900-127">Code Access Security</span></span>](../../../docs/framework/misc/code-access-security.md)
