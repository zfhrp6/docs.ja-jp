---
title: '&lt;generatePublisherEvidence&gt;要素'
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f56bbef6ed6decf6be4246f649665db4cf0f766
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746021"
---
# <a name="ltgeneratepublisherevidencegt-element"></a><span data-ttu-id="ed00a-102">&lt;generatePublisherEvidence&gt;要素</span><span class="sxs-lookup"><span data-stu-id="ed00a-102">&lt;generatePublisherEvidence&gt; Element</span></span>
<span data-ttu-id="ed00a-103">ランタイムを作成するかどうかを示す<xref:System.Security.Policy.Publisher>コード アクセス セキュリティ (CAS) の証拠。</span><span class="sxs-lookup"><span data-stu-id="ed00a-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
 <span data-ttu-id="ed00a-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="ed00a-104">\<configuration></span></span>  
<span data-ttu-id="ed00a-105">\<ランタイム ></span><span class="sxs-lookup"><span data-stu-id="ed00a-105">\<runtime></span></span>  
<span data-ttu-id="ed00a-106">\<generatePublisherEvidence ></span><span class="sxs-lookup"><span data-stu-id="ed00a-106">\<generatePublisherEvidence></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed00a-107">構文</span><span class="sxs-lookup"><span data-stu-id="ed00a-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed00a-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ed00a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ed00a-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ed00a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed00a-110">属性</span><span class="sxs-lookup"><span data-stu-id="ed00a-110">Attributes</span></span>  
  
|<span data-ttu-id="ed00a-111">属性</span><span class="sxs-lookup"><span data-stu-id="ed00a-111">Attribute</span></span>|<span data-ttu-id="ed00a-112">説明</span><span class="sxs-lookup"><span data-stu-id="ed00a-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ed00a-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="ed00a-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ed00a-114">ランタイムを作成するかどうかを示す<xref:System.Security.Policy.Publisher>証拠。</span><span class="sxs-lookup"><span data-stu-id="ed00a-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ed00a-115">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="ed00a-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="ed00a-116">値</span><span class="sxs-lookup"><span data-stu-id="ed00a-116">Value</span></span>|<span data-ttu-id="ed00a-117">説明</span><span class="sxs-lookup"><span data-stu-id="ed00a-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="ed00a-118">作成されません<xref:System.Security.Policy.Publisher>証拠。</span><span class="sxs-lookup"><span data-stu-id="ed00a-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="ed00a-119">作成<xref:System.Security.Policy.Publisher>証拠。</span><span class="sxs-lookup"><span data-stu-id="ed00a-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="ed00a-120">既定値です。</span><span class="sxs-lookup"><span data-stu-id="ed00a-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ed00a-121">子要素</span><span class="sxs-lookup"><span data-stu-id="ed00a-121">Child Elements</span></span>  
 <span data-ttu-id="ed00a-122">なし。</span><span class="sxs-lookup"><span data-stu-id="ed00a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ed00a-123">親要素</span><span class="sxs-lookup"><span data-stu-id="ed00a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ed00a-124">要素</span><span class="sxs-lookup"><span data-stu-id="ed00a-124">Element</span></span>|<span data-ttu-id="ed00a-125">説明</span><span class="sxs-lookup"><span data-stu-id="ed00a-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ed00a-126">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="ed00a-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ed00a-127">ランタイム初期化オプションに関する情報を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="ed00a-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed00a-128">コメント</span><span class="sxs-lookup"><span data-stu-id="ed00a-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed00a-129">[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]後で、この要素にはアセンブリの読み込み時間に影響はありません。</span><span class="sxs-lookup"><span data-stu-id="ed00a-129">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="ed00a-130">詳細についてを参照してください「セキュリティ ポリシーの簡略化」[セキュリティの変更点](../../../../../docs/framework/security/security-changes.md)です。</span><span class="sxs-lookup"><span data-stu-id="ed00a-130">For more information, see the "Security Policy Simplification" section in [Security Changes](../../../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="ed00a-131">共通言語ランタイム (CLR) を作成する読み込み時に、Authenticode 署名を検証しようとしました。 <xref:System.Security.Policy.Publisher> 、アセンブリの証拠。</span><span class="sxs-lookup"><span data-stu-id="ed00a-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="ed00a-132">ただし、既定では、ほとんどのアプリケーションは必要ありません<xref:System.Security.Policy.Publisher>証拠。</span><span class="sxs-lookup"><span data-stu-id="ed00a-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="ed00a-133">標準の CAS ポリシーに頼りません、<xref:System.Security.Policy.PublisherMembershipCondition>です。</span><span class="sxs-lookup"><span data-stu-id="ed00a-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="ed00a-134">アプリケーションがカスタムの CAS ポリシーを使用しているコンピューター上で実行またはの需要を満たすために意図しない限り、発行元の署名の検証に関連付けられている不要なスタートアップ コストを回避する必要があります<xref:System.Security.Permissions.PublisherIdentityPermission>部分的に信頼された環境でします。</span><span class="sxs-lookup"><span data-stu-id="ed00a-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="ed00a-135">(Id アクセス許可の要求は常には、完全に信頼された環境で失敗した)。</span><span class="sxs-lookup"><span data-stu-id="ed00a-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed00a-136">サービスが使用することをお勧め、`<generatePublisherEvidence>`起動時のパフォーマンスを向上させるために要素。</span><span class="sxs-lookup"><span data-stu-id="ed00a-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="ed00a-137">この要素を使用しても、タイムアウトと、サービスのスタートアップのキャンセルを引き起こす可能性がある遅延を避けるためとことができます。</span><span class="sxs-lookup"><span data-stu-id="ed00a-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="ed00a-138">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="ed00a-138">Configuration File</span></span>  
 <span data-ttu-id="ed00a-139">この要素は、アプリケーション構成ファイルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ed00a-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed00a-140">例</span><span class="sxs-lookup"><span data-stu-id="ed00a-140">Example</span></span>  
 <span data-ttu-id="ed00a-141">次の例を使用する方法を示しています、`<generatePublisherEvidence>`要素をアプリケーションで CA 発行者ポリシーのチェックを無効にします。</span><span class="sxs-lookup"><span data-stu-id="ed00a-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ed00a-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="ed00a-142">See Also</span></span>  
 [<span data-ttu-id="ed00a-143">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="ed00a-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="ed00a-144">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="ed00a-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
