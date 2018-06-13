---
title: '&lt;バインド&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
ms.openlocfilehash: d72b3a34e0696df944b2338c89f167c8bfa06400
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392253"
---
# <a name="ltbindinggt"></a><span data-ttu-id="a1c86-102">&lt;バインド&gt;</span><span class="sxs-lookup"><span data-stu-id="a1c86-102">&lt;binding&gt;</span></span>
<span data-ttu-id="a1c86-103">`binding` 要素を使用して、Windows Communication Foundation (WCF) によって提供される異なる型の定義済みバインディングを構成できます。</span><span class="sxs-lookup"><span data-stu-id="a1c86-103">You can use the `binding` element to configure different types of predefined bindings provided by Windows Communication Foundation (WCF).</span></span>  
  
## <a name="system-provided-binding"></a><span data-ttu-id="a1c86-104">システム指定のバインディング</span><span class="sxs-lookup"><span data-stu-id="a1c86-104">System-Provided Binding</span></span>  
 <span data-ttu-id="a1c86-105">システム指定のバインディングは、WCF メッセージ スタックの複雑さを隠蔽します。</span><span class="sxs-lookup"><span data-stu-id="a1c86-105">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="a1c86-106">システム指定のバインディングを使用しているアプリケーションは、スタックを完全に制御する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a1c86-106">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="a1c86-107">システム指定の各バインディングに公開される属性は、バインディングが処理する使用シナリオに最適な属性です。</span><span class="sxs-lookup"><span data-stu-id="a1c86-107">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="a1c86-108">システム指定の各バインディングの構成セクションは、バインディングの構成に使用される複数の構成を定義できます。</span><span class="sxs-lookup"><span data-stu-id="a1c86-108">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="a1c86-109">各構成は、一意の名前によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="a1c86-109">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="a1c86-110">要素または属性をシステム指定のバインディングに追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="a1c86-110">It is not possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="a1c86-111">追加するには、このトピックの「カスタム バインディング」セクションで説明するように、カスタム バインディングを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1c86-111">To do so, you should implement a custom binding as described in the "Custom Binding" section of this topic.</span></span> <span data-ttu-id="a1c86-112">システム指定のバインディングを完全に再現し、ユーザー アプリケーションで制御するいくつかの設定を追加するカスタム バインディングを定義できます。</span><span class="sxs-lookup"><span data-stu-id="a1c86-112">It is possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
## <a name="custom-binding"></a><span data-ttu-id="a1c86-113">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="a1c86-113">Custom Binding</span></span>  
 <span data-ttu-id="a1c86-114">カスタム バインディングを使用すると、WCF メッセージ スタックのフル コントロールが可能になります。</span><span class="sxs-lookup"><span data-stu-id="a1c86-114">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="a1c86-115">個別のバインディングは、メッセージ スタックを、スタック要素の構成要素をスタックに出現する順序で指定することにより定義します。</span><span class="sxs-lookup"><span data-stu-id="a1c86-115">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="a1c86-116">各要素は、スタック内の 1 つの要素を定義および構成します。</span><span class="sxs-lookup"><span data-stu-id="a1c86-116">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="a1c86-117">各カスタム バインディング内の `transport` 要素は 1 つだけにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1c86-117">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="a1c86-118">この要素がない場合、メッセージ スタックは不完全です。</span><span class="sxs-lookup"><span data-stu-id="a1c86-118">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="a1c86-119">要素がスタックに出現する順序は重要です。それは、その順序で操作がメッセージに適用されるためです。</span><span class="sxs-lookup"><span data-stu-id="a1c86-119">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="a1c86-120">スタック要素で推奨される順序を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a1c86-120">The recommended order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="a1c86-121">トランザクション (省略可能)</span><span class="sxs-lookup"><span data-stu-id="a1c86-121">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="a1c86-122">リライアブル メッセージ機能 (省略可能)</span><span class="sxs-lookup"><span data-stu-id="a1c86-122">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="a1c86-123">セキュリティ (省略可能)</span><span class="sxs-lookup"><span data-stu-id="a1c86-123">Security (optional)</span></span>  
  
4.  <span data-ttu-id="a1c86-124">エンコーダー</span><span class="sxs-lookup"><span data-stu-id="a1c86-124">Encoder</span></span>  
  
5.  <span data-ttu-id="a1c86-125">Transport</span><span class="sxs-lookup"><span data-stu-id="a1c86-125">Transport</span></span>  
  
 <span data-ttu-id="a1c86-126">カスタム バインディングは、`name` 属性によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="a1c86-126">Custom bindings are identified by their `name` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1c86-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1c86-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [<span data-ttu-id="a1c86-128">バインディング</span><span class="sxs-lookup"><span data-stu-id="a1c86-128">Bindings</span></span>](../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a1c86-129">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="a1c86-129">Custom Bindings</span></span>](../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="a1c86-130">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a1c86-130">\<customBinding></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
