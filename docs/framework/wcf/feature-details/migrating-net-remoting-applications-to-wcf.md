---
title: ".NET リモート処理アプリケーションの WCF への移行 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ", .NET リモート処理 [WCF]"
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# .NET リモート処理アプリケーションの WCF への移行
**このトピックの対象は、既存のアプリケーションとの下位互換性のために残されているレガシ テクノロジに特定されています。新規の開発には、このトピックを適用しないでください。現在、分散アプリケーションは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用して開発する必要があります。**  
  
 既存の .NET リモート処理アプリケーションから [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を利用するには、統合と移行という 2 つの方法があります。統合によって、.NET Remoting 2.0 と [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を並行で実行できるようになり、既存の.NET Remoting 2.0 のコードに手を加えることなく、両方のテクノロジで同時に同じビジネス オブジェクトを公開できます。統合では、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 以降が実行されている必要があります。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の機能を利用し、Remoting 2.0 システムとのネットワーク上での互換性が必要ではない場合は、サービス全体を [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に移行できます。.NET Remoting 2.0 から [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] への移行には、リモート オブジェクトのインターフェイスとその構成設定の変更が必要になります。この両トピックについては、「[From .NET Remoting to the Windows Communication Foundation \(WCF\)](http://go.microsoft.com/fwlink/?LinkId=74403)」を参照してください。  
  
## 参照  
 [概念](../../../../docs/framework/wcf/conceptual-overview.md)