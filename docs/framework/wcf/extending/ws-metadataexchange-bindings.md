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
# <a name="ws-metadataexchange-bindings"></a>WS-MetadataExchange のバインディング
ここでは、既定のメタデータ交換バインディングを各種のトランスポート用に構築する方法を説明します。  
  
## <a name="the-default-bindings"></a>既定のバインディング  
  
|既定のバインディング名|バインディングを構築する方法|  
|--------------------------|------------------------------------|  
|MexHttpBinding|トランスポート レベルのセキュリティが無効な <xref:System.ServiceModel.WSHttpBinding>。|  
|MexHttpsBinding|トランスポート レベルのセキュリティをサポートする <xref:System.ServiceModel.WSHttpBinding>。|  
|MexNamedPipeBinding|<xref:System.ServiceModel.Channels.CustomBinding> で既定値を使用する <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>。|  
|MexTcpBinding|<xref:System.ServiceModel.Channels.CustomBinding> で既定値を使用する <xref:System.ServiceModel.Channels.TcpTransportBindingElement>。|
