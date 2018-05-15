---
title: WS-MetadataExchange のバインディング
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 384e5bb05ba4263f245f6901b84e2388ea19bd73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="b1c3a-102">WS-MetadataExchange のバインディング</span><span class="sxs-lookup"><span data-stu-id="b1c3a-102">WS-MetadataExchange Bindings</span></span>
<span data-ttu-id="b1c3a-103">ここでは、既定のメタデータ交換バインディングを各種のトランスポート用に構築する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="b1c3a-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="b1c3a-104">既定のバインディング</span><span class="sxs-lookup"><span data-stu-id="b1c3a-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="b1c3a-105">既定のバインディング名</span><span class="sxs-lookup"><span data-stu-id="b1c3a-105">Default Binding Name</span></span>|<span data-ttu-id="b1c3a-106">バインディングを構築する方法</span><span class="sxs-lookup"><span data-stu-id="b1c3a-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="b1c3a-107">MexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="b1c3a-107">MexHttpBinding</span></span>|<span data-ttu-id="b1c3a-108">トランスポート レベルのセキュリティが無効な <xref:System.ServiceModel.WSHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="b1c3a-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="b1c3a-109">MexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="b1c3a-109">MexHttpsBinding</span></span>|<span data-ttu-id="b1c3a-110">トランスポート レベルのセキュリティをサポートする <xref:System.ServiceModel.WSHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="b1c3a-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="b1c3a-111">MexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="b1c3a-111">MexNamedPipeBinding</span></span>|<span data-ttu-id="b1c3a-112"><xref:System.ServiceModel.Channels.CustomBinding> で既定値を使用する <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="b1c3a-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="b1c3a-113">MexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="b1c3a-113">MexTcpBinding</span></span>|<span data-ttu-id="b1c3a-114"><xref:System.ServiceModel.Channels.CustomBinding> で既定値を使用する <xref:System.ServiceModel.Channels.TcpTransportBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="b1c3a-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
