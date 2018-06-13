---
title: '&lt;バインド&gt;'
ms.date: 03/30/2017
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: 76ebd7c317bf5f0aa1ec02d4014235df232314f0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747822"
---
# <a name="ltbindingsgt"></a><span data-ttu-id="13462-102">&lt;バインド&gt;</span><span class="sxs-lookup"><span data-stu-id="13462-102">&lt;bindings&gt;</span></span>
<span data-ttu-id="13462-103">このセクションには、標準バインディングおよびカスタム バインドのコレクションが保持されます。</span><span class="sxs-lookup"><span data-stu-id="13462-103">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="13462-104">各エントリは、その一意の `binding` 属性で識別できる `name` 要素です。</span><span class="sxs-lookup"><span data-stu-id="13462-104">Each entry is a `binding` element that can be identified by its unique `name`.</span></span> <span data-ttu-id="13462-105">サービスは、`name` を使用してバインディングをリンクすることにより、バインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="13462-105">Services use bindings by linking them using the `name`.</span></span> <span data-ttu-id="13462-106">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="13462-106">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="13462-107">既定の構成と無名のバインディングおよび動作の詳細については、次を参照してください。[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="13462-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="system-provided-binding"></a><span data-ttu-id="13462-108">システム指定のバインディング</span><span class="sxs-lookup"><span data-stu-id="13462-108">System-Provided Binding</span></span>  
 <span data-ttu-id="13462-109">システム指定のバインディングは、WCF メッセージ スタックの複雑さを隠蔽します。</span><span class="sxs-lookup"><span data-stu-id="13462-109">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="13462-110">システム指定のバインディングを使用しているアプリケーションは、スタックを完全に制御する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="13462-110">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="13462-111">システム指定の各バインディングに公開される属性は、バインディングが処理する使用シナリオに最適な属性です。</span><span class="sxs-lookup"><span data-stu-id="13462-111">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="13462-112">システム指定の各バインディングの構成セクションは、バインディングの構成に使用される複数の構成を定義できます。</span><span class="sxs-lookup"><span data-stu-id="13462-112">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="13462-113">各構成は、一意の名前によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="13462-113">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="13462-114">要素または属性をシステム指定のバインディングに追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="13462-114">It is not possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="13462-115">追加するには、このトピックの「カスタム バインディング」セクションで説明するように、カスタム バインディングを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="13462-115">To do so, you should implement a custom binding as described in the "Custom Binding" section of this topic.</span></span> <span data-ttu-id="13462-116">システム指定のバインディングを完全に再現し、ユーザー アプリケーションで制御するいくつかの設定を追加するカスタム バインドを定義できます。</span><span class="sxs-lookup"><span data-stu-id="13462-116">It is possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
 <span data-ttu-id="13462-117">システム指定のバインディングの一覧は、次を参照してください。[システム指定のバインディング](../../../../../docs/framework/wcf/system-provided-bindings.md)です。</span><span class="sxs-lookup"><span data-stu-id="13462-117">For a list of system-provided bindings, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
## <a name="custom-binding"></a><span data-ttu-id="13462-118">カスタム バインド</span><span class="sxs-lookup"><span data-stu-id="13462-118">Custom Binding</span></span>  
 <span data-ttu-id="13462-119">カスタム バインディングを使用すると、WCF メッセージ スタックのフル コントロールが可能になります。</span><span class="sxs-lookup"><span data-stu-id="13462-119">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="13462-120">個別のバインディングは、メッセージ スタックを、スタック要素の構成要素をスタックに出現する順序で指定することにより定義します。</span><span class="sxs-lookup"><span data-stu-id="13462-120">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="13462-121">各要素は、スタック内の 1 つの要素を定義および構成します。</span><span class="sxs-lookup"><span data-stu-id="13462-121">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="13462-122">各カスタム バインディング内の `transport` 要素は 1 つだけにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="13462-122">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="13462-123">この要素がない場合、メッセージ スタックは不完全です。</span><span class="sxs-lookup"><span data-stu-id="13462-123">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="13462-124">要素がスタックに出現する順序は重要です。それは、その順序で操作がメッセージに適用されるためです。</span><span class="sxs-lookup"><span data-stu-id="13462-124">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="13462-125">スタック要素で必要な順序を次に示します。</span><span class="sxs-lookup"><span data-stu-id="13462-125">The required order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="13462-126">トランザクション (省略可能)</span><span class="sxs-lookup"><span data-stu-id="13462-126">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="13462-127">リライアブル メッセージ機能 (省略可能)</span><span class="sxs-lookup"><span data-stu-id="13462-127">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="13462-128">セキュリティ (省略可能)</span><span class="sxs-lookup"><span data-stu-id="13462-128">Security (optional)</span></span>  
  
4.  <span data-ttu-id="13462-129">エンコーダー</span><span class="sxs-lookup"><span data-stu-id="13462-129">Encoder</span></span>  
  
5.  <span data-ttu-id="13462-130">Transport</span><span class="sxs-lookup"><span data-stu-id="13462-130">Transport</span></span>  
  
 <span data-ttu-id="13462-131">カスタム バインディングは、`name` 属性によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="13462-131">Custom bindings are identified by their `name` attribute.</span></span> <span data-ttu-id="13462-132">カスタム バインドの詳細については、次を参照してください。[カスタム バインド](../../../../../docs/framework/wcf/extending/custom-bindings.md)です。</span><span class="sxs-lookup"><span data-stu-id="13462-132">For more information on custom bindings, see [Custom Bindings](../../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13462-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="13462-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [<span data-ttu-id="13462-134">バインディング</span><span class="sxs-lookup"><span data-stu-id="13462-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="13462-135">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="13462-135">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="13462-136">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="13462-136">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="13462-137">\<binding></span><span class="sxs-lookup"><span data-stu-id="13462-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
