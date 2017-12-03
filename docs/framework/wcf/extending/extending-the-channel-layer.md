---
title: "チャネル レイヤーの拡張"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending channels [WCF]
ms.assetid: 4238db74-2fb6-4dc8-a326-f58527230810
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f9d14183092b70f0bbe1ce8894f10369aa46c31
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="extending-the-channel-layer"></a><span data-ttu-id="47151-102">チャネル レイヤーの拡張</span><span class="sxs-lookup"><span data-stu-id="47151-102">Extending the Channel Layer</span></span>
<span data-ttu-id="47151-103">チャネル レイヤーはクライアントとサービス間のメッセージの交換を担います。</span><span class="sxs-lookup"><span data-stu-id="47151-103">The channel layer is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="47151-104">チャネル拡張では、新しいプロトコル機能 (セキュリティなど)、またはトランスポート機能 (SOAP メッセージを送信する新しいネットワーク トランスポートの実装など) を実装できます。</span><span class="sxs-lookup"><span data-stu-id="47151-104">Channel extensions can implement new protocol functionality, such as security, or transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="47151-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="47151-105">In This Section</span></span>  
 [<span data-ttu-id="47151-106">チャネル モデルの概要</span><span class="sxs-lookup"><span data-stu-id="47151-106">Channel Model Overview</span></span>](../../../../docs/framework/wcf/extending/channel-model-overview.md)  
 <span data-ttu-id="47151-107">チャネルとその機能、サービス アプリケーションおよびクライアント アプリケーションとの連携について概要を示します。</span><span class="sxs-lookup"><span data-stu-id="47151-107">Provides a high-level overview of what channels are, the features that they provide and how they work both in a service and a client application.</span></span>  
  
 [<span data-ttu-id="47151-108">チャネルの開発</span><span class="sxs-lookup"><span data-stu-id="47151-108">Developing Channels</span></span>](../../../../docs/framework/wcf/extending/developing-channels.md)  
 <span data-ttu-id="47151-109">各種のチャネル インフラストラクチャが果たす役割、ステート エンジンとステート ライフサイクルのしくみ、例外とエラーの処理方法、メタデータ サポートの実装方法、チャネルとメッセージ エンコーダーの連携について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="47151-109">Describes in depth the roles that the various channel infrastructure types play, how the state engine and state lifecycle works, how to handle exceptions and faults, how to implement metadata support, and how channels work with message encoders.</span></span>  
  
 [<span data-ttu-id="47151-110">カスタム エンコーダー</span><span class="sxs-lookup"><span data-stu-id="47151-110">Custom Encoders</span></span>](../../../../docs/framework/wcf/extending/custom-encoders.md)  
 <span data-ttu-id="47151-111">メッセージ エンコーダーがチャネルで果たす役割、およびメッセージ エンコーダーの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="47151-111">Describes the role that message encoders play in channels and how to build one.</span></span>  
  
 [<span data-ttu-id="47151-112">カスタム ストリーム アップグレード</span><span class="sxs-lookup"><span data-stu-id="47151-112">Custom Stream Upgrades</span></span>](../../../../docs/framework/wcf/extending/custom-stream-upgrades.md)  
 <span data-ttu-id="47151-113">ストリーム指向のトランスポートによって提供されるストリームのアップグレード プロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="47151-113">Describes the process of upgrading the streams provided by stream-oriented transports.</span></span>
