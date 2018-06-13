---
title: '&lt;GCCpuGroup&gt;要素'
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4461667bdb47d410c857b4ac2c9dd268438a02f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744019"
---
# <a name="ltgccpugroupgt-element"></a><span data-ttu-id="001c2-102">&lt;GCCpuGroup&gt;要素</span><span class="sxs-lookup"><span data-stu-id="001c2-102">&lt;GCCpuGroup&gt; Element</span></span>
<span data-ttu-id="001c2-103">ガベージ コレクションが複数の CPU グループをサポートするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="001c2-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>  
  
 <span data-ttu-id="001c2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="001c2-104">\<configuration></span></span>  
<span data-ttu-id="001c2-105">\<ランタイム ></span><span class="sxs-lookup"><span data-stu-id="001c2-105">\<runtime></span></span>  
<span data-ttu-id="001c2-106">\<GCCpuGroup></span><span class="sxs-lookup"><span data-stu-id="001c2-106">\<GCCpuGroup></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="001c2-107">構文</span><span class="sxs-lookup"><span data-stu-id="001c2-107">Syntax</span></span>  
  
```xml  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="001c2-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="001c2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="001c2-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="001c2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="001c2-110">属性</span><span class="sxs-lookup"><span data-stu-id="001c2-110">Attributes</span></span>  
  
|<span data-ttu-id="001c2-111">属性</span><span class="sxs-lookup"><span data-stu-id="001c2-111">Attribute</span></span>|<span data-ttu-id="001c2-112">説明</span><span class="sxs-lookup"><span data-stu-id="001c2-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="001c2-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="001c2-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="001c2-114">ガベージ コレクションが複数の CPU グループをサポートするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="001c2-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="001c2-115">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="001c2-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="001c2-116">値</span><span class="sxs-lookup"><span data-stu-id="001c2-116">Value</span></span>|<span data-ttu-id="001c2-117">説明</span><span class="sxs-lookup"><span data-stu-id="001c2-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="001c2-118">ガベージ コレクションは複数の CPU グループをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="001c2-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="001c2-119">既定値です。</span><span class="sxs-lookup"><span data-stu-id="001c2-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="001c2-120">ガベージ コレクションは、サーバーのガベージ コレクションが有効な場合に複数の CPU グループをサポートします。</span><span class="sxs-lookup"><span data-stu-id="001c2-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="001c2-121">子要素</span><span class="sxs-lookup"><span data-stu-id="001c2-121">Child Elements</span></span>  
 <span data-ttu-id="001c2-122">なし。</span><span class="sxs-lookup"><span data-stu-id="001c2-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="001c2-123">親要素</span><span class="sxs-lookup"><span data-stu-id="001c2-123">Parent Elements</span></span>  
  
|<span data-ttu-id="001c2-124">要素</span><span class="sxs-lookup"><span data-stu-id="001c2-124">Element</span></span>|<span data-ttu-id="001c2-125">説明</span><span class="sxs-lookup"><span data-stu-id="001c2-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="001c2-126">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="001c2-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="001c2-127">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="001c2-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="001c2-128">コメント</span><span class="sxs-lookup"><span data-stu-id="001c2-128">Remarks</span></span>  
 <span data-ttu-id="001c2-129">コンピューターに複数の CPU グループとサーバーのガベージ コレクションが有効になっている (を参照してください、 [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)要素)、この要素を有効にするすべての CPU グループ全体でガベージ コレクションを拡張し、すべてのコアにアカウントを作成すると、ヒープを分散します。</span><span class="sxs-lookup"><span data-stu-id="001c2-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="001c2-130">この要素は、ガベージ コレクション スレッドにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="001c2-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="001c2-131">すべての CPU グループにユーザー スレッドを分散するランタイムを有効にする必要がありますも有効にする、 [< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)要素。</span><span class="sxs-lookup"><span data-stu-id="001c2-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="001c2-132">例</span><span class="sxs-lookup"><span data-stu-id="001c2-132">Example</span></span>  
 <span data-ttu-id="001c2-133">次の例は、複数の CPU グループのガベージ コレクションを有効にする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="001c2-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="001c2-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="001c2-134">See Also</span></span>  
 [<span data-ttu-id="001c2-135">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="001c2-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="001c2-136">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="001c2-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="001c2-137">方法: 同時実行ガベージ コレクションを無効にします。</span><span class="sxs-lookup"><span data-stu-id="001c2-137">How to: Disable Concurrent Garbage Collection</span></span>](http://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)  
 [<span data-ttu-id="001c2-138">ワークステーションとサーバーのガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="001c2-138">Workstation and server garbage collection</span></span>](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
