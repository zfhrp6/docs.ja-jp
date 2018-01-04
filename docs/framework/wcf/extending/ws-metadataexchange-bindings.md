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
ms.workload: dotnet
ms.openlocfilehash: 8d305f3bf34b3b14da566fa792552e24e695ef33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="76935-102">WS-MetadataExchange のバインディング</span><span class="sxs-lookup"><span data-stu-id="76935-102">WS-MetadataExchange Bindings</span></span>
<span data-ttu-id="76935-103">ここでは、既定のメタデータ交換バインディングを各種のトランスポート用に構築する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="76935-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="76935-104">既定のバインディング</span><span class="sxs-lookup"><span data-stu-id="76935-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="76935-105">既定のバインディング名</span><span class="sxs-lookup"><span data-stu-id="76935-105">Default Binding Name</span></span>|<span data-ttu-id="76935-106">バインディングを構築する方法</span><span class="sxs-lookup"><span data-stu-id="76935-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="76935-107">MexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="76935-107">MexHttpBinding</span></span>|<span data-ttu-id="76935-108">トランスポート レベルのセキュリティが無効な <xref:System.ServiceModel.WSHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="76935-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="76935-109">MexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="76935-109">MexHttpsBinding</span></span>|<span data-ttu-id="76935-110">トランスポート レベルのセキュリティをサポートする <xref:System.ServiceModel.WSHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="76935-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="76935-111">MexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="76935-111">MexNamedPipeBinding</span></span>|<span data-ttu-id="76935-112"><xref:System.ServiceModel.Channels.CustomBinding> で既定値を使用する <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="76935-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="76935-113">MexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="76935-113">MexTcpBinding</span></span>|<span data-ttu-id="76935-114"><xref:System.ServiceModel.Channels.CustomBinding> で既定値を使用する <xref:System.ServiceModel.Channels.TcpTransportBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="76935-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
