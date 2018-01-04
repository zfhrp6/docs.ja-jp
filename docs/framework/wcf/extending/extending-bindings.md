---
title: "バインディングの拡張"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending bindings [WCF]
ms.assetid: 5e40d306-b3c1-4429-80c4-fbb1d956856c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d0be5e799137d24c2d6e53f4b6846007f3a2a79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="extending-bindings"></a><span data-ttu-id="9b4ba-102">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="9b4ba-102">Extending Bindings</span></span>
<span data-ttu-id="9b4ba-103">バインディングは、エンドポイントに接続するために必要なトランスポート、エンコード、およびプロトコルを指定します。</span><span class="sxs-lookup"><span data-stu-id="9b4ba-103">Bindings specify the transport, encoding, and protocol required to connect to an endpoint.</span></span> <span data-ttu-id="9b4ba-104">バインディングの拡張およびカスタム バインディングは、アプリケーションの各種機能をサポートするために必要なカスタム通信機能を実装します。</span><span class="sxs-lookup"><span data-stu-id="9b4ba-104">Binding extensions and custom bindings implement custom communication functionality required to support application features.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b4ba-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9b4ba-105">In This Section</span></span>  
  
|<span data-ttu-id="9b4ba-106">トピック</span><span class="sxs-lookup"><span data-stu-id="9b4ba-106">Topic</span></span>|<span data-ttu-id="9b4ba-107">説明</span><span class="sxs-lookup"><span data-stu-id="9b4ba-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="9b4ba-108">バインディングとバインド要素</span><span class="sxs-lookup"><span data-stu-id="9b4ba-108">Bindings and Binding Elements</span></span>](../../../../docs/framework/wcf/extending/bindings-and-binding-elements.md)|<span data-ttu-id="9b4ba-109">バインディングとバインド要素について説明し、その使用方法と拡張方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9b4ba-109">Describes bindings, binding elements, and how they are used and extended.</span></span>|  
|[<span data-ttu-id="9b4ba-110">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="9b4ba-110">Custom Bindings</span></span>](../../../../docs/framework/wcf/extending/custom-bindings.md)|<span data-ttu-id="9b4ba-111"><xref:System.ServiceModel.Channels.CustomBinding> クラスを使用して、システム定義およびサードパーティのバインド要素を使用するカスタム バインディングを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b4ba-111">Describes how to use the <xref:System.ServiceModel.Channels.CustomBinding> class to create custom bindings using system-defined and third-party binding elements.</span></span>|  
|[<span data-ttu-id="9b4ba-112">ユーザー定義バインディングの作成</span><span class="sxs-lookup"><span data-stu-id="9b4ba-112">Creating User-Defined Bindings</span></span>](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)|<span data-ttu-id="9b4ba-113">他のユーザーが使用できるバインディングとバインド要素を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b4ba-113">Describes how to create bindings and binding elements that can be used by others.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="9b4ba-114">参照</span><span class="sxs-lookup"><span data-stu-id="9b4ba-114">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9b4ba-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b4ba-115">Related Sections</span></span>  
 [<span data-ttu-id="9b4ba-116">BindingElement の作成</span><span class="sxs-lookup"><span data-stu-id="9b4ba-116">Creating a BindingElement</span></span>](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md)  
  
 [<span data-ttu-id="9b4ba-117">構成とメタデータのサポート</span><span class="sxs-lookup"><span data-stu-id="9b4ba-117">Configuration and Metadata Support</span></span>](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)
