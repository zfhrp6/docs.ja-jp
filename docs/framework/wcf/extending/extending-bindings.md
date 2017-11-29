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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7f51aea5451f4f74c6658e16c4aced6e76ecbb3b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="extending-bindings"></a><span data-ttu-id="ff78d-102">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="ff78d-102">Extending Bindings</span></span>
<span data-ttu-id="ff78d-103">バインディングは、エンドポイントに接続するために必要なトランスポート、エンコード、およびプロトコルを指定します。</span><span class="sxs-lookup"><span data-stu-id="ff78d-103">Bindings specify the transport, encoding, and protocol required to connect to an endpoint.</span></span> <span data-ttu-id="ff78d-104">バインディングの拡張およびカスタム バインディングは、アプリケーションの各種機能をサポートするために必要なカスタム通信機能を実装します。</span><span class="sxs-lookup"><span data-stu-id="ff78d-104">Binding extensions and custom bindings implement custom communication functionality required to support application features.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ff78d-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ff78d-105">In This Section</span></span>  
  
|<span data-ttu-id="ff78d-106">トピック</span><span class="sxs-lookup"><span data-stu-id="ff78d-106">Topic</span></span>|<span data-ttu-id="ff78d-107">説明</span><span class="sxs-lookup"><span data-stu-id="ff78d-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ff78d-108">バインディングとバインド要素</span><span class="sxs-lookup"><span data-stu-id="ff78d-108">Bindings and Binding Elements</span></span>](../../../../docs/framework/wcf/extending/bindings-and-binding-elements.md)|<span data-ttu-id="ff78d-109">バインディングとバインド要素について説明し、その使用方法と拡張方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ff78d-109">Describes bindings, binding elements, and how they are used and extended.</span></span>|  
|[<span data-ttu-id="ff78d-110">カスタム バインド</span><span class="sxs-lookup"><span data-stu-id="ff78d-110">Custom Bindings</span></span>](../../../../docs/framework/wcf/extending/custom-bindings.md)|<span data-ttu-id="ff78d-111"><xref:System.ServiceModel.Channels.CustomBinding> クラスを使用して、システム定義およびサードパーティのバインド要素を使用するカスタム バインディングを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ff78d-111">Describes how to use the <xref:System.ServiceModel.Channels.CustomBinding> class to create custom bindings using system-defined and third-party binding elements.</span></span>|  
|[<span data-ttu-id="ff78d-112">ユーザー定義のバインディングを作成します。</span><span class="sxs-lookup"><span data-stu-id="ff78d-112">Creating User-Defined Bindings</span></span>](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)|<span data-ttu-id="ff78d-113">他のユーザーが使用できるバインディングとバインド要素を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ff78d-113">Describes how to create bindings and binding elements that can be used by others.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="ff78d-114">参照</span><span class="sxs-lookup"><span data-stu-id="ff78d-114">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ff78d-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff78d-115">Related Sections</span></span>  
 [<span data-ttu-id="ff78d-116">BindingElement の作成</span><span class="sxs-lookup"><span data-stu-id="ff78d-116">Creating a BindingElement</span></span>](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md)  
  
 [<span data-ttu-id="ff78d-117">構成とメタデータのサポート</span><span class="sxs-lookup"><span data-stu-id="ff78d-117">Configuration and Metadata Support</span></span>](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)
