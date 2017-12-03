---
title: "WS-MetadataExchange のバインディング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a7267fa8e71a7bbe202bce9897ea09079307be50
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="6e032-102">WS-MetadataExchange のバインディング</span><span class="sxs-lookup"><span data-stu-id="6e032-102">WS-MetadataExchange Bindings</span></span>
<span data-ttu-id="6e032-103">ここでは、既定のメタデータ交換バインディングを各種のトランスポート用に構築する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6e032-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="6e032-104">既定のバインディング</span><span class="sxs-lookup"><span data-stu-id="6e032-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="6e032-105">既定のバインディング名</span><span class="sxs-lookup"><span data-stu-id="6e032-105">Default Binding Name</span></span>|<span data-ttu-id="6e032-106">バインディングを構築する方法</span><span class="sxs-lookup"><span data-stu-id="6e032-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="6e032-107">MexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="6e032-107">MexHttpBinding</span></span>|<span data-ttu-id="6e032-108">トランスポート レベルのセキュリティが無効な <xref:System.ServiceModel.WSHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="6e032-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="6e032-109">MexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="6e032-109">MexHttpsBinding</span></span>|<span data-ttu-id="6e032-110">トランスポート レベルのセキュリティをサポートする <xref:System.ServiceModel.WSHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="6e032-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="6e032-111">MexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="6e032-111">MexNamedPipeBinding</span></span>|<span data-ttu-id="6e032-112"><xref:System.ServiceModel.Channels.CustomBinding> で既定値を使用する <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="6e032-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="6e032-113">MexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="6e032-113">MexTcpBinding</span></span>|<span data-ttu-id="6e032-114"><xref:System.ServiceModel.Channels.CustomBinding> で既定値を使用する <xref:System.ServiceModel.Channels.TcpTransportBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="6e032-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
