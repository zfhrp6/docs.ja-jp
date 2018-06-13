---
title: WS-MetadataExchange のバインディング
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 384e5bb05ba4263f245f6901b84e2388ea19bd73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488625"
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
