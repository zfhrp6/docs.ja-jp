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
ms.openlocfilehash: 692e51fc6276fbee0c1764c0040a251fe32b2c9f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="extending-bindings"></a><span data-ttu-id="a4dbe-102">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="a4dbe-102">Extending Bindings</span></span>
<span data-ttu-id="a4dbe-103">バインディングは、エンドポイントに接続するために必要なトランスポート、エンコード、およびプロトコルを指定します。</span><span class="sxs-lookup"><span data-stu-id="a4dbe-103">Bindings specify the transport, encoding, and protocol required to connect to an endpoint.</span></span> <span data-ttu-id="a4dbe-104">バインディングの拡張およびカスタム バインディングは、アプリケーションの各種機能をサポートするために必要なカスタム通信機能を実装します。</span><span class="sxs-lookup"><span data-stu-id="a4dbe-104">Binding extensions and custom bindings implement custom communication functionality required to support application features.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a4dbe-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a4dbe-105">In This Section</span></span>  
  
|<span data-ttu-id="a4dbe-106">トピック</span><span class="sxs-lookup"><span data-stu-id="a4dbe-106">Topic</span></span>|<span data-ttu-id="a4dbe-107">説明</span><span class="sxs-lookup"><span data-stu-id="a4dbe-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a4dbe-108">バインディングとバインド要素</span><span class="sxs-lookup"><span data-stu-id="a4dbe-108">Bindings and Binding Elements</span></span>](../../../../docs/framework/wcf/extending/bindings-and-binding-elements.md)|<span data-ttu-id="a4dbe-109">バインディングとバインド要素について説明し、その使用方法と拡張方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a4dbe-109">Describes bindings, binding elements, and how they are used and extended.</span></span>|  
|[<span data-ttu-id="a4dbe-110">カスタム バインド</span><span class="sxs-lookup"><span data-stu-id="a4dbe-110">Custom Bindings</span></span>](../../../../docs/framework/wcf/extending/custom-bindings.md)|<span data-ttu-id="a4dbe-111"><xref:System.ServiceModel.Channels.CustomBinding> クラスを使用して、システム定義およびサードパーティのバインド要素を使用するカスタム バインディングを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a4dbe-111">Describes how to use the <xref:System.ServiceModel.Channels.CustomBinding> class to create custom bindings using system-defined and third-party binding elements.</span></span>|  
|[<span data-ttu-id="a4dbe-112">ユーザー定義のバインディングを作成します。</span><span class="sxs-lookup"><span data-stu-id="a4dbe-112">Creating User-Defined Bindings</span></span>](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)|<span data-ttu-id="a4dbe-113">他のユーザーが使用できるバインディングとバインド要素を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a4dbe-113">Describes how to create bindings and binding elements that can be used by others.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="a4dbe-114">参照</span><span class="sxs-lookup"><span data-stu-id="a4dbe-114">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a4dbe-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a4dbe-115">Related Sections</span></span>  
 [<span data-ttu-id="a4dbe-116">BindingElement の作成</span><span class="sxs-lookup"><span data-stu-id="a4dbe-116">Creating a BindingElement</span></span>](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md)  
  
 [<span data-ttu-id="a4dbe-117">構成とメタデータのサポート</span><span class="sxs-lookup"><span data-stu-id="a4dbe-117">Configuration and Metadata Support</span></span>](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)
