---
title: "WS-MetadataExchange のバインディング | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# WS-MetadataExchange のバインディング
ここでは、既定のメタデータ交換バインディングを各種のトランスポート用に構築する方法を説明します。  
  
## 既定のバインディング  
  
|既定のバインディング名|バインディングを構築する方法|  
|-----------------|--------------------|  
|MexHttpBinding|トランスポート レベルのセキュリティが無効な <xref:System.ServiceModel.WSHttpBinding>。|  
|MexHttpsBinding|トランスポート レベルのセキュリティをサポートする <xref:System.ServiceModel.WSHttpBinding>。|  
|MexNamedPipeBinding|<xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> で既定値を使用する <xref:System.ServiceModel.Channels.CustomBinding>。|  
|MexTcpBinding|<xref:System.ServiceModel.Channels.TcpTransportBindingElement> で既定値を使用する <xref:System.ServiceModel.Channels.CustomBinding>。|