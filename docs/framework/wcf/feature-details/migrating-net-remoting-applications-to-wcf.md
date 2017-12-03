---
title: ".NET リモート処理アプリケーションの WCF への移行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 240901f4fa04a2468d5964821680506ea117bf7f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>.NET リモート処理アプリケーションの WCF への移行
**このトピックの対象は、既存のアプリケーションとの下位互換性のために残されているレガシ テクノロジに特定されています。新規の開発には、このトピックを適用しないでください。現在、分散アプリケーションは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用して開発する必要があります。**  
  
 既存の .NET リモート処理アプリケーションから [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を利用するには、統合と移行という 2 つの方法があります。 統合によって、.NET Remoting 2.0 と [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を並行で実行できるようになり、既存の.NET Remoting 2.0 のコードに手を加えることなく、両方のテクノロジで同時に同じビジネス オブジェクトを公開できます。 統合では、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 以降が実行されている必要があります。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の機能を利用し、Remoting 2.0 システムとのネットワーク上での互換性が必要ではない場合は、サービス全体を [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に移行できます。 .NET Remoting 2.0 から [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] への移行には、リモート オブジェクトのインターフェイスとその構成設定の変更が必要になります。 これらのトピックの両方については、「[からリモート処理を Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403)です。  
  
## <a name="see-also"></a>関連項目  
 [概念](../../../../docs/framework/wcf/conceptual-overview.md)
