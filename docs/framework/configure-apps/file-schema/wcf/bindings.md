---
title: "&lt;バインド&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ed672ee918ad969feb8be6d20c9206e6b5d12278
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltbindingsgt"></a><span data-ttu-id="a9da8-102">&lt;バインド&gt;</span><span class="sxs-lookup"><span data-stu-id="a9da8-102">&lt;bindings&gt;</span></span>
<span data-ttu-id="a9da8-103">このセクションには、標準バインディングおよびカスタム バインディングのコレクションが保持されます。</span><span class="sxs-lookup"><span data-stu-id="a9da8-103">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="a9da8-104">各エントリは、その一意の `binding` 属性で識別できる `name` 要素です。</span><span class="sxs-lookup"><span data-stu-id="a9da8-104">Each entry is a `binding` element that can be identified by its unique `name`.</span></span> <span data-ttu-id="a9da8-105">サービスは、`name` を使用してバインディングをリンクすることにより、バインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="a9da8-105">Services use bindings by linking them using the `name`.</span></span> <span data-ttu-id="a9da8-106">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a9da8-106">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="a9da8-107">既定の構成と無名のバインディングおよび動作の詳細については、次を参照してください。[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="a9da8-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="system-provided-binding"></a><span data-ttu-id="a9da8-108">システム指定のバインディング</span><span class="sxs-lookup"><span data-stu-id="a9da8-108">System-Provided Binding</span></span>  
 <span data-ttu-id="a9da8-109">システム指定のバインディングは、WCF メッセージ スタックの複雑さを隠蔽します。</span><span class="sxs-lookup"><span data-stu-id="a9da8-109">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="a9da8-110">システム指定のバインディングを使用しているアプリケーションは、スタックを完全に制御する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a9da8-110">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="a9da8-111">システム指定の各バインディングに公開される属性は、バインディングが処理する使用シナリオに最適な属性です。</span><span class="sxs-lookup"><span data-stu-id="a9da8-111">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="a9da8-112">システム指定の各バインディングの構成セクションは、バインディングの構成に使用される複数の構成を定義できます。</span><span class="sxs-lookup"><span data-stu-id="a9da8-112">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="a9da8-113">各構成は、一意の名前によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="a9da8-113">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="a9da8-114">要素または属性をシステム指定のバインディングに追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="a9da8-114">It is not possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="a9da8-115">追加するには、このトピックの「カスタム バインディング」セクションで説明するように、カスタム バインディングを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9da8-115">To do so, you should implement a custom binding as described in the "Custom Binding" section of this topic.</span></span> <span data-ttu-id="a9da8-116">システム指定のバインディングを完全に再現し、ユーザー アプリケーションで制御するいくつかの設定を追加するカスタム バインドを定義できます。</span><span class="sxs-lookup"><span data-stu-id="a9da8-116">It is possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
 <span data-ttu-id="a9da8-117">システム指定のバインディングの一覧は、次を参照してください。[システム指定のバインディング](../../../../../docs/framework/wcf/system-provided-bindings.md)です。</span><span class="sxs-lookup"><span data-stu-id="a9da8-117">For a list of system-provided bindings, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
## <a name="custom-binding"></a><span data-ttu-id="a9da8-118">カスタム バインド</span><span class="sxs-lookup"><span data-stu-id="a9da8-118">Custom Binding</span></span>  
 <span data-ttu-id="a9da8-119">カスタム バインディングを使用すると、WCF メッセージ スタックのフル コントロールが可能になります。</span><span class="sxs-lookup"><span data-stu-id="a9da8-119">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="a9da8-120">個別のバインディングは、メッセージ スタックを、スタック要素の構成要素をスタックに出現する順序で指定することにより定義します。</span><span class="sxs-lookup"><span data-stu-id="a9da8-120">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="a9da8-121">各要素は、スタック内の 1 つの要素を定義および構成します。</span><span class="sxs-lookup"><span data-stu-id="a9da8-121">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="a9da8-122">各カスタム バインディング内の `transport` 要素は 1 つだけにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9da8-122">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="a9da8-123">この要素がない場合、メッセージ スタックは不完全です。</span><span class="sxs-lookup"><span data-stu-id="a9da8-123">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="a9da8-124">要素がスタックに出現する順序は重要です。それは、その順序で操作がメッセージに適用されるためです。</span><span class="sxs-lookup"><span data-stu-id="a9da8-124">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="a9da8-125">スタック要素で必要な順序を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a9da8-125">The required order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="a9da8-126">トランザクション (省略可能)</span><span class="sxs-lookup"><span data-stu-id="a9da8-126">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="a9da8-127">リライアブル メッセージ機能 (省略可能)</span><span class="sxs-lookup"><span data-stu-id="a9da8-127">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="a9da8-128">セキュリティ (省略可能)</span><span class="sxs-lookup"><span data-stu-id="a9da8-128">Security (optional)</span></span>  
  
4.  <span data-ttu-id="a9da8-129">エンコーダー</span><span class="sxs-lookup"><span data-stu-id="a9da8-129">Encoder</span></span>  
  
5.  <span data-ttu-id="a9da8-130">Transport</span><span class="sxs-lookup"><span data-stu-id="a9da8-130">Transport</span></span>  
  
 <span data-ttu-id="a9da8-131">カスタム バインディングは、`name` 属性によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="a9da8-131">Custom bindings are identified by their `name` attribute.</span></span> <span data-ttu-id="a9da8-132">カスタム バインドの詳細については、次を参照してください。[カスタム バインド](../../../../../docs/framework/wcf/extending/custom-bindings.md)です。</span><span class="sxs-lookup"><span data-stu-id="a9da8-132">For more information on custom bindings, see [Custom Bindings](../../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9da8-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="a9da8-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [<span data-ttu-id="a9da8-134">バインディング</span><span class="sxs-lookup"><span data-stu-id="a9da8-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a9da8-135">カスタム バインド</span><span class="sxs-lookup"><span data-stu-id="a9da8-135">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="a9da8-136">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a9da8-136">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="a9da8-137">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="a9da8-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
